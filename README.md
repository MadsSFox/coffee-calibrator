# Sage Coffee Calibrator

A single-file web app for dialling in espresso on a Sage machine. Measure, diagnose, and get machine-specific adjustment advice.

**[Open the app →](https://madsSFox.github.io/coffee-calibrator)**

## Features

- **pH slider** — set your espresso pH (3.0–7.0) to indicate extraction level
- **Crema colour picker** — six swatches from no crema to dark/black
- **Extraction time** — optional seconds input for finer diagnosis
- **Machine profile** — select your Sage model for model-specific grind/dose recommendations
  - Barista Express, Barista Pro, Oracle, Oracle Touch, Dual Boiler, Bambino, Bambino Plus
  - Reads grinder dial or display via photo (Claude AI vision)
- **Crema photo analysis** — upload a top-down shot and let Claude classify the crema colour
- **Instant diagnosis** — 9 extraction cases mapped to actionable Sage-specific advice
- **PWA / iPhone** — add to Home Screen from Safari for a full-screen app experience, works offline

## How to use

1. Open the app in Safari on iPhone (or any browser on desktop)
2. Select your Sage model under **Machine Profile**
3. Set the **pH** using the slider (use a digital pH pen for best accuracy — paper strips are unreliable with dark espresso)
4. Pick the closest **crema colour**
5. Optionally enter **extraction time** in seconds
6. Tap **Evaluate & Calibrate**

## Add to iPhone Home Screen

1. Open the link in **Safari** (must be Safari, not Chrome)
2. Tap the Share button → **Add to Home Screen**
3. The app installs with a coffee icon, opens full-screen, and works offline

## pH measurement note

Paper pH strips are inaccurate with dark-coloured liquids like espresso — the brown colour interferes with the indicator dye reading. A digital pH pen (~€15–25, e.g. Hanna or Milwaukee) gives reliable results.

## AI photo analysis

Crema photo analysis and machine settings reading use the [Claude API](https://console.anthropic.com). Enter your Anthropic API key in the **API Settings** section of the app. The key is stored only in your browser's localStorage and sent only to `api.anthropic.com`.

## Technical

- Pure HTML/CSS/JS — zero dependencies, no build step
- Single file (`index.html`) — works from the filesystem or any static host
- API calls go directly to `api.anthropic.com` from the browser (using `anthropic-dangerous-direct-browser-access`)
- PWA: inline manifest + service worker registered via Blob URL
