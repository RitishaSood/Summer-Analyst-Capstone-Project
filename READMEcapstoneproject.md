# Smart Parking Dynamic Pricing System

## 🚗 Overview

The **Smart Parking Dynamic Pricing System** is a Capstone project leveraging real-time data streams and advanced analytics to optimize parking prices dynamically. The system adjusts parking rates on-the-fly based on live occupancy, demand, queue lengths, traffic, events, and other contextual signals. This maximizes revenue for operators and improves convenience for users, all via a scalable, maintainable, and insightful data pipeline.

---

## 🛠 Tech Stack

- **Python** – Primary language for data processing and analytics
- **[Pathway](https://pathway.com/)** – Real-time streaming data framework
- **[Bokeh](https://bokeh.org/)** & **[Panel](https://panel.holoviz.org/)** – Interactive visualizations and dashboards
- **Pandas** – Data manipulation and feature engineering
- **Mermaid** – Architecture diagrams
- **Jupyter Notebook** – Prototyping and workflow documentation

---

## 🏗️ System Architecture

```mermaid
flowchart TD
    A["CSV Data Source (Parking Dataset)"] -->|Replay/Stream| B[Pathway Streaming Pipeline]
    B --> C[Feature Engineering & Aggregation]
    C --> D[Dynamic Pricing Algorithm]
    D --> E[Visualization Engine (Bokeh/Panel)]
    E --> F[Dashboard/Reports]
    F --> G[API Endpoint (Future)]
    B --> H[Monitoring]
    H --> I[Logs & Metrics]


---

## ⚙️ Project Architecture & Workflow

### 1. **Data Ingestion**
   - Parking lot data (CSV) is streamed using Pathway's `replay_csv` to simulate real-time sensor feeds.
   - Data features include: lot ID, capacity, location, occupancy, vehicle type, queue length, traffic, special day flags, and timestamps.

### 2. **Preprocessing & Feature Engineering**
   - Combine date/time into unified timestamps.
   - Sort and clean data.
   - Generate features: occupancy rate, demand volatility, hourly/daily trends, queue length, etc.

### 3. **Streaming Processing (Pathway)**
   - Pathway handles event-by-event record ingestion and stateful streaming aggregations.
   - Tumbling/daily window aggregations are used for dynamic computations.

### 4. **Dynamic Pricing Algorithm**
   - Baseline: Price is a function of max/min occupancy swings and capacity.
   - Extendable: Incorporates traffic, queue, special events, vehicle type for more advanced pricing models (ML/optimization).
   - Output: Recommended price per lot per time window.

### 5. **Visualization & Dashboard**
   - Real-time trends, occupancy, and pricing visualized via Bokeh and Panel.
   - Interactive dashboard for stakeholders to monitor system performance.

### 6. **Scalability & Extensibility**
   - Modular design: Plug in new data sources, pricing models, or dashboard components.
   - (Planned) API endpoints to serve prices to external apps.

---

## 📊 Sample Workflow

1. **Upload** your dataset (e.g., `Capstone dataset.csv`) to the project directory.
2. **Launch** `CapstoneProjectFinalNotebook.ipynb` and execute the cells.
3. **Observe** the live dashboard as prices respond to streaming data.
4. **Extend** the pricing logic in `DynamicPricingFunction` for more sophisticated strategies.

---

## 📝 Documentation & References

- [Pathway Documentation](https://pathway.com/docs/)
- [Bokeh Documentation](https://docs.bokeh.org/)
- [Panel Documentation](https://panel.holoviz.org/)
- [Mermaid Live Editor](https://mermaid-js.github.io/mermaid-live-editor/)
- Example dataset schema:
    - `SystemCodeNumber`, `Capacity`, `Latitude`, `Longitude`, `Occupancy`, `VehicleType`, `TrafficConditionNearby`, `QueueLength`, `IsSpecialDay`, `LastUpdatedDate`, `LastUpdatedTime`

---

## 🚀 Extending the Project

- Add machine learning models for demand forecasting.
- Integrate real-time city-wide traffic or event feeds.
- Deploy as a REST API for real-world parking apps.
- Enhance dashboard with more KPIs, predictive analytics, and alerts.

---

## 📄 License

This repository is for educational and demonstration purposes as part of a Capstone project.
