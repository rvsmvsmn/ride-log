# Cycling Log Specification

Version: v1.1  
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

SPEC.md

---

## Core Principles

- One ride per day
- One bike per ride
- Bikes are referenced by ID, never duplicated
- Specs change slowly, rides change daily
- History must be explicit
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

---

### Bike File (/bikes/{bike_id}.md)

# <Bike Display Name>

id: <bike_id>

## Frame
## Drivetrain
## Wheels & Tires
## Brakes
## Notes

---

## Bike Reference Convention

- Each ride MUST reference exactly one bike using bike_id
- The referenced bike_id MUST correspond to a file in /bikes/
- Ride entries MUST NOT duplicate bike specifications

Example:

Bike: momon105

---

## Change History

### v1.1
- Added formal Bike Reference Convention
- Clarified separation between bike spec and bike state
- Updated schema to require Bike field

### v1.0
- Initial specification
