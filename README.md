# Art, art, art, and more art!

Vue 3 + Vite starter focused on the animated collage background.

## Install

```bash
npm install
npm run dev
```

## Add your 30 images

Put them inside:

```text
public/background/
```

The starter already expects your existing naming pattern:

```text
painting_1.webp ... painting_5.webp
origami_1.webp ... origami_5.webp
drawing_1.webp ... drawing_5.webp
rapping_1.webp ... rapping_5.webp
piano_1.webp ... piano_5.webp
theater_1.webp ... theater_5.webp
```

If any filename differs, edit `categories` / `sourceImages` in `src/components/CollageBackground.vue`.

## What is already implemented

- shuffle on every load
- dense patchwork grid
- mixed tile shapes
- one animated collage track rather than 30 independent animations
- duplicated track for an infinite loop
- slight diagonal drift
- alternating grayscale/color
- slow grayscale/color swaps
- pause/resume control
- `prefers-reduced-motion`
- mobile-specific column count and slower animation
- translucent readability overlay

## Performance

Your 1600px WebP images are more than enough for this background. If the full collage still feels heavy, 1200px at WebP quality 76–80 is also fine.
