# FAA Reference Viewer

A self-hosted PDF viewer for embedding FAA handbook pages inside ThriveCart (or any LMS that accepts an iframe). Deep-links to an exact page, works on phones, no accounts, no monthly cost.

FAA handbooks are U.S. government works in the public domain — hosting them yourself is allowed.

---

## Part 1 — Put this on GitHub Pages (one time, ~5 minutes)

1. Go to **github.com → New repository**. Name it exactly `faa-viewer`, set it to **Public**, click **Create repository**.
2. Click **"uploading an existing file"** on the new repo's page.
3. Drag the **contents** of this folder in — `index.html`, the `lib` folder, the `pdfs` folder. (Drag the folders themselves; the uploader keeps the structure.) Click **Commit changes**.
4. Go to **Settings → Pages**. Under *Build and deployment*, set Source to **Deploy from a branch**, branch **main**, folder **/ (root)**. Save.
5. Wait 1–2 minutes. Your viewer is now live at:

   `https://YOUR-USERNAME.github.io/faa-viewer/`

   (If your GitHub account already serves a custom domain — e.g. clearcutcfi.com — project sites inherit it: `https://clearcutcfi.com/faa-viewer/`.)

**Verify it worked** before doing anything else. Open this in your browser:

```
https://YOUR-USERNAME.github.io/faa-viewer/index.html?file=pdfs/sample.pdf&page=2
```

You should land on a page that says **PAGE 2 — Deep links are working.** If you see that, everything downstream is guaranteed to work.

---

## Part 2 — Add the FAA handbooks (~5 minutes)

The FAA PDFs are not bundled here (keeps the repo light; you always get the current edition). Download the chapter files you need:

- **PHAK** (Pilot's Handbook of Aeronautical Knowledge): https://www.faa.gov/regulations_policies/handbooks_manuals/aviation/phak — download **Chapter 7: Aircraft Systems**
- **AFH** (Airplane Flying Handbook): https://www.faa.gov/regulations_policies/handbooks_manuals/aviation/airplane_handbook — download whichever chapters your lessons reference

Rename the downloads to short, predictable names before uploading — these exact names are what the snippets use:

| FAA file | Rename to |
|---|---|
| 09_phak_ch7.pdf | `phak-ch07.pdf` |
| 03_afh_ch2.pdf | `afh-ch02.pdf` |
| (chapter N of either book) | `phak-chNN.pdf` / `afh-chNN.pdf` |

Then in your repo: open the **pdfs** folder → **Add file → Upload files** → drag them in → Commit. Give Pages a minute to redeploy.

Use per-chapter files, not the full-book PDF — the full AFH is 260 MB and would make every lesson load slowly (GitHub also caps files at 100 MB).

---

## Part 3 — Embed in ThriveCart

In the lesson editor, add a **Custom HTML** element (not a text block) and paste:

```html
<iframe
  src="https://YOUR-USERNAME.github.io/faa-viewer/index.html?file=pdfs/phak-ch07.pdf&page=8&title=PHAK%20Ch.7%20-%20Carburetor%20Systems"
  width="100%" height="720" style="border:0;border-radius:8px;"
  loading="lazy" title="FAA Reference"></iframe>
```

Three things you change per lesson: the **file**, the **page**, and the **title** (URL-encoded: spaces become `%20`).

### If it looks broken

- **Grey/blank box in the ThriveCart editor** — normal. ThriveCart's admin editor often can't preview embeds; check the student-facing preview instead.
- **Blank box on the live page** — open the iframe's `src` URL directly in a browser tab. If it errors there, the viewer will tell you exactly what's wrong (usually a filename typo — names are case-sensitive).
- **"Couldn't load that PDF"** — the file isn't in `pdfs/` yet, or the name in the snippet doesn't match the uploaded name exactly.

### Page numbers: printed vs. physical

FAA chapters use printed numbers like "7-8". The viewer's `page=` parameter counts **physical pages of the chapter file**, and FAA chapter PDFs start right at page X-1, so printed **7-8 = page 8** of `phak-ch07.pdf`. If a future edition adds a cover sheet, everything shifts by one — open the viewer, find the right page with the toolbar, and use whatever number the readout shows.

See `snippets.md` for a ready-made cheat sheet.
