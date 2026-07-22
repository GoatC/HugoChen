# Hugo Chen — Personal Website

Static site. Pure HTML/JS, no build step. All paths are relative, so it works
from a repo sub-path (e.g. `username.github.io/HugoChen/`) or a custom domain.

## Files
- `index.html` — entry point (redirects to `Home.dc.html`)
- `Home.dc.html`, `About.dc.html`, `Work.dc.html` — the three pages
- `WorkGallery.dc.html` — photo-gallery component used by the Work page
- `support.js`, `image-slot.js` — runtime the pages load
- `uploads/` — fonts + personal photo
- `.image-slots.state.json` — stored gallery photos (About / Work)
- `.nojekyll` — REQUIRED: tells GitHub Pages to serve the dotfile
  `.image-slots.state.json` (Jekyll hides files starting with `.`).
  Without it the gallery photos will not load.

## Deploy to GitHub Pages
From this folder:

```bash
git init
git add -A                 # -A so .nojekyll and the .json sidecar are included
git commit -m "Publish site"
git branch -M main
git remote add origin https://github.com/GoatC/HugoChen.git
git push -u origin main
```

Then on GitHub: **Settings → Pages → Build and deployment → Source: Deploy from
a branch → Branch: `main` / `(root)` → Save**.

Live at: `https://goatc.github.io/HugoChen/`

## Custom domain
Point your domain's DNS to GitHub Pages, then set it under
**Settings → Pages → Custom domain**. GitHub writes a `CNAME` file into the
repo. Keep all the files above; nothing else needs to change.

## Notes
- Gallery photos are read-only on the live site. To change them, upload in the
  editor, then re-export this `dist/` folder and push again.
- Committing dotfiles: `git add -A` (or `git add .nojekyll .image-slots.state.json`)
  — a plain `git add *` skips dotfiles.
