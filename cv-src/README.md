# CV & cover letter sources

The rendered PDFs used to have no source in this repo — the HTML lived in a
throwaway session container and was lost. These files are that source,
reconstructed on 2026-07-26 to match the existing design exactly. **Edit here,
re-render, never patch a PDF.**

| Source | Renders to |
|---|---|
| `cv-en.html` | `../assets/Daniela_Patricio_CV.pdf` |
| `cv-pt.html` | `../assets/Daniela_Patricio_CV_PT.pdf` |
| `cover-letter-mbio.html` | `../Daniela_Patricio_Cover_Letter_MBio.pdf` |

`cv-pt.html` was translated from `cv-en.html` on 2026-07-26. Keep both in sync
when editing content — English changes first, then port to Portuguese.

## Rebuilding

Needs Python, WeasyPrint, and the two fonts installed system-wide.

```bash
pip install weasyprint

# Fonts: Inter (Regular/Medium/SemiBold/Bold/Italic) and JetBrains Mono
# (Regular/Medium/Bold) must be installed, or WeasyPrint silently
# substitutes and the layout drifts.
#   https://github.com/rsms/inter/releases
#   https://github.com/JetBrains/JetBrainsMono/releases

python -c "from weasyprint import HTML; HTML('cv-en.html').write_pdf('../assets/Daniela_Patricio_CV.pdf')"
python -c "from weasyprint import HTML; HTML('cv-pt.html').write_pdf('../assets/Daniela_Patricio_CV_PT.pdf')"
python -c "from weasyprint import HTML; HTML('cover-letter-mbio.html').write_pdf('../Daniela_Patricio_Cover_Letter_MBio.pdf')"
```

## Design constants

Locked to the original render, measured from the previous PDF. Don't drift these.

- Page A4, `595.92 × 842.88 pt`, zero margin
- Sidebar `213pt` wide, `#F8FAFC`, `0.8pt` right border `#E2E8F0`
- Main column starts at `240.7pt`, `321pt` wide
- Accent teal `#0891B2` · ink `#0F172A` · body `#334155` · muted `#94A3B8`
- Sidebar rules `#CFFAFE` · key-results panel `#ECFEFF`
- Inter for prose, JetBrains Mono for labels, dates and metadata

## Pagination

Both files use **manual pagination** — one `.page` div per printed page, fixed
height, `overflow: hidden`. Content that grows past the box gets silently
clipped rather than reflowing. After any content edit, render and eyeball both
pages before shipping, especially the page-1 sidebar, which is close to full.
