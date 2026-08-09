# Gridlock Watch — UAE Traffic Congestion Dashboard

An interactive dashboard exploring one of the UAE's most visible and fast-growing urban challenges: **road traffic congestion**.

[**View Live Dashboard →**](https://jamila-hanif.github.io/uae-traffic-dashboard/)

---

## 🚦 The Problem

Traffic congestion is becoming an increasingly significant challenge across the UAE, particularly in Dubai.

Dubai motorists lost **45 hours to traffic in 2025**, compared with 35 hours in 2024 — an increase of approximately **29% in one year**, according to figures reported from the INRIX Global Traffic Scorecard.

The average time required to travel **10 km reached approximately 19.1 minutes** in 2025.

Beyond longer journeys, congestion can influence commuting patterns, residential choices and pressure on the road network as travel demand grows.

Traffic congestion was selected for this project over other candidate issues such as housing affordability and healthcare access because it offered:

* A clear year-over-year worsening trend
* Strong availability of public reporting and transport data
* Measurable effects that can be communicated visually
* An active government response through RTA traffic-improvement programmes

---

## 📊 What the Dashboard Shows

| **Section**        | **What it visualizes**                                                                   |
| ------------------ | ---------------------------------------------------------------------------------------- |
| Hero statistic     | Annual hours lost to congestion, styled as a highway gantry sign                         |
| Metric strip       | 10 km journey time, RTA upgrade locations, planned initiatives and capacity improvements |
| Year-on-year trend | Comparison of congestion hours in 2024 and 2025                                          |
| Journey-time chart | Comparison of average time required to travel 10 km                                      |
| Peak-hour chart    | Toggle between standard weekday and Ramadan 2026 congestion patterns                     |
| Hotspot corridors  | Toggle between major Dubai and Abu Dhabi traffic corridors                               |
| RTA response       | Overview of the government's 2026 rapid traffic-improvement programme                    |
| Salik pricing      | Peak and off-peak Ramadan 2026 toll pricing                                              |

---

## 🧭 Data & Methodology

The dashboard uses publicly reported figures available at the time of development.

Where reported numerical data is available, the dashboard displays those figures directly.

The **hour-by-hour congestion curves are illustrative**. They are constructed from publicly reported peak travel windows rather than a live traffic API.

Similarly, the hotspot section identifies major corridors discussed in public traffic reporting; it should **not be interpreted as a real-time traffic map**.

This distinction is intentional: the dashboard aims to communicate the scale and pattern of congestion without implying a level of real-time precision that the underlying data cannot support.

---

## 🛠 Tech Stack

* **HTML5**
* **CSS3**
* **Vanilla JavaScript**
* **Chart.js 4.5.0** for interactive charts
* **Google Fonts**

  * Oswald — display typography
  * IBM Plex Sans — body text
  * IBM Plex Mono — statistics and labels
* **GitHub Pages** for deployment

The project requires **no framework, package manager or build step**. The complete interactive dashboard runs from a single `index.html` file.

---

## 🎨 Design Direction

The interface takes inspiration from UAE road infrastructure rather than using a generic analytics-dashboard aesthetic.

The visual system combines:

* Dark asphalt-inspired backgrounds
* Amber traffic-warning accents
* Cyan information signals
* Highway exit-sign styling
* Gantry-style statistics
* Monospaced transport/data labels

The goal is to make the subject of the dashboard immediately recognizable while keeping the information easy to scan.

---

## 🐛 Technical Note: Chart.js CDN Issue

During development, an incorrect Chart.js CDN version caused the dashboard's JavaScript to stop executing.

The broken reference was:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.4.4/chart.umd.min.js"></script>
```

Because that resource failed to load, `Chart` was undefined. The first chart initialization then threw an error and prevented later JavaScript — including hotspot rendering and toggle interactions — from executing.

The working reference is:

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/Chart.js/4.5.0/chart.umd.min.js"></script>
```

**Key lesson:** external CDN dependencies should be verified before deployment because a failed dependency can affect functionality beyond the component that directly uses it.

---

## 💻 Running Locally

Clone the repository:

```bash
git clone https://github.com/Jamila-Hanif/uae-traffic-dashboard.git
cd uae-traffic-dashboard
```

On macOS:

```bash
open index.html
```

Alternatively, open `index.html` directly in any modern browser.

No installation is required.

---

## 🌐 Live Deployment

The dashboard is deployed using **GitHub Pages**.

[**Open Gridlock Watch →**](https://jamila-hanif.github.io/uae-traffic-dashboard/)

Repository:

https://github.com/Jamila-Hanif/uae-traffic-dashboard

---

## 📚 Data Sources

The project draws on public reporting and transport information including:

* **INRIX Global Traffic Scorecard** — annual congestion and hours-lost data
* **TomTom traffic reporting** — journey-time indicators
* **Dubai Roads and Transport Authority (RTA)** — traffic-improvement programmes
* **Dubai Media Office** — RTA infrastructure and rapid traffic-solution announcements
* **Khaleej Times** — UAE congestion and commuting reporting
* **Gulf News** — Ramadan traffic patterns and Salik pricing
* **Gulf Business** — RTA traffic-upgrade reporting
* **Emirates 24|7** — Dubai road-project reporting

Detailed source links are included within the dashboard.

---

## 🚀 Roadmap

Future improvements could include:

* Connect a licensed **live traffic API** to replace the illustrative peak-hour curve
* Integrate publicly available **RTA real-time traffic information**
* Add an interactive geographic map using **Leaflet or Mapbox**
* Plot congestion hotspots geographically
* Expand the historical trend beyond 2024–2025
* Add commuter-impact indicators such as estimated time cost, fuel consumption and emissions
* Add responsive filtering for individual roads and time periods

---

## ⚠️ Disclaimer

Gridlock Watch is an **awareness and data-visualization project**, not a navigation or official traffic-information service.

Illustrative visualizations are explicitly identified and should not be interpreted as real-time traffic conditions.

For current road conditions, users should rely on official transport authorities and real-time navigation services.

---

## 📄 License

This project is licensed under the **MIT License**.

Reuse and adaptation are welcome with appropriate attribution.

