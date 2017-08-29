# Observability & Logging - 1PM
* What issues are we looking to solve?
	* Log retention policies
	* Manual versus automagic logging tools
	* Logging aggregation - the ability to effectively query for specific behaviors
	* Dockerized solution where each container logs to stderr or stdout and then off to a remote store/aggregation.
	* How do we separate out the audit friendly or audit required from the noise? (incredibly chatty)
	* Some folks are using basic logs, some folks are using spunk or ELK, or mtail, etc
	* Major sticking point regardless of strategy is log noise.
	* Greylog (front end search for elastic search)
		* Solves need to apply access controls / permissions for logging?
		* The 'E' from ELK can be crazy expensive (paid version necessary for access control / permissions)
	* Essential first step is to decide what it is that you want from your logging tool before deciding on the implementation.
	* Search-Guard project - a possible solution. Role based access application. Can get out of sync with Elastic Search.
	* Greylog just uses the API for elastic search. Open source project that does a lot of what ELK does without the cost.
		* Greylog is a UI to elastic search
		* Greylog uses filebeat
	* Honeybadger is another tool in the arena. Very specific tool for very specific purpose. A tool like Rollbar.
	* Reducing noise!!
* What kinds of things do people want to do with their logging tools?
	* Want to make sure only the right people are logging into the servers. Validation of user login.
	* One person says that normalizing the data in Greylog or similar tools is a herculean effort.
	* The ability to do retrospectives is, say, there was a security breach.
	* On the application side
		* Here are stats about the usage of the system
	* There are two distinct but overlapping arenas of logging:
		* System logs
		* Application logs
		* User logs? outside application, like google analytics?
	* Seems that the important thing is really *knowing what your use case is*
	* Heroku kinda forces you to write a 12 factor app.
	* Access control for logging is important for:
		* Government reporting
		* Patron identifing data - IPs, etc
		* There is some importance from the perspective of historical need.
		* Are the history department students using [X] application? Otherwise, it doesn't deserve funding (according to administration).
	* Reporting / Alerting (might be a different kind of thing than logging or monitoring)
		* It kinda goes from Logging to Monitoring to Alerting. 

## Deliverables?
* A list of use cases.
* A list of tools, with a basic feature set for each.
* After listing use cases and tool features sets, create mappings between use cases and tools.
* After creating mappings, can create recommendations for most popular mappings.
	* This could be great for grants or compaigning stakeholders for time to pay technical debt.

## List of Use Cases
* Access control for logging data
	* Government reporting
	* Patron identifing information.
	* Historical context
	* Traffic history as justification for funding.
* Debugging clustered applications
	* Which box of a particular role is it?
	* Clustering of logging would help alleviate this issue.
* Exception logging - More of a developer centric kinda thing
	* Honeybadger or Rollbar - could communicate out to slack
	* However, debugging process may need to drill down to a dependent component causing an exception higher up the call stack.
* Security Logging
	* Insuring that only the appropriate users are accessing servers etc.
* Trust but Verify logging (application level stuff)
	* Dedups and transfers jp2s from one location to another.
		* When initalizes
		* When starts
		* When completes
		* etc

## List of Tools
* Logging
	* Honeybadger
	* Rollbar
	* Promethus / Graphana
* Monitoring
	* Huginn - builds agents to take actions based on events.
	* Techstack
	* telegraph
	* influxdb
	* chronograf
	* kapacitor
	* Veem
* Alerting
