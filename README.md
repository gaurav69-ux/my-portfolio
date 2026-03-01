# Gaurav Durge — Developer Portfolio (Cloud & DevOps)

This repository contains a static developer portfolio built with plain HTML, CSS and vanilla JavaScript. The site is deployed to an AWS EC2 instance and uses GitHub Actions for CI/CD.

## Cloud & DevOps Highlights

- Hosting: AWS EC2 (Ubuntu) running a lightweight web server (NGINX).
- CI/CD: GitHub Actions pipeline that builds (optional), and deploys site assets to the EC2 instance on push to `main`.
- Deployment method: Secure SSH-based artifact copy (SCP / rsync) from GitHub Actions to EC2.
- Secrets: All sensitive data (SSH private key, EC2 host, user) stored in GitHub Secrets.
- Monitoring & ops: (recommended) add CloudWatch, basic uptime checks, and a process manager for services.

## Repository Structure

- `index.html` — main site markup
- `style.css` — styling and responsive rules
- `script.js` — client-side behavior (mobile menu, smooth scroll, EmailJS integration)
- `profile.webp` — profile image (if present)

## Architecture (high level)


graph LR
  GH[GitHub (push to main)] --> GA[GitHub Actions CI/CD]
  GA --> Build[Build / Lint (optional)]
  Build --> Deploy[Deploy via SSH/SCP]
  Deploy --> EC2[AWS EC2 (NGINX)]
  EC2 --> Users[Users (web browsers)]


## How to run locally

From the project folder you can run a simple static server (Python):

```powershell
# from project folder
python -m http.server 8000
# open http://localhost:8000
```

Or open `index.html` directly in your browser.

