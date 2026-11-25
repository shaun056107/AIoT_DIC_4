# OpenSpec Agent Instructions

This guide defines how AI assistants operate within the `AIoT_DIC4` OpenSpec workflow when drafting, revising, or finalizing the IEEE ICEIB paper.

## 1. Mandatory Reading Order

Before modifying `ICEIB paper/main.txt` or any file under `myRef/`, read:
1. `openspec/project.md` for non-negotiable constraints, canonical metrics, and file locations.
2. `openspec/specs/iceib-paper/spec.md` for section-level requirements and acceptance criteria.
3. Relevant active proposals under `openspec/changes/` (starting with `openspec/changes/draft-iceib-paper/`).
4. Ground-truth source material in `myplan/` and `README.md` whenever verifying claims or numbers.

## 2. Editing Rules for the Paper

- **Single-File Overleaf Target:** Keep `ICEIB paper/main.txt` self-contained so the author can paste or upload it directly into Overleaf (`main.tex`) without missing local include files.
- **Keep Citations Synchronized:** Whenever adding, removing, or renumbering a reference, update both the `\begin{thebibliography}{...}` block in `ICEIB paper/main.txt` and `myRef/references.bib` so citation numbers (`[1]`--`[31]`) match identically.
- **Respect Experimental Boundaries:** Never replace `[TBD]` placeholders in Section IV (`Experiment and Evaluation`) unless actual verified experimental outputs from executed code/logs are provided in the workspace.
- **No Emojis:** Ensure every edited file contains zero emojis.
- **pdfLaTeX Safety:** Escape all LaTeX special characters (`%`, `&`, `_`, `#`, `$`) in prose and tables, ensure every `tabularx` environment includes at least one `X` column, and ensure zero raw CJK characters appear in `ICEIB paper/main.txt`.

## 3. Change Workflow

1. **Propose:** Create a new folder under `openspec/changes/<change-name>/` with `proposal.md`, `design.md`, and `tasks.md` for substantial revisions (e.g., `populate-experiment-results` once E1--E4 run).
2. **Implement:** Update `ICEIB paper/main.txt` and `myRef/` strictly according to the approved spec and change design.
3. **Verify:** Check balanced LaTeX environments, citation completeness, absence of raw CJK or emoji characters, and alignment with `openspec/specs/iceib-paper/spec.md`.
4. **Update Spec & Archive:** Once a change is finalized and verified (e.g., camera-ready numbers populated), merge delta requirements into `openspec/specs/iceib-paper/spec.md`, mark all tasks complete in `tasks.md`, and archive the change folder under `openspec/changes/archive/`.
