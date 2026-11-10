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
              Before taking Art Appreciation, I mostly thought of art as the finished product: a drawing, a painting, a song, or a performance. I also never really thought of myself as an artist. Looking back at this portfolio, I realized that art is not only about what is produced in the end, but also about the effort, choices, mistakes, and experiences behind it.

            </p>

            <p>
              One pattern I noticed is that I rarely create something for no reason. I usually become interested in something first, then that interest pushes me to make something. I drew because I liked a character, painted because I was curious about Picasso’s style, learned a keyboard piece because it came from an anime I liked, and tried rapping because I wanted to see if I could actually perform the song. Even origami started because I simply found something that looked cool.

            </p>

            <p>
              Some activities also surprised me by being much harder than they looked. Origami became a test of patience, playing the keyboard required weeks of practice, and rapping taught me that breathing and timing mattered just as much as speaking quickly. These experiences made me appreciate the amount of skill behind things that can look simple when done well.

            </p>

            <p>
              If a stranger explored this portfolio, they might think I am constantly making art, but that isn't really true. I can go years without drawing or practicing some of these skills. What this portfolio represents more accurately is that when something genuinely catches my interest, I can become deeply invested in it.

            </p>

            <p>
              Looking forward, I still don't think I am becoming one specific kind of artist. I would rather keep art as something I can return to whenever an idea, character, song, story, or challenge makes me want to create again. Art may not become the center of my life, but I think it will continue to be one of the ways I explore my interests, express what I care about, and discover things I didn't expect myself to be able to do.

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
    990px,
    100%
  );

  margin: 0 auto;
}
.reflection-copy p {
  margin:
    0
    0
    24px;

  line-height: 1.65;

  text-align: justify;
  text-indent: 2em;
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
  top: 28px;
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