# Containers

## Containers In Development

Advantages include spinning up multiple instances of an environment side-by-side.
Trying to also use it for "QA":

(e.g. spinning up containers locally and using ngrok-like tools to expose them.)

A good fit for people who had been using VMs in the past.
But an advantage of containers over VMs is the the ability to use a [docker-compose file](https://docs.docker.com/compose/compose-file/) to string together apps
that have to communicate with one another. (e.g. A web application and a solr instance).

We talked about [multi-stage builds](https://docs.docker.com/v17.09/engine/userguide/eng-image/multistage-build/)
as a way to get a `Dockerfile` to possibly work in both dev mode and production mode.
Temple is also doing this by merging/layering `docker-compose.yml` & `Dockerfile`s.
Here's [an example](https://github.com/tulibraries/tul_cob/blob/master/cli.docker-compose.yml).

We talked about using Rake files to hide docker commands from folks who may not be comfortable with it.

## Containers In Production

Penn is running production Docker.
We talked about the difference between [Fargate](https://aws.amazon.com/blogs/aws/aws-fargate/) vs traditional/EC2-backed Amazon ECS.

We also talked about [Kubernetes](https://kubernetes.io/).
And it's orchestration - which, compared to ECS.
Kubernetes is supported by Google Compute Engine & Azure.
Coming soon to Amazon.

## Other

* A discussion about how much better the Docker experience is with regards to VM
for OS X user than it was a year ago.

* We talked about how `docker attach` is a way to view `STDOUT` of a running instance.

* Found out that writing your code to Dockerizing an application forces you to be a good [12-Factor-App](https://12factor.net/) citizen.
