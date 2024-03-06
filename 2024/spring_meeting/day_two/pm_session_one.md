## Containerization/Orchestration Tools

Roles:
Facilitator: Andrew
Notetakers: Francis, Jeremy
Gatekeeper: Mike

### Session Outline Request:
 * Group: Containerization Orchestration Tools (12)
     * Podman / Docker / Colima
     * Kubernetes
     * Docker Swarm
     * OpenShift
     * Others???? (Nomad)
     * Containerized Application Environments (K8s [Kubernetes], Docker Swarm, Etc.)
  * Notes:
  * Containerization
      * WHY containerize?
         * Set it up once, not constantly
         * Repeatability
         * Scaling
         * Handle dependencies consistently
         * Everyone is doing it? Is it our responsibility to make sure our staff has the skills necessary to excel in the market
         * Immutable instances. If an application misbehaves, just redeploy it.
      * Tools
         * Podman
             * allows (requires?) you to run containers without root
          * Docker
             * docker-cli
             * Licensing concerns introduce uncertainty when using Docker for Desktop
          * Colima
          * Rancher
    * Orchestration
        * What is orchestration?
            * Allocation/apportioning of resources
            * match production deployments to available resources (nodes)
        * Tools
            * Kubernetes
            * Docker Swarm
            * capistrano is an orchestrator for code deploys
            * Docker Compose
                * Connects multiple containers to work together (often on their own internal network)
            * Lando (uses Docker Compose under the hood)
        * Where are the nodes?
            * the cloud
            * your own kubernetes cluster on premises
        * Deployment with an orchestrator
            * the container is created, tested, and distributed to different nodes. The new containers and old containers run at the same time. Once the new ones are good, the old ones are turned off one by one.
        * What is the scale at which orchestration becomes a necessity?
            * Depends on the features of orchestration you are interested in
            * Zero downtime deployments (not exclusive of container based deployments)
        * DNS is handled differently
            * orchestration tool has its own set of DNS and IPs that it manages?
        * Example: I run independent containers on aws lambda
            * we’re not coordinating a bunch of containers with one another
            * is it useful to think of this as orchestration, even if it technically is management and deployment of containers?
              * Probably not
        * I worked at a company that used container, used rancher, etc, and it was so complex and undocumented that i felt like I had gone back in time
            * there were 5 different ways of setting up a system in docker compose
            * 5 different ways of getting it onto rancher
            * it did not feel like progress
            * Any technology needs to be implemented with conventions and consistency
        * example: If I name my branch ‘feature/whatever’ then it gets deployed to a qa environment and i can play with it before it gets merged
        * I don’t think I am doing a good job taking notes, other notetakers?? You are doing great but also I’m not. :D
        * There are lots of options for orchestration. K8s is just the most common option due to who was backing it.
        * There is a lot of complexity. Can small teams successfully do k8s? Should they?
            * If you don’t need the features, you don’t need the solution.
        * What are the light versions of kubernetes, for those of us who know we don’t want that level of complexity
            * One person has used the ubuntu implementation
                * Microk8s from Ubuntu
            * k0s, k3s - these are tools that do the same thing as kubernetes, but are smaller / lighter weight (that’s what the numbers signify)
            * I use k3s at home. with k8s there is so much tweaking you do, these light versions use an opinionated approach, e.g. you can only use traefik
            * Convention over configuration helps these simpler solutions easier to have less config options (rails-like)
            * kamal is apparently a new thing rails is doing, to deploy containers
        * Some service providers are allowing for more efficient pricing by only running containers when they are requested
        * Orchestration options handle secrets management fairly well