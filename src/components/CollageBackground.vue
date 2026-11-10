<script setup>
import {
  computed,
  onBeforeUnmount,
  onMounted,
  ref,
} from 'vue'

const categories = [
  'painting',
  'origami',
  'drawing',
  'rapping',
  'piano',
  'theater',
]

const sourceImages = categories.flatMap((category) =>
  Array.from(
    { length: 5 },
    (_, index) =>
      `/background/${category}_${index + 1}.webp`,
  ),
)

const rows = ref([])
const imageData = ref([])

const isPaused = ref(false)
const reduceMotion = ref(false)

let mediaQuery = null
let resizeFrame = null

const motionStopped = computed(
  () => isPaused.value || reduceMotion.value,
)

function shuffle(items) {
  const copy = [...items]

  for (let i = copy.length - 1; i > 0; i -= 1) {
    const j = Math.floor(Math.random() * (i + 1))

    ;[copy[i], copy[j]] = [
      copy[j],
      copy[i],
    ]
  }

  return copy
}

function loadImageData(src) {
  return new Promise((resolve) => {
    const image = new Image()

    image.onload = () => {
      resolve({
        src,
        ratio:
          image.naturalWidth /
          image.naturalHeight,
        naturallyMonochrome:
          src.includes('/drawing_'),
      })
    }

    image.onerror = () => {
      console.warn(
        `Could not load ${src}`,
      )

      resolve({
        src,
        ratio: 1,
        naturallyMonochrome:
          src.includes('/drawing_'),
      })
    }

    image.src = src
  })
}

/*
  Larger number = larger images.

  Desktop images are now slightly bigger
  than the previous version.
*/
function getTargetRowHeight() {
  const width = window.innerWidth

  if (width >= 2000) return 260
  if (width >= 1600) return 245
  if (width >= 1200) return 230
  if (width >= 900) return 215
  if (width >= 700) return 200

  // Phone
  return 185
}

function getImagesForDevice() {
  /*
    Desktop:
    use all 30.

    Mobile:
    only use 16 images in the active collage.
    This substantially reduces image rendering work.
  */
  if (window.innerWidth <= 700) {
    return imageData.value.slice(0, 16)
  }

  return imageData.value
}

function createBatch(images, cycle) {
  return shuffle(images).map(
    (image, index) => ({
      ...image,
      uid:
        `${cycle}-${index}-${image.src}`,
    }),
  )
}

function applyAlternatingGrayscale(
  rowImages,
  rowIndex,
) {
  /*
    Each row can start in one of two ways:

    COLOR | B&W | COLOR | B&W
    B&W   | COLOR | B&W | COLOR

    Drawing images are already visually
    monochrome, so we treat them as B&W
    without applying an extra filter.

    We choose whichever starting pattern
    places more drawing images into the
    B&W positions naturally.
  */
  function countDrawingConflicts(phase) {
    return rowImages.reduce(
      (conflicts, image, index) => {
        if (!image.naturallyMonochrome) {
          return conflicts
        }

        const shouldLookMonochrome =
          (index + phase) % 2 === 1

        return conflicts +
          (shouldLookMonochrome ? 0 : 1)
      },
      0,
    )
  }

  /*
    Alternate the preferred starting phase
    between rows so the overall collage feels
    closer to a checkerboard.
  */
  const preferredPhase =
    rowIndex % 2

  const alternatePhase =
    preferredPhase === 0 ? 1 : 0

  const preferredConflicts =
    countDrawingConflicts(
      preferredPhase,
    )

  const alternateConflicts =
    countDrawingConflicts(
      alternatePhase,
    )

  const phase =
    preferredConflicts <= alternateConflicts
      ? preferredPhase
      : alternatePhase

  return rowImages.map(
    (image, index) => {
      const shouldLookMonochrome =
        (index + phase) % 2 === 1

      return {
        ...image,

        /*
          Never grayscale drawings.

          They already count as monochrome
          when choosing the row pattern.
        */
        grayscale:
          !image.naturallyMonochrome &&
          shouldLookMonochrome,
      }
    },
  )
}

