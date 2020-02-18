# Mock Repo for Bot Testing
### A mockery of what a repo should be.

## Setup
Create Milestones "Backlog" then "Backlog Candidates", in that order.

Ensure the label `needs more info` exists.

Ensure Backlog is https://github.com/[...this...]/milestone/1 and Backlog Candidates is https://github.com/[...this...]/milestone/2, if they aren't simply update the relavant config lines in `.github/feature-requests`:


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

## Supported Features

### Commands

Comment "/needsMoreInfo" or label `~needs more info` and the bot will add a comment add the `needs more info` label, removing the `~needs more info` label if it exists. The bot will only respond to comments left by repo owners and `['Tyriar', 'rebornix', 'sbatten', 'octref', 'roblourens', 'RMacfarlane', 'sana-ajani']` (defined in `.github/commands.yml`).

### Feature Requests

When an issue is labeled `feature-request`, it will be placed in the `Backlog Candidates` milstone if it is not assigned to some other milestone within `.github/feature-requests.yml#onLabeled.delay` seconds (10).

At that point, if the issue goes for `.github/feature-requests.yml#onMonitorDaysOnCandidateMilestone.daysOnMilestone` days (0.0007 days, 1 minute) without recieving `.github/feature-requests.yml#onMonitorUpvotes.upvoteThreshold` upvotes (1), it will be commented on stating it has not been tranfered to `Backlog`. Otherwise, it will be transfered to `Backlog`.

### Locker

If an issue goes `.github/locker.yml#daysAfterClose` days (1 minute) without having an update in `.github/locker.yml#daysSinceLastUpdate` (30 seconds), and doesnt have labels `.github/locker.yml#ignoredLabels` (`*out-of-scope`), it will be locked.

### Needs More Info

If an issue goes `.github/needs_more_info.yml#daysUntilClose` days (1 minute) since update with the label `needs mroe info`, it will be closed.