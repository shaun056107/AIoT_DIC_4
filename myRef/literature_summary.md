# Literature Summary and Domain Synthesis (`myRef`)

This summary extracts the 10 key comparative references, the 5 domain mental models, and the 3 unresolved policy/engineering debates from `myplan/期末專題提案.pdf` to support IEEE ICEIB paper drafting (`ICEIB paper/main.txt`).

## 1. Comparative Summary of Key References

| Ref. | Year | Problem | AI Method | Domain Knowledge | Dataset | Key Findings | Limitation |
|---|---|---|---|---|---|---|---|
| `[20]` GridMind | 2025 | Natural-language grid analysis and operations | LLM multi-agent + deterministic solver | Optimal power flow (OPF), N-1 contingency | IEEE 14, 30, 57, 118, 300 buses | Integrates LLM reasoning with power-system solvers | Focuses on simulated buses; does not process Taiwan public operational data |
| `[21]` X-GridAgent | 2025 | Lowering expert barrier for grid analysis | Hierarchical planning & execution; MCP; KB | Power flow analysis | Texas 2k-bus synthetic & real grid | Enables natural-language grid analysis | Assumes steady-state grid conditions |
| `[22]` Grid-Agent | 2025 | Automated detection and repair of grid violations | Multi-agent: planner + validation agent | Voltage and thermal overload limits | IEEE 30/69, CIGRE MV test systems | Combines semantic reasoning with numerical precision; explainable | Focuses on power-flow violation repair rather than supply adequacy |
| `[23]` LLM Power Survey | 2025 | LLM applications and challenges in power systems | Literature survey | Power system operations | N/A | Highlights limited domain data, reliability, and explainability barriers | Survey only; no implemented system |
| `[24]` LLM Renewable Survey | 2026 | Forecast-to-decision disconnect; LLM hallucination | Quantile regression forest, conformal prediction, LLM agent | Reserve procurement, grid-aware decisions | N/A | Proposes hybrid ML + tool-constrained agent architecture | Survey only; no Taiwan operational implementation |
| `[26]` Taiwan Netload | 2025 | Load and net-load forecasting | SARIMAX, NNARX, FPCA hybrid | Renewable generation and meteorology | Taipower hourly load and renewable data | Benchmarks statistical vs. ML forecasting methods | Predicts load only; no reserve or outage scenarios |
| `[27]` Week-ahead Peak | 2023 | Week-ahead daily peak load forecasting | Hybrid CNN | Temperature impact | Taiwan daily peak load and temperature | Outperforms MLP, RNN, VARMA, and SVM | Point forecasting only; no explanation or decision layer |
| `[28]` Taiwan 2025 UC | 2020 | Unit commitment under high renewable penetration | Optimization (AMPL/CPLEX) | Duck curve, pumped-storage hydro | Taiwan system scenario | Pumped storage mitigates duck-curve ramping | Planning-layer study; not daily operational risk analysis |
| `[29]` Probabilistic Duck | 2019 | Net-load uncertainty under high PV penetration | Probabilistic modeling | Duck curve, ramping uncertainty | Qinghai, China | Quantifies probabilistic net-load and ramping curves | Non-Taiwan power system |
| `[14]` 513/517 Blackout Analysis | 2022 | Evaluating whether reserve margins are overestimated | Investigative analysis | Fast/slow reserve, solar PV inclusion | News and operational reports | Demonstrates gap between headline reserve rate and fast-ramping capacity | Journalistic analysis; requires quantitative cross-validation |

## 2. Research Gap Statement

- **Existing Research:** LLM grid agents target synthetic power-flow simulation (`[20]`--`[22]`); Taiwanese ML studies target point load/net-load prediction (`[26]`, `[27]`); unit-commitment studies focus on long-term planning (`[28]`, `[29]`).
- **Gap:** None combine Taiwan's public operational CSVs, Taipower's dual-logic five-tier supply indicator regulations, and generator unit inventories into a conversational, outage-aware, numerically traceable Domain AI Agent while respecting the fact that operating reserve rate is a post-dispatch outcome (`r ~ -0.07` with temperature).
- **GridReserve Agent Contribution:** ML handles weather-driven peak load intervals (`10/50/90%` + conformal calibration); deterministic rules handle supply deductions, indicator lights, and `N-1` ratio; the LLM handles intent parsing and narrative synthesis behind a strict numerical verification gate.

## 3. Domain Mental Models (M1--M5) and Policy Debates (Q2)

- **M1 (Reserve as Insurance):** Reliability carries cost and environmental trade-offs (e.g., Hsinta coal units restricted under EIA permits to dispatch only below 8% reserve `[18]`).
- **M2 (Quality Over Quantity):** Fast-ramping hydro/gas capacity differs sharply from slow thermal units (`513` blackout: ~10% nominal vs. ~2% fast-start `[14]`).
- **M3 (N-1 Contingency):** System adequacy must survive single-largest-unit trips (`C_max = 130 x 10^4 kW`, Taichung New Units 1 & 2 `[31]`).
- **M4 (Day vs. Night Peak):** Daytime peaks have PV support; night peaks do not (`[4]`, `[7]`, `[8]`).
- **M5 (Uncertainty-Linked Decisions):** Calibrated quantiles support risk thresholds better than single point estimates (`[24]`, `[29]`).

Three active debates informed system caveats:
1. **10% vs. 6% Reserve Standard:** Spinning (6%) + non-spinning (4%) split (`[16]`) vs. vulnerability to single-plant trips like the ~8% 815 Tatan event (`[17]`). Current indicator rules retain 10% and 6% tiers (`[11]`).
2. **Overestimation of Effective Supply:** Official reserve vs. fast-dispatchable operating reserve (`[14]`).
3. **Optimism of Official Forecasts:** Scheduled new units vs. commissioning delays and outages (e.g., September 2025 Hsinta/Linkou drops from ~14% toward 3%--4% `[9]`, `[10]`, `[12]`, `[13]`).
