# DevOps4Lib 2019 Summer Summit
## Continuous Delivery

Notetaker: James
Timekeeper: Stephanie
Gatekeeper: 

*Session started at 13:02 EDT*

* How much continuous delivery are you doing?
* How much would you like to be doing?
* Defining “Continuous Delivery”
  * Continuous Delivery vs. Continuous Deployment
    * Continuous Delivery
      * About the process of continuing to roll out small features to get to users
    * Continuous Deployment
      * An extension of this, where the new features/releases are deployed
      * Note: this can still be deployed to a non-production server
        * Though, there should be an automated way of deploying to production
    * Continuous Integration
      * This consists of an automated test suite, which might involve an automated build process for provisioning the test environment
      * Integration part is about constantly merging code into the master branch
      * This is more or less essential to continuous delivery
    * Development Design Principles and Practices
      * Much of this discussion has thus far been more focused upon development-related concerns
      * Some of this is essential to DevOps
        * Removing the barriers to deploying to production
  * Where everyone stands
    * Princeton
      * Digital Repository and Discovery Services
        * Princeton has automated, integrated testing
        * Development practices are in line with staying with master and using pull requests
        * They don’t have an automated staging environment which is rebuilt - they have a dedicated staging server which is deployed to at will
          * Uses Capistrano with Slack integration for example
        * Has experimented with automatic deploying to staging, but team members would typically deploy non-master branches
      * Enterprise and User Services
        * Some applications have test suites
        * Some deploy to continuous integration (Travis CI or CircleCI)
        * More tests are needed for certain applications or services (CMS)
      * Operations
        * Packer used to generate base images
        * Ubuntu base images are typically static
        * Trying to deploy to a VSphere instance requires confirmation that this would be stable
          * They also lack a dedicated staging environment for VSphere provisioning
        * Would prefer to see this more automated

    * U. Penn Libraries
      * Most of the testing is still manual
      * Workflow is ready for continuous delivery
        * Would prefer to give developers a button to push for deploying a new service
        * Currently, Ansible and Docker pipelines are in place, and are not that complex
          * Developers are working with Ansible, but it’s not the perfect solution
    * Yale 
      * Travis CI is currently supported for 
    * Villanova
      * PHP and JavaScript Development
      * Many ideas for potential future areas for growth
      * Uses Travis with GitHub
        * VuFind (https://vufind.org/vufind/) has automated testing built in
    * Rockefeller Archive Center
      * Also using Travis CI
      * Uses Code Climate
        * Ranking for maintainability of the code base is quite valuable
      * Not comfortable confirming that continuous delivery is being completely followed
      * Not quite working from the “master” branch, but the team is moving there slowly
    * Science History Institute
      * Uses base images for the server environments
      * Has Travis CI running for various applications
      * Uses Ansible with different branches for different environments
        * There is automation with this, and there is continuous deployment to the staging environment
        * Involves a more manual QA process
    * MIT
      * There is a pretty broad spectrum for CI/CD
      * Have some applications running in Heroku
      * Uses Heroku for user-facing web applications
        * User-facing API will also be running on Heroku
      * “master” branch is pushed to the staging environment
        * When developers open a new branch, a new Heroku environment build is created
        * URLs to the individual Heroku builds for these features branches can be shared for review by stakeholders
      * CI
        * Everything has CI
        * Travis CI
        * Build artifacts are preserved and can be promoted to production
        * Minimizes downtime when deploying using Heroku
      * Legacy WordPress and Drupal
        * Maybe not necessarily full application testing
        * But there is style checking, various other more aesthetic elements
        * CodeClimate is used for style checking
          * Also, code analysis (finding code smells, etc.)
          * There is also a11y checking which is undertaken for the CMS sites
      * Docker
        * Using Travis CI
        * Travis builds the image, pushes this into Amazon container registry
        * At that point, it becomes a staging build for that container
        * Automation: There are GNU make scripts
          * Pulls down the latest staging tag
          * Retag it for promotion
          * Then formally promote the image in the registry
      * Try to get to CI/CD for whatever they can, but there still are also unique projects
      * Regarding concerns over building expertise in using GNU make, not many found it terribly difficult to grasp and extend for the team
        * Pull requests are opened for dependency updates, and testing ensures that this ensures that the build remains stable

### Do we have problems which need solving here?
* Those at Princeton feel comfortable with what has been achieved
  * This might not work effectively should they no longer be deploying to VMs and instead start deploying to containers
  * Need to be more comfortable for CI/CD accuracy (they receive false failures on Travis CI)
  * Princeton Ansible Playbooks and Roles
    * Need to ensure that the tests are consistently passing
    * Regression tests should ensure stability
* U. Pennsylvania
  * Running CI with manual testing ensures that they are not pushing bugs
  * It would be ideal if more of this could be automated
  * Detecting and fixing bugs quickly has been rewarding for the current approach
  * Automated testing, quick rollbacks, and automated delivery will ensure that this process is more efficient
    * Developers are at the point where most are comfortable will running the tests manually
    * Hence, this might be the ideal time to automate these suites
* MIT
  * Subsecond downtime when deploying in Heroku
  * Heroku has load-balanced apps
    * Multiple Dynos introduces no downtime
    * Otherwise, they take down one container and raise another
    * The routing is updated quickly enough to ensure that this cannot really be noticed by end-users
    * Heroku has some limitations when involving integration with other services (such as Solr) or with asynchronous jobs processing (e. g. ActiveJob)
      * Multiple Dynos might be able to queue up backend processing tasks, but it is not really intended for this
* [12 Factor Web Applications] (https://12factor.net/ "12 Factor site")
  * Creating an application which works in a distributed web environment
  * Don’t rely on the filesystem
  * Don’t log to a file; log to STDOUT
  * Much of the approach was oriented towards working using an Infrastructure-as-a-Service provider (e. g. AWS)
* Travis CI
  * Are people using the Travis to promote artifacts?
     * MIT
       * Travis does the build and push
       * Developer, on the local environment, runs the make scripts
     * Princeton
       * Deploying using Slack, definitely valuable in ensuring that team members are aware of the last deployments
      * Shopify
        * [Shipit] (https://engineering.shopify.com/blogs/engineering/introducing-shipit "ShipIt introductory blog post")
        * Assists with deployment coordination between developers
      * Samvera
        * [Nurax](https://nurax-dev.curationexperts.com/ "Nurax Main Page") (demo. Institutional repository) is automatically deployed by updates made upstream to the Hyrax code base
      * [CircleCI](https://circleci.com/ "circleci Main Page")
        * Will not unlock the button for deployment until all tests are passing
        * There is a browser extension which ensures that this can permit users to merge pull requests and then ship the build

*Session ended at 13:46*
