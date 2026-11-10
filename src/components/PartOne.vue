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

      <!-- =========================
           FLOOR ART + MEME
           ========================= -->

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
            <h3>
              Floor Art
            </h3>

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
            <h3>
              Meme
            </h3>

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

      <!-- =========================
           AI ART + PAINTING
           ========================= -->

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
            <h3>
              Painting
            </h3>

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

      <!-- =========================
           ARTWORK ANALYSIS
           ========================= -->

      <article
        class="
          performance-card
          analysis-card
        "
      >
        <div class="performance-copy">
          <h3>
            Artwork Analysis
          </h3>

          <p>
            This was a group activity where I was the designated leader of our group. We decided to pick this song because we have deeply connected with it in our theater performance for GEWORLD during our freshman year. My contributions here aside from managing and leading were building a script, contributing to the research, and refining the powerpoint presentation. Listening to the song brought back a lot of good memories from our theater play, and also reminded me of some of our classmates who are no longer with us (they either shifted, dropped, or moved to another country).
          </p>
        </div>

        <div class="performance-media">
          <video
            controls
            preload="metadata"
            playsinline
          >
            <source
              src="/part-1/artwork-analysis.mp4"
              type="video/mp4"
            />
          </video>
        </div>
      </article>

      <!-- =========================
           1 MINUTE VIDEO
           ========================= -->

      <article
        class="
          performance-card
          minute-card
        "
      >
        <div class="performance-media">
          <video
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

        <div class="performance-copy">
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
   TWO-COLUMN ARTWORK ROWS
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
   PART I ARTWORK CARDS
   ========================= */

/*
  PART I RULE:
  Card moves on hover.
  Image itself stays still.
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
}

/* =========================
   ARTWORK DIVIDER
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

.work-copy p,
.performance-copy p {
  width: 100%;

  margin: 0;

  font-size: 1rem;

  line-height: 1.7;
}

/* =========================
   VIDEO / PERFORMANCE CARDS
   ========================= */

/*
  These intentionally use the same layout
  structure as Part II performance cards.
*/

.performance-card {
  display: grid;

  grid-template-columns:
    minmax(0, 1.55fr)
    minmax(280px, 0.7fr);

  align-items: stretch;

  gap: 0;

  padding: 0;

  margin-bottom: 34px;

  border:
    2px solid #171717;

  box-shadow:
    8px 8px 0 #171717;
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
   ARTWORK ANALYSIS
   ========================= */

/*
  Desktop:
  text LEFT
  video RIGHT
*/

.analysis-card {
  grid-template-columns:
    minmax(280px, 0.7fr)
    minmax(0, 1.55fr);

  background:
    rgba(180, 207, 203, 0.94);
}

.analysis-card .performance-copy {
  border-left: 0;

  border-right:
    2px solid #171717;
}

/* =========================
   1 MINUTE VIDEO
   ========================= */

/*
  Desktop:
  video LEFT
  text RIGHT
*/

.minute-card {
  background:
    rgba(202, 196, 218, 0.94);
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

  .performance-card,
  .analysis-card {
    grid-template-columns: 1fr;
  }

  /*
    Mobile/tablet ordering matches Part II:
    video first, text second.
  */

  .analysis-card .performance-media {
    order: 1;
  }

  .analysis-card .performance-copy {
    order: 2;
  }

  .performance-copy,
  .analysis-card .performance-copy {
    border-left: 0;
    border-right: 0;

    border-top:
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
    No meaningful hover movement on touch.
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

  .performance-card {
    margin-bottom: 20px;

    box-shadow:
      5px 5px 0 #171717;
  }

  .performance-media {
    padding: 16px;
  }

  .performance-copy {
    padding: 20px;
  }
}
</style>