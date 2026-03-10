# Build Spec

## Tech Stack

- Single index.html file
- Tailwind CSS (CDN)
- Vanilla JavaScript (no framework)
- No backend, no build step
- Local dev: just open the file or use a simple HTTP server

## Page Structure

### 1. Welcome Screen
- JWB logo/attribution at top
- "Move Your Mental Health" title
- Brief intro: "Take this 2-minute quiz to discover the best movement practice for your wellbeing - backed by 1,600+ scientific studies."
- "Get Started" button
- Mobile: full viewport height, centered

### 2. Quiz Flow (5 screens)
- One question per screen
- Progress indicator (dots or bar: 1/5, 2/5, etc.)
- Answer options as large tappable cards (mobile-first)
- Back button on Q2-Q5
- Smooth transition between questions
- No "submit" button - tapping an answer advances to next question

### 3. Results Screen
- "Your Movement Plan" header
- Top 3 recommendations as cards, ranked #1 (featured/large), #2, #3
- Each card shows:
  - Exercise name
  - "Why this matches you" (personalized to their Q1 answer)
  - "Your starter routine" (personalized to their Q2 level + Q5 duration)
  - Evidence callout (% of studies, from the data matrix)
- #1 card includes the "build from here" message
- "Retake Quiz" button at bottom
- Share/save option (simple - print or screenshot prompt)

### 4. Footer
- Medical disclaimer
- Crisis resources (988 Lifeline)
- JWB report citation and link
- "Learn more at johnwbrickfoundation.org"

## Design Tokens

```
--color-navy-dark: #0a1628
--color-navy: #1a2744
--color-blue: #2d5f9a
--color-cyan: #5bc4d4
--color-cyan-light: #7dd8e6
--color-white: #ffffff
--color-text-muted: #94a3b8 (slate-400)

--font-heading: system sans-serif (clean, modern)
--font-body: system sans-serif

--radius: 12px (cards)
--spacing-card: 24px padding
```

## Responsive Breakpoints

- Mobile first: 320px-768px (primary target)
- Tablet: 768px-1024px
- Desktop: 1024px+

## Animations

- Subtle fade/slide between quiz questions
- Card entrance animation on results
- Keep it smooth but not slow - this is a quick tool

## Accessibility

- All interactive elements keyboard-navigable
- Sufficient color contrast on navy backgrounds
- ARIA labels on progress indicator
- Focus states visible

## Disclaimer Text

"This tool provides general wellness information based on the Move Your Mental Health report, a review of over 1,600 scientific studies. It is not a substitute for professional medical or mental health advice, diagnosis, or treatment. Always seek the advice of a qualified health provider with any questions you may have regarding a medical condition. If you are in crisis or experiencing thoughts of self-harm, please contact the 988 Suicide & Crisis Lifeline by calling or texting 988."

## Attribution Text

"Based on the Move Your Mental Health Report (2022) by the John W. Brick Mental Health Foundation - a review of over 1,600 peer-reviewed studies on exercise and mental health. Learn more at johnwbrickfoundation.org/move-your-mental-health-report"

## Dev Server

Run locally: `python3 -m http.server 8080` or `npx serve .`
