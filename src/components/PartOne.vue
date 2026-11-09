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
          <img
            src="/part-1/floor-art.webp"
            alt="Floor Art"
            class="artwork-image"
          />

          <div class="media-divider"></div>

          <div class="work-copy">
            <h3>Floor Art</h3>

            <p>
              Add your short reflection about the
              Floor Art activity here, including the
              concept, materials, process, and what
              you learned from creating it.
            </p>
          </div>
        </article>

        <article class="work-card meme-card">
          <img
            src="/part-1/meme.webp"
            alt="Meme"
            class="artwork-image"
          />

          <div class="media-divider"></div>

          <div class="work-copy">
            <h3>Meme</h3>

            <p>
              Add your short explanation of the meme
              here, including the artwork or idea
              being referenced and how humor was used
              to communicate it.
            </p>
          </div>
        </article>
      </div>

      <!-- AI APPROPRIATION + PAINTING -->
      <div class="two-work-grid">
        <article class="work-card appropriation-card">
          <img
            src="/part-1/ai-art-appropriation.webp"
            alt="AI Art Appropriation"
            class="artwork-image"
          />

          <div class="media-divider"></div>

          <div class="work-copy">
            <h3>
              AI Art Appropriation
            </h3>

            <p>
              My appropriation reimagines Caspar
              David Friedrich's
              <em>Wanderer Above the Sea of Fog</em>
              as a student facing a sea of uncertainty
              represented by school, career, family,
              health, coding, and other responsibilities.
            </p>
          </div>
        </article>

        <article class="work-card painting-card">
          <img
            src="/part-1/painting.webp"
            alt="Painting"
            class="artwork-image"
          />

          <div class="media-divider"></div>

          <div class="work-copy">
            <h3>Painting</h3>

            <p>
              Add your short reflection about the
              painting here, including its subject,
              process, artistic choices, and what the
              activity helped you understand about
              painting.
            </p>
          </div>
        </article>
      </div>

      <!-- VIDEO -->
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

            Your browser does not support the
            video element.
          </video>
        </div>

        <div class="video-copy">
          <h3>
            Pressure
          </h3>

          <p>
            Add your final explanation here. You can
            discuss how the video communicates
            pressure through framing, close-ups,
            camera angles, slow motion, editing,
            performance, sound, and other cinematic
            techniques.
          </p>
        </div>
      </article>
    </div>
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
    2px solid
    #171717;

  box-shadow:
    8px 8px 0
    #171717;
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
   INDIVIDUAL WORK CARDS
   ========================= */

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
    2px solid
    #171717;

  box-shadow:
    8px 8px 0
    #171717;

  transition:
    transform 160ms ease,
    box-shadow 160ms ease;
}

.work-card:hover {
  transform:
    translate(
      -3px,
      -3px
    );

  box-shadow:
    11px 11px 0
    #171717;
}

.floor-card {
  background:
    rgba(
      206,
      215,
      185,
      0.92
    );
}

.meme-card {
  background:
    rgba(
      199,
      214,
      225,
      0.92
    );
}

.appropriation-card {
  background:
    rgba(
      225,
      208,
      183,
      0.92
    );
}

.painting-card {
  background:
    rgba(
      221,
      195,
      188,
      0.92
    );
}

/* =========================
   ARTWORK IMAGES
   ========================= */

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

  border-radius: 0;
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
   ARTWORK TEXT
   ========================= */

.work-copy {
  margin: 0;
}

.work-copy h3 {
  margin:
    0
    0
    8px;

  font-size:
    clamp(
      1.6rem,
      2.1vw,
      2.2rem
    );

  line-height: 1.05;
}

.work-copy p {
  max-width: 650px;

  margin: 0;

  font-size: 1rem;
  line-height: 1.65;
}

/* =========================
   VIDEO
   ========================= */

.video-card {
  display: grid;

  grid-template-columns:
    minmax(0, 1.6fr)
    minmax(280px, 0.7fr);

  align-items: stretch;

  gap: 0;

  padding: 0;

  background:
    rgba(
      202,
      196,
      218,
      0.92
    );

  border:
    2px solid
    #171717;

  box-shadow:
    8px 8px 0
    #171717;
}

.video-side {
  padding:
    clamp(
      18px,
      2.5vw,
      32px
    );

  border-right:
    2px solid
    #171717;
}

.video {
  display: block;

  width: 100%;
  height: auto;

  aspect-ratio:
    16 / 9;

  object-fit: contain;

  border-radius: 0;

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

.video-copy h3 {
  margin:
    0
    0
    14px;

  font-size:
    clamp(
      2rem,
      3vw,
      3rem
    );
}

.video-copy p {
  margin: 0;

  font-size: 1rem;
  line-height: 1.7;
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
      2px solid
      #171717;
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
      5px 5px 0
      #171717;
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
    grid-template-columns:
      1fr;

    gap: 20px;

    margin-bottom: 20px;
  }

  .work-card {
    padding: 16px;

    box-shadow:
      5px 5px 0
      #171717;
  }

  .work-card:hover {
    transform: none;

    box-shadow:
      5px 5px 0
      #171717;
  }

  .artwork-image {
    height: auto;

    max-height: 520px;
  }

  .video-card {
    box-shadow:
      5px 5px 0
      #171717;
  }
}
</style>