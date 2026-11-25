# Specification: IEEE ICEIB Academic Paper (`iceib-paper`)

## Purpose

Define the authoritative content, structure, formatting, and traceability requirements for the IEEE ICEIB conference paper describing **GridReserve Agent** (`ICEIB paper/main.txt`).

---

## Requirements

### Requirement 1: Abstract and Keywords
The paper SHALL open with an IEEE-formatted `abstract` and `IEEEkeywords` block grounded in the A--F structure of `myplan/A2Z大綱.pdf` and `myplan/期末專題提案.pdf`.

- **Scenario: Complete A--F narrative in Abstract**
  - **WHEN** a reader inspects the Abstract
  - **THEN** it covers (A) 2026 summer peak (`4,294 x 10^4 kW`) and night peak (`3,853 x 10^4 kW`) motivation plus September 2025 outage shocks (`210 x 10^4 kW` lost, reserve down to ~4%), (B) the three core gaps (reserve rate temperature correlation `-0.07`, day/night and quality ambiguities, simulation-only grid agents and LLM hallucination), (C) GridReserve Agent as the proposed solution, (D) decoupled ML load forecasting + deterministic scenario/domain rules + verification-gated LLM planner, (E) the 1,339-day dataset and E1--E4 evaluation protocol, and (F) preliminary EDA findings and expected outcomes with transparent limitation reporting.

- **Scenario: IEEE Index Terms present**
  - **WHEN** the paper is compiled in `IEEEtran` conference mode
  - **THEN** an `IEEEkeywords` block follows the abstract with 5--6 domain-relevant terms.

### Requirement 2: Section I -- Introduction
The paper SHALL present Section I following the G--L progression (General background, However/core problems, In Literature, Judgement, Keypoint contributions, List of organization).

- **Scenario: Operational context and definitions**
  - **WHEN** Section I introduces Taiwan's power grid
  - **THEN** it defines reserve capacity (`R = S - L`) and reserve rate (`r = R / L * 100%`), explains the five-tier supply indicator lights, notes the 2022 (ROC 111) shift to nighttime reserve reporting, and identifies Taipower EMS and CWA CODiS stations as the sensing/telemetry sources.

- **Scenario: Four core limitations and five contributions**
  - **WHEN** Section I motivates the proposed system
  - **THEN** it enumerates the four existing limitations (unpredictable dispatch-driven reserve rate, headline quantity vs. fast-start quality, forecast-vs-outage divergence, simulation-only LLM grid agents) and five concrete contributions (decoupled architecture, Taiwan domain KB, 6-anomaly data cleaning pipeline, verification gate, reproducible evaluation protocol).

### Requirement 3: Section II -- Related Work
The paper SHALL organize Section II into AI Technology, Domain Know-How, a comparative summary table of 10 key works, and an explicit Research Gap subsection.

- **Scenario: Balanced coverage of AI and Taiwan grid literature**
  - **WHEN** Section II is reviewed
  - **THEN** Subsection II-A covers LLM grid agents (GridMind `[20]`, X-GridAgent `[21]`, Grid-Agent `[22]`, smart-grid LLM surveys `[23]`--`[25]`), Taiwan load forecasting (`[26]`, `[27]`), and conformal/quantile intervals (`[24]`), while Subsection II-B covers reserve lights (`[4]`, `[11]`), reserve quality (`[14]`, `[15]`), duck curve & unit commitment (`[28]`, `[29]`), September 2025 outages and 2026 gas units (`[10]`, `[12]`, `[13]`, `[18]`, `[19]`, `[31]`), and public data sources (`[1]`--`[6]`, `[30]`).

- **Scenario: Ten-paper comparative summary table**
  - **WHEN** Table I is rendered
  - **THEN** it compares `[20]`, `[21]`, `[22]`, `[23]`, `[24]`, `[26]`, `[27]`, `[28]`, `[29]`, and `[14]` alongside the proposed GridReserve Agent across Year, Problem, AI Method, Domain Focus, Dataset, Key Findings, and Limitation.

### Requirement 4: Section III -- Proposed Design
The paper SHALL specify the system design of GridReserve Agent, including domain mental models (M1--M5), the 8-module architecture with a vector diagram, mathematical equations, and formal pseudocode.

