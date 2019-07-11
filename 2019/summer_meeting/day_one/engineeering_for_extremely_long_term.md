# DevOps4Lib 2019 Summer Summit
## Engineering for Extremely Long Term

Notetaker: James
Gatekeeper: Francis
Timekeeper: Dan

*Beginning at 15:05 EDT*

### Defining extremely long term
* In perpetuity
* Anything without a sell-by date
* Duration of a grant has some hard deadline
* Multiple years
  * 3 years is long enough for some platform to be deprecated and removed
* Extremely long term
  * Users might need to simply use a platform forever (at least 5 years)
  * This affects how one weighs stability against efficiency
* **There is no actual consensus around this time span**
* When the lifespan affects one’s decisions - this renders it long term
* What would be the grounds for some platform to be shut down?
  * Outliving its utility
  * Stakeholders and users are no longer with the institution/organization
  * There are some cases where a small, short-term solution emerges into a long term platform
    * Triggered by a need to fix certain problems in the production environment immediately
* Architectural Decision Records (https://adr.github.io/)
  * Assists with guiding long-term architectural decision making
  * Highlights when a decision might be optimal for only six months, but not for two years
  * Need to be more flexible when it comes to what constitutes an architectural decision
    * It should not be limited just to software design
* Assumes that you or someone like you will be on the team to support the platform years later
  * Bioinformatics projects can be assumed to be continuously-funded by grants
    * In this case, they might simply not have any way to die
  * However, this is obviously a faulty assumption
  * The project itself won’t fail, but grant funding will no longer be available after a certain point
  * Planning needs to be addressed for these cases
    * Data exportation is a common consideration
* Formally Exporting the Data
  * Ideally, one would not need access to the database
* Planning for Maintenance
  * This should be addressed at the very beginning of the project planning process
  * What is the next step for this?
    * Rockefeller Archive Center has had success with this
  * Version upgrades or addressing disaster recovery
    * Here, data exportation becomes essential
  * Also impacts the language selected for implementing an application
* User and Platform Lifespan
  * In certain cases, the users are researchers who have been working using similar tools for more than 10 years
    * Resistant to changing their approach to using more modern tools for analysis
  * Scripting and automating updates for these legacy systems become essential here
* Assumptions for Coding
  * Code becomes a liability regarding platform maintenance
  * Do stakeholders have an understanding of what maintenance is required in order to support new projects?
  * Some organizations have started instituting maintenance days
    * Now we have people above us seeing that there are entire days blocked off on a monthly basis
    * This renders the cost visible to management
  * The Maintainers (https://themaintainers.org/)
    * Offers events
    * Not specific to DevOps engineers or developers

### What makes an application hard to maintain
* To keep something running, maintenance should be made easier
* Containerization can assist with this
  * Minimizes dependencies
  * Management of application state
  * Provides layers of abstraction which can assist when addressing concerns for legacy systems
* Application development often uses automated dependency management as a standard part of the workflow
  * Dependency management challenges are more often found in server administration
    * Automating deployment for services ensures that configurations are not local to each server
* Central points of failure for dependencies
  * rubygems.org is a single point of failure for Ruby on Rails applications
  * Maven dependencies also have these problems 
  * Even central repositories for code can raise these problems
    * Although, this might be mitigated by ensuring that teams do not entirely neglect certain applications
* Automated dependency management
  * Security alerts for packages or libraries can be offered
    * GitHub is getting better at providing this for open source projects

### Disaster Recovery and Backup Practices
* Within the context of an extremely long term life cycle
* Most of those involved are creating data which should remain preserved and accessible forever
  * Recopying indefinitely is a common practice
  * If “forever” is 100 years, how can this data be preserved economically?
* Preserving the data itself is not always enough
  * Software used to access the format itself also becomes a problem
* Longer timeframes introduce a higher likelihood that there will be a disaster
* Redundancy can be extremely valuable
* Some use a dark LOCKSS archive (https://www.lockss.org/)
  * Duplicated geographically
  * Archive which will never have access to the public
  * There are hubs in contact with one another
  * The files are distributed across the network, hence corrupted files can be restored
* Tape storage
  * Some still use tape storage (LTOs)
* Want to avoid colocating practices where the data from digitized material is places in the same building as the material itself
* Ceph (https://ceph.com/ceph-storage/) also self-healing digital object storage
* Amazon Glacier (https://aws.amazon.com/glacier/) is also valuable in providing third-party backups
  * Retrieving data can be expensive or slow for cases where testing smaller sets of bitstreams (e. g. 9000 images from manuscript digitization)
  * Amazon Snowball (https://aws.amazon.com/snowball/) can actually be less expensive
    * Need to transfer the data to S3, which is then transferred to Glacier
* Princeton has a local Isilon (https://www.dellemc.com/en-us/storage/isilon/index.htm)
  * This is mirrored and has snapshots
  * Backup to Google Coldline (https://cloud.google.com/storage/archival/)
  * Have a user requirement to checksum locally and in Coldline
  * Will checksum 5% percent of objects annually
  * There is a dashboard for indicating the progress of the checksum checks
### Version Management
* Build artifacts
  * Cases such as RubyGems
* Having version build dependencies
  * Have a built version which is run using the Gems which are cached in a build artifact repository
* Penn uses VM images and Docker images
  * Easily attributable builds which can be used to recreate the environment
* Science History Institute supports a similar approach
  * Uses S3 buckets to manage and track dependency libraries for building applications
* Sometimes, can even vendor the dependencies in a Git repository
* Running a separate gems server (for Ruby) is another alternative
* Offering mirrors for certain open source projects also combines this approach with returning some support for the larger community
* Versioning the system itself, or the applications running?
  * Ideally, some would like to be able to reproduce the server from scratch, and rebuild and run all applications without access to the World Wide Web
  * Containers provide something analogous to a statically-linked binary
  * Database state
    * Replication alone won’t save someone from user error
    * Rolling back database migrations has implications for how the APIs for the database

*Session concluded at 16:03 EDT*


