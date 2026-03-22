# Lead Capture Popup + Mobile Header Fix

## Overview
Add a lead capture popup to the Buyer Tour Scheduling App showcase to collect early access sign-ups from realtors viewing the demo.

## Lead Capture Popup

### Trigger
- Popup appears when user reaches **slide 4** (Route Optimizer)
- `sessionStorage` prevents re-triggering within the same session
- If user has already submitted, never show again (`localStorage`)

### Full Popup UI
- Backdrop: `rgba(0,0,0,0.5)` covering viewport
- Card: white background, `border-radius: 20px`, max-width `400px`, centered
- Header: "Sign Up Today for Free Early Access" in sage green (`#8a9a7b`)
- Form fields:
  - Name (required)
  - Email (required)
  - Brokerage (required)
  - Phone (optional, labeled as such)
- Submit button: sage green background, white text, "Get Early Access"
- Close: X button top-right corner
- Animation: fadeIn + scaleIn (0.95 -> 1), 300ms ease

### Dismiss -> Floating Button
- When user closes popup via X, a floating pill button appears
- Position: `fixed`, bottom-right (`bottom: 24px; right: 24px`)
- Label: "Get Free Early Access"
- Style: sage green background, white text, pill shape, subtle bounce animation
- Click: re-opens the full popup
- Disappears permanently after successful form submission

### Data Submission
- POST to Google Apps Script Web App URL
- Payload: `{ name, email, brokerage, phone, timestamp }`
- Script writes row to Google Sheet
- On success: form replaced with "Thank you! We'll be in touch." message, auto-close after 2s
- On error: show inline error, allow retry

## Mobile Header Fix
- Reduce top padding: `48px` -> `28px`
- Reduce h1 font: `24px` -> `20px`
- Reduce subtitle font: `14px` -> `12px`
- Tighten dot indicator and title spacing
