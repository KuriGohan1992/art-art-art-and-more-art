<script setup>
import {
  onBeforeUnmount,
  onMounted,
  ref,
} from 'vue'

const audio = ref(null)
const musicEnabled = ref(false)

const TARGET_VOLUME = 0.25
const FADE_DURATION = 500

const activeVideos = new Set()

let fadeFrame = null
let fadeId = 0
let hasPlayedOnce = false
let switchingVideos = false

function cancelFade() {
  fadeId += 1

  if (fadeFrame) {
    cancelAnimationFrame(fadeFrame)
    fadeFrame = null
  }
}

function fadeTo(targetVolume, pauseAfter = false) {
  if (!audio.value) {
    return
  }

  cancelFade()

  const currentFadeId = fadeId
  const startVolume = audio.value.volume
  const difference = targetVolume - startVolume
  const startTime = performance.now()

  function step(currentTime) {
    if (
      !audio.value ||
      currentFadeId !== fadeId
    ) {
      return
    }

    const elapsed = currentTime - startTime

    const progress = Math.min(
      elapsed / FADE_DURATION,
      1
    )

    audio.value.volume =
      startVolume +
      difference * progress

    if (progress < 1) {
      fadeFrame =
        requestAnimationFrame(step)

      return
    }

    fadeFrame = null

    if (pauseAfter) {
      audio.value.pause()
    }
  }

  fadeFrame =
    requestAnimationFrame(step)
}

async function turnMusicOn() {
  if (!audio.value) {
    return
  }

  cancelFade()

  musicEnabled.value = true

  try {
    /*
      First-ever play always starts
      the song from the beginning.
    */
    if (!hasPlayedOnce) {
      audio.value.currentTime = 0
    }

    if (audio.value.paused) {
      audio.value.volume = 0

      await audio.value.play()

      hasPlayedOnce = true
    }

    /*
      If a portfolio video is already
      playing, keep the background music
      silent until that video stops.
    */
    if (activeVideos.size === 0) {
      fadeTo(TARGET_VOLUME)
    }
  } catch (error) {
    musicEnabled.value = false

    console.error(
      'Could not play background music:',
      error
    )
  }
}

function turnMusicOff() {
  if (!audio.value) {
    return
  }

  musicEnabled.value = false

  if (!audio.value.paused) {
    fadeTo(0, true)
  }
}

function toggleMusic() {
  if (musicEnabled.value) {
    turnMusicOff()
  } else {
    turnMusicOn()
  }
}

function pauseOtherAudibleVideos(currentVideo) {
  switchingVideos = true

  const videos =
    document.querySelectorAll('video')

  for (const video of videos) {
    if (video === currentVideo) {
      continue
    }

    /*
      Leave intentionally muted looping
      previews alone, such as Origami.
    */
    if (
      video.muted ||
      video.volume === 0
    ) {
      continue
    }

    if (
      !video.paused &&
      !video.ended
    ) {
      video.pause()
    }
  }

  switchingVideos = false
}

function handleVideoPlay(event) {
  const video = event.target

  if (!(video instanceof HTMLVideoElement)) {
    return
  }

  /*
    Ignore muted looping videos,
    such as the Origami preview.
  */
  if (
    video.muted ||
    video.volume === 0
  ) {
    return
  }

  /*
    Only one audible portfolio video may
    play at a time. Starting this video
    pauses every other audible video.
  */
  pauseOtherAudibleVideos(video)

  activeVideos.clear()
  activeVideos.add(video)

  if (
    musicEnabled.value &&
    audio.value &&
    !audio.value.paused
  ) {
    fadeTo(0)
  }
}

function handleVideoStop(event) {
  const video = event.target

  if (!(video instanceof HTMLVideoElement)) {
    return
  }

  activeVideos.delete(video)

  /*
    Do not briefly fade the music back in
    while one video is being replaced by
    another video.
  */
  if (switchingVideos) {
    return
  }

  if (
    activeVideos.size === 0 &&
    musicEnabled.value &&
    audio.value &&
    !audio.value.paused
  ) {
    fadeTo(TARGET_VOLUME)
  }
}

onMounted(() => {
  document.addEventListener(
    'play',
    handleVideoPlay,
    true
  )

  document.addEventListener(
    'pause',
    handleVideoStop,
    true
  )

  document.addEventListener(
    'ended',
    handleVideoStop,
    true
  )
})

onBeforeUnmount(() => {
  document.removeEventListener(
    'play',
    handleVideoPlay,
    true
  )

  document.removeEventListener(
    'pause',
    handleVideoStop,
    true
  )

  document.removeEventListener(
    'ended',
    handleVideoStop,
    true
  )

  cancelFade()
})
</script>