- **Scenario: Domain mental models M1--M5 integrated**
  - **WHEN** Section III-A explains design principles
  - **THEN** it articulates M1 (reserve as insurance/trade-off), M2 (quality over quantity), M3 (`N-1` contingency against `C_max = 130 x 10^4 kW`), M4 (day vs. night peak distinction), and M5 (uncertainty-aware interval outputs).

- **Scenario: Eight-module architecture and TikZ diagram**
  - **WHEN** Section III-B is compiled
  - **THEN** it describes Modules 1--8 (including 4 agent intents, 6 cleaning rules, anti-leakage policy excluding same-day unit/PV/wind outputs from forecasting, 7-week same-weekday attribution, 175-unit + new gas KB + RAG, verification gate, and Streamlit UI) accompanied by a non-overlapping TikZ diagram (`Fig. 1`).

- **Scenario: Mathematical formulation and dual-logic precedence**
  - **WHEN** Section III-C defines the scenario equations
  - **THEN** it specifies `S' = S_ref - sum(C_u)`, `R = S' - L_hat`, `r = (R / L_hat) * 100%`, `eta_{N-1} = R / C_max`, and explicitly states that absolute capacity thresholds (`<= 50` Black, `<= 90` Red) take precedence over percentage thresholds (`<= 6%` Orange, `< 10%` Yellow, else Green).

- **Scenario: Formal pseudocode for Agent and Light Classifier**
  - **WHEN** Section III-D presents control flow
  - **THEN** Algorithm 1 (`GridReserve Agent Execution Pipeline`) covers `SafeRefusal`, subtask dispatch, `Verify(R_out, tool_outputs)` with up to 2 retries (3 total attempts), and `SafeFailure`, and Algorithm 2 (`ClassifyLight`) implements the exact five-tier precedence logic.

### Requirement 5: Section IV -- Experiment and Evaluation
The paper SHALL document the integrated datasets, separate preliminary EDA from formal experimental results, specify the E1--E4 evaluation suite, and use `[TBD]` placeholders for unexecuted formal experiments.

- **Scenario: Dataset summary and cleaning diagnostics**
  - **WHEN** Sections IV-A and IV-B are inspected
  - **THEN** Table II documents all five public datasets (`1,096`, `608`, `6`, `1,339 x 3`, and `175` units) and Section IV-B clearly labels preliminary EDA metrics (`0.014%` MRE over 365 overlapping days, 6 corrected reserve-rate errors, light counts, correlation coefficients `0.75`, `-0.07`, `0.92`, naive reserve-rate MAE `5.8--6.2`, exploratory linear load MAE `100--150` vs. `367`, and Sep 2025 Linkou #2 zero output trace) as pre-experimental feasibility checks.

- **Scenario: E1--E4 protocol and honest placeholders**
  - **WHEN** Sections IV-C and IV-D specify formal evaluation
  - **THEN** Table III details E1 (rolling load forecasting + weather-noise sensitivity), E2 (Sep 9--23, 2025 outage backtest), E3 (40-question QA benchmark comparing Pure LLM, LLM+RAG, and ablation of the verification gate), and E4 (boundary unit tests), with explicit `[TBD]` markers for unrun results and zero fabricated numbers.

### Requirement 6: Section V -- Conclusion and Future Work
The paper SHALL summarize technical contributions, list six structural limitations transparently, and outline future extensions.

- **Scenario: Explicit limitations and 10-minute data roadmap**
  - **WHEN** Section V concludes the paper
  - **THEN** it states the six known limitations (dispatch-driven reserve rate, missing nighttime peak reserve in public daily CSVs, outdated static unit table missing IPPs/renewables, weather observation upper bound, zero Orange-light events in 3.7 years, output delta vs. available capacity) and identifies nighttime net-load reconstruction via Taipower 10-minute unit generation data `[30]` plus 2026 summer validation as future work.

### Requirement 7: References
The paper SHALL format all 31 citations from `myplan/期末專題提案.pdf` in IEEE conference reference style compatible with `pdfLaTeX` and synchronized with `myRef/references.bib`.

- **Scenario: Complete and pdfLaTeX-safe bibliography**
  - **WHEN** the bibliography is inspected
  - **THEN** all 31 entries (`\bibitem{ref1}` through `\bibitem{ref31}`) appear in exact `[1]`--`[31]` order using English bibliographic titles, `\url{...}` links, zero raw CJK characters, and zero emojis.
