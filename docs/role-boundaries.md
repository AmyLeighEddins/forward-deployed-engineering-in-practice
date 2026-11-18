# Ask Halyard Role Boundaries

## Responsibility matrix

| Activity | Responsible (does the work) | Accountable (approves) | Approval status |
|---|---|---|---|
| Discovery | FDE and Delivery Lead | Sponsor | Approval Pending |
| Source access | FDE and Client Security | Security Team Lead | Approval Pending |
| Deployment | FDE, Client Technical Team, and Delivery Lead | Client Technical Team Lead | Approval Pending |
| Incidents | FDE and Operations Team | Operations Lead | Approval Pending |
| Acceptance | FDE, SME, and Pilot Users | Operations Lead | Approval Pending |

## Duties that remain with the client

### Client security
- Grants us access to documents.
- Tells us who has access to what information. If documents are not organized by access and also not categorized in the database then this will need to be done.
- Works with us on current security measures the company takes.

### Client operations
- Reports incidents from users and testers so we can fix those after an agreed upon solution.
- Runs through acceptance criteria to approve the release.

### Client Technical Team
- Approves or denies deployments and works with us on issues the SME and Pilot Users experience or other reasons why it was denied.

## Capacity reduction
- First remove all 'Could Have' column from scope if any are included since they are not needed.
- Then go through 'Should Have' column and pick through what we can move to 'Could Have' depending on how much needs reducing.
- If that's still not enough then start reducing scope of items in 'Must Have' column.

### Scope removed if capacity halves
- Reduce which users see the first version.
- Reduce bonus functionality that isn't important to first release.

### Safety gates that remain
- We will not remove any security or permission requirements/tests. Permission tests stay because the charter's escalation halts release on any access-control failure.
- We will not remove any scope for testing.