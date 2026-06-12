# Gas Turbine Air-Permitting Lane Finder

A single-page, client-side tool that screens federal (PSD / NSPS Subpart KKKKa / Title V)
and Texas (TCEQ) air-permitting paths for stationary combustion turbines. Enter a turbine,
operation, and emission controls, and it computes potential-to-emit, runs the major-source
tests, shows which permitting "lane" applies, suggests target control levels, and lays out
the application steps with links.

> **Disclaimer:** Planning/screening tool only — not a permit determination or legal advice.
> Replace nominal preset specs and default emission factors with vendor-guaranteed rates and
> your pipeline-gas sulfur spec, and have a Texas-licensed air-permitting professional run the
> formal applicability analysis and NAAQS modeling before filing.

## Tech

- 100% static: one `index.html` with inline CSS + vanilla JavaScript. **No build step, no backend.**
- Settings persist in the browser via `localStorage`.
- No external dependencies or network calls.

## Run locally

Just open `index.html` in any browser. (Or serve it: `python3 -m http.server` then visit http://localhost:8000.)

## Deploy to Vercel (via GitHub)

1. Put `index.html` in this folder (rename your working file: `Turbine_Permit_Tool.html` -> `index.html`).
2. Create the repo and push:
   ```bash
   git init
   git add .
   git commit -m "Initial commit: turbine air-permitting tool"
   git branch -M main
   git remote add origin https://github.com/<your-username>/turbine-permit-tool.git
   git push -u origin main
   ```
3. In Vercel: **Add New… → Project → Import** your GitHub repo.
   - Framework Preset: **Other**
   - Build Command: *(leave empty)*
   - Output Directory: *(leave empty / root)*
   - Click **Deploy**. Every future `git push` auto-deploys.

## Optional phase 2 — Supabase

Not needed for current functionality (everything runs in the browser). Add later only if you
want saved/shareable scenarios or user logins across devices; that would add a small backend
(e.g., a Vercel serverless function + Supabase table) and environment variables in Vercel.

## Sources behind the rules

EPA NSPS Subpart KKKKa fact sheet & 40 CFR 60 Subpart KKKKa; 40 CFR 52.21 (PSD); EPA AP-42
Section 3.1 (turbine emission factors); EPA Method 19 / 40 CFR 75 App F (ppm conversions);
TCEQ EGU Standard Permit (30 TAC 116.601-615) and Title V (30 TAC Ch. 122); GE Vernova /
Siemens Energy turbine datasheets.
