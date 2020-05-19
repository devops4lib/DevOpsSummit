# Session 1: Deployment and Automation

Notetaker 1: Andrew Gearhart

Notetaker 2: James Griffin

## Initial topics proposed
* Standardizing application environments and deploys
* Continuous Deployment - Is anyone employing this strategy? If so, how? If not, why not?
* Is anyone else using AWX (Tower) for production using the docker-compose?  Any gotchas to share?
* Auto-provisioning for devs -- can we remove the bottleneck of spinning up new systems? 

## Defining Deployment and Automation
* Deployment primarily focuses upon the moving or duplication of applications between environments
  * This can be a production environment, or from a local MacBook to a staging server
* Automation
  * Reduces the number of steps required to get started
  * Reduces the number of cooks in the kitchen
  * Formalizes the process by which the code moves from the developers’ hands to production in collaboration with the operations team
    * Process in the past was a bit more difficult; developers and systems administrators had different goals and there was more negotiation of needs
  * Automation and deployment doesn’t exclusively address production; it can also address QA, staging, and development environments
  * Production-level deployment in some environments requires a change management process; there can be security and accessibility audits required

## Deployment
Problem Statements:
1. Communication of whether or not an application is deployed in production or staging/QA can be introduced as the user interface layer - can DevOps help communicate this to users (e. g. by introducing a banner?)
  1. There is an issue where ITIL (IT Service Management) reduces impact on the users for change, and DevOps also addresses this; however, the strategies employed differ between managers and DevOps engineers
  1. Communication the status of deployments is also necessary in some cases (e. g. a status board) - who is responsible for maintaining and updating this board? DevOps? Management?
  1. How do we ensure that everyone knows what is happening?
  1. Documentation changes should also be tracked within the deployment process
1. There are cases where may be one staging environment, and communication issues can arise when one team member is solely occupying this to test a feature branch
  1. Some use a “demo” branch for this
  1. Automating accessibility and security checks on the code when it is deployed or moved between environments
    1. Which tools are used?
    1. **This might fit better under the testing category**
1. Outside of the ideal of the ideal deployment, how consistent can deployments be between applications?
  1. Which steps can be taken in order to ensure that there is strict consistency (e. g. using Slack chat bots for deployment)
1. Continuous Deployment can be more of a cultural issue
  1. This can be very difficult to convince stakeholders that an application can be deployed to production without their review
  1. Which sort of stakeholders are hard to be brought into this process? Technical stakeholders?
    1. The technical stakeholders are willing to participate - they realize that they may have their time saved
    1. There are less technical stakeholders who prefer to reserve the power to personally approve of user interface design and features before a deployment
1. Goal behind DevOps in its entirety is to ensure that no one actually knows that you deployed anything
  1. Perhaps that should consistently be the goal

### Communication
* Does anyone have great solutions for synchronizing communication with deployment?
  * With respect to it being a cultural issue, communication with stakeholders is best when engineers can build an environment
  * Docker is used by some with a Helm-driven stack for creating environments in k8s
    * Continuous integration tool will tag a branch as a preview branch, and this will trigger the creation of a container which builds using this feature branch
  * Kubernetes (k8s)
    * Orchestration platform of workloads, identified by groups of Linux Containers
    * Using Docker containers without orchestration is manual, and it is very messy to track and organize systematically
  * Helm
    * This exists within the cloud-native framework for k8s which provides a number of YAML files which describe the final state of the k8s cluster
* Distinguishing how one disambiguates between production and staging environments for users
  * For some, new code deploys to production are distinct from the approach to deployment to staging
    * The audience notified for staging deployments is far more limited, but all 
    * Slack and E-mail are used in the cases discussed
### Continuous Deployment
* Some use Heroku-style Builds
  * Arbitrary branches trigger entirely new container builds
    * When a pull request opens, a new environment will be created in k8s
  * A stakeholder will be notified manually, and a notification will be issued in Slack
  * Others can request to cancel the deployment of feature branch builds
  * This is internal the technicians and engineers with stakeholders; there is a separate communications group for formal production deployment
  * Are you creating arbitrary numbers of deployments with preview branches?
    * In our case no - we don't have a declarative infrastructure yet so we have a pre-set demo url for the applications that use it.  Andrew's Kubernetes example would be able to handle that by defining a new deployment.
