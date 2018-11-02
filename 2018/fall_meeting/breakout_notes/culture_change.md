# Culture Change

*Session Started at 15:00 EDT*

## Training

Success Stories?  Failures?

**Princeton University**

* DevOps engineer in the process of working with developers from Digital Repository and Discovery Services (DRDS) and Web & User Services

* After 2 years, he has been getting everyone to use Ansible for deployment in DRDS

* Introduced Ansible Kindergarten for Web & User Services

* Objectives are to have web devs create and manage their own Playbooks in a virtual environment

    * "Cowboy ops/infrastructure"

* DevOps engineer facilitates in using Vagrant/Ansible in order to provision environments

* Example: Take a WordPress site, walk through constructing a role for this

    * Review idempotency and Ansible Roles in provisioning servers

* Practices were established when just building Rails apps at Princeton, so this is meant to foster growth beyond this technology

* Prefer to have Web/User developers issue Pull Requests, and have DRDS developers review these

**Temple University**

* Dungeons and Dragons for Troubleshooting

* Used to provide insight into how best to debug a given system or give some insight into how systems work

* DevOpsDays Philadelphia 2018: Inspired by a presentation given there

* Outline a scenario, and have developers describe how they would resolve an error for a web application (e. g. 400 error response)

* As the "Dungeon Master", try to lightly guide the developers towards the goal

* Identify the decisions which are made when troubleshooting throughout this process

* Also, following this exercise with documentation is ideal

* **How is the scenario described/presented?**

* Temple has not had the chance to run a session yet

* RefWorks: People couldn’t use this rapid import, just a meaningless error for clients

* After massive debugging, TLS 1.2 was not supported by their client; RefWorks needed something older

* Using this scenario, the Dungeon Master would use a shell...wait for the developers to guide him through this process (example: searching for which logs?)

* Perhaps even mocking the data being used during the session

* DevOpsDays Philly: Google Cloud Platform was used to provide a more interactive reference

* **How long should these sessions last?**

    * Should not take longer than 1 hour…

* **Is one of the goals to have participants take notes and produce documentation?**

* **Or, is this more focused upon training than generating documentation?**

* **Should only the DM take documentation?**

* Temple: Would probably take some prep. time to produce documents which could be referenced after the session

* Proposal: Perhaps integrate GitHub into this process, submit a PR for the docs for review afterwards?

* One needs to frame the exercise in a neutral way, and ensure that those who have never played D&D don’t feel excluded

* Proposal: Can script it out and turn it into a terminal (TTY) game

**Drexel**

* Walkthroughs are great...as an experience

* Uses tmux with a colleague, shares the session and have them passively observe how this undertaken

### Learning New Technology

**When dealing with an exposure to a vast array of technologies...what is your process for learning a new technology?**

**How do you establish fluency with so many new tools?**

* When trying to solve a recurring problem...it might not ultimately have an answer

    * What is the framework which addresses 90% of their problems?

    * These are problems which keep emerging in personal conversations, on online forums…

* Knowing the problem list:

    * One should have a small toolset to be able to spin up infrastructure

    * Should be able to throw it away

    * It should retain useful artifacts

    * It should adhere to a plug and play architecture for software

* AWS and Cloudformation: these bring the solution halfway there

* Terraform brings one closer to a solution

* Some find that speed and locality are needed

    * CLI calls to AWS endpoints can be slow

    * One needs to be able to quickly mock/mimic an environment for testing

    * Docker images were found to be ideal for this

