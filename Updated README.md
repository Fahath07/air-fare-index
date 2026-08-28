# air-fare-index
# ✈️ Real-time Airfare Price Index for India.

> **Problem Statement ID: 26056**

## 📌 Overview

The **Real-time Airfare Price Index for India** is a software platform designed to automatically collect, clean, analyze, and monitor domestic airfare prices across major Indian airline and online travel platforms.

The system aims to provide a reliable and high-frequency view of airfare movements in India and support the augmentation of the **Consumer Price Index (CPI)** by providing a data-driven **Airfare Price Index (APIx)**.

---

## 🎯 Problem Statement

Traditional airfare price collection relies heavily on manual collection from a limited number of sources. However, airline ticket prices are highly dynamic and can change significantly based on:

* Advance booking period
* Demand and seat availability
* Day of the week
* Holidays and festivals
* Route
* Airline
* Taxes and additional charges

With most domestic air tickets being purchased online, manual collection may not accurately represent the prices faced by consumers.

This project addresses the problem through **automated, ethical, and scalable airfare data collection and analysis**.

---

## 💡 Proposed Solution

The platform will:

1. Automatically collect airfare data from permitted airline and travel portals.
2. Capture prices for representative domestic routes.
3. Track different advance-purchase windows such as **T+1, T+7, T+15, T+30, and T+45**.
4. Clean and normalize collected airfare data.
5. Separate base fare, taxes, and additional charges.
6. Store standardized airfare data in a structured database.
7. Calculate a weighted **Airfare Price Index (APIx)**.
8. Visualize airfare trends through an interactive dashboard.
9. Provide APIs for external consumers such as researchers and policymakers.
10. Validate the index through historical/back-testing analysis.

---

## 🏗️ System Architecture

```text
        Airline / OTA Portals
                 │
                 ▼
        ┌──────────────────┐
        │ Scraping Engine  │
        │ Playwright /     │
        │ Selenium /       │
        │ Scrapy           │
        └────────┬─────────┘
                 │
                 ▼
          Raw Airfare Data
                 │
                 ▼
        ┌──────────────────┐
        │ Data Cleaning &  │
        │ Normalization    │
        └────────┬─────────┘
                 │
                 ▼
          Airfare Database
                 │
          ┌──────┴──────┐
          ▼             ▼
   Index Calculation   Analytics
          │             │
          └──────┬──────┘
                 ▼
        Interactive Dashboard
                 │
                 ▼
             REST API
                 │
                 ▼
       Researchers / Policymakers
```

---

## ✈️ Representative Routes

The system will initially focus on high-volume domestic routes such as:

| Route     | Example               |
| --------- | --------------------- |
| DEL → BOM | Delhi → Mumbai        |
| DEL → BLR | Delhi → Bengaluru     |
| BOM → BLR | Mumbai → Bengaluru    |
| DEL → CCU | Delhi → Kolkata       |
| BLR → HYD | Bengaluru → Hyderabad |
| MAA → DEL | Chennai → Delhi       |

The final route basket will be determined using relevant passenger-traffic data.

---

## ⏱️ Advance-Purchase Windows

The system will capture airfare at different booking horizons:

| Window | Meaning              |
| ------ | -------------------- |
| T+1    | Flight tomorrow      |
| T+7    | Flight 7 days later  |
| T+15   | Flight 15 days later |
| T+30   | Flight 30 days later |
| T+45   | Flight 45 days later |

This enables analysis of **lead-time elasticity** and booking behavior.

---

## 📊 Data Collected

Each airfare observation may contain:

```text
Origin
Destination
Airline
Flight Date
Collection Timestamp
Advance-Purchase Window
Fare Class
Base Fare
Taxes
User Development Fee
Convenience Charges
Total Fare
Availability Status
Source
```

---

## 🧹 Data Processing

Collected data will pass through a data-quality pipeline that handles:

* Duplicate records
* Missing values
* Invalid prices
* Outliers
* Sold-out flights
* Cancelled flights
* Different fare formats
* Taxes and additional charges
* Base fare vs total fare normalization

```text
Raw Data
   ↓
Validation
   ↓
Deduplication
   ↓
Missing Value Handling
   ↓
Outlier Detection
   ↓
Fare Normalization
   ↓
Clean Dataset
```

---

## 📈 Airfare Price Index

The platform will calculate a weighted **Airfare Price Index (APIx)** using representative routes and their corresponding weights.

The index will be available at:

* Daily frequency
* Weekly frequency
* Monthly frequency

Example:

```text
Base Period Index = 100

Month       APIx
----------------
January     100.0
February    103.5
March       107.2
April       105.8
May         111.4
```

This allows users to understand whether airfare prices are increasing or decreasing over time.

---

## 📊 Dashboard

The interactive dashboard will provide:

### Key Metrics

