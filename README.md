# 🌐 SeismoWatch — Live Earthquake Tracker

A frontend-only, single-file web application that displays real-time earthquake data from the USGS Earthquake Hazards Program. No build tools, no backend, no dependencies to install — just open `index.html` and go.

**[Live Demo →](https://your-username.github.io/seismowatch)** *(update after deploying)*

---

## Features

- **Live USGS data** — fetches from the [USGS All Earthquakes (Past Hour)](https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/all_hour.geojson) GeoJSON feed
- **Auto-refresh** every 60 seconds with an animated countdown ring
- **Interactive Leaflet map** with magnitude-scaled markers; click any marker to pan and pop up details
- **Synchronized list & map** — selecting a list item flies the map to that location, and vice versa
- **Color-coded severity** — green (< 5.0), orange (5.0–6.9), red (≥ 7.0)
- **Filter by minimum magnitude** — All, ≥ 1.0, ≥ 2.5, ≥ 4.5, ≥ 6.0
- **Sort** by magnitude (ascending/descending) or time (newest/oldest first)
- **Live stats bar** — total shown, maximum magnitude, count of significant quakes (≥ 5.0)
- **Loading indicator**, graceful error banner, and empty state for filtered results
- **Fully responsive** — works on desktop, tablet, and mobile

---

## Getting Started

### Run Locally

No server required. Just open the file in any modern browser:

```bash
# Clone the repo
git clone https://github.com/your-username/seismowatch.git
cd seismowatch

# Open directly
open index.html        # macOS
start index.html       # Windows
xdg-open index.html    # Linux
```

> **Note:** Some browsers block `fetch()` requests from `file://` URLs due to CORS policy. If the data doesn't load, serve it locally instead:
>
> ```bash
> # Python 3
> python -m http.server 8080
> # then visit http://localhost:8080
> ```

### Deploy to GitHub Pages

1. Push `index.html` (and this `README.md`) to a GitHub repository
2. Go to **Settings → Pages**
3. Under **Source**, select `main` branch and `/ (root)`
4. Click **Save** — your site will be live at `https://your-username.github.io/repo-name`

---

## Project Structure

```
seismowatch/
├── index.html   # Entire application — HTML, CSS, and JS in one file
└── README.md
```

Everything is self-contained in `index.html`:

| Section | Description |
|---|---|
| `<style>` | All CSS — design tokens, layout, components, responsive rules |
| `<body>` | Semantic HTML — header, controls, sidebar list, Leaflet map container |
| `<script>` | All JavaScript — fetch, render, map, countdown, event handling |

---

## External Dependencies (CDN only)

| Library | Version | Purpose |
|---|---|---|
| [Leaflet.js](https://leafletjs.com/) | 1.9.4 | Interactive map |
| [OpenStreetMap](https://www.openstreetmap.org/) | — | Map tiles |
| [Syne](https://fonts.google.com/specimen/Syne) | — | Display font |
| [DM Mono](https://fonts.google.com/specimen/DM+Mono) | — | Monospace body font |

No npm, no bundlers, no build step.

---

## Data Source

All seismic data is provided by the **U.S. Geological Survey (USGS)** Earthquake Hazards Program, updated in real time.

- **Feed URL:** `https://earthquake.usgs.gov/earthquakes/feed/v1.0/summary/all_hour.geojson`
- **Coverage:** All earthquakes recorded globally in the past hour
- **Format:** GeoJSON (magnitude, location, depth, time, etc.)
- **Terms:** [USGS Data Policy](https://www.usgs.gov/information-policies-and-instructions/copyrights-and-credits)

---

## Magnitude Scale Reference

| Color | Range | Severity |
|---|---|---|
| 🟢 Green | < 5.0 | Minor / Light |
| 🟠 Orange | 5.0 – 6.9 | Moderate / Strong |
| 🔴 Red | ≥ 7.0 | Major / Great |

---

## Browser Support

Works in all modern browsers (Chrome, Firefox, Safari, Edge). Requires JavaScript enabled and network access to the USGS API and CDN resources.

---

## License

MIT — free to use, modify, and deploy.
