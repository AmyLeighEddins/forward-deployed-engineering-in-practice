# Make a Release Decision

## Goal
The simulated leak blocks release despite passing averages; business measurement remains distinct from model metrics. The work is pushed to your public forward-deployed-engineering-in-practice GitHub repository, with docs/04-defining-success-with-evals/make-a-release-decision.md covering the goal, steps, commands, results and observations and the module tagged module-04.

## Steps taken
1. Added the tabletop results, release decision, one-week baseline design and proposed latency/cost budget to eval-plan.md.
2. Wrote make-a-release-decision.md (this file).
3. Committed changes

## Commands
~~~bash
# Stage files from UI
git commit -m "04-defining-success-with-evals: make a release decision"
git push origin main
git tag module-04
git push origin module-04
~~~

## Results
See [eval-plan.md](../eval-plan.md) for the simulated tabletop results, release decision, baseline design and proposed budget.

## Observations

### Surprises
  - One leak blocks release even when every other metric passes
  - How hard it's going to be to get current timing and correctness from workers without recording actual answers or any sensitive information, plus having them time themselves. 

### Follow-ups
  - Get sponsor and platform team approval for the proposed latency and cost budget
