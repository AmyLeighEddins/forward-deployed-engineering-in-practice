# Create the Production Readiness Plan

## Goal
A plan with evidence, status, owners and go/no-go consequences that never equates planned controls with verified controls. The work is pushed to your public forward-deployed-engineering-in-practice GitHub repository, with docs/05-from-prototype-to-production/create-the-production-readiness-plan.md covering the goal, steps, commands, results and observations.

## Steps taken
1. Filled out the prototype debt register, readiness table and staged release in production-readiness-plan.md after reading through the module, data inventory, decomposition memo and eval plan.
2. Wrote create-the-production-readiness-plan.md (this file).
3. Committed changes

## Commands
~~~bash
# Stage files from UI
git commit -m "05-from-prototype-to-production: create the production readiness plan"
git push origin main
~~~

## Results
See [production-readiness-plan.md](../production-readiness-plan.md) for the prototype debt register, readiness table and staged release.

## Observations

### Most expensive "not verified" row
  - Identity, because it depends on Halyard's company login and security team rather than our own work, and needs their review and approval before the pilot can start
  - Second is Ownership because having every single part of the project assigned to someone seems like it could be a lot

### Surprises
  - How much the prototype can work while still proving "nothing about real login, access removal or keeping sources current"
  - How much needs to rollback for each release

### Follow-ups
  - Confirm owners for each readiness row and get platform approval for RTO and RPO
