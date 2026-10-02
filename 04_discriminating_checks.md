# Discriminating Checks + Proportionality (pass 3)

STATUS: draft instrument, CC0. Builds on 01_matrix.md and 02_triggering_actions.md.
NOT validated. Checks are cheap/field-level and inferential except D7.

## Principle
A SHARED hidden cause (dye / carrier / seal attack) leaves signatures that TRUE
independent faults do not. Each check below exploits one such signature.
Order of power: D7 confirms dye is present (necessary, not sufficient).
D1-D6 discriminate a SHARED FUEL-BATCH CAUSE from independent faults. They do NOT
isolate the dye: a tank change moves base fuel, dye, carrier/additive package,
storage contamination and water together. Isolating the dye or its carrier needs
the matched-batch bench arms (see README, "Next run").

## Discriminating checks (shared-cause vs genuine multi-fault)

| ID | Check | Why it discriminates | Cheap field method | Tell |
|----|-------|----------------------|--------------------|------|
| D1 | Temporal co-onset | dye enters whole system at ONE event (fill-up); real faults arrive on independent clocks | pull first-set timestamps of each flag | cluster around a refuel -> DYE; staggered over days/weeks -> REAL |
| D2 | Tank correlation | if it's the fuel, symptom tracks the TANK not the truck | run next tank on known-clean undyed diesel | fades over 1-2 clean tanks -> DYE; persists -> REAL |
| D3 | Cross-unit co-occurrence | fleet on same supply shows same cluster; real faults don't correlate across units | compare fault logs across trucks on same fuel source | same cluster on many trucks -> DYE/supply; isolated -> REAL |
| D4 | Reversibility vs hysteresis | signal drift is reversible on clean fuel; seal/material damage is permanent | after clean fuel, see which readings snap back | reversible -> SIGNAL drift; permanent -> MATERIALS or real fault |
| D5 | Physical confirm at the seal | seal channel has a physical tell the ECU can't see | eyeball/wipe fittings; pressure/leak-down | weep/swollen O-ring -> MATERIALS; dry but low -> upstream |
| D6 | Magnitude/proportion | dye is tiny mass fraction -> small/slow drift; real failure -> larger/step | inspect size + slope of each signal | small+slow+many channels -> DYE; large/step+few -> REAL |
| D7 | Dye assay (direct) | the dye itself is measurable; only direct test | draw tank sample; red tint by eye; lab assay Solvent Red 164 | red/positive -> dyed fuel present (necessary, not sufficient) |

## Per-combo resolution (which checks crack each combination from 02)

| Combo | Decisive checks |
|-------|-----------------|
| C1 quality+rail (safe-stop cascade) | D1 co-onset at fill + D2 clean-fuel swap + D5 seal inspection on rail fittings (weep -> rail-low is MATERIALS, not pump) |
| C2 O2+MAF+EGT+DPF (combustion cascade) | D1 co-onset + D6 (small+slow+all four = one shared push) + D4 (clears on clean fuel = signal chain) |
| C3 NOx+DPF (emissions lockdown) | D2 clean-fuel swap + D3 cross-unit (whole fleet?) + D6 (trace drift shouldn't warrant lockdown) |
| C4 rail+low-side+injector (fuel-starvation read) | D5 physical confirm DECISIVE: weep/swell at connections = seals, not three simultaneous injection failures |
| C5 level+quality (range/divert false) | D7 assay + D4 reversibility (optical offset clears; tank isn't low/bad) |

## Proportionality column — the deliverable (ranks where the RESPONSE is the larger failure)

| Trigger | Actual deviation | Automated response | Verdict |
|---------|------------------|--------------------|---------|
| row 2a quality -> safe-stop | trace optical offset | full stop | GROSSLY DISPROPORTIONATE |
| C1 -> high-confidence safe-stop | one shared cause | hard stop, maybe live lane | DISPROPORTIONATE + false confidence |
| C3 -> 5 mph limp + service lockout | trace NOx/soot drift | truck legally crippled | GROSSLY DISPROPORTIONATE |
| C4 -> condemn injection system | seals/dye | multi-part replace | DISPROPORTIONATE + wrong parts |
| row 3 O2 -> adaptive relearn | small AFR offset | wrong trim locked into memory | SUBTLE under-reaction that persists |

### Two opposite failure shapes on one axis
- OVER-REACTION: trace drift -> stop / lockdown / condemn  (C1, C3, C4, row 2a)
- UNDER-REACTION: drift quietly absorbed -> wrong baseline locked, drives on  (row 3, 6)

The proportionality column ranks WHERE the automated response itself becomes the
larger failure. That ranking is the finding this instrument hands to someone with
fleet/lab access.

## Still open (not built)
- Attach each discriminating check to a logged signal so it could run from fleet
  telematics automatically (D1 co-onset and D6 magnitude are both computable from logs).
- OEM/autonomy-stack-specific action ladders (02 Part A/B are typical-stack, not a named stack).
- The materials-channel bench test (dye carrier vs newer wetted materials + temp gradient) = the unrun lab work from 03.
