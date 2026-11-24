# Design Twenty Golden Questions

## Goal
Twenty cases cover normal retrieval, permissions, messy data, abstention, injection, tool routing, outages and freshness without inventing policy answers. The work is pushed to your public forward-deployed-engineering-in-practice GitHub repository, with docs/04-defining-success-with-evals/design-twenty-golden-questions.md covering the goal, steps, commands, results and observations.

## Steps taken
1. Filled out the golden cases, scoring and dataset freeze in eval-plan.md after reading through the module, data inventory and decomposition memo.
2. Wrote design-twenty-golden-questions.md (this file).
3. Committed changes

## Commands
~~~bash
# Stage files from UI
git commit -m "04-defining-success-with-evals: design twenty golden questions"
git push origin main
~~~

## Results
See [eval-plan.md](../eval-plan.md) for the golden cases, thresholds, scoring and dataset freeze.

## Observations

### Surprises
  - How many cases can't be scored yet because they need a source owner to supply the correct answer
  - How thorough the plan is for just 20 questions
  - How you're basically going to have to check for a leak for all questions, but makes sense

### Follow-ups
  - Get source owners to supply expected facts and location of answers for the blocked cases
