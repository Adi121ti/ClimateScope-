# Climate Hazard Trend Analyzer

A full-stack dashboard for exploring long-term climate risk in a selected region. The app combines a Django backend with a React frontend to analyze historical weather data from Open-Meteo, detect hazard patterns, and show trend summaries on an interactive dashboard.

## Overview

This project helps users:

- search for a location or region
- choose a study period and hazard type
- analyze historical temperature and rainfall records
- review trend summaries and event counts
- view regional context on a map
- export the current chart data as CSV

The app is designed for local development and can also be deployed on lightweight hosting platforms such as Vercel and Render.

## Features

- React + Vite frontend with JavaScript (no TypeScript)
- Django API for region lookup and climate analysis
- Open-Meteo geocoding and archive data integration
- Hazard analysis for:
  - heatwaves
  - drought conditions
  - heavy rainfall events
- Summary metrics, trend labels, and charted annual patterns
- Map view with region markers and CSV export

## Tech stack

- Frontend: React, Vite, JavaScript, Recharts, Leaflet
- Backend: Django, Python
- Data source: Open-Meteo public APIs
- Styling: Custom CSS

## Project structure

```text
CHTrendAnalyzer/
├── README.md
├── package.json
├── backend/
│   ├── manage.py
│   ├── requirements.txt
│   ├── app/
│   │   ├── config.py
│   │   ├── db.py
│   │   ├── urls.py
│   │   ├── views.py
│   │   ├── services/
│   │   │   └── climate.py
│   └── climate_project/
│       ├── settings.py
│       ├── urls.py
│       ├── wsgi.py
│       └── asgi.py
├── frontend/
│   ├── package.json
│   ├── vite.config.js
│   ├── index.html
│   ├── public/
│   └── src/
│       ├── App.jsx
│       ├── App.css
│       ├── main.jsx
│       └── index.css
└── Windows-Setup-Run.md
```

## How it works

1. The user searches for a city or region and sets the analysis window.
2. The frontend sends a request to the Django backend.
3. The backend validates the request and resolves the selected coordinates.
4. The climate service fetches historical records from Open-Meteo.
5. Hazard-specific logic identifies events such as heatwaves, drought periods, or extreme rainfall clusters.
6. Results are summarized into yearly counts, averages, trend labels, and threshold values.
7. The frontend renders the dashboard cards, charts, and map markers.

## Supported hazard analysis

### Heatwave detection
- detects sustained runs of unusually hot days
- calculates yearly event counts and average duration
- identifies a long-term trend signal

### Drought detection
- uses precipitation totals as a rainfall deficit signal
- summarizes unusually dry years or periods
- highlights the direction of the trend

### Heavy rainfall detection
- captures extended periods of intense precipitation
- reports event duration and peak rainfall totals
- tracks frequency and trend direction

## API endpoints

The backend exposes these primary routes:

- GET /api/health
- GET /api/default-regions
- GET /api/search-regions?query=<name>
- GET /api/analysis?region_name=...&latitude=...&longitude=...&start_year=...&end_year=...&hazard=...

## Data sources

This project uses public data from Open-Meteo:

- geocoding API for region location and search suggestions
- archive API for daily weather records used in hazard detection

## Local setup

### 1) Clone the repository

```bash
git clone <repository-url>
cd CHTrendAnalyzer
```

### 2) Create and activate a Python environment

```bash
python -m venv .venv
# macOS/Linux
source .venv/bin/activate
# Windows PowerShell
.venv\Scripts\Activate.ps1
```

### 3) Install backend dependencies

```bash
pip install -r backend/requirements.txt
```

### 4) Start the Django backend

```bash
python backend/manage.py runserver 0.0.0.0:8000
```

### 5) Install frontend dependencies

```bash
cd frontend
npm install
```

### 6) Run the frontend

```bash
npm run dev -- --host 0.0.0.0
```

The app should open on http://localhost:5173.

## Notes

- The project intentionally uses public weather data and therefore depends on the availability and limitations of those APIs.
- Hazard thresholds are designed to be transparent and explainable rather than climate-science-grade official classifications.
- This project is intended as a practical demo and can be extended with rate limiting, better storage, and more advanced climate analytics.

## License

This project is currently for educational and demo purposes.

