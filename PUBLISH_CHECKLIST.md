# Public Repo Publish Checklist (No Source Code)

Use this checklist to publish a showcase-only GitHub repository while keeping implementation private.

## 1) Create a new empty folder for public repo

Do **not** publish from your full project root.

Create a new folder, for example:

- `fairlend-showcase-public/`

Copy only the following from `PUBLIC_SHOWCASE_REPO/`:

- `README.md`
- `SYSTEM_ARCHITECTURE.md`
- demo media files (screenshots/video) in `media/`

## 2) Add media assets

In your public repo folder, create:

- `media/login.png`
- `media/dashboard.png`
- `media/mitigation.png`
- `media/fairlend-demo.mp4` (optional if not using YouTube)

Then update links in `README.md`.

## 3) Sanity check for accidental leaks

Before pushing:

- Ensure there is **no** `backend/` or `frontend/` code
- Ensure there are **no** `.env*`, keys, or credentials
- Ensure there are **no** notebooks, prompts, model configs, or scripts
- Ensure there are **no** private dataset files

## 4) Initialize and push to GitHub

```bash
git init
git add .
git commit -m "Initial public showcase for FairLend"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-public-repo>.git
git push -u origin main
```

## 5) GitHub repo settings

- Set repository visibility to **Public**
- Add topics: `responsible-ai`, `fairness`, `genai`, `fintech`, `governance`
- Pin repo to your profile
- Add demo video link in repo About section

## 6) Optional legal note

If needed, add this disclaimer in `README.md`:

> This repository is a product showcase and intentionally excludes proprietary implementation details, source code, and internal algorithms.