* Kubernetes (K8s) and Amazon web Services

    * Amazon Elastic Container Service for Kubernetes (EKS)

    * [https://aws.amazon.com/eks/](https://aws.amazon.com/eks/)

    * EKS Module development: Mocking is not supported

    * AWS Kubernetes was too different from standard Kubernetes, so this EKS mocking comes with challenges as well

* **Is additional time consumed by anyone for studying?**

    * Some take additional time for a Coursera course

* Usually the documentation for K8s is good, but very theoretical

    * Kelsey Hightower: [https://github.com/kelseyhightower](https://github.com/kelseyhightower)

        * Used for tutorials/walkthroughs during this period

### Productivity

* Some prioritize trying to minimize distraction during the workday, and in doing so, trying to avoid meetings when they can

* One telecommuter focuses entirely upon work for the day for 8 hours

    * May also take a late lunch and short break, on those days take some evening time for additional work
* Someone referenced the Daniel Pink book *When* ([https://www.amazon.com/When-Scientific-Secrets-Perfect-Timing/dp/0735210624](https://www.amazon.com/When-Scientific-Secrets-Perfect-Timing/dp/0735210624))

    * For some, mental productivity wanes at certain points during the day

    * Someone explained that they use 02:00PM as a period for non-engineering work (notes/e-mails), and generally tries to address this type of work in an uninterrupted block

    * Some can work outside of standard business hours, but it has to be on their terms

    * Employees with families use a 07PM-10PM productivity boost for addressing their family

        * Any energy left over, this also has to be used to manage life-related issues outside of work (e. g. home maintenance)

        * Work-life balance is essential

### Workplace Culture and Stress

* As a manager/boss, it is important to ensure that colleagues do not expect themselves to be forced to work just given that management is working on a given day (uses traveling and jet-lag in an incident for an example)

    * Managers should be certain to ensure that employees don’t assume that their managers demand unreasonable hours

* Tracking time is a terrible habit...this is never accurate

## Professional Development

* Events and Conferences are excellent for professional development

* PSU started a DevOps group

    * Penn State University Development Operations Group

    * There are staff who must undertake systems admin. tasks, but are still primarily developers

    * 2 hours every other week are allocated for discussing topics related to operations

* Safari Books is a huge resource

    * Also Red Hat Learning

* Safari Books can be offered as Inter-Library Loan resources

* Code Reading Group is currently held by Princeton and Temple

    * Having Safari Books alone is good, but the motivation improves this (particularly for social discussions)

**Conferences**

* Velocity

    * O’Reilly sponsors this, involves DevOps and distributed systems

	* Configuration management was also discussed

* KubeCon and CloudNativeCon have been attended

* Discounts

    * GitHub for Education: Unlimited private repositories

        * Needs to be research-related, just needed to mention that institutions received grant funding

* Amazon’s re:Invent Conference

    * The talks are online, it might be worthwhile to just watch the videos online

        * Otherwise, one might need to travel between 8 hotels

        * 50,000 attendees last year

* Google.io is another event with videos available online

    * Difficult to attend in-person, they screen potential attendees (simply too many wish to attend)

* GitHub Universe

    * Featured interesting talks…

    * Stanford attended the first event...learned more about how people were using GitHub to empower their own services/operations

* Monitorama

    * Focused upon monitoring, small, 500 people attend

        * Brilliant talks are offered there

* USENIX Lisa

    * Talks around best practices, demonstrating local, customized solutions

    * Not all that helpful for those looking for more generic solutions

* HashiConf (HashiCorp)

    * None have attended this

    * Some opted for online training instead, this was more affordable

* Sematext Training for Solr

    * Overall very quality, but required some experience on the track pursued for PSU

    * Walkthrough of the documentation was also a part of this

* LucidWorks Training

    * Recommended only for entry-level training for Solr/Lucene

    * Maybe if it was smaller in size it would be slightly more focused

* Massive Open Online Courses (MOOCs)

    * Coursera, Udemy?

    * Nick: Udacity is a for-profit MOOC platform

        * Very good for software engineering, not as good for DevOps

        * Some found the Udemy course for k8s was very good

* Lynda also has decent offerings for introductory-level

* Ultimate Go course by William Kennedy (Ardan Labs)

    * Very good

## Onboarding

Problem Scope: What are our blockers to doing good onboarding?

* Requiring the right tools and the right place...ensuring that everyone has the right tools installed and configured

* Establishing a culture in which all trust each other, can admit shortcomings, failures, and whether or not they know something

    * Promotes sharing knowledge

    * Explicit understanding was made between all members on the team to achieve this

* Every new person brought on to the team needs to be onboarded differently

    * Different professional backgrounds shape these needs

    * Emphasis upon culture allows adaptability around onboarding

* Obsessed with pairing

    * Some people can be really energized by this setup

* Corporate onboarding brings with it many strengths

    * Readily integrates new group members into the organizational culture

* Some have used presentations in order to ensure that other team members could ask questions

    * Also brought them closer to the organizational culture through this process

* Post-mortems in process

    * These are undertaken in some institutions

        * Post-mortems have been given for travelling disruptions

## Post-mortems

*We did not address these*
