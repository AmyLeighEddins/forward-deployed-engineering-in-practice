# 0001: Permission-aware policy pilot
Status: Proposed; approval pending

## Context
Approved ops guidance must be retrievable without legal disclosure.
Production identity and operating ownership remain release blockers.

## Options
PostgreSQL/pgvector; managed search; non-generative source search.

### PostgreSQL/pgvector
- **Advantage:** Have AI in the loop to help find the right answer faster. Data stays inside Halyard (HF-INT-01 Q5).
- **Drawback:** Model and hosting costs versus the $0.03 per request budget plus prompt injection and leakage risks. 

### Managed search
- **Advantage:** Less for owner (pending) to manage.
- **Drawback:** Not approved (HF-INT-01 Q5). Plus we would have to wait on them to fix any issues.

### Non-generative source search
- **Advantage:** No model cost versus the $0.03 per request budget and no prompt injection possibility.
- **Drawback:** Slower to find the answer (may not be fast enough for expected business outcome), dependant on them cleaning up the data and that speeding up their process enough to be all they need.

## Decision
Recommend the local PostgreSQL-first slice for the lab. It keeps data from going out to outside sources and has AI to help find answers faster. 
Production promotion requires identity and source-owner approval.

## Consequences
One permission chokepoint simplifies review but needs query tests.
Local inference constrains throughput; no availability claim is implied.
Citation cache should be permission-aware and cleared on model, prompt, or index changes.

## Verification
Negative ACL tests, approved-source evals and restore rehearsal.

## Revisit triggers
- Unmet latency budget - p95 is over the 10s budget for a week or more
- Cost - average cost per request is over the $0.03 budget for a week or more
- Indexing limits - Indexing takes too long to be done overnight (a good cadence to get updated versions)
- Changed deployment constraints - Halyard changes the constraint on managed search
