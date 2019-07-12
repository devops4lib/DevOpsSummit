# DevOps4Lib 2019 Summer Summit
## Continuous Delivery

### Problem Statement: How to handle situations that arise during times of short staffing?

* Starting on a process allows you a foot in the door for a solution?
* Does everyone have a process?
  * Francis’ process - Anything with more than 30 minutes of downtime starts an incident response
     * Template in google drive 
     * Create a copy from the template and tag people in slack to get them to edit the document
     * Makes sure everyone in the leadership team sees it
     * Turns into a timeline of what was done
      * [Google SRE book](https://landing.google.com/sre/books/)
      * [PagerDuty](https://response.pagerduty.com/after/post_mortem_template/ "Pager Duty Postmortem Template)  has a good example - UI and contact that can do the triage
        * Automatically escalate
      * [Gitlab[(https://about.gitlab.com/2017/02/10/postmortem-of-database-outage-of-january-31/ "GitLab outage postmortem") has a write up of when they had an outage

* How do make sure all relevant people have their eyes on the document?
* How do make sure enough people are participating?
* How do you communicate with stakeholders?
* How do you make sure the people working are communicating?
* What roles do you assign people and how do they get assigned? 
  * Incident Commander
  * Note taker
  * Person fixing the problem

* What can be immediately be put in place to make the process better?

* Lack of a formal process causes a large amount of stress, but it is happening first.
  * Defined roles
  * Keep notes
  * 15 minute post mortem

* Everyone adopted the simple process, and everyone knows that it exists
* Putting the templated document in the channel that the project runs.

* Practice would make this easier

* Chronic slowness, when does that get elevated?  
  * Once you feel this is a real issue.  It can be used as a communication mechanism to leadership about a problem.

* Error severity:  Warning: day or two, Error: soon, Critical: immediately

* If you have SLA (service level agreement) that says that the response time would be a certain amount, if the service misses the sla then it is critical.

* What did we write down as acceptable working?
  * No formal process, but opening a zoom room for all responders to join and work on together
  * An additional benefit of the notes is who is continuing to respond.
  * Allows for questions to be created for how do we prevent this in the future

* Who goes to the post mortem?  Stake holders? Team?  Outage channel which includes the boss and grand boss. Have the outcome in slack and have a 15 meeting meeting.  Boss & responders.
  * Document that gets discussed during a weekly multi team meeting.  What went wrong, what went well, how will we avoid it.
  * In the document you make it blame free. What are the sources of failure
* As you deal with the incident you keep a running notes, so that you do not have to think hard at the retro.  Slack channel can run like running notes
  * Here is why it happened.  Here is what we are currently doing.  Here is what we are going to do.
  * Once the list os produced how do you make sure the action items have been completed?  You can create tickets or action items and a timeline.

* Create the tickets during the retro.

* It is good to communicate to the users, so that they know when you are going to respond.

* SLAs can help developers and DevOps protect themselves
  * They can set out rules for working and helps you protect your time
  * Impact of an SLA can change the architecture of the system.  For example You do not have to have automated failover. 

* Service Level Agreement vs Service Level Objective
  * The database went down how to I know which one to work on first?  The SLA can help.

* [SRE Book]((https://landing.google.com/sre/books/) is worth a read to free you from 100% up time.  Focus on priority of what to do next.
  * When you miss the SLA it makes it easier to argue more staff resources.

* Potential roles:
  * Incident commander - someone equipped to delegate tasks, report up
    * can also make sure people are building notes as you go along
    * doesn't actually work the problem
    * keeps the team updated/free to work the problem
    * communications liaison
    * Keeps the team fresh (possibly pass off to another person)
