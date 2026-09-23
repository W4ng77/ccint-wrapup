# ccint — Reports

LaTeX source for the **ccint (Canada Cyber Social Intelligence)** project:
design rationale, implementation, measurements, findings and limitations.

This repository is set up for **Overleaf ↔ GitHub sync**, so the documents sit
at the repository root.

## The two current documents

| Document | Length | Root file | For |
|---|---|---|---|
| **Brief** — start here | 4 pp | `Brief.tex` | Why the system is built this way, what was built, where it stands |
| **Full report** | 14 pp | `Full_Report.tex` | The same ground with the measurements, figures, limitations and method detail |

Both share `preamble.tex`. The brief is self-contained; the full report is
where every number in it is derived and qualified.

Everything else at the repository root — `main.tex`, `tldr.tex`,
`iteration.tex`, `Progress_Brief.tex` — is **superseded**. It is kept because
it records the state of the work at earlier dates, not because it should be
read first.

### Switching which one Overleaf compiles

Overleaf compiles one root document at a time:
**Menu → Settings → Main document → `Brief.tex` or `Full_Report.tex`.**

If the compile button looks like it is building the wrong document, that
setting is why.

## Build

Compiles with **pdfLaTeX** — Overleaf's default. No compiler setting to change.

```bash
latexmk -pdf Brief.tex
latexmk -pdf Full_Report.tex
```

## Figures

`figures/*.pdf` are generated from the database by
`scripts/figures_iteration.py` and `scripts/figures_report.py` in the companion
repository, and are **committed**, because Overleaf has no database to
regenerate them from.

Two figures are TikZ and live under `figures/src/`, kept out of the repository
root so Overleaf does not mistake their `\documentclass` for a second main
document:

| Source | Output | Shows |
|---|---|---|
| `figures/src/architecture.tex` | `Architecture.png` | The seven-stage processing pipeline |
| `figures/src/agent_stack.tex` | `figures/agent_stack.pdf` | Tool layer, agent loop and portal over the existing subsystems |

Rebuild them with:

```bash
pdflatex figures/src/architecture.tex
pdftoppm -png -r 160 architecture.pdf Architecture && mv Architecture-1.png Architecture.png
cp Architecture.png figures/

pdflatex -output-directory=figures figures/src/agent_stack.tex
```

`Architecture.png` also sits at the repository root because it is delivered on
its own, not only as a figure inside the brief.

Build artefacts other than the two report PDFs are gitignored, so Overleaf sync
does not produce binary conflicts on every compile.

## Companion repository

The system these documents describe — collector, labelers, analytics, CVE
enrichment, agent tools, portal, tests — lives at
[W4ng77/ccint](https://github.com/W4ng77/ccint). See its `README.md`,
`HANDOFF.md` and `PROJECT_WRAPUP.md` for implementation detail; this repository
holds only the typeset write-up.
