# Session 5 - Secrets management & Testing in Production

Proposed topics
 * Automatic Key rotation
 * Secrets management (Vault? -AG)
 * Secrets management with Rancher/Kubernetes

* Defined as: Secrets management (David) is about storing some secret and deploying them locally, dev, stage, prod and do it secretly. Use of Ansible Playbook Vaults. His organization uses a secret repository to pull/retrieve. Unable to locate location of secrets easily. Secrets were on but are now retrieved via environment.  How are folks managing in containers? K8s

* Andrew uses Hashicorp’s Vault. Were initially discouraged to do this by vendor but were able to set up much faster. Vault allows both local and Kubernetes secret management. Run the container and inject values from the Hashicorp vault storage. In K8s one can identify Vault as a source for secrets. In Docker using Consul (?) template. 
* Hashicorp has really good documentation that allows one to walk through the entire process.
* Vault has the ability to create timed sensitive passwords that expire for password rotation.
* Use Keybase encrypted git repository to store hashicorp vault passwords which initializes the vault

* Ansible-Vault and is slotted into one of the attendees build scripts. (Ansible will not work well with Docker) when they move to Docker

* Pulling from Lastpass and setting them as variables. One attendee uses `lpass` command line utility heavily on a personal basis, but could also be extended into production workflow?  Tightly integrated with their organizations Ansible workflow.  `lpass` password will open / decrypt Ansible key; when done will re-encrypt and close.

* CyberArk good for Windows based systems, but not many other systems


#### Discussion on value of automated key rotation

 * One participating institution removes keys using a calendar reminder
 * A participating institution removes from the Terraform Configurations (?)

## Testing in Production

We briefly discussed this topic due to some extra time after finishing the above
discussion.

Primarily we worked toward a definition of testing in production; discussion
also ranged over troubleshooting production errors, developing in production, and creating fixtures from
production data.

 * Initial Problem statement: a production system which stopped working because copy operation failed. Is there a mechanism to test things that assert that things actually work?

 * The pressure of a hotfix occasionally needing the change to be implemented is hard to overstate.

 * The subtle differences in Alma require making changes to production mirror and making screenshots to verify that things work then testing in Primo -- it can be difficult to replicate connections between systems (some of which may be external) into a staging or development environment, and many teams struggle to find time to make these kinds of gains toward automated / devops way of life.

 * An example of `testing in production` is getting the DB from production and then anonymize. Set it up in a “shrunk” instance. Apply fix in the instance and then apply the process to the production.

 * Earlier comment about restoring from production backup a possible solution; test there in a restored environment, and then make change in production.

 * Running actual test suite in a production environment.

 * Containerized deployment pipelines reduce the problem of testing in
   production because all environments can be the same.

 #### Miscellaneous

 * HashiCorp Vault: [https://www.vaultproject.io/](https://www.vaultproject.io/) ; Learn Vault: [https://learn.hashicorp.com/vault](https://learn.hashicorp.com/vault)
 * Hacked Private Repos in Github: [https://www.bleepingcomputer.com/news/security/microsofts-github-account-allegedly-hacked-500gb-stolen/](https://www.bleepingcomputer.com/news/security/microsofts-github-account-allegedly-hacked-500gb-stolen/)
 * Ruby LastPass gem: [https://rubygems.org/gems/lastpass-ansible](https://rubygems.org/gems/lastpass-ansible)
 * Keybase: [https://keybase.io/](https://keybase.io/)  (purchased by Zoom in May 2020)

Gatekeeped Definitions:

IAM keys - Identity management Amazon keys for users.  

