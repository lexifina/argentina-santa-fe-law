# Santa Fe: law history in git

The law of the Province of Santa Fe (Provincia de Santa Fe, Argentina) as a git history: one file per article, one commit per norm on the day it took effect. `git log` lists the changes to an article; checking out a date gives the text the record holds for that day.

It follows the shared design of [lexifina/global-law](https://github.com/lexifina/global-law), which places it at `ar-s/`. Argentina's national law is in [lexifina/argentina-law](https://github.com/lexifina/argentina-law).

The text is in Spanish, exactly as the source prints it.

## What this repository holds

2 norms so far: the constitution first, then the codes, then laws, newest first, added in parts. 1 of them is shown as enacted; the rest are their current consolidated text only (see Dates).

| Folder | Norm | History |
| --- | --- | --- |
| `constitucion/` | Constitución de la Provincia Invencible de Santa Fe (Reforma 2025) | as enacted, in force 11 September 2025 |
| `reglamento-interno/` | Reglamento interno de la Cámara de Diputadas y Diputados de Santa Fe (version 1.4) | current text, oldest version included; source edition dated 6 April 2026; one complete-text unit |

The rulebook includes the accompanying Assembly rules, contents and textual numerical tables in the official PDF.

## Source

Cámara de Diputadas y Diputados de la Provincia de Santa Fe (diputadossantafe.gov.ar), <https://diputadossantafe.gov.ar/web/camara/constitucion-provincial/>. The Cámara publishes the "Ejemplar auténtico" of the Constitución de la Provincia Invencible de Santa Fe, Reforma 2025 (Edición 0, from the text sanctioned in plenary session on 10 September 2025), as a PDF with a text layer. The site footer reads "Todos los derechos reservados"; it states no terms for the legal texts themselves.

The current rulebook version 1.4 is published at <https://diputadossantafe.gov.ar/web/camara/reglamento/> and dated 6 April 2026 by the source.

## Dates

- Each commit is dated at **noon, America/Argentina/Cordoba, on the day the norm took effect**: the day its own vigencia clause names, or otherwise the ninth day after its publication in the Boletín Oficial de la Provincia de Santa Fe (Código Civil y Comercial de la Nación, arts. 5 and 6).
- The source publishes only today's consolidated text of each norm. A norm that no later norm is recorded as related to, and whose text carries no amendment notes, is shown as enacted. Every other norm is its current text only, the **oldest version available**, dated by the day the source last updated its record; its earlier wording is not shown.
- Versions that take effect after the retrieval day are on the `futuro` branch, never merged into `main`.

## Files

`<norm>/art-005.md` is Artículo 5, `art-005-bis.md` Artículo 5 bis; `encabezado.md` holds the number, the enacting formula and anything printed before Artículo 1. Section headings, signatures and the source's amendment notes stay in the file of the article they follow. One paragraph per line.

## How it is checked

- Every version of every norm is read back from git on the day it took effect and on the day before (`tools/check_repo.py`); both must match `corpus.json`.
- The letters and digits of every version equal those of the source document it was read from (read again with an independent HTML reader), so no word is lost or added.
- Health checks: no merge commits, commit dates never go backwards, nothing dated in the future, and every commit's trailers parse.

## Limits

This is not an official publication. The binding text is the one published in the Boletín Oficial de la Provincia de Santa Fe. Only the norms listed above are included, and most show only their current text.
