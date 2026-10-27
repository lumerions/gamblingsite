<h1 align="center">Gambling Website</h1>

<p align="center">
  A FastAPI-powered gambling site for Roblox games: Mines, Towers, Dice, and Coinflip, with Roblox deposits and withdrawals.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI">
  <img src="https://img.shields.io/badge/python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Roblox-000000?style=for-the-badge&logo=roblox&logoColor=white" alt="Roblox">
  <img src="https://img.shields.io/badge/deployed%20on-Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white" alt="Vercel">
  <img src="https://img.shields.io/badge/status-inactive-lightgrey?style=for-the-badge" alt="Status: inactive">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white" alt="PostgreSQL">
  <img src="https://img.shields.io/badge/MongoDB-47A248?logo=mongodb&logoColor=white" alt="MongoDB">
  <img src="https://img.shields.io/badge/Redis-DC382D?logo=redis&logoColor=white" alt="Redis">
  <img src="https://img.shields.io/badge/Jinja2-B41717?logo=jinja&logoColor=white" alt="Jinja2">
  <img src="https://img.shields.io/badge/Pydantic-E92063?logo=pydantic&logoColor=white" alt="Pydantic">
  <img src="https://img.shields.io/badge/maintained-no-red" alt="Not maintained">
</p>

<p align="center">
  <a href="#features">Features</a> •
  <a href="#tech-stack">Tech Stack</a> •
  <a href="#installation">Installation</a> •
  <a href="#configuration">Configuration</a> •
  <a href="#project-structure">Structure</a> •
</p>

> [!NOTE]
> This project is **no longer actively maintained**.

---

## Features

- **Games**: Mines, Towers, Dice, and Coinflip
- **User Authenication system**: register/login with cookie-based sessions and CSRF tokens
- **Roblox deposits and withdrawals**: move balance and items in and out through a Roblox game via launch data
- **Item inventory**: deposit, and withdraw Roblox items
- **Rate limiting**: per-session limits with SlowAPI
- **Auto docs**: Swagger UI at `/docs`

## Tech Stack

| Layer | Tech |
|---|---|
| Backend | FastAPI, Uvicorn, Pydantic |
| Templates | Jinja2 + static JS in `javascript/` |
| Accounts | PostgreSQL (`psycopg`) |
| Balances, items, coinflips | MongoDB (`pymongo`) |
| Sessions and live game state | Upstash Redis |
| Hosting | Vercel |

## Installation

```bash
git clone https://github.com/lumerions/gamblingsite.git
cd gamblingsite
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

Run the dev server:

```bash
uvicorn main:app --reload
```

Then open <http://localhost:8000>.

## Configuration

Set these environment variables before starting the app:

| Variable | Description |
|---|---|
| `MONGO_CONNECTIONURI` | MongoDB connection string |
| `POSTGRES_DATABASE_URL` | PostgreSQL connection string (accounts) |
| `REDIS_URL` | Upstash Redis REST URL |
| `REDIS_TOKEN` | Upstash Redis REST token |

You'll also need to set your Roblox `place_id` in `main.py` and replace the placeholder marketplace/inventory URLs with your own endpoints.

## Project Structure

```
gamblingsite/
├── main.py            # FastAPI app and all routes
├── templates/         # Jinja2 HTML pages (home, mines, towers, dice, coinflip...)
├── javascript/        # client-side scripts
├── public/            # static assets
├── vercel.json        # Vercel deployment config
├── pyproject.toml
└── requirements.txt
```

