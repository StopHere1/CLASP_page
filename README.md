# CLASP_page

Project page for **CLASP: A Cluster-Level Autonomous Selective Picking Robot with a
Soft Rolling-Band Gripper for Fresh-Market Blueberry Harvesting**
([arXiv:2609.18051](https://arxiv.org/abs/2609.18051)).

Style adapted from the [Nerfies](https://github.com/nerfies/nerfies.github.io) template
via [paper-website](https://paper-website.github.io/).

## Layout

| Path | Purpose |
| --- | --- |
| `index.html` | The whole page. Bulma / Font Awesome / Academicons are loaded from CDN; no build step. |
| `static/css/index.css` | Page styles (Nerfies-derived). |
| `static/images/` | Paper figures (`fig*.jpg`, extracted from the arXiv PDF) and field photos. |
| `static/paper/` | The paper PDF served by the **Paper** button. |
| `.nojekyll` | Tells GitHub Pages to serve files as-is instead of running Jekyll. |

## Adding the demo video

`index.html` has a hatched **Demo video coming soon** placeholder in the `#video`
section. The HTML comment directly above it gives the two drop-in replacements:

- a YouTube embed (`<div class="publication-video"><iframe …></iframe></div>`), or
- a local file (`<video class="demo-video" …>` pointing at `static/videos/clasp_demo.mp4`).

Delete the `.video-placeholder` block once the real video is in.

## Publishing

Settings → Pages → Build and deployment → **Deploy from a branch**, branch `main`,
folder `/ (root)`. Push to `main` and the page redeploys within a minute or so.
