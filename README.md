# manga-data-warehouse
End-to-end data pipeline: MangaDex API scraping, Oracle Cloud star schema, and NLP-based mining for sentiment, clustering, and recommendations.

**Project Title:** Manga Data Warehousing and Mining Using MangaDex

**Author:** Dharl Russell C. Perez

**Course:** ITS132L – Data Warehousing and Data Mining

**Date:** August 2025

**DESCRIPTION:**
This project demonstrates a complete end-to-end data pipeline involving web scraping, preprocessing, data warehousing, and data mining. 
It uses metadata from the MangaDex API to build a star schema in an Oracle Autonomous Database and applies sentiment analysis, trend analysis, 
clustering, and a recommendation system on the cleaned data.

**SYSTEM REQUIREMENTS:**

To run this project successfully, make sure the following are installed:

- Python 3.8 or higher
- pip (Python package manager)
- Jupyter Notebook
- Oracle Autonomous Database access and wallet (for Oracle DB connection)
- Internet connection (for scraping the MangaDex API)

**PYTHON LIBRARIES:**

You can install all required libraries using pip:

pip install requests pandas tqdm cx_Oracle nltk scikit-learn matplotlib seaborn

Also, download the NLTK VADER lexicon:

python
import nltk
nltk.download('vader_lexicon')

**EXECUTION INSTRUCTIONS:**

Step 1: Run scraping.ipynb
- Opens a connection to the MangaDex API using requests
- Scrapes manga data with filtering by language, status, and demographic
- Stores the output in mangadex_data.csv

Step 2: Run cleaning.ipynb
- Cleans missing values, standardizes text, and flattens nested fields
- Performs sentiment analysis using NLTK VADER
- Saves the cleaned data as mangadex_final.csv

Step 3: Run ET.ipynb
- Establishes connection to Oracle Autonomous DB using cx_Oracle
- Creates fact and dimension tables (star schema)
- Inserts the cleaned records from mangadex_final.csv into the database

Step 4: Run data mining.ipynb
- Performs:
 • Sentiment analysis using precomputed scores
 • Trend analysis using dim_time data
 • Clustering with TF-IDF + KMeans
 • PCA visualization of clusters
 • Content-based recommendation using cosine similarity

**NOTES AND REMINDERS:**

- Make sure the Oracle wallet is configured properly before running ET.ipynb
- Use correct database credentials and test your Oracle DB connection before execution
- All notebooks must be run in sequence to avoid missing dependencies
- The project does not scrape or store any user data. All data is public metadata
- If any API calls fail during scraping, retry the notebook or use included backup files

**CONTACT INFO:**

For questions or setup issues, contact:
Dharl Russell C. Perez
Email: [dharlrussell@gmail.com]

**REPRODUCIBILITY:**

This project is fully reproducible as long as:
- All dependencies are installed
- The notebooks are run in the correct order
- Oracle connection is properly configured

Failure to follow instructions or missing setup will lead to incomplete results.
