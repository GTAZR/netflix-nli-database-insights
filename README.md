# Natural Language Interface (NLI) for Database Insights

**Course:** SEP 6DA3 – Data Analytics and Big Data  
**Institution:** McMaster University  
**Semester:** Fall 2025  
**Team:** Group 6  
**Contributors:** Andi Dong, Zhiyu Hu, Foram Brahmbhatt, Jiarui Yang, Linghe Shen, Shannon Chen  
**Instructor:** Prof. Pedro Tondo  

---

## 🎯 Project Overview
This project demonstrates how **Natural Language Interfaces (NLI)** can enable human-friendly database interaction.  
Using the **Netflix Movies and TV Shows** dataset, our team built a lightweight system that converts everyday English queries into database operations.  
We implemented the NLI with **SQLite** (relational database) and compared it with **InfluxDB 3** (time-series / NoSQL) to evaluate ease of use, performance, and best-fit use cases.

---

## 🧠 Objectives
- Load and query a real-world dataset (Netflix titles).  
- Generate automated insights such as **top countries**, **genres**, and **total titles**.  
- Build a **Natural Language Interface** that maps simple questions to SQL queries.  
- Compare **SQLite vs InfluxDB 3** for analytical flexibility.  
- Reflect on how NLI bridges human language and data analysis.

Dataset: [Netflix Movies and TV Shows (Kaggle)](https://www.kaggle.com/datasets/shivamb/netflix-shows)

---

## 🧩 Methodology

### 1️⃣ Database Setup
- **SQLite:** Used as the primary database — fast, built-in, and seamlessly compatible with Pandas.  
- **InfluxDB 3:** Reviewed for comparison; suited for time-series / real-time data but requires external configuration.  
- The dataset (`netflix_titles.csv`, 8 ,807 records) was imported into SQLite and verified for consistency.

### 2️⃣ Automated SQL Queries
| Query | Goal | Key Finding |
|:------|:------|:------------|
| **Q1** – Total titles | Count all records | 8 ,807 titles |
| **Q2** – Top 5 countries | Split and aggregate `country` field | 🇺🇸 US (3 ,690), 🇮🇳 India (1 ,046), 🇬🇧 UK (806), 🇨🇦 Canada (445), 🇫🇷 France (393) |
| **Q3** – Top genres | Explode `listed_in` column | *International Movies*, *Dramas*, *Comedies*, *International TV Shows*, *Documentaries* |
| **Q4** – Recent shows (2020 +) | Filter `release_year ≥ 2020` | e.g., *Blood & Water (2021)*, *Ganglands (2021)*, *Kota Factory (2021)* |

---

## 💬 Natural Language Interface (NLI)

A simple keyword-driven NLI was implemented to map user input to database logic.

| Example Question | Mapped Query | Result |
|:-----------------|:-------------|:--------|
| “**total shows**” | `SELECT COUNT(*) FROM netflix` | 8 ,807 |
| “**top countries**” | Pre-computed aggregation | US > India > UK > Canada > France |
| “**top genres**” | Pre-computed aggregation | International Movies > Dramas > Comedies |
| “**recent shows 2020+**” | SQL filter on release year ≥ 2020 | List of recent titles |

This approach demonstrates that even a simple text-parsing model can make data retrieval **intuitive** and **accessible** to non-technical users.

---

## 🗄️ Database Comparison: SQLite vs InfluxDB 3

| Aspect | SQLite (Relational) | InfluxDB 3 (Time-Series / NoSQL) |
|:--------|:--------------------|:---------------------------------|
| **Setup** | Built-in, zero configuration | Requires server / token / bucket |
| **Query Language** | SQL – ideal for grouping & filtering | Flux / SQL+ – optimized for time operations |
| **Data Model** | Tables (rows & columns) | Measurements (time, tags, fields) |
| **Performance** | Excellent for small static datasets | Better for large time-series workloads |
| **Ease of Use** | Integrates easily with Pandas & Python | Requires API client setup |
| **Best Use Case** | Categorical / static data (e.g., Netflix metadata) | Streaming / temporal data (e.g., content trends over time) |

**Conclusion:** SQLite was ideal for this project’s structured static dataset, while InfluxDB would shine in real-time streaming contexts.

---

## 📊 Key Findings
- Netflix catalog = **8 ,807 titles** spanning dozens of countries and genres.  
- The US dominates production volume → reflects global content distribution.  
- ~9 % of records lack country metadata → handled transparently.  
- “International Movies” and “Dramas” lead genre frequency → emphasizes cross-cultural storytelling.  
- NLI proved effective for making querying more natural and accessible.  

---

## 🛠️ Technologies Used
- **Python 3.x**
