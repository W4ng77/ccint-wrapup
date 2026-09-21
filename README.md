# ccint — Project Wrap-up

LaTeX source for the **ccint (Canada Cyber Social Intelligence)** project
wrap-up: design rationale, implementation, findings, and limitations.

This repository is set up for **Overleaf ↔ GitHub sync**, so the documents sit
at the repository root.

| Document | Length | Root file |
|---|---|---|
| Full write-up | 15 pp | `main.tex` |
| **Two-page summary** | 2 pp | `tldr.tex` |

Both share `preamble.tex`.

### Switching which one Overleaf compiles

Overleaf compiles one root document at a time. To switch:
**Menu → Settings → Main document → `main.tex` or `tldr.tex`.**

If the compile button looks like it is building the wrong document, that setting
is why.

## Build

Compiles with **pdfLaTeX** — Overleaf's default. No compiler setting to change.

```bash
latexmk -pdf main.tex     # full write-up
latexmk -pdf tldr.tex     # two-page summary
```

## Files

| File | Contents |
|---|---|
| `main.tex` | Full write-up (15 pp) |
| `tldr.tex` | Two-page summary |
| `preamble.tex` | Packages, colours, section and table styling |

Build artefacts (including the PDFs) are gitignored so that Overleaf sync does
not produce binary conflicts on every compile.

## Companion repository

The system this document describes — collector, labeler, analytics, agent,
tests — lives separately. See `HANDOFF.md`, `README.md` and `PROJECT_WRAPUP.md`
there for implementation detail; this repo holds only the typeset write-up.
