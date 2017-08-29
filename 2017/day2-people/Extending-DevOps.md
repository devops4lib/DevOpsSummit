# Extending DevOps Across the Organization
* Erin
	* Back to: "If you have devops in your title, you're doing it wrong."
	* Should be a method engaged by all involved, rather than the responsibility of one or few individuals.
* Alex
	* Cherity Majors?
		* Devops should be at the top. CEO should be the chief devops officera
* Kieran
	* 
* Chad
	* What are the goals that we're trying to accomplish.
	* Trying to accomplish more regular, frequent updates to production (for example).
* Erin
	* Devops wants to have specific environments setup.

## Who is our Audience?
May need different messaging for different audiences.
* Sysadmins
* DevOps
* AppDevs
* Managers
* Administrators
* Service Stakeholders

## What are we extending?
We are extending an understanding of necessary divergence between two opposing "forces for good". This understanding needs to be shared among the various audiences. It's great when devops practices are implemented in a grass roots fashion, but sometimes it goes laterally from ops to devs, other times the value of it needs to be communicated up a heirarchy (managers) so that it can come down from above to other teams / individuals.
* Stability, Predictability (ops)
	* The focus here might be "Automation". We should be able to automate everything so that:
		* We get devops out of appdev's way
		* We free up our time to work on other more challenging or innovative projects.
	* The workload coming in should be predictable, we should know what our priorities are.
* Volatility, Innovation (devs)
	* Here, the focus is more on "Agility"
		* we get to just do the work and not get hung up on ops "territory".
		* We get more time to "just do the work".
	* The workload coming in should be open to shifting targets in order to capture innovation.

## How do we extend it?
In the earlier section, a vision was elucidated for what it is we are trying to extend. Here, we talk about how to extend it.
* Surfacing inefficiencies
	* In the Ops world, our focus is on stability, dependability, and predictability. That being the case, we must focus much more stringently on having a problem free {process, environment, atmosphere}. However, that leaves us without the ability to compete in what seems to be the only competition for time - id est, having problems to prioritize.
	* If we shift our perspective from our day to day scope to instead include *opportunity cost* and/or *potentiality* into the conversation, then we can then participate in the negotions of what priorities to spend time upon.
	* In order to present those inefficiences, we must *surface inefficiencies*.

## Technical Debts
What a dev thinks of as technical debt and what ops thinks of as technical debt can be very different things. This should be identified as part of the effort to communicate needs and values of the opposing forces that together help create worthwhile services.

## What are the metrics?
How can we track technical app or ops technical debt?
* create backlog tickets for technical debt
* How much time does 'x' step take? How often is it done?
	* This can help prioritize when to automate a task.
* Dependency tracking
* Code metrics

## Deliverables
* Could pull in devs to do maintenance sprints focused specifically on gamifying the elimination of technical debt.
* Could utilize a system where the threshold of time dedicated to technical debt increases until a ceiling. (Northwestern's model).
