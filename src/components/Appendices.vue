<template>
  <section
    id="appendices"
    class="appendices"
  >
    <div class="section-inner">
      <!-- HEADER -->
      <header class="section-header">
        <h2>Appendices</h2>
      </header>

      <!-- =========================
           TRADITIONAL DRAWING
           ========================= -->
      <article class="appendix-card drawing-card paired-card">
        <div class="card-heading">
          <h3>Traditional Drawing</h3>
        </div>

        <div class="divider"></div>

        <div class="paired-media-grid">
          <figure class="proof-item">
            <div class="media-frame">
              <img
                src="/appendices/drawing-process.gif"
                alt="Traditional drawing progress"
                class="proof-image"
              />
            </div>

            <figcaption>PROGRESS PHOTOS</figcaption>
          </figure>

          <figure class="proof-item">
            <div class="media-frame">
              <img
                src="/appendices/drawing-proof.webp"
                alt="Completed traditional drawing"
                class="proof-image"
              />
            </div>

            <figcaption>FINAL WORK</figcaption>
          </figure>
        </div>
      </article>

      <!-- =========================
           ORIGAMI
           ========================= -->
      <article class="appendix-card origami-card video-card">
        <div class="video-heading">
          <h3>Origami | Timelapse</h3>
        </div>

        <div class="divider"></div>

        <div class="video-body">
          <video
            src="/appendices/origami-timelapse.mp4"
            controls
            playsinline
            preload="metadata"
          ></video>
        </div>
      </article>

      <!-- =========================
           RAPPING
           ========================= -->
      <article class="appendix-card rapping-card video-card">
        <div class="video-heading">
          <h3>Rapping | Behind the Scenes</h3>
        </div>

        <div class="divider"></div>

        <div class="video-body">
          <video
            src="/appendices/rapping-proof.mp4"
            controls
            playsinline
            preload="metadata"
          ></video>
        </div>
      </article>

      <!-- =========================
           PLAYING THE KEYBOARD
           ========================= -->
      <article class="appendix-card keyboard-card video-card">
        <div class="video-heading">
          <h3>Playing the Keyboard | Behind the Scenes</h3>
        </div>

        <div class="divider"></div>

        <div class="video-body">
          <video
            src="/appendices/keyboard-proof.mp4"
            controls
            playsinline
            preload="metadata"
          ></video>
        </div>
      </article>

      <!-- =========================
           ROLEPLAYING
           ========================= -->
      <article class="appendix-card roleplaying-card paired-card">
        <div class="card-heading">
          <h3>Roleplaying</h3>
        </div>

        <div class="divider"></div>

        <div class="paired-media-grid">
          <figure class="proof-item">
            <div class="media-frame">
              <img
                src="/appendices/roleplaying-proof-1.webp"
                alt="Roleplaying props and outfits"
                class="proof-image"
              />
            </div>

            <figcaption>PROPS & OUTFITS</figcaption>
          </figure>

          <figure class="proof-item">
            <div class="media-frame">
              <img
                src="/appendices/roleplaying-proof-2.webp"
                alt="Roleplaying process"
                class="proof-image"
              />
            </div>

            <figcaption>PROCESS</figcaption>
          </figure>
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
    100px;
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
   GENERAL CARDS
   ========================= */

.appendix-card {
  margin-bottom: 34px;

  border:
    2px solid #171717;

  box-shadow:
    8px 8px 0 #171717;

  overflow: hidden;
}

.drawing-card {
  background:
    rgba(200, 205, 219, 0.94);
}

.origami-card {
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

.divider {
  width: 100%;
  height: 2px;

  background: #171717;
}

/* =========================
   PAIRED IMAGE CARDS
   ========================= */

.card-heading {
  padding:
    24px
    28px;
}

.card-heading h3 {
  margin: 0;

  font-size:
    clamp(
      2rem,
      3vw,
      3rem
    );

  line-height: 1.1;
}

.paired-media-grid {
  display: grid;

  grid-template-columns:
    repeat(
      2,
      minmax(0, 1fr)
    );
}

.proof-item {
  margin: 0;

  padding: 24px;
}

.proof-item + .proof-item {
  border-left:
    2px solid #171717;
}

.media-frame {
  display: flex;
  align-items: center;
  justify-content: center;

  width: 100%;

  overflow: hidden;

  /* No extra background behind image */
  background: transparent;
}

.proof-image {
  display: block;

  width: 100%;

  height:
    clamp(
      340px,
      36vw,
      540px
    );

  object-fit: contain;
}

.proof-item figcaption {
  margin-top: 14px;

  font-size: 0.82rem;
  font-weight: 700;

  letter-spacing: 0.1em;
}

/* =========================
   VIDEO CARDS
   ========================= */

.video-heading {
  display: flex;
  align-items: center;
  justify-content: space-between;

  gap: 24px;

  padding:
    22px
    28px;
}

.video-heading h3 {
  margin: 0;

  font-size:
    clamp(
      2rem,
      3vw,
      3rem
    );

  line-height: 1.1;
}

.proof-label {
  flex-shrink: 0;

  font-size: 0.82rem;
  font-weight: 700;

  letter-spacing: 0.12em;
}

.video-body {
  padding: 24px;
}

.video-body video {
  display: block;

  width: 100%;
  height: auto;

  border: 0;
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
    margin-bottom: 24px;

    box-shadow:
      5px 5px 0 #171717;
  }

  .card-heading,
  .video-heading {
    padding:
      20px
      18px;
  }

  .video-heading {
    align-items: flex-start;
    flex-direction: column;

    gap: 8px;
  }

  .paired-media-grid {
    grid-template-columns: 1fr;
  }

  .proof-item {
    padding: 18px;
  }

  .proof-item + .proof-item {
    border-left: 0;

    border-top:
      2px solid #171717;
  }

  .proof-image {
    height: auto;

    max-height: 500px;
  }

  .video-body {
    padding: 18px;
  }
}
</style>