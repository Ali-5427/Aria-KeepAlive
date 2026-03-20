# ARIA Keep-Alive

Keeps Kaggle-hosted Ollama model alive by pinging it every 30 seconds.

## How it works

cron-job.org → pings Render app every 14 minutes (keeps Render alive)
Render app → pings Ollama on Kaggle every 30 seconds (keeps model alive)

## Setup

### Environment Variables
Add these in Render dashboard:
- `KAGGLE_URL` — your Cloudflare tunnel URL from Kaggle
- `MODEL_NAME` — model name (default: qwen2.5:7b)

### Update URL
Every new Kaggle session generates a new tunnel URL.
Just update `KAGGLE_URL` in Render environment variables and redeploy.

## Files
- `keepalive.py` — main script that pings Ollama every 30 seconds
- `requirements.txt` — Python dependencies
- `render.yaml` — Render deployment config
