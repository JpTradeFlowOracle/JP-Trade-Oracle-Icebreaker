# 🏛️ JP-Trade-Oracle Icebreaker
**High-Precision Economic Intelligence Node for the Japanese Market**

## 📊 Project Overview
JP-Trade-Oracle Icebreaker is an autonomous data node designed to detect
**Structural Margin Anomalies** within the Japanese supply chain.

Two independent analytical engines run in parallel:

**V1 — CPI Signal:** Cross-references real-time CPI data with official **e-Stat** releases to quantify how far each item is rising above Japan's inflation baseline. FX-adjusted delta strips out yen depreciation to isolate domestic gouging from currency effects.

**anomaly_core — Cost Signal:** A multivariate regression engine trained on 36 months of import costs, freight rates, exchange rates, wages, and energy prices. Outputs an **SJ-Score** — the statistically standardized gap between what retail prices *should* be given actual input costs, and what they *are*. When both signals fire simultaneously, the combined verdict is **CONFIRMED**.

## ⚡ API Specifications
Optimized for **Machine-to-Machine (M2M)** integration.
AI agents and financial models can programmatically query
Japanese economic health in real time.

- **Status:** Operational
- **Endpoint:** `https://ifgk6mi0oc.execute-api.ap-northeast-1.amazonaws.com`
- **Docs:** `https://ifgk6mi0oc.execute-api.ap-northeast-1.amazonaws.com/docs`

## 💰 Pricing
- **Rate:** $0.30 USDC per Analytical Request
- **Protocol:** Skyfire

## 🔍 Analytical Metrics

**V1 Signals**
- **Delta Index:** Price divergence from baseline CPI inflation
- **FX-Adjusted Delta:** Delta with yen depreciation stripped out
- **Alert Levels:** EXTREME / WARNING / WATCH / FAIR

**anomaly_core Signals**
- **SJ-Score:** Cost-justified price deviation (σ units, Huber regression)
- **Signal Strength:** UI-ready intensity indicator (0.0–1.0)
- **Confidence:** Model reliability score (R² × 0.6 + sign consistency × 0.4)
- **Combined Verdict:** CONFIRMED / POSSIBLE / FAIR
- **Reason Codes:** Machine-readable causal flags (e.g. `IMPORT_COST_DOWN`, `PRICE_STICKINESS`)
- **Summary JP:** Japanese-language narrative for human review

**Coverage**
- **Sectors:** Energy, Food, IT/Services, Logistics, Housing, Medical, Industrial, Macro
- **Update Cycle:** Every 12 hours

## 🛠️ Tech Stack
- **Runtime:** Python / FastAPI
- **Data Sources:** e-Stat · FRED · USDA MARS · USDA GTR · Bank of Japan API · Ministry of Health, Labour and Welfare
- **Model:** PCA + HuberRegressor · EWM rolling z-score · TimeSeriesCV lag optimization
- **Auth:** Skyfire Protocol (ES256 JWT / JWKS)
- **Deployment:** AWS Lambda + API Gateway

---
*Developed by **JpTradeFlowOracle** — Bridging the gap between raw government data and actionable economic intelligence.*
