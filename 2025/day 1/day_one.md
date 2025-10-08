## Review of What is DevOps from spring 2024

* What else?  
  * An attendee years ago said DevOps is about safety. E.g. You’re not going to have a huge bug over the weekend that you have to respond to. Also, caring for one another and feeling safe working together.  
  * Dev and Ops are in a relay:  
    * The DevOps lemniscate, also known as the DevOps infinity loop, is a visual model that represents the continuous and iterative nature of the DevOps lifecycle.  
    * Shaped like the mathematical symbol for infinity, it illustrates the seamless collaboration and flow of work between development (Dev) and operations (Ops) teams.

## Topic 1 - Caring for people

Fostering a culture of safety   
Work Management and Bridging "Healthy" Agile practices to libraries with tickets and documentation  
Self-care for the on-call

* Have there been effective allowances for the challenging times? Adjustments for productivity? Deal with stresses outside of work?  
  * More support for mental health sick days  
  * Shorthand for what we’d leaving tech to do:  
    * Shepherding in New Zealand: 2   
    * Goatherding in Maine: 1  
  * One team did a “9 whys” about our core expertise to get connected with the meaning of our work  
    * “Life is hard and work shouldn’t be hard”  
    * The people are more important than the technology  
  * Flexibility in work schedules to accommodate outside responsibilities  
  * “Unofficial” Paid time off to offset work performed outside of regular hours  
  * DEI committee and pushes for organizational change  
    * However, the expectations for getting things done haven't changed necessarily. Inherent tension between goals and messaging.  
    * [9 Whys Exercise](https://www.liberatingstructures.com/3-nine-whys/)  
  * Defining priorities in our systems as a response to emergency situations  
    * What do we have to get up at 2am to fix?  
    * Creating internal SLA (Service Level Agreements) for stakeholders  
      * Who is signing this? How do you measure if that’s working? These are more human solutions rather than technological solutions.  
      * ticketing system-enforced rules about how fast to respond to tickets. SLA timers.  
* How do we carefully work together as teams as dev and ops?  
  * Benefits both sides to more fully understand one another’s work and domain  
  * How do we compassionately communicate needs and priorities?  
    * Cross-teams meeting every other week  
  * How do we make procedures and work patterns that make us feel like we’re more “on the same team” as the people that we work closely with, even when they’re technically on different teams?  
  * Approach a situation as a team vs separate responsibilities  
  * Approach anything with compassion towards the other person/party  
  * Benefits of separation of ownership/when they aren’t the “same team”  
    * Clarity of roles/responsibilities  
* Self-care for on call  
  * Flexible scheduling (self-accountability)  
  * Maintain work-life balance  
  * Rotating responsibility for after-hours  
  * A manager can act as a touch point and join to pair for the beginning of an incident, that makes it feel less isolating  
* Inherent sense of responsibility to solve a problem when we see it, but when there’s tension between responsibility and clarity  
* How do you create a safe community of like-minded practitioners?  
  * Slack isn’t necessarily a “safe” space  
  * DevOps4Lib meeting as a possible safer environment for sharing concerns and dealing with issues  
* Account for lost time from unplanned work  
  * Tension between making up for time when something goes wrong  
  * Important to have a manager or team lead that reminds someone to take time  
  * Advocate for self care

## Topic 2 - Documentation

Guidelines and best practices among large institutions   
Understanding Documentation as a Product (DaaP)   
Sustainability - prepping my work for the next person after I leave or die 

* How can we create documentation that prepares someone to pick up where you left off if you win the lottery?  
* What is the appropriate way to template documentation?  
  * Standardization  
  * High-level cover memo that gets included in a “service catalog” that acts as a one-pager for information about the system  
    * Form as a template to keep the documentation reasonable length-wise  
    * Basic troubleshooting  
    * Small, precise, and obtainable  
* Understanding who you’re writing for is one of the most important things to know when creating documentation  
* What platforms are people using for documentation?  
  * SharePoint  
  * OneNote  
  * Documentation “cover memo” template \[please note this is still in development\!)  
    * Document purpose: to define the \[BLANK\] service supported by Library IT Client Services and list the basic information needed to assume temporary support of that service.  
    * Audience: Library IT Client Services staff  
    * Service Name:   
    * System permissions needed:   
    * Service owner: \[position not role\]   
    * Product manager:  
    * Application/system Name:  
    * Application/system Description: \[what does it do, what service it supports\]  
    * Service Front End Users/groups:   
    * Service Back End Users/groups:   
    * Governance:   
    * Major stakeholders: \[roles and/or departments\]   
    * Glossary: \[definitions for specialized terminology & acronyms\]   
    * \[Links to other existing documentation\]  
* Example of RAC documentation: [RAC Docs](https://docs.rockarch.org/)  
  * There is a divide between public and private documentation.  
  * There are separate repositories for each type of documentation. Example: parts of systems documentation may not be appropriate for a public audience.  
  * Desire for the staff working on specific systems to take ownership of writing/maintaining documentation. This can facilitate training and development (documenting a system can help staff become more familiar with it, including calling themselves a “developer”).  
* Documentation can be a good outreach tool to expose the work/labor of DevOps  
  * Documentation can be woven into measuring performance and metrics  
  * Writing new documentation is also considered a part of the finalization of a project/closing a ticket.  
  * Comparison to the work of technical writing.  
  * When approaching documentation, can start by using a menu approach that starts with taking an inventory of tools/applications used throughout the library system.  
* Examples of DevOps docs:  
  * Cover memo for each service (Google Drive), README files of ansible playbook for specific application; external docs describing for developers on basic application management (how to start, how to build a container, how to troubleshoot)  
      
* The why: What is the purpose of DevOps documentation?  
  * “How to do the thing”  
  * Document so I can remember how to do the thing myself  
  * Keep documentation as close to the work itself as possible (i.e. in the same repository)  
  * Example: A bunch of different Github repos, folder of markdown documents specific to various services. The point is to have the documentation as close to the work as possible (meaning, a dev can switch over to the markdown documentation from where they are working, rather than completely pivoting platforms to Sharepoint, etc.)  
  * Why though?: Why was it designed this way? Why was it set up this way? This may fit into a “technical approach” type document  
* Documenting processes may also be interwoven into systems like Ansible, pull requests/issues  
* ADR (Architectural Decision Record)  
* Maintaining an appetite for documentation  
* There are some things that documentation can’t fix! (organizationally)  
* Develop a culture around documentation or it will die  
  * Nothing works forever  
  * Just because the effort dies, doesn’t mean it wasn’t worth it  
* What is the review process for documentation  
  * During new deployments, runbooks are stepped through  
  * Templates for different types of documents with recommended headings, e.g.: pre-requisites, runbook/checklists, measures of success  
  * Starting with something to fill out helps not face the blank page  
* AI can be helpful summarizing a well-written ticket and can be used to integrate into documentation  
* Buddying up/working with someone on documentation can be motivating  
* Not writing documentation is a form of gatekeeping  
* Newly-hired staff may be the best documentation testers/poke holes  
* “It’s just in my head”  
* Development can be exhausting. Once the dev work is done, it’s hard to go back and summarize/document.  
* Praise someone for documenting when they do it \- encourages them to do more of it  
* Documentation aversion is not uncommon, so good to see the big picture (this can help new hires in their training and is an act of kindness to future staff)  
* Documentation as advocacy from the work that you did  
* Tips for developing documentation as a skill?  
  * [https://diataxis.fr/](https://diataxis.fr/)  
  * [https://ctodocs.github.io/ctod/write-documentation.html](https://ctodocs.github.io/ctod/write-documentation.html)  
  * [https://docs.divio.com/documentation-system/](https://docs.divio.com/documentation-system/)  
* How do you document incident reports?  
  * Ticket that fixes underlying cause of the incident  
  * Example solution: Separate solution from incident ticket.

## Topic 3 - Communication

Engaging with difficult colleagues  
Championing DevOps in an organization of System/Server Admins  
How can library workers and DevOps work better together  
How best to communicate what DevOps is to library workers unfamiliar with DevOps culture 

* How do you translate your work to leadership/management? How do you show the value of DevOps? How do you communicate what you’ve accomplished to leadership levels?  
* Is it “our” developer’s job to communicate our work to executive/leadership level, to translate our work value?  
* Playing “telephone” doesn’t always work, is there a better way to capture wins and value-adds as summaries?  
  * Pairing “why” to the task itself?  
    * I.e. organizational values, this work supports this value  
    * Create reporting w/ project updates and strategic plans  
      * Swarmed authorship  
* Slack channel where they communicate with stakeholders  
  * Librarians involved in the Slack channel and in design meetings  
  * Prioritization meetings  
* Without “justifying existence”, how can we say, “this project supports this part of our vision/mission”.  
  * Engage the team to do this as a group possibly  
  * Product management i.e. a dedicated comms lead who leads a change advisory group  
* Do we have to document our work AND “sell” our work?  
* DevOps \== Fostering communication (including people above) to tie business directives to the work you’re doing  
* Translating to values can be affirming when done collaboratively with colleagues.  
  * Started a “book club” or “reading group” to talk about common issues  
  * For example, reading the “DevOps Handbook”  
  * assign chapters to different people and have them summarize or lead discussion  
  * Scoping membership of the group can be a challenge and facilitation is important to get right, can be quite a bit of work.  
  * Can be hard to ensure everyone feels safe to talk   
* Can library workers (general population) work better together?  
  * The term “DevOps” can be scary, sound military, feel like I’m in trouble if they contact me  
  * It’s not “general” knowledge.  Even the term “infrastructure” is loaded.  
  * The term “infrastructure” can also be confusing  
  * Is it ok that a librarian or archivist doesn’t know what DevOps does?  
  * *Should* we be invisible, assuming we did our jobs?  
    * If not, how do we talk about the right way to do something  
    * Being a resource can make problems invisible, but we can only do that if we are “known”  
* Archivists tend to become their own IT over time, organically.  
  * Partner that can guide and help solutionize, a dedicated knowledgeable resource.  
* DevOps helps to liaise between vendors and should be a part of early-project planning.  
* Consider saying no to re-branding to “DevSecOps” as it may sound more militant.  
* How do you get library workers to climb over the wall, not just toss things over the wall?  
  * Grassroots mobilization affects change, not top-down.  
  * Get the right people involved to unblock you.  Market the team and advocacy to create solidarity.  
* Deploy small changes more frequently  
* Create capacity to add a buffer after deployment so that things that come up can be addressed right away.  
* RACI charts can also help get clarity on who’s doing what and when, creating expectations matrix.

## Topic 4 - Infrastructure Choices

Tech stacks on-prem vs cloud  
Infrastructure Assessments  
Bringing the Product Mindset to DevOps and the Product Operating Model; Infrastructure as Product?  
Containers and networking

* What are people doing for infrastructure assessments?  
  * Security and resilience  
  * Example:  AWS [Well-Architected Framework](https://aws.amazon.com/premiumsupport/business-support-well-architected/?trk=64889dc8-355d-4be1-8abb-b78d97ad2a1f&sc_channel=ps&ef_id=Cj0KCQjw9JLHBhC-ARIsAK4PhcrBD0DAkXO7mATBO7vNJqAAli89YLclIHvoYf4HdADboimblS2nrHsaAhq4EALw_wcB:G:s&s_kwcid=AL!4422!3!719333527370!e!!g!!aws%20well%20architected!21852254337!176452274104&gad_campaignid=21852254337&gbraid=0AAAAA-aZeIVW2ENWA9lNhDbkFrA-3ykBF&gclid=Cj0KCQjw9JLHBhC-ARIsAK4PhcrBD0DAkXO7mATBO7vNJqAAli89YLclIHvoYf4HdADboimblS2nrHsaAhq4EALw_wcB)  
* Make sure you’re running supported versions of software  
* Endoflife.date  
  * Applications, databases, packages, etc.  
  * Overarching understanding of when something will expire  
* How do you make end of life dates part of your workflow?  
  * A lot of manual matching up end of life dates to long time services  
* Scheduled maintenance windows for infrastructure  
  * A week after patch Tuesday  
  * Updates via availability zones using Automox (https://www.automox.com/)  
  * Staging environments one week, and then prod a week later  
* Have to work a hybrid environment based on some of our records, but a lot of our focus is AWS  
* CloudFormation vs. Terraform  
  * Terraform would be great to avoid vendor lock-in with AWS  
  * Being platform agnostic does take a lot of work, and moving to a single platform made it a lot easier.  
* You probably have time to rewrite terraform or ansible playbooks if you do move cloud  
* Deploy containers to a Nomad cluster (which is installed on VMs on actual hardware)  
  * How do you have a VM with a container on an orchestration layer? How does it all come together.  
  * Container and server share the same kernel  
  * The container orchestration builds another networking bridge that creates a private network with different containers  
  * Containers build bridges on the device  
* Some institutions working with about 15 containers and that’s enough to make the orchestration helpful  
  * Had to use containers for their new things  
  * Nomad vs. Kubernetes   
    * Everyone that had used Kubernetes was unhappy with using it  
* Docker Swarm is clustering of Docker Containers  
  * How do you get it there? Compose a container to a specific node  
* Some are testing Dockerizing their own Sidekick images  
  * Has not shown a ton of performance improvement  
* Putting some extra tools on their base images on their containers, e.g. monitoring  
* Trouble keeping up with the amount of tools that are out  
  * How do you find solutions for what you need?  
  * Concept of “innovation tokens” (you can only spend so much energy on new things)  
* [https://boringtechnology.club/](https://boringtechnology.club/)