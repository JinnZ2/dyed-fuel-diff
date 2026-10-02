# Dyed-Fuel Sensor-Drift — Automation Failure-Mode Matrix

STATUS: draft instrument. CC0. Field-observation + first-pass reasoning.
NOT a validated result. The dye-as-direct-cause link is UNRUN (see LITERATURE).
Purpose: name the seam so someone with lab/fleet access can run it.

## Scope
Running red-dyed (ag / off-road) diesel in NEWER, sensor-dense diesel trucks,
specifically the AUTOMATION case where no human felt-baseline backstops the stack.

## Two coupling channels (both carried here)
1. SIGNAL/ELECTRICAL — dye + carrier shift what a sensor reads (direct: optical/
   dielectric fuel sensors; indirect: carrier trace HC+metals offset combustion-
   side sensors).
2. MECHANICAL/CHEMICAL — carrier solvents degrade newer wetted materials at SEALS
   and CONNECTIONS (O-rings, quick-connects), worsened by temperature gradients.
   This channel shows up in the matrix wearing an electrical mask (rows 5, 10).

## The structural property (applies to every row)
Drift has no clean "dyed fuel" code. The true cause is ABSENT from the stack's
answer set, so the stack resolves to the NEAREST NAMED FAULT and commits to that
fault's action. The action can be a larger failure than the deviation that triggered it.

## Matrix — 11 fuel-coupled sensors, ALL feed CONTROL (none log-only)

| # | Sensor | Measurand | Dye coupling (true cause) | Misnamed as | Automated action | Consequence | Channel |
|---|--------|-----------|---------------------------|-------------|------------------|-------------|---------|
| 1 | Fuel level (optical/dielectric) | tank volume | dye shifts light transmission / dielectric const | low fuel / implausible level / sender fault | range replan, early refuel divert, or ignore sender | false divert, or runs tank low on bad estimate | signal (direct) |
| 2a | Fuel quality / WIF — OPTICAL type | contamination state | dye absorbance read as turbidity | contamination detected | derate / refuse-continue / safe-stop | mechanically-fine truck stops, maybe live lane | signal (direct) |
| 2b | Fuel quality / WIF — CAPACITIVE type | contamination state | carrier/blend shifts fuel dielectric constant; dye molecule itself minor here | water detected | derate / refuse-continue / safe-stop | same as 2a | signal (direct, via carrier) |
| 3 | O2 (wideband) | exhaust O2 / AFR | carrier trace HC+metals offset mixture result | lean/rich fault, O2 sensor aging | fuel trim correction, adaptive relearn | trims toward wrong target, drives on bad mix | signal (indirect) |
| 4 | NOx (up/down stream) | NOx ppm | post-combustion offset from altered burn | SCR efficiency / emissions fault | regulatory derate / limp mode | rolling roadblock mid-route | signal (indirect) |
| 5 | Rail pressure | injection pressure | seal weep at fittings bleeds pressure | rail pressure low, pump/injector fault | derate, limit power, fault-stop | chases pump/injector; real cause is a seal | MECHANICAL masked as signal |
| 6 | Mass airflow (MAF) | intake air mass | indirect; interacts via trim with O2 drift | MAF fault, intake leak | trim + boost correction | compounds the O2 misread | signal (indirect) |
| 7 | EGT | exhaust gas temp | altered burn shifts temp profile | overtemp / regen needed | forced / extended regen | wastes fuel, thermal load on DPF | signal (indirect) |
| 8 | DPF differential pressure | soot-load proxy | altered PM from carrier HC | DPF loading / regen fault | regen cycle, then derate if unresolved | repeated regens, premature DPF service | signal (indirect) |
| 9 | Fuel temp | fuel temp | minor property shift with blend | implausible temp / sensor fault | compensation tweak | small trim error | signal (minor) |
| 10 | Fuel pressure (low side) | lift-pump pressure | seal / air ingress at connections | lift pump fault, filter clog | derate, warn | chases pump/filter; cause is connection | MECHANICAL masked as signal |
| 11 | Injector feedback (balance/leak-down) | per-cyl correction | seal/material change in injector | injector imbalance / fault | injector cutout / replace flag | matched-set replace on good injectors | MECHANICAL masked as signal |

Rows 2a/2b: which principle a given truck uses is UNVERIFIED per vehicle; check the installed part before reading either row.

Camera / optical autonomy sensors: OUT OF SCOPE — not fuel-coupled. Listed only to bound the set.

## Cascade note (rows are NOT independent)
O2 drift (3) -> MAF correction (6) -> EGT shift (7) -> DPF regen (8).
One dye-driven O2 offset propagates through four control loops. Treat 3-6-7-8 as a chain, not four rows.
Seal channel: 5 and 10 share a root (weep/ingress at connections); 11 shares the material root.

## Open column to fill (proportionality) — the finding lives here
For each row: was the automated response PROPORTIONATE to the actual deviation,
or did the response itself become the larger failure? (e.g. row 2: trace drift -> full safe-stop.)
