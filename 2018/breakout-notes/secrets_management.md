## Problem Statement
What are the risks? What points of failure? How to hand off secrets without opening ip vulnerability?


## Discussion notes


What tools?
* Amazon KMS (key management system)
   * Instances (e.g. an EC2 instance) have access via roles; people don't have access
   * AWS encryption SDK can be used with KMS
* AWS parameter store
* Hashicorp's vault
* Ansible vault
* Docker secrets
* Puppet’s Hierra


How to combine with version control?


Environment variables: You have to trust the security of the operating system environment


Who are we keeping the secrets from?
* People looking at codebase on github?
* People in other departments?
* People we want to share our configuration with?


Managing ssh access
* We have a key in a private terraform repo so that everyone can access


Does anyone have a process for rolling out/retiring new keys?
* Can this type of thing be scripted or is it doomed to be a manual process?
* Moving toward temporary (think 1-hour) keys for everything
   * This can be difficult when you have to restart a service to load the new key
* Hashicorp vault
   * Temporary keys for everything
   * audit feature
* LastPass Enterprise rolling keys




Whose job is it to manage secrets?
* Trying to convince other people on your team that security is a broad responsibility
   * How do we breed developers who care about security?
   * but this leads to it being no one's responsibility
   * this is an authority issue?
* Authorizing people to enforce security practices
   * example: Making sure everyone uses multifactor auth




SecOps
* Layers of security (what level of access)
* There are people who view security as an impedance
   * At some point you have to sacrifice security to actually be able to accomplish something
   * Ease of use is the diametric opposite of security
* Making security “easy” to allow work to be done
* My own phone becomes part of my company's security policy?
   * Use a separate key
* If our organizations don't give us time to prioritize this then they're "Making the choice to get hacked"








How to make this transparent?
* Ansible-vault
* LastPass Enterprise (key management for small team)
   * granularly controlled; still have to manually roll things in and out of build services.




Managing onboarding / offboarding
* pairing with someone who has a script / checklist
* Sharing of onboarding (Alex and Stephen/NYPL) practices
* We take for granted that people who write code understand ssh and key management. This should be part of our formal onboarding process
* walk them through ssh key generation, key management, setting up github, as a pair
* have an ops person periodically pair with developers on their daily work could help surface security leaks or improve delivery of secure products
* Find where the inconveniences are. they are not always on the surface. "Mind the seam of inconvenience"
* Purchase yubi-keys for employees




Who knows what they want their system to look like but not how to get there (few)
A good system
* Want to get around not knowing the perfect by being able to rotate / rebuild quickly
* want to isolate systems from one another so they don't provide access to one another
* Ensure "this key only goes so far"
* always use multi factor auth
* Use roles vs. individual machines
* Limit exposure per each secret to a known scope
* If a breach occurs, know how to stop and rebuild
* Principle of least access without getting in the way of people: Use sub-accounts in AWS, limit what each account can do. If someone in the subaccount tries to do something they can't, they get blocked. they are confused, walk over to ops person and a conversation can take place. key to not having devs get frustrated about access is making sure these conversations can happen very quickly.
* Someone has to run these things. Because enterprise systems.
* A single tool that fits all purposes.
* could we make key generation a part of our deploy process? similar to the way let's encrypt does cert regeneration
   * let's encrypt: cert bot is a docker container that generates short-lived ssl certs as part of your build process. can use this to change ssl cert per deploy and container.


vs. who doesn't know what their system should look like? (many)
* analyze what's the worst that could happen if any given breach happens?
* Is there a strategic vision for the department in terms of policy?
* can containers help here? docker?
   * Note that if your containers are running as root, a breach of one is a breach of all.


A vision (Dan)
* Something where you can quickly change keys and they're pushed out to where they need to be
* Have secrets locked down but easily viewable, with clear diffs
* Easy for developers to see what variables are in the config vs. what variables are in the code.


A vision (Erin)
* Expirable keys
* A system that will migrate the service roles and keys that the services need themselves
* Expirable ssh keys
* one simple interface for a place to know where I'm sshing, how to mint a temporary ssh key, and get there


A vision (Cole)
* Key and secret generation / deployment is orchestrated and automated
* No one has to ssh into any box


Observation: key / secret rolling seems adjacent to the problem of cache expiration, a famously difficult problem.


SSH certificate-based access
* feature afforded by hashicorp vault
* don't have to update the instance to accept a new cert
* Can expire certs (unlike ssh keys)
* Use a central service to which you can auth via your organizations SSL, which can then give you the temporary cert


Hashicorp vault! It's very unique. Read their primer for a good philosophy of secrets management.


Let's solicit suggested readings to share with one another for tiers of secrets management, other foundational documents.


Know that compromised secrets isn't a matter of 'if' but 'when'