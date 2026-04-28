# 🚆 UK Train Rides Dashboard – Insight Hunters 📊

> _"Hunting the Unknown, Revealing the Unseen!"_

A full-scale Power BI project analyzing over **32,000 UK train journeys** to uncover patterns in **delays**, **revenue**, **customer behavior**, and **operational efficiency**. This interactive dashboard suite enables transportation analysts and decision-makers to act on data-driven KPIs and business intelligence.

---

## 🧑‍💼 Team Overview

| Member Name | Role(s) | Background | Governorate |
|-------------|---------|------------|-------------|
| **Mazen Moustafa Sayem Abdel-tawwab** | Team Leader, Dashboard Designer, Data Cleaning & Modeling | Computer Science & AI | Al Fayoum |
| **Shahd Noman Esawy Esawy** | Operational Dashboard Developer | Commerce (Accounting) | Al Beheira |
| **Asmaa Salah Mohamed Alhady** | Executive Summary & Strategic Dashboard | Statistics | Al Sharqia |
| **Abdallh Mohamed Abdelmonem Soliman** | Home Page & Navigation | Computer Science (AI) | Al Dakahlia |
| **Saif Mohammed Godah** | Analytical Dashboard Developer | Computer Science | Al Dakahlia |

---

## 🎯 Objectives

- ✅ Detect and visualize major **delay reasons** and associated **financial losses**
- ✅ Monitor **journey statuses** (on-time, delayed, canceled) across routes
- ✅ Break down **ticket class distributions** and **purchase patterns**
- ✅ Reveal **high-traffic routes and stations**
- ✅ Analyze **weekly revenue trends** and demand fluctuations
- ✅ Build a scalable **Star Schema data model**

---

## 📈 Business Questions Addressed

### 📊 Performance & Delay Analysis
- What are the most frequent **delay reasons** and their **refund costs**?
- Which delay reasons result in the highest **avg cost per delay**?
- How do **actual vs. scheduled arrival times** compare across delay reasons?

### 🗺️ Departure & Arrival Analysis
- What are the busiest **departure and arrival stations**?
- How are **ticket classes** and **journey statuses** distributed geographically?
- Which station pairs generate the most **trip volume**?

### ⚙️ Operational Efficiency & Delay Impact
- Which **routes** suffer the most delays by reason?
- What is the total **refund loss** broken down by delay cause?
- What percentage of delayed trips result in **refund requests**?

### 💰 Revenue Trends
- How does **weekly revenue** fluctuate across Q1 and Q2?
- What are the **peak and trough weeks** for revenue?

---

## 🧼 Data Preparation

### 🔍 Cleaning Steps
- Replaced missing `Reason for Delay` with `"No Delay"` when journey status = "On Time"
- Kept `Actual Arrival Time` as null for canceled trips
- Verified datetime fields and calculated delay durations
- Removed duplicates and unnecessary calculated columns

### 🧠 Data Model – Star Schema

| Table | Description |
|-------|-------------|
| `Fact Transactions` | Central fact table (ticket sales, delays, routes) |
| `Dim Tickets` | Ticket class and type |
| `Dim Route` | Departure and arrival stations |
| `Dim Status` | Journey status and delay reasons |
| `Dim Calendar` | Purchase and journey date hierarchy |
| `Dim Buying Process` | Payment method and purchase type |
| `Dim Railcard` | Customer segmentation |

---

## 💡 Key KPIs Tracked

| KPI | Value |
|-----|-------|
| 🔢 Total Number of Trips | ~31,653 |
| 💰 Total Refund Loss | $34.8K |
| 📉 Avg Cost per Delay | $1.10 |
| 🔁 Total Delay Reasons | 7 |
| 🌦️ Most Frequent Delay Cause | Weather (1,372 trips) |
| 💸 Highest Refund Loss Cause | Technical Issue ($13.5K) |
| 🎟️ Dominant Ticket Class | Standard (79.86%) |
| ✅ On-Time Rate | 86.82% |

---

## 💻 Key DAX Measures

```DAX
-- Total Revenue
Total Revenue = SUM('Fact Transactions'[Price])

-- Average Delay Duration
Average Delay Time = AVERAGEX('Fact Transactions', [Delay Minutes])

-- Delay Minutes (Calculated Column)
Delay Minutes =
SUM('Fact Transactions'[Actual Arrival Time])
- SUM('Fact Transactions'[Arrival Time])

-- Cost Per Delay
Avg Cost per Delay = DIVIDE([Total Delay Cost], [Delay Reason Count])

-- Delayed Trips (excluding No Delay)
Delayed Trips by Reason =
COUNTROWS(
    FILTER('Fact Transactions',
    'Fact Transactions'[Reason for Delay] <> "No Delay")
)

-- Distinct Delay Reasons
Delay Reasons Distinct =
DISTINCTCOUNT('Fact Transactions'[Reason for Delay])
```

---

## 🎨 Dashboard Design

### 🎨 Color Palette

| Purpose | Color |
|---------|-------|
| Background | `#F7F7F7` |
| Highlights & KPIs | `#FFB22C` |
| Charts & Accents | `#854836` |
| Text | `#000000` |

### 📊 Report Structure

