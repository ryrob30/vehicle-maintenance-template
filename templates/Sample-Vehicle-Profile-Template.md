# Vehicle Profile — [Year Make Model]

> Template: copy this file per vehicle into `vehicles/` (e.g. `vehicles/my_car.md`). Replace all bracketed values.

## Identity

- **Year/Make/Model:** [Year Make Model]
- **Trim/Body:** [confirm from VIN decode]
- **Engine:** [confirm from VIN decode]
- **Transmission:** [confirm from VIN decode]
- **Drivetrain:** [confirm from VIN decode]
- **Engine/transmission codes:** [confirm]
- **Tire/wheel size:** [confirm from door placard and installed tires]
- **Emissions/market configuration:** [confirm if relevant]
- **VIN:** [your VIN]
- **Configuration source:** VIN decode + owner confirmation *(record source/date)*
- **Current odometer:** [mileage] *(owner-reported; update whenever the user reports a reading)*
- **Odometer reading date:** [date]
- **Date profile last updated:** [date]

## Operating conditions

- **Maintenance schedule basis:** [normal / severe / unknown — confirm against the owner's manual]
- **Relevant use or environment:** [short trips, towing, dusty roads, extreme temperatures, road salt, etc.]
- **Modifications affecting service or fitment:** [none known / describe]

## Fluids currently in use

| System | Fluid/specification currently used | Last confirmed service | Source/status |
|---|---|---|---|
| Engine oil | [spec, capacity — verify in manual] | [date / mileage] | [owner log / unverified / etc.] |
| Transmission fluid | [spec — verify] | Unknown | Service history unknown |
| Coolant | [spec — verify] | Unknown | Service history unknown |
| Brake fluid | [spec] | Unknown | Service history unknown |

## Known quirks & open issues

Record symptom, status, when first noted, and source/evidence. Do not list a common failure mode here unless it has been observed on this vehicle.

- [example: symptom] — status: [monitor/diagnose/inspect]; first noted: [date]; evidence: [owner report / inspection]

## Common failure points for this model/year/mileage *(to be filled in from manual/web research)*

These are research leads, not confirmed defects. Cite the source and applicability for every item.

- [failure point] — [source/reference]

## Past repair history *(phase 2 — to be backfilled)*

See `maintenance-log/<vehicle>.md` for completed-work entries. Summary of major work to be added here once compiled.

## Profile source notes

- Use `sources/` entries to locate manuals, references, and web material; the catalog is metadata, not the source itself.
- Record the source and date for configuration details, capacities, specifications, and externally researched claims.
- When a specification conflicts across sources, retain the conflict and prefer an official source that covers this exact configuration.

## Notes for the agent

- [any vehicle-specific guidance for the agent — age-related wear, aftermarket vs. OEM manuals, known research gaps, etc.]
