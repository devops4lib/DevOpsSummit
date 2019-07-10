Note taker: Francis
Gatekeeper: Nikitas
Timekeeper: Dan


### When to / not to use containers
* Like them when there's a complicated dev stack. 
* Frustrating when `compose up` wants to rebuild the local app every time. Becomes time consuming.
* Don't like: docker containers add a build step to a process that doesn't always require one.
  * In particular, rails is tricky to build efficiently. Currently recommended to run a ruby container and 
* Don't use if you don't have time to make it all work right.
* Use docker after you have CI, external (build) artifact hosting -- until you're using this set of tools it doesn't make sense to use docker.
* With a very small team this might go beyond the bandwidth of the team to maintain or support.
* If you're having reliability issues with your application/s going down this path will force you to reckon with them.
* Can end up worse off if you don't put in the time. Hard to spread use of docker beyond a highly-trained, committed team.
* If you're administering enough machines to outgrow puppet you might want to use containers, orchestration.
* Kubernetes networking is complicated. You can't get an IP address for everything, e.g.
* The documentation is copious and confusing; a lot of it is out of date or partially out of date. Assumes you know everything and nothing at the same time.
* You should already be developing 12-factor applications. E.g. you can't assume the same filesystem will be there for your crons as for your applications.

### What containers are we using?
* Docker: Most people are using
* Docker, swarm orchestrated
* rkt (pronounced: rocket) for Kubernetes

Swarm brings up containers, replicates them, monitors them, DNS service discovery, communication between nodes, configuration mounting.

### What's the sell for developers?
* I can run a full stack very easily as a developer
* If I work on that application a lot I don't use the build setup, I just point my develop my app at all the running containers, then test it in the docker container when I'm done.
* Trying to always use the full docker environment for development leads to config drift
* Containers can enable a deployment process that allows for easy deployment, rollbacks, version tracking.
* Rolling updates with zero downtime. Developers used to batch big releases.
* When you're using containers your development process can integrate QA by providing a fully operational version of your application with each PR. E.g. No more "Staging Server" because there's a staging server with each PR.

### Integrating with developer workflow
* Who is taking care of docker? Systems folks or developers?
* You can get to working quickly, but you may not be doing it well / efficiently 
* It's been sold as something that makes operations easy, but that's false.

### Orchestration
* If you're using containers in fargate (you can put your container there but it doesn't orchestrate). What do we do now?
* Swarm vs kubernetes may be a personal matter -- one may make sense to you while the other is confusing.
  * Swarm does have limits at a certain point that are making us consider moving to kubernetes
* Use Rancher as your training wheels to use kubernetes. It has a GUI and makes it easier to visualize / learning what's going on.
  * Rancher is a kubernetes management cluster that has a CLI but as you're trying to understand the different moving parts it has a clean way of explaining all the elements of kubernetes and how they communicate.

### What's the use case for multiple kubernetes clusters?



### Amazon's managed kubernetes?
* I want to not run the cluster but just get the benefits of it. (EKS: elastic kubernetes service)

### What I wish we did: 
* Configuration management on our docker host instances
* Version Control
* Monitoring
* CI/CD 
* Comfort with microservices architecture

It is much easier to keep things in sync in a container cluster 
Kubernetes documentation changes frequently

https://quay.io/ 

Honor the 12 factor principles when adopting containers

### 2 skill sets:
* Building containers
  * Takes a couple weeks to figure it out
* Running containers
  * Steeper learning curve if you don't have experience running distributed systems; machines have numbers not names, etc.
