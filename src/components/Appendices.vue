<template>
  <section
    id="appendices"
    class="appendices"
  >
    <div class="section-inner">
      <header class="section-header">
        <h2>
          Appendices
        </h2>
      </header>

      <!-- =========================
           TRADITIONAL DRAWING
           ========================= -->

      <article class="appendix-card drawing-card">
        <div class="work-type-tab">
          Progress Photos & Final Work
        </div>

        <div class="appendix-heading">
          <h3>
            Traditional Drawing
          </h3>
        </div>

        <div class="full-divider"></div>

        <div class="paired-media-grid">
          <div class="paired-media-cell">
            <div class="media-frame">
              <img
                src="/appendices/drawing-process.gif"
                alt="Traditional drawing progress photos"
                class="appendix-image"
              />
            </div>
          </div>

          <div class="paired-media-cell">
            <div class="media-frame">
              <img
                src="/appendices/drawing-proof.webp"
                alt="Traditional drawing final work"
                class="appendix-image"
              />
            </div>
          </div>
        </div>
      </article>

      <!-- =========================
           ORIGAMI
           ========================= -->

      <article class="appendix-card origami-card">
        <div class="work-type-tab">
          Timelapse
        </div>

        <div class="appendix-heading">
          <h3>
            Origami
          </h3>
        </div>

        <div class="full-divider"></div>

        <div class="single-media">
          <video
            class="appendix-video"
            controls
            preload="metadata"
            playsinline
          >
            <source
              src="/appendices/origami-timelapse.mp4"
              type="video/mp4"
            />
          </video>
        </div>
      </article>

      <!-- =========================
           RAPPING
           ========================= -->

      <article class="appendix-card rapping-card">
        <div class="work-type-tab">
          Behind the Scenes
        </div>

        <div class="appendix-heading">
          <h3>
            Rapping
          </h3>
        </div>

        <div class="full-divider"></div>

        <div class="single-media">
          <video
            class="appendix-video"
            controls
            preload="metadata"
            playsinline
          >
            <source
              src="/appendices/rapping-proof.mp4"
              type="video/mp4"
            />
          </video>
        </div>
      </article>

      <!-- =========================
           PLAYING THE KEYBOARD
           ========================= -->

      <article class="appendix-card keyboard-card">
        <div class="work-type-tab">
          Behind the Scenes
        </div>

        <div class="appendix-heading">
          <h3>
            Playing the Keyboard
          </h3>
        </div>

        <div class="full-divider"></div>

        <div class="single-media">
          <video
            class="appendix-video"
            controls
            preload="metadata"
            playsinline
          >
            <source
              src="/appendices/keyboard-proof.mp4"
              type="video/mp4"
            />
          </video>
        </div>
      </article>

      <!-- =========================
           ROLEPLAYING
           ========================= -->

      <article class="appendix-card roleplaying-card">
        <div class="work-type-tab">
          Props, Outfits, & Process
        </div>

        <div class="appendix-heading">
          <h3>
            Roleplaying
          </h3>
        </div>

        <div class="full-divider"></div>

        <div class="paired-media-grid">
          <div class="paired-media-cell">
            <div class="media-frame roleplaying-frame">
              <img
                src="/appendices/roleplaying-proof-1.webp"
                alt="Roleplaying props and outfits"
                class="appendix-image roleplaying-image"
              />
            </div>
          </div>

          <div class="paired-media-cell">
            <div class="media-frame roleplaying-frame">
              <img
                src="/appendices/roleplaying-proof-2.webp"
                alt="Roleplaying process"
                class="appendix-image roleplaying-image"
              />
            </div>
          </div>
        </div>
      </article>
    </div>
  </section>
</template>

