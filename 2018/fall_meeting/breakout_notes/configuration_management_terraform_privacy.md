# Configuration Mgmt

If you are doing config management, you might be doing something wrong - i.e., not immutable deploys.

Why not just use Cloud Init (bash script injection at startup time) and in a bashy way?

Something like puppet has more flexible ways.

Depending on your setup organizationally, cloud focused tools might exclude who can work with it. The Ops person becomes the blocker.

With cloud INit, you have to include the modularity, but it is possible.

But even the flexibility comes back to - why not just use Docker to create immutable containers. 

A concern with Docker is - where do you persist your images. 

IN kubernetes, you “teach” kube how to do persistent storage, and it alots the storage when needed.

In kube, a deployment is a data model for the the infrastructure.

But in order to take advantage of this, you need a infrastructure that can handle it.

Erin would be nervous running a DB in Kubernetes

PSU is running a DB in docker in Kubernetes

So, for those doing config management, are you treating them as immutable?

Princeton is kind of doing it immutable - using packer to create a base image, and then deploying. Running on a cron to keep things in a certain state.

## Ansible
One of Ansible’s real benefits is the low level buy in. Makes it easiest. 

Ansible tower - a UI front end for Ansible - allows setting user permissions, running cron jobs, etc.


AWX is the free version

AWX can be configured to send API calls to Github or Travis to farm out tests

KInd of Like Foreman for Puppet (a UI for puppet)

Temple is running Ansible playbooks from Jenkins



## Terraform
Kustomize.io - terraform style 

NYU using it for VPCs, Load Balancers, Auto-scaling groups

Feature set of Providers is different based on the provider. AWS is fully featured.

Terraform has a local or remote exec option to run commands after the terraform configuration has run.


## Testing

You can test individual components, on Travis

Example - https://github.com/geerlingguy/ansible-role-solr/blob/master/.travis.yml

You can test builds after they have been created, like GauntLT  and ServerSpec

These kind of test are more like Integration Tests, they test the API through which other components will integrate with the role or component.

There is a python example - https://testinfra.readthedocs.io/en/latest/


Molecule - Python based library for testing ansible roles and playbooks

Mozilla Observatory will check SSL config

Only a few using CERTbot

### Privacy

Connecticut Public Library has details of patron usage of computers by FBI. Resisted, and eventually FBI relented.

Is this still possible when we are shipping out data out to external vendors? 

Maybe don’t ship most sensitive data outside local servers?
Use alternatives to Google Analytics, like Matomo - https://matomo.org/blog/2017/01/11-ways-piwik-analytics-helps-protect-visitors-privacy/

How do you handle things like EzProxy - turns out EZProxy logs file format can be altered to be less identifying?

Can be really hard to move forward when you don’t have support of administration.

Bringing it to the attention of others who may be interested, like rabid privacy librarians, can help.

Is there a pragmatic balance to to strike? Data retention schedule can be useful about this.

Important patterns are to to make sure that data is 
encrypted in transit 
Encrypted at rest

Doing research on providers can be difficult, as it can easily go out of date
