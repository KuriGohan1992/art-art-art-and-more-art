<template>
  <section
    id="reflection"
    class="final-reflection"
  >
    <div class="section-inner">
      <header class="section-header">
        <h2>
          Looking Forward: Who Am I Becoming?
        </h2>
      </header>

      <div class="reflection-composition">
        <!-- MAIN REFLECTION -->
        <article class="reflection-card">
          <div class="reflection-copy">
            <p>
              Before taking Art Appreciation, I often thought of art mainly
              in terms of the finished work: a drawing, a painting, a song,
              or a performance. Throughout the course, I became more aware
              of everything behind that final result—the choices of medium,
              composition, technique, context, presentation, and the meaning
              that both the artist and the audience can bring to a work.
            </p>

            <p>
              The activities in Part I allowed me to experience art through
              structured exercises, from visual works and appropriation to
              video. Part II gave me more freedom to explore practices that
              are either familiar to me or outside the usual forms I associate
              with schoolwork, such as traditional drawing, origami, rapping,
              playing the keyboard, and roleplaying. Seeing these works
              together made me realize that my creative interests do not fit
              neatly into only one medium.
            </p>

            <p>
              Moving forward, I want to continue approaching art with more
              curiosity and intention. I do not think I need to become one
              specific kind of artist. Instead, I want to keep experimenting,
              learning unfamiliar forms, improving the skills I already have,
              and finding ways to combine creativity with the other things I
              enjoy. More than anything, this course changed art from something
              I simply make or observe into something I now think about,
              interpret, and understand more consciously.
            </p>
          </div>
        </article>

        <!-- MONKEY TAB -->
        <div class="photo-tab monkey-tab">
          <img
            src="/reflection/reflection-monkey.webp"
            alt=""
            aria-hidden="true"
          />
        </div>

        <!-- MY PHOTO TAB -->
        <div class="photo-tab me-tab">
          <img
            src="/reflection/reflection-me.webp"
            alt=""
            aria-hidden="true"
          />
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.final-reflection {
  position: relative;
  z-index: 2;

  padding:
    110px
    var(--page-padding)
    120px;
}

.section-inner {
  width: min(
    var(--page-max-width),
    100%
  );

  margin: 0 auto;
}

/* =========================
   TITLE
   ========================= */

.section-header {
  width: 100%;

  margin-bottom: 54px;

  padding:
    20px
    28px;

  background:
    rgba(224, 187, 120, 0.94);

  border:
    2px solid #171717;

  box-shadow:
    8px 8px 0 #171717;
}

.section-header h2 {
  margin: 0;

  font-size:
    clamp(
      2rem,
      2.85vw,
      3.25rem
    );

  line-height: 1;

  white-space: nowrap;
}

/* =========================
   COMPOSITION
   ========================= */

/*
  There is NO background on this element.

  This means the collage remains visible in
  all of the unused space instead of creating
  a giant purple rectangle.
*/

.reflection-composition {
  position: relative;

  width: 100%;

  min-height: 720px;

  padding:
    42px
    0;
}

/* =========================
   MAIN REFLECTION PANEL
   ========================= */

.reflection-card {
  position: relative;

  width: 76%;

  min-height: 630px;

  margin: 0 auto;

  padding:
    clamp(
      48px,
      5vw,
      76px
    );

  background:
    rgba(212, 198, 224, 0.95);

  border:
    2px solid #171717;

  box-shadow:
    8px 8px 0 #171717;
}

.reflection-copy {
  width: min(
    790px,
    100%
  );

  margin: 0 auto;
}

.reflection-copy p {
  margin:
    0
    0
    26px;

  font-size:
    clamp(
      1rem,
      1.15vw,
      1.12rem
    );

  line-height: 1.8;
}

.reflection-copy p:last-child {
  margin-bottom: 0;
}

/* =========================
   PHOTO TABS
   ========================= */

/*
  Instead of filling the entire corners with
  purple, each image gets only enough purple
  around it to look attached to the reflection.
*/

.photo-tab {
  position: absolute;

  z-index: 3;

  width:
    clamp(
      175px,
      16vw,
      235px
    );

  padding: 12px;

  background:
    rgba(212, 198, 224, 0.95);

  border:
    2px solid #171717;

  box-shadow:
    7px 7px 0 #171717;
}

.photo-tab img {
  display: block;

  width: 100%;

  aspect-ratio: 1 / 1;

  object-fit: cover;
}

/*
  Both images use the same 48px inset
  from their respective outer edges.
*/

.monkey-tab {
  top: 48px;
  right: 48px;

  transform:
    rotate(7deg);
}

.me-tab {
  bottom: 48px;
  left: 48px;

  transform:
    rotate(-7deg);
}

/* =========================
   TABLET
   ========================= */

@media (max-width: 1050px) {
  .section-header h2 {
    font-size:
      clamp(
        1.8rem,
        2.8vw,
        2.7rem
      );
  }

  .reflection-card {
    width: 78%;

    padding:
      44px
      54px;
  }

  .photo-tab {
    width:
      clamp(
        150px,
        18vw,
        195px
      );
  }

  .monkey-tab {
    top: 38px;
    right: 28px;
  }

  .me-tab {
    bottom: 38px;
    left: 28px;
  }
}

/* =========================
   MOBILE
   ========================= */

@media (max-width: 760px) {
  .final-reflection {
    padding:
      84px
      var(--page-padding)
      70px;
  }

  .section-header {
    margin-bottom: 24px;

    padding: 18px;

    box-shadow:
      5px 5px 0 #171717;
  }

  .section-header h2 {
    font-size:
      clamp(
        2rem,
        8vw,
        3rem
      );

    white-space: normal;
  }

  .reflection-composition {
    display: flex;
    flex-wrap: wrap;

    gap: 18px;

    min-height: 0;

    padding: 0;
  }

  .reflection-card {
    order: 1;

    width: 100%;

    min-height: 0;

    padding:
      26px
      20px;

    box-shadow:
      5px 5px 0 #171717;
  }

  .reflection-copy {
    width: 100%;
  }

  .reflection-copy p {
    font-size: 0.96rem;

    line-height: 1.7;
  }

  /*
    On phones the images stop overlapping
    so they don't cover any text.
  */

  .photo-tab {
    position: relative;

    top: auto;
    right: auto;
    bottom: auto;
    left: auto;

    width:
      calc(50% - 9px);

    padding: 8px;

    box-shadow:
      5px 5px 0 #171717;
  }

  .me-tab {
    order: 2;

    transform:
      rotate(-4deg);
  }

  .monkey-tab {
    order: 3;

    transform:
      rotate(4deg);
  }
}
</style>