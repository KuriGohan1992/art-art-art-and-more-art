<script setup>
import { ref } from 'vue'
import ImageModal from './ImageModal.vue'

const selectedImage = ref(null)

function openImage(src, alt) {
  selectedImage.value = {
    src,
    alt,
  }
}

function closeImage() {
  selectedImage.value = null
}
</script>

<template>
  <section
    id="part-two"
    class="part-two"
  >
    <div class="section-inner">
      <header class="section-header">
        <h2>
          My Artistic Exploration
        </h2>
      </header>

      <!-- =========================
           TRADITIONAL DRAWING
           ========================= -->

      <article class="exploration-card drawing-card">
        <div class="entry-copy top-copy">
          <h3>
            Traditional Drawing
          </h3>

          <p>
            (Caption Placeholder)
          </p>
        </div>

        <div class="media-divider"></div>

        <div class="pair-grid">
          <div class="media-column">
            <button
              class="image-button"
              type="button"
              @click="
                openImage(
                  '/part-2/drawing.webp',
                  'Traditional Drawing'
                )
              "
            >
              <img
                src="/part-2/drawing.webp"
                alt="My finished traditional drawing"
                class="paired-media"
              />
            </button>

            <p class="media-label">
              My Drawing
            </p>
          </div>

          <div class="media-column">
            <button
              class="image-button"
              type="button"
              @click="
                openImage(
                  '/part-2/drawing-reference.webp',
                  'Drawing Reference'
                )
              "
            >
              <img
                src="/part-2/drawing-reference.webp"
                alt="Reference used for the drawing"
                class="paired-media"
              />
            </button>

            <p class="media-label">
              Reference
            </p>
          </div>
        </div>
      </article>

      <!-- =========================
           ORIGAMI
           ========================= -->

      <article class="exploration-card origami-card">
        <div class="entry-copy top-copy">
          <h3>
            Origami
          </h3>

          <p>
            (Caption Placeholder)
          </p>
        </div>

        <div class="media-divider"></div>

        <div class="pair-grid">
          <div class="media-column">
            <button
              class="image-button"
              type="button"
              @click="
                openImage(
                  '/part-2/origami.webp',
                  'Origami'
                )
              "
            >
              <img
                src="/part-2/origami.webp"
                alt="Finished origami"
                class="origami-media"
              />
            </button>
          </div>

          <div class="media-column">
            <div class="video-hover-frame">
              <video
                class="origami-media origami-video"
                autoplay
                muted
                loop
                playsinline
                preload="metadata"
              >
                <source
                  src="/part-2/origami-loop.mp4"
                  type="video/mp4"
                />
              </video>
            </div>
          </div>
        </div>
      </article>

      <!-- =========================
           RAPPING
           ========================= -->

      <article class="exploration-card performance-card rapping-card">
        <div class="performance-media">
          <video
            controls
            preload="metadata"
            playsinline
          >
            <source
              src="/part-2/rapping.mp4"
              type="video/mp4"
            />
          </video>
        </div>

        <div class="performance-copy">
          <h3>
            Rapping
          </h3>

          <p>
            (Caption Placeholder)
          </p>
        </div>
      </article>

      <!-- =========================
           PLAYING THE KEYBOARD
           ========================= -->

      <article class="exploration-card performance-card keyboard-card">
        <div class="performance-copy">
          <h3>
            Playing the Keyboard
          </h3>

          <p>
            (Caption Placeholder)
          </p>
        </div>

        <div class="performance-media">
          <video
            controls
            preload="metadata"
            playsinline
          >
            <source
              src="/part-2/piano.mp4"
              type="video/mp4"
            />
          </video>
        </div>
      </article>

      <!-- =========================
           ROLEPLAYING
           ========================= -->

      <article class="exploration-card performance-card roleplaying-card">
        <div class="performance-media">
          <video
            controls
            preload="metadata"
            playsinline
          >
            <source
              src="/part-2/joseriz.mp4"
              type="video/mp4"
            />
          </video>
        </div>

        <div class="performance-copy">
          <h3>
            Roleplaying
          </h3>

          <p>
            (Caption Placeholder)
          </p>
        </div>
      </article>
    </div>

    <ImageModal
      v-if="selectedImage"
      :src="selectedImage.src"
      :alt="selectedImage.alt"
      @close="closeImage"
    />
  </section>
</template>

<style scoped>
.part-two {
  position: relative;
  z-index: 2;

  padding:
    110px
    var(--page-padding)
    90px;
}

.section-inner {
  width: min(
    var(--page-max-width),
    100%
  );

  margin: 0 auto;
}

/* =========================
   SECTION TITLE
   ========================= */

.section-header {
  width: 100%;

  margin-bottom: 32px;

  padding:
    22px
    28px;

  background:
    rgba(151, 186, 175, 0.94);

  border:
    2px solid #171717;

  box-shadow:
    8px 8px 0 #171717;
}

.section-header h2 {
  margin: 0;

  font-size:
    clamp(
      2.5rem,
      4vw,
      4.5rem
    );

  line-height: 1;

  white-space: nowrap;
}

/* =========================
   STATIC PART II CARDS
   ========================= */

.exploration-card {
  margin-bottom: 34px;

  border:
    2px solid #171717;

  box-shadow:
    8px 8px 0 #171717;
}

/*
  No hover/transform here.
  Part II containers always stay still.
*/

.drawing-card {
  padding:
    clamp(
      20px,
      2.4vw,
      32px
    );

  background:
    rgba(200, 205, 219, 0.94);
}

