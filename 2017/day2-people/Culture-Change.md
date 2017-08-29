# Shifting Culture / Culture Change

## What do we mean by these phrases?
* Metrics / Measurements
* Infrastructure as code - e.g. making the right thing easy to do.
* There is an invisibility to devops, it's only visible when things go wrong.
* A successful shift is dependent upon a process of shared goals and the communication thereof.
* Google published a doc talking about psychological safety - should be ok to fail.

## What are examples of culture change working well?
* Alex
	* Implementing a CI/CD process
	* Devs having control over shipping code. Ship it and turn it on later.
	* There was a delay between commits and production results.
	* Bepress was different than earlier jobs.
		* Shipped a feature that wasn't ready.
		* What?! You're not allowed to ship to production!
		* But 100 pushes went perfectly!
		* Oh? There's value to shipping to production? Ok, cool. We can manage that.
		* Used feature flags to ship features much faster in a measureable way.
		* Went from shipping features in a few months to in a few days.
		* By making meetings more interesting for manager, everyone had higher morale.
	* Comments:
		* Being able to show the value right away is not always possible. Need to get buy in.
			* True, but this situation was different, didn't need to get buy in - not typical for most folk.
		* Liked, Learned, Lacked, and Longed-for.
		* Liked that the process showed 'the visibility of devops behinds the sceens'.
* Kevin
	* Were using Puppet, wanted to explore ansible
	* Took small projects and wrote in ansible
	* Success in small projects allowed for shift to ansible
	* Puppet faded away because examples of ansible were easy to communicate.
	* Success was due to test and experimentation on a small scale.
	*Comments:
		* Moral of the story is small achieveable goals
		* Early easy win
* Jeremy
	* Code Review seems to be a bellweather for success.
		* It's not just the quality of the code, but making sure that the code that's being worked on is a good strategic decision.
		* Pairing looks like it costs twice as much, but it can have critical value.
* Chad
	* Tried to get one of his ops folks up to speed and involved with new tool (ansible?)
	* Person said, if I wanted changes, why wouldn't I just grab a snapshot from other resource and just go from there?
	* Chad had so much implicit knowledge, maybe didn't do a good job of communicating the value.
	* Comments:
		* Erin - long list of similar conversations
			* Virtualization, trying to get everything on one machine.
				* Confuses dependencies on each service. What's required to get a thing running?
			* Folks saying - This is needlessly complex. Lots of resistence.
			* Better to start at what the perceived problem is. Then get to a solution from there.
			* Training program - "Answers are in the room!" - Get buy in from people in the room.
				* Start asking questions, proposing ideas.
			* The natural process of a river to flow around its topology (politics, culture, etc)
* Kieran
	* Rephrasing Erin: "Be like water my friend" - Bruce Lee
	* Politics and culture are among the features of a landscape that guide where the river flows.
* Francis
	* Some times you just can't reach a person.
	* Had to go to an intermediary
	* Comments:
		* Kieran - Sometimes an intermediary is the best route, it's a good faith avenue to use sometimes.
		* Aaron - Sometimes you need to just assign people duties you know they can accomplish
		* Erin - There are team members that are systems thinkers and others who are detail oriented
			* Neither good nor bad, both are necessary
			* Devops is more systems thinkers
			* Some folk can't talk about emotions
			* The way to surface these things is:
				* Have conversations even when folk aren't interested in conversations, but you can:
				* ask them what their ideal work environment is?
				* what do they enjoy working on?
* Alex
	* Humans exist in an environment larger than work
	* Sometimes you can't get a person to be effective, and maybe that's a point where you have to ask them to leave,
	* But, again, trying to find things that they can/will do can be significant. Reorienting how you think of what they can contribute.
* ?
	* Service level agreements
	* Currently baked into their vm hosting solution, can just spin up machines.
	* Task/mission to upgrade kernels. Contacted managers about up/down time related to these hosted services.
	* Projects involving backups for services. There are concerns about this.
* Alicia
	* (in reference to above) Earlier we were talking about intra-group culture change. Now it's inter-group culture change.
* Kate
	* Bringing in stakeholders into the conversation, i.e.We need to make sure people understand what 100% uptime means!
* Daniel
	* Trouble explaining to people what 100% uptime costs.
	* Here is what the financial picture is for what uptime means.
* Kate
	* Similar negotiation but about number of records going into a repo.
	* Asked for time to plan for disaster recovery.
	* So, if bad things happen it's not a catastrophe and doesn't take long to recover.
* Alex
	* Sounds like we're talking about bringing all these implications of a service up front
	* It's slow! - style complaints
	* This necessitates a agile approach so that we can prioritize needs.
* Alex
	* John Alspah? Writes a lot about safety.
	* A lot of devops stuff comes from hospitals and airlines
	* Culture Survey - When a person comes with a problem, what kind of response do they get?
	* Responses kept coming back super good reviews. Was he just not perceiving things as others?
	* Comments
		* Dan - didn't trust survey or that it was anonymus or lack of retrobution.
* Alicia
	* Similar to feelings of code review - 
	* Purpose and effect of survey
	* Some people might 
	* A lot of the shared culture here requries a common understanding
	* If it's to find who to blame:
		* retrospectives won't be good
		* code review
* Kieran
	* Biggest success from biggest failure
	* This is an idea 
* Erin
	* Embracing reality and providing hope.
	* Flip side is, when we're having conflict:
		* Being right isn't always being effective.
		* Identifying where people 
* Alicia
	* Being dead right isn't any better than being dead wrong (you're still dead)
* Alex
	* Corporate b.s. - Strive for success and expect nothing less (ugh)

## General Comments
* Stakeholder anxiety - You're telling me how awesome this is, BUT i can't see what the immediate benefit is.
	* What if it doesn't work??
	* If we define an explicit scope and an explict cut off, this failsafe eases stakeholder anxiety
	* Issues can be addressed in retrospectives
	* If the retrospective goes really well, another iteration could always be campaigned for again in the future.
	* this raises the next big question (below)
* Big Question -
	* How to engage in culture change while not immediately putting people on the defensive.
	* This is an emotional intuition skill.
	* Requires a healthy self-awareness.
	* Often ties in to having (or not) a sense of psychological safety (safety to fail).
	* When things go wrong, who's there as a safety net?
	
## Tips
* Have talking points - what is the shift about? what is it trying to achieve?
* Having a strategy about approach
* Experimentation using small projects at first
* Take time to understand the other side (app vs dev, etc)
	* Foster an environment encourging diversity of stakeholder viewpoints.
* How people feel about using a tool should factor into the evaluation of its success.
* Use a solution that "meets people where they are" in order to get more involvement, contributions
	* id est, have a low on-ramp
	* Note obstacles to participation, address specific issues
* Have a practice where the less experienced can attain effective feedback from the more experienced
* Using code reviews is important for devops
	* Allows for better quality of code
	* Allows for ensuring continual good direction of choices for code work to be done
	* Can require emotional intelligence because code reviews can be high anxiety for some devs
	* Code review is a forcing function between two minds, still must entail a good emotional bond for good teamwork results
		* Id est - code review itself is a venue for continually growing/building good teamwork

## Characteristics
* Be strategic
	* Have a goal
	* make it achieveable (experiment in small steps)
	* fold in current culture
	* fold in current politics
	* be willing to accept no sometimes
	* Use an appropriate tempo for change, guided by stakeholders

## How to measure success
(didn't quite get to metrics for measuring success. A topic for next year!!)
