# Change Proposal: `draft-iceib-paper`

## Why

The GridReserve Agent team (Group 4) has completed a 14-page project proposal (`myplan/期末專題提案.pdf`), an A--Z paper outline (`myplan/A2Z大綱.pdf`), an executive summary (`myplan/專業摘要.pdf`), a 37-slide presentation (`myplan/期末專題提案簡報.pdf`), and an architectural design document (`README.md`). To prepare for academic submission to **IEEE ICEIB**, these materials must be synthesized into an Overleaf-ready IEEE conference manuscript alongside a structured OpenSpec specification that tracks section requirements and separates verified preliminary diagnostics from pending formal experiments.

## What Changes

- Create `ICEIB paper/main.txt`: a complete, self-contained `\documentclass[conference]{IEEEtran}` Overleaf manuscript containing Abstract, Introduction, Related Work (with 10-study Table I), Proposed Design (with TikZ 8-module architecture diagram, equations, Algorithms 1 & 2), Experiment and Evaluation (with dataset Table II, preliminary EDA diagnostics, E1--E4 protocol Table III, and `[TBD]` placeholders), Conclusion, and all 31 IEEE-formatted References.
- Create `openspec/` specification files (`project.md`, `AGENTS.md`, `specs/iceib-paper/spec.md`, and this `changes/draft-iceib-paper/` package) to govern ICEIB paper authoring and future experimental updates.
- Create `myRef/references.bib` and `myRef/literature_summary.md` to mirror all 31 citations and 10 comparative literature entries in reusable BibTeX and Markdown formats.
- Create root `AGENTS.md`, `agent.md`, and `.gitignore` matching the project repository structure.

## Scope and Non-Goals

- **In Scope:** Structuring and translating all proposal content into rigorous IEEE conference English, creating pdfLaTeX-compatible figures/algorithms/tables, synchronizing all 31 references, and explicitly marking unexecuted E1--E4 experiment outcomes as `[TBD]`.
- **Out of Scope (Non-Goals):** Modifying `myplan/` or `README.md`, implementing Python source code under `src/`, or fabricating formal experimental results for E1--E4.

## Impact

- Provides an immediately compilable Overleaf draft (`ICEIB paper/main.txt`) ready for iterative refinement and final experimental result insertion.
- Establishes a spec-driven workflow so a future change (e.g., `populate-experiment-results`) can cleanly replace `[TBD]` entries after E1--E4 execute.
