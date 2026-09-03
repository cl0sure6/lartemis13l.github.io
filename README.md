# Adilkhan Salkimbayev — Research Portfolio

A [Hugo](https://gohugo.io/) site (theme: [Ananke](https://github.com/gohugo-ananke/ananke))
showcasing research projects, preprints, and a CV. Deploys to GitHub Pages at
**https://lartemis13l.github.io/**.

## Edit the content

| What | File |
| --- | --- |
| Homepage / bio | `content/_index.md` |
| Homepage tagline (the line under your name) | `description` in `content/_index.md` front matter |
| Your name | `title` in `hugo.toml` |
| Projects | `content/projects/` — one `.md` file per project |
| CV page | `content/cv.md` |
| Nav menu & social/contact links | `hugo.toml` |
| Homepage card layout | `layouts/home.html`, `layouts/summary-with-image.html` |

**Hosted files:**

- CV PDF → `static/files/cv.pdf` (linked from the CV page).
- Preprint PDFs → `static/preprints/`, e.g. `static/preprints/my-paper.pdf` is served at
  `/preprints/my-paper.pdf` and linked from the relevant project page.

## Run locally

```bash
hugo server -D      # http://localhost:1313/  (-D shows drafts)
```

(`.claude/launch.json` also defines a `hugo` server config for the editor preview.)

## Deploy

The repo is connected to GitHub at **`cl0sure6/lartemis13l.github.io`**. Every push to
`master` runs `.github/workflows/hugo.yml`, which checks out the ananke submodule, builds
with Hugo extended, and publishes to Pages (~1 min):

```bash
git add -A && git commit -m "your message" && git push
```

One-time GitHub setting: **Settings → Pages → Build and deployment → Source: GitHub Actions**.

Bump `HUGO_VERSION` in the workflow when you upgrade Hugo locally (check with `hugo version`).

## When you're ready

- **Restore Publications:** uncomment the menu block in `hugo.toml` and recreate
  `content/publications/` — it was removed until the EAAI paper is under review. (The
  homepage tagline in `content/_index.md` still says "publications & preprints"; adjust to
  taste.)
- **More socials:** uncomment the LinkedIn / Google Scholar / ORCID blocks in `hugo.toml`
  and add each name to the `networks` list.
- **Contact email:** `params.ananke.social.email` currently uses your account address —
  swap it if you prefer another.
- **Custom domain:** the GitHub Student Pack free domain can point at this Pages site later.
