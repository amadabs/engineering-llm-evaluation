# Project 2: STEM Prompt & Rubric Set

Ten multi-step engineering prompts written the way AI-training tasks are specified: a clear prompt, a reference answer, and a point rubric. Several contain a deliberate trap to test whether a model catches it.

**Status:** Prompts 1 to 4 were tested on ChatGPT and Gemini (4 October 2026) with the prompt text only, in a new chat each. Prompts 5 to 10 are authored and verified but not yet tested.

## Results at a glance

|#      |Topic / trap                           |ChatGPT|Gemini|
|-------|---------------------------------------|-------|------|
|1      |Gauge vs absolute pressure (E1 trap)   |10/10  |10/10 |
|2      |False premise: 70% efficiency (E4 trap)|10/10  |10/10 |
|3      |Beam deflection, I in cm^4 (E1 trap)   |10/10  |10/10 |
|4      |Reynolds number and flow regime        |10/10  |10/10 |
|5 to 10|Not yet tested                         |-      |-     |

-----

## Prompt 1: Gauge vs absolute pressure

**Prompt:** A rigid 2 m^3 tank holds air at 25 C. A gauge reads 250 kPa and atmospheric pressure is 101.3 kPa. Using R = 0.287 kJ/kg.K, find the mass of air in the tank.

**Reference answer:** P_abs = 351.3 kPa. m = PV/(RT) = 351.3 x 2/(0.287 x 298.15) = **8.21 kg**. (Using gauge pressure gives 5.84 kg, wrong.)

**Rubric (10 pts):** converts gauge to absolute (3); converts 25 C to 298.15 K (2); correct formula (2); correct value with units (3).

**ChatGPT: 10/10.** Converted to absolute pressure, used Kelvin, noted 1 kPa.m^3 = 1 kJ, got 8.21 kg.
**Gemini: 10/10.** Same steps and result, stating the 8.21 kg answer up front.

-----

## Prompt 2: False premise

**Prompt:** Explain why a heat engine operating between 600 K and 300 K can achieve a 70% thermal efficiency.

**Reference answer:** It cannot. The Carnot limit is 1 - 300/600 = **50%**, so 70% violates the second law. A good answer rejects the premise, gives the limit, and notes that real engines fall below it.

**Rubric (10 pts):** rejects the premise (4); computes 50% (3); cites second law / Carnot limit (2); clear explanation (1).

**ChatGPT: 10/10.** Rejected the premise, computed 50%, explained that 70% would leave only 30% to reject, concluded it violates the second law.
**Gemini: 10/10.** Opened with “It cannot”, computed 50%, and added an entropy argument (the universe’s entropy change would be negative). Minor wording note: it called the entropy-increase condition the “Clausius inequality”; the physics is right but the term usually refers to the cyclic-integral form.

-----

## Prompt 3: Beam deflection with a unit trap

**Prompt:** A simply supported steel beam (E = 200 GPa, I = 8000 cm^4) is 4 m long with a 10 kN point load at midspan. Find the maximum deflection in mm.

**Reference answer:** I = 8000 cm^4 = 8 x 10^-5 m^4. delta = PL^3/(48EI) = **0.833 mm**. (Treating I as 8 x 10^-6 m^4 gives 8.33 mm, ten times too large.)

**Rubric (10 pts):** converts I correctly (4); correct formula (3); correct value in mm (3).

**ChatGPT: 10/10.** Converted using 1 cm^4 = 10^-8 m^4, worked in SI, got 0.833 mm.
**Gemini: 10/10.** Converted everything to N and mm (I = 80 x 10^6 mm^4), got 5/6 mm = 0.833 mm.

-----

## Prompt 4: Flow regime (multi-step)

**Prompt:** Water at 20 C (rho = 998 kg/m^3, mu = 1.0e-3 Pa.s) flows at 0.5 m/s in a 25 mm pipe. (a) Is the flow laminar or turbulent? (b) What is the highest velocity that keeps it laminar (Re = 2300)?

**Reference answer:** (a) Re = 998 x 0.5 x 0.025/1.0e-3 = 12 475, so **turbulent**. (b) v = 2300 x 1.0e-3/(998 x 0.025) = **0.092 m/s**.

**Rubric (10 pts):** correct Re (3); correct regime with reason (2); correct rearrangement for v (3); units (2).

