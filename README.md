# Illuminate

The magazine for Vanderbilt staff, published by People, Culture and Belonging. This repo replaces the FlipHTML5 flipbook with a web-native magazine.

**Current issue:** Vol 3.11, November 2026 (prototype)

## What it is

One static page. No framework, no build step, no backend.

- `index.html` holds the cover, the home page and every story. Inline CSS and JS.
- `img/` holds the issue photos and the watercolor cover art.
- `assets/` holds the FLH brand fonts (Libre Caslon, Inter, Antonio), the VU lockup and the favicon.

The issue reads as one continuous magazine of 16 spreads. On desktop the right page turns over the spine to the next spread. On phones each page is a screen you scroll, then swipe.

- Turn with the arrow keys, Page Up and Down, the space bar, the scroll wheel, a swipe, or the side arrows.
- The scrubber along the bottom jumps to any spread. **All pages** opens a thumbnail grid.
- Every spread has a deep link by its id: `#cover`, `#contents`, `#cover-story`, `#staff-stories`, `#fall-assembly`, `#veterans`, `#leadership-redefined`, `#gratitude`, `#acorn`, `#around-campus`, `#holiday`, `#back-cover`.
- Running heads and page numbers are added by script from each page's `data-run`. The contents page numbers come from the same count.

## Motion

Built from two MotionSites designs (Golden Portal and Digital Experiences), adapted to the FLH brand.

- An ambient loop of golden clouds and doves (`media/golden-clouds.mp4`, 280 KB) sits behind the book. It shows full strength on the cover and back cover and dims behind the interior spreads.
- The cover opens with a blur-in masthead, staggered cover lines and a spinning-in seal. It tilts toward the pointer, the art drifts slowly, and a gold sheen crosses it.
- After each page turn lands, the type develops in: headlines word by word with a blur, then kickers, deks and body. Photos settle from a slight zoom. Full-bleed photos drift slowly. Statistics count up.
- The top bar, buttons, arrows and scrubber use a gold-edged liquid-glass treatment.
- Everything stops under the reduced-motion setting, and the video is replaced by its still frame.

## Run it locally

```
python3 -m http.server 8000
```

Then open http://localhost:8000.

## Deploy

Any static host works. Point GitHub Pages or Vercel at the repo root. No build command, output directory is `/`.

## Design rules

Built to the FLH house style from the vu-course-builder skill:

- Black `#1C1C1C`, white, Flat Gold `#CFAE70`, Oak `#946E24` where gold sits on white. Cream `#F5F3EF` for bands.
- Headlines in Libre Caslon with one italic word, ending in a period. Body in Inter. Labels in Antonio caps.
- No em or en dashes anywhere in the copy.
- WCAG 2.2 AA: skip link, landmarks, visible focus, focus moves to the story heading on open, reduced motion honored, reflows to 320px.

## Making a new issue

1. Swap the cover art in `img/` and the cover text in the `.cover` section.
2. Each spread is a `<section class="spread">` with two `.pg` pages (`left` and `right`). A full-bleed photo page is `.pg.bleed`. Give text pages a `data-run` for the running head.
3. Fit each page to one screen at 1440x900. Split long stories across spreads (see Staff Stories). Pages scroll internally on smaller screens as a fallback.
4. Update the `TOC` array for the contents page and the `E` array for Around Campus.
5. Update the volume and month in the top bar, the cover strip, the running heads and the back cover.
