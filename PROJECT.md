# Move Your Mental Health - Quiz Tool

## What This Is

A static web page for the John W. Brick Mental Health Foundation where visitors take a 5-question quiz about their current mental wellbeing and receive a personalized exercise recommendation they can do once a week to benefit their mental health.

Based on JWB's "Move Your Mental Health" report (2022) - a scoping review of 1,623 peer-reviewed studies mapping exercise types to mental health outcomes.

## Client

Leah (via Avry) for the John W. Brick Mental Health Foundation (johnwbrickfoundation.org)

## Audience

General public seeking non-crisis mental wellbeing advice and resources. These are people who don't exercise much - adding movement once a week is a meaningful step for them.

## Key Decisions

- 5 questions, not more
- Results: ranked list of top 3 exercise recommendations
- Take quiz once, get a recommendation to do once/week
- Framing: "start with once/week, optimal is 3-5x/week, build from there"
- Static page, no backend, no data collection, no accounts
- Mobile-first design
- Client-side logic only (vanilla JS + Tailwind)
- Must include medical disclaimer + crisis resources
- Must include proper JWB report attribution per their copyright

## Brand

Colors pulled from johnwbrickfoundation.org:
- Deep navy/dark blue: ~#0a1628 to #1a2744 (background gradients)
- Medium blue: ~#2d5f9a (mid-tones)
- Light cyan/teal: ~#5bc4d4 to #7dd8e6 (accents, highlights)
- White: #ffffff (text on dark backgrounds)
- Subtle starfield/cosmic aesthetic on their hero section
- Clean, professional, calming

## Source Report

PDF: ~/Downloads/MYMH_FullReport_2022.pdf
Published: August 2022
Authors: Cassandra Vieten PhD, Meredith Sprengel, Olivia Lubarsky et al.
Copyright: John W. Brick Mental Health Foundation
Citation required: "John W. Brick Mental Health Foundation (2020) Move Your Mental Health: A Review of the Scientific Evidence on the Role Exercise and Physical Activity in Mental Health"

## Files

- PROJECT.md - this file (what and why)
- QUIZ-DESIGN.md - the 5 questions, answer options, scoring logic
- DATA-MATRIX.md - exercise-to-condition mappings extracted from the report
- BUILD-SPEC.md - technical spec for the actual page
- WEBSITE-REBUILD.md - research notes for potential full JWB website rebuild
- index.html - the quiz (live, working)

## Deploying Live

The quiz is a single static HTML file - no build step, no backend. Two easy options to get it live on a public URL:

### Option 1: GitHub Pages (free, easiest)
1. Go to the repo Settings > Pages
2. Under "Source", select "Deploy from a branch"
3. Pick `main` branch, `/ (root)` folder
4. Click Save
5. The quiz will be live at `https://<username>.github.io/leah-idea/` within a few minutes

### Option 2: Vercel (free, more features)
1. Go to vercel.com and sign in with GitHub
2. Click "Add New Project" and import this repo
3. No build settings needed - it detects the static HTML automatically
4. Click Deploy
5. Get a live URL like `leah-idea.vercel.app` (can connect a custom domain later)

**Vercel advantages:** Custom domains, automatic HTTPS, instant deploys on every push, analytics. Better for production.
**GitHub Pages advantages:** Zero setup, no extra account needed, good enough for sharing and review.

### Option 3: Embed in existing WordPress site
If JWB wants the quiz on their current site without a full rebuild, the index.html content can be embedded into a WordPress custom HTML block or page template. This keeps everything on johnwbrickfoundation.org.

## Backlog

- [ ] **Deploy quiz live** - Pick a hosting option above and deploy so JWB team can review
- [ ] **Website rebuild exploration** - JWB is considering a full website redesign (currently WordPress). Need to understand Leah's actual pain point with the current site before scoping. See `WEBSITE-REBUILD.md` for research notes and open questions.
- [ ] Get feedback from Leah on quiz v1
- [ ] Decide final hosting for quiz (embed in existing WordPress? standalone subdomain? Vercel?)
