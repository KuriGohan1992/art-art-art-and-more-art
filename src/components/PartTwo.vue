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
        <div class="work-type-tab">
          Traditional Drawing
        </div>

        <div class="entry-copy top-copy">
          <h3>
            Mahito, Todo, Yuji
          </h3>

          <p>
            This was my most recent drawing. I drew this from
            December 23, 2023 to January 20, 2024. Before
            this, the last time I drew was in November 2021.
            I don't really draw for the sake of drawing;
            drawing, to me, is more of a means to express my
            passion for a show or a character. I guess
            recently, I haven't really been interested in any
            fictional characters, mainly because I don't
            watch anime anymore since I've gotten pretty
            busy. But I do hope that I can find a character
            that I can pour my passion into once again. Side
            note, I don't believe myself to be a good artist
            because I really just copy things, and if you
            look closely, I use the grid method, so it's more
            of a patience test if anything. But if you think
            this looks good, you can check out my entire
            drawing collection
            <a
              href="https://drive.google.com/drive/folders/1cZ1HMJl471jRczDNghU_LOIdmkia_yn_?usp=sharing"
              target="_blank"
              rel="noopener noreferrer"
            >here</a>.
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
                  'Mahito, Todo, Yuji'
                )
              "
            >
              <img
                src="/part-2/drawing.webp"
                alt="Mahito, Todo, Yuji"
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
              My Reference
            </p>
          </div>
        </div>
      </article>

      <!-- =========================
           ORIGAMI
           ========================= -->

      <article class="exploration-card origami-card">
        <div class="work-type-tab">
          Origami
        </div>

        <div class="entry-copy top-copy">
          <h3>
            Magic Ball
          </h3>

          <p>
            I searched "cool looking origami" on YouTube and
            this showed up. The
            <a
              href="https://youtu.be/W-ms0cyJ64Q?si=-FOTC26JrG_JHkRT"
              target="_blank"
              rel="noopener noreferrer"
            >video</a> was 45 minutes long, so I thought it
            would take me about that long. But boy was I
            wrong. I folded this during our department's "Day
            with the Chair." I started even before the event
            began, and I didn't even manage to fully finish it
            within the 3-hour event. I finished it shortly
            after in the Space Lounge. It was an interesting
            challenge, but I don't think I'd want to do it
            again anytime soon.
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
                  'Magic Ball'
                )
              "
            >
              <img
                src="/part-2/origami.webp"
                alt="Magic Ball origami"
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

      <article
        class="
          exploration-card
          performance-card
          rapping-card
          description-right
        "
      >
        <div class="work-type-tab">
          Rapping
        </div>

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
            Bagsakan
          </h3>

          <p>
            This is probably the most iconic rap song in the
            Philippines. I hear it all the time, and I was
            confident that I could talk pretty fast. So I
            memorized the lyrics, then I approached one of my
            classmates, John Patrick Piamonte. He
            has a studio for rent where he let me record for
            dirt cheap compared to normal. Then I learned
            that the hard part wasn't talking fast; it was
            managing my breathing during the verses. You can
            hear me mistime my breaths in the video. Also, I
            added the oldie damaged-film effect because one
            of the phones I used to record was pretty blurry,
            so I might as well commit to that, it fits
            the era of the song perfectly too.
          </p>
        </div>
      </article>

      <!-- =========================
           PLAYING THE KEYBOARD
           ========================= -->

      <article
        class="
          exploration-card
          performance-card
          keyboard-card
        "
      >
        <div class="work-type-tab">
          Playing the Keyboard
        </div>

        <div class="performance-copy">
          <h3>
            Gate of Steiner
          </h3>

          <p>
            This is the one that I spent the most time
            practicing for. We had a broken keyboard in our
            house that I never really bothered playing. Then
            this project was announced, and I tried searching
            for something interesting I could play that was
            also easy enough to learn in a few weeks. I found
            a piece of music from my favorite anime,
            "Steins;Gate," called "Gate of Steiner," so I
            bought repair parts and fixed the keyboard to the
            point of being playable enough. I practiced at
            least 4 hours per day for a month. I filmed this
            the same day I did the rap at Patrick's studio. I
            wasn't able to play it perfectly, but I'll get
            there.
            <a
              href="https://youtu.be/7YfOzt3L41U?si=q0ur7dCP80cptLGS"
              target="_blank"
              rel="noopener noreferrer"
            >
              Link to bottom-right video
            </a>
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

      <article
        class="
          exploration-card
          performance-card
          roleplaying-card
          description-right
        "
      >
        <div class="work-type-tab">
          Roleplaying
        </div>

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
            Ang Pagpupulong sa Tribunal
          </h3>

          <p>
            Like many of my other classmates, I am also here
            to shamelessly submit an output from another
            subject. Kidding, of course. But I think I've put
            in enough effort for this video to be submitted
            to two subjects. It genuinely looks simple, but
            man, there's so much thinking ahead and timing
            required to pull this off. My PC got so hot for
            so long while recording this. I think, along with
            editing, it took me more than 15 hours to finish
            this. One thing that bothers me here is how it
            sometimes looks like I'm reading a script when I
            act like I'm looking at the meet participants.
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

  color: #171717;
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

  color: #171717;

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
   STATIC CARDS
   ========================= */

