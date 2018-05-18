Terraform
Configuration management for cloud services. Can also be used for on-premise stuff (e.g. VMWare) -- but this can be considered "on-premise cloud services".


“Chef, Puppet and Ansible are IaC(Infrastructure as code)  tools too, but they focus on configuring operating system and applications. They are called Configuration Management Tools and they also can build infrastructure on the cloud with a help of plugins, but usually it is hard to configure and sometimes it is limited. With Terraform you can build from the services to the networking part. You can use Terraform to create the infrastructure and a configuration management tool to configure the applications. Terraform can’t replace your configuration management tool, but it’s made to work together with it.”


Erin F. We use it to spin up VMs within our VMWare cluster. It goes to our local DNS service and local Firewall rule service. Wouldn't call this cloudy. YOu can force Terraform to interact with any service that has an API.


This is "provisioning" the infrastructure. Not for provisioning an instance.


What is a Terraform Provider?
An API-specific wrapper to make calls on your behalf to spin up resources. YOU can write your own. There is also a null provider, which allows you to do terraform stuff. Can be used for testing. "Fake out" an API that doesn't have a predictable response (Erin & co do this for one of their local providers).


You can't easily switch providers. You'd have to rewrite everything to move from AWS to google cloud.
What is a Terraform Provisioner?
Used to execute scripts on a local or remote machine as part of the resource creation or destruction.
“When you go into the instance and provision it”


State file
Known resources that you're using terraform to create or provision. If someone goes onto the console and creates a new instance, but you tell terraform to do it some other way, terraform will tell you about the discrepancies.


In puppet this would be known as "drift" management.


You can share state between machines on different providers if they're both managed by terraform.


How to break out state files? You can do this in lots of different ways.
* One example: Per VPC (One for applications and one for databases)
   * Base state per environment, e.g. `production base`
   * 'Stateful VPC' (virtual private cloud)
   * 'Stateless VPC'
* One dir per provider
   * one dir per region
      * use remote state (see some links below, esp first youtube hashicorp video)


Import
You can import state of a machine created from the console.
It is “a bit of a pain” but also “almost awesome.”


To move to terraform management from an instance created on the console: Import resource with no attributes. Then run `terraform plan`. It will tell you what's different and you can fill those in on the state file.


Personal story
Was going along fine on the cloud with ansible. But things weren't working well. Found that TerraForm encodes cloud best practices. Example of what "wasn't working well": what happens if we deploy when an autoscaling event is happening? if we build a new box every time we deploy, it's always patched.


Best practices are still forming as the tool matures.


How does secrets management work with Terraform?
* In your terraform files
* In an S3 instance that can only be read by instances
   * encrypted with KMS
   * Even the terraform code cannot access this instance.
   * The s3 bucket is set up by a terraform. limit set of people who can put the secret there.
   * 

How do you deal with IP addresses?
* mit-lib.net and use cnames
* Use Elastic Load balancers (ELBs) Or Application load balancer (ALB allows you to have more complicated routing; use it like a reverse proxy; use it for internal-only traffic)
* terraform is updating the DNS via elastic ip and route53.
   * may be a bug where you have to run terraform twice


A real use case
Lesson: directory structure is really important. reusable code in the `modules` directory.


Notes / Pitfalls
* Do not create your own VPC module. There is one already; find it.
* Sometimes a module isn't really reusable in a way you want it to be; have had to copy/paste into a new module and change a couple things.
   * One way to deal with this is only put known-reusable stuff in modules and put the rest in local files, hope they become generalizable down the line.
* there have been times when the documentation wasn't enough. terraform is written in go.




Potential Useful Links for tfstate/team using Terraform
https://www.youtube.com/watch?v=wgzgVm7Sqlk - Hashicorp Employee talks about tfstate and the different ways of setting up your terraform environment “folder structure” (good -> ideal setup)
 
https://blog.gruntwork.io/how-to-use-terraform-as-a-team-251bc1104973 - good resource/info all around
 
https://medium.com/@brendanspinks/terraform-on-aws-using-remote-state-backends-with-workspaces-7e0f2f341b2b - info on workspace and remote tfstates (remote tfstate in S3 and using terraform workspaces)
 
https://github.com/cloudposse - good link for starter modules for use to use/modify
 
https://thecode.pub/creating-your-cloud-servers-with-terraform-bfa01a499bad - intro on layout/modules/using (Why Terraform? What is the difference between Chef, Puppet or Ansible?)


https://charity.wtf/tag/terraform/ - This article might be starting to get a bit dated, but it’s a nice intro to terraform.