# Configuration Management - 10AM

## Tools
* Ansible - 10
	* Low learning curve, easy to jump into
	* Can refactor easily later on
	* Doesn't require agents (just uses ssh)
	* Ansible Tower - Logs all playbook runs, etc.
	* Ansible Galaxy (like Chef Supermarket)
	* Ansible Vault
	* Not idempotent
* Chef - 1
	* Very puppet like - Ruby DSL
	* Does not use database, rather compiles
	* Option of using Habitat instead of Capistrano
	* Option of using Inspec for compliance
	* Uses Berksfile like Gemfile
	* Has integration with (basic) Secrets Management
	* Has a supermarket for shared recipes
	* Idempotent
	* Chef Automate (like Ansible Tower or Hashicorp Terraform)
	* Chef Supermarket (community recipes / code)
	* Chef Vault
	* Idempotent
* Puppet - 5
	* Master / Slave
	* Push setup
	* Database backend to store configuration
	* Can use certificate authority
	* Mcollective (messaging thing)
	* Idempotent
	* Puppet Forge

## Commonalities - Tool agnostic stuff
How granular should our best practices be?
* Roles
* Environments
* Overriding Recipes / Playbooks
* Scalability
* Secrets Management (if managed, could be easier to share code with community)
* If we have community standards behind DevOps, we could reap:
	* Boiler plate text for Grants, e.g. - We use [standard] for our infrastructure (the standard being a multi-institution thought out document)

## Roles - What are best practices? (possible most sensical roles:)
* ruby web app box
* java web app box
* database box

## Other things
* Use Jenkins to trigger Ansible runs
* Terraform - Stand up AWS/GCE network, security groups, etc
* Drying out code can increase complexity - Tension between leveraging community code versus simplicity of reinventing the wheel?
* What forces branching of code?
	* Centos 7 vs Centos 6
	* rhel based vs debian based
	* Fedora 3 vs Fedora 4
	* Targets
		* GCE
		* AWS
		* bare-metal
		* other / mixture
* There is a trust issue with pulling from communitiy sources (pulling docker images or community recipes/playbooks)
* Great strength of containerization is it forcing you to be up front about dependencies
* Documentation about existing applications which follow best practices could be a good guide for smaller teams?
	* Might also help show what the benefits are of using some of these best practices.
* We've been talking about community best practices, but is there room for conversations around legacy projects?
	* What is an application vs a service?
* Puppet isn't great about being able to leverage different repos, tends to really want you to centralize into one repo.
* Ruby 5 will be able to do encrypted secrets natively. Calls into question, where should secrets live?
* Can we move past provisioning? Do folks need help building up bare machines?
	* Some folks use Packer for this purpose. Works okay but there are issues / conflicts.
	* Docker solves issue of being able to rebuild machine from scratch.
	* Where we meet is when machine is ready for configuration (networking, etc is complete)?
	* There are different immages to start from where not everyone will use the same stuff.
	* There are different baseline utilities / configurations where not everyone will use the same stuff.
	* Best place to start is after provisioning, and having a box ready for configuration management.
* Twelve Factor App - https://12factor.net - helpful for understanding separation of concerns for apps/devops
* If we can separate out our secrets from our codebases, it becomes much easier to share our code with each other.

## What we could do:
* Decide on most common roles (e.g.:)
	* web
	* database
	* jobs
	* etc.
* Write pseudo code for roles to be implemented into specfic tools:
	* ansible
	* chef
	* puppet

## Let's start talking about specific commonalities!
	* MySQL, Postgres, Oracle, MSSQL
	* Application 
	* A firm dividing line is putting components that could conflict (in terms of resource utilization) in different roles (if not VMs).
	* There is an overlap between topology and tuning. Decoupling roles may a single large 'tune' operation.
	* We should makes sure that the best practices we design can be used by institutions with slim resources (technological or human). The effort we're on should support that by really doing a lot of the planning work up front.
	* Are messagng clients separate from databases?
	* Cache layer? Memcache? etc
	* Limitation of clusterization or architecting with containers is: Storage. Still has to be local for some people? Would backup be a resolution?
	* persistance, storage, mempower, etc
	* The conversation of moving from configuration management to roles to containerization is a mirror of what has already happened in the software development world.
	* Systems thinking versus modular thinking? At which place do we need to worry about what responsibility?
