# Nashville Housing Pressure Map

An interactive map of short-term rental density against rent burden by census tract in Davidson County — built entirely on live public data, no backend.

## What it does

- Pulls every active Residential Short-Term Rental permit from Metro Nashville's live open data feed and renders it as both a density heatmap and individual points
- Overlays a rent-burden choropleth by census tract (median gross rent as % of household income) from Census ACS 5-year estimates
- Joins the two datasets on census tract, so you can see where STR concentration and housing cost burden overlap — a live view into Nashville's short-term rental / housing supply debate
- Popups on both layers surface the underlying numbers (permit details, median rent, median income) rather than just a color

## Why

Nashville's STR permitting fight is a real, ongoing policy debate — bachelorette-party tourism and STR supply on one side, housing affordability and neighborhood displacement pressure on the other. This turns that debate into something you can actually look at, tract by tract, instead of an argument.

<img width="1432" height="668" alt="Screenshot 2026-08-12 at 2 13 42 PM" src="https://github.com/user-attachments/assets/6babf24b-ca37-4c65-8c1e-dbd5710a7fdb" />

## How it works

Single HTML file, zero build tooling, runs entirely client-side:

- **STR permits & tract boundaries** — queried live from Metro Nashville's and the Census Bureau's public ArcGIS Feature Services (paginated automatically, no API key required)
- **Rent burden data** — Census ACS 5-year estimates via the Census Data API (free key required — see Setup)
- **Map** — Leaflet + Leaflet.heat for the density layer, CARTO dark basemap

**Tools:** Leaflet.js, Metro Nashville Open Data (ArcGIS Feature Services), Census ACS API, vanilla JS

## Setup

1. Get a free Census API key: [api.census.gov/data/key_signup.html](https://api.census.gov/data/key_signup.html) (instant, no cost)
2. Open `index.html`, set `CONFIG.CENSUS_API_KEY` near the top of the script
3. Open in a browser, or host as a static site (GitHub Pages works out of the box)

Without a key, the STR heatmap and points still load — only the rent-burden choropleth is skipped, with an on-screen note telling you why.

## Notes

Nashville's permit data is a live production feed and updates continuously — permit counts shown will drift slightly run to run, which is expected, not a bug.
