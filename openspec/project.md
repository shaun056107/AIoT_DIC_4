# OpenSpec Project Constitution: GridReserve Agent (IEEE ICEIB Paper)

## 1. Purpose and Target Venue

This OpenSpec workspace governs the specification, drafting, and verification of an academic conference paper for **IEEE ICEIB** based on the Group 4 course project **GridReserve Agent** (`myplan/`).

- **Paper Title:** GridReserve Agent: A Tool-Constrained Domain AI Agent for Weather-Driven Load Forecasting and Outage Scenario Analysis in Taiwan's Power Grid
- **Target Format:** IEEE Conference Proceedings (`\documentclass[conference]{IEEEtran}`), self-contained single-file Overleaf source at `ICEIB paper/main.txt`
- **Primary Source Material (Read-Only Ground Truth):**
  - `myplan/期末專題提案.pdf` (14-page Final Project Proposal, Sections 1--6, 31 References)
  - `myplan/A2Z大綱.pdf` (A--Z SOP academic paper outline mapping A--F Abstract, G--L Introduction, M--O Related Work, Q1--Q3 Deep Research, PA--PM Proposed Scheme, Q--V Simulation & Evaluation, W--Z Conclusion)
  - `myplan/專業摘要.pdf` (Executive technical summary)
  - `myplan/期末專題提案簡報.pdf` (37-slide presentation deck)
  - `myplan/GridReserve_Agent_Infographic_A4_Landscape.png` (Visual architecture and summary infographic)
  - `README.md` (`DESIGN.md` technical specification v0.1)

## 2. Required Paper Structure (IEEE ICEIB)

The paper in `ICEIB paper/main.txt` must include all seven core sections following IEEE conference style:
1. **Abstract** (plus IEEE Index Terms)
2. **I. Introduction**
3. **II. Related Work** (including AI Technology, Domain Know-How, 10-paper comparative summary table, and Research Gap)
4. **III. Proposed Design** (including domain mental models M1--M5, 8-module architecture + diagram, mathematical formulation, dual-logic light rules, 6 data-cleaning rules, Algorithm 1, and Algorithm 2)
5. **IV. Experiment** (Dataset overview, preliminary exploratory feasibility diagnostics, E1--E4 experimental protocol, baselines, evaluation metrics, and explicit `[TBD]` placeholders for pending runs)
6. **V. Conclusion** (Summary, 6 explicit system limitations, and future work using 10-minute generation logs)
7. **References** (All 31 references in IEEE conference bibliography format)

## 3. Non-Negotiable Constraints

1. **No Emojis:** Do not use any Unicode emojis in any LaTeX source, OpenSpec document, Markdown summary, or commit/status text.
2. **Scientific Integrity (No Fabricated Results):** Formal experiments E1--E4 have not been run yet. Never invent MAE, MAPE, pinball loss, coverage, accuracy, or hallucination rates for E1--E4. Only report verified preliminary EDA observations from `myplan/` clearly labeled as preliminary diagnostics, and keep `[TBD]` placeholders for formal experiment outputs.
3. **Overleaf pdfLaTeX Compatibility:** `ICEIB paper/main.txt` must compile cleanly on Overleaf using standard `pdfLaTeX` without external custom `.cls` files or raw CJK characters in LaTeX prose or `\bibitem` entries.
4. **Source Preservation:** Never edit or delete files in `myplan/` or the root `README.md`.
5. **Unit Convention:** Report power capacities and peak loads consistently in Taipower's standard unit of `10^4 kW` (10 MW), optionally noting MW equivalents in parentheses on first mention.
6. **Canonical Ground-Truth Numbers (from `myplan/`):**
   - 2026 summer daytime peak forecast: `4,294 x 10^4 kW` (42,940 MW, +4.89% over 2025 `4,092 x 10^4 kW`); night peak forecast: `3,853 x 10^4 kW` (38,530 MW); 4 new units > `500 x 10^4 kW` entering trial operation.
   - MOEA 2025--2029 reserve margin projection: 11.3%--14.2% (below 15% benchmark).
   - Sep 2025 incidents: Hsinta New Unit 2 + Linkou Unit 2 loss of `210 x 10^4 kW` (~6% of night peak), expanding to `290 x 10^4 kW` after Linkou Unit 1 tube leak; reserve fell from projected 14% to ~3%--4% before emergency units lifted night reserve to ~6%.
   - Merged historical dataset: `1,339` consecutive days (`2023-01-01` to `2026-08-31`), merging 3-year file (`1,096` rows) and main file (`608` rows, containing `6` erroneous reserve-rate records).
   - Preliminary EDA metrics: `r(load, 3-station max temp) ~ 0.75`, `r(reserve rate, temp) ~ -0.07`, `r(supply, load) ~ 0.92`; reverse-load MRE over 365 overlapping 2025 days `~ 0.014%`; naive reserve-rate MAE `5.8--6.2` percentage points (std `6.6`); linear load test MAE `100--150 x 10^4 kW` vs. mean baseline `367 x 10^4 kW`.
   - Unit inventory: `175` units (`~2,963 x 10^4 kW`), supplemented by Hsinta New (`3` units, `390 x 10^4 kW`) and Taichung New Units 1 & 2 (`130 x 10^4 kW` each, setting `C_max = 130 x 10^4 kW`).

## 4. Workspace Layout

```text
AIoT_DIC4/
├── .gitignore
├── agent.md
├── AGENTS.md
├── README.md                              # Existing technical DESIGN.md (read-only)
├── ICEIB paper/
│   └── main.txt                           # Overleaf IEEEtran conference paper draft
├── myRef/
│   ├── references.bib                     # BibTeX entries for all 31 citations
│   └── literature_summary.md              # Structured notes on 10 key papers & research gap
├── myplan/                                # User's original proposal, slides, A2Z outline (read-only)
└── openspec/
    ├── project.md                         # Project constitution and canonical facts
    ├── AGENTS.md                          # Workflow instructions for AI assistants
    ├── specs/
    │   └── iceib-paper/
    │       └── spec.md                    # Authoritative section-by-section requirements
    └── changes/
        └── draft-iceib-paper/
            ├── proposal.md                # Change rationale and scope
            ├── design.md                  # LaTeX & structural design decisions
            └── tasks.md                   # Execution and post-experiment checklist
```