| Page | Description |
|------|-------------|
| **Home** | Narrative story introducing the dashboard and key context |
| **Navigation** | Interactive sidebar to all report pages |
| **Executive Dashboard** | High-level KPIs: trips by station, revenue by date, ticket class split, delayed trips by reason |
| **Performance & Delay Analysis** | Trip volumes by day/month/quarter, journey status breakdown |
| **Departure & Arrival Analysis** | Map visuals, station-level trip counts, ticket class & status donut charts |
| **Operational Efficiency & Delay Impact** | Delay reason matrix by route, refund loss bars, avg actual vs. scheduled arrival |
| **Predictive Delay Page 1** | Route-level delay breakdown table by cause with totals |
| **Predictive Delay Page 2** | Decomposition tree & Sankey diagram for trip flow analysis |
| **Revenue Trends** | Weekly total revenue line chart across Q1–Q2 2024 |
| **Q&A** | Natural language query interface for ad-hoc exploration |
| **Closure & Recommendations** | Strategic takeaways and future action points |
| **Measures Dictionary** | Full DAX measures reference with descriptions and expressions |

---

## 🖼️ Dashboard Previews

### 🏠 Home & Navigation

![Home Page](assets/dashboard_home.png)
*Narrative landing page covering network scale, delay costs, revenue trends, and data-driven goals.*

![Navigation Panel](assets/dashboard_nav.png)
*Interactive sidebar with links to all report pages.*

---

### 📋 Executive Dashboard

![Executive Dashboard](assets/dashboard_strategic.png)
*High-level view of total rides by station, delayed trips by reason, ticket class distribution, and monthly revenue.*

---

### 📊 Performance & Delay Analysis

![Performance & Delay Analysis](assets/dashboard_analytical_1.png)
*Trip volumes by day of week and month, on-time vs. delayed vs. cancelled breakdown, quarterly filter.*

---

### 🗺️ Departure & Arrival Analysis

![Departure & Arrival Analysis](assets/dashboard_analytical_2.png)
*Map-based visuals for station activity, trip counts by route, and ticket class/journey status distributions.*

---

### ⚙️ Operational Efficiency & Delay Impact

![Operational Efficiency](assets/dashboard_operational_1.png)
*Refund loss by delay reason, refund request rates, and avg actual vs. scheduled arrival time comparison.*

---

### 🔍 Predictive Delay Pages

![Predictive Delay Page 1](assets/dashboard_operational_2.png)
*Route-level matrix showing delay counts by cause (Weather, Signal Failure, Technical Issue, etc.) with row totals.*

![Predictive Delay Page 2](assets/dashboard_operational_3.png)
*Decomposition tree and Sankey diagram tracing trip flow from departure station through delay reason to refund outcome.*

---

### 💰 Revenue Trends

![Revenue Trends](assets/dashboard_operational_4.png)
*Weekly total revenue across Q1–Q2 2024, highlighting peaks (~$47K) and troughs (~$5K) by week number.*

---

### 💬 Q&A

![Q&A Page](assets/dashboard_Q&A.png)
*Natural language query interface with suggested questions for ad-hoc data exploration.*

---

### 💡 Closure & Recommendations

![Recommendations](assets/dashboard_recommendations.png)
*Strategic recommendations across on-time performance, financial optimization, and passenger-centric improvements.*

---

### 📖 Measures Dictionary

![Data Dictionary](assets/dashboard_data_dictionary.png)
*Full reference of all DAX measures: names, descriptions, and expressions organized by category.*

---

## 🔑 Key Findings

- **Weather** is the most frequent delay cause (1,372 trips), but **Technical Issues** drive the highest refund loss ($13.5K)
- **86.82%** of trips ran on time; only 7.24% delayed and 5.94% cancelled
- **Manchester Piccadilly → Liverpool Lime Street** is the most delay-prone route (644 total delays)
- **Standard class** dominates at 79.86% of ticket sales
- Revenue peaked at **~$47K/week** and dropped as low as **~$5K/week**, indicating high demand volatility
- **Liverpool Lime Street → London Euston** recorded the highest weather-related delays (556 trips)

---

## 🚧 Challenges & Future Enhancements

### ❗ Challenges
- Inconsistent datetime formats and null values for cancelled journeys
- Designing role-playing date dimensions for both **purchase** and **journey** dates
- Balancing **report performance** with advanced visuals (decomposition trees, Sankey diagrams)

### 🌱 Future Improvements
- 🔮 ML model to **predict delay probability** by route and time
- 💬 Sentiment analysis from **customer feedback**
- 📊 "What-if" dynamic pricing scenario modeling
- 🔗 Real-time data integration via APIs

---

## 🗂️ Repository Structure

```
📦 UK-Train-Rides
 ┣ 📁 assets/          → Dashboard screenshots
 ┣ 📁 Dataset/         → Source data files
 ┣ 📄 Documentation.pdf
 ┣ 📄 Tech Rep.pdf
 ┣ 📄 Insights Hunters Presentation.pptx
 ┣ 📄 UK Train Rides.pbix
 ┗ 📄 README.md
```

---

## 👨‍💻 Maintainer

**Mazen Moustafa Sayem Abdel-tawwab**
📧 mazen110.net@gmail.com
📱 +20 155 565 7877
🔗 [LinkedIn Profile](https://linkedin.com/in/mazen-abdel-tawwab)

---

> Made with ❤️ by **Insight Hunters**