.origami-card {
  padding:
    clamp(
      20px,
      2.4vw,
      32px
    );

  background:
    rgba(235, 192, 139, 0.94);
}

.rapping-card {
  background:
    rgba(193, 174, 201, 0.94);
}

.keyboard-card {
  background:
    rgba(180, 207, 203, 0.94);
}

.roleplaying-card {
  background:
    rgba(219, 185, 171, 0.94);
}

/* =========================
   TITLE + CAPTION
   ========================= */

.top-copy {
  width: 100%;
  max-width: none;
}

.entry-copy h3,
.performance-copy h3 {
  margin:
    0
    0
    10px;

  font-size:
    clamp(
      1.8rem,
      2.5vw,
      2.8rem
    );

  line-height: 1.05;
}

.entry-copy p,
.performance-copy p {
  width: 100%;

  margin: 0;

  font-size: 1rem;

  line-height: 1.7;
}

/* =========================
   DIVIDER
   ========================= */

.media-divider {
  width: 100%;
  height: 2px;

  margin:
    20px
    0
    24px;

  background:
    #171717;
}

/* =========================
   PAIRED MEDIA
   ========================= */

.pair-grid {
  display: grid;

  grid-template-columns:
    repeat(
      2,
      minmax(0, 1fr)
    );

  gap:
    clamp(
      20px,
      3vw,
      48px
    );

  align-items: start;
}

.media-column {
  min-width: 0;
}

/* =========================
   CLICKABLE PART II IMAGES
   ========================= */

.image-button {
  display: block;

  width: 100%;

  padding: 0;
  margin: 0;

  border: 0;

  background: transparent;

  cursor: zoom-in;

  overflow: hidden;
}

.paired-media {
  display: block;

  width: 100%;
  height: auto;

  max-height: 560px;

  object-fit: contain;

  transition:
    transform 180ms ease,
    filter 180ms ease;
}

/*
  Part II behavior:
  container stays still,
  individual image moves.
*/

.image-button:hover .paired-media {
  transform:
    scale(1.025);

  filter:
    brightness(1.05);
}

.media-label {
  margin:
    12px
    0
    0;

  text-align: center;

  font-size: 0.78rem;
  font-weight: 800;

  letter-spacing: 0.08em;

  text-transform: uppercase;
}

/* =========================
   ORIGAMI
   ========================= */

.origami-media {
  display: block;

  width: 100%;

  aspect-ratio:
    3 / 4;

  object-fit: cover;

  transition:
    transform 180ms ease,
    filter 180ms ease;
}

.image-button:hover .origami-media {
  transform:
    scale(1.025);

  filter:
    brightness(1.05);
}

.video-hover-frame {
  overflow: hidden;
}

.video-hover-frame:hover .origami-video {
  transform:
    scale(1.025);

  filter:
    brightness(1.05);
}

.origami-video {
  background: #111;
}

/* =========================
   PERFORMANCE CARDS
   ========================= */

.performance-card {
  display: grid;

  grid-template-columns:
    minmax(0, 1.55fr)
    minmax(280px, 0.7fr);

  align-items: stretch;

  gap: 0;

  padding: 0;
}

.performance-media {
  display: flex;
  align-items: center;

  padding:
    clamp(
      18px,
      2.5vw,
      30px
    );
}

.performance-media video {
  display: block;

  width: 100%;

  aspect-ratio:
    16 / 9;

  object-fit: contain;

  background: #111;
}

.performance-copy {
  display: flex;
  flex-direction: column;
  justify-content: center;

  padding:
    clamp(
      24px,
      3vw,
      42px
    );

  border-left:
    2px solid #171717;
}

/* Keyboard reverses text/video */

.keyboard-card {
  grid-template-columns:
    minmax(280px, 0.7fr)
    minmax(0, 1.55fr);
}

.keyboard-card .performance-copy {
  border-left: 0;

  border-right:
    2px solid #171717;
}

/* =========================
   TABLET
   ========================= */

@media (max-width: 950px) {
  .section-header h2 {
    white-space: normal;
  }

  .performance-card,
  .keyboard-card {
    grid-template-columns: 1fr;
  }

  .performance-copy,
  .keyboard-card .performance-copy {
    border-left: 0;
    border-right: 0;

    border-top:
      2px solid #171717;
  }

  .keyboard-card .performance-media {
    order: 1;
  }

  .keyboard-card .performance-copy {
    order: 2;
  }
}

/* =========================
   MOBILE
   ========================= */

@media (max-width: 760px) {
  .part-two {
    padding:
      84px
      var(--page-padding)
      56px;
  }

  .section-header {
    margin-bottom: 20px;

    padding: 18px;

    box-shadow:
      5px 5px 0 #171717;
  }

  .section-header h2 {
    font-size:
      clamp(
        2.25rem,
        10vw,
        3.3rem
      );
  }

  .exploration-card {
    margin-bottom: 20px;

    box-shadow:
      5px 5px 0 #171717;
  }

  .drawing-card,
  .origami-card {
    padding: 16px;
  }

  .pair-grid {
    grid-template-columns: 1fr;

    gap: 28px;
  }

  .paired-media {
    max-height: none;
  }

  .origami-media {
    max-height: 520px;
  }

  .performance-media {
    padding: 16px;
  }

  .performance-copy {
    padding: 20px;
  }

  /*
    Hover effects aren't useful on touch,
    so don't leave transformed states around.
  */

  .image-button:hover .paired-media,
  .image-button:hover .origami-media,
  .video-hover-frame:hover .origami-video {
    transform: none;

    filter: none;
  }
}
</style>