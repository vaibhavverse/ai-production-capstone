# AI in Production — Country-Level Sales Prediction API

Runnable capstone starter: ingestion, EDA charts, baseline/model comparison, FastAPI endpoints, logging, tests, and Docker.

**Data warning:** `data/sample_sales.csv` is synthetic demo data. Replace it with the official course dataset before submitting; demo metrics are not course-dataset results.

## Run locally
```bash
pip install -r requirements.txt
python -m src.train
uvicorn app.main:app --reload
```
Open `http://127.0.0.1:8000/docs`.

## Endpoints
- `GET /health`
- `GET /countries`
- `GET /predict?country=United%20Kingdom`
- `GET /predict?country=all`
- `GET /metrics`

## Tests
Run all tests with one command: `python -m pytest -q` (or `bash scripts/run_tests.sh`).

## Docker
```bash
docker build -t ai-production-capstone .
docker run --rm -p 8000:8000 ai-production-capstone
```

Expected input columns: `InvoiceDate`, `Country`, `Quantity`, `UnitPrice`. This demo predicts a simple next-day revenue estimate from day-of-week and month. Country is currently not a model feature, so country-specific predictions are identical; improve the feature set before business use.
