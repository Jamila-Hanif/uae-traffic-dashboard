# Gridlock Watch — UAE Traffic Congestion Dashboard

An interactive, single-file dashboard visualizing one of the UAE's highest-need,
fastest-worsening problems: road traffic congestion.

[**Live demo →**](https://Jamila-Hanif.github.io/uae-traffic-dashboard/)

---

## The problem

Dubai motorists lost **45 hours to traffic in 2025**, up from 35 hours in 2024 — a
29% jump in a single year (Inrix Global Traffic Report). A 10km drive now averages
**19.1 minutes**. Congestion is reshaping where people live, feeding into commuter
stress and burnout, and costing the road network measurably as vehicle density
climbs faster than infrastructure.

Of the candidate problems considered (traffic, housing affordability, healthcare
access), traffic congestion was chosen because it had:
- The clearest year-over-year worsening trend
- The most available public data (Inrix, TomTom, RTA, Gulf News reporting)
- A live government response already underway (RTA's 2026 intervention plan) to
  benchmark against

## What the dashboard shows
| **Section** | **What it visualizes** |
| --- | --- |
| Hero stat | Hours lost per year, styled as a highway gantry sign |
| Metric strip | Avg. 10km drive time, RTA upgrade sites, initiative count, capacity gains |
| Year-on-year chart | 2024 vs 2025 hours lost (Chart.js bar chart) |
| Peak-hour chart | Toggle between standard weekday and Ramadan 2026 congestion patterns |
| Hotspot corridors | Toggle Dubai / Abu Dhabi, styled as highway exit signs |
| RTA 2026 plan | Progress bars for the government's 45-initiative, 8-site intervention plan |
| Salik toll pricing | Peak vs off-peak toll comparison |

All figures are sourced from public reporting current to August 2026 (full source
list in the dashboard footer and below). The hour-by-hour congestion curve is
explicitly labeled **illustrative** — it's built from reported peak windows, not a
live traffic feed, and the dashboard says so rather than implying more precision
than the data supports.

## Tech stack

- Plain HTML/CSS/JS — no build step, no framework, one file
- [Chart.js 4.5.0](https://www.chartjs.org/) via cdnjs for the bar/line charts
- Google Fonts: Oswald (display), IBM Plex Sans (body), IBM Plex Mono (data/labels)
- Design direction: dark "asphalt" background with amber/cyan signal colors and a
  dot-matrix gantry-sign motif for key numbers — chosen to be visually specific to
  the subject (highway signage, Salik toll gantries) rather than a generic
  dashboard template

## A bug that came up, and the fix

The first version shipped with every stat and chart missing. Root cause: the
`<script>` tag pointed at Chart.js version `4.4.4` on cdnjs —

```html
<!-- broken: this version was never published to cdnjs -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.4/chart.umd.min.js"></script>
```

That 404'd, so `Chart` was undefined. The first `new Chart(...)` call threw, which
halted the rest of the inline `<script>` block — including the hotspot-card
rendering and the toggle-button event listeners further down the same script.
One dead CDN link took out charts, stats formatting, and interactivity together.

Fix: point at a version that's actually hosted on cdnjs.

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.5.0/chart.umd.min.js"></script>
```

**Lesson for anyone reusing this file:** if you change the Chart.js version, verify
the exact path exists at `https://cdnjs.com/libraries/Chart.js` first — a silently
failed CDN script can take out unrelated JS later in the same file, not just the
charts.

## Running locally

No install needed — it's a static file.

```bash
git clone https://github.com/<your-username>/uae-traffic-dashboard.git
cd uae-traffic-dashboard
open index.html          # macOS
# or just double-click index.html
```

## Deploying

**GitHub Pages (recommended, free):**
1. Push this repo to GitHub (see commands below)
2. Repo → Settings → Pages → Source: `Deploy from a branch` → Branch: `main` → `/ (root)`
3. Your dashboard goes live at `https://<your-username>.github.io/uae-traffic-dashboard/`

## Pushing this to GitHub

```bash
cd uae-traffic-dashboard
git init
git add .
git commit -m "Initial commit: UAE traffic congestion dashboard"
git branch -M main
git remote add origin https://github.com/<your-username>/uae-traffic-dashboard.git
git push -u origin main
```

(Create the empty repo first at github.com/new, then run the commands above.)

## Data sources

- [Khaleej Times — Traffic redefines where residents live](https://www.khaleejtimes.com/uae/uae-property-trends-traffic-redefines-where-residents-live) (May 2026)
- [Gulf Business — RTA 45 traffic upgrades](https://gulfbusiness.com/en/2026/infrastructure/dubai-rta-45-traffic-upgrades-commutes-change/) (2026)
- [Emirates 24|7 — 5 new RTA road projects](https://www.emirates247.com/uae-guide/dubai-traffic-2026-5-new-rta-road-projects-slash-travel-times-across-the-city/4038) (2026)
- [Gulf News — Ramadan 2026 traffic guide](https://gulfnews.com/uae/transport/ramadan-2026-uae-traffic-guide-peak-hours-key-roads-and-how-to-beat-the-congestion-1.500446898)
- [Gulf News — Rush-hour gridlock hotspots](https://gulfnews.com/uae/transport/uae-traffic-alert-rush-hour-gridlock-hits-key-routes-in-dubai-and-abu-dhabi-1.500317917)
- [Pitstop Arabia — How the UAE plans to tackle congestion](https://www.pitstoparabia.com/en/news/uae-traffic-congestion-solutions)

## Roadmap / next steps

- [ ] Swap the illustrative peak-hour curve for a live source (TomTom Traffic Index
      API or Google Maps Traffic API)
- [ ] Connect the hotspot list to RTA's real-time monitoring feed
- [ ] Add a map view (Mapbox/Leaflet) plotting hotspot corridors geographically
- [ ] Historical trend beyond 2024–2025 once more years of Inrix data are public

## License

MIT — reuse and adapt freely.
