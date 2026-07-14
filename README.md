# Portfolio

Personal engineering portfolio, built with plain HTML/CSS (no build step,
no dependencies). Hosted on GitHub Pages.

## Structure

```
index.html       All page content — header, hero, and one <section class="company-group">
                  per company, each holding <article class="project"> blocks.
css/style.css     All styling, colors, and layout.
images/           Project photos/drawings. Currently holds only placeholder.svg.
```

Each project follows a repeating **text → image → text → image** pattern.
That structure lives entirely in `index.html`; there's no template engine
or data file to keep in sync.

## Adding or editing a project

1. Open `index.html` and find the company's `<section class="company-group ...">`.
2. Copy an existing `<article class="project">...</article>` block (there's
   a commented "PROJECT TEMPLATE" note above the first one in each pattern).
3. Update the title, the two (or more) `<p class="project__text">` blocks,
   and the `<figure class="project__image">` blocks.
4. Add or remove `project__text` / `project__image` pairs to make the
   section longer or shorter — the pattern just keeps alternating.

## Adding images

Drop image files into `images/` (JPG/PNG/WebP all work), then point the
`<img src="...">` in the relevant `<figure>` at the new file, e.g.:

```html
<img src="images/nevados-tracker-1.jpg" alt="Tracker row assembly" />
```

Until you have a real photo for a slot, leave it pointing at
`images/placeholder.svg` — it renders as a labeled gray box so the layout
stays intact.

Images are cropped to a consistent aspect ratio automatically (see
`.project__image img` in `css/style.css`) — no need to pre-crop, just use
a reasonably high-resolution source.

## Adding a whole new company / section group

Copy an entire `<section class="company-group company-group--...">` block,
give it a new `id` (used by the nav bar anchor links at the top of
`index.html`), and add a matching `<a href="#your-id">` link in `.site-nav`
in the `<header>`.

## Previewing locally

From the `portfolio/` directory:

```
python3 -m http.server 4173
```

Then open http://localhost:4173 in a browser.

## Publishing changes

This repo is served by GitHub Pages directly from the `main` branch, so any
push to `main` updates the live site (usually within a minute or two):

```
git add -A
git commit -m "Update project X"
git push
```