function createRows(
  images,
  width,
  targetHeight,
) {
  const result = []

  let row = []
  let ratioTotal = 0

  for (const image of images) {
    row.push(image)
    ratioTotal += image.ratio

    const estimatedWidth =
      ratioTotal * targetHeight

    if (estimatedWidth >= width) {
      result.push(row)

      row = []
      ratioTotal = 0
    }
  }

  /*
    Handle the final incomplete row.

    Borrow a few images from the previous row
    so the final row doesn't become one giant tile.
  */
  if (row.length > 0) {
    const minimumRatio =
      (width / targetHeight) * 0.6

    let currentRatio =
      row.reduce(
        (sum, image) =>
          sum + image.ratio,
        0,
      )

    const previousRow =
      result[result.length - 1]

    if (previousRow) {
      while (
        currentRatio < minimumRatio &&
        previousRow.length > 2
      ) {
        const borrowed =
          previousRow.pop()

        row.unshift(borrowed)

        currentRatio +=
          borrowed.ratio
      }
    }

    result.push(row)
  }

  return result.map(
    (rowImages, index) => {
      const totalRatio =
        rowImages.reduce(
          (sum, image) =>
            sum + image.ratio,
          0,
        )

      return {
        id: index,

        /*
          This is what allows the row
          to fill the exact width.
        */
        height:
          width / totalRatio,

        images:
          applyAlternatingGrayscale(
            rowImages,
            index,
          ),
      }
    },
  )
}

function buildRows() {
  if (!imageData.value.length) {
    return
  }

  const isMobile =
    window.innerWidth <= 700

  const panelWidth =
    window.innerWidth *
    (isMobile ? 1.08 : 1.04)

  const targetHeight =
    getTargetRowHeight()

  const minimumHeight =
    window.innerHeight * 1.03

  const deviceImages =
    getImagesForDevice()

  let combinedImages = []
  let builtRows = []

  let totalHeight = 0
  let cycle = 0

  /*
    Add shuffled batches only until we have
    enough rows to cover the viewport.

    This prevents huge unnecessary collages.
  */
  while (
    totalHeight < minimumHeight &&
    cycle < 5
  ) {
    combinedImages.push(
      ...createBatch(
        deviceImages,
        cycle,
      ),
    )

    builtRows = createRows(
      combinedImages,
      panelWidth,
      targetHeight,
    )

    totalHeight =
      builtRows.reduce(
        (sum, row) =>
          sum + row.height,
        0,
      )

    cycle += 1
  }

  rows.value = builtRows
}

async function initializeCollage() {
  /*
    Shuffle only once per page load.

    Resizing the browser will rearrange
    row sizes but won't constantly reshuffle
    the artwork.
  */
  const shuffled =
    shuffle(sourceImages)

  imageData.value =
    await Promise.all(
      shuffled.map(loadImageData),
    )

  buildRows()
}

function togglePause() {
  isPaused.value =
    !isPaused.value
}

function handleMotionPreference(
  event,
) {
  reduceMotion.value =
    event.matches
}

function handleResize() {
  if (resizeFrame) {
    cancelAnimationFrame(
      resizeFrame,
    )
  }

  resizeFrame =
    requestAnimationFrame(
      () => {
        buildRows()
      },
    )
}

onMounted(() => {
  mediaQuery =
    window.matchMedia(
      '(prefers-reduced-motion: reduce)',
    )

  reduceMotion.value =
    mediaQuery.matches

  mediaQuery.addEventListener(
    'change',
    handleMotionPreference,
  )

  window.addEventListener(
    'resize',
    handleResize,
  )

  initializeCollage()
})

onBeforeUnmount(() => {
  mediaQuery?.removeEventListener(
    'change',
    handleMotionPreference,
  )

  window.removeEventListener(
    'resize',
    handleResize,
  )

  if (resizeFrame) {
    cancelAnimationFrame(
      resizeFrame,
    )
  }
})
</script>

