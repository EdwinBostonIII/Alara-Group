# Scenario: Supply Chain Prediction (Ops)

**Category:** Operations / Logistics
**Trigger:** A manufacturing client keeps running out of raw materials because their forecasting is based on "last year's Excel spreadsheet," failing to account for weather, strikes, or geopolitical shifts.

---

## 1. The Situation
The client buys steel and microchips. They order based on a simple moving average. Then a port strike happens, or a war breaks out, and they are caught flat-footed. They want AI to "predict the future."

## 2. The Diagnosis
Traditional forecasting is univariate (looks only at past sales). AI forecasting is multivariate (looks at sales + weather + news + oil prices).

## 3. The Alara Playbook

### Phase 1: Data Unification (Month 1-2)
1.  **Internal Data**: ERP data (Orders, Inventory levels).
2.  **External Signals**: We integrate APIs for:
    - Weather patterns (for shipping delays).
    - Commodity prices.
    - News sentiment (e.g., "Strike" mentions in port cities).

### Phase 2: The Model Build (Month 3-4)
1.  **Time-Series Forecasting**: Use models like "Temporal Fusion Transformers" (Google) or "Prophet" (Meta) enhanced with external regressors.
2.  **Scenario Planning**: We don't just give one number. We give scenarios:
    - *Base Case*: Demand +5%.
    - *Risk Case*: Port strike lasts 2 weeks -> Inventory -20%.

### Phase 3: The "Nudge" System
1.  **Actionable Alerts**: The system doesn't just show a dashboard. It sends an email to the procurement manager:
    - "Alert: High risk of resin shortage in Q3 due to hurricane forecast. Recommendation: Increase safety stock by 15% now."

## 4. The "Gotchas"
- **Black Swans**: AI cannot predict truly unprecedented events (like COVID-19 in 2019). It relies on patterns.
- **Data Latency**: If the ERP data is updated only once a month, the prediction is always stale. We need real-time data feeds.
