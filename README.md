# NYC Charter Explorer — Vital City

A searchable, sortable web version of the **Charter of the City of New York**, styled for Vital City and built to be embedded in an article or opened full screen. Includes the full Charter text, Charter Revision Commission tagging, per-section highlights and notes, and a link to a plain-language Q&A notebook.

**Live (full screen):** https://vitalcity-nyc.github.io/nyc-charter-explorer/
**Embed view:** add `?embed=1` to the URL.

This is the Vital City edition of the explorer (Halyard + Gascogne, Vital City palette, white/dark data-tool theming). The full data methodology — sourcing, currency, the Charter Revision Commission mapping and its verification — is in [`README-methodology.md`](README-methodology.md).

## Embedding in an article

The `?embed=1` view is a **compact, fixed-height search widget**: a search box plus results that scroll **inside** the box, so the article stays the same length no matter how much someone searches. Paste this into a Ghost HTML card (or any CMS that allows an iframe) — no script needed.

Use the wrapper version below: the fixed height lives on the outer `<div>` and the iframe fills it absolutely, so a theme's `iframe { height: … }` CSS can't squash or stretch it.

```html
<div style="position:relative;width:100%;height:600px;margin:1.5em 0;border:1px solid #dddddd;border-radius:10px;overflow:hidden;">
  <iframe
    src="https://vitalcity-nyc.github.io/nyc-charter-explorer/?embed=1"
    title="Search the New York City Charter"
    loading="lazy"
    style="position:absolute;inset:0;width:100%;height:100%;border:0;"></iframe>
</div>
```

- Adjust the wrapper `height:600px` to taste (≈560–680px works well). The widget fills the article width and scrolls internally; it never grows the page.
- The widget shows only the title, the search box, and the results. The chapter sidebar, filters, themes, notes/share controls and footer are kept for the full view to stay lightweight in-article.
- A **"Full screen"** button (top-right of the widget) opens the complete explorer in a new tab — chapter index, filters, light/dark themes, highlights and notes, export, and the Gemini Notebook link. The full view also shows a brief banner confirming it was expanded.

## What it does

- Full-text and title search with relevance ranking; `"quoted phrases"`, `-exclude` and `OR` operators.
- Sort by chapter, section number, most/least recently amended, length or relevance; filter by chapter or Charter Revision Commission.
- Per-section **Charter Revision Commission** tags (2018, 2019, 2024, 2025 passed proposals) with the added/amended/repealed action, independently verified against the official amendment text.
- Personal **highlights** (select any passage) and **notes**, saved privately in the browser, with backup/restore and inclusion in the text export.
- In-text cross-reference links, shareable section/passage links (copy, email, tweet) and a per-view text export.
- **"Ask the Charter a question"** links to a Gemini Notebook of the full Charter for plain-language Q&A.

## Files

- `index.html` — the explorer (single page; data bundled in `charter-data.js`, so it also works by double-click).
- `charter-data.js` / `charter-data.json` — the bundled Charter data with Charter Revision Commission tags.
- `fonts/GascogneTS-Light.ttf` — Vital City display serif (used for the § numerals). Halyard loads from Adobe Typekit.
- `data/` + `build.py` + `refresh/` — the data pipeline (see the methodology doc).
- `NYC-Charter-for-GeminiNotebook.md` / `.txt` — the single-file Charter for Gemini Notebook.

## Credit & source

Charter text from the American Legal Publishing code library, compiled via the open [BetaNYC nyc-charter-laws-rules](https://github.com/BetaNYC/nyc-charter-laws-rules) dataset. For research and informational purposes only — not legal advice. Verify against the official code before relying on any provision.
