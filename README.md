
  # Premium Responsive Website Design

  This is a code bundle for Premium Responsive Website Design. The original project is available at https://www.figma.com/design/v3eLnByyGAxml4nph4uiQC/Premium-Responsive-Website-Design.

## Running the project (frontend + backend)

Quick overview:

- Option A — Frontend-only (fast demo): the app runs in the browser and stores contact messages, subscribers, projects and clients in `localStorage`.
- Option B — Lightweight JSON backend (`server/`): quick local Node/Express server that persists to `server/data.json` (no native modules required).
- Option C — Full MongoDB backend (`backend/`): production-like backend (Mongoose + MongoDB Atlas). Use when you need a real database.

Recommended quick start (Option A):

1. Open PowerShell and run:

```powershell
cd "C:\Users\hp\Desktop\Modern Company Website"
npm install
npm run dev
```

This runs the frontend (Vite) at `http://localhost:5173` by default. Without `VITE_API_URL` set, the frontend uses localStorage fallbacks (no server required).

Run lightweight JSON backend (Option B):

1. In one terminal start the server:

```powershell
cd "C:\Users\hp\Desktop\Modern Company Website\server"
npm install
npm run dev
```

2. In another terminal start the frontend (project root):

```powershell
cd "C:\Users\hp\Desktop\Modern Company Website"
npm install
npm run dev
```

3. (Optional) If you want the frontend to use the JSON backend, create a `.env` or set `VITE_API_URL` to `http://localhost:4000` in the project root and restart Vite.

Run both frontend + server together (single command):

```powershell
cd "C:\Users\hp\Desktop\Modern Company Website"
npm install
npm run dev:all
```

Full MongoDB backend (Option C) — Flipr assignment backend:

1. Configure MongoDB (Atlas) and create a `.env` in `backend/` with `MONGO_URI` and optional `PORT`.
2. Start the backend:

```powershell
cd "C:\Users\hp\Desktop\Modern Company Website\backend"
npm install
npm run dev
```

3. Point the frontend to the backend by setting `VITE_API_URL` to the backend URL (e.g. `http://localhost:5000`) and restart Vite.

Important notes
- `src/lib/api.ts` detects `VITE_API_URL` — when set the frontend calls the remote API; when unset the helper uses localStorage fallbacks for messages, subscribers, projects and clients so the UI remains fully interactive without a server.
- The `server/` implementation is intentionally lightweight and file-based for fast local demos — it's not recommended for production use. Use `backend/` (MongoDB) for production-like behavior.
- Dev scripts use `node --watch` (Node >=18 recommended). If you have an older Node version, replace with `nodemon` or run without the `--watch` flag.

If you'd like, I can now:

- Add simple confirm dialogs for deletes in the Admin panel.
- Add small toasts for success/error feedback after actions (add/delete/subscribe/send).
- Run through the app end-to-end and help troubleshoot any runtime errors you hit locally.

Tell me which of the above you'd like next and I'll proceed.
  