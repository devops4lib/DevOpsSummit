Ansible for Deploys to replace scripts
Best Practice
Model for transitioning to it?
Ansible-Vault
Not necessarily self-documenting
In-line vault - have variables defined in a file and then have them fit into other files as needed
Inheritance chain
Two levels of variable inheritance set-up ie env staging vs production, role - solr, database, etc

Temple reuse “roles” across “playbooks”
*Roles - a resuable chunk of deployment
*Playbooks - set up for each application and can pull in multiple roles

Vagrant box is included with ansible configs for testing out playbooks before deploying to staging and production environments

Pulling in from externally managed/maintained roles
One strategy is to have less general roles to not be dependent on other role maintainers

Ansible “meta” feature - check to see if a role was run might be harder to maintain

A goal/benefit to Ansible is that it’s more readable, but it depends on how roles/playbooks are defined

https://github.com/pulibrary/princeton_ansible

How frequent to deploy/run ansible-playbooks?
Autodeploys can be triggered/tracked through Git and pull requests, test in staging environments

Princeton has a mix of machines that are fully configured through Ansible and ones that are approaching that level

Updates - should be idempotent (added note: It is very possible to make them non-idempotent by mistake)
For each role - use travis and docker to build and run a second time to make sure it’s consistent
Example - https://github.com/tulibraries/ansible_passenger-apache/blob/master/.travis.yml

Build servers on aws to test out playbooks

Having a couple of base images could speed up deployments/setup for basic components like java or ruby installs

Phasing into an ansible system
Destroy servers and restore from backup
Create a playbook to mimic the environment of an already running application and add have them run in load balanced environment alongside existing servers

https://www.ansible.com/products/tower
https://github.com/ansible/awx

Relying upon external roles can cause problems sometimes, like the mysql one
Versioning of the roles isn’t the best in Ansible

Nightly ansible builds could help with preventive maintenance
Maintaining your own roles lessens the danger of unexpected updates

Ansible can also be used for desktops / laptops to help set up developer environments.

Could Ansible be used for responding to security incidents?
