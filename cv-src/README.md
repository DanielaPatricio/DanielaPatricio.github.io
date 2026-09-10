# CV & cover letter sources

The rendered PDFs used to have no source in this repo — the HTML lived in a
throwaway session container and was lost. These files are that source,
reconstructed on 2026-07-26 to match the existing design exactly. **Edit here,
re-render, never patch a PDF.**

## ⚠️ Ownership — read before editing

These files are edited from **one place only: the CV/job-search chat.** On
2026-07-26 two chats wrote `cv-src/` within six minutes of each other and the
second silently reverted the first, losing the engineering variant and the
employer descriptors. The split that prevents it:

| Owned by the CV chat | Owned by the portfolio chat |
|---|---|
| `cv-src/**` | `index.html`, `projects/**`, `css/`, `js/` |
| `assets/*.pdf` | `.gitignore`, staging, commits, push |

If you need a CV change and you're the portfolio chat: say so, don't edit.

## Career folder

Job-search material lives **outside this repo** at `Documents/Claude/Projects/Career/`:
`applications/<employer>/`, `interview-prep/`, `salary-research/`, `outreach/`, `_archive/`.
Nothing job-search-specific belongs in the GitHub Pages repo — it is public.

## Files

| Source | Renders to | Use |
|---|---|---|
| `cv-en.html` | `../assets/Daniela_Patricio_CV.pdf` | **Engineering-leaning. The only CV linked from the site.** |
| `cv-en-analyst.html` | `Daniela_Patricio_CV_Analyst.pdf` (stays in this folder) | Analyst-titled applications. **Never linked from the site** — uploaded to the form. |
| `cv-pt.html` | `../assets/Daniela_Patricio_CV_PT.pdf` | Single Portuguese variant. Translated 2026-07-26 from the analyst ordering. |
| `cover-letter-mbio.html` | `../../Career/applications/mercedes-benz-io/Daniela_Patricio_Cover_Letter_MBio.pdf` | Per-employer. Lives **outside the repo** in the Career folder. |

## The two English variants

Same facts, different order. Nothing is added or removed between them —
only emphasis.

|  | Engineering (`cv-en.html`) | Analyst (`cv-en-analyst.html`) |
|---|---|---|
| Profile opens on | SQL/ETL infrastructure beneath analytics: medallion pipelines, dimensional models, RLS | dashboards and automated reporting |
| Skills order | Data Engineering & ETL first | Visualisation & Reporting first |
| Key Results | RLS → **Operational Alarms** → most-viewed reports | RLS → most-viewed reports → NPS dashboard |
| Alarms system | promoted into Key Results | stays as bullet 4 |

**Pick a variant per application. Never edit a CV per job** — that is a
40-minute task that gets skipped when tired, and it is how applications stop
going out.

Why engineering is the public one: the case studies already lean that way
(RLS architecture, Alarms, Python scraper), and the site is an inbound funnel,
so it should aim at the band she wants rather than the one she'd accept.

**Keep PT to one file.** EN/PT × analyst/engineering is four CVs and would stop
being maintained. `cv-pt.html` currently mirrors the analyst ordering; porting
the engineering ordering to it is optional and not blocking.

## Employer descriptors

Foreign recruiters don't recognise CTT, Audiogest or EDP. Each role carries a
small mono line under its dates turning an unknown name into a known scale:

- CTT — *National postal operator*
- Audiogest / PassMúsica — *National music rights society*
- EDP Distribuição — *National electricity distribution grid*

These must stay in sync with the same descriptors on `index.html`.

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
python -c "from weasyprint import HTML; HTML('cv-en-analyst.html').write_pdf('Daniela_Patricio_CV_Analyst.pdf')"
python -c "from weasyprint import HTML; HTML('cv-pt.html').write_pdf('../assets/Daniela_Patricio_CV_PT.pdf')"
python -c "from weasyprint import HTML; HTML('cover-letter-mbio.html').write_pdf('../../Career/applications/mercedes-benz-io/Daniela_Patricio_Cover_Letter_MBio.pdf')"
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

Every file uses **manual pagination** — one `.page` div per printed page, fixed
height, `overflow: hidden`. Content that grows past the box gets silently
clipped rather than reflowing. After any content edit, render and eyeball every
page before shipping, especially the page-1 sidebar, which is close to full.
