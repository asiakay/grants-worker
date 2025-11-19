# 🚀 Grants Dashboard  
Cloudflare Worker API + Cloudflare Pages UI  
Auto-generated & deployed using GitHub Actions

---

## 🔥 Overview

This project provides a fast, modern interface for searching federal grants using the Grants.gov `search2` API.

Everything — the Worker code, TypeScript build, UI files, and deployments — is generated **programmatically** in a GitHub Action.  
No local environment or manual build steps required.

---

## 🌐 Architecture

```
repo/
 └── .github/workflows/deploy.yml     # Full automation pipeline
     generates →
 ├── src/index.ts                     # Worker API (TypeScript)
 ├── dist/index.js                    # Compiled Worker
 ├── wrangler.toml                    # Worker configuration
 ├── tsconfig.json                    # TS compiler rules
 └── public/                          # Frontend UI deployed to Pages
      ├── index.html
      ├── styles.css
      └── app.js (Worker URL injected at build time)
```

All generated files are created **inside CI**.

---

## 🛠 Features

### **Cloudflare Worker (API)**
- Written in TypeScript  
- Calls the Grants.gov search API  
- Accepts a `?keyword=` query param  
- Returns JSON  
- Includes CORS headers  
- Automatically deployed via `wrangler deploy`

### **Frontend UI**
- Pure HTML, CSS, JS  
- Clean card-style grant results  
- Keyword search bar  
- Makes API request to Worker  
- Deployed to Cloudflare Pages on every push

### **CI/CD**
- No local Wrangler or Node.js required  
- GitHub Actions generates everything  
- Worker + UI deployed on every push to `main`

---

## 🔧 Required GitHub Secrets

Add these in:

**Repository Settings → Secrets → Actions**

| Secret | Description |
|--------|-------------|
| `CLOUDFLARE_API_TOKEN` | API token with Workers + Pages permissions |
| `CLOUDFLARE_ACCOUNT_ID` | Your Cloudflare account ID |
| `WORKER_URL` | URL of your deployed Worker (e.g. `https://grants-worker.<yourname>.workers.dev`) |
