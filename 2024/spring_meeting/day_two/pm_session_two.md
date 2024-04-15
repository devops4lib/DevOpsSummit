## Cloud

What problems are folks having with their cloud environment?
* Some people in charge are not happy with having technology/servers that are( not in their control
    * Building trust
    * ask what makes it easy to accomplish the goal
    * Let’s try it out with a small example/project and evaluate/expand
    * Allow people targeted access to the server so they can see what is going on/ be transparent
* Cloud environment in place from before, not willing to make changes after leadership change, want to take back control
* Amazon Web Services offers ACM -> Amazon Certificate Management
    * Let’s Encrypt
    * ACME - Automatic Certificate Management Environment
* expensive

Does anyone have a Hybrid cloud/on-prem environment
* Lots of people have hybrid environments
* Clouds environment used for backups

What makes you decide to run something locally vs in the cloud?
* Cost considerations, special contract?
* Moving to cloud as a means of reducing staff?
    * May result in hiring more people to manage all of the cloud services
* Reliability
* Scalability
* Organizational mandates forcing you to move from local to cloud
* Donor agreements may require application/materials remain local
* Ease of launching off the shelf cloud packages 
    * [serverless IIIF](https://github.com/samvera/serverless-iiif) on AWS lambda (one of best use cases), just points to S3 bucket
        * Scalability
        * Running only when needed
        * Thanks mbklein
        * Public cloud formation repository, build from Gitlab CI pipeline and point to S3 buckets
        * Could possibly point to MinIO instead of AWS
* cloud storage is too expensive (hundreds of terabytes)
    * especially when i need to set up backups
    * AWS Glacier -> cheaper low-access service, slower and more expensive to access
* storage is fast to get in the cloud, not fast to buy disk for
* Storing content on shared network drives, not too expensive moving to AWS
* costs can be unpredictable

Assumption that cloud = AWS (or Google CS or Microsoft Azure) -> what are alternatives?
* There are other cloud providers that are explicit about their values, which may be / likely are better aligned with library values
* Europe is seeking more cloud alternatives that are not based in the U.S.
* [Linode](https://www.linode.com/approach/) (aquired by akamai)
* Hardware as a Service
* [Scaleway](https://www.scaleway.com/en/about-us/)
* Run cloud-like things locally (S3FS)
* We’ve been trying to use a company called wasabi but no one has heard of it and they don’t have experience with large institutional customers, so it’s difficult.
* there are a lot of services that are not aws on the service but often are underneath. it’s important to look at where the servers are physically located
* platform as a service, e.g. heroku, Pantheon

Critical infrastructure:
* If the cloud goes down, do you have a plan in place for recovery?

Processing content in the cloud first and then pulling down for local storage for lower cost

Tips:
* If you scale up an EC2 server for a weekend project, don’t forget to turn it off! Or you will get a huge bill. You can setup of billing alerts.
* Don’t post your Amazon key in a public repo!
* Learn Identity Access Management [https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)

We are able to run our load more ethically by using cloud resources because we can right-size the computer to the task.
* How did you measure this?
    * hired consultants to look at our electric consumption
* put the link here to [Hillel’s code4lib talk and/or blog
    post](https://www.youtube.com/live/McqOGzHfmOM?si=QXssdDDAABF_fOYw&t=4626)
* Consider where your electricity is coming from

VMWare - everyone wants to jump ship
* ownership changed to Broadcom, price has increased by 600%
* Proxmox -> not ready for primetime
    * Does it support alternative storage backends? Not sure
    * Ceph (a way of storing data; it abstracts away the contents of the data into a high availability cluster and balances) is under the hood, handling storage is clunky and complicated
    * Moving data from one node to the other is a hassle
    * Have to go through many (like 15) steps to set something up in the cloud
    * Veeam may soon support Proxmox
* Azure on-prem?
* Linux on Hypervisor?
* Xen is an option for local hosting
* What are we going to do for the future? The important thing is the data, not necessarily the platform
* Many hardware vendors are committed to us being able to run our own clusters; hopefully their parent companies are going to help figure this out (maybe via supporting alternative open source projects)
