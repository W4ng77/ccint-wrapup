# ccint — Project Wrap-up

LaTeX source for the **ccint (Canada Cyber Social Intelligence)** project
wrap-up: design rationale, implementation, findings, and limitations.

This repository is set up for **Overleaf ↔ GitHub sync**, so `main.tex` sits at
the repository root.

## Build

Compiles with **pdfLaTeX** — Overleaf's default. No compiler setting to change.

```bash
latexmk -pdf main.tex
```

## Files

| File | Contents |
|---|---|
| `main.tex` | The document |
| `preamble.tex` | Packages, colours, section and table styling |

Build artefacts (including `main.pdf`) are gitignored so that Overleaf sync does
not produce binary conflicts on every compile.

## Companion repository

The system this document describes — collector, labeler, analytics, agent,
tests — lives separately. See `HANDOFF.md`, `README.md` and `PROJECT_WRAPUP.md`
there for implementation detail; this repo holds only the typeset write-up.
