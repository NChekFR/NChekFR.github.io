# NChekFR.github.io

Personal website of **Nikita Chekhovskoy**, a Computer Science and Mathematics student at the University of Toronto. It collects my projects, experience, resume, and handwritten lecture notes in one place.

**Live site: [nchekfr.github.io](https://NChekFR.github.io/)**

I'm looking for software engineering internships and math or theoretical CS research opportunities for Summer 2027.

## What's on the site

- **About:** education, coursework, awards, and skills.
- **Projects:** hackathon and team projects, each with a short write-up and links to code, demos, or slides:
  SecondChance, RateMyResume, Blocked In, an Online Casino Prototype, and a Networked Battleship Game.
- **Experience:** leadership, tutoring, and teaching roles.
- **Notes:** my handwritten lecture notes in group theory, complex analysis (in progress), analysis II, and topology.
  Each course has a lecture index that links straight to the right page of the PDF.
- **Resume:** a downloadable PDF.

## How it's built

The site is a small static page with no build step and no framework.

- **HTML, CSS, and a little JavaScript.** Everything is in `index.html`, `style.css`, and `script.js`.
- **Light and dark themes.** The site follows the visitor's system setting, and the toggle in the header overrides it (the choice is remembered in the browser).
- **A four-color palette** defined as CSS variables at the top of `style.css`. Changing those four lines re-themes the whole site. With the current palette, text contrast meets the WCAG AA threshold in both modes.
- **Responsive and accessible.** It works on phones, has a skip-to-content link, visible focus outlines, respects reduced-motion settings, and has a clean print layout.
- **KaTeX** (loaded from a CDN) typesets the math in the lecture titles.
- **Hosted on GitHub Pages**, served from the `main` branch.

## Repository layout

```
.
├── index.html        # all page content
├── style.css         # theme and layout
├── script.js         # theme toggle, active nav link, math rendering
├── files/
│   ├── resume.pdf
│   ├── slides.pdf    # slides for the casino project
│   └── notes/        # lecture-note PDFs
├── images/           # social preview image (og.png) and project screenshots
├── .nojekyll         # tells GitHub Pages to serve files as they are
└── README.md
```

## Run it locally

You need Python 3 (any recent version). From the repository folder:

```
python -m http.server 8000
```

On Windows, use `py -m http.server 8000` if `python` isn't recognized. Then open `http://127.0.0.1:8000` in a browser. Press `Ctrl+C` in the terminal to stop the server.

## Deploy

Pushing to `main` publishes the site. In the repository's **Settings → Pages**, the source is set to **Deploy from a branch**, using `main` and the `/ (root)` folder.

## Maintaining the notes

The notes are handwritten in OneNote and published as PDFs, with a bookmark outline in each file and a matching lecture index on the site. The workflow is:

1. Export each course's section from OneNote to PDF.
2. Shrink the PDF with [Ghostscript](https://ghostscript.com/), which flattens each page to a moderate-resolution image:
   `gs -sDEVICE=pdfimage24 -r<dpi> -dNOPAUSE -dBATCH "-sOutputFile=small.pdf" "big.pdf"`
3. Add the chapter bookmarks with a small `pdfmark` file, one line per lecture:
   `[ /Title (Day 1: Topic) /Page 1 /View [/Fit] /OUT pdfmark`
   and run `gs -sDEVICE=pdfwrite -dNOPAUSE -dBATCH "-sOutputFile=notes.pdf" "small.pdf" "bookmarks.txt"`.
4. Put the PDF in `files/notes/` and update that course's lecture index in `index.html`. Links use `file.pdf#page=N`.

Whenever I re-export a course, the page numbers can shift, so the bookmarks and the lecture index need to be regenerated together.

## About the notes

- The notes are **my own personal lecture notes**, written for studying. They are not official course materials and aren't endorsed by any instructor or by the University of Toronto.
- They are based on lectures and the standard references for each course, and **they may contain mistakes**.
- If you're an instructor or author and would like something changed or taken down, please get in touch through the contact links on the site.

## Contact

The easiest way to reach me is through the [Contact section of the site](https://NChekFR.github.io/#contact), or on [LinkedIn](https://www.linkedin.com/in/nikita-chekhovskoy) and [GitHub](https://github.com/NChekFR).