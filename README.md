# CompLift

CompLift extracts executive compensation tables from Canadian AIC PDFs and helps review and export CSVs.

## Run locally

1. Install dependencies:

```bash
npm install
```

2. Run dev server:

```bash
npm run dev
```

Open http://localhost:5173

## Project structure

- `complift.jsx` — original single-file app (kept for reference).
- `src/components/CompLift.jsx` — main UI component (moved from root).
- `src/pages/Home.jsx` — simple landing page.
- `src/pages/Viewer.jsx` — page that renders the `CompLift` component.
- `src/App.jsx`, `src/main.jsx` — routing and app bootstrap.

## Features

- Drop multiple PDF AICs to extract compensation tables via Anthropic API.
- Flag uncertain values for manual review and correction.
- Export per-document or aggregated CSVs.

## Environment

The extraction uses Anthropic's API; ensure your browser can access the API and that your key is configured where the code calls `fetch("https://api.anthropic.com/v1/messages"...)`. For local development you can proxy or add a small server to inject the API key.

## Deploy to Vercel

1. Push the repo to GitHub.
2. In Vercel, import the project and set:
   - Framework Preset: `Vite` (or `Other`)
   - Build Command: `npm run build`
   - Output Directory: `dist`
3. Add any required environment variables (e.g., `ANTHROPIC_API_KEY`) in Vercel's dashboard.
4. Deploy.

Notes: This app currently calls Anthropic directly from the browser; for production you should move the API key to a serverless function or backend endpoint and call that from the client to avoid exposing secrets.
