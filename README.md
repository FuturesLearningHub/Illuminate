# Illuminate

The magazine for Vanderbilt staff, published by People, Culture and Belonging. This repo replaces the FlipHTML5 flipbook with a web-native magazine.

**Current issue:** Vol 3.11, November 2026 (prototype)

## What it is

One static page. No framework, no build step, no backend.

- `index.html` holds the cover, the home page and every story. Inline CSS and JS.
- `img/` holds the issue photos and the watercolor cover art.
- `assets/` holds the FLH brand fonts (Libre Caslon, Inter, Antonio), the VU lockup and the favicon.

Stories open as their own view by hash: `#story-tina-soo`, `#story-leaders40`, and so on. Sections are plain anchors: `#people`, `#leadership`, `#wellbeing`, `#campus`.

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
2. Replace each `<article class="story">` with the new stories. Keep the `id="s-<slug>"` pattern and add the slug to `ORDER` in the script.
3. Update the `E` events array for Around Campus.
4. Update the volume and month in the top bar, the masthead strip and the footer.
