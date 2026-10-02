# dyed-fuel-diff — instrument set

**Draft · CC0 · not validated.** A differential and automation failure-mode instrument for the hypothesis that a red-dyed (ag/off-road) diesel **dye package, fuel batch or storage context** might be misread by sensors in newer, sensor-dense diesel trucks. Built from a field observation and first-pass reasoning to name a testable seam for someone with lab/fleet access. The **dye-as-direct-cause link is UNRUN**. Nothing in this repository demonstrates a dye-induced sensor fault, seal failure, controller decision, or measured fleet effect.

| File | What it contains | Provenance |
|---|---|---|
| [`01_matrix.md`](01_matrix.md) | Eleven proposed fuel-coupled sensor paths, two proposed coupling channels and cascade | User-supplied draft, copied byte-for-byte |
| [`02_triggering_actions.md`](02_triggering_actions.md) | Hypothetical single-sensor ladders and five combination/arbitration cases | User-supplied draft, copied byte-for-byte |
| [`03_literature.md`](03_literature.md) | The literature split, links to checked sources, and the unrun causal join | Adapted from the user's inline literature split, with source verification and explicit limitations |
| [`04_discriminating_checks.md`](04_discriminating_checks.md) | D1–D7 candidate checks, per-combo discriminators and proportionality hypotheses | User-supplied draft, copied byte-for-byte |
| [`REVIEW_NOTE.md`](REVIEW_NOTE.md) | Read-this-first limits on causation, action ladders and legal/physical testing | Editorial caveats added for this public draft |

**Do not confuse correlation with proof of dye causation.** Dye present in a tank can coexist with water, debris, different base fuel, additives, storage condition or genuine hardware faults. The original D1–D6 checks are screening hypotheses, not dye-specific causal tests; D7 confirms only marker presence. A real diagnosis must identify actual installed sensors and calibrations, independently assay fuel and inspect hardware. The proposed outcomes in the three copied draft files are **conditional examples**, not observations or instructions to operate a truck. See [the evidence-to-claim register](03_literature.md#evidence-to-claim-register) and [the review note](REVIEW_NOTE.md).

**Open / next:** measured proportionality rather than the draft's proposed ranking; demonstrated per-combo discriminators rather than the current candidate list; OEM/model/software-specific action maps; and a matched, lawful bench test separating dye, carrier, base fuel, contamination and temperature. HMAC is not applicable here. No code or experimental harness is supplied, so **no test run is claimed**.

This repository is licensed under [CC0 1.0 Universal](LICENSE). Dyed-fuel road-use restrictions and fuel specifications vary by jurisdiction and application; this research proposal is not permission to use untaxed fuel on public roads, disable emissions systems or bypass a vehicle safety response.
