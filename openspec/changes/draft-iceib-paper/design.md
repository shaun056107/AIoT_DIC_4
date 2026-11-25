# Technical Design: `draft-iceib-paper`

## 1. Overleaf Single-File Architecture (`ICEIB paper/main.txt`)

- **Document Class:** `\documentclass[conference]{IEEEtran}` with `\IEEEoverridecommandlockouts`.
- **Self-Contained Compilation:** Rather than splitting sections across multiple `.tex` files or importing external `.bib` or `.png` assets that require multi-file Overleaf uploads, `ICEIB paper/main.txt` embeds:
  1. An inline **TikZ** vector diagram (`Fig. 1`) for the 8-module architecture using non-overlapping outer feedback corridors (`leftcorridor` for Verification Retry `<= 2`, `rightcorridor` for User Follow-up).
  2. Inline **algpseudocode** environments (`Algorithm 1` and `Algorithm 2`) matching `myplan/期末專題提案.pdf` Section 5.5.
  3. Inline `\begin{thebibliography}{31}` matching `[1]`--`[31]` order, with `\usepackage[hyphens]{url}` to break long URLs cleanly across two-column margins.
  4. `tabularx` tables with explicit `>{\raggedright\arraybackslash}X` columns so Tables I--III strictly obey `\columnwidth` / `\textwidth`.

## 2. Language and Encoding Decisions

- **pdfLaTeX Compatibility:** All Chinese dataset names, agency names, and news citations from `myplan/` are translated into standardized English equivalents (e.g., Taiwan Power Company / Taipower, Central Weather Administration / CWA, Taipei/Taichung/Kaohsiung stations `466920`/`467490`/`467441`) so `ICEIB paper/main.txt` compiles under Overleaf's default `pdfLaTeX` without `xeCJK` or `ctex`.
- **Unit Notation:** Preserves Taipower's native `10^4 kW` unit across equations, algorithms, and tables while providing MW conversions (`42,940 MW`, `38,530 MW`, `2,100 MW`) in the Abstract and Introduction for international IEEE readers.
- **No Emojis:** Zero emoji codepoints appear in any file.

## 3. Handling Pending Experiments (E1--E4)

- Section IV separates **Preliminary Exploratory Feasibility Analysis** (verified numbers already observed during proposal EDA across 1,339 days) from the **Experimental Protocol (E1--E4)** and **Formal Result Placeholders**.
- Unexecuted E1--E4 quantitative cells and outcome bullets carry explicit `\texttt{[TBD]}` markers so future authors know precisely where to insert experimental metrics without misrepresenting planned work as completed results.

## 4. Reference Synchronization

- `ICEIB paper/main.txt` uses `\bibitem{ref1}` through `\bibitem{ref31}` in exact numerical correspondence with `[1]`--`[31]` in `myplan/期末專題提案.pdf`.
- `myRef/references.bib` provides matching BibTeX entries (`ref1`--`ref31`) should the authors later switch to `\bibliographystyle{IEEEtran}` and `\bibliography{references}` in Overleaf.
