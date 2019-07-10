Note taker: Patrick Galligan
Timekeeper: Francis Kayiwa
Gatekeeper: 

## General topics (start with 10 minutes each):

### Vendor lock-in
* Problem statement: Using AWS is great for a lot of things, but using a lot of built-in services makes it difficulty to leave or migrate to other services.
* If you’re designing something to work with AWS primarily, you might have a little flexibility in moving specific pieces? But it depends on how the process is created (easier with a microservice approach maybe?)
* There can be conceptual mismatches between different cloud service providers, especially on a more abstract level
* In enabling parts of an application to migrate between systems, it's very much a developer's job to build in insulation layers (also useful for testing)
* If you can mock something locally with fake S3 and then deploy it, it’ll be easier than deploying straight to the cloud
* Each individual component could be easy to move out of a vendor, but if you try to remove the entire process out of AWS, it could be super difficult
* Is it the application itself that’s locked in? Or is it the infrastructure itself? Often the operations and automating the setup can make it harder to move from one provider to another
    * Terraform is specifically written to deploy to specific provider
* In theory you could deploy across cloud providers as a form of redundancy
    * Could be expensive and time-consuming
* In a sense, the goal is to make migrating from one cloud to another really hard, but not impossible
    * Are there people concerned about this in our wider organizations?
    * Is the time scale of potential change such that we need to be ready for moving on a dime?
    * Migration planning maybe should be an essential portion of application deployment infrastructure
* Conclusions: 
    * Vendor lock-in is real, and creating an “escape-hatch” is important during planning.
    * Custom weird little things you should be a little more worried about / consider not using
    * How far up the chain do people understand what vendor lock-in means?
    * Two kind of lock-in: commodities lock-in and application lock-in. The application lock-in can be scary and painful.

### Cloud agnostic implementations
Problem statement: How to create an “escape-hatch” in your code to plan for migration.
* Use a library that abstracts, e.g. storage (instead of writing directly to S3).
* Generic API with multiple implementations and running it just has different configurations
* A lot of the abstraction might come for free depending on the specific application (for instance, Rails can do some of this already)
* The easy abstractions are already done; you can abstract file storage at multiple levels, but it’s the harder ones that get really bad (esoteric projects like machine learning libraries and process messaging)
    * Only bite the bullet when you have to
    * Some of the smaller existing abstraction libraries get abandoned because they don’t always reach a “critical mass”
      * Maintenance is important to consider
    * Not necessarily standardized, which has to become part of the consideration
    * Does the value of implementation outweigh the risk of something going away?
* Should the escape-hatch part of the design?
    * Migration planning should be part of the design process
    * Start with the concept of how much it will cost to react and move away?
* Examine all of the internal and external dependencies before creation/deployment
    * Hopefully built into the architecture phase
    * Isolate the dependencies and list them out
* Isolate risky applications so they are easier to remove and replace if necessary
* There’s a cost to avoiding the specialized features and boutique services
* Conclusion
  * Always be abstracting

### Integrating cloud or migrating from on-premise implementations
Problem statement: Using applications that could integrate with both cloud and on-prem services?
* On premise is still a vendor; you’re your own vendor
* Trying to avoid locking yourself into your own hardware
* Hybrid cloud solution can get expensive with the data-in and data-out fees
* Can run into pushback to moving to cloud for security or legal reasons
  * If the NSA/FBI/etc are moving to the cloud, is security a fair concern?
  * Threat model is different and it’s important in making an argument between cloud and on-prem. On-prem is just another vendor and cloud is just someone else’s infrastructure

#### When to use on-prem machines:
* When you have really big files that will take a long time to transfer over the network (like video archives)
* When you have files that you never let see the light of day
* Users that are primarily local can lend itself to on-prem use because you’re going to have less need of cloud. They can continue to work if internet goes out (although balance with likelihood of local server going down)
* Local machine may be less reliable than “the internet”, but you may be able to fix issues quickly
* When your mission doesn’t align with cloud principles
  * Trust model is different in the cloud
    * We think something is good until it’s not, but sometimes it’s not well-audited
  * Privacy is paramount sometimes

#### When to use cloud:
* Competency and ability to ensure uptime
* Reliability in general

#### Architecting an application that uses both cloud machines / services and on-premises machines.
* Lack of fixed IP addresses working with the cloud can be an issue
  * Local firewalls can cause issues
* Example: Backups of digital repository onto amazon glacier
  * Works well -- 1-way flow of data. Designing an automated workflow around this.
* Using a set of generalizable tools that can point to the cloud or a machine can help you assess how to move forward
  * Using object store, even for local storage, can help you migrate either into or out of the cloud
  * Mirroring cloud systems and tooling into a local system can make it easier
  * Set up local architecture to look more like the cloud will make decisions easier
* The cost of cloud shapes a lot of the architecture we end up using
  * Film archives doesn’t work given the size of AV archives
* Example: Migrate things to the cloud for public use, but transcode video
* Need to decide upon an acceptable level of redundancy when deciding to keep data on-prem
* Easy to get to "unsustainable cloud data densities" even without film e.g. research data.
* Running your own storage, while it might be cheaper, isn’t free
  * Opportunity cost of personnel
  * Human labor costs
* It can be way cheaper to go cloud if you have higher than normal storage rates
  * Most of the costs were done on Isilon
    * Not enough analysis was done on whether everything on the Isilon really needed that level of guarantee
* DocNow has a hybrid, and Azure allows them to coexist between
  * Pain point became the egress/ingress points for their infrastructure
  * Constant traffic between local and AWS can drastically increase costs
  * Understanding AWS billing is a skill in and of itself
  * Bringing in a consultant that can tell you why you’re being billed for something can be helpful
* Central IT doesn’t generally bill for data, so it can be difficult to anticipate and understand what the cloud costs will be
