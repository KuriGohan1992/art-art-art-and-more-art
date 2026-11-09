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
    id="part-one"
    class="part-one"
  >
    <div class="section-inner">
      <header class="section-header">
        <h2>
          My Art Appreciation Journey
        </h2>
      </header>

      <!-- FLOOR ART + MEME -->
      <div class="two-work-grid">
        <article class="work-card floor-card">
          <button
            class="image-button"
            type="button"
            @click="
              openImage(
                '/part-1/floor-art.webp',
                'Floor Art'
              )
            "
          >
            <img
              src="/part-1/floor-art.webp"
              alt="Floor Art"
              class="artwork-image"
            />
          </button>

          <div class="media-divider"></div>

          <div class="work-copy">
            <h3>Floor Art</h3>

            <p>
              This was our first activity in GEARTS and it was
              a group project. I played the role of a co-leader
              here. We didn't exactly have a leader either, but
              I did my best to organize the group, gather
              materials, and support the other members. The
              resulting artwork turned out way better than
              expected.
            </p>
          </div>
        </article>

        <article class="work-card meme-card">
          <button
            class="image-button"
            type="button"
            @click="
              openImage(
                '/part-1/meme.webp',
                'Meme'
              )
            "
          >
            <img
              src="/part-1/meme.webp"
              alt="Meme"
              class="artwork-image"
            />
          </button>

          <div class="media-divider"></div>

          <div class="work-copy">
            <h3>Meme</h3>

            <p>
              This was probably the most fun activity, mainly
              because of the limitless ideas for humor,
              especially within our generation. I had like 10
              other ideas I could've submitted, but I picked
              this one because this picture always makes me
              laugh. Also, it was funny to view the memes
              submitted by my other classmates.
            </p>
          </div>
        </article>
      </div>

      <!-- AI ART APPROPRIATION + PAINTING -->
      <div class="two-work-grid">
        <article class="work-card appropriation-card">
          <button
            class="image-button"
            type="button"
            @click="
              openImage(
                '/part-1/ai-art-appropriation.webp',
                'AI Art Appropriation'
              )
            "
          >
            <img
              src="/part-1/ai-art-appropriation.webp"
              alt="AI Art Appropriation"
              class="artwork-image"
            />
          </button>

          <div class="media-divider"></div>

          <div class="work-copy">
            <h3>
              AI Art Appropriation
            </h3>

            <p>
              This was the first time I've ever used AI to
              submit an actual artwork. My appropriation
              reimagines Caspar David Friedrich's
              <em>Wanderer Above the Sea of Fog</em>
              as a student (me) facing a sea of uncertainty
              represented by school, career, family, health,
              relationships, and other responsibilities.
            </p>
          </div>
        </article>

        <article class="work-card painting-card">
          <button
            class="image-button"
            type="button"
            @click="
              openImage(
                '/part-1/painting.webp',
                'Painting'
              )
            "
          >
            <img
              src="/part-1/painting.webp"
              alt="Painting"
              class="artwork-image"
            />
          </button>

          <div class="media-divider"></div>

          <div class="work-copy">
            <h3>Painting</h3>

            <p>
              I've always been attracted to the art style of
              Pablo Picasso, so when I had a chance to try and
              paint one, I did. This was an individual
              activity, but while painting it, nobody really
              felt alone because we were all huddled up in a
              circle, sharing brushes, paint, ideas, and
              laughs. It's my best painting evah!
            </p>
          </div>
        </article>
      </div>

      <!-- PRESSURE -->
      <article class="video-card">
        <div class="video-side">
          <video
            class="video"
            controls
            preload="metadata"
            playsinline
          >
            <source
              src="/part-1/one-minute-video.mp4"
              type="video/mp4"
            />
          </video>
        </div>

        <div class="video-copy">
          <h3>
            1 Minute Video
          </h3>

          <p>
            Although it wasn't official, I think I can say I
            was the leader in this group activity. I thought
            of the idea, approached the people we filmed, and
            filmed all the shots except for the first one. It
            was embarrassing at first to approach people and
            ask if we could film them, but the pressure of
            time was greater. This was probably the activity
            with the most time pressure. In fact, we were
            supposed to present this, but none of us were able
            to due to the lack of time. But with all that
            being said, credits to Zaki Goc since he was the
            one who edited the video, and we were able to
            submit on time at the very least.
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
.part-one {
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
    rgba(213, 166, 119, 0.92);

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
   TWO-COLUMN ROW
   ========================= */

.two-work-grid {
  display: grid;

  grid-template-columns:
    repeat(
      2,
      minmax(0, 1fr)
    );

  gap:
    clamp(
      18px,
      2.2vw,
      34px
    );

  margin-bottom: 34px;
}

/* =========================
   PART I CARDS
   ========================= */

/*
  PART I RULE:
  THE CARD MOVES.
  THE IMAGE DOES NOT.
*/

.work-card {
  position: relative;

  min-width: 0;

  padding:
    clamp(
      18px,
      2vw,
      28px
    );

  border:
    2px solid #171717;

  box-shadow:
    8px 8px 0 #171717;

  transition:
    transform 160ms ease,
    box-shadow 160ms ease;
}

.work-card:hover {
  transform:
    translate(-3px, -3px);

  box-shadow:
    11px 11px 0 #171717;
}

.floor-card {
  background:
    rgba(206, 215, 185, 0.92);
}

.meme-card {
  background:
    rgba(199, 214, 225, 0.92);
}

.appropriation-card {
  background:
    rgba(225, 208, 183, 0.92);
}

.painting-card {
  background:
    rgba(221, 195, 188, 0.92);
}

/* =========================
   IMAGES
   ========================= */

.image-button {
  display: block;

  width: 100%;

  margin: 0;
  padding: 0;

  border: 0;

  background: transparent;

  cursor: zoom-in;
}

.artwork-image {
  display: block;

  width: 100%;

  height:
    clamp(
      380px,
      38vw,
      560px
    );

  object-fit: contain;
  object-position: center;

  margin: 0;

  /*
    IMPORTANT:
    no transition
    no transform
    no hover animation
  */
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
    16px;

  background:
    #171717;
}

/* =========================
   TEXT
   ========================= */

.work-copy h3,
.video-copy h3 {
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

.work-copy p,
.video-copy p {
  margin: 0;

  font-size: 1rem;

  line-height: 1.7;
}

/* =========================
   PRESSURE
   ========================= */

/*
  PRESSURE RULE:
  completely static container.
*/

.video-card {
  display: grid;

  grid-template-columns:
    minmax(0, 1.6fr)
    minmax(280px, 0.7fr);

  align-items: stretch;

  gap: 0;

  background:
    rgba(202, 196, 218, 0.92);

  border:
    2px solid #171717;

  box-shadow:
    8px 8px 0 #171717;
}

.video-side {
  padding:
    clamp(
      18px,
      2.5vw,
      32px
    );

  border-right:
    2px solid #171717;
}

.video {
  display: block;

  width: 100%;

  aspect-ratio:
    16 / 9;

  object-fit: contain;

  background: #111;
}

.video-copy {
  display: flex;
  flex-direction: column;
  justify-content: center;

  padding:
    clamp(
      22px,
      3vw,
      38px
    );
}

/* =========================
   TABLET
   ========================= */

@media (max-width: 950px) {
  .section-header h2 {
    white-space: normal;
  }

  .artwork-image {
    height: 430px;
  }

  .video-card {
    grid-template-columns: 1fr;
  }

  .video-side {
    border-right: 0;

    border-bottom:
      2px solid #171717;
  }
}

/* =========================
   MOBILE
   ========================= */

@media (max-width: 760px) {
  .part-one {
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

  .two-work-grid {
    grid-template-columns: 1fr;

    gap: 20px;

    margin-bottom: 20px;
  }

  .work-card {
    padding: 16px;

    box-shadow:
      5px 5px 0 #171717;
  }

  /*
    No meaningful hover on touch screens.
  */

  .work-card:hover {
    transform: none;

    box-shadow:
      5px 5px 0 #171717;
  }

  .artwork-image {
    height: auto;

    max-height: 520px;
  }

  .video-card {
    box-shadow:
      5px 5px 0 #171717;
  }
}
</style>