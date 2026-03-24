# Backend (FastAPI + MySQL)

This is the API for the Yelp-style restaurant project.

## What it includes

- Auth (user + owner)
- Restaurants (local + Yelp import/search)
- Reviews, favorites, history
- Owner dashboard APIs
- AI assistant endpoint

## Requirements

- Python 3.11+
- MySQL 8+

## Setup

```bash
cd backend
cp .env.example .env
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

Create database:

```sql
CREATE DATABASE restaurant_lab CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;
```

Run migrations:

```bash
alembic upgrade head
```

## Important `.env` values

- `DATABASE_URL` (required)
- `SECRET_KEY` (required)
- `CORS_ORIGINS` (must include frontend origin, usually `http://localhost:5173`)
- `YELP_API_KEY` (required for live Yelp data)
- `GEMINI_API_KEY`, `TAVILY_API_KEY` (for AI assistant features)

## Run API

```bash
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

- Docs: [http://localhost:8000/docs](http://localhost:8000/docs)
- Health: [http://localhost:8000/health](http://localhost:8000/health)

## Main route groups

- `/auth`
- `/users`
- `/restaurants`
- `/reviews`
- `/favorites`
- `/owner`
- `/ai-assistant`
