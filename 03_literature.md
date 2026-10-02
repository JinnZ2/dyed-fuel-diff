# Literature split — which body holds which half

**Status:** draft instrument, CC0. Based on the literature-split text supplied in the task and a focused source check on 2026-10-02. This is **not** an exhaustive review, and absence of evidence here is not evidence of no effect. The proposition that a red-dye molecule or its commercial carrier directly creates the sensor/automation cascade in [`01_matrix.md`](01_matrix.md) is **UNRUN**. See [`REVIEW_NOTE.md`](REVIEW_NOTE.md) before interpreting the other documents as observed results.

## 1. Dyed fuel: marker and diagnostics, not a demonstrated sensor fault

- [ASTM D6258-17](https://store.astm.org/d6258-17.html) describes visible-spectroscopy measurement of Solvent Red 164 in diesel for tax-compliance purposes. This **proves the marker has a measurable optical signature in a dedicated assay**. It does not establish that a particular truck's level, water-in-fuel (WIF), NOx, O2, or other sensor responds to that dye or that an ECU misnames it.
- The diagnostic article [“Common Rail Diesel Performance Problems” (MOTOR)](https://www.motor.com/magazine-summary/common-rail-diesel-performance-problems/) states that red-dyed fuel's composition, specific gravity and energy content are the same as nondyed fuel in its discussion, but flags poorly maintained storage as a source of contamination. That is a **diagnostic account**, not an experimental null result for each dye formulation, carrier, sensor, or fuel batch. Its concrete signs—water, debris, pressure fault codes—also supply plausible alternatives to a dye effect.
- WIF hardware is not uniformly optical: for example, [Rochester Sensors describes a capacitive WIF device](https://rochestersensors.com/product/capacitive-water-in-fuel-sensors/) that senses separated water by capacitance. The matrix's optical/turbidity mechanism therefore requires identification of the **actual installed part**, not an inference from the WIF label.
- [IRS fuel-inspection guidance](https://www.irs.gov/irm/part4/irm_04-024-015r) treats red dye as a tax/usage marker and checks on-road tanks for dyed fuel. [EPA's diesel standard overview](https://www.epa.gov/diesel-fuel-standards/diesel-fuel-standards-and-rulemakings) says on-road and (with specified exceptions) nonroad fuel transitioned to ultra-low sulfur diesel. **Red color alone is not a measurement of sulfur, water, lubricant content, storage condition, or material compatibility.** On-road use of tax-exempt dyed fuel can carry legal consequences; do not use public-road operation as an experiment.

**Present state:** a dye-specific in-vehicle response is neither demonstrated nor ruled out by these sources. “Effectively unstudied” here means **not located in this targeted source check**, not a definitive literature-wide negative.

## 2. Elastomer degradation: measured for other fuel compositions, not this dye package

[Farfan-Cabrera, Pérez-González & Gallardo-Hernández, “Deterioration of seals of automotive fuel systems upon exposure to straight Jatropha oil and diesel,” *Renewable Energy* 127 (2018), 125–133](https://doi.org/10.1016/j.renene.2018.04.048) exposed VMQ, FKM, EPDM and CR elastomers to straight Jatropha oil, ordinary diesel, and an 80:20 diesel/Jatropha blend. It measured material-property changes; the reported outcomes **vary by fuel and elastomer**. The article does **not** test commercial red dye or its carrier, nor does it establish that FKM always “holds” while all others fail. A [2022 multi-fuel O-ring experiment](https://pmc.ncbi.nlm.nih.gov/articles/PMC9414156/) likewise measures properties over long immersion using diesel and other blends; those are different exposures.

**What transfers:** method—matched materials, known fuel composition, temperature and exposure controls, mass/volume/hardness/tensile and leakage measurements. **What does not transfer:** a conclusion that dyed fuel or a dye-carrier solvent attacked a newer truck's seals. A field-observed weep does not identify its chemical cause.

## 3. Common-rail contamination and automation action: adjacent, but not the join

- The [MOTOR diagnostic article](https://www.motor.com/magazine-summary/common-rail-diesel-performance-problems/) discusses contaminated fuel and common-rail pressure-related fault codes; it recommends sampling early. It supports the need to **test water, debris, fuel quality, pressure and fittings before blaming a particular component**. It does not assign those failures to dye.
- [EPA's diesel-exhaust-fluid/SCR guidance](https://www.epa.gov/regulations-emissions-vehicles-and-engines/diesel-exhaust-fluid) documents that some SCR/DEF system faults or shortages can lead to severe derates, including older strategies approaching five mph, while guidance and implementations change. This **does not validate** the specific `NOx + DPF -> 5 mph` path or a fuel-quality flag causing an immediate safe-stop in any named truck. OEM, model year, software calibration, jurisdiction and fault code are missing.
- [INL's common-cause failure analysis](https://nrcoe.inl.gov/publicdocs/CCF/NUREGCR-6268_Rev1.pdf) explains how dependence among component failures can make an independence-based redundancy calculation overstate reliability. This supports the **conceptual concern** about counting correlated evidence as independent confirmation; it does not show that a diesel controller implements the exact arbitration claimed in [`02_triggering_actions.md`](02_triggering_actions.md).

## 4. The join to run, not a result to quote

No source above measures **the dye molecule versus its commercial carrier** on a **specified newer truck's wetted materials, installed sensor types, logged signals and response map** under controlled thermal exposure. The user's field-observation hypothesis about a pre-1990 versus newer-fleet boundary is likewise **not checked in these sources**.

A discriminating program should use matched base-fuel aliquots with (A) no added dye/package, (B) independently characterized carrier-only, (C) characterized dye-only if technically feasible, and (D) the commercial dye package, while independently measuring water, sulfur, biodiesel content, additives, storage condition and batch identity. Bench-test actual installed sensors and seal materials at declared temperatures and durations; log raw measurements and fault thresholds before testing any software response. Distinguish apparent signal offset, real pressure leakage and true multi-faults. Use [ASTM D6258](https://store.astm.org/d6258-17.html) or an equivalent qualified assay to confirm marker exposure, **not** to infer causation. A lawful controlled bench setting is preferable to using dyed fuel in a highway vehicle. The experimental design, data, OEM action maps and outcome are **NOT BUILT / NOT RUN**.

## Evidence-to-claim register

| Evidence | What it supports | What it does not support |
|---|---|---|
| ASTM D6258 | Solvent Red 164 can be quantified optically in diesel | An installed truck sensor reacts to it |
| MOTOR diagnostic article | Contamination is a plausible alternative and fuel sampling matters | A controlled dye-versus-clear causal comparison |
| Elastomer exposure studies | Fuel/elastomer compatibility can be measured and can depend on composition | Failure of a particular seal caused by the red-dye package |
| EPA DEF guidance | SCR/DEF faults may cause severe derates in some vehicles | C3's exact two-sensor arbitration or universal five-mph outcome |
| INL common-cause analysis | Correlated failures undermine independence assumptions | This truck's ECU makes the assumed independence error |

**Bottom line:** there are literatures on **fuel markers**, **fuel/material compatibility**, **common-rail contamination**, **inducement strategies**, and **dependent faults**. Their intersection, for this claimed fuel package and a named newer truck, remains unmeasured. That missing join is the proposed experiment, **not** evidence that dyed fuel has caused the proposed cascade.
