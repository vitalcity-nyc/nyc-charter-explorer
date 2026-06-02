# NYC Charter Explorer — Vital City

A searchable, sortable web version of the **Charter of the City of New York**, styled for Vital City and built to be embedded in an article or opened full screen. Includes the full Charter text, Charter Revision Commission tagging, per-section highlights and notes, and a link to a plain-language Q&A notebook.

**Live (full screen):** https://vitalcity-nyc.github.io/nyc-charter-explorer/
**Embed view:** add `?embed=1` to the URL.

This is the Vital City edition of the explorer (Halyard + Gascogne, Vital City palette, white/dark data-tool theming). The full data methodology — sourcing, currency, the Charter Revision Commission mapping and its verification — is in [`README-methodology.md`](README-methodology.md).

## Embedding in an article

The explorer runs in an `<iframe>` and reports its height to the host page, so the frame grows and shrinks with the content (no inner scrollbar). Paste this where you want it (works in Ghost HTML cards and most CMSes):

```html
<iframe
  src="https://vitalcity-nyc.github.io/nyc-charter-explorer/?embed=1"
  title="NYC Charter Explorer"
  loading="lazy"
  scrolling="no"
  style="width:100%;height:780px;border:1px solid #dddddd;border-radius:10px"></iframe>
<script>
window.addEventListener('message', function (e) {
  if (e.data && e.data.type === 'vc-charter-height' && e.data.id === 'nyc-charter-explorer') {
    document.querySelectorAll('iframe[src*="nyc-charter-explorer"]').forEach(function (f) {
      f.style.height = e.data.height + 'px';
    });
  }
});
</script>
```

- The starting `height` is a fallback for before the script runs; the script then keeps the frame sized to the content.
- In embed view the chapter sidebar, the footer and the theme/compact toggles are hidden to keep it lightweight. A **"Full screen"** button and an **"Open the full explorer"** link both open the full version (no `?embed=1`) in a new tab.
- The full-screen version has everything: the chapter table of contents, the methodology footer, light/dark themes and the compact-density toggle.

## What it does

- Full-text and title search with relevance ranking; `"quoted phrases"`, `-exclude` and `OR` operators.
- Sort by chapter, section number, most/least recently amended, length or relevance; filter by chapter or Charter Revision Commission.
- Per-section **Charter Revision Commission** tags (2018, 2019, 2024, 2025 passed proposals) with the added/amended/repealed action, independently verified against the official amendment text.
- Personal **highlights** (select any passage) and **notes**, saved privately in the browser, with backup/restore and inclusion in the text export.
- In-text cross-reference links, shareable section/passage links (copy, email, tweet) and a per-view text export.
- **"Ask the Charter a question"** links to a Google NotebookLM notebook of the full Charter for plain-language Q&A.

## Files

- `index.html` — the explorer (single page; data bundled in `charter-data.js`, so it also works by double-click).
- `charter-data.js` / `charter-data.json` — the bundled Charter data with Charter Revision Commission tags.
- `fonts/GascogneTS-Light.ttf` — Vital City display serif (used for the § numerals). Halyard loads from Adobe Typekit.
- `data/` + `build.py` + `refresh/` — the data pipeline (see the methodology doc).
- `NYC-Charter-for-NotebookLM.md` / `.txt` — the single-file Charter for NotebookLM.

## Credit & source

Charter text from the American Legal Publishing code library, compiled via the open [BetaNYC nyc-charter-laws-rules](https://github.com/BetaNYC/nyc-charter-laws-rules) dataset. For research and informational purposes only — not legal advice. Verify against the official code before relying on any provision.
