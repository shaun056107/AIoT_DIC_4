# Tasks: `draft-iceib-paper`

## Phase 1: Overleaf IEEE ICEIB Draft (`ICEIB paper/main.txt`)
- [x] Configure `IEEEtran` conference preamble (`cite`, `amsmath`, `algorithm`, `algpseudocode`, `booktabs`, `tabularx`, `url`, `tikz`)
- [x] Draft Title, Author block (Group 4 placeholder affiliations), Abstract (A--F structure), and IEEE Index Terms
- [x] Draft Section I: Introduction (G--L structure, reserve equations, 5-tier lights, 4 limitations, 5 contributions, organization)
- [x] Draft Section II: Related Work (AI Technology, Domain Know-How, 10-paper Table I, Research Gap)
- [x] Draft Section III: Proposed Design (M1--M5 mental models, 8-module architecture + TikZ Fig. 1, Eqs. (1)--(3), Algorithms 1 & 2)
- [x] Draft Section IV: Experiment and Evaluation (Dataset Table II, Preliminary EDA subsection, E1--E4 Protocol Table III, `[TBD]` placeholders)
- [x] Draft Section V: Conclusion and Future Work (contributions recap, 6 limitations, 10-minute net-load & 2026 summer roadmap)
- [x] Format all 31 references (`\bibitem{ref1}`--`\bibitem{ref31}`) in IEEE style with `\url{...}`

## Phase 2: OpenSpec and Reference Structure
- [x] Create `openspec/project.md` and `openspec/AGENTS.md`
- [x] Create `openspec/specs/iceib-paper/spec.md` covering all 7 ICEIB paper sections
- [x] Create `openspec/changes/draft-iceib-paper/{proposal.md,design.md,tasks.md}`
- [x] Create `myRef/references.bib` (31 BibTeX entries) and `myRef/literature_summary.md`
- [x] Create root `AGENTS.md`, `agent.md`, and `.gitignore`

## Phase 3: Verification of Current Draft
- [x] Verify zero emojis across all created files
- [x] Verify balanced LaTeX environments, escaped characters, zero raw CJK characters, and 31 bibliography entries in `ICEIB paper/main.txt`

## Phase 4: Post-Experiment Follow-Up (Pending Implementation & Evaluation)
- [ ] Verify exact official English romanization of author names, university/department affiliation, and email addresses in `ICEIB paper/main.txt`
- [ ] Run Experiment E1 (Ridge/GBDT + Conformal calibration + weather-noise sensitivity) and replace E1 `[TBD]` placeholders with verified metrics
- [ ] Run Experiment E2 (September 9--23, 2025 Hsinta/Linkou outage backtest) and replace E2 `[TBD]` placeholders with verified reserve errors and light agreement
- [ ] Run Experiment E3 (40-question evaluation across Pure LLM, LLM+RAG, unverified Agent, and full GridReserve Agent) and replace E3 `[TBD]` placeholders
- [ ] Run Experiment E4 (`ClassifyLight` boundary unit tests) and replace E4 `[TBD]` placeholder with verified pass rate
- [ ] Compile `ICEIB paper/main.txt` in Overleaf with `pdfLaTeX` and verify IEEE ICEIB page limit and figure/table placement
