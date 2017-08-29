# Observability & Monitoring / Tuning

## The Good, The Bad, and Maybe Something Ugly - Monitoring
Start with something we're doing well, then something we'd like to be doing better.
* Francis
	* Need improvement on: Black box monitoring using Nagios.
		* Really just asks: "Are you up?"
		* Generates lots of noise. Flapping, etc.
	* Doing well: Implemented "NetData".
		* Wonderful fancy dashboards
		* Wanted to setup Promethus, but Promethus does not do access control where NetData does.
		* NetData feels lighter than Promethus.
		* Delivers on all things Nagios does but does it better
			* De-dups alerts.
		* Needs to do:
			* CPU usage
			* Memory usage
			* etc
		* Ships with sane defaults.
* Brandon
	* Uses "Icinga"
		* Very like Nagios, basically up or down.
		* Can setup alerts for vm system.
		* Found bitcoin miner!
			* Tomcat wasn't up to date, security leak, bitcoin miner was using the box.
		* Simple metrics.
		* Now doing logging through Splunk.
			* Security breach triggered security lockdown and usage of splunk. Centralized logging.
		* Same plugin architecture as Icinga.
		* Free version is more frequently updated.
* Kieran
	* The Good:
* Chad
	* NewRelic for "Servers", won't continue with "Infrastructure", need a new solution.
	* Leveraging NewRelic Ruby and Java agents.
	* Using Monit for server monitoring
	* Not using anything like Nagios, so... hoping things work?
* Daniel
	* (I was typing and didn't get it captured)
* John
	* Very good and solid setup with Nagios
	* Zabbix is on the todo list
	* NetData is also on the todo list
	* Setup union graphs so that ramp up with utilization is discoverable.
		* Not good for real time.
	* Munin - keeps historical graphs. Uses RD databases to keep stuff.
		* Good for real time?
	* Checking out UFW (available in rhel environments).
* Alicia
	* Also has a very good setup with Nagios. If it's yellow or red, there's actually a problem.
		* This may be because there's not a lot of traffic on most of the boxes.
	* Pain point - Secondary attributes (SSL certificates, maybe adding CNAMES)
	* Transition from sandboxes to production environments.
* Kevin
	* Tried NewRelic for a while but ended up not purchasing it.
	* Uses Nagios but not totally happy with it. Glad to hear recommendations of other tools.

## The Good, The Bad, and Maybe Something Ugly - Tuning
* RIFF is bad.
* Java 7 to Java 8 is hard.
* Mostly, we're throwing cpus and memory at tuning problems.

## List of Tools
* Monitoring
* Tuning