<style scoped>
.appendices {
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
   SECTION HEADER
   ========================= */

.section-header {
  width: 100%;

  margin-bottom: 32px;

  padding:
    22px
    28px;

  background:
    rgba(184, 194, 218, 0.94);

  border:
    2px solid #171717;

  box-shadow:
    8px 8px 0 #171717;
}

.section-header h2 {
  margin: 0;

  font-size:
    clamp(
      2.8rem,
      4vw,
      4.5rem
    );

  line-height: 1;
}

/* =========================
   GENERAL CARD
   ========================= */

.appendix-card {
  position: relative;

  margin:
    64px
    0
    34px;

  padding:
    18px
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

  border:
    2px solid #171717;

  box-shadow:
    8px 8px 0 #171717;
}

.drawing-card {
  --card-bg:
    rgba(200, 205, 219, 0.96);

  background:
    var(--card-bg);
}

.origami-card {
  --card-bg:
    rgba(235, 192, 139, 0.96);

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
   PROTRUDING TAB
   ========================= */

.work-type-tab {
  position: absolute;

  top: -36px;
  left: -2px;

  z-index: 3;

  display: inline-flex;
  align-items: center;

  min-height: 36px;

  padding:
    0
    16px;

  background:
    var(--card-bg);

  border:
    2px solid #171717;

  color: #171717;

  font-size: 0.78rem;
  font-weight: 800;

  letter-spacing: 0.08em;
  text-transform: uppercase;

  white-space: nowrap;
}

/* solid bottom divider on the tab */

.work-type-tab::before {
  content: "";

  position: absolute;

  left: -2px;
  right: -2px;
  bottom: -2px;

  height: 2px;

  background: #171717;
}

/* right-side shadow that stops before the top */

.work-type-tab::after {
  content: "";

  position: absolute;

  top: 8px;
  right: -10px;

  width: 8px;

  height:
    calc(
      100% - 8px
    );

  background: #171717;
}

/* =========================
   HEADING + DIVIDER
   ========================= */

.appendix-heading h3 {
  margin: 0;

  color: #171717;

  font-size:
    clamp(
      2rem,
      3vw,
      3rem
    );

  line-height: 1.05;
}

.full-divider {
  width: 100%;
  height: 2px;

  margin:
    14px
    0
    22px;

  background: #171717;
}

/* =========================
   MEDIA
   ========================= */

.single-media {
  width: 100%;
}

.appendix-video {
  display: block;

  width: 100%;
  height: auto;

  background: #000;
}

/* =========================
   PAIRED MEDIA
   ========================= */

.paired-media-grid {
  display: grid;

  grid-template-columns:
    repeat(
      2,
      minmax(0, 1fr)
    );

  gap: 0;
}

.paired-media-cell {
  padding:
    0
    18px
    0
    0;
}

.paired-media-cell + .paired-media-cell {
  padding:
    0
    0
    0
    18px;
}

.media-frame {
  display: flex;
  align-items: center;
  justify-content: center;

  width: 100%;

  overflow: hidden;
}

.appendix-image {
  display: block;

  width: 100%;

  height:
    clamp(
      340px,
      36vw,
      540px
    );

  object-fit: contain;
  object-position: center;
}

/* =========================
   ROLEPLAYING IMAGE RULES
   ========================= */

.roleplaying-frame {
  min-height:
    clamp(
      340px,
      36vw,
      540px
    );
}

.roleplaying-image {
  width: auto;

  max-width: 100%;

  height:
    clamp(
      340px,
      36vw,
      540px
    );

  object-fit: contain;
  object-position: center;
}

/* =========================
   TABLET
   ========================= */

@media (max-width: 900px) {
  .paired-media-grid {
    grid-template-columns: 1fr;
  }

  .paired-media-cell {
    padding: 0;
  }

  .paired-media-cell + .paired-media-cell {
    padding:
      24px
      0
      0;

    margin-top: 24px;
  }
}

/* =========================
   MOBILE
   ========================= */

@media (max-width: 760px) {
  .appendices {
    padding:
      84px
      var(--page-padding)
      60px;
  }

  .section-header {
    margin-bottom: 22px;

    padding: 18px;

    box-shadow:
      5px 5px 0 #171717;
  }

  .section-header h2 {
    font-size:
      clamp(
        2.4rem,
        11vw,
        3.4rem
      );
  }

  .appendix-card {
    margin:
      56px
      0
      24px;

    padding:
      14px
      16px
      16px;

    box-shadow:
      5px 5px 0 #171717;
  }

  .work-type-tab {
    top: -34px;

    min-height: 34px;

    padding:
      0
      12px;

    font-size: 0.68rem;

    letter-spacing: 0.06em;
  }

  .appendix-heading h3 {
    font-size:
      clamp(
        1.9rem,
        8vw,
        2.6rem
      );
  }

  .full-divider {
    margin:
      12px
      0
      18px;
  }

  .appendix-image,
  .roleplaying-image {
    width: 100%;
    height: auto;

    max-height: none;
  }

  .roleplaying-frame {
    min-height: 0;
  }
}
</style>