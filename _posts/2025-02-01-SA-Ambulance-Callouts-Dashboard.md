---
layout: post
title: SA Ambulance Service Callouts Dashboard
image: "/posts/saas-callouts-dashboard.png"
tags: [Dashboard, Power BI, Data Visualisation, Data Mining, Data Modelling]
---

## Project Overview
The **SA Ambulance Service Callouts Dashboard** is a Power BI visualisation tool that aggregates approx **185,000 pager messages** sent to the **South Australian Ambulance Service (SAAS)** over a **five-month period (August 1st, 2024 – February 28th, 2025)**. This dashboard integrates **geographic and population data** to offer a **state-wide overview of emergency callout patterns**, providing timely and localised insights that would not otherwise be available.

---

## The Dashboard
<iframe seamless frameborder="0" src="https://app.powerbi.com/view?r=eyJrIjoiM2VkNmY0ZmUtN2I5Yy00YjM3LWE0N2QtNjZhZGJjNWM4N2M1IiwidCI6ImMwNmY1NDJlLTQ3NWEtNDUzMy1iMTM1LTVkMjI3MDk4ZTViYyJ9" width = '1090' height = '650'></iframe>

---

## Target Users & Audience
This dashboard serves a wide range of stakeholders, including:
- **Governmental Agencies** - for resource allocation and emergency response planning.
- **Local Governments** - to assess healthcare demands and infrastructure needs.
- **Insurance Companies & Health Providers** - for risk assessment and policy adjustments.
- **General Public** - for awareness of emergency response trends in their local community.

---

## Business Value & Real-World Impact
### **1. Enhanced Decision-Making & Operational Efficiency**
- **Timely Insights**: Unlike traditional health reports that rely on aggregated and delayed data, this dashboard provides near real-time **visibility into emergency trends**.
- **Geographic & Population-Based Analysis**: By **mapping suburb-level callout data to local government areas (LGAs)**, the dashboard **integrates population statistics**, allowing for **per capita comparisons and deeper analysis**.
- **Trend Identification**: Health agencies can **detect patterns in ambulance callouts**, helping to anticipate healthcare service demands.


### **2. Automation & Efficiency Gains**
- **Automated Data Collection & Transformation**: A **data pipeline scrapes a live-feed of pager messages daily**, cleaning and transforming them into structured tabular formats.
- **Dynamic Filtering & Visualisation**: Users can **drill down by region, time period, or callout type**, enabling quick insights without manual data manipulation.
- **Elimination of Data Silos**: This model centralises disparate datasets (pager messages, callout codes, station codes, geographic boundaries and population data) into a single source of truth.


### **3. Differentiation from Existing Solutions**
- **Comparative Analytics**: The **integration of local government and population data** enables **per capita comparisons**, making it easier to identify areas with disproportionately high emergency response demands.
- **Scalability & Long-Term Value**: Unlike static reports, this dashboard continues to evolve with ongoing data collection, making historical and predictive trend analysis possible.

---

## Technical Implementation
### **Core Technologies & Methods**
- **Text Parsing & Data Structuring**: Converts **unstructured pager messages into structured datasets**, making them queryable for analytics.
- **Snowflake Schema Data Modeling**: Optimised for **handling large-scale temporal and geographic data** within Power BI.
- **Advanced Power BI Measures**: Enables **time-series analysis, anomaly detection, spatial and temporal heatmaps**.


### **Challenges & Solutions**
- **Data Sparsity & Early Noise Issues**: Initially, **limited data volume made trend detection difficult**. However, after around three months (**~80,000 messages**), meaningful patterns had begun to stabilise.
- **Handling Unstructured Text Data**: Developed a **custom parsing pipeline** to extract **priority, suburb, dispatched unit, timestamps, and incident types** from pager messages.


### **Deployment & Scalability Considerations**
- **Deployed as a Power BI Dashboard** – accessible via **Power BI Service** for secure sharing and collaboration.
- **Scalable Data Model** – supports ongoing data ingestion, allowing for extended historical analysis.


## Future Applications & Expansions
- **Long-Term Data Collection**: Extending to a **12-month dataset** would allow for **year-over-year comparisons**, helping policymakers assess seasonal trends.
- **Real-Time Anomaly Detection**: Increasing the **data collection frequency (e.g., every 15 minutes)** could enable **real-time alerts for healthcare providers**.
  - Example: "Anomalous trend in **breathing problems** reported in **XYZ City Council** in the **past hour**."
- **Integration with Predictive Analytics & AI**: Incorporating machine learning models could enhance **forecasting capabilities**, potentially allowing hospitals to **anticipate ambulance surges before they occur**.