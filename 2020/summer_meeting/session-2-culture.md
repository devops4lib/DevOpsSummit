# Session 2 - Culture
Notetakers: James Griffin, Nikitas Tampakis

## What cultural differences are we experiencing in our institutions and what challenges do they present?
### Resistance changing the way one works
 - Being unwilling to automate isn’t necessarily the challenge, but there is resistance often in letting go of old ways and where the direction to change comes from. ie peers vs manager.
 - Some find that there is an unwillingness to change because a person might be uncomfortable with the new technologies.

### Wanting to contribute, but lacking adequate knowledge or access
 - In a smaller institution, the backup is a small group of other librarians without technical experience. How do you bring others up to speed?
 - People with experience around a problem space, say working with Ansible for server provisioning, however, Ansible itself must be updated. What is the life cycle for this type of work?
 - There are cases where staff members want to contribute to a solution, but they may not have the technical background.
 - If one is hosting customized installations of ArchivesSpaces, with staff who want shell access to the servers. They cannot be granted root privileges.
 - On-call idea, operations staff are often on the hook for work that isn’t quite an incident response but is an issue that falls into a gap.
 - Challenges for team organization for vendor product support and applications you manage that integrate with vendor solutions.
   - There is a perception that you have more control over it than you do because it is possible to provide some JavaScript or other surface customization atop of the proprietary code base.
   - When addressing the vendor product customization and bug fixes, the workflow changes.
   -  There was recently a request to see what changes are being introduced to the vendor-produced system. While there are support tickets which were submitted, this and the internal documentation simply isn’t sufficient to communicate to stakeholders a list of change.
   -  Someone from the web team might be borrowed for improving the UI, while members from other teams might address code cleaning. However, there is no dedicated team for this specific vendor product.

### Accountability beyond the individual
 - Workflow where Jenkins is running on pull requests, pull requests shouldn’t be merged unless tests pass. However people go ahead and merge the pull request when the build fails if the failing tests appear unrelated to changes introduced in the PR. How do you help create a culture where people think beyond their immediate change, or failures that are outside of their own code?
 - There are challenges for some regarding the pressure around merging pull requests for GitHub.
 - Having a dedicated a single person to become an on-call person to address urgent issues has flaws.

### Lacking trust
 - Trust gaps tend to be the underlying issue when technical problems are encountered.
 - Others find that there might also be difficulty with the vision for new strategies promoted by administration. Past visions may have failed, and the confidence in this new direction shaped by DevOps is not there.
 - As a longtime staff member, there can be territorial disputes between teams/departments as new practices, tools, and ability to automate alter the way people work.


