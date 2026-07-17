# Derrick Watson — QA Portfolio

Static portfolio site. No build step, no dependencies — plain HTML, CSS, and vanilla JS.

## Deploy to GitHub Pages

### Option A — user site (clean URL: `username.github.io`)

1. Create a **public** repo named exactly `USERNAME.github.io` (use your real GitHub username).
2. Upload `index.html`, `derrick-watson.jpg`, `.nojekyll`, and `README.md` to the repo root.
3. Go to **Settings → Pages**.
4. Under **Build and deployment → Source**, choose **Deploy from a branch**.
5. Set branch to `main` and folder to `/ (root)`. Save.
6. Wait 1–2 minutes. Site is live at `https://USERNAME.github.io/`

### Option B — project site (URL: `username.github.io/portfolio`)

Same steps, but name the repo whatever you like (e.g. `portfolio`). The site
publishes to `https://USERNAME.github.io/portfolio/`.

### Via command line

```bash
git init
git add .
git commit -m "Portfolio site"
git branch -M main
git remote add origin https://github.com/USERNAME/USERNAME.github.io.git
git push -u origin main
```

Then enable Pages under Settings → Pages as described above.

## Before you publish

- [ ] Replace `USERNAME` in the `canonical`, `og:url`, `og:image`, and `twitter:image` meta tags in `index.html`
- [ ] Point the GitHub button at your real profile/repo: search for `.repo-cta` and replace
      `https://github.com/USERNAME`
- [ ] Replace the four placeholder cards in the `WORK` array with real projects, and add
      `link:` URLs as repos become public
- [ ] Replace the placeholder `247` cases-passing figure (search for `const total = 247`) with a real number, or remove that stat block
- [ ] Confirm the leadership stats (15+ led, 6 yrs managing, 8 yrs QA delivery) match how you'd describe them in an interview
- [ ] Confirm the "7+ years" figure reads the way you want (counts from the 2018 trainee role)

## About the photo

The headshot is **embedded directly in `index.html`** as a base64 data URI, so the page
renders correctly even if you open the HTML file on its own. You do not need the image
file for the photo to display.

`derrick-watson.jpg` is still included and should be uploaded to the repo root — it is
used for the social preview (`og:image` / `twitter:image`), since link-preview crawlers
can't read embedded data URIs.

To swap the photo, replace the `src="data:image/jpeg;base64,..."` value on the
`.heroshot img` tag, and replace `derrick-watson.jpg`.

## Editing content

All content lives in data arrays in the `<script>` block at the bottom of `index.html`:

- `SPECS` — the skills / "specs under test" grid
- `TOOLS_CURRENT` — toolchain marked "IN USE"
- `TOOLS_GROWING` — toolchain marked "EXPANDING" (Python, Selenium, etc.)
- `WORK` — project cards in the "selected work" section. Each object:
  - `t` title, `s` description, `tags` array of pill labels
  - `status`: `"LIVE"` (green badge) | `"WIP"` (amber "IN PROGRESS") | `""` (no badge)
  - `link`: a URL makes the whole card clickable with an ↗ cue; `""` renders it as a
    plain non-clickable card (no misleading hover), so placeholders look intentional
- `LEAD` — leadership evidence bullets in the leadership section
- `ASSERTIONS` — work history entries. Two fields drive the card's visual tier:
  - `status`: `"RUNNING"` → current role (large amber card w/ CURRENT tab), `"LED"` → leadership role (blue left rule), `"PASS"` → standard
  - `tier`: add `tier:"prior"` to de-emphasize a pre-QA role (dimmed, compact)
- `CERTS` — credentials cards. Each is an object: `{t, s, org, yr}` (title, description, issuing org, badge text)

The **approach** section prose is plain HTML in the `<section id="approach">` block.

Edit those arrays rather than the markup; the page renders from them.

## Custom domain (optional)

1. Add a file named `CNAME` at the repo root containing just your domain, e.g. `derrickwatson.com`
2. At your DNS registrar, add four `A` records for the apex domain pointing to:
   `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
3. In Settings → Pages, enter the domain and enable **Enforce HTTPS**.