<template>
  <div
    class="collage-background"
    aria-hidden="true"
  >
    <div
      class="collage-motion"
      :class="{
        'is-paused':
          motionStopped,
      }"
    >
      <!--
        Two identical panels sit beside
        each other to create the infinite loop.
      -->
      <div
        v-for="copy in 2"
        :key="copy"
        class="collage-panel"
      >
        <div class="collage-track">
          <div
            v-for="row in rows"
            :key="
              `${copy}-${row.id}`
            "
            class="collage-row"
            :style="{
              height:
                `${row.height}px`,
            }"
          >
            <figure
              v-for="image in row.images"
              :key="
                `${copy}-${image.uid}`
              "
              class="collage-item"
              :style="{
                flexGrow:
                  image.ratio,
              }"
            >
              <img
                :src="image.src"
                :class="{
                  'is-grayscale':
                    image.grayscale,
                }"
                alt=""
                draggable="false"
                decoding="async"
              />
            </figure>
          </div>
        </div>
      </div>
    </div>

    <div
      class="collage-overlay"
    ></div>
  </div>
</template>

<style scoped>
.collage-background {
  position: fixed;
  inset: 0;

  z-index: -2;

  overflow: hidden;

  background: #111;
}

/*
  Only this one large layer moves.

  Individual images are completely static.
*/
.collage-motion {
  position: absolute;

  top: 0;
  left: -2vw;

  display: flex;

  width: max-content;

  animation:
    horizontal-scroll
    120s
    linear
    infinite;

  will-change: transform;

  /*
    Encourage GPU compositing.
  */
  transform:
    translate3d(
      0,
      0,
      0
    );

  backface-visibility:
    hidden;
}

.collage-motion.is-paused {
  animation-play-state:
    paused;
}

.collage-panel {
  flex: none;

  width: 104vw;
  min-height: 100vh;

  margin: 0;
  padding: 0;
}

.collage-track {
  width: 100%;
  min-height: 100vh;

  margin: 0;
  padding: 0;

  line-height: 0;
}

.collage-row {
  display: flex;

  width: 100%;

  margin: 0;
  padding: 0;

  overflow: hidden;

  line-height: 0;
}

.collage-item {
  flex-basis: 0;

  min-width: 0;
  height: 100%;

  margin: 0;
  padding: 0;

  border: 0;

  overflow: hidden;

  /*
    Each image paints inside
    its own box only.
  */
  contain: paint;
}

.collage-item img {
  display: block;

  width: 100%;
  height: 100%;

  margin: 0;
  padding: 0;

  border: 0;

  object-fit: cover;

  filter: none;

  /*
    Filters are assigned deliberately in
    JavaScript so naturally B&W drawings
    can count as monochrome tiles.
  */
}

.collage-item img.is-grayscale {
  filter: grayscale(100%);
}

/*
  Very subtle wash.

  We will rely primarily on the navbar
  and content panels for readability later.
*/
.collage-overlay {
  position: absolute;
  inset: 0;

  background:
    rgba(
      246,
      242,
      234,
      0.10
    );

  pointer-events: none;
}

.motion-toggle {
  position: fixed;

  right: 18px;
  bottom: 18px;

  z-index: 20;

  padding:
    0.7rem
    1rem;

  border:
    1px solid
    rgba(
      30,
      30,
      30,
      0.14
    );

  border-radius:
    999px;

  color: #171717;

  background:
    rgba(
      248,
      245,
      238,
      0.94
    );

  font: inherit;

  font-size:
    0.8rem;

  font-weight:
    650;

  cursor: pointer;
}

/*
  Move exactly one panel width.

  Because there are two identical
  panels, the reset is invisible.
*/
@keyframes horizontal-scroll {
  from {
    transform:
      translate3d(
        0,
        0,
        0
      );
  }

  to {
    transform:
      translate3d(
        -50%,
        0,
        0
      );
  }
}

/* Tablet */
@media (max-width: 900px) {
  .collage-motion {
    left: -3vw;

    animation-duration:
      160s;
  }

  .collage-panel {
    width: 106vw;
  }
}

/* Mobile */
@media (max-width: 700px) {
  /*
    Mobile intentionally renders
    only 16 source images.

    It also has:
    - the same drawing-aware grayscale pattern
    - no filter transitions
    - no backdrop blur
    - no per-image animation
  */

  .collage-motion {
    left: -4vw;

    animation-duration:
      125s;
  }

  .collage-panel {
    width: 108vw;
  }

  .motion-toggle {
    right: 12px;
    bottom: 12px;

    padding:
      0.6rem
      0.8rem;

    font-size:
      0.72rem;
  }
}

@media (
  prefers-reduced-motion:
  reduce
) {
  .collage-motion {
    animation:
      none !important;

    transform:
      none !important;
  }
}
</style>