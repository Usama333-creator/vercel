# Améza Parfums — Vercel-ready

React (Vite) frontend + Express API (Supabase), deployed together on Vercel.
The API runs as a serverless function (`api/index.js` → `backend/src/server.js`), the site is served from `frontend/dist`.

## Deploy
1. Push this folder to GitHub → Vercel → **Add New Project** (root directory = this folder, framework "Other").
2. Add the environment variables from `.env.example` (Project → Settings → Environment Variables).
   - `SUPABASE_SERVICE_ROLE_KEY` is secret: set it only in Vercel, never commit it.
3. Deploy. Admin panel: `/admin`. Health check: `/health`.

## New: "What's your mood today?" section
`frontend/src/components/MoodPicker.jsx` + `frontend/src/styles/mood-picker.css`, shown on the home page under the category tiles.
Each mood loads the matching real product (name, price, bottle image, Add to cart) and plays its own animation.
To change which perfume belongs to a mood, edit `handle` in the `MOODS` list.

Everything else (products, cart, checkout, orders, admin, Supabase) is unchanged.
The only backend edit: `server.js` no longer calls `listen()` on Vercel and exports the app.

Local: `cd backend && npm i && npm run dev` and `cd frontend && npm i && npm run dev`.
