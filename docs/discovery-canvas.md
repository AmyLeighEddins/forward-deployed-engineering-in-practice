# Ask Halyard discovery canvas

## Users and jobs
- 600 staff and offices in Rotterdam, Felixstowe and Singapore. (fact) [HF-BRIEF-01]
- Sales and ops need help locating current approved guidance for a specific task. (fact) [HF-BRIEF-01]

## Current workflow and baseline
- Sales, ops, legal and finance keep guidance across a shared drive, CRM records and historical support tickets. (fact) [HF-BRIEF-01]
- Staff often ask colleagues which version is authoritative. (fact) [HF-BRIEF-01]
- Yesterday a customer asked which handling policy applied to a temperature-sensitive shipment. Priya found two SOP PDFs and an incident note. Priya asked Tom which one was current. It took perhaps fifteen minutes, but Priya did not time it. Priya says they get several questions like that each day. (interview claim) [HF-INT-01]

## Wrong-answer cost
- Even confirming that a litigation note exists can be a disclosure. (interview claim) [HF-INT-01]
- Stop a release for any permission leak, unapproved external data transfer or answer presented as contractual authority without a source. Lena will review the legal boundary tests, not the model's marketing benchmark. (interview claim) [HF-INT-01]
- Incorrect rates and contractual terms can have financial consequences. (fact) [HF-BRIEF-01]

## First slice and exclusions
- The sponsor proposes Ask Halyard: a permission-aware assistant for sales and ops with grounded citations, an HTTP API and an MCP server. A later workstream could fine-tune a small model to summarize support tickets. The sponsor wants something demonstrable quickly but has not approved a production date, budget or service-level objective. Do not turn this desire into a contractual commitment. (fact) [HF-BRIEF-01]
- The brief's product scope is a north star, not evidence that every feature belongs in the first slice. (fact) [HF-BRIEF-01]
- Shipment mutation, autonomous external messages, legal advice and automated compensation decisions are outside the initial concept. (fact) [HF-BRIEF-01]
- For a first demonstration: “What is our demurrage policy for Felixstowe?” would be useful. Another is “Which rate card applies to account ACME-0042?” But Priya would rather see one reliable workflow than ten polished guesses. (interview claim) [HF-INT-01]
- For the pilot a response time of a few seconds would feel good, but Priya cannot approve a number for everybody. Measure our current searches for a week and compare matched tasks. Include whether answers were right, not only whether people liked them. (interview claim) [HF-INT-01]
- Read-only initially. Escalation to a person is part of the workflow, not a failure to hide. (interview claim) [HF-INT-01]
- For the pilot it should be able to answer “What is our demurrage policy for Felixstowe?” asked by different users to show which users have access to the documents containing the info. We don't want to use the rate card question yet since incorrect rates can have financial consequences. (decision)

## Systems and data owners
- The proposed estate contains read-only CRM entities accounts, contacts, shipments and opportunities; team folders under lab/shared-drive/; and lab/tickets.jsonl. Documents include contracts, SOPs, incident reports, spreadsheet rate cards and policies. Duplicate bytes, superseded versions and sensitive legal documents are expected. (fact) [HF-BRIEF-01]
- After the project is completed and we hand it off, the platform team may operate it, but they have not agreed. Ask them to rehearse the runbook before we accept handover. (interview claim) [HF-INT-01]

## Success hypothesis
- The current approved policy, a page reference and a clear statement if the available document does not answer the question. A confident summary of an old incident is not a policy. Incident records explain what happened once; they are not blanket authority. (interview claim) [HF-INT-01]
- If it can't find the evidence it should say it cannot answer from the accessible sources and direct the user to an appropriate owner. Do not replace missing evidence with general freight knowledge. A model outage and an empty search are different operational problems. (interview claim) [HF-INT-01]
- A success would involve the answer (checked for correctness) along with the referenced supporting policy. It should only use the approved version of the document (pending how to know for sure which one is the right one). It should not use past incidents as the answer since those could have been done incorrectly. If it cannot find an answer it should state that and not make up false claims. This will reduce lookup time compared with the one-week baseline. (decision) 

## Constraints and approvals
- Production identity, network location, retention, data residency and egress restrictions remain unconfirmed. Source owners must approve any real-data sampling. (fact) [HF-BRIEF-01] 
- Usually a filename ending in v2 means newer, but teams sometimes copy old files into new folders. Tom can identify the current handling SOP for our first pilot. We need an owner list for the others. Please do not assume modification time means approval. (interview claim) [HF-INT-01]
- Sales must not see legal documents. Ops policies can be visible to sales. Legal has access to finance material, but finance does not automatically have access to legal. Do not reveal a legal title or snippet while saying access was denied. (interview claim) [HF-INT-01]
- Sending all documents to a hosted model is not approved. Show the data flow and retention policy first. Synthetic material is fine for the lab. Production prompts and traces may also contain confidential material, so logging is part of that review. (interview claim) [HF-INT-01]

## Questions to validate
- What is the production due date?
- Who are the other owners besides the current handling SOP for the pilot?
- What is the average time that it takes currently to get a right answer (not a guess of 15 min)?
- How do we know what the correct document when there are different versions if we can't use modification time or the version number?
- Are the document permissions separated by folders or have a type on them so we know when we can show them?
- They want it fast but have not approved an budget or access to test data, so that will delay us. 
