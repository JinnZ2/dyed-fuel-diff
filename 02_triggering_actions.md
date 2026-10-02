# Dyed-Fuel Drift — Triggering-Action Layer (singles + combinations)

STATUS: draft instrument, CC0. First-pass reasoning on TOP of 01_matrix.md.
NOT validated. Action ladders are typical-stack reasoning, not a specific OEM's logic.

## Part A — Single-sensor triggers (threshold -> action ladder -> cost)

| Sensor | Trigger condition | Automated action ladder | Cost of the misread |
|--------|-------------------|-------------------------|---------------------|
| 1 Fuel level | level crosses low / plausibility band | low-fuel warn -> reroute to fuel -> conservative speed/range limit if ignored | divert or range limp when tank is fine |
| 2 Fuel quality/WIF | WIF/quality flag asserts | warn -> power derate -> REFUSE / SAFE-STOP to protect injection | full stop on trace optical offset — worst single action |
| 3 O2 | AFR error past adaptive window | closed-loop trim -> adaptive relearn -> O2-aging fault if persistent | locks a wrong trim baseline into memory |
| 4 NOx | SCR conversion below regulated floor | inducement ladder: warn -> speed cap -> 5 mph limp (regulatory) | legally-mandated rolling roadblock |
| 5 Rail pressure | measured rail below commanded | raise pressure-control effort -> power limit -> fault-stop | stop attributed to pump/injector (cause: seal) |
| 6 MAF | airflow vs model mismatch | boost/EGR trim -> fault if implausible | quietly compounds row 3 |
| 7 EGT | past regen / overtemp threshold | initiate regen -> derate to cool if overtemp | unneeded regen cycle |
| 8 DPF dP | dP implies high soot load | active regen -> repeat -> derate -> service-required lockout | service lockout on mis-estimated load |
| 9 Fuel temp | temp implausible | compensation -> sensor fault if out of range | minor |
| 10 Low-side pressure | supply below threshold | lift-pump effort -> derate + warn | stop attributed to pump/filter (cause: connection) |
| 11 Injector feedback | per-cyl correction past limit | cylinder cutout -> derate -> replace flag | cutout of a good cylinder |

## Part B — Combination triggers (dye hits several AT ONCE; arbitration escalates)

| Combo | Sensors co-firing | Arbitration outcome | Cost |
|-------|-------------------|---------------------|------|
| C1 Safe-stop cascade | 2 quality + 5 rail-low | two "fuel integrity" flags -> CONFIRMED fuel emergency -> immediate SAFE-STOP, high confidence | one cause read as two confirmations -> hard stop, maybe live lane |
| C2 Combustion cascade | 3 O2 + 6 MAF + 7 EGT + 8 DPF | chained trims -> "aftertreatment system fault" -> forced regen then emissions derate | one O2 offset becomes system-level derate; cause invisible |
| C3 Emissions lockdown | 4 NOx + 8 DPF | both aftertreatment channels bad -> regulatory inducement + DPF service -> 5 mph limp + service lockout | truck legally crippled |
| C4 Fuel-starvation read | 5 rail + 10 low-side + 11 injector | three injection-path faults -> "fuel delivery failure" -> fault-stop + multi-part replace flag | whole injection system condemned; real cause = seals/dye |
| C5 Range/divert false | 1 level + 2 quality | "bad fuel + low level" -> urgent divert or stop at nearest point | unnecessary divert, or refuse-start at a stop |

## THE CORE FINDING (why combinations matter more than singles)

A single dye source couples into MULTIPLE sensors at once. The stack's arbitration
is built to treat co-occurring faults as INDEPENDENT CORROBORATION -> it raises
confidence -> it escalates to a bigger action.

But here the co-occurring signals are NOT independent — they share one hidden cause
(the dye / its carrier / seal attack). So:

  CORRELATED-CAUSE masquerades as INDEPENDENT-CONFIRMATION.

This INVERTS the safety logic of redundancy. Redundancy is supposed to raise trust
when independent sensors agree. When they secretly share a cause, agreement raises
a WRONG trust, and the system commits hardest (safe-stop, lockdown) exactly when it
is most wrong. The more sensors the dye touches, the more "confirmed" the false fault.

## NEXT PASS (not yet built)
- Per-combo: the cheap DISCRIMINATING check that separates the shared-cause case from
  a genuine multi-fault (ties back to 01_matrix proportionality column + the differential).
- Map each action ladder to a specific OEM/autonomy stack if a target is chosen.
