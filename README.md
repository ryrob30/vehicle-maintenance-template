# Vehicle Maintenance AI Agent — Setup Guide

How to stand up this project for your own vehicle(s). Full agent behavior lives in `AGENTS.md` — this file is just the human setup steps.

> **This is a template.** It ships with two sample vehicles (`sample_sedan`, `sample_truck`) containing entirely **dummy data** — fake VINs, placeholder mileage, made-up log entries — so you can see the structure and format in use. Delete or replace them with your own vehicle(s) following the steps below.

## 1. Folder structure

```
your-project/
├── AGENTS.md            # agent instructions (copy from this repo, edit vehicle list)
├── vehicles/             # one profile per vehicle: specs, mileage, fluids, quirks
├── maintenance-log/       # one running log per vehicle: completed work only
├── manuals/               # owner's/service manual PDFs, one subfolder per vehicle
├── reference/              # TSBs, wiring diagrams, door-tag photos, VIN decode exports
├── obd-exports/            # OBD-II scanner data drops here when you have it (can start empty)
├── sources/                # agent-maintained catalog: what source backs each answer
├── intake/                 # drop new files here unfiled; agent renames/sorts them
└── templates/              # blank vehicle-profile and maintenance-log templates
```

Create one subfolder per vehicle under `manuals/` and `reference/`, named consistently (e.g. `sample_sedan`).

**`intake/` workflow (recommended):** rather than naming/filing every new asset yourself, drop it into `intake/` as-is (a phone photo, a downloaded PDF, a pasted CSV) and ask the agent to file it. The agent identifies the vehicle, renames it to match this project's conventions, moves it to the right `manuals/`/`reference/` subfolder, and adds a `sources/` entry. Nothing should stay in `intake/` long-term — it's a landing zone, not storage.

## 2. Per-vehicle setup steps

1. **Collect the door tag / VIN plate photo.** Driver's door jamb sticker (or glovebox/frame on some trucks). Drop it in `intake/` and ask the agent to file it (or save directly to `reference/<vehicle>/<Make>-<Model>-<Year>-Door-Jamb-Label.jpg`). Gives GVWR/GAWR, tire pressures, paint/trim codes, build date.
2. **Decode the VIN via NHTSA.** Free, official, no login. Two options — pick whichever is convenient:
   - **Browser:** go to **https://vpic.nhtsa.dot.gov/decoder/**, enter the VIN, confirm model year, export the result as CSV — drop it in `intake/` for the agent to file, or save directly to `reference/<vehicle>/NHTSA-VIN-Decode.csv`.
   - **Have the agent pull it via API:** ask the agent to fetch `https://vpic.nhtsa.dot.gov/api/vehicles/DecodeVinValuesExtended/<VIN>?format=json` and save the result to `reference/<vehicle>/NHTSA-VIN-Decode.csv` (or `.json`). Same NHTSA data either way — no API key required.
3. **Get the owner's manual PDF** (and service manual if available). Drop it in `intake/` for the agent to file, or save directly to `manuals/<vehicle>/`.
4. **Copy the blank templates** from `templates/` into `vehicles/<vehicle>.md` and `maintenance-log/<vehicle>.md`; fill in from the VIN decode + door tag + what you know. (`vehicles/sample_sedan.md` and `sample_truck.md` are filled-in dummy *examples* of the finished result, not blank forms — delete them once you've added your own vehicles.)
5. **Ask the agent to add a `sources/<vehicle>.md` entry** for each source above (what it is, where it lives, publisher, date). This file is agent-maintained — you generally won't write it by hand, just confirm/correct what the agent records.
6. Repeat for each additional vehicle; update the vehicle table in `AGENTS.md`.

## 3. Suggested starter assets per vehicle

| Asset | Where | Why |
|---|---|---|
| Door jamb / VIN plate photo | `reference/<vehicle>/` | Confirms GVWR, tire specs, build date without re-measuring |
| NHTSA VIN decode (CSV or saved page) | `reference/<vehicle>/` | Authoritative engine/trim/drivetrain confirmation — browse at https://vpic.nhtsa.dot.gov/decoder/ or ask the agent to pull it via the API at `https://vpic.nhtsa.dot.gov/api/vehicles/DecodeVinValuesExtended/<VIN>?format=json` |
| Owner's manual PDF | `manuals/<vehicle>/` | Maintenance intervals, fluid capacities, torque specs |
| Service/factory manual PDF (if available) | `manuals/<vehicle>/` | Deeper procedures beyond the owner's manual |
| Any known TSBs or recall notices | `reference/<vehicle>/` | Check https://www.nhtsa.gov/recalls by VIN |
| Current maintenance records (receipts, prior shop invoices) | `maintenance-log/<vehicle>.md` | Seeds known history so projections aren't guessing |

## 4. First run

Ask the agent something like *"what's my `<vehicle>` due for soon?"* — it will tell you if it needs a current odometer reading first. Correct anything it gets wrong in `vehicles/<vehicle>.md` directly; markdown is cheap to edit.
