# Vercel Deployment Guide — Modern Company Website

## Quick Start Deployment (5 minutes)

### Prerequisites
- GitHub account with your repo pushed
- Vercel account (free tier available at vercel.com)

### Step 1: Push to GitHub
```powershell
cd "C:\Users\hp\Desktop\Modern Company Website"
git init
git add .
git commit -m "Initial commit - ready for Vercel"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
git push -u origin main
```

### Step 2: Connect to Vercel
1. Go to https://vercel.com
2. Click "New Project"
3. Select "Import Git Repository"
4. Paste your GitHub repo URL and click Import
5. Vercel auto-detects Vite + React settings
6. Click "Deploy"

**That's it!** Your frontend is live. Vercel automatically runs `npm run build` and serves the `dist/` folder.

### Step 3: Add Environment Variables (Optional)
If you want to connect to a backend API:

1. In Vercel project dashboard, go to **Settings** → **Environment Variables**
2. Add new variable:
   - Name: `VITE_API_URL`
   - Value: `https://your-backend-url.com` (e.g., a Render, AWS, or GCP backend)
3. Redeploy from the Deployments tab

## What Gets Deployed

✅ Frontend React app (Vite optimized)
✅ All pages (Home, Projects, Clients, Contact, Admin)
✅ localStorage fallback mode (works without backend)
✅ All UI components and animations

❌ Backend API (not included in Vercel Frontend deployment)

## Deploying the Backend (Optional)

If you want to also deploy the JSON backend or MongoDB backend:

### Option A: Lightweight JSON Backend → Render
1. Create account at https://render.com
2. New → Web Service → Connect GitHub repo
3. Configure:
   - Runtime: Node
   - Build command: `cd server && npm install`
   - Start command: `npm --prefix server start`
4. Deploy
5. After deployment, get URL (e.g., `https://yourapp.onrender.com`)
6. Add to Vercel env var `VITE_API_URL=https://yourapp.onrender.com`

### Option B: MongoDB Backend → Render
1. Same as above but point to `backend/` folder
2. Create `.env` on Render with:
   ```
   MONGO_URI=mongodb+srv://user:password@cluster.mongodb.net/dbname
   PORT=5000
   ```
3. Deploy
4. Connect frontend via `VITE_API_URL`

## What Vercel Does Automatically

- Builds the project using `npm run build`
- Serves static files from `dist/`
- Handles routing via SPA rewrite (all routes → index.html)
- Caches assets and CDN distribution
- Free SSL/HTTPS for your domain
- Auto-redeploys on git push

## Performance Notes

- Vercel serves your frontend from a global CDN (fast)
- First visit may take 1-2s (cold start), then cached
- localStorage works in the browser (no server needed for demo)
- If you add a backend API, latency depends on backend region

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Build fails | Check `npm run build` works locally first; push fixes to git |
| 404 errors | Vercel's SPA rewrite handles all routes; check network tab for API calls |
| API calls fail | Set `VITE_API_URL` env var in Vercel Settings to your backend URL |
| Page is blank | Check browser console for JS errors; Vite build output in Vercel logs |

## Access Your Site

After deployment, Vercel gives you a URL like:
```
https://your-project-name.vercel.app
```

Share this link anywhere! It's live on the internet.

## Redeploy

Every time you push to `main` branch on GitHub, Vercel auto-redeploys. No extra steps needed.

## Next Steps

1. **Try it**: Deploy now and share the link.
2. **Custom domain**: In Vercel Settings, add your own domain (e.g., mycompany.com).
3. **Staging**: Create a new branch (e.g., `staging`) for a separate preview deployment.
4. **Backend**: Deploy your backend separately and set `VITE_API_URL` env var.

## Commands for Local Testing Before Deploy

```powershell
# Build locally (same as Vercel does)
npm run build

# Preview build locally
npm run preview

# If satisfied, push to git
git add .
git commit -m "Ready for deployment"
git push
```

That's all! Your site is now on Vercel and globally accessible.

Questions? Check Vercel docs: https://vercel.com/docs