<template>
  <audio
    ref="audio"
    src="/sans.mp3"
    loop
    preload="auto"
  ></audio>

  <div class="music-control">
    <Transition name="play-hint">
      <div
        v-if="!musicEnabled && !hasPlayedOnce"
        class="play-hint"
      >
        Play me!
      </div>
    </Transition>

    <button
      class="music-toggle"
      type="button"
      :class="{
        'music-toggle--off': !musicEnabled,
      }"
      :aria-label="
        musicEnabled
          ? 'Mute background music'
          : 'Play background music'
      "
      :title="
        musicEnabled
          ? 'Mute background music'
          : 'Play background music'
      "
      @click="toggleMusic"
    >
      <svg
        v-if="musicEnabled"
        viewBox="0 0 24 24"
        aria-hidden="true"
      >
        <path d="M9 18V5l10-2v13" />

        <circle
          cx="6"
          cy="18"
          r="3"
        />

        <circle
          cx="16"
          cy="16"
          r="3"
        />
      </svg>

      <svg
        v-else
        viewBox="0 0 24 24"
        aria-hidden="true"
      >
        <path d="M9 18V5l10-2v13" />

        <circle
          cx="6"
          cy="18"
          r="3"
        />

        <circle
          cx="16"
          cy="16"
          r="3"
        />

        <path
          class="mute-line"
          d="M3 3l18 18"
        />
      </svg>
    </button>
  </div>
</template>

<style scoped>
.music-control {
  position: fixed;

  right: 18px;
  bottom: 18px;

  z-index: 100;

  display: flex;
  align-items: center;
  gap: 12px;
}

.music-toggle {
  width: 48px;
  height: 48px;

  flex-shrink: 0;

  display: grid;
  place-items: center;

  padding: 0;

  color: #171717;
  background: #fffdf7;

  border: 2px solid #171717;

  box-shadow:
    5px 5px 0 #171717;

  cursor: pointer;

  transition:
    transform 150ms ease,
    box-shadow 150ms ease,
    opacity 150ms ease;
}

.music-toggle svg {
  width: 25px;
  height: 25px;

  fill: none;

  stroke: currentColor;
  stroke-width: 2;
  stroke-linecap: round;
  stroke-linejoin: round;
}

.music-toggle circle {
  fill: currentColor;
}

.music-toggle:hover {
  transform:
    translate(-2px, -2px);

  box-shadow:
    7px 7px 0 #171717;
}

.music-toggle--off {
  opacity: 1;
}

.mute-line {
  stroke-width: 2.5;
}

.play-hint {
  position: relative;

  padding:
    7px
    12px;

  color: #171717;
  background: #fffdf7;

  border: 2px solid #171717;

  box-shadow:
    4px 4px 0 #171717;

  font-size: 0.9rem;
  font-weight: 700;

  white-space: nowrap;
  pointer-events: none;

  animation:
    hint-bob
    1.2s
    ease-in-out
    infinite;
}

.play-hint::before {
  content: "";

  position: absolute;

  top: 50%;
  right: -10px;

  transform:
    translateY(-50%);

  border-top:
    8px solid transparent;

  border-bottom:
    8px solid transparent;

  border-left:
    10px solid #171717;
}

.play-hint::after {
  content: "";

  position: absolute;

  top: 50%;
  right: -7px;

  transform:
    translateY(-50%);

  border-top:
    6px solid transparent;

  border-bottom:
    6px solid transparent;

  border-left:
    8px solid #fffdf7;
}

/*
  Fade the Play me! hint away after
  the visitor starts the music.
*/
.play-hint-leave-active {
  transition:
    opacity 450ms ease,
    transform 450ms ease;
}

.play-hint-leave-to {
  opacity: 0;
  transform: translateX(8px);
}

@keyframes hint-bob {
  0%,
  100% {
    transform: translateX(0);
  }

  50% {
    transform: translateX(-4px);
  }
}

@media (max-width: 760px) {
  .music-control {
    right: 12px;
    bottom: 12px;

    gap: 10px;
  }

  .music-toggle {
    width: 44px;
    height: 44px;
  }

  .music-toggle:hover {
    transform: none;

    box-shadow:
      5px 5px 0 #171717;
  }

  .play-hint {
    padding:
      6px
      10px;

    font-size: 0.82rem;
  }
}

@media (prefers-reduced-motion: reduce) {
  .play-hint {
    animation: none;
  }

  .play-hint-leave-active {
    transition: opacity 250ms ease;
  }

  .play-hint-leave-to {
    opacity: 0;
    transform: none;
  }
}
</style>
