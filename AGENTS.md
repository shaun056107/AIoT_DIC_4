# Repository Agent Guidelines (`AGENTS.md`)

This repository contains the **GridReserve Agent** project materials (`myplan/`, `README.md`), the **IEEE ICEIB** conference paper draft (`ICEIB paper/main.txt`), bibliography resources (`myRef/`), and OpenSpec specifications (`openspec/`).

## Core Operating Rules

1. **Follow OpenSpec Workflow:** Read `openspec/project.md`, `openspec/AGENTS.md`, and `openspec/specs/iceib-paper/spec.md` before editing the paper or reference files.
2. **Preserve Source Documents:** Never modify or delete files inside `myplan/` or the root `README.md`. They serve as read-only ground truth.
3. **Zero Emojis:** Do not write Unicode emojis anywhere in `ICEIB paper/`, `openspec/`, `myRef/`, or documentation updates.
4. **No Fabricated Results:** Formal experiments E1--E4 have not yet been executed. Keep `[TBD]` markers for formal results and distinguish preliminary EDA metrics (Section IV-B) from formal experiments (Section IV-C/D).
5. **Overleaf Compatibility:** Maintain `ICEIB paper/main.txt` as a standalone `\documentclass[conference]{IEEEtran}` file that compiles cleanly with `pdfLaTeX` (no raw CJK text in LaTeX body/references, all special characters properly escaped).
6. **Citation Sync:** Keep `\bibitem{ref1}`--`\bibitem{ref31}` in `ICEIB paper/main.txt` aligned 1-to-1 with `myRef/references.bib`.
