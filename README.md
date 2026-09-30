# dilankaraguler.github.io

Personal academic website of Dilan Karaguler, built with the [al-folio](https://github.com/alshedivat/al-folio) Jekyll template (v1.x).
Live at <https://dilankaraguler.github.io>. See [UPLOAD.md](UPLOAD.md) for how to publish it.

## Where things live

| What                               | File                                                         |
| ---------------------------------- | ------------------------------------------------------------ |
| Name, site description, SEO keywords | `_config.yml` (top of the file)                            |
| About page (bio, photo, contact)   | `_pages/about.md`, photo in `assets/img/prof_pic.jpg`        |
| News on the About page             | one file per item in `_news/`                                |
| Publications                       | `_bibliography/papers.bib` (in-prep items: `_pages/publications.md`) |
| Research, talks, posters           | `_pages/research.md`                                         |
| Project cards                      | `_projects/*.md` (each links to its GitHub repo)             |
| Teaching                           | `_pages/teaching.md`                                         |
| Industry experience and skills     | `_pages/industry.md`                                         |
| CV page and PDFs                   | `_pages/cv.md`, PDFs in `assets/pdf/`                        |
| Social icons (email, Scholar, GitHub, LinkedIn, ORCID) | `_data/socials.yml`                      |
| Order of pages in the top menu     | `nav_order:` in each page's front matter                     |

## Changing the accent color

The accent (links, headings, highlights) is set in **`_sass/_themes.scss`**. Search for `ACCENT`:
there is one hex value for light mode (currently `#2f6f8f`, a calm slate teal) and one for dark mode
(currently `#7db8d4`). Change both lines in each block (`--global-theme-color` and `--global-hover-color`).

This file is a local copy of the theme gem's `_themes.scss`; if you ever upgrade the `al_folio_core` gem,
run `bundle exec al-folio upgrade overrides audit` to see whether it needs refreshing.

## CV PDFs

The PDFs in `assets/pdf/` are **website versions** built from the LaTeX CV in the parent `website/` folder
via `web_cv/*.tex`: same content, but with no phone number and no references' contact details.
To rebuild after editing the CV, run from the `website/` folder:

```bash
for f in web_cv/cv_*.tex; do pdflatex -output-directory=web_cv/out "$f"; done
cp web_cv/out/cv_*.pdf DilanKaraguler.github.io/assets/pdf/
```

## Adding things

- **News item:** copy a file in `_news/`, change the `date:` and the sentence.
- **Paper:** add a BibTeX entry to `_bibliography/papers.bib`. Useful extra fields: `arxiv`, `doi`, `pdf`, `code`, `slides`, `selected = {true}` (shows it on the About page).
- **Project:** copy a file in `_projects/`, change `title`, `description`, `importance` (order) and `redirect` (link).

## Local preview (optional)

Needs Ruby 3.x (macOS's built-in Ruby 2.6 is too old; `brew install ruby imagemagick`), then:

```bash
bundle install
bundle exec jekyll serve   # open http://localhost:4000
```
