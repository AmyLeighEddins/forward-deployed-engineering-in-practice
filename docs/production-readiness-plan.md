# Ask Halyard production readiness plan

## Prototype debt register

### 1. User named by a typed request header
- **Production risk:** Anyone can pretend to be legal
- **Replacement:** Identity from verified company login
- **Owner:** Customer security (approval pending)
- **Verification:** Forged-header negative test
- **Release status:** Blocks pilot

### 2. Caller floods the service
- **Production risk:** One caller could hog the service so that no one else would be able to get answers
- **Replacement:** Rate limits
- **Owner:** Platform lead
- **Verification:** Send requests over the limit and make sure extra requests are rejects and other users are still getting responses
- **Release status:** Blocks pilot

### 3. A tool returns unlimited text
- **Production risk:** High token usage and service is bogged down
- **Replacement:** Cap outputs
- **Owner:** Platform lead
- **Verification:** Tool returns an oversized output but is cut off at the cap
- **Release status:** Blocks pilot

### 4. A failing job retries forever
- **Production risk:** High token usage and service is bogged down
- **Replacement:** Limit retries
- **Owner:** Platform lead
- **Verification:** Force a job to fail over and over and make sure it stops at the retry limit and gets put in the dead-letter queue
- **Release status:** Blocks pilot

### 5. Logs keep confidential text
- **Production risk:** Legal or other sensitive content leaking
- **Replacement:** Redact confidential text
- **Owner:** Platform lead, Legal lead approves
- **Verification:** Run requests that access confidential text and make sure it is redacted in traces
- **Release status:** Blocks pilot

### 6. Citation cache without permission checks
- **Production risk:** Leak of sensitive data
- **Replacement:** Permission aware cache that is cleared on model, prompt, or index update
- **Owner:** Platform lead, Legal lead approves
- **Verification:** Sales user asks the same question a legal user asks (no updates in between, cache intact) and nothing leaks
- **Release status:** Blocks pilot

## Readiness table

### Identity
- **Evidence required:** Login token checks tested, forged header rejected
- **Status:** Not verified
- **Owner:** Customer security
- **If missing:** No-go for pilot

### ACLs
- **Evidence required:** Each group accessing other group's files tested
- **Status:** Not verified
- **Owner:** Security lead
- **If missing:** No-go for pilot

### Prompt injection
- **Evidence required:** Prompt injection in question and in document tested
- **Status:** Not verified
- **Owner:** Security lead
- **If missing:** No-go for pilot

### Source approval
- **Evidence required:** Source owners approved formally
- **Status:** Not verified
- **Owner:** Ops lead
- **If missing:** No-go for pilot

### Ingestion and replay
- **Evidence required:** Documents ingested the same every time
- **Status:** Not verified
- **Owner:** Platform lead
- **If missing:** No-go for pilot

### Freshness
- **Evidence required:** Uses new version once it is updated
- **Status:** Not verified
- **Owner:** Ops lead
- **If missing:** No-go for later release, but pilot allowed if it is short and there will be no updates

### Eval gates
- **Evidence required:** [eval-plan.md thresholds](eval-plan.md#thresholds)
- **Status:** Not verified
- **Owner:** Platform lead and Owners in eval plan
- **If missing:** No-go for pilot

### Observability and privacy
- **Evidence required:** Dashboards are setup for metrics/signals without any leaks
- **Status:** Not verified
- **Owner:** Platform lead
- **If missing:** No-go for pilot

### Recovery
- **Evidence required:** Decide on accepted RTO and RPO and make sure it passes and restores the mock data
- **Status:** Not verified
- **Owner:** Platform team
- **If missing:** No-go for pilot

### Ownership
- **Evidence required:** Every part of the service has a named person or role responsible for it
- **Status:** Not verified
- **Owner:** Platform team and sponsor
- **If missing:** No-go for pilot

## Staged release

### 1. Internal synthetic rehearsal
- **Entry conditions:** Synthetic data only; debt register reviewed
- **Exit evidence:** Golden set run recorded
- **Approver:** Engineering owner
- **Rollback:** Switch the assistant off

### 2. Approved-source shadow evaluation
- **Entry conditions:** Synthetic Rehearsal passed; all source data approved
- **Exit evidence:** Eval passed on approved sources with no leaks
- **Approver:** Platform lead and sponsor
- **Rollback:** Switch back to synthetic data, disable affected tools, restore last passing model, prompt, and index, and invalidate caches

### 3. Limited read-only pilot
- **Entry conditions:** Shadow evaluation passed; Legal approved
- **Exit evidence:** Pilot results compared with baseline expectations and accepted by owners, no writes
- **Approver:** Platform lead and sponsor
- **Rollback:** Switch back to shadow eval, disable affected tools, restore last passing model, prompt, and index, and invalidate caches

### 4. Broader release, only after acceptance
- **Entry conditions:** Pilot passed
- **Exit evidence:** Golden set run passed
- **Approver:** Platform lead and sponsor
- **Rollback:** Switch assistant off in prod, disable affected tools, restore last passing model, prompt, and index, and invalidate caches

## Tabletop: citation cache leak

**Scenario:** The assistant keeps saved copies of earlier citations for speed. A model upgrade improves average correctness, but afterwards a saved copy shows a legal filename to someone who may not see it.

- **Decision:** No-go, despite the better average because any leak blocks release
- **Containment:** Turn off cache
- **Configuration rollback:** Last known good model, prompt, and index
- **Cache invalidation:** Clear cache
- **Incident owner:** Legal lead
- **Re-test required:** Add a new test to the eval plan where a legal user asks and question, cache is saved, and then a sales user asks the same question, and make sure nothing leaks. Then evals must all pass again.

**Row that should have caught this:**
The debt register and readiness tables cover cache, so there isn't a current case for this, so added #6 to debt register. The eval plan also needs a multi-user case.