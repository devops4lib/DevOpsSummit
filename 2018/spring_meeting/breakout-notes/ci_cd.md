#CI/CD

##CI:
* Syncing with master at least once a day
* Running tests after merge or before
* If doing CI, it’s possible a build artifact is a requirement of CI

##CD: Continuous Delivery? or Continuous Deploy?
merging into a branch triggers a deploy to an appropriate server


Fully automated continuous delivery is not required to be doing CI / CD. It’s okay to have a “button” to release after QA.

Full test coverage may not be required, but high confidence is. Usually high confidence is achieved through high test coverage.

###CI examples
* CircleCI or Travis running tests as part of Pull Requests. GitHub allows protected branches that can block if tests fail.
* Git Flow
  * https://nvie.com/posts/a-successful-git-branching-model/
* GitHub Flow
  * https://guides.github.com/introduction/flow/
* What kinds of tests are we running?
  * Linting (rubocop, pep8, es6lint)
  * White spacing
  * Unit testing
  * Timed tests (can’t exceed specified time)
  * Coverage drops
  * Performance budget
  * AccessLint: https://www.accesslint.com
* Is anyone running unit and integration tests separately?
  * Some using Unit tests only in dev but full suite in CI
  * Many doing both in both environments
* BrowserStack is an option to run full integration tests with various browsers
* May need different rules for libraries vs applications
* CI minting tags in the repo on successful


###CD Examples
* stable master, pr accepted into master, master promoted to a “special” branch such as “qa” where it is deployed and a stakeholder can look at it, and “qa” branch is then promoted into “production” branch which kicks off build and push to production servers.
* Continuously deploying to development, manual qa branch for release testing, then merge into staging, then production branches.
  * Delivery: customer facing and usable release
* Tags instead of branches for various releases; minting of tag automated staging environment, manual change production
* Merge to master triggers staging environment, slackbot to production
* Heroku Pipelines; master pinned to staging environment automatically, prs open new builds, merge cleans up pr builds, manual step to promote staging slug to production
* Netlify
* Feature Flags:
  * Turn on a feature at runtime
  * Allows you to get code merged into master before it is signed off on
  * Can be client opt-in or ENV controlled

“If we can validate that a thing doesn’t work faster, we will work on less things.” - Alex






