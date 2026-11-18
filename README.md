# StreetLens — Pedestrian Safety Watch

**Sector:** Urban Planning | **Generated:** 2026-11-18

Portfolio prototype to record hazard reports at each intersection, flag readings
above an **illustrative** threshold of 3 reports, and track reviews.

## Features
- Responsive frontend, validated FastAPI REST API and SQLite persistence.
- Timestamped records, threshold flags, review workflow and audit history.
- Live metric summary, filters and local Docker deployment.
- Integration tests, GitHub Actions CI, MIT license. No paid APIs.

## Run locally
1. python -m venv .venv
2. Activate the virtual environment (source .venv/bin/activate, or Windows .venv\Scripts\activate).
3. pip install -r requirements-dev.txt
4. python -m pytest -q
5. uvicorn app:app --reload
Open http://localhost:8000; API docs at http://localhost:8000/docs.

## Docker
docker build -t streetlens .
docker run --rm -p 8000:8000 -v streetlens-data:/data streetlens

## Architecture
HTML/CSS/JS → FastAPI → SQLite (records, audit events).

## API
GET /api/health, /api/config, /api/metrics, /api/records,
GET /api/records/{id}, POST /api/records,
POST /api/records/{id}/review.

## Safety and scaling
This is a domain-configured, reusable template, not a fully custom AI
application. Thresholds are made-up examples, not safety standards.
Before production add authentication, role-based permissions, TLS,
rate limiting, backups and monitoring. SQLite is for a single instance.
Do not use as certified decision-support software.
