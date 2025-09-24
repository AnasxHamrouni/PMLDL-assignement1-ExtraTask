# Badminton ML deployment - quick start

## About
- the model helps to guess the winner of a badminton match, by choosing match type you may insert players current points, ranking and played tournaments.
Match type labeling:
MS - man's singles
WS - woman's singles
MD - man's doubles
WD - woman's doubles
XD - mixed doubles

This project still needs improvements, in the future:
- improve data preprocessing and balancing
- improve model design and mechanism
- improve UI to be able to select players
- improve prediction model to be able to predict tournament winner's ranking

## Prerequisites
- Docker & docker-compose
- (Optional) Python 3.10 for running scripts locally
- Clone SanderP99/Badminton-Data and copy `out/` to `data/raw/out/` (recommended)

## Quick local run (fastest)
1. Build & run services (mlflow, api, app):
   cd code/deployment
   docker-compose up --build

2. Open:
   - Streamlit app: http://localhost:8501
   - FastAPI docs: http://localhost:8000/docs
   - MLflow UI: http://localhost:5000

## Run preprocessing & training locally (optional)
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
python code/datasets/prepare_data.py --raw-dir data/raw/out --out-dir data/processed
python code/models/train.py --processed-dir data/processed --models-dir models --mlflow-uri http://localhost:5000