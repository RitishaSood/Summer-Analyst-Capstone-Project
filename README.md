# Smart Parking Dynamic Pricing System

## Overview

This project is a Capstone implementation of a **Smart Parking Dynamic Pricing System** using real-time data streams and advanced analytics. The goal is to optimize parking prices dynamically based on real-time occupancy, demand, and other contextual factors, maximizing both revenue for operators and efficiency/convenience for users.

The solution leverages the [Pathway](https://pathway.com/) streaming data framework in Python, with interactive visualizations powered by [Bokeh](https://bokeh.org/) and [Panel](https://panel.holoviz.org/). It demonstrates how to process, aggregate, and analyze live parking data to generate actionable pricing strategies.

---

## Problem Statement

> **Objective:**  
> Design and implement a real-time dynamic pricing algorithm for smart parking lots, using live data on occupancy, capacity, vehicle types, traffic conditions, special events, and other relevant features.
>
> **Key Goals:**
> - Ingest and process real-time data streams from multiple parking locations.
> - Compute optimal prices dynamically, adapting to changes in demand and supply.
> - Visualize pricing trends and system performance over time.
> - Ensure scalability, interpretability, and actionable insights.

---

## Dataset

The dataset contains real/realistic parking lot data with the following features:
- **ID:** Unique observation identifier
- **SystemCodeNumber:** Parking lot identifier
- **Capacity:** Total parking spots
- **Latitude/Longitude:** Location
- **Occupancy:** Current number of occupied spots
- **VehicleType:** Type of parked vehicle (car, bike, cycle, truck)
- **TrafficConditionNearby:** Low/Average/High
- **QueueLength:** Queue at entry (proxy for demand)
- **IsSpecialDay:** Binary indicator for special events/holidays
- **LastUpdatedDate** & **LastUpdatedTime:** Observation timestamp

---

## Solution Approach

1. **Data Ingestion & Preprocessing**
    - Combine date & time into a single timestamp.
    - Sort records chronologically.
    - Select relevant features for pricing (expandable as needed).

2. **Streaming Simulation**
    - Use Pathway's `replay_csv` to simulate real-time data ingestion at a controlled rate.

3. **Feature Engineering**
    - Extract temporal features (e.g., day, hour).
    - Compute occupancy rates, demand volatility, and other dynamic features.

4. **Dynamic Pricing Model**
    - Implement a baseline (e.g., fluctuation-based) dynamic pricing function.
    - (Extendable) Incorporate advanced models using demand, queue, special events, vehicle types, etc.

5. **Windowed Aggregation**
    - Aggregate data in daily tumbling windows (or other intervals).
    - Calculate statistics (max/min occupancy, capacity) for pricing logic.

6. **Visualization**
    - Use Bokeh/Panel to plot daily pricing trends and system performance.

7. **Execution**
    - Run the Pathway pipeline to enable real-time stream processing.

---

## Usage

1. **Environment Setup**

   Install required packages:
   ```bash
   pip install pathway bokeh panel
   ```

2. **Upload Dataset**

   Place your CSV dataset (e.g., `Captone dataset.csv`) in the working directory.

3. **Run the Notebook**

   Open and execute `CapstoneProjectFinalNotebook.ipynb` step by step.

4. **Visualize Results**

   Interactive Bokeh plots will display dynamic pricing trends.

---

## Example Pricing Logic

```python
price = 10 + (occ_max - occ_min) / cap
```
- **Intuition:** Higher volatility in occupancy → higher demand → higher price.

> **Note:**  
> The baseline model is intentionally simple. You are encouraged to design and implement more sophisticated algorithms that incorporate additional features for improved pricing optimization.

---

## Extending the Project

- Expand the pricing model to use all available features (vehicle type, queue, traffic, special days).
- Explore machine learning or optimization-based approaches.
- Support multi-lot, multi-city scenarios.
- Add API endpoints for real-world integration.
- Enhance the dashboard with more KPIs and user interactivity.

---

## References

- [Pathway Documentation](https://pathway.com/docs/)
- [Bokeh Documentation](https://docs.bokeh.org/)
- [Panel Documentation](https://panel.holoviz.org/)

---

## License

This project is for educational purposes as part of a Capstone assignment.