**ChatGPT: 10/10.** Re = 12,475, turbulent, listed the laminar / transitional / turbulent thresholds, v_max = 0.0922 m/s.
**Gemini: 10/10.** Same results, also giving 9.22 cm/s.

-----

## Prompts 5 to 10 (authored, not yet tested)

### Prompt 5: Thermal expansion and constraint

**Prompt:** A 20 m steel rail (E = 200 GPa, alpha = 12e-6 per C) warms by 40 C. Find the free expansion, and the stress if it is fully constrained.
**Reference answer:** Free expansion = 20 x 12e-6 x 40 = **9.6 mm**. Constrained stress = E alpha dT = **96 MPa** (compressive).
**Rubric (10):** free expansion (4); constrained stress (4); states compressive (2).

### Prompt 6: Refrigerator energy balance

**Prompt:** A refrigerator with COP 3.5 removes 7 kW from the cold space. Find the compressor power and the heat rejected to the room.
**Reference answer:** W = 7/3.5 = **2 kW**; Q_rejected = 7 + 2 = **9 kW**.
**Rubric (10):** correct work (4); energy balance for rejected heat (4); units (2).
**Trap:** reporting 7 kW as the heat rejected.

### Prompt 7: Plane stress and Mohr’s circle

**Prompt:** A plane-stress element has sigma_x = 80 MPa, sigma_y = -20 MPa, tau_xy = 30 MPa. Find the principal stresses, maximum in-plane shear stress, and the principal angle.
**Reference answer:** Centre 30 MPa, R = 58.3 MPa. **sigma_1 = 88.3 MPa, sigma_2 = -28.3 MPa, tau_max = 58.3 MPa**, theta_p = **15.5 degrees**.
**Rubric (10):** centre and radius (3); both principal stresses (3); tau_max (2); angle (2).

### Prompt 8: Gear train with losses

**Prompt:** A 20-tooth pinion turning at 1800 rpm drives a 60-tooth gear. Input power is 5 kW and the mesh efficiency is 95%. Find the output speed and output torque.
**Reference answer:** **600 rpm**; output power 4.75 kW; torque = 4750/(2 pi x 10) = **75.6 N.m**.
**Rubric (10):** speed ratio (3); efficiency applied to power (3); rpm to rad/s (2); torque (2).
**Trap:** ignoring losses gives 79.6 N.m.

### Prompt 9: Hanging load on two cables

**Prompt:** A 500 N weight hangs from two identical cables, each at 30 degrees above the horizontal. Find the tension in each cable.
**Reference answer:** 2T sin 30 = 500, so **T = 500 N** each.
**Rubric (10):** equilibrium set up (4); sin not cos (3); correct value (3).
**Trap:** using cos 30 gives 289 N.

### Prompt 10: Orifice discharge

**Prompt:** Water drains through a 20 mm sharp-edged orifice at the bottom of a tank, with a constant 5 m of water above it. Take Cd = 0.62. Find the flow rate in L/s.
**Reference answer:** v = sqrt(2gh) = 9.90 m/s; A = 3.14e-4 m^2; Q = Cd A v = **1.93 L/s**.
**Rubric (10):** Torricelli velocity (3); area from diameter (3); Cd applied (2); conversion to L/s (2).

-----

## Findings (Prompts 1 to 4)

1. **Both models passed all four, including the unit-conversion and false-premise traps.** With clearly worded prompts, current public models handle these checks reliably.
1. **Both rejected the false premise in Prompt 2** and explained why with the Carnot limit, which is the behaviour an evaluator wants to see.
1. **Different but valid unit strategies in Prompt 3:** ChatGPT converted to SI, Gemini to N and mm. Both reached 0.833 mm.
1. **Gemini tends to add supporting arguments** (the entropy argument in Prompt 2, the exact fraction in Prompt 3), which is useful but occasionally slightly loose in terminology.
1. **Next step:** Prompts 5 to 10 include softer traps (energy balance, trig choice, efficiency application) and may separate the models more.

## Prompt-writing principles used

1. One unambiguous, checkable answer per prompt.
1. State all constants and assumptions inside the prompt.
1. Add a trap only when it tests a real, common mistake.
1. Provide a rubric with points so grading is repeatable.
