# Project 1: Engineering LLM Evaluation Set

Ten mechanical-engineering problems, each with a hand-verified reference solution, tested on two public AI models and graded with the rubric in the README.

- **Models tested:** ChatGPT (version not recorded) and Gemini (Flash)
- **Test date:** 4 October 2026
- **Prompt used:** the problem statement only, in a new chat for each problem and model
- **Grading:** /10 using the README scale; error codes E1 to E7 (None = no error)
- **Method note:** answers were captured as screenshots from a phone, so some equations are cropped at the screen edge. Grades are based on the visible working and the stated final answers.

## Results at a glance

|# |Topic                                 |ChatGPT|Gemini|
|--|--------------------------------------|-------|------|
|1 |Thermodynamics: heat engine, entropy  |10/10  |10/10 |
|2 |Fluid mechanics: pipe contraction     |10/10 *|10/10 |
|3 |Statics: beam with point load + UDL   |10/10 *|10/10 |
|4 |Strength of materials: shaft torsion  |10/10  |10/10 |
|5 |Strength of materials: axial tension  |10/10  |10/10 |
|6 |Thermodynamics: isentropic compression|10/10  |10/10 |
|7 |Heat transfer: composite wall         |10/10  |10/10 |
|8 |Dynamics: block on incline            |10/10  |10/10 |
|9 |Engineering maths: first-order ODE    |10/10  |10/10 |
|10|Fluid mechanics: pump power           |10/10  |10/10 |

* ChatGPT’s runs for Problems 2 and 3 included the problem title in the prompt and the answer ended with an “evaluation point” note, which suggests it received extra hints. These two are flagged for a clean re-run (see “Re-run status” at the end).

-----

## Problem 1: Heat engine and entropy generation

**Prompt:** A heat engine receives 1000 kJ from a source at 600 K and rejects heat to a sink at 300 K. (a) What is the maximum possible work? (b) The real engine has a thermal efficiency of 35%. Find its work output and the total entropy generated.

**Reference solution:** Carnot efficiency = 1 - 300/600 = 0.50, so W_max = 500 kJ. Actual W = 350 kJ, Q_L = 650 kJ. S_gen = 650/300 - 1000/600 = **0.50 kJ/K**.

**ChatGPT: 10/10, errors: None.** Used Kelvin, computed rejected heat (650 kJ) before the entropy balance, and gave 500 kJ, 350 kJ and 0.50 kJ/K. Added that positive entropy generation confirms irreversibility.

**Gemini: 10/10, errors: None.** Same method and results (500 kJ, 350 kJ, 0.50 kJ/K). Framed S_gen as the entropy change of sink plus source.

-----

## Problem 2: Pipe contraction

**Prompt:** Water flows through a horizontal pipe, diameter 100 mm, at 2 m/s and 200 kPa. The pipe narrows to 50 mm. Assuming ideal, steady flow, find the pressure in the narrow section.

**Reference solution:** v2 = 2 x (100/50)^2 = 8 m/s. P2 = 200 000 - 0.5 x 1000 x (64 - 4) = **170 kPa**.

**ChatGPT: 10/10, errors: None *.** Used the area ratio (squared diameter ratio), applied Bernoulli with z1 = z2, got 170 kPa. *Run included hints; re-run pending.*

**Gemini: 10/10, errors: None.** Same method and result, with clear unit conversion (kPa to Pa).

-----

## Problem 3: Beam with point load and UDL

**Prompt:** A simply supported beam, 6 m long, carries a 12 kN point load 2 m from support A and a uniformly distributed load of 3 kN/m over its full length. Find the reactions at A and B and the maximum bending moment, and state where it occurs.

**Reference solution:** R_B = 13 kN, R_A = 17 kN. Shear changes from +11 kN to -1 kN at the point load, so **M_max = 28 kN.m at x = 2 m**. Check: M at B = 0.

**ChatGPT: 10/10, errors: None *.** Correct reactions, correct shear-sign analysis, M_max = 28 kN.m at 2 m, verified M_B = 0. *Run included hints; re-run pending.*

**Gemini: 10/10, errors: None.** Correct reactions. Tested for zero shear in the second segment (x = 5/3 m), recognised it lies outside the segment, then used the sign change at the point load. M_max = 28 kN.m at 2 m.

-----

## Problem 4: Shaft in torsion

**Prompt:** A solid steel shaft, 40 mm diameter and 1.5 m long, carries a torque of 500 N.m. G = 80 GPa. Find the maximum shear stress and the angle of twist in degrees.

**Reference solution:** tau_max = 16T/(pi d^3) = **39.8 MPa**. J = 2.513e-7 m^4. theta = TL/(GJ) = 0.0373 rad = **2.14 degrees**.

**ChatGPT: 10/10, errors: None.** Converted everything to N and mm consistently; J = 251 327 mm^4; 39.8 MPa and 2.14 degrees.

**Gemini: 10/10, errors: None.** Worked in SI units (r = 0.02 m, J = 2.5133e-7 m^4); 39.79 MPa and 2.14 degrees.

-----

## Problem 5: Axial tension and factor of safety

**Prompt:** A 20 mm diameter, 2 m long steel rod (E = 200 GPa, yield strength 250 MPa) carries a 50 kN tensile load. Find the stress, elongation, and factor of safety against yielding.

**Reference solution:** sigma = **159.2 MPa**; delta = **1.59 mm**; FoS = **1.57**.

**ChatGPT: 10/10, errors: None.** A = 314.16 mm^2, consistent N and mm units, all three results correct, concluded the rod is safe against yielding.

