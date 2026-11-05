# How this repository was made (Santa Fe)

This file is written by the build on 2026-11-05, the day the source data was retrieved.

## Sources

| Source | Address | Retrieved | Licence |
| --- | --- | --- | --- |
| Cámara de Diputadas y Diputados de la Provincia de Santa Fe (diputadossantafe.gov.ar) | <https://diputadossantafe.gov.ar/web/camara/constitucion-provincial/> | 2026-10-30 | Official legal texts of the province, published by its government for public consultation. Argentina's copyright law (Ley 11.723) has no express exclusion for them; laws are public acts of government, binding on everyone once officially published (Código Civil y Comercial, art. 5). The source states no restriction on reuse. Reproduced with attribution, following the official text. |
| Cámara de Diputadas y Diputados de Santa Fe: Reglamento interno, versión 1.4 | <https://diputadossantafe.gov.ar/web/camara/reglamento/> | 2026-11-05 | Official legislative text; the website footer states “Todos los derechos reservados” and gives no separate terms for legislative texts. |

Every word of law in this repository comes from these sources. Lexifina reads them and records each act's dated versions, and the laws that made each change, in one corpus file. This repository is built from that file.

## What is in it

| Act | Title | Versions | Span |
| --- | --- | ---: | --- |
| `constitucion` | Constitución de la Provincia Invencible de Santa Fe (Reforma 2025) | 1 | 2025-09-11 to 2025-09-11 |
| `reglamento-interno` | Reglamento interno de la Cámara de Diputadas y Diputados de Santa Fe (versión 1.4) | 1 | 2026-04-06 to 2026-04-06 |

The build made 2 commits:

| Commits | Kind |
| ---: | --- |
| 2 | first version of an act |
| 0 | one law on its in-force day |
| 0 | changes no amendment note explains, credited to the publisher |

Other counts:
- 0 commits on the branch `futuro`: laws not yet in force on 2026-11-05.
- 0 commits dated 1 January 1970: in force before 1970, with the real day in their `In-force` trailer.
- 1 laws in the record.
- 3 tags.

## Dates

Each commit is dated at noon (America/Argentina/Cordoba) on the day the change took effect. The other dates, enacted and published, are trailers.

When a law gives no date of its own, the default rule applies: Código Civil y Comercial de la Nación, art. 5: "Las leyes rigen después del octavo día de su publicación oficial, o desde el día que ellas determinen", counted under art. 6 (the day of publication is excluded), so a law without its own vigencia clause is in force from the ninth day after its publication in the provincial Boletín Oficial (before 1 August 2015, Código Civil art. 2 as replaced by Ley 16.504, to the same effect). A law's own vigencia clause overrides the rule. https://servicios.infoleg.gob.ar/infolegInternet/anexos/235000-239999/235975/texact.htm

## How the history is built

`tools/build.py` turns the corpus into this history in one pass: one commit per law, on the day it took effect. The same corpus always gives the same commit hashes. `tools/check_repo.py` reads every version back from git and compares it with the corpus. `tools/on.py` shows the law as it stood on any date. The corpus format is described in `tools/SCHEMA.md`.

- Corpus: sha256 `2e25d368da993f75f7acb94b2bab3610db803f9ee6079b49b961e750ac6e8799` (299166 bytes).
- Builder blob hashes (`git hash-object`): `build.py` `35388bee5aa05369f7da68f5a8fa015ea8d442b8`, `check.py` `5d719354ea4c62d240c93d2cae446307d81d9e81`, `on.py` `aff48cf1b68d50c7ba8f399ca32261871c301824`.
- Python 3.14.4; git version 2.53.0.

## Checks

Not yet run for this build.

A second build from the same corpus into an empty folder gave identical hashes for all 2 history commits and 3 tags (history tip `fe8ad4fde11757fb398733cb367bba6afc52f8c6`).

## Decisions made by hand

- The constitution is the 2025 text (Reforma 2025, sanctioned 10 September 2025), shown as enacted and dated the day its own cláusula transitoria primera puts it in force, the day of its publication: the Boletín Oficial of 11 September 2025. The 1962 text it replaces is not published by the source and is not shown.
- Units: the heading (encabezado: the edition's title pages, the list of the Convención's members and staff, the Preámbulo and the headings before Artículo 1) and one file per article, holding the article and everything printed after it up to the next article (section headings, the page numbers printed in the PDF and, after the last article, the Disposiciones transitorias and the closing formula). Nothing is dropped. One paragraph per line, spacing normalised; a word broken at a line end by a soft hyphen is joined.
- The PDF is read in its content order (PyMuPDF), and its letters and digits are checked against poppler's pdftotext -raw, which reads the same order.
- The current official rulebook is included as one complete-text unit, preserving the contents, printed folios, numerical tables and the accompanying Asamblea Legislativa rules in the PDF content order. Earlier linked editions are not included in this breadth part.
- In-force basis for the current rulebook: the official source labels version 1.4 “06/04/2026”. This is the source consolidation date used for this current-text record; no separate commencement date for the edition is stated. The original sanction date, 25 October 1963, is not used for the amended text.
- The source PDF has one decorative cover bitmap reused on its pages and no normative bitmap. All textual tables are retained. No OCR is used.

## What AI did and did not do

The scripts that read the sources and build this repository were written by Claude Code running Claude Opus 5.5 (`claude-opus-5-5`) under Lexifina's direction.

No model wrote, translated or corrected legal text. No model runs at build time. Every word of law in this repository comes from the official sources above.

The commit messages are written by `build.py` from the source data.

Model use at data-build time:
- A model (Claude) wrote the fetch and parse code and chose which norms to include; it wrote no law text. Every word of law comes from the provincial source's own texts.
- GPT-6 assisted source research, metadata classification and parser/check code for one current-text act. No model supplied or corrected law text; no model runs during git build.
