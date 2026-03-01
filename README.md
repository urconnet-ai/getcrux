# Crux

Chrome extension that summarizes Gmail threads and synthesizes open browser tabs into a single, structured output.

---

## What It Does

**Email Thread** — Open any Gmail thread, click Crux, get a structured summary: what was decided, what is still open, and what action you need to take. No reading required.

**Tab Synthesis** — With multiple tabs open (research, shopping, news), click Crux and get a synthesized answer: the core question, consensus across sources, key differences, and a direct verdict.

---

## Project Structure

```
crux/
  manifest.json         Chrome extension config (Manifest V3)
  popup.html            Extension popup UI
  settings.html         API key configuration page
  src/
    popup.js            All UI logic, Claude API calls, state management
    background.js       Service worker — install lifecycle, message routing
    gmail.js            Content script injected into Gmail pages
  icons/
    icon16.png          (to be created)
    icon48.png          (to be created)
    icon128.png         (to be created)
```

---

## Loading Into Chrome (Development)

1. Open Chrome and navigate to `chrome://extensions`
2. Enable **Developer Mode** (toggle, top right)
3. Click **Load unpacked**
4. Select the `crux/` folder
5. The extension icon appears in your Chrome toolbar

---

## Configuration

Crux requires a Claude API key to function.

1. Get your key at [console.anthropic.com](https://console.anthropic.com)
2. Click the Crux icon in Chrome toolbar
3. Click **Settings** at the bottom of the popup
4. Paste your API key and click **Save Key**

Your key is stored locally in Chrome's extension storage. It never leaves your device in development mode.

---

## Business Model

| Tier   | Price       | Limits                            |
|--------|-------------|-----------------------------------|
| Free   | $0          | 15 summaries per month            |
| Pro    | $8 / month  | Unlimited summaries, both features |

Payment via Stripe. Upgrade prompt appears when free limit is reached.

---

## What Needs Building Before Launch

- [ ] Create icon files (16x16, 48x48, 128x128 PNG)
- [ ] Build a lightweight backend to proxy Claude API calls (protects API key in production)
- [ ] Integrate Stripe for payment and pro activation
- [ ] Build a landing page at a custom domain
- [ ] Submit to Chrome Web Store ($5 one-time developer fee)

---

## Tech Stack

| Layer          | Tool                   | Cost                     |
|----------------|------------------------|--------------------------|
| AI             | Claude Haiku API       | ~$0.01 per summary       |
| Extension      | Chrome MV3, vanilla JS | Free                     |
| Auth + Storage | Chrome Storage API     | Free                     |
| Payments       | Stripe                 | Free until revenue       |
| Backend (prod) | Node.js on Railway     | Free tier available      |

---

## Revenue Projection

| Month | Paying Users | MRR     |
|-------|-------------|---------|
| 2     | 10–20       | $80–160 |
| 3     | 30–60       | $240–480 |
| 6     | 100–150     | $800–1,200 |
