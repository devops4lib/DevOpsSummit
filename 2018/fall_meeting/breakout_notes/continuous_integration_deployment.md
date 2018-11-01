Continuous Integration/Continuous Deployment
Problem Statement: Is there a problem to solve using CI/CD?

CI - testing every single change in code, automated testing, ease review process
Pushing changes every day with feature flags to exclude things that are broken
More dated definition of it. Time interval is not so much a factor any more

Iteration of change
Do pull requests and testing before integrating


Git flow branching structure
------
Example - https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow
Can help to work backwards from breaks
Merge conflicts
Develop
Feature branches
Master
Hot fixes
Github allows for squashing branches when merging PRs - https://help.github.com/articles/about-pull-request-merges/

Development auto-deploy on Pull Requests
Or on-demand approach, separate from a staging server, tied to the proposed code changes and not squashed by other branches being deployed to a staging server
De-commission deploys on PR close, webhook event
Close vs merge

CI/CD are often coupled, are they separate?

How do you have a short-lived feature branch?
Feature flippers - a boolean in the code to activate a new feature, adding new code to master branch while still working on a feature but deactivated until feature is ready, AKA feature flag

List of entitlements, some people have abilities to turn on or off new features captured by feature flags
CanCanCan example implementation in Ruby https://github.com/CanCanCommunity/cancancan

Cleanup process - remove them? Or always keep them in the code base?
Can make the code messy

Problem with new feature branches is that they can languish in QA, if they linger, is adding a new feature actually a priority or a need?

CI - keep codebase dynamic and add gatekeepers
CD - master/deploy branch should always be deploy branch
CI - getting changes into codebase
CD - getting changes deployed

On-demand appealing - sometimes the auto-deploys of a “development” branch might not be desired (ie overwriting a branch deploy that is undergoing QA)

Release Workflows
------
Manually prep release
Deploy after testing and documentation is ready
Local and Travis for checking/confirming
  -> Less frequent releases, around milestones, 1-2x per month

Immediate Production Releases, deploy and test from production - maybe not the best idea :)

Replicating production environments - challenges in having equal hardware/server setup in staging, AWS could maybe fix this
