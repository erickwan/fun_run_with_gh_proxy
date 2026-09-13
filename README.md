# Peninsula Bridge Fun Run 2026 — GitHub Pages site

The public registration form (`index.html`, with the `?pb=1` family variant) and the organizer dashboard (`admin.html`) for the Peninsula Bridge Fun Run, hosted on GitHub Pages.

## Why this exists

The primary deployment runs on Google Apps Script, but some visitors who are signed in to multiple Google accounts (especially school/work accounts) hit a Drive "unable to open the file" error on `script.google.com` URLs. These static copies call the same Apps Script backend through its JSON API (`doPost`) over anonymous `fetch()` — no Google session is involved, so every visitor gets the form.

## How it's wired

- `SCRIPT_URL` near the top of the script in both files points at the Apps Script web app `/exec` URL.
- Requests are JSON over POST (`{action: 'submit'|'status'|'adminStats', ...}`); responses are `{ok, result|error}`.
- Bib numbers, the shirt counter, the category rules, and the admin password all stay server-side in the Apps Script project — this repo is front-end only and safe to be public.

## Updating

These files are copies of `Index.html` / `Admin.html` from the private `peninsula-bridge-fun-run` repo, with `SCRIPT_URL` filled in. When those change: re-copy, re-set `SCRIPT_URL`, commit.

## URLs

- Registration: `https://erickwan.github.io/fun_run_with_gh_proxy/`
- Peninsula Bridge families: `https://erickwan.github.io/fun_run_with_gh_proxy/?pb=1`
- Organizer dashboard: `https://erickwan.github.io/fun_run_with_gh_proxy/admin.html`
