# Automation (Afternoon Session One)

* Facilitator: Francis
* Notes: James, Anna
* Gatekeeper: Andrew

## Notes
* Automation: (Defining from the earlier notes)
    * [https://docs.google.com/document/d/1fR_mSeciXx3HAEBaK2jf1uk0DpGtSInr2zzfnGkND1I/edit](https://docs.google.com/document/d/1fR_mSeciXx3HAEBaK2jf1uk0DpGtSInr2zzfnGkND1I/edit) 
    * deployment of webapps
    * Ansible
    * Ci/Cd (Continuous Integration/Continuous Deployment)
    * Dev to prod pipelines
    * Deployment of webapps
    * 
* Thoughts about automation?
  * How many are using Chef?
* Does anyone have an automation problem which they are looking to solve?
    * Bess: Vendor-provided software which we are required to develop a front-end for this
        * Looking to request a Docker Image for a proprietary back-end in order to support continuous integration
    * How do I get started with automation? I use docker locally and in production, but we’re moving to something else for production, maybe podman (_this question is returned to later_)
    * Are there Container users who use automation?
    * GitLab provides automation tool suite
        * Comes with a built-in CI/CD suite of tools
    * GitHub Actions used to build up Containers
        * These Images are then published to Amazon Web Services
        * Orchestration is not used
        * Amazon Fargate is used (this is used to run the actual container images)
    * An organization is using Travis CI, and is currently undertaking a migration to GitHub Actions
        * CodeDeploy is a hosted service which is used to automate deployment to server infrastructure
        * Amazon Web Services ecosystem is also used heavily, and integrated into automation workflows for various organizations
* Getting Started with Automation
    * Automated tests are a great starting point
    * Currently, some may have tests which are run locally by developers
    * Start by measuring test coverage. put in tools to ensure you can’t change the code without increasing coverage or at least keeping it the same. Ensure that tests always run before it can be merged.
* Automation for Development Environments
    * Setting up Django (Python) web applications locally for development, but with increased automation
        * Try to avoid the manual labor of creating virtual machines and database servers
    * This is not for pushing any applications into the production environment
    * (Re)learning Ansible comes with a steeper learning curve
    * **VM templates are very valuable here**
        * VirtualBox provides this, and this saves time on builds
        * Also, Vagrant (which can wrap VirtualBox) can be of value here
    * Shell (Bash/ZShell) scripts are also automation tools which are valuable
    * Language environment tools ([asdf](https://asdf-vm.com/) or [https://github.com/jdx/mise](https://github.com/jdx/mise)) can also automate
        * Configurations which are parsed by these tools can be tracked within the git repository for the project
    * Docker-based tools for development environments ([https://lando.dev/](https://lando.dev/)) also exist within the open source ecosystem
        * Suggestion: Explore replacing Lando with DDEV ([https://ddev.readthedocs.io/en/stable/](https://ddev.readthedocs.io/en/stable/))
        * More advanced features involving the state management and Docker environments for the containers running the services
    * Django community also offers a Docker Compose configuration which assists with the automation of bootstrapping a new application
        * [https://docs.docker.com/samples/django/](https://docs.docker.com/samples/django/) 
    * MacOS and Docker
        * Docker Desktop, Rancher for Desktop ([https://rancherdesktop.io/](https://rancherdesktop.io/)), Colima  ([https://github.com/abiosoft/colima](https://github.com/abiosoft/colima))
        * Podman ([https://github.com/containers/podman](https://github.com/containers/podman)): Renames the Docker infrastructure
* Containers within Linux Host
    * One organization runs containers within a Linux host for production environment
    * Hence, for development environment, a Vagrant configuration mirroring the production environment is provided (Vagrant virtualizes Linux host, which, in turn, runs the Docker containers)
* Debugging within the local deployment environment for IDEs such as RubyMine is a requirement
* Please recall: each layer within a given suite of automation tools is added subsequently over time
    * Automation may simply start with one shell script, and grow over time
* Automation for small teams:
    * If for new employees during onboarding, more than 2 days are required to understand and follow the automation process, then this approach may be problematic
    * Developers should be familiar enough to understand what is being automated within templates for a tool such as Ansible
        * They must be able to understand whether or not Ansible or some system service (e. g. NGINX) is actually breaking during an error
        * “Just enough automation”
    * **Undocumented automation is a potential disaster**
    * 
* Who’s running big ETL processes in AWS lambdas?
    * [https://aws.amazon.com/step-functions/](https://aws.amazon.com/step-functions/)
    * Batch nodes orchestrated via kubernetes, on prem. Argo ([https://argoproj.github.io/workflows/](https://argoproj.github.io/workflows/))  is used to run scheduled jobs.
    * GitOps as a methodology employed by some: [https://about.gitlab.com/topics/gitops/](https://about.gitlab.com/topics/gitops/) 
        * Creating releases within GitHub or GitLab, this triggers a release within the production environment
        * Pushing branches may also trigger certain deployment actions
* KBART (Knowledge Bases And Related Tools)
    * [https://www.niso.org/standards-committees/kbart](https://www.niso.org/standards-committees/kbart)
    * Processing and validating files involves processes which may be automated
        * Has anyone implemented or adopted a tool which automates these processes?
* ETL Automation
    * Sources for Extraction:
        * Export MARC-XML from Alma (ILS)
        * Harvest OAI-PMH sources (multiple DSpace instances)
            * OAI-PMH ([https://www.openarchives.org/pmh/](https://www.openarchives.org/pmh/)) 
            * protocol for metadata harvesting
        * LibGuides
        * Harvesting from geospatial sources is not currently supported but will be in the future (OpenGeometadata is named)
    * Harvesting Tools
        * Docker container which wraps a Python tool
        * Command-line tool
    * FTP Server
        * This integrates with Amazon S3, and runs constantly
        * 
* Containers in Deployment
    * Some prefer to avoid using SSH or tunnel into a virtual server or Docker container in order to actively edit the code base
        * Code is edited within the local development environment, and the VM or Docker container mounts a file share with access to the code base
        * Still required to use SSH to access to VM or Docker in order to restart system services (e. g. NGINX, Apache, PostgreSQL)
    * Mutagen
        * [https://github.com/mutagen-io/mutagen](https://github.com/mutagen-io/mutagen) 
        * Syncs between Docker container filesystem and file system of the host
    * Dev Containers
        * Spec for VSCode (and other code editors)
            * [https://code.visualstudio.com/docs/devcontainers/tutorial](https://code.visualstudio.com/docs/devcontainers/tutorial) 
            * [https://github.com/devcontainers](https://github.com/devcontainers)
        * Looks like the app or website is running on some private cloud
        * How is debugging approached for this?
            * Code editor must have access to the port (XDebug uses port 9000)
    * Makefiles
        * These can also be used for wrapping commands and provide transparency for accessing
        * Also ensures consistency when testing code bases (`make test`)
    * Docker in Vagrant
        * When the Vagrant VM is running Docker containers, multiple layers of port forwarding must be supported for interactive debuggers
    * Several Ansible Roles might be used to isolate automated processes when provisioning a new environment
        * Ansible provides Inventories, which permit to have Roles configured for different environments
            * An Inventory for production is separate from the staging Inventory
            * Both will exist for a given PostgreSQL Ansible Role
            * In one approach, each Ansible Role is used to provision Docker containers
                * The Docker container image will be versioned differently based upon the Inventory used
        * This may also be managed using a selection of scripts
* Most Common Components for Applications used in Automation
    * Apache Solr for Blacklight
    * Some are considering migrating from Rails who have heavily invested in this framework
        * PostgreSQL should replace MySQL wherever possible
        * Automation for Rails applications is currently easy, as one specifies different environment variables during the deployment process for different environments (prod/staging/test)
    * PHP Projects
        * PHP standalone is different from PHP for content management systems (e. g. Drupal)
            * With Drupal, the community provides solutions for Docker containers
            * Layer additional configurations upon the Drupal community container
* Orchestration
    * Kubernetes, Fargate were mentioned
    * Is anyone using HashiCorp Nomad?
        * (No)
        * One considered Nomad years ago, but at the time, there were licensing issues with using the software on server infrastructure

_(Session concluded at 13:43 EST)_