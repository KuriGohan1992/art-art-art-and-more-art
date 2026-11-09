<script setup>
import CollageBackground from './components/CollageBackground.vue'
import Navbar from './components/Navbar.vue'
import PartOne from './components/PartOne.vue'
import PartTwo from './components/PartTwo.vue'
import FinalReflection from './components/FinalReflection.vue'
import Appendices from './components/Appendices.vue'
</script>

<template>
  <div class="site">
    <CollageBackground />

    <Navbar />

    <main>
      <!-- =========================
           FRONT MATTER
           ========================= -->
      <section
        id="home"
        class="front-matter-page"
      >
        <div class="front-matter">
          <!-- =========================
               INTRODUCTION
               ========================= -->
          <div class="front-matter-top">
            <div class="intro-panel">
              <h1>
                Art, art, art,
                <br />
                and more art!
              </h1>

              <p class="introduction">
                This portfolio brings together my works,
                activities, explorations, and reflections
                from Art Appreciation. It documents not
                only the artworks I created throughout the
                course, but also how my understanding of
                art developed through observation,
                experimentation, interpretation, and
                reflection.
              </p>
            </div>

            <div class="profile-photo-wrapper">
              <img
                src="/profile.webp"
                alt="Portrait of Cham"
                class="profile-photo"
              />
            </div>
          </div>

          <!-- =========================
               TABLE OF CONTENTS
               ========================= -->
          <div class="contents">
            <div class="contents-heading">
              <p>TABLE OF CONTENTS</p>
            </div>

            <div class="contents-list-wrapper">
              <!-- PART I -->
              <a
                class="contents-row contents-part-one"
                href="#part-one"
              >
                <div class="contents-number-column">
                  <span class="contents-number">
                    01
                  </span>
                </div>

                <div class="contents-body">
                  <div class="contents-main">
                    <h2>Part I</h2>

                    <p>
                      My Art Appreciation Journey
                    </p>
                  </div>

                  <ul class="contents-items">
                    <li>Floor Art</li>
                    <li>Meme</li>
                    <li>AI Art Appropriation</li>
                    <li>Painting</li>
                    <li>Pressure</li>
                  </ul>
                </div>
              </a>

              <!-- PART II -->
              <a
                class="contents-row contents-part-two"
                href="#part-two"
              >
                <div class="contents-number-column">
                  <span class="contents-number">
                    02
                  </span>
                </div>

                <div class="contents-body">
                  <div class="contents-main">
                    <h2>Part II</h2>

                    <p>
                      My Artistic Exploration
                    </p>
                  </div>

                  <ul class="contents-items">
                    <li>Traditional Drawing</li>
                    <li>Origami</li>
                    <li>Rapping</li>
                    <li>Playing the Keyboard</li>
                    <li>Roleplaying</li>
                  </ul>
                </div>
              </a>

              <!-- FINAL REFLECTION -->
              <a
                class="contents-row contents-reflection"
                href="#reflection"
              >
                <div class="contents-number-column">
                  <span class="contents-number">
                    03
                  </span>
                </div>

                <div class="contents-body reflection-body">
                  <div class="contents-main">
                    <h2>Final Reflection</h2>

                    <p>
                      Looking Forward:
                      Who Am I Becoming?
                    </p>
                  </div>
                </div>
              </a>

              <!-- APPENDICES -->
              <a
                class="contents-row contents-appendices"
                href="#appendices"
              >
                <div class="contents-number-column">
                  <span class="contents-number">
                    04
                  </span>
                </div>

                <div class="contents-body">
                  <div class="contents-main">
                    <h2>Appendices</h2>

                    <p>
                      Creative process and documentation
                    </p>
                  </div>

                  <ul class="contents-items">
                    <li>Traditional Drawing</li>
                    <li>Origami | Timelapse</li>
                    <li>Rapping | Behind the Scenes</li>
                    <li>
                      Playing the Keyboard |
                      Behind the Scenes
                    </li>
                    <li>Roleplaying</li>
                  </ul>
                </div>
              </a>
            </div>
          </div>
        </div>
      </section>

      <!-- =========================
           PORTFOLIO
           ========================= -->
      <PartOne />

      <PartTwo />

      <FinalReflection />

      <Appendices />
    </main>
  </div>
</template>

<style scoped>
/* =========================
   TABLE OF CONTENTS
   ========================= */

.contents {
  margin-top:
    clamp(
      30px,
      4vh,
      44px
    );
}

/* =========================
   HEADING
   ========================= */

.contents-heading {
  display: inline-flex;
  align-items: center;

  margin-bottom: 16px;

  padding:
    8px
    16px;

  background:
    rgba(245, 238, 220, 0.96);

  border:
    2px solid #171717;

  box-shadow:
    5px 5px 0 #171717;
}

.contents-heading p {
  margin: 0;

  color: #171717;

  font-size:
    clamp(
      0.9rem,
      1.1vw,
      1.05rem
    );

  font-weight: 700;

  letter-spacing: 0.12em;
}

