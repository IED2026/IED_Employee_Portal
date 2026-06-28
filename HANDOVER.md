# IED Employee Portal — Project Handover

## Repository
- **GitHub:** `IED2026/IED_Employee_Portal`
- **Live site (GitHub Pages):** https://ied2026.github.io/IED_Employee_Portal/
- **Deploy:** Pushing to the `main` branch auto-rebuilds GitHub Pages (legacy Pages, source = `main` / root). No build step.

## GitHub Access
- Requires a **fine-grained Personal Access Token** scoped **only** to this repo with **Contents: Read & Write**.
- ⚠️ **The token is NOT written in this file by design.** Hand it over through a secure channel (password manager share such as 1Password/Bitwarden), or simply add the person as a repo collaborator instead of sharing a token.
- Create/manage tokens: GitHub → Settings → Developer settings → Fine-grained tokens.
- Recommended: generate a **separate token per person** so each can be revoked independently.

## Tech Stack
- Single file: **`index.html`** — entire app (HTML + CSS + vanilla JS) in one file.
- **No framework, no build step.**
- External libraries via CDN:
  - Leaflet (check-in/out map)
  - Font Awesome (icons)
  - Chart.js
  - Google Fonts: Fraunces (display serif) + Plus Jakarta Sans

## File Structure
```
IED_Employee_Portal/
├── index.html      # the whole application
└── HANDOVER.md     # this file
```

## Data Storage
- **No backend yet.** All data persists in the browser's **localStorage** (per-device, per-browser).
- Keys:
  - `ied_attendance_log` — daily check-in / check-out times
  - `ied_leave_data` — leave applications
  - `ied_recon_data` — reconciliation applications
- **Supabase:** not integrated in the code; no Supabase URL/key/config exists in this repo.
- For real multi-user data, a backend (e.g. Supabase) would need to be added.

## Current Features
- **Home:** live ticking clock; check-in / check-out with animated Leaflet map + GPS location (two-stage: fast cached fix, then high-accuracy refine) and reverse-geocoded address.
- **My Attendance:** year → month period picker; "This Month" shows the last 45 days (incl. today); pen icon opens the reconciliation form for that date.
- **Apply for Leave:** Annual / Casual leave only; click-to-open calendar date pickers; correct working-day count (Sat & Sun = weekend); submits to My Leave Applications.
- **My Leave Applications:** edit/delete for **pending** only; approved/rejected rows show locked icons with a red slash; includes rejected dummy rows; delete confirmation modal.
- **Reconciliation Application:** custom 12-hour AM/PM clock picker (drag the hand; In defaults to AM, Out defaults to PM); submitted entries appear in the list showing In/Out times.

## Working Notes
- Validate JS syntax before pushing: extract the inline `<script>` and run `node -c`.
- CSS sanity check: compare `{` vs `}` counts.
- GitHub Pages deploys automatically on push to `main`.