.exploration-card {
  position: relative;

  margin:
    70px
    0
    34px;

  border:
    2px solid #171717;

  box-shadow:
    8px 8px 0 #171717;
}
.drawing-card {
  --card-bg:
    rgba(200, 205, 219, 0.96);

  padding:
    16px
    clamp(
      20px,
      2.4vw,
      32px
    )
    clamp(
      20px,
      2.4vw,
      32px
    );

  background:
    var(--card-bg);
}

.origami-card {
  --card-bg:
    rgba(235, 192, 139, 0.96);

  padding:
    16px
    clamp(
      20px,
      2.4vw,
      32px
    )
    clamp(
      20px,
      2.4vw,
      32px
    );

  background:
    var(--card-bg);
}

.rapping-card {
  --card-bg:
    rgba(193, 174, 201, 0.96);

  background:
    var(--card-bg);
}

.keyboard-card {
  --card-bg:
    rgba(180, 207, 203, 0.96);

  background:
    var(--card-bg);
}

.roleplaying-card {
  --card-bg:
    rgba(219, 185, 171, 0.96);

  background:
    var(--card-bg);
}

/* =========================
   FOLDER TAB
   ========================= */

.work-type-tab {
  position: absolute;

  top: -36px;
  left: -2px;

  z-index: 4;

  height: 36px;

  display: flex;
  align-items: center;

  box-sizing: border-box;

  padding: 0 16px;

  color: #171717;

  background: var(--card-bg);

  border: 2px solid #171717;
  border-bottom: 0;

  font-size: 0.78rem;
  font-weight: 800;
  line-height: 1;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  white-space: nowrap;
}

/* NEW: solid divider line at the bottom of the tab */
.work-type-tab::before {
  content: "";

  position: absolute;

  left: 0;
  right: 0;
  bottom: 0;

  height: 2px;

  background: #171717;
}

.work-type-tab::after {
  content: "";

  position: absolute;

  top: 8px;
  right: -10px;

  width: 8px;
  height: calc(100% - 8px);

  background: #171717;

  pointer-events: none;
}
.description-right .work-type-tab {
  right: -2px;
  left: auto;
}

.description-right
.work-type-tab::after {
  height: 100%;
}

/* =========================
   TITLES + COPY
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

  color: #171717;

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

  color: #171717;

  font-size: 1rem;

  line-height: 1.7;
}

.entry-copy a,
.performance-copy a {
  color: #0645ad;
  font-weight: 700;
  text-decoration: underline;
}

.entry-copy a:visited,
.performance-copy a:visited {
  color: #551a8b;
}

.entry-copy a:hover,
.performance-copy a:hover {
  text-decoration-thickness: 2px;
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
   CLICKABLE IMAGES
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

  color: #171717;

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

  min-width: 0;

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

  min-width: 0;

  padding:
    clamp(
      24px,
      3vw,
      42px
    );

  border-left:
    2px solid #171717;
}

/* =========================
   KEYBOARD REVERSED
   ========================= */

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

  .description-right .work-type-tab {
    right: auto;
    left: -2px;
  }

  .description-right
  .work-type-tab::after {
    height:
      calc(
        100% - 8px
      );
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
    margin:
      56px
      0
      20px;

    box-shadow:
      5px 5px 0 #171717;
  }

.drawing-card,
.origami-card {
  padding:
    10px
    16px
    16px;
}

  .work-type-tab {
    top: -34px;

    height: 34px;

    padding:
      0
      12px;

    font-size:
      0.7rem;

    letter-spacing:
      0.06em;
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

  .image-button:hover .paired-media,
  .image-button:hover .origami-media,
  .video-hover-frame:hover .origami-video {
    transform: none;

    filter: none;
  }
}
</style>