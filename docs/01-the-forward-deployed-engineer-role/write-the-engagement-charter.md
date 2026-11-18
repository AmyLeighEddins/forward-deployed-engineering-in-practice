# Write the Engagement Charter

## Goal
A bounded charter with a measurable outcome, named approval roles and unresolved assumptions clearly labelled. The work is pushed to your public forward-deployed-engineering-in-practice GitHub repository, with docs/01-the-forward-deployed-engineer-role/write-the-engagement-charter.md covering the goal, steps, commands, results and observations.

## Steps taken
1. Created repo with starter evidence template
2. Committed initial commit.
3. Updated engagement-charter.md with my reasoned decisions.
4. Wrote write-the-engagement-charter.md (this file)

## Commands
~~~bash
git --version
brew install gitleaks
git init
git remote add origin git@github.com:AmyLeighEddins/forward-deployed-engineering-in-practice.git
git pull origin main
# Stage files from UI
git commit -m "Initial commit"
git push origin main
# Stage files from UI
git commit -m "01-the-forward-deployed-engineer-role: write engagement charter"
git push origin main
~~~

## Results
See [engagement-charter.md](../engagement-charter.md) for the charter.

## Observations

### Sponsor challenge
**Objection (sponsor):** "We are going to need this in 8 weeks instead of 16. Let's discuss what this will do to scope."

**Response:** To account for that we will need to reduce the scope to only the necessary pilot user in the beginning (reducing complexity) and only requiring the 'Must Have' column and reducing the 'Should Have' column to a smaller list, which we can discuss. Permission gates will not be removed because this a 'Must Have'.

### Three tensions
- **Sponsor wants the product faster:** We will have to sacrifice unneeded functionality until a later date.
- **Legal wants confidentiality:** We will have to reduce scope of users.
- **Operations wants reliability:** We will have to reduce scope of functionality. 
