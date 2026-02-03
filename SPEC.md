# Cycling Log Specification

Version: v1.3  
Status: Source of Truth

---

## Purpose

This document defines the canonical rules, schemas, and conventions for the cycling log repository.

It exists to prevent ambiguity, drift, and loss of intent over time.

If something is unclear in ride entries, scripts, or summaries, **this file wins**.

---

## Repository Structure

```
/bikes/
  {bike_id}.md

/rides/
  YYYY/
    YYYY-MM-DD.md

/summaries/
  YYYY/
    week-XX.md
    YYYY-MM.md

/events/
  YYYY-<event-name>.md

SPEC.md
```

---

## Core Principles

- One ride entry per calendar day
- One bike per day
- Bikes are referenced by ID, never duplicated
- Specs change slowly, rides change daily
- History must be explicit
- Text is the primary source of truth
- This repository is both human-readable and machine-friendly
- Context (weather, intent, fitness) explains numbers

---

## Ride Entry Schema  
`/rides/YYYY/YYYY-MM-DD.md`

```md
# YYYY-MM-DD

## Stats
- Distance: <km>
- Elevation: <m>
- Bike: <bike_id>

## Heart Rate
- Avg: <bpm | unknown>
- Max: <bpm | unknown>

## Fitness
- CTL: <value | unknown>
- ATL: <value | unknown>
- Form: <value | unknown>
- Ramp rate: <value | unknown>
- Source: intervals.icu

## Weather
- Condition: Dry | Rain | Mixed
- Road: Dry | Wet
- Notes: <optional>

## Bike State
- Tires: <OK | note>
- Brakes: <OK | note>
- Drivetrain: <OK | note>
- Chain: <OK | note>
- Notes: <optional>

## Intent
<why the ride happened>

## Effort
Very easy | Easy | Steady | Hard

## Links
- Strava: <url | none>
- Intervals.icu: <url | none>
- Instagram: <url | none>

## Notes
<optional>
```

### Ride Rules

- Exactly one ride file per calendar date
- Multiple activities in a day MUST be aggregated
- Bike field is required
- Ride entries MUST NOT contain bike specifications
- Fitness values are snapshots, not targets
- Weather must stay simple and descriptive

---

## Bike File Schema  
`/bikes/{bike_id}.md`

```md
# <Bike Display Name>

id: <bike_id>

## Frame
## Drivetrain
## Wheels & Tires
## Brakes
## Notes
```

### Bike Rules

- `bike_id` must be lowercase kebab-case
- `bike_id` is immutable once created
- Specs live only in bike files
- Bike state lives only in ride entries

---

## Weekly Summary Schema  
`/summaries/YYYY/week-XX.md`

```md
# Weekly Summary — Week XX (YYYY-MM-DD → YYYY-MM-DD)

## Overview
- Days ridden
- Primary bike
- Theme of the week

## Totals
- Total distance
- Total elevation

## Effort Distribution
- Easy / Steady / Hard days

## Fitness Trend
- CTL: ↑ / → / ↓
- Form: Mostly positive / neutral / negative
- Notes

## Weather Impact
- Dry vs wet days
- Effect on volume or effort

## Bike State & Maintenance
- Notable component changes
- Wear observations

## Reflection
Short narrative summary.
```

---

## Monthly Summary Schema  
`/summaries/YYYY/YYYY-MM.md`

```md
# Monthly Summary — YYYY-MM

## Overview
- Days ridden
- Primary bike
- Monthly theme

## Volume
- Total distance
- Total elevation

## Fitness & Load
- CTL trend
- Ramp behavior
- Fatigue management notes

## Conditions
- Weather patterns
- Environmental constraints

## Equipment
- Component changes
- Mileage milestones

## Reflection
What this month established or changed.
```

---

## Event Summary Schema  
`/events/YYYY-<event-name>.md`

Events are optional narrative artifacts that connect multiple daily rides.

Rules:
- Events never replace daily ride logs
- No raw metrics introduced
- Purpose is context and memory

---

## Change History

### v1.3
- Added Fitness section to ride entries
- Added Weather section with low-noise rules
- Added Monthly summary schema
- Formalized Events directory

### v1.2
- Added weekly summaries
- Defined aggregation rules
- Clarified bike reference convention

### v1.1
- Added Bike reference convention
- Separated bike spec from bike state

### v1.0
- Initial specification
