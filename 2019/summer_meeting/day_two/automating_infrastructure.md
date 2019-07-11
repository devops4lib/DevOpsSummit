Note taker: Patrick Galligan
Timekeeper: Daniel Sanford
Gatekeeper: Cole Kettler

### What are people doing right now?
* For everything on Heroku we use their automation and it's great
* Most of the rest of the stuff is on AWS, using terraform
  * Automating some of the AWS build in Ansible, e.g. bucket creation
* A few VMs have no automation and that is one of the main reasons they haven’t been migrated
* Uses [Terraform](https://www.terraform.io/)
* Princeton builds VM images using [Packer](https://packer.io/)
  * Creating a template through either VirtualBox, but Rockethey’re using less and less as Ansible work is getting better
  * Ansible takes over standing up the infrastructure after VirtualBox
* Francis is using Terraform with DocNow because it can build across different clouds (Azure, AWS, etc.)
* Yale Center for British Art is mostly using the GUI
  * Had a question about what advantage automation would have for setting up something like Solr.
* Everything at U Penn on prem with Ansible but thinks the VMs are created by manual processes
  * Sees themselves moving more towards using AWS
  * Mostly working through images and manual configuration
* At Penn State they use [Chef](https://www.chef.io/solutions/devops/) to build the infrastructure
  * Provisioning framework
  * Runs over and over and tracks what your server should be and will fix any unexpected changes
  * In the same space as Ansible or Puppet
  * Can be difficult to actually find search results relevant to the work

### What exactly do we mean by automating infrastructure?
* Automating provisioning vs. automating infrastructure itself
  * Infrastructure is creating your box or cloud services
  * Does putting a docker image in Swarm count as provisioning or infrastructure? If Ansible is provisioning, is Docker step two?
  * Thinking about infrastructure as everything that happens before you provision
* Tools to use to actually automate the infrastructure
  * [Kubernetes](https://kubernetes.io/): What you’re getting is a place to deploy your containers. Argument is that having the Swarm or Kubernetes is part of the infrastructure.
  * Would love to have configuration as code that configures a Kubernetes cluster
  * Docker has taken a load off of their initial provisioning work
  * Terraform gives DevOps a method to put in pull requests to set up infrastructure
    * If I need to run a Docker container in Fargate, can look at how someone’s already done that and set up a section in the Terraform repo
    * Have a place to run containers without having to wait for new VMs
  * Packer for building images and using Ansible to configure it
  * If you don’t already have any automating provisioning, Ansible is probably the place to start. It’s what a lot of people are using and it’s fairly easy to start
* Configuration
  * Bundle install as part of a deploy step

### What is the benefit of automating infrastructure?
* Specifically speaking about automating Solr
  * Label hosts with metadata using Ansible so that the Docker containers know what it needs to do and make sure everything is where it needs to be
  * Prep work done before handing it over to Docker Swarm
* Integrating capistrano with AWS build
  * AWS build process applies tags to machines for [capistrano](https://capistranorb.com/) to use
  * Makes it easier for updates and deploys
* What’s the Buy-In?
  * The benefit to automating even the simple tasks is that you are freeing yourself up to let others do specific jobs. Frees you to leave, take vacation, create redundancy.
  * Others could respond to incidents and help out if you are not immediately available
  * If you leave your job, the next person will know how to keep things running
    * Someone will know they can stand up anything with just a few commands
    * If you eliminate the toil, others can start critiquing the decisions rather than working on the manual work and hopefully improve the decision-making
  * Want to be able to say that if you have it all automated, you can re-stand everything up within a short amount of time as long as you have the money to pay for it
  * Automation documentation is a good way to show what DevOps does and increases transparency
    * Infrastructure as code acts as documentation, especially since it’ll break
  * Ansible gives you a lot of flexibility to recover and redeploy in major incidents
  * Automation can help prevent vendor lockdown

### What are people’s goals and hopes and dreams in this area?
* Would love CI/CD to be more robust at Princeton
* Wants to moleculize more of the roles
* Wants more uniformity in the Ansible roles because some of the older ones feel more monolithic compared to the newer ones
* Wants to move to Hybrid cloud by incorporating AWS into our infrastructure
* Would like to move to Cloudformation
* Would like to see more testing as part of MIT’s next steps. Would like to consider refactoring a lot of their code in Terraform because past abstractions actually made it more difficult over the long term

### What pain points are people trying to address?
* Shared configuration changing the url and knowing whether you have to deploy to other servers because Solr changed host, for instance
* Can’t deal with adding people that don’t have the highest level of server permissions and provisions from outside of the team
  * Feels like going to “neutral territory” like AWS and set up security permissions would do a lot to solve that
* Biggest pain point in moving to Amazon was getting taken out of a sandbox so they could actually send more than 50 messages
