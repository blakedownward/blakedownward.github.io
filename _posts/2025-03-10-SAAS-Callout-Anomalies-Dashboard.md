---
layout: post
title: SA Ambulance Service Anomaly Dashboard
image: "/posts/SAAS-anomaly-dashboard.png"
tags: [Dashboard, Power BI, Data Visualisation, Anomaly Detection, Isolation Forest]
---

## Project Overview
The **SA Ambulance Service Anomalies Dashboard** is a Power BI dashboard that highlights **potential** anomalies detected over the previous 7 days. Behind the scenes, we use a Machine Learning algorithm called an "Isolation Forest" for detecting anomolous spikes in daily callouts per Local Government Area, and type of event (eg, "Falls", "Chest Pain", "Breathing"). The aim of this dashboard is to quickly show recent anomalies in South Australia, and the raw pager messages which triggered/contributed to the anomaly.

---

## The Dashboard
<iframe title="seven-day-anomaly-dashboard" width="1090" height="650" src="https://app.powerbi.com/view?r=eyJrIjoiZTg4MDM1NGEtOWQ5ZS00ZWFjLWEzODktOWM1ZmZjZjFmNzI4IiwidCI6ImMwNmY1NDJlLTQ3NWEtNDUzMy1iMTM1LTVkMjI3MDk4ZTViYyJ9" frameborder="0" allowFullScreen="true"></iframe>

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
- **Ensemble Anomaly Detection**: Uses a combination of **rolling time-series statistics** and an **isolation forest** to detect anomolous spikes in daily callouts for each event type in each geographic area.


### **Challenges & Solutions**
- **Temporal Distribution**: Exploratory Data Analysis showed a significant difference between weekday and weekend callout distributions. Similarly with weekends, public holidays display different behaviour to "workdays". To help the isolation forest understand these differences, we engineered a "non-workday" feature to highlight weekends and public holidays.
- **Handling Imbalanced Populations**: Differences between Local Government populations can skew the raw volume data. To overcome this, we've **normalised callouts on a per capita basis** to allow direct comparison between geographical regions.


### **Deployment & Scalability Considerations**
- **Deployed as a Power BI Dashboard** – accessible via **Power BI Service** for secure sharing and collaboration.
- **Slim Data Model** - Focusing only on anomalies detected in the past seven days, this dashboard remains lightweight whilst providing the most **up-to-date** information for stakeholders.


## Future Applications & Expansions
- **Real-Time Anomaly Detection**: Increasing the **data collection frequency (e.g., every 15 minutes or hour)** could enable **near real-time alerts for healthcare providers**.
  - Example: "Anomalous trend in **breathing problems** reported in **XYZ City Council** in the **past hour**."
- **Integration with Predictive Analytics & AI**: Incorporating machine learning models could enhance **forecasting capabilities**, potentially allowing hospitals to **anticipate ambulance surges before they occur**.