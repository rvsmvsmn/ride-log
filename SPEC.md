# Cycling Log Specification

Version: v1.2  
Status: Source of Truth

---

## Purpose

This document defines the canonical rules, schemas, and conventions for the cycling log repository.

It exists to prevent ambiguity, drift, and loss of intent over time.

If something is unclear in ride entries, scripts, or summaries, **this file wins**.

---

## Repository Structure

/bikes/
  {bike_id}.md

/rides/
  YYYY/
    YYYY-MM-DD.md

/summaries/
  YYYY/
    week-XX.md

SPEC.md

---

## Core Principles

- One ride entry per day
- One bike per day
- Bikes are referenced by ID, never duplicated
- Specs change slowly, rides change daily
- History must be explicit
- Text is the primary source of truth
- This repository is both human-readable and machine-friendly

---

## Schema

### Ride Entry (/rides/YYYY/YYYY-MM-DD.md)

# YYYY-MM-DD

## Stats
- Distance: <km>
- Elevation: <m>
- Bike: <bike_id>

## Heart Rate
- Avg: <bpm | unknown>
- Max: <bpm | unknown>

## Bike State
- Tires: <OK | note>
- Brakes: <OK | note>
- Drivetrain: <OK | note>
- Chain: <OK | note>

## Intent
<free text>

## Effort
<Easy | Steady | Hard | Skip>

## Links
- Strava: <url | none>
- Intervals.icu: <url | none>
- Instagram: <url | none>

## Notes
<optional>

Rules:
- Exactly one ride entry per date
- Multiple activities in a day MUST be aggregated
- Bike field is required
- Ride entries MUST NOT contain bike specifications

---

### Bike File (/bikes/{bike_id}.md)

# <Bike Display Name>

id: <bike_id>

## Frame
## Drivetrain
## Wheels & Tires
## Brakes
## Notes

Rules:
- bike_id MUST be lowercase kebab-case
- bike_id is immutable once created
- Bike specs live only in bike files
- Bike state lives only in ride entries

---

### Weekly Summary (/summaries/YYYY/week-XX.md)

# Weekly Summary — Week XX (YYYY-MM-DD → YYYY-MM-DD)

## Overview
- Days ridden
- Primary bike(s)

## Totals
- Total distance
- Total elevation gain

## Effort Distribution
- Easy / Steady / Hard days

## Heart Rate & Fitness
High-level trends only.

## Bike State & Maintenance
Notable changes or issues.

## Reflection
Short narrative summary of the week.

Rules:
- Summaries are interpretive, not raw data
- Numbers must come from ride entries
- No new metrics introduced here

---

## Bike Reference Convention

- Each ride MUST reference exactly one bike using bike_id
- The referenced bike_id MUST correspond to a file in /bikes/
- Ride entries MUST NOT duplicate bike specifications

Example:

Bike: momon105

---

## Change History

### v1.2
- Added /summaries directory for weekly summaries
- Defined weekly summary schema and scope
- Clarified aggregation of multiple rides per day

### v1.1
- Added formal Bike Reference Convention
- Clarified separation between bike spec and bike state
- Updated schema to require Bike field

### v1.0
- Initial specification
