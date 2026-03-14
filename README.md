# ✦ AguirreTech — Drone Mission Checklist

A progressive web app that guides drone students through every phase of a mission — from airspace verification to post-flight logging — built for Part 107 and TRUST recreational flight training programs.

**Live app:** [https://aguirretech.github.io/drone-checklist/](https://aguirretech.github.io/drone-checklist/)

---

## What It Does

A single-file PWA that structures a complete drone mission into a guided before/after workflow. Students fill out the mission form, work through a phase-based checklist, print a pre-flight briefing, fly, then return to complete the post-flight record and log the mission.

### Checklist Phases

**Before Flight**
- 📋 **Mission Setup** — Form completion, weather fetch, airspace verification, LAANC confirmation
- 🦺 **Crew & Equipment** — PPE, battery levels, controller link, props inspection, GPS lock
- ✅ **Pre-Flight Acknowledgments** — RPIC gate + pilot/crew commitments (VLOS, airspace, battery monitoring, VO briefing)
- 🚀 **Ready to Launch** — Launch zone, bystander clearance, RTH altitude, announce launch, start timer

**After Flight**
- 🛬 **Post-Flight** — Power down, equipment inspection, battery check, media secured, site cleanup
  - 📋 **Flight Record** — Incident reporting, mission notes, end timer, altitude, log mission, reprint briefing

### Mission Info Form
Captures 25+ fields per flight across 5 grouped sections:

| Group | Fields |
|---|---|
| 👤 Who | Pilot Name, Class Level, Visual Observer(s), VO Part 107 Certified |
| 📍 When & Where | Date, Time, Flight Type, Location (GPS + autocomplete) |
| 🚁 Aircraft | Drone Fleet Roster, Drone Model, FAA Reg. #, Remote ID Broadcasting |
| 🌤 Conditions & Airspace | Weather, Wind Speed, KP Index, Airspace Class, Airspace Authorization, LAANC Confirmation, Mission Description |
| ⏱ Flight Record | Mission Insurance, Flight Start/End/Duration, Max Altitude, Incident/Anomaly, Mission Notes |

### Pre-Flight Briefing
A printable mission briefing sheet generated from the form. Students print it before launch and reprint it after landing with the completed flight record.

### Mission Log
All logged missions are stored locally and can be searched, sorted, exported to Excel, and optionally synced to Google Sheets.

---

## Features

| Feature | Details |
|---|---|
| Guided Workflow | Phase-based checklist separates before-flight and after-flight tasks with a clear ▶ Start / ■ Stop timer flow |
| Pre-Flight Briefing | Printable briefing sheet — blank flight record pre-flight, auto-filled on return |
| Live Weather | Auto-fills weather + wind via Open-Meteo (no API key required) |
| Wind Safety Indicator | Color-coded go / caution / no-fly based on Part 107 wind thresholds |
| KP Index | Live geomagnetic data from NOAA — flags conditions that may affect GPS |
| FAA Airspace Auto-Detection | Detects airspace class and LAANC authorization ceiling from GPS location |
| LAANC Integration | Shows max authorized altitude; flags DroneZone-required locations |
| GPS Location | Auto-detects via browser geolocation + OpenStreetMap reverse geocoding |
| Drone Fleet Roster | Save and reuse drone/registration pairs across missions |
| Pilot Profile Persistence | Pilot name and class level saved across sessions |
| Mission Insurance | Toggle-on insurance details for commercial or high-risk missions |
| Auto-Save Draft | Form state saves automatically every 800ms; restores on next visit |
| Mission Log | Searchable, sortable log with per-entry Excel export |
| Excel Export | Single mission or full log export as .xlsx |
| Google Sheets Sync | Optional sync via Google Apps Script Web App |
| Accessibility | High contrast, font scaling, reduced motion, full keyboard nav, screen reader support |
| Mobile / PWA | Installable on iOS and Android; swipe tabs, 44px touch targets, offline capable |
| Keyboard Shortcuts | Ctrl+L (Log), Ctrl+R (Reset), Ctrl+1/2 (Switch tabs) |
| Print / PDF | Clean print layout with AguirreTech branding and mission date |
| No Backend | Fully static — works on GitHub Pages with no server or API keys required |

---

## Student Workflow

1. **Fill in Mission Info** — Pilot, aircraft, location, date, and flight type
2. **Fetch weather and airspace** — Use the 🌤 Fetch and ⚡ Live buttons; airspace auto-fills from GPS
3. **Work through Before-Flight checklist** — Setup → Crew & Equipment → Acknowledgments → Ready to Launch
4. **Acknowledge the RPIC gate** — Unlocks pre-flight commitment items
5. **Click ▶ Start** — Stamps flight start time and opens the pre-flight briefing for printing
6. **Fly**
7. **Return — click ■ Stop** — Stamps end time and calculates duration
8. **Complete Post-Flight checklist** — Wrap-up → Flight Record (incident, notes, altitude)
9. **Press ✦ Log This Mission** — Saves to mission history
10. **Reprint the briefing** — Now shows the complete post-flight record

---

## Deployment

This app is a **single `index.html` file** plus 4 supporting PWA files. All 5 files must be in the same GitHub repo root:

```
index.html
manifest.json
sw.js
icon-192.png
icon-512.png
apple-touch-icon.png
```

To update to a new version:

1. Download the new `index.html` from your build
2. Go to your GitHub repo → **Add file → Upload files**
3. Drag in the new file — GitHub replaces the old one automatically
4. Commit with a version note (e.g. `Update to v61`)
5. GitHub Pages redeploys in ~60 seconds

---

## External Services Used

All free, no API keys required:

| Service | Purpose |
|---|---|
| [Open-Meteo](https://open-meteo.com) | Live weather and wind data |
| [OpenStreetMap Nominatim](https://nominatim.openstreetmap.org) | Address autocomplete + reverse geocoding |
| [NOAA SWPC](https://www.swpc.noaa.gov) | KP planetary geomagnetic index |
| [FAA UAS Facility Map](https://faa.gov/uas) | Airspace class and LAANC ceiling auto-detection |
| [FAA DroneZone](https://faadronezone.faa.gov) | Linked for manual authorization when LAANC ceiling = 0 |
| [SheetJS (cdnjs)](https://sheetjs.com) | Excel (.xlsx) file generation |
| [Google Fonts](https://fonts.google.com) | Rajdhani, Share Tech Mono, Exo 2 |

---

## Data & Privacy

- All mission data is stored in your **browser's localStorage** — nothing leaves your device unless you use the Google Sheets sync feature
- No accounts, no tracking, no server
- Clearing browser data will erase the mission log — use **Export All** regularly to back up
- PWA icons and manifest enable home screen installation on iOS and Android

---

## Google Sheets Integration (Optional)

To sync missions to a Google Sheet:

1. Create a new Google Sheet
2. Go to **Extensions → Apps Script** and paste the provided script (available inside the app under ⬆ Google Sheets)
3. Click **Deploy → New deployment → Web App**
4. Set access to **Anyone**
5. Copy the Web App URL and paste it into the app's Google Sheets modal

---

## About

Built by **AguirreTech** for drone education programs serving youth, veterans, and community learners.

> *"Where Safety, Service, and Integrity Take Flight."*

**Program contact:** [Ramon@AguirreTech.com](mailto:Ramon@AguirreTech.com)
**Website:** [aguirretech.com](https://aguirretech.com)

---

*Built with AI assistance. Current build: v61.*
