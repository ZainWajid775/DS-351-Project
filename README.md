# PULSE — Engine Health Intelligence

> A narrative web visualization exploring fault patterns across 19,535 engine sensor readings.

**Live Demo:** [https://your-username.github.io/pulse-engine-health](https://zainwajid775.github.io/pulse-engine-health)  
**Course:** Information Visualization — Spring 2026  
**Team:** Zain Wajid (2023775) · Abdullah Yasin (2023049)

---

## What This Is

PULSE is a scrollytelling data story built with D3.js. It guides the reader through three research questions about automotive engine health — using a combination of author-driven narrative chapters and a reader-driven interactive explorer — to answer the question:

> **Can real-time sensor telemetry detect engine faults before catastrophic failure?**

The answer, across 19,535 readings and 6 sensor streams, is yes — and PULSE shows you exactly how.

---

## Project Structure

```
pulse-engine-health/
├── index.html          ← The entire visualization (single-file, self-contained)
├── engine_data.csv     ← Raw dataset (19,535 engine sensor readings)
└── README.md           ← This file
```

The visualization is fully self-contained in `index.html`. It embeds a 200-point representative sample directly in the JavaScript for the interactive charts, and loads the full CSV for the scrollytelling histograms.

---

## The Story

The visualization unfolds across five chapters:

| Chapter | Title | Type |
|---------|-------|------|
| Hero | Engine Telemetry Intelligence | Author-driven — cinematic entry |
| 01 | The Fleet at a Glance | Author-driven — dataset overview |
| 02 | RPM: The Loudest Signal | Scrollytelling — 4-step animated sequence |
| 03 | Reading the Warning Signs | Author-driven — multi-sensor analysis |
| 04 | Your Turn to Explore | **Reader-driven** — interactive scatter plot |
| 05 | What the Data Tells Us | Author-driven — findings & conclusions |

---

## Dataset

**Automotive Vehicles Engine Health Dataset**  
Source: [Kaggle — Parv Modi](https://www.kaggle.com/datasets/parvmodi/automotive-vehicles-engine-health-dataset)

| Property | Value |
|----------|-------|
| Records | 19,535 |
| Features | 6 sensor variables + 1 condition label |
| Target | Engine Condition: `1` = Good · `0` = Faulty |
| Class split | 63.1% Good · 36.9% Faulty |
| Missing values | None |

**Sensor Features:**

| Feature | Unit | Key Finding |
|---------|------|-------------|
| Engine RPM | RPM | Faulty engines average +148 RPM higher |
| Lub Oil Pressure | Bar | Pressure *instability* is the fault signal |
| Fuel Pressure | Bar | Extremes in both directions indicate faults |
| Coolant Pressure | Bar | Outliers in either direction precede failure |
| Lub Oil Temperature | °C | Compound thermal stress is the top predictor |
| Coolant Temperature | °C | Combined with oil temp → worst fault outcomes |

---

## Research Questions & Key Findings

**Q1 — RPM & Fuel Pressure as fault indicators**  
Faulty engines run at a mean of 885 RPM vs. 736 RPM for healthy ones. Engines above 1,400 RPM show the highest fault concentration. Fuel pressure extremes — starvation *and* over-pressure — both signal distinct failure modes.

**Q2 — Oil & Coolant Pressure as fault indicators**  
Pressure *instability* — not a single threshold — is the diagnostic signature. Multi-modal distributions in faulty engines expose at least three concurrent failure mechanisms: pump failure, active leak, and blockage.

**Q3 — Thermal Interaction as the primary failure predictor**  
High oil temperature and high coolant temperature individually elevate fault risk, but occurring *simultaneously* produces disproportionately worse outcomes. The interaction heatmap confirms compound thermal stress as the primary mechanical failure pathway.

---

## Tech Stack

| Tool | Version | Purpose |
|------|---------|---------|
| D3.js | v7.8.5 | All charts — histograms, scatter, box plots, gauges, donut |
| Syne | Google Fonts | Display / heading typeface |
| Space Mono | Google Fonts | Section labels / monospace telemetry aesthetic |
| Inter | Google Fonts | Body text |
| Vanilla JS | ES2020 | IntersectionObserver scrollytelling, transitions |
| CSS | Custom properties | Theming, animations, responsive layout |

No build step. No framework. No bundler. Pure HTML + CSS + JS — open `index.html` in a browser and it works.

---

## Running Locally

```bash
# Clone the repo
git clone https://github.com/your-username/pulse-engine-health.git
cd pulse-engine-health

# Option A — Python (built-in, recommended)
python -m http.server 8000
# Open http://localhost:8000

# Option B — Node.js
npx serve .
# Open http://localhost:3000

# Option C — VS Code
# Install the "Live Server" extension, right-click index.html → Open with Live Server
```

> **Why a server?** The visualization fetches `engine_data.csv` via a relative path. Browsers block local file requests (CORS), so you need a local server — or just deploy to GitHub Pages and browse it there.

---

## Acknowledgements

- **Dataset:** Automotive Vehicles Engine Health Dataset — Parv Modi, Kaggle (2024)
- **Visualization library:** [D3.js](https://d3js.org/) v7.8.5 — Mike Bostock et al.
- **Scrollytelling pattern inspiration:** [The Pudding](https://pudding.cool)
- **Color & design inspiration:** Bloomberg Terminal, NASA Mission Control telemetry displays, NYT Visual Investigations
- **Technical references:** Bosch Automotive Handbook (9th Ed.); SAE Technical Paper 2019-01-0232; ASME Tribology Transactions
- **Course reference:** [vis-society.github.io](https://vis-society.github.io/)

---

## Team

| Name | Reg. No. |
|------|----------|
| Zain Wajid | 2023775 |
| Abdullah Yasin | 2023049 |

*PULSE — Engine Condition Visualization © 2026*