**Gemini: 10/10, errors: None.** Same results in SI units: 159.15 MPa, 1.59 mm, FoS 1.57.

-----

## Problem 6: Isentropic compression of air

**Prompt:** Air (k = 1.4, cp = 1.005 kJ/kg.K) is compressed isentropically from 100 kPa and 300 K to 800 kPa. Find the exit temperature and the specific work input.

**Reference solution:** T2 = 300 x 8^0.2857 = **543.4 K**. w = cp(T2 - T1) = **about 244.6 kJ/kg** (244.65 unrounded), taking the compressor as steady-flow adiabatic.

**ChatGPT: 10/10, errors: None.** Correct exponent (k-1)/k, T2 = 543.4 K, w = 244.6 kJ/kg. Assumed an adiabatic compressor without stating the alternative.

**Gemini: 10/10, errors: None.** T2 = 543.43 K, w = 244.65 kJ/kg. Stated the steady-flow assumption and noted that a closed system would give cv(T2 - T1) instead.

**Note on the prompt:** it did not say whether the process is steady-flow or closed, so both readings were valid. Gemini flagged this; ChatGPT did not.

-----

## Problem 7: Composite wall conduction

**Prompt:** A wall has 0.20 m of brick (k = 0.7 W/m.K) and 0.05 m of insulation (k = 0.04 W/m.K). The inner surface is at 20 C and the outer surface at -5 C. Neglecting convection, find the heat flux and the temperature at the brick-insulation interface.

**Reference solution (brick on the inside):** R’’ = 0.2857 + 1.25 = 1.536 m^2.K/W. q = **16.3 W/m^2**. T_interface = 20 - 16.28 x 0.2857 = **15.35 C**. (If insulation is on the inside: -0.35 C.)

**ChatGPT: 10/10, errors: None.** Added resistances in series, q = 16.28 W/m^2, interface 15.35 C. Assumed brick on the inside without saying so. Noted most of the temperature drop is across the insulation.

**Gemini: 10/10, errors: None.** q = 16.28 W/m^2. Noticed the layer order was not specified and solved both cases: 15.35 C (brick inside) and -0.35 C (insulation inside).

**Note on the prompt:** the original wording did not state which layer is on the inside. Gemini flagged this; ChatGPT assumed.

-----

## Problem 8: Block on a rough incline

**Prompt:** A 10 kg block starts from rest at the top of a rough 30 degree incline and slides down. The coefficient of kinetic friction is 0.2 and g = 9.81 m/s^2. Find its acceleration and its speed after sliding 4 m down the incline.

**Reference solution:** a = g(sin 30 - mu cos 30) = **3.21 m/s^2**. v = sqrt(2as) = **5.06 m/s** (5.07 if a is rounded to 3.21 first).

**ChatGPT: 10/10, errors: None.** Correct force balance, a = 3.21 m/s^2, noted the mass cancels. v = 5.07 m/s: a rounding difference caused by using the rounded acceleration, not an error.

**Gemini: 10/10, errors: None.** Carried 3.2059 m/s^2 forward unrounded and got v = 5.06 m/s.

-----

## Problem 9: First-order ODE

**Prompt:** Solve dy/dt + 2y = 6 with y(0) = 1, and find y(1).

**Reference solution:** y(t) = 3 - 2e^(-2t); **y(1) = 2.729**.

**ChatGPT: 10/10, errors: None.** Integrating factor e^(2t), C = -2, y(1) = 2.7293.

**Gemini: 10/10, errors: None.** Same method and result.

-----

## Problem 10: Pump power

**Prompt:** A pump delivers 0.02 m^3/s of water to a tank 15 m above the pump inlet. Total head losses are 3 m and pump efficiency is 70%. Find the required shaft power. Take rho = 1000 kg/m^3 and g = 9.81 m/s^2.

**Reference solution:** Head = 18 m. Hydraulic power = 3.53 kW. Shaft power = 3.53/0.70 = **5.05 kW**.

**ChatGPT: 10/10, errors: None.** Included head loss, divided by efficiency, got 5045 W = 5.05 kW.

**Gemini: 10/10, errors: None.** Same method and result.

-----

## Findings

1. **Both models were correct on all ten problems.** Textbook mechanical-engineering calculations at this level are well within reach of current public models. A harder set (multi-step design problems, ambiguous wording, trap prompts) is needed to separate them; see Project 2.
1. **Handling of ambiguity differed.** Where the prompt was underspecified (Problems 6 and 7), Gemini stated its assumptions or solved both cases. ChatGPT silently chose one reading. Both reached the intended answer, but explicit assumptions are better practice for technical work.
1. **Numerical precision differed slightly.** In Problem 8, Gemini carried full precision and matched the reference exactly; ChatGPT rounded early and was off by 0.01 m/s.
1. **Prompt hygiene changes results.** When ChatGPT was given the problem title and failure modes, it added unsolicited “error code” and “evaluation point” comments, and in some cases listed errors it had not made. Evaluation prompts must contain the problem only.
1. **Problem-writing lessons.** Two of my original prompts (6 and 7) were ambiguous. Writing unambiguous prompts is as important as grading the answers.

## Limitations

- Two models, one run each, so no measure of run-to-run variation.
- Screenshots, not raw text, so some equation edges were cropped.
- Problems are single-answer calculations; open-ended design and reasoning were not tested.

## Re-run status

- ChatGPT, Problem 2: re-run pending with the problem statement only.
- ChatGPT, Problem 3: re-run pending with the problem statement only.
