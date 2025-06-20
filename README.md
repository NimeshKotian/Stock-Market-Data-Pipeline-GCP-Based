# 📈 Stock Market Data Pipeline (GCP-Based)

This repository contains the source code and documentation for a real-time stock market **data pipeline prototype**, developed as part of the **Data Engineering 2: Big Data Architecture** course at SRH University.

## 🔍 Project Overview

In today's fast-paced financial markets, timely analysis of stock data is essential. This project demonstrates an **end-to-end cloud-based pipeline** for collecting, processing, storing, and visualizing stock market data in near-real-time using **Google Cloud Platform (GCP)** services.

### 📦 Key Features

- Ingests data from **Alpha Vantage API** for 10 major stocks at 5-minute intervals  
- Implements **API key rotation** to bypass rate limits  
- Uses **Google Pub/Sub** for decoupled message queuing  
- Processes and deduplicates data with Python and Pandas  
- Stores raw and processed data in **Google Cloud Storage** and **BigQuery**  
- Provides real-time visualization through a **Streamlit dashboard**  
- Achieves high throughput (~13,000+ records/month) with <1 second latency  

---

## 🛠️ Technologies Used

- **Python 3.8+**
- **Alpha Vantage API**
- **Google Cloud Platform (GCP)**: Pub/Sub, BigQuery, Cloud Storage
- **Streamlit**
- **Pandas, Requests**
- **Docker** (for deployment – optional)
- **CI/CD Tools** (used during automation)

---

## 🗃️ Data Summary

We collected stock data for:

| Symbol | Company      | Sector         |
|--------|--------------|----------------|
| AMZN   | Amazon       | Technology     |
| TSLA   | Tesla        | Automotive     |
| PFE    | Pfizer       | Healthcare     |
| JPM    | JPMorgan     | Finance        |
| IBM    | IBM          | Technology     |
| XOM    | ExxonMobil   | Energy         |
| KO     | Coca-Cola    | Consumer Goods |
| AAPL   | Apple        | Technology     |
| GOOGL  | Google       | Technology     |
| MSFT   | Microsoft    | Technology     |

Each record includes timestamp, OHLC data, volume, technical indicators (moving average, cumulative average), and deduplication metadata.

---

## 🧩 System Architecture

```
Alpha Vantage API → Google Pub/Sub → Python Processor → BigQuery & GCS → Streamlit Dashboard
```

- **Data Collection Layer**: Fetches and validates data using Python.
- **Messaging Layer**: Uses Google Pub/Sub for buffering and reliability.
- **Processing Layer**: Handles deduplication and transformation.
- **Storage Layer**: BigQuery (structured), Cloud Storage (backups).
- **Visualization Layer**: Streamlit dashboard for historical and live trends.

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/NimeshKotian/Stock-Market-Data-Pipeline-GCP-Based.git
cd your-repo-name
```

### 2. Install Requirements

```bash
pip install -r requirements.txt
```

### 3. Configure Environment Variables

Create a `.env` file and add the following:

```env
GOOGLE_APPLICATION_CREDENTIALS=path/to/service_account.json
ALPHA_VANTAGE_API_KEYS=key1,key2,key3,key4,key5
PROJECT_ID=your-gcp-project-id
PUBSUB_TOPIC=your-pubsub-topic
BIGQUERY_DATASET=your-bigquery-dataset
```

### 4. Run the Pipeline

Start data collection:
```bash
python data_collector.py
```

Process and store data:
```bash
python data_processor.py
```

Launch the dashboard:
```bash
streamlit run dashboard.py
```

---

## 📊 Streamlit Dashboard

- Visualizes OHLC data, volume trends, RSI, and moving averages  
- Allows interactive stock and date range selection  
- Pulls live data directly from BigQuery  

---

## 🧠 Contributions

This was a group project by:

- **Nimesh Kotian** – *Business insights, data visualization (volume analysis), data preprocessing, testing, API integration support, presentation & report*  
- **Ansh Kumar** – *GCP pipeline architecture, implementation, automation (CI/CD), data transformation, deduplication, dashboard development*  
- **Utkarsh Sawant** – *Data collection, preprocessing support, CI/CD help, deduplication, visualization (overview), report and presentation support*  

---

## 📈 Performance Highlights

- ✅ Real-time ingestion every 5 minutes  
- ✅ 99.9% data completeness  
- ✅ <1 second latency from source to visualization  
- ✅ Robust error handling and retry mechanisms  
- ✅ Dual-layer deduplication (Python + SQL)  

---

## 📚 References

- [Alpha Vantage API Docs](https://www.alphavantage.co/documentation/)  
- [Google Cloud Pub/Sub](https://cloud.google.com/pubsub/docs/)  
- [BigQuery Documentation](https://cloud.google.com/bigquery/docs/)  
- [Streamlit Docs](https://docs.streamlit.io/)  

---

## 🔗 GitHub Repository

> 💡 This version is personalized by **Nimesh Kotian** as part of the team contribution.

Project Repo: [https://github.com/utkarshsawant65/Data-Engineering-2-project](https://github.com/utkarshsawant65/Data-Engineering-2-project)

---

## 📜 License

This project was developed for academic purposes as part of the **Applied Data Science and Analytics – Data Engineering 2** course at SRH University. Please contact the authors before reuse.
