<script setup>
import CollageBackground from './components/CollageBackground.vue'
import Navbar from './components/Navbar.vue'
import PartOne from './components/PartOne.vue'
</script>

<template>
  <div class="site">
    <CollageBackground />
    <Navbar />

    <main>
      <section
        id="home"
        class="front-matter-page"
      >
        <div class="front-matter">
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

          <div class="contents">
            <div class="contents-heading">
              <p>TABLE OF CONTENTS</p>
            </div>

            <div class="contents-grid">
              <a
                class="contents-item"
                href="#part-one"
              >
                <span class="contents-number">
                  01
                </span>

                <div>
                  <h2>Part I</h2>
                  <p>
                    My Art Appreciation Journey
                  </p>
                </div>

                <span class="contents-arrow">
                  ↗
                </span>
              </a>

              <a
                class="contents-item"
                href="#part-two"
              >
                <span class="contents-number">
                  02
                </span>

                <div>
                  <h2>Part II</h2>
                  <p>
                    My Artistic Exploration
                  </p>
                </div>

                <span class="contents-arrow">
                  ↗
                </span>
              </a>

              <a
                class="contents-item"
                href="#reflection"
              >
                <span class="contents-number">
                  03
                </span>

                <div>
                  <h2>Final Reflection</h2>
                  <p>
                    Looking Forward:
                    Who Am I Becoming?
                  </p>
                </div>

                <span class="contents-arrow">
                  ↗
                </span>
              </a>

              <a
                class="contents-item"
                href="#appendices"
              >
                <span class="contents-number">
                  04
                </span>

                <div>
                  <h2>Appendices</h2>
                  <p>
                    Creative process and documentation
                  </p>
                </div>

                <span class="contents-arrow">
                  ↗
                </span>
              </a>
            </div>
          </div>
        </div>
      </section>

      <PartOne />

      <section
        id="part-two"
        class="future-section"
      ></section>

      <section
        id="reflection"
        class="future-section"
      ></section>

      <section
        id="appendices"
        class="future-section"
      ></section>
    </main>
  </div>
</template>