## What are some methods of creative positive cultural changes in an organization?
 - Hire a good manager. When you work on a team with folk who work really hard but it’s hard to quantify their efforts. Work with staff to determine an appopriate unit of measure. In the weekly meeting you go through the projects and in a blame-free way you discuss if you met last week’s quantified goal. Then you discuss why you may have not been able to reach the goal. In the team meeting, propose ways to change or enlist the help of someone else on the team.
 - [The Phoenix Project](https://www.goodreads.com/book/show/17255186-the-phoenix-project) is a recommended read. It’s a novel that describes the mindset of devops for people without an IT background to understand. It can help to create culture change.
 - Introduce automation for maintenance tasks in order to reduce the time spent on more menial tasks (e. g. Gem upgrades for Ruby applications).

### Addressing lack of skills or access
- To help colleagues can be limited in technical experience, One can document how to use a specific technology, and then have a colleague step through the tasks by following this documentation.
- For those without server/shell access, set up CI pipeline with access to dev/staging environments.
- For those who can't interact with the command line, they can use the GitLab UI to add Ruby files, and they work with developers and DevOps engineers to deploy these to the staging environment. Confidence in the pipeline and knowing where manual assistance is needed is vital to supporting this type of approach.
- For someone who is uncomfortable with a task, it is important to work towards bringing the team together and improve knowledge across the team.
  - Of course there are people with expertise and “go-to” people.
  - It is important to do this to make sure problems can be addressed in case the “go-to” person leaves your team/organization.

### Addressing overlooked and unforeseen issues
 - Might it be possible to take a different approach for ensuring that documentation and communication with these stakeholders becomes a part of the release process?
 - There are some who feel that all members of the team should be equally accountable for system failures.
 - Those who see the problem as contributors and maintainers for products are able to see some of these obstacles.
 - One possible strategy is to ensure that there are well-defined roles drawing upon the skillsets from each team member.
 - One of the principles of modern software development is that the team should be responsible.

### Take turns being in the "runner" role for the team's projects
 - There is a weekly process of assigning a different team member as a “runner” who monitors any errors that get reported across all applications.
   - Spend up to 30 minutes diagnosing and trying to fix the issue before opening up a Github issue.
   - It requires that the team member takes a look at various portions of the code that they didn’t write.
 - Helps team members feel a sense of ownership of their codebase that they didn’t write and their work in general.
 - Runner catches things that fall through. Operations observe a lot of the issues but developers pay attention to the issues more when they are in the runner role and can offer their insight into why there is an issue (and if it needs to be a cause of concern).
 - How do you deal with the runner role if there are too many errors?
   - People don’t always put a full half hour in if there are too many things going on, but 5-10 minutes should still be put in.
 - This is *not* an incident response person, as team we have incident management structured differently.
 - This is a role reserved for very low-impact bugs which are logged in response to user interface errors.
 - In the past, these bugs were too small in scope to be considered worthy of prioritization. As a result, these small errors were not addressed and forgotten.
 - Others have tried to implement the runner role.
   - It actually forced others to work cross-team in these cases, as there were various team members who developed code more independently.
   - It was fairly successful, but still was not sustained.
   - The applications were noisy, and everyone wanted to work to ensure that their applications were not noisy before disambiguating between major and minor bugs.
   - They couldn’t get to the point where these bugs could be fixed, and the apps could be tuned in order to reduce this noise.
 - The runner model had another successful implementation reported.
   - HoneyBadger was utilized here, and this runner prioritized without drawing them away from their current project during a scheduled sprint.
   - If the bug was a higher priority, then it would be brought to the attention of administration.
   - This also ensured that other team members had a broad and encompassing knowledge of all projects under development.
 - Encountering recurring bug reports and incidents within projects while "runner." These can be sorted into different buckets.
   - Certain applications have regularly scheduled downtime, triggering error reports. Hence, an uptime alert integrated with this might be preferred.
   - One limitation of error reporting platforms such as HoneyBadger is incidents can be logged excessively. However, Honeybadger does provide commenting features which ensure that users can provide better context.

### Open up channels of communication and build trust
 - For problems involving working on teams, there are periodic (typically twice a year) at least one-hour long retrospective meetings for the whole team to talk about pain points encountered recently and how the problems can be addressed to make things better in the future.
 - One of the positive principles of devops is safety and trust. Any efforts in communications to develop feelings of respect and trust can help build the foundation to allow discussions over tools and technologies to be handled effectively.
 - An observed approach for addressing system failures and major bugs has been the ability to communicate openly on Slack.
   - There are many who can respond and engage who are not directly involved in the maintenance or development of the project.
   - This also broadens channels for knowledge dissemination - some may not be developing an application, but may have been present.
 - Document decisions made in meetings in a transperent way so teams can look back and recall why certain design decisions were made.

### Fighting resistance
 - Convincing team members to adopt the usage of git:
    - In one case, it was quite difficult to convince colleagues and managers that version control for code bases was preferred.
    - At times, one needs to just use git and remain persistent.
    - If one is passionate, and lead the team in terms of using a tool such as git effectively, this can work to open the minds of more resistant colleagues.
 - Try new ways of doing things and brand it as prefessional development/experimental.
    - Formed a group, betech, bleeding edge technology. Worked on new experimental ideas.
    - Bring the proposal back to management after positive new change is already underway and proven to have a measured impact.

### Addressing technical debt
 - Scheduled maintenance days:
   - Some dedicate several days per month for exclusively addressing maintenance issues.
   - Generally take two days for addressing tickets marked for maintenance by a Century/Honeybadger.
 - When wrapping up a project/sprint/engagement, set up a retro specifically to address technical debt.
   - Have a discussion to identify areas where technical debt is accumulating or challenges that were encountered due to technical debt. How can these issues be improved and what can be automated?
 - Time should be built into work estimates allocated to address technical debt.

### Using Git/Github to collaborate and introduce application changes effectively
 - Forcing someone to merge a pull request into a code base, even when the continuous integration tests are failing, should be a practice avoided at all costs.
 - Some use GitHub to prevent the merging of branches without tests passing on CI and for test code coverage. By enabling this features, users absolutely cannot merge the branch (the button the UI is disabled).
 - Developing practices for using GitHub between team members has been successful.