/* =========================
   ROW LIST
   ========================= */

.contents-list-wrapper {
  display: flex;
  flex-direction: column;

  gap: 18px;
}

/* =========================
   ROW
   ========================= */

.contents-row {
  display: grid;

  grid-template-columns:
    110px
    minmax(0, 1fr);

  width: 100%;

  color: #171717;
  text-decoration: none;

  border:
    2px solid #171717;

  box-shadow:
    8px 8px 0 #171717;

  overflow: hidden;

  transition:
    transform 160ms ease,
    box-shadow 160ms ease;
}

.contents-row:hover {
  transform:
    translate(
      -3px,
      -3px
    );

  box-shadow:
    11px 11px 0 #171717;
}

/* =========================
   ROW COLORS
   ========================= */

.contents-part-one {
  background:
    rgba(213, 166, 119, 0.92);
}

.contents-part-two {
  background:
    rgba(151, 186, 175, 0.92);
}

.contents-reflection {
  background:
    rgba(224, 187, 120, 0.92);
}

.contents-appendices {
  background:
    rgba(184, 194, 218, 0.92);
}

/* =========================
   NUMBER COLUMN
   ========================= */

.contents-number-column {
  display: flex;

  align-items: center;
  justify-content: center;

  padding:
    20px
    12px;

  border-right:
    2px solid #171717;
}

.contents-number {
  font-size:
    clamp(
      2rem,
      2.5vw,
      2.8rem
    );

  font-weight: 700;

  line-height: 1;

  letter-spacing:
    -0.04em;
}

/* =========================
   ROW BODY
   ========================= */

.contents-body {
  display: grid;

  grid-template-columns:
    minmax(280px, 0.9fr)
    minmax(0, 1.3fr);

  align-items: center;

  gap:
    clamp(
      28px,
      4vw,
      70px
    );

  padding:
    22px
    30px;
}

.reflection-body {
  grid-template-columns: 1fr;
}

/* =========================
   TITLE
   ========================= */

.contents-main {
  min-width: 0;
}

.contents-main h2 {
  margin: 0;

  font-size:
    clamp(
      2.25rem,
      3vw,
      3.35rem
    );

  line-height: 0.95;

  letter-spacing:
    -0.025em;
}

.contents-main p {
  margin:
    9px
    0
    0;

  font-size:
    clamp(
      1rem,
      1.25vw,
      1.35rem
    );

  line-height: 1.25;
}

/* =========================
   CONTENT ITEMS

   Using columns instead of grid prevents
   long items in one column from creating
   empty vertical space in the other.
   ========================= */

.contents-items {
  margin: 0;

  padding-left: 22px;

  column-count: 2;
  column-gap: 44px;
}

.contents-items li {
  margin-bottom: 8px;

  font-size:
    clamp(
      1rem,
      1.2vw,
      1.28rem
    );

  line-height: 1.25;

  break-inside: avoid;
}

/* =========================
   TABLET
   ========================= */

@media (max-width: 1000px) {
  .contents-row {
    grid-template-columns:
      90px
      minmax(0, 1fr);
  }

  .contents-number-column {
    padding:
      20px
      10px;
  }

  .contents-body {
    grid-template-columns:
      minmax(220px, 0.9fr)
      minmax(0, 1.1fr);

    gap: 24px;

    padding:
      20px
      24px;
  }

  .reflection-body {
    grid-template-columns: 1fr;
  }

  .contents-items {
    column-count: 1;
  }
}

/* =========================
   MOBILE
   ========================= */

@media (max-width: 760px) {
  .contents {
    margin-top: 28px;
  }

  .contents-heading {
    margin-bottom: 14px;

    padding:
      7px
      12px;

    box-shadow:
      4px 4px 0 #171717;
  }

  .contents-list-wrapper {
    gap: 14px;
  }

  .contents-row {
    grid-template-columns:
      70px
      minmax(0, 1fr);

    box-shadow:
      5px 5px 0 #171717;
  }

  .contents-row:hover {
    transform: none;

    box-shadow:
      5px 5px 0 #171717;
  }

  .contents-number-column {
    align-items: center;

    padding:
      18px
      8px;
  }

  .contents-number {
    font-size:
      clamp(
        1.55rem,
        7vw,
        2rem
      );
  }

  .contents-body,
  .reflection-body {
    grid-template-columns: 1fr;

    gap: 16px;

    padding:
      18px
      16px;
  }

  .contents-main h2 {
    font-size:
      clamp(
        1.8rem,
        8vw,
        2.5rem
      );
  }

  .contents-main p {
    font-size:
      clamp(
        0.9rem,
        4vw,
        1.08rem
      );
  }

  .contents-items {
    column-count: 1;

    padding-left: 18px;
  }

  .contents-items li {
    margin-bottom: 5px;

    font-size:
      clamp(
        0.9rem,
        4vw,
        1.05rem
      );
  }
}
</style>