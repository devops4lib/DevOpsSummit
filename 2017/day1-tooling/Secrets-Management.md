# Secrets Management
* Patrick
	* Any file that has a credential is copied via configuration management from a mounted NFS share to the needed location.
* Chad
	* Ansible vault
* John
	* Ansible vault
	* Pain: devs handing api tokens (etc) through side channels rather than commiting them themselves.
* Jeremy
	* Legacy applications, secrets are in 
	* On premise
	* Lastpass stores Yaml files
* Francis
	* No system in place for secrets
	* Green field
	* Looked into ansible vault.
	* What to use for things that are not part of an Ansible repo?
		* Was going to use a sprint to investigate Hashicorp vault.
	* Hashicorp vault server
		* Pain points
			* In order to do inital launch requires two concurrently needed keys
			* When are we going to need those keys?
		* Will be using Hashicorp vault for sure.
			* Feels Hashicorp Vault is really solid, very good product.
		* There is a Vault Enterprise, but it is largely open source.
			* Can work with LDAP, etc
* Brandon
	* Not many server administration passwords
	* More about a few people knowing passwords by memory
	* There is a level of auth already by needing to log into the central auth before getting to other credential logins.
	* Uses box for storing passwords in text (protected by central auth)
	* Text does not provide any information about what it's for.

## Stories
* How does Hashicorp Vault work?
	* Install server (as S3 server)
	* Anyone who needs a password would need to install vault client.
	* Based on keys.
	* Access control kicks in, either for user or environment.
	* Vault has an API - Ansible / Capistrano would get value for variable through API call to Hashicorp Vault.
	* Will allow for randomized keys/credentials.
	* Advantage of Hashicorp Vault over NFS:
		* Don't have to manually edit files on NFS
		* Can spin up multiple machines (automagically to handle load) and have individual passwords per machine rather than one set for all machines.
	* "You get me!" - Hashicorp seems very well thoughtout and designed. Easy to grow into.
* How to campaign for shifting from local control to remote control.
	* Chances are you already have tons of stuff on AWS!
	* Wouldn't security be greater at Hashicorp than local academia infrastructure?
	* If bad things happen, wouldn't admin understand that breach was on infrastructure more secure than local?
* For people who use Ansible, how do you end up storing something in vault where you need `sudo` or some such.
	* John
		* Use `kickstart` user, use -k for sudo password. Can do `become {user}`.
	* Kieran
		* Use `build` (ansible) or `deploy` (capistrano) which already have ssh key privileges and also have `sudo` privileges on the box vi `visudo` (via `become {user}`.
* Very handy things:
	* Adding issue numbers to commit messages. Great for github, good for jira. Also helps when having a space for issue number in pull request template.
* Very Unhandy things:
	* Service Now. (Round of "oh god no, please no, shoot me now"s).

## What are the kinds of secrets?
* API tokens
* User credentials
* SSH Keys
* NewRelic login
* Lastpass Enterprise

## Tools
* Hashicorp Vault
* Ansible Vault
* NFS mount
* Lastpass Enterprise API
* VMWare Fusion - Whatever is built locally can be built remotely (ESIx)
* Packer - Can build vmx profiles which can be built on VMWare or VirtualBox
* Github - Has a CLI called "Hub". Mixed reviews
* There is such a thing as Pull Request Templates. Can be managed through "Hub".
