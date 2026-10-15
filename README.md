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
| `static/images/` | Paper figures (`fig*.jpg`, extracted from the arXiv PDF), field photos, and the video poster frame. |
| `static/paper/` | The paper PDF served by the **Paper** button. |
| `static/videos/` | The demo video (`clasp_demo.mp4`). |
| `.nojekyll` | Tells GitHub Pages to serve files as-is instead of running Jekyll. |

## The demo video

`static/videos/clasp_demo.mp4` (43 MB, 1280×720, 3:31) is played by the `<video>`
element in the `#video` section, with `static/images/demo_poster.jpg` as its poster.

**Size matters here.** GitHub refuses any file over 100 MB and warns above 50 MB, and
every version you commit stays in the repo's history forever. The source recording was
245 MB, so it was re-encoded down with ffmpeg:

```bash
ffmpeg -i source.mp4 -c:v libx264 -preset veryslow -crf 32 \
  -profile:v high -level 4.0 -pix_fmt yuv420p \
  -vf "hqdn3d=4:4:9:9,scale=1280:-2" \
  -c:a aac -b:a 96k -ac 2 -movflags +faststart \
  static/videos/clasp_demo.mp4
```

- `-crf` is the quality dial: lower is better and bigger (23 ≈ visually lossless, 32 is
  what we used, 34+ starts to soften small on-screen text). Re-run with a different
  value to trade size against quality.
- `hqdn3d` denoises — field foliage is grainy and grain is expensive to encode.
- `+faststart` moves the index to the front of the file so playback can begin before
  the whole file downloads.

To regenerate the poster frame (frame 4500 here — pick any frame you like):

```bash
ffmpeg -i static/videos/clasp_demo.mp4 -vf "select=eq(n\,4500)" -frames:v 1 -q:v 3 static/images/demo_poster.jpg
```

### Using YouTube instead

If the video grows or you want adaptive streaming, upload it to YouTube and replace the
`<video>` element with the embed given in the HTML comment just above it. That drops the
43 MB from the repo entirely. The `.video-placeholder` CSS class is still in
`static/css/index.css` if you ever need the "coming soon" box back.

## Publishing

Settings → Pages → Build and deployment → **Deploy from a branch**, branch `main`,
folder `/ (root)`. Push to `main` and the page redeploys within a minute or so.
