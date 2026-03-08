# Spaceports 2025 — Interactive Launch Atlas

An interactive web map of global spaceport launch sites, originally built as a client project in QGIS and converted into a fully interactive web application. The atlas covers every active launch site in 2025 — launch pads, mission histories, trajectories, and statistics — all driven from a single CSV file.

**Live demo:** [gegz-geom.github.io/spaceports2025](https://gegz-geom.github.io/spaceports2025)

---

## Features

- **Mission history** — click any launch pad to view its full log: payloads, vehicles, dates, orbit altitudes, and remarks
- **Live azimuth tracing** — click any mission and its launch trajectory is drawn as a great-circle arc stretching 5,000+ km across the map
- **Basemap switching** — Dark, Light (CartoDB), and Satellite (ArcGIS)
- **Filters** — by country, launch vehicle, mission status, and category (Commercial / Government)
- **Marker clustering** — nearby pads are grouped at lower zoom levels and expand on zoom
- **Azimuth compass** — per-site compass rose showing the distribution of launch directions
- **Mobile responsive** — full bottom sheet navigation, works on any device
- **CSV upload** — load your own data on arrival, or explore with the built-in demo dataset

---

## Getting Started

No installation or build step required. The entire app is a single HTML file.

### Run locally

```bash
git clone https://github.com/your-username/spaceports-2025.git
cd spaceports-2025
# Open index.html in your browser
open index.html
```

### Deploy on GitHub Pages

The project is deployment-ready as-is. To enable GitHub Pages:

1. Push this repository to GitHub
2. Go to your repo → Settings → Pages
3. Under "Source", select your branch (usually `main`) and set folder to `/ (root)`
4. Save — your site will be live at `https://gegz-geom.github.io/your-repo-name`

---

## CSV Format

When you load your own data, the CSV should include the following columns:

| Column | Description |
|---|---|
| `Site` | Launch pad identifier (e.g. `CCK LC-39A`) |
| `LATITUDE` | Decimal latitude |
| `LONGITUDE` | Decimal longitude |
| `COUNTRY` | Country name |
| `CATEGORY` | `COMMERCIAL` or `GOVERNMENT` |
| `STATUS` | `FAILED` or `PLANNED` — blank fields are treated as `SUCCESSFUL` |
| `Date` | Launch date (YYYY-MM-DD) |
| `Payload(s)` | Payload name |
| `Launch Vehicle` | Vehicle name |
| `AZIMUTH_DEG` | Launch azimuth in decimal degrees |
| `SAT_ALT_KM` | Satellite orbit altitude in km (optional) |
| `Remark` | Mission note (optional) |

---

## Tech Stack

| Library | Role |
|---|---|
| [Leaflet.js](https://leafletjs.com) | Core map rendering — tiles, markers, polylines, popups |
| [Leaflet MarkerCluster](https://github.com/Leaflet/Leaflet.markercluster) | Groups nearby launch pads into numbered clusters |
| [PapaParse](https://www.papaparse.com) | Parses CSV data directly in the browser |
| [CartoDB Positron](https://carto.com/basemaps) | Light basemap tile source |
| [ArcGIS World Imagery](https://www.arcgis.com) | Satellite basemap tile source |
| Vanilla JS / HTML / CSS | No frameworks — single portable file |

---

## Project Structure

```
spaceports-2025/
├── index.html        # The entire application
├── favicon.svg       # Site icon
├── README.md         # This file
├── .gitignore        # Standard web gitignore
└── netlify.toml      # Netlify deployment config
```

---

## License

MIT — free to use, modify, and deploy.
