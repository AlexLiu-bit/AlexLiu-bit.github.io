# AlexLiu-bit.github.io

Source for my personal academic homepage: <https://alexliu-bit.github.io/>

Static HTML with no build step — GitHub Pages serves these files directly.
Edit, commit, push; the live site updates in about a minute.

## Layout

```
index.html            the whole homepage
stylesheet.css        fonts and the handful of rules the page uses
images/               profile photo, paper thumbnails, favicon/
data/                 CV.pdf and .bib files
project-template/     copy this folder to make a per-paper project page
```

## Adding a paper

Open `index.html`, find the publications table, and copy one of the three
labelled row templates:

| Template | Thumbnail behavior | Use when |
| --- | --- | --- |
| **A** | static image | you have no animation |
| **B** | two images cross-fade on hover | before/after comparisons |
| **C** | image fades into a looping video on hover | anything with motion |

Templates B and C need a unique short name per paper — the comment above each
one lists every occurrence to rename. To highlight a paper, add
`bgcolor="#ffffd0"` to its `<tr>`.

Thumbnails are 160×160. Keep hover videos small (under ~200KB) since every one
of them loads when the page opens:

```bash
ffmpeg -i in.mov -vf scale=160:160 -c:v libx264 -pix_fmt yuv420p -crf 30 out.mp4
```

## Adding a project page

Copy `project-template/` to a new folder named after the paper, fill in the
`[TODO]`s, and link to it from the paper's row in `index.html`. It includes a
drag-to-compare video slider — that one needs a side-by-side source video, as
explained in the comment next to it.

## Local preview

```bash
python3 -m http.server 8000   # then open http://localhost:8000
```

## Credit

Built on [Jon Barron](https://jonbarron.info/)'s
[website template](https://github.com/jonbarron/jonbarron_website).
The project page template came to that repo from
[Michaël Gharbi](http://mgharbi.com/) and
[Ref-NeRF](https://dorverbin.github.io/refnerf).
