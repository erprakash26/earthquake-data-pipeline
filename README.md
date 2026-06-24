# Earthquake Data Pipeline

An end-to-end data engineering pipeline that ingests global earthquake data from the USGS public API, transforms it with dbt, loads it into BigQuery, orchestrates the whole flow with Airflow, and visualizes results in Looker Studio.

This is a learning-by-building portfolio project. It is being built incrementally and documented honestly — the status table below reflects what's actually working right now, not the end goal.

## Project Status

| Stage | Tool | Status |
|---|---|---|
| Ingestion | Python + USGS API | 🚧 In Progress |
| Transformation | dbt | ⏳ Planned |
| Loading | BigQuery | ⏳ Planned |
| Orchestration | Airflow | ⏳ Planned |
| Visualization | Looker Studio | ⏳ Planned |

**Legend:** ✅ Done · 🚧 In Progress · ⏳ Planned

## Project Goal

Build a real, fully working data pipeline using global earthquake data (magnitude 4.5+) from the USGS Earthquake API, covering ingestion through visualization, as a demonstration of practical data engineering skills: API ingestion, data modeling/transformation, cloud data warehousing, orchestration, and dashboarding.

## Architecture

```
earthquake-data-pipeline/
├── ingestion/
│   └── fetch_earthquakes.py        # Fetches earthquake data from USGS API, saves CSV
├── data/
│   └── earthquakes.csv             # Raw data output
├── transformation/
│   └── dbt_project/                # dbt models: staging + mart layers
├── loading/
│   └── load_to_bigquery.py         # Loads CSV into BigQuery
├── orchestration/
│   └── dags/
│       └── earthquake_dag.py       # Airflow DAG scheduling the full pipeline
├── dashboard/
│   └── README.md                   # Link to Looker Studio dashboard
├── requirements.txt                # Python dependencies
└── README.md
```

### Data Flow

```
USGS Earthquake API
        │
        ▼
  [Ingestion: Python]  →  data/earthquakes.csv
        │
        ▼
  [Loading: BigQuery]  →  raw table
        │
        ▼
  [Transformation: dbt]  →  staging model → mart model
        │
        ▼
  [Visualization: Looker Studio]

  Orchestrated end-to-end by Airflow (daily schedule)
```

## Data Source

- **API:** [USGS Earthquake Catalog API](https://earthquake.usgs.gov/fdsnws/event/1/query) (public, free, no API key required)
- **Scope:** Global earthquakes, magnitude 4.5+
- **Date range:** 2024-01-01 to present
- **Format:** GeoJSON

## Tech Stack

- **Language:** Python
- **Ingestion:** `requests`, `pandas`
- **Transformation:** dbt (`dbt-bigquery`)
- **Data Warehouse:** Google BigQuery
- **Orchestration:** Apache Airflow
- **Visualization:** Looker Studio
- **Version Control:** Git / GitHub

## How to Run Locally

> ⚠️ This section will be filled in as each pipeline stage is completed. Currently only ingestion is in progress, so only that step is documented below.

### Prerequisites
- Python 3.10+
- Git

### Setup
```bash
git clone https://github.com/erprakash26/earthquake-data-pipeline.git
cd earthquake-data-pipeline
python -m venv venv
venv\Scripts\activate      # Windows
pip install -r requirements.txt
```

### Run ingestion
```bash
python ingestion/fetch_earthquakes.py
```

*(Loading, transformation, orchestration, and dashboard instructions will be added here once those stages are built.)*

## Dashboard

⏳ Not yet available — link will be added once the Looker Studio dashboard is built.

## Roadmap

- [ ] Finish ingestion script and validate output CSV
- [ ] Set up GCP project + BigQuery dataset
- [ ] Load raw data into BigQuery
- [ ] Build dbt staging + mart models
- [ ] Build and test Airflow DAG
- [ ] Build Looker Studio dashboard
- [ ] Add dashboard screenshots to this README

## Author

**erprakash26**
GitHub: [github.com/erprakash26](https://github.com/erprakash26)
