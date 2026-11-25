# Record the Architecture Decision

## Goal
A proposed ADR with defensible alternatives and a no-go incident decision that includes cache invalidation and re-testing. The work is pushed to your public forward-deployed-engineering-in-practice GitHub repository, with docs/05-from-prototype-to-production/record-the-architecture-decision.md covering the goal, steps, commands, results and observations and the module tagged module-05.

## Steps taken
1. Filled out 0001-permission-aware-policy-pilot.md after reading through the module, interview, eval plan and production readiness plan.
2. Added the citation cache leak tabletop and a new debt register entry to production-readiness-plan.md.
3. Wrote record-the-architecture-decision.md (this file).
4. Committed changes

## Commands
~~~bash
# Stage files from UI
git commit -m "05-from-prototype-to-production: record the architecture decision"
git push origin main
git tag module-05
git push origin module-05
~~~

## Results
See [0001-permission-aware-policy-pilot.md](../adr/0001-permission-aware-policy-pilot.md) for the ADR and [production-readiness-plan.md](../production-readiness-plan.md#tabletop-citation-cache-leak) for the citation cache leak tabletop.

## Observations

### Question a reader is most likely to ask in a year
  - Why didn't we use a managed search service, and does the HF-INT-01 Q5 ruling on managed transfer still apply?

### Surprises
  - No existing readiness or debt register entry would have caught the cache leak

### Follow-ups
  - Add a multi-user cache leak case to the golden set (evals) in the next version
