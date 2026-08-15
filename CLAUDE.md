# R3 Media Production website

Static site, no build step. This folder IS the git repo root; it deploys to
GitHub Pages on every push to `main`.

Lives at `~/Documents/*R3 Media Productions/07_Websites/R3Mediapro Website/`
(moved under `07_Websites` Aug 15 2026, alongside the EVP site). Source brand
assets are in `../../../06_Brand Assets/`.

## Repo (moved Aug 2026 — do not use the old URL)

    https://github.com/R3MediaPro/r3mediapro-website

It used to live under `Downstage-Systems`. Repos for the R3 family now sit in
the **R3MediaPro** organization; Downstage Systems repos stayed on the
personal `Downstage-Systems` account. If a remote still points at the old
owner, fix it with:

    git remote set-url origin https://github.com/R3MediaPro/r3mediapro-website.git

## Deploying

    git add -A && git commit -m "..." && git push

Live at https://r3mediapro.com within a minute or two. `CNAME` in this folder
holds the custom domain — never delete it.

## Layout

- `index.html`, `services.html`, `portfolio.html`, `about.html`, `contact.html`
- `portal/` — client delivery portal. `index.html` takes an access code and
  forwards to `event.html?event=<code>`, which reads live session status from
  the Apps Script API shared with the Video Editing Tracker. Older one-off
  client pages are AES-encrypted standalone `<code>.html` files; they are
  **not editable** without the client's password, so regenerate them with
  `portal-generator.html` (one folder up, local-only, never commit it).
- `tracker/` — the internal Video Editing Tracker, copied in by `deploy.sh`
  from `~/Documents/*R3 Media Productions/Video Editing Tracker/`. Edit it
  there, not here.
- `assets/`, `css/styles.css`

## Gotchas

- This folder is inside iCloud Drive and is visible from a second Mac.
  **Run git from this Mac only** — concurrent git from two machines mid-sync
  can corrupt the repo.
- The contact form posts to Formspree `meeyyjpn` (shared with the EVP site,
  which tags its submissions with a hidden `brand` field).
- Client passwords and the portal log live OUTSIDE this repo on purpose.
  Nothing secret belongs in here — the repo is public.
