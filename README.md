# dyed-fuel-diff — instrument set

CC0 · draft instrument · dye-as-direct-cause link UNRUN

Instrument for one question: what does red-dyed (ag / off-road) diesel do to the
SENSOR CHAIN and WETTED MATERIALS of newer, sensor-dense diesel trucks — and what
does the automation do with the result. Built so someone with lab or fleet access
can run it. Posture: written for working people on the risk-mitigation side;
limits are carried as marked terms, not as caveat blocks.

## Inputs (status-tagged)

| Input | Status | Scope |
|---|---|---|
| A farm operation buying only pre-1990 trucks for ag diesel use | OBSERVED | one operation's fleet decisions |
| Newer trucks on dyed fuel: deterioration at connections and seals (O-rings, fittings), not molded parts | OBSERVED | same operation |
| Temperature gradients accelerate the deterioration | OBSERVED | same operation |
| Mechanics working from the code reader get the nearest named fault, never "dyed fuel" | OBSERVED | field practice |
| Two coupling channels (below) | DERIVED | from the observations + typical stack |
| Action ladders and combinations in 02 | PROPOSED | typical-stack reasoning, not a named OEM map |
| Dye or its carrier as the specific cause | UNRUN | — |

## Two channels

1. SIGNAL / ELECTRICAL — dye and carrier shift what fuel-coupled sensors read
   (direct: optical or capacitive fuel sensors; indirect: combustion-side sensors).
2. MECHANICAL / CHEMICAL — carrier solvents degrade newer wetted materials at
   seals and connections, with heat as the accelerant. This channel appears in the
   fault codes wearing an ELECTRICAL MASK (rail pressure, lift-pump pressure,
   injector balance). Least-doubtful piece of the set, because it rests directly
   on the observed seal deterioration.

## Core finding (DERIVED, generalizes beyond fuel)

One hidden source couples into several sensors at once. Arbitration logic treats
co-occurring faults as INDEPENDENT CORROBORATION, raises confidence and escalates.
A correlated cause masquerades as independent confirmation, inverting the safety
logic of redundancy: the system commits hardest exactly when it is most wrong.
The same structure applies to any automated stack with an unmodelled common cause.

Structural property: there is no "dyed fuel" code. The true cause is absent from
the answer set, so the stack resolves to the nearest named fault and commits to
that fault's action.

## Files

| File | Contents |
|---|---|
| `01_matrix.md` | 11 fuel-coupled sensor paths (row 2 split by WIF sensing type), both channels |
| `02_triggering_actions.md` | per-sensor action ladders; combinations C1–C5 (PROPOSED) |
| `03_literature.md` | which literature holds which half; the unrun join |
| `04_discriminating_checks.md` | D1–D7 checks; proportionality column |
| `REVIEW_NOTE.md` | marked limits on each file |

## The join (the deliverable is the gap)

- Dye as a direct cause: filed as inert marker — a concluded-inert gap, not a tested null.
- Seal / elastomer degradation: measured, but under alternative/vegetable fuels.
- Common-rail contamination: framed as water / debris / micron tolerance.

Nobody has measured the dye package's carrier against newer wetted materials, on
sensor-laden trucks, with the temperature gradient in the loop.

## Marked limits

- D1–D6 discriminate a shared fuel-batch cause from independent faults; they do not isolate the dye. D7 confirms presence only.
- Sensor type, control authority and action ladders are unverified per vehicle; inventory the actual truck first.
- Proportionality rankings in 04 are conditional on deviation size and OEM action, neither measured here.
- Nothing here is a run result. No assay, immersion, bench or fleet data.

## Next run

Matched fuel batch, separated arms:
`base fuel | + dye | + carrier/package | contaminated storage` × recorded temperature gradient.
Measure named elastomers (connection/seal parts from newer trucks vs pre-1990
equivalents) and the actual installed sensors. Pre-state thresholds.
Fleet side: wire D1 (temporal co-onset with fueling) and D6 (magnitude/proportion)
to telematics.

Population of interest: lawful dyed-fuel use — farm and off-road operation, and
shortage-relief waiver periods (where heat, the accelerant, is highest).

## Provenance

Instrument content built by Claude (Anthropic) from the repo owner's field
observations; published via Manus; patched per audit 2026-10-02. Committer ≠ author.

CC0 1.0 Universal — see LICENSE.
