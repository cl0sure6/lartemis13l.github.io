# Adilkhan Salkimbayev — Research Portfolio

A [Hugo](https://gohugo.io/) site (theme: [Ananke](https://github.com/gohugo-ananke/ananke))
for projects, publications, and preprints.

## Edit the content

| What | File |
| --- | --- |
| Homepage / bio | `content/_index.md` |
| Name & tagline | `title` and `[params].description` in `hugo.toml` |
| Projects | `content/projects/` (one `.md` file per project) |
| Publications & preprints | `content/publications/` (one `.md` file per paper) |
| CV page | `content/cv.md` |
| Nav menu & social links | `hugo.toml` |

**Hosted files:**

- CV PDF → put it at `static/files/cv.pdf` (linked from the CV page).
- Preprint PDFs → put them in `static/preprints/`, e.g. `static/preprints/my-paper.pdf`
  becomes available at `/preprints/my-paper.pdf`.

## Personalize first (quick checklist)

- [ ] Replace every `[bracketed placeholder]` in `content/`.
- [ ] Set your tagline (`description`) and confirm your name (`title`) in `hugo.toml`.
- [ ] Confirm/replace the contact email in `hugo.toml` (`params.ananke.social.email`).
- [ ] (Optional) Enable LinkedIn / Google Scholar / ORCID — uncomment the blocks in `hugo.toml`.
- [ ] Replace the two example projects and the example publication with your own.
- [ ] Add your `cv.pdf` and any preprint PDFs.

## Run locally

```bash
hugo server -D      # http://localhost:1313/ , -D shows drafts
```

## Deploy (GitHub Pages)

A workflow at `.github/workflows/hugo.yml` builds and deploys on every push.

1. Create a GitHub repo named **`lArtemis13l.github.io`** (empty — no README).
2. Push this project:
   ```bash
   git remote add origin https://github.com/lArtemis13l/lArtemis13l.github.io.git
   git push -u origin master
   ```
3. In the repo: **Settings → Pages → Build and deployment → Source: GitHub Actions**.
4. The site goes live at **https://lartemis13l.github.io/** (served in lowercase).

Update `HUGO_VERSION` in the workflow when you upgrade Hugo locally.
