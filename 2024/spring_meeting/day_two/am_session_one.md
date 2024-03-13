## DevOps Culture


* Facilitator: Bess Sadler
* Note Takers: Hector Correa and Laurin Penland
* Gatekeeper: Francis Kayiwa


    * DevOps Culture (17)
        * Cultural Changes as devops implementation
        * Establishing DevOps team, roles and practices
        * How people implemented DevOps as part of larger organization
        * Communication, documentation, release notes
        * Applying DevOps to agile project framework and ongoing enhancement processes
  
## Notes:

 * How people implemented DevOps as part of larger organization.
     * The DevOps engineers will be resident in particular projects, in large part they are there to ease process to deploy things, building development environment
     * DevOps engineer helps fixing problems a developer has asides from “I wrote code”. Helps the developer keep going.
     * (What is difference between SysAdmin and DevOps engineers) System Administrator is limited to a single system
     * Generational change: 1990s sys admins had a specific and limited role (not a software engineer).
     * DevOps culture helps to flatten the hierarchy (everybody is part of the team, all needs need to be accounted for).
  * What goes into DevOps culture?
  * The risk of overloading the DevOps engineer (give them too much)
      * Some institutions don’t assign a DevOps engineer on purpose for this reason. Have cloud engineers and software engineers. Have team leads. Comes down to communicating effectively.
      * DevOps engineers don’t need to know the intricacies of Ruby on Rails, but they need to *care* that we are writing code with it and that needs to be deployed.
  * Use to have to ask SysAdmins to do stuff for you on the server, would take a really long time
  * Having to circumvent the people that need to do the stuff (e.g. setup a server) is not DevOps.
  * Another example of not DevOps: Developers can’t get a dev environment, they go around the system admin and that creates more trust issues.
  * Building trust between groups of people with different needs (devs + ops).
  * What questions would you ask to understand the DevOps culture?
      * What’s the process to go from writing code to deploying it to production
      * What is the collaboration
      * List of past incident reports
      * Documentation for using tools (Git, workflows, )
      * Is it realistic for DevOps be everyone’s job? Everyone should be thinking and doing DevOps, just part of being a developer.
  * “If you have DevOps in your title you are doing it wrong” – given that DevOps is a shared responsibility.
  * The structure of these roles varies depending on the size of the organization. For those with DevOps engineer in their title, their role is to know more about a diversity of stacks, not just one stack
  * [Choose Boring Technology](https://mcfunley.com/choose-boring-technology): you can innovate, but choose new things selectively, boring technology is more stable. Some people are going to static sites.
  * What is skinning? A way to change the way a site looks (UI/UX) while keeping most of the structure the same
Example: [ERIC - EJ935495 - LibGuides: A CMS for Busy Librarians, Computers in Libraries, 2011 (ed.gov)](https://eric.ed.gov/?q=EJ935495&id=EJ935495).
  * What does it mean for a developer to do DevOps?
      * You’re developing and deploying
      * You are responsible for all these things, but you are part of a team, responsible for reaching out to product owner
      * Includes one on one interaction/training (there is documentation but not everyone wants to sit and read)
  * Runner: a role in which a person monitors applications for exceptions and errors.
      * The role rotates among team members
      * Brings exceptions and errors to the team (i.e. does not have to fix the issues themselves)
      * Use Honeybadger, Datadog
      * Some orgs have an on-call process for after hours support, role rotates too..
  * How to enjoy pairing?
      * Pairing can feel restrictive (can’t get up and move around, listen to music)--solution: could do the Pomodoro method, pair for a little while, walk around, switch who is coding
      * “ping pong pairing”: one person drives when writing the test, the other person drives to make the test pass
      * Pair with different people
      * Set some intentions for pairing sessions; what are the goals?
      * If you’re in a more senior position, make sure to be open to questions, slowing down, etc
      * Can check in at the end to discuss how things went
      * You don’t have to do pairing, pick things that you think you will really benefit from pairing–a technology that you don’t know much about; pairing isn’t for everyone or every project. Useful for when the group doesn’t know how to fix a problem.
      * How does pairing work for people with different learning styles? Different people have different needs.
Can change it up – pairing can look differently. You can work independently for 20 minutes and then check in for five minutes about the work that you did.
      * People need to feel comfortable enough to say “this isn’t working for me”
      * Pair for things other than programming: architecture, decisions, information sharing.
      * Not everybody does it (pair programming) on the same way.
      * For fully remote team: use VS code to share out workspace, very interactive experience
      * Use pairing as an opportunity for rubber ducking (explain a problem to others).
      * If you don’t think linearly pairing can be stressful (particulary if you don’t know how the other person’s thinking process works).
      * At one point we (as an industry) were afraid to let others see our code, we are past that. Are we afraid of letting others see our thought process?
      * Trying to be thoughtful, not going too fast
      * Pairing is not the goal, collaborating is the goal.
      * Pairing can prevent a large pull request where only one person knows the code being introduced.
      * As a new developer it can be good to see how others do things, a way to also understand the larger context of why things are done. Share code during weekly stand-up.
      * Encourage developers to push work in progress so others can view/review .
      * Not everybody pairs all the time, some groups do it when they get stuck (rather than an on-going practice)...but they still collaborate on-goingly.
  * Writing up detailed issues/tickets makes things easier/is good practice. Some teams write tickets together. Are we on the same page (pointing)? What are the options going forward, which one are we choosing?
  * Creating smaller tickets and smaller merge requests (not more than 200 lines of code) is good practice. Using a merge request template helps: what changes were made, why they were made, any screenshots for UI changes.
  * From Slack: Links on pairing in tech and neurodivergence
      * [Understanding the Challenges Faced by Neurodiverse Software Engineering Employees: Towards a More Inclusive and Productive Technical Workforce](https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/neurodiverse_tech_employees_assets2015.pdf)
      * [Pairing at Work: the Weaponization of Coder Vulnerability](https://www.metafilter.com/191442/Pairing-at-Work-the-Weaponization-of-Coder-Vulnerability)
      * [Students with Learning Disabilities, Pair Programming And Situational Motivation](https://www.learntechlib.org/primary/p/207984/)
        