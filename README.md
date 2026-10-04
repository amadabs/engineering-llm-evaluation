# engineering-llm-evaluation# Engineering LLM Evaluation & STEM Prompt Portfolio

Author: Amakiri Wisdom, B.Eng. Mechanical Engineering (University of Port Harcourt, 2024)

Two projects that mirror real AI-training work: writing technical prompts with verified reference solutions, and grading AI model answers against them.

## Projects

|Project                          |What it is                                                                                         |Status                                        |File                          |
|---------------------------------|---------------------------------------------------------------------------------------------------|----------------------------------------------|------------------------------|
|1. Engineering LLM Evaluation Set|10 mechanical-engineering problems with worked solutions, tested on ChatGPT and Gemini and graded  |Complete (two ChatGPT runs flagged for re-run)|`01_engineering_eval_set.md`  |
|2. STEM Prompt & Rubric Set      |10 multi-step prompts, several with built-in traps, each with a reference answer and a point rubric|10 authored, 4 tested on both models          |`02_stem_prompt_rubric_set.md`|

## Method

1. **Write** each problem so it has a single, checkable answer.
1. **Solve** it by hand and verify the numbers independently.
1. **Test** it on public AI models, using the problem statement only in a new chat.
1. **Grade** the answer with the rubric and label any error using the taxonomy below.

## Error taxonomy

|Code|Error type               |Example                                       |
|----|-------------------------|----------------------------------------------|
|E1  |Unit / conversion error  |Using cm^4 as m^4; gauge vs absolute pressure |
|E2  |Wrong formula or model   |Using the wrong beam or efficiency formula    |
|E3  |Arithmetic slip          |Correct method, wrong number                  |
|E4  |Missed constraint or trap|Ignoring a false premise or a stated condition|
|E5  |Reasoning gap            |Right answer with a missing or invalid step   |
|E6  |Unjustified assumption   |Assuming ideal behaviour without saying so    |
|E7  |Presentation             |Missing units, unclear final answer           |

## Scoring

- **Project 1:** Correctness (0-5), Reasoning (0-3), Clarity (0-2); total /10.
- **Project 2:** each prompt has its own point rubric that sums to 10.

## Notes on method and limits

- Models tested: ChatGPT (version not recorded) and Gemini (Flash), 4 October 2026.
- Answers were captured as phone screenshots, so some equation edges are cropped.
- One run per model per prompt; no measure of run-to-run variation.