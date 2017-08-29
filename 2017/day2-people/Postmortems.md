# Postmortems
One way to define it is in contrast to a retrospective. Where a retrospective is an event with a somewhat regular schedule (post-sprint, etc), a postmortem tends to occur at the end of the lifecycle of a thing. Often it tends to arise as an event after some significant issue that a system or team encounters. For a postmortem, it's a deeper dive and often a larger portion of the system of topic needs to be called into question.

## What are the components of a "good" (successful) postmortem?
* Facts are important (like from a police report)
* but human-perspective content is just as important.
* A good postmortem should be an opportunity to step back and re-evaluate the priorities or necessities of a service.
	* An example: Waking people up for a service with a 24/7 requirement in the SLA. If people are being woken at 2am, is this really needed?
* Psychological safety is critical for the efficiency and productivity of teams.

## What are the components of a "bad" postmortem?
* Blame is at least unproductive and can be counter-productive.

## Challenges
* Psychological safety can get us far, but there are limitations. Can't quite say "implementing this feature will make our staff safer". Could come off as Chicken Little.
	* Shifting to "Psychological Health" can make it easier to carry this idea/conversation further.
		* However, could get to a point beyond limitations of manager's expected or reasonable asked for skill set.

## Strategy
There's a strategy here that can be implemented in two overarching steps:
* Incorporate either regular or more frequent postmortems
* Ensure that there is an entity (individual, group, rotation) that reviews postmortems in order to discover and surface patterns.

## Method to Incorporate Postmortems
* Incorporate into refactoring?
* Moving from kanban style work to sprints for devops work, adding postmortems (like end-sprint retrospectives)
* Lowering the bar of postmortems from major incidents (outages) instead to "close calls"

## How to ensure pattern surfacing
(not much conversation on this point yet)

## Other notes:
* amazon published a postmortem about a very public failure.
* ibm exec says (after major failure), "fire you? i just spent 3 million educating you! Now what are we going to do to fix it?"
* John alspah writes a lot about mostmortems (arenas of health, manufacturing, and airlines, etc).
* Blameless postmortems! (turning postmortems on their head)

## Resources
* Surprisingly applicable: [A Field Guide to Understanding 'Human Error'](https://www.amazon.com/Field-Guide-Understanding-Human-Error/dp/1472439058/ref=sr_1_1?ie=UTF8&qid=1504034085&sr=8-1&keywords=a+field+guide+to+human+error)
* Also very applicable: [Drift into Failure](https://www.amazon.com/Drift-into-Failure-Components-Understanding/dp/1409422216/ref=sr_1_1?s=books&ie=UTF8&qid=1504033671&sr=1-1&keywords=drift+into+failure)
