# Mussel Rock Weather Dashboard

A single-page weather dashboard for paraglider and hang glider pilots flying at **Mussel Rock**, Daly City, CA (37.6137°N, 122.4857°W) — one of the premier coastal soaring sites in the San Francisco Bay Area.

Live site: https://zjusbo.github.io/mussel-rock-weather-dashboard/

---

## Features

### Wind Forecast
- **GFS Seamless model** via [Open-Meteo](https://open-meteo.com/) — blends HRRR (3 km resolution, first ~48 h) and GFS Global (0.25°, 7 days)
- Wind speed, wind gust, and wind direction on a single merged chart
- **Flyable conditions** highlighted in green: speed 9–14 mph, direction W / WNW / WSW, precipitation probability < 40%, during daylight hours
- **Day/night shading** — bright background for daylight, dark for night, with soft gradient transitions at sunrise/sunset
- Wind direction arrows showing downwind direction at each time step

### Tide Forecast
- Hourly tide height predictions from **NOAA CO-OPS** station #9414290 (San Francisco)
- Height in feet MLLW

### Precipitation
- Hourly precipitation probability from GFS Seamless

### UI / Interaction
- **48-hour / 7-day toggle** — switches all panels simultaneously; data is cached so toggling never triggers a second API call
- **Synchronized crosshair** — hover over any panel to see a vertical time marker on all panels, snapped to 30-minute intervals
- Current conditions summary cards (wind speed, direction, gust, tide height, precip probability)
- Interactive compass rose showing current wind direction
- Auto-refresh every 15 minutes

---

## Data Sources

| Data | Provider | Endpoint |
|------|----------|----------|
| Wind & precipitation forecast | [Open-Meteo GFS API](https://open-meteo.com/en/docs/gfs-api) | `/v1/gfs?models=gfs_seamless` |
| Tide predictions | [NOAA CO-OPS](https://tidesandcurrents.noaa.gov/) | Station 9414290, datum MLLW |
| Sunrise / sunset | [SunCalc](https://github.com/mourner/suncalc) | Client-side calculation |

---

## Flyable Conditions

Mussel Rock is a west-facing coastal bluff. Good flying conditions require:

- **Wind speed:** 9 – 14 mph
- **Wind direction:** W, WNW, or WSW (236° – 304°)
- **Precipitation probability:** < 40%
- **Time:** after sunrise, at least 1 hour before sunset

The dashboard highlights these windows in green across all chart panels.

---

## Technology

- Pure HTML + JavaScript — single `index.html`, no build step required
- [Chart.js 4.4](https://www.chartjs.org/) for charting with custom canvas plugins
- [SunCalc 1.9](https://github.com/mourner/suncalc) for DST-aware sunrise/sunset
- Open-Meteo and NOAA APIs (both free, no API key required)

---

## Running Locally

Just open `index.html` in any modern browser — no server or dependencies needed.

```bash
open index.html
```
