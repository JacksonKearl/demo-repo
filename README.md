# Mock Repo for Bot Testing
### A mockery of what a repo should be.

## Setup
Create Milestones "Backlog" then "Backlog Candidates", in that order. 

Ensure Backlog is https://github.com/[...this...]/milestone/1 and Backlog Candidates is https://github.com/[...this...]/milestone/2, if they aren't simply update the relavant config lines in `.github/feature-requests`.

```
  candidateMilestone: {
    number: 2,
    name: 'Backlog Candidates'
  },
  approvedMilestone: {
    number: 1,
    name: 'Backlog'
  },
```
