# giedriusr.lt

Personal website of Giedrius Rimkus. Plain HTML and CSS, no build step, hosted on GitHub Pages.

## Layout

| Path | What it is |
| --- | --- |
| `index.html` | The one and only page |
| `css/style.css` | Styles: warm palette, light/dark via `prefers-color-scheme` |
| `img/og.png` | Social share image (1200×630) |
| `favicon.svg`, `favicon.ico` | Icons |
| `CNAME`, `google*.html` | Domain + Search Console verification, leave as is |
| `bin/` | Helper scripts (see below) |
| `.github/workflows/` | Deploy and PR preview automation |

## Previewing changes

**Locally** (Ruby's built-in server, no dependencies):

```sh
bin/serve            # http://localhost:4000
bin/screenshot       # desktop light/dark + mobile PNGs into test-results/ (needs Node)
```

**On a pull request.** Every PR gets:

1. A live preview at `https://giedriusr.lt/pr-preview/pr-<N>/`, posted as a sticky comment on the PR
   and removed when the PR closes (`rossjrw/pr-preview-action`).
2. Desktop (light + dark) and mobile screenshots attached to the workflow run as an artifact.
3. HTML validation (`html-validate`).

**Going live.** Merging to `master` runs `deploy.yml`, which publishes the site to the `gh-pages`
branch. Open previews under `pr-preview/` survive production deploys.

### One-time repository settings (needed for the live preview URLs)

1. Settings → Actions → General → Workflow permissions → **Read and write permissions**.
2. Settings → Pages → Build and deployment → Source: **Deploy from a branch** → `gh-pages` / `(root)`.
   Do this after `deploy.yml` has run once so the branch exists.

Until step 2 is done, Pages keeps serving `master` directly (as today). Screenshots and validation
work regardless.

## Editing content

Everything lives in `index.html` in reading order: hero → About → Highlights → Career → Toolbox → Contact.
Career entries are a `<li class="timeline-item">` each; add `is-current` to the one that is ongoing.
Colours are CSS custom properties at the top of `css/style.css`.
