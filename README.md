# manga-data-warehouse

End-to-end data pipeline: MangaDex API scraping, Oracle Cloud star schema, and NLP-based mining for sentiment, clustering, and recommendations.

![Python](https://img.shields.io/badge/Python-3.8+-blue) ![Oracle](https://img.shields.io/badge/Oracle-Autonomous_DB-red) ![License](https://img.shields.io/badge/License-MIT-green)

---

## Overview

This project demonstrates a complete end-to-end data pipeline involving web scraping, preprocessing, data warehousing, and data mining. It uses metadata from the MangaDex API to build a star schema in an Oracle Autonomous Database and applies sentiment analysis, trend analysis, clustering, and a recommendation system on the cleaned data.

| | |
|---|---|
| **Course** | ITS132L – Data Warehousing and Data Mining |
| **Author** | Dharl Russell C. Perez |
| **Date** | August 2025 |

---

## Pipeline
```
MangaDex API → scraping.ipynb → mangadex_data.csv
                                      ↓
                             cleaning.ipynb → mangadex_final.csv
                                                     ↓
                                             ET.ipynb → Oracle Autonomous DB (Star Schema)
                                                                    ↓
                                                        data_mining.ipynb → Results
```

---

## Execution Order

> **All notebooks must be run in sequence.**

### Step 1 — `scraping.ipynb`
- Connects to the MangaDex API using `requests`
- Scrapes manga metadata filtered by language, status, and demographic
- Output: `mangadex_data.csv`

### Step 2 — `cleaning.ipynb`
- Cleans missing values, standardizes text, flattens nested fields
- Performs sentiment analysis using NLTK VADER
- Output: `mangadex_final.csv`

### Step 3 — `ET.ipynb`
- Connects to Oracle Autonomous DB via `cx_Oracle`
- Creates fact and dimension tables (star schema)
- Inserts cleaned records from `mangadex_final.csv`

### Step 4 — `data_mining.ipynb`
- Sentiment analysis using precomputed scores
- Trend analysis using `dim_time` data
- Clustering with TF-IDF + KMeans
- PCA visualization of clusters
- Content-based recommendation using cosine similarity

---

## System Requirements

- Python 3.8 or higher
- Jupyter Notebook
- Oracle Autonomous Database access + wallet
- Internet connection (for MangaDex API)

---

## Installation
```bash
pip install requests pandas tqdm cx_Oracle nltk scikit-learn matplotlib seaborn
```

Then download the NLTK VADER lexicon:
```python
import nltk
nltk.download('vader_lexicon')
```

---

## Oracle Setup

Before running `ET.ipynb`:
1. Download your Oracle Autonomous DB wallet
2. Configure `cx_Oracle` with the correct wallet path
3. Test your DB connection before execution

---

## Notes

- Run notebooks **in order** — each step depends on the previous output
- No user data is scraped or stored — all data is public metadata from MangaDex
- If API calls fail during scraping, retry or use included backup files
- Missing Oracle setup will cause `ET.ipynb` to fail

---

## Contact

**Dharl Russell C. Perez**  
dharlrussell@gmail.com
