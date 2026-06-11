<div align="center">

# CHRONIS

### Behavioral Intelligence Platform — Prototype

**Hiring Assessment: Task C — End-to-End User Experience Prototype**
Product & App Engineer | Submitted by Jai Dhuria

---

[![Live Demo](https://img.shields.io/badge/Live%20Demo-chornis.vercel.app-6366f1?style=for-the-badge&logo=vercel&logoColor=white)](https://chornis.vercel.app)
[![React](https://img.shields.io/badge/React-19-61DAFB?style=for-the-badge&logo=react&logoColor=black)](https://react.dev)
[![Vite](https://img.shields.io/badge/Vite-8-646CFF?style=for-the-badge&logo=vite&logoColor=white)](https://vitejs.dev)
[![Deployed on Vercel](https://img.shields.io/badge/Deployed-Vercel-black?style=for-the-badge&logo=vercel)](https://vercel.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](LICENSE)

</div>

---

## What Is Chronis?

Chronis is a **behavioral intelligence platform** that turns raw biosensor and self-reported data into actionable, confidence-aware insights. It tracks the relationships between sleep, focus, physical activity, caffeine intake, and circadian rhythm — and explains *why* those relationships exist, not just that they do.

This prototype was built for the **Chronis Product & App Engineer Hiring Assessment (Task C)**. It implements all four required components:

| Component | Description | Status |
|---|---|---|
| **Dashboard** | Behavioral trends, confidence indicators, live telemetry feed | Complete |
| **Insight Explorer** | Drill-down evidence view with uncertainty explanations and protocol triggers | Complete |
| **Narrative Timeline** | Epoch-based historical view showing behavioral evolution over time | Complete |
| **Product Judgment** | UX decisions, tradeoffs, and roadmap rationale | Complete |

---

## Live Demo

**[chornis.vercel.app](https://chornis.vercel.app)**

Start at **The Locket** → click **Begin Calibration** → explore all five tabs via the navbar.

---

## Application Walkthrough

### The Locket — Calibration Onboarding

The app opens on a dark, cinematic landing page called **The Locket**. Rather than dumping users into a dense analytics dashboard, the entry point features a **Circadian Calibration Console** — an interactive terminal that simulates a live biosensor scan before unlocking the dashboard.

**How it works:**
1. User clicks **Begin Calibration**
2. A terminal-style log streams six sequential steps — Apple Watch accelerometer link, cortisol tracker sync, blue-light log parsing, HRV baseline calibration — each with a timed delay to simulate real telemetry handshake
3. A procedural audio engine (built with the Web Audio API — no libraries) plays a low saw-hum that ramps in pitch across the scan, followed by a C5→E5→G5→C6 arpeggio chime on completion
4. After the chime, the app automatically transitions to the Dashboard

The landing page also includes a **Waitlist Form** with email validation and live simulated count (currently 1,104 signups).

**Design intent:** The calibration gate creates a narrative bridge between "product marketing" and "biosensor analytics." It gives the user a sense that the system is wiring up to their hardware — making the subsequent data feel earned and real.

---

### Dashboard

The home screen is the command center, surfacing actionable signals at a glance across four behavioral domains:

**Metric Cards — 4 tracked domains:**

| Metric | Current Value | Trend | Confidence |
|---|---|---|---|
| Sleep Quality | 84 / 100 | ↑ +5.1% | 94% — continuous Watch data |
| Cognitive Focus | 68 / 100 | ↓ −12% | 76% — desktop agent offline Tue/Wed |
| Physical Activity | 420 kcal/day | ↑ +8% | 98% — GPS + Apple Health |
| Evening Screen Time | 2.8 hrs/night | ↑ +28% | 85% — mobile + desktop logs |

Each metric card is **clickable** — tapping one navigates directly to the most relevant insight in the Explorer (e.g., Screen Time → "Late Screen Time Suppresses Sleep Quality"), with a subtle audio click via the Web Audio synth engine.

**Confidence Indicator Panel** — All four data sources are displayed with their live status and plain-language impact explanations:
- ✅ Apple Watch (HR & Movement) — 98% reliability
- ✅ Phone Usage API — 95% reliability
- ⚠️ Desktop Work Agent — 60% reliability (VPN cert expiry Tue/Wed)
- ❌ Self-Reported Dietary Logs — 40% reliability (48-hour weekend gap)

**Live Telemetry Terminal** — A rolling bio-synth log in the dashboard footer simulates live biosensor streaming: HRV deltas, adenosine clearance estimates, accelerometer deltas, and encryption handshakes cycle through every 3.8 seconds with real timestamps.

**Recent Changes Panel** — Three behavioral shift cards highlight the most meaningful signal changes from the past 7 days, each categorized as a shift, improvement, or anomaly with severity-coded styling.

---

### Insight Explorer

The Explorer is the analytical core of the app. It contains **three fully built insights**, each with supporting quantitative evidence, a data visualization, uncertainty explanations, and an actionable protocol trigger.

#### Insight 1 — Delay Caffeine to Protect Morning Focus
*Category: Focus & Circadian | Confidence: 88%*

- Correlates caffeine timing (minutes post-waking) against focus duration and afternoon crash probability
- Evidence: Focus duration 45 mins (caffeine <60m waking) vs. 110 mins (caffeine >90m waking); crash probability 78% vs. 22%
- Chart: 7-day scatter of caffeine delay vs. measured focus score
- Uncertainty: Weekend dietary logs missed — Chronis interpolated wake times from phone movement data
- **Protocol CTA:** "Start 90-Min Caffeine Delay Protocol" → activates inline tracking state

#### Insight 2 — Late Screen Time Suppresses Sleep Quality
*Category: Sleep & Circadian | Confidence: 94%*

- Correlates post-10 PM screen usage minutes against sleep latency and deep sleep duration
- Evidence: Sleep latency 34 min (screen use) vs. 12 min (no screen); deep sleep 48 min vs. 82 min
- Chart: 7-day view of sleep quality score vs. evening screen minutes
- Uncertainty: 6% gap attributed to ambient room lighting not captured by any sensor
- **Protocol CTA:** "Commit to 10 PM Digital Sunset" → commits with confirmation state

#### Insight 3 — Mid-Day Cardio Drives Next-Day HRV Recovery
*Category: Recovery & Activity | Confidence: 76%*

- Correlates 12–4 PM aerobic activity minutes against next-morning HRV
- Evidence: Next-day HRV 54ms (no exercise) vs. 69ms (mid-day cardio); resting HR 62 bpm vs. 57 bpm
- Chart: 7-day HRV vs. cardio minutes
- Uncertainty: 2-hour Monday HRV gap due to Watch sensor cleaning — data interpolated, reducing confidence from 92% to 76%
- **Protocol CTA:** "Add Cardio Blocks to Calendar" → protocol activation

**Left-panel navigation** shows all three insights with confidence badges and impact tags. The selected insight is highlighted with an accent border. Clicking any insight in the list — or navigating from a Dashboard metric card — updates the explorer without a page reload.

---

### Narrative Timeline

The Timeline organizes behavioral history into discrete, human-readable **Narrative Epochs** rather than infinite scroll time-series charts. Three epochs represent a real-world self-optimization arc:

**Epoch 1 — Baseline Audit** *(Weeks 1–2, Completed)*
> Established behavioral baseline with no interventions. Sleep was irregular, caffeine was immediate, screens ran past midnight. Chronis identified caffeine timing and screen habits as the highest-leverage levers.

| Metric | Value |
|---|---|
| Sleep Quality | 71 / 100 |
| Focus Duration | 2.1 hrs/day |
| Evening Screen | 2.9 hrs/night |
| Caffeine Delay | 15 mins |

**Epoch 2 — The Caffeine Shift** *(Weeks 3–4, Completed)*
> Isolated caffeine timing as the single intervention. Screen times and sleep schedules held constant. Result: focus duration jumped from 2.1h to 3.4h/day — a **61% increase** — with mid-morning crash eliminated.

| Metric | Value |
|---|---|
| Sleep Quality | 73 / 100 |
| Focus Duration | 3.4 hrs/day (+61%) |
| Evening Screen | 3.1 hrs/night |
| Caffeine Delay | 95 mins |

**Epoch 3 — Digital Sunset Experiment** *(Weeks 5–6, Ongoing)*
> Added the 10 PM screen curfew. Sleep quality surged from 73 to 84/100. Sleep latency dropped from 32 minutes to 11 minutes. HRV trended +8ms. Best sleep consistency in 6 months.

| Metric | Value |
|---|---|
| Sleep Quality | 84 / 100 |
| Focus Duration | 3.8 hrs/day |
| Evening Screen | 0.4 hrs/night |
| Caffeine Delay | 105 mins |

Each epoch card shows key metrics, a findings list (3 bullet observations per epoch), a status badge (Completed / Ongoing), and an outcome summary. The active epoch is visually distinguished to orient users in their own arc.

---

## Technical Architecture

### Stack

| Layer | Technology | Version |
|---|---|---|
| UI Framework | React | 19.2 |
| Build Tool | Vite | 8.0 |
| Icon Library | lucide-react | 1.17 |
| Audio Engine | Web Audio API (custom) | Native |
| Deployment | Vercel | — |
| Linting | ESLint + react-hooks plugin | 10.x |

**No charting library.** All data visualizations in the Insight Explorer are rendered with vanilla CSS and inline styles — deliberate choice to keep the bundle lean and maintain full visual control.

**No routing library.** Navigation between the five views is managed with a single `activeTab` state in `App.jsx` and a `switch` render function. With only five views and no deep-link requirements for this prototype, client-side routing would be overengineering.

### Audio Synth Engine (`src/utils/audio.js`)

A custom procedural sound engine built entirely with the [Web Audio API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API) — no audio files, no external library. Five sound types:

| Sound | Trigger | Description |
|---|---|---|
| `click` | Any nav tap or metric card click | 1200→100 Hz exponential drop, 40ms |
| `hoverTick` | Navbar hover | 1600→800 Hz, 8ms, ultra-low gain |
| `scanHum` | Calibration start | Triangle wave, 70→190 Hz ramp over 5.2s, filtered lowpass |
| `chime` | Calibration complete | C5→E5→G5→C6 sine arpeggio, 100ms apart |
| `commit` | Protocol activation | 440→880 Hz + 880→1760 Hz double sweep |

The `AudioContext` is lazily initialized on first interaction (respecting browser autoplay policies) and can be globally muted/unmuted via the Navbar mute toggle.

### Data Layer (`src/data/mockData.js`)

All behavioral data is self-contained in a single mock data module with five top-level keys:

- `userProfile` — Name, avatar (DiceBear pixel-art), join date
- `metrics` — 4 metric objects with value, trend, confidence, color, and description
- `recentChanges` — 3 behavioral shift events with severity and timestamp
- `confidenceIndicators` — 4 sensor sources with status, reliability %, and impact explanations
- `insights` — 3 full insight objects with evidence arrays, 7-day chart data, uncertainty text, and action labels
- `timelineEpochs` — 3 epoch objects with metrics, findings, status, and outcomes

### Component Map

```
src/
├── main.jsx                    # React DOM entry point
├── App.jsx                     # Root: tab state, routing, data injection
├── App.css                     # Global design tokens, layout, utility classes
├── index.css                   # CSS reset and base typography
│
├── components/
│   ├── Navbar.jsx              # Top nav with 5 tabs, mute toggle, user avatar
│   ├── LocketLanding.jsx       # Onboarding: calibration console + waitlist form
│   ├── Dashboard.jsx           # 4 metric cards, confidence panel, telemetry feed
│   ├── InsightExplorer.jsx     # Insight list + detail view with protocol triggers
│   ├── NarrativeTimeline.jsx   # Epoch cards with metrics and findings
│   └── ProductJudgment.jsx     # In-app render of UX rationale
│
├── data/
│   └── mockData.js             # All behavioral mock data (metrics, insights, epochs)
│
├── utils/
│   └── audio.js                # Web Audio API synth engine (5 sound types)
│
└── assets/
    └── hero.png                # Landing page hero image
```

---

## Local Setup

**Requirements:** Node.js 18+, npm 9+

```bash
# Clone
git clone https://github.com/Jaidhuria/Chornis.git
cd Chornis

# Install dependencies
npm install

# Start dev server (http://localhost:5173)
npm run dev

# Production build
npm run build

# Preview production build locally
npm run preview

# Lint
npm run lint
```

The Vercel deployment uses a catch-all rewrite (`vercel.json`) to support SPA routing: all paths resolve to `/index.html`.

---

## Product Judgment Summary

### Three UX Decisions

**1. Contextualizing confidence scores**
Every confidence percentage is paired with a plain-language explanation of *why* it's at that level — sensor gaps, VPN outages, charging interruptions. Users forgive missing data; they don't forgive unexplained numbers.

**2. Narrative Epochs on the Timeline**
Grouping history into human-titled chapters (Baseline → Caffeine Shift → Digital Sunset) instead of raw time-series scroll turns 6 weeks of data into a legible arc. Users see causality, not correlation noise.

**3. Inline Protocol Triggers**
The "Commit" CTA lives inside the insight card. Clicking it activates tracking immediately, eliminating the gap between reading an insight and acting on one. Motivation is highest at the moment of discovery.

### One Tradeoff

**Telemetry transparency vs. interface minimalism.** Displaying sensor dropouts, sync gaps, and reliability percentages directly on the main dashboard adds visual weight. We accepted this cost because a user acting on silently incorrect data is worse than a user seeing a slightly busier UI. Trust is the product.

### One Prioritized Future Feature

**Passive Circadian Calibration Prompts** — A real-time engine that detects sensor dropouts and sends context-aware nudges at optimal circadian windows. If the Watch battery drops below 15% at 9 PM: *"Charge for 20 minutes now so we can track tonight's deep sleep."* If a dietary log is skipped: *"Did you drink coffee before 10 AM? [Yes / No]."*

A behavioral analytics platform is only as valuable as the quality of its input streams. This feature turns data collection from a manual burden into a guided habit loop.

---

*Built for the Chronis Product & App Engineer Hiring Assessment — Task C*
*Prototype recreated from [chronis.in](https://www.chronis.in)*