### Containers and Kubernetes (k8s)
* Kubernetes Environments
  * A true k8s workflow deprecates the idea of production vs. staging environments
  * Different clusters permit one to isolate the testing environments more readily, with a development cluster being isolated from a production cluster
  * Stakeholders can preview the new features in the development cluster, and pending approval, this can then be propagated through branch management for git and deployment to the production cluster
### Interacting with Stakeholders
* Stakeholder Review
  * Some use a dedicated UAT (user acceptance testing) server
    * Service management oversees change management
      * Communications on a weekly basis to what will change
      * Deployments are scheduled on Wednesday for a maintenance period
      * What does this look like for developers?
        * There is a test branch, into which are merged topic branches
        * There is Jenkins for CI, which deploys to the UAT for stakeholder sign-off
    * Others will track changes by offering a changelog to end-users
      * For each new feature or bug-fix which affects user experience, updating this log is required in order to ensure that a pull request can be merged
    * User Acceptance Testing branch
      * It will be very complicated to deal with situations where changes need to be shown, but the deployment cannot be handled in a linear fashion
* Branches requiring user acceptance testing
  * Sometimes this can be circumvented by providing screenshots to stakeholders without a staging deployment
### Data Management for Deployments
* Cloning data into non-production environments
  * Does the data get cleaned for k8s users?
    * Test data can be derived from the fixtures used in test-driven development suites
    * This can be imported into the non-production environments, as all non-production environments are testing environments
  * Exceptions:
    * Open Journal Systems, where data are cloned from production into a QA system
    * This is for testing very specific aspects of performance (e. g. load testing)
### Testing
* Changes in all environments without formalized deployment strategies are still employed by everyone to some extent
* Testing integrated systems with Kubernetes
  * For authentication, k8s will permit one to pass in parameters for testing single-sign on
    * A consistent configuration can be referenced from multiple k8s clusters, ensuring that testing with integrated systems can be addressed systematically

## Automation
### AWX/Ansible Tower
* Does any else use this?
* Some have installed this, but have found that using single sign-on can be problematic for integration
  * Reviewing the source code in depth is necessary, and generally deploying and maintaining AWX is difficult
* ansible-semaphore is a project which provides the same features for Ansible Tower, but without hte maintenance burden
  * There is quite a bit of labor involved in the configuration of templates for AWX/Ansible Tower, and discussions will continue beyond this session
  * The requirement to run AWX in Docker is problematic for many, as not all use Docker consistently and with the same degree of support for Docker infrastructure across organizations
### Spinning up new systems
* Bottlenecks and difficulties
  * Some pursued k8s with containers in response to difficulty of running ~90 individual servers for projects
    * Configuration management using Chef was successfully used originally for new systems
      * However, changes to individual servers could through the configuration management out of synchronization
      * There were times were resetting the state of the servers could not be avoided
    * k8s is not used for local development environments
      * docker-compose is used instead with the same containers
* What is meant by spinning up new systems for a developer?
  * At times, allocating new IP addresses and other network configuration tasks are needed
  * Some use Docker in place of this for providing developers with dev. environments with custom domain names
    * HAProxy is used as a load balancer with wildcard DNS server
      * Developers can choose their own domain names
    * Containers are chosen by developers
    * Developers work in GitLab, developers work within their own pipeline
      * Changes in the git repositories trigger GitLab builds
      * Local Docker registry is used to host local Docker containers
      * Wildcard DNS, along with the HAProxy load balancer, provides developers with more of a self-service model
        * Developers request their own domain names with these new builds
    * Others use a similar approach, but with a non .edu domain they pay for to solve the “network admins won’t give us wildcard” limitation
      * (For the initial work and then register .edu eventually)
    * We run a \*.<unit-name>.libraries.psu.edu … and that’s what we have our k8s clusters running under.
* Steps to reduce the bottleneck
  * F5 or NGINX will allow developers to take a custom domain name (e. g. jenkins.library.institution.edu) - this wildcard is the \*.library.institution.edu
    * Packer will build base images for VSphere
    * Developers use the same base images to then customize their own build environments
    * Docker is similar to Packer, in that it uses base images
      * However, Packer produces an entire VM, not just a Container
* For k8s users, the goal can be to have a vanilla server environment
  * Workloads are then layered atop of the vanilla server environments