* Current Airfare Price Index
* Daily change
* Weekly change
* Monthly change
* Average airfare

### Visualizations

* Airfare Index trend
* Route-wise price comparison
* Airline-wise comparison
* Sector heatmap
* Lead-time elasticity curves
* Historical airfare trends
* Price distribution

---

## 🔌 REST API

The system will expose airfare and index data through APIs.

Example endpoints:

```text
GET /api/airfare-index
GET /api/routes
GET /api/airlines
GET /api/airfare-prices
GET /api/historical-data
```

The API will enable integration with analytical and policy-oriented applications.

---

## 🛡️ Ethical Scraping

The project will follow responsible data-collection practices.

The scraping system will incorporate:

* `robots.txt` compliance
* Terms-of-service awareness
* Rate limiting
* Controlled request frequency
* Session management
* Request logging
* Respect for anti-bot mechanisms
* No unauthorized access or bypassing of security controls

Where automated collection is not permitted, the prototype will use **approved/public datasets or simulated data** for demonstration.

---

## 🧪 Back-Testing

The project will include at least **30 days of historical/back-tested results**.

The calculated Airfare Price Index will be compared against publicly available reference data, including relevant DGCA airfare statistics where applicable.

```text
Our APIx
   │
   ├──────────────┐
   │              │
   ▼              ▼
Calculated     Reference
Index          Data
   │              │
   └──────┬───────┘
          ▼
   Trend Comparison
          │
          ▼
     Validation
```

---

## 🛠️ Technology Stack

### Frontend

* React
* TypeScript
* Tailwind CSS
* Recharts / Chart.js
* Leaflet / Map visualization

### Backend

* Python
* FastAPI
* Pydantic
* SQLAlchemy

### Data Collection

* Playwright
* Selenium
* Scrapy

### Data Processing

* Python
* Pandas
* NumPy

### Database

* PostgreSQL

### Testing

* Pytest
* API testing
* Scraper validation tests

### Development Tools

* Git
* GitHub
* VS Code

---

## 📁 Project Structure

```text
airfare-price-index/
│
├── backend/
│   ├── app/
│   ├── api/
│   ├── models/
│   ├── services/
│   └── database/
│
├── frontend/
│   ├── src/
│   ├── components/
│   ├── pages/
│   └── services/
│
├── scraper/
│   ├── spiders/
│   ├── parsers/
│   ├── pipelines/
│   └── scheduler/
│
├── data/
│   ├── raw/
│   ├── processed/
│   └── reference/
│
├── tests/
│   ├── backend/
│   ├── scraper/
│   └── index/
│
├── docs/
│
├── .gitignore
├── requirements.txt
└── README.md
```

---

## 🚀 Development Roadmap

### Phase 1 — Project Setup

* [x] Initialize Git repository
* [x] Create project structure
* [x] Add README
* [x] Add `.gitignore`

### Phase 2 — System Design

* [ ] Define system architecture
* [ ] Design database schema
* [ ] Define API specifications
* [ ] Select representative routes

### Phase 3 — Backend

* [ ] Set up FastAPI
* [ ] Configure PostgreSQL
* [ ] Create database models
* [ ] Create API endpoints

### Phase 4 — Data Collection

* [ ] Develop scraper framework
* [ ] Implement airline data collectors
* [ ] Implement OTA collectors where permitted
* [ ] Add scheduling
* [ ] Add scraping safeguards

### Phase 5 — Data Processing

* [ ] Data validation
* [ ] Deduplication
* [ ] Missing-value handling
* [ ] Outlier detection
* [ ] Fare normalization

### Phase 6 — Index Engine

* [ ] Define route weights
* [ ] Implement index calculation
* [ ] Generate daily index
* [ ] Generate weekly index
* [ ] Generate monthly index

### Phase 7 — Dashboard

* [ ] Build dashboard
* [ ] Add index charts
* [ ] Add route heatmap
* [ ] Add airline comparison
* [ ] Add lead-time analysis

### Phase 8 — Validation

* [ ] Collect historical/reference data
* [ ] Perform 30-day back-testing
* [ ] Compare trends
* [ ] Measure index accuracy

### Phase 9 — Finalization

* [ ] Automated testing
* [ ] Documentation
* [ ] API documentation
* [ ] Deployment
* [ ] Final demonstration

---

## 👥 Team

**Project:** Real-time Airfare Price Index for India

**Problem Statement:** 26056

**Domain:** Data Science / Web Scraping / Economic Analytics

---

## 📌 Project Status

🚧 **Currently in Initial Development**

The project is currently at the **initial setup and architecture phase**.

---

## ⚠️ Disclaimer

This project is developed as a software prototype for research and demonstration purposes. Data collection will be performed only through permitted and compliant sources, respecting applicable website policies, access controls, and legal requirements.
