# Climate Hazard Trend Analyzer Frontend

This folder contains the React dashboard for the climate analysis app. The frontend is built with JavaScript and Vite and communicates with the Django backend through a local proxy.

## Features

- region search and selection
- hazard selector for heatwaves, drought, and heavy rainfall
- yearly range controls
- summary cards with risk metrics
- interactive charts for event trends
- map-based region overview
- CSV export for chart data

## Local development

From this folder, install dependencies:

```bash
npm install
```

Then run the app:

```bash
npm run dev -- --host 0.0.0.0
```

The app is usually available at http://localhost:5173.

## Build

```bash
npm run build
```

## Notes

- The app uses a Vite proxy to route requests to the Django backend on port 8000.
- The frontend is intentionally kept in JavaScript rather than TypeScript to match the current project setup.
