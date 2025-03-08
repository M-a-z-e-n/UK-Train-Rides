# UK Train Rides Dashboard 🚆📊

## 📌 Project Overview
**Insight Hunters** presents the **UK Train Rides Dashboard**, an interactive **Power BI** solution providing deep insights into train performance, passenger behavior, and financial trends. This project aims to enhance decision-making for railway services using data-driven strategies.

---

## 🏆 Team Details
- **Team Name:** Insight Hunters
- **Motto:** "Hunting the Unknown, Revealing the Unseen!"
- **Project Leader:** Abdallh Mohamed Abdelmonem Soliman
- **Team Members:**
  - Mazen Moustafa Sayem Abdel-tawwab
  - Shahd Noman Esawy Esawy
  - Asmaa Salah Mohamed Alhady
  - Abdallh Mohamed Abdelmonem Soliman
  - Saif Mohammed Godah

---

## 🎯 Project Goals
This dashboard aims to:
✅ Analyze **payment methods** and transaction efficiency.
✅ Identify **ticket pricing trends** and revenue streams.
✅ Highlight **busiest train stations** and congestion points.
✅ Examine **journey delays** and their financial impact.
✅ Assess **seasonal demand trends** for strategic planning.
✅ Evaluate **real-time operational performance**.

---

## 📊 Key Business Questions & Insights
### 🔍 Analytical Dashboard
- **What are the most commonly used payment methods?**
- **What is the average ticket price for each ticket type?**
- **What are the most frequently used departure and arrival stations?**

### 🎯 Strategic Dashboard
- **How do journey delays impact customer satisfaction and revenue?**
- **Which ticket categories generate the highest revenue?**
- **What are the seasonal demand trends for tickets?**

### ⚙ Operational Dashboard
- **What is the percentage of on-time vs. delayed journeys?**
- **What are the most common reasons for journey delays?**
- **How many refund requests have been submitted due to delays?**

---

## 🎨 Dashboard Design
### 📌 Color Palette
- **Background:** `#F7F7F7`
- **Highlights & KPI Cards:** `#FFB22C`
- **Charts & Graphs:** `#854836`
- **Text & Contrast:** `#000000`

### 🖥 Dashboard Mockups
**Analytical Dashboard:**
- 📊 **Bar Charts & Pie Charts** for payment method insights.
- 🎟 **Ticket pricing trends** per category.
- 🚉 **Station traffic visualization** (Top 5 busiest stations & heatmaps).

**Strategic Dashboard:**
- 🔗 **Correlation analysis** between delays & refunds.
- 💰 **Revenue breakdown** by ticket category.
- 📈 **Time Series Analysis** for seasonal demand trends.

**Operational Dashboard:**
- ⏰ **Real-time monitoring** of journey punctuality.
- 🛑 **Delay reasons analysis** with bar charts & tree maps.
- 💵 **Refund requests impact assessment**.

---

## 🔄 Data Processing & Modeling
### 🧹 **Data Cleaning**
✔ Removed empty values in **Reason for Delay** column by setting "On Time" as default.
✔ Verified **data types** to ensure smooth processing.
✔ Managed **null values** in actual time for canceled journeys.

### 🌟 **Star Schema Data Model**
✅ **Fact Table:** `Transactions Fact` (Holds transactional data)
✅ **Dimension Tables:**
- `Dim Tickets` 🎫 (Ticket details)
- `Dim Journeys` 🚆 (Journey details)
- `Dim Status` 🚦 (Journey status & delays)

---

## 📌 Power BI Relationships
🔗 `Transactions Fact` → `Dim Tickets` (1-to-Many)
🔗 `Transactions Fact` → `Dim Journeys` (1-to-Many)
🔗 `Dim Journeys` → `Dim Status` (1-to-Many)

---

## 🧮 Key DAX Measures
📊 **Total Sales:** `SUM('Transactions Fact'[Price])`
🛒 **Transaction Count:** `COUNTROWS('Transactions Fact')`
🚆 **Total Delayed Journeys:** `CALCULATE(COUNTROWS('Dim Status'), 'Dim Status'[Journey Status] = "Delayed")`
❌ **Total Cancelled Journeys:** `CALCULATE(COUNTROWS('Dim Status'), 'Dim Status'[Journey Status] = "Cancelled")`
💳 **Sales by Payment Method:** `CALCULATE(SUM('Transactions Fact'[Price]), ALLEXCEPT('Transactions Fact', 'Transactions Fact'[Payment Method]))`
🎟 **Revenue by Ticket Class:** `CALCULATE(SUM('Transactions Fact'[Price]), ALLEXCEPT('Dim Tickets', 'Dim Tickets'[Ticket Class]))`
🔄 **Running Total Sales:** `CALCULATE([Total Sales], FILTER(ALLSELECTED('Transactions Fact'[Purchase Date]), 'Transactions Fact'[Purchase Date] <= MAX('Transactions Fact'[Purchase Date])))`

---

## 📢 Conclusion
This **Power BI dashboard** empowers railway operators with **data-driven insights** to enhance service efficiency, optimize pricing, and improve passenger satisfaction. 🚆📈

---

## 📎 Repository Contents
📂 `Data/` → Cleaned datasets (if public)
📂 `Dashboard/` → `.pbix` files & screenshots
📂 `Scripts/` → Python/SQL scripts (if applicable)
📂 `Docs/` → Project documentation

📌 **Created by:** *Insight Hunters - Capstone Project W14* 🚀

