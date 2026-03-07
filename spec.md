# Website Specification

## Overview
Personal website for Stuti Nayak, served over HTTPS on a custom domain via GitHub Pages.

## Hosting
- **Platform:** GitHub Pages (free tier)
- **Repository type:** Public or Private (GitHub Pages works on both for personal accounts)
- **Branch:** `main` (or `gh-pages` branch)
- **HTTPS:** Enabled via GitHub Pages + Let's Encrypt (free, automatic)

## Domain
- **Custom domain:** `stutinayak.com`
- **DNS provider:** Namecheap

## Tech Stack
- **HTML/CSS/JS** — static site (no backend required for GitHub Pages)
- Optionally: a static site generator (e.g. Hugo, Jekyll, Astro, Next.js with static export)

## Pages / Sections
- [ ] Home / Landing page
- [ ] About
- [ ] Projects / Work
- [ ] Contact

## Design
- Responsive (mobile + desktop)
- Accessible (WCAG AA)

## Requirements
- HTTPS enforced (no HTTP access)
- Custom domain resolves correctly
- Fast load time (minimal dependencies)

---

## Deployment Steps

### 1. Create GitHub Repository
- Go to github.com and create a new repo
- Name it `<your-github-username>.github.io` for a user site, OR any name for a project site
- Initialize with a README

### 2. Build Your Site Locally
- Add your `index.html` (and other files) to the repo
- Commit and push to `main`

### 3. Enable GitHub Pages
- Go to repo Settings > Pages
- Source: Deploy from branch > `main` > `/ (root)` or `/docs`
- GitHub will give you a `*.github.io` URL — verify it works

### 4. Configure Custom Domain on GitHub
- In Settings > Pages > Custom domain, enter your domain (e.g. `stutinayak.com`)
- Check "Enforce HTTPS" (this option appears after DNS is verified)

### 5. Configure DNS at Your Domain Registrar
For an apex domain (e.g. `example.com`), add these A records:
```
A  @  185.199.108.153
A  @  185.199.109.153
A  @  185.199.110.153
A  @  185.199.111.153
```
For a `www` subdomain, add a CNAME record:
```
CNAME  www  <your-github-username>.github.io
```

### 6. Wait for DNS Propagation
- DNS can take a few minutes to 48 hours to propagate
- You can check with: `dig your-domain.com` or https://dnschecker.org

### 7. Enable HTTPS
- Once DNS is verified, go back to Settings > Pages
- Check the box: "Enforce HTTPS"
- GitHub will auto-provision an SSL certificate via Let's Encrypt
- Certificate provisioning can take up to 24 hours after DNS propagates

### 8. Verify
- Visit `https://your-domain.com` — it should load over HTTPS with a valid certificate
- Check that HTTP redirects to HTTPS automatically

---

## File Structure (suggested)
```
website_stuti/
├── index.html
├── about.html
├── projects.html
├── contact.html
├── css/
│   └── style.css
├── js/
│   └── main.js
├── assets/
│   └── images/
└── CNAME          # contains your custom domain, e.g.: stutinayak.com
```

## Notes
- The `CNAME` file in the repo root must contain your domain (GitHub Pages uses it)
- GitHub Pages has a soft limit of 1 GB storage and 100 GB/month bandwidth (plenty for a personal site)
- Certificates auto-renew — no manual action needed
