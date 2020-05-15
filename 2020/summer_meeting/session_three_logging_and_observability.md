#Session 3 - Logging / Observability
Notetaker 1: David
Notetaker 2: Daniel 

Stack
Francis

##Notes
Who keeps your logs these days? (FK)
APM? Pros/Cons? Worth it? (AG) (Application Performance metrics)
What are folks doing for monitoring these days? 
Automated alerts - what do you keep track of, how do you get notified

##Observability Definitions:
* See what is happening inside a running application
    * Log streaming
    * Metrics
    * Services to view inside the code
* Compared to tests see what is happening inside the environment distinct from the tests

##What types of tools people are using:
* Honey Badger to Splunk
    * Use splunk to colocate logs.
* Logsz.io as a central log repository 
* Cloudwatch
    * Amazon’s centralized logging solution
* Fargate
    * Container system in AWS
* Sentry and Heroku Dashboards
* Data Dog
    * Uses Elastic Search
    * Help avoid log bloat/disk space issues when getting crawled
* Multiple people have mentioned using mixes of these systems
* Nagios being used for up/down monitoring such as disk space or not-unusual issues
    * Nagios being used to monitor nagios
* Icinga is a re-implementation of Nagios which is free and cool and very configurable (helps if you speak german). (https://icinga.com/)
    * Much better interface than Nagios.
* Sematext (https://sematext.com/)
    * Like Data Dog without venture money
    * Eastern european company that is involved in Solr codebase, can be used for other issues but it is being used to handle Solr
    * It does have a local hosting option
* New Relic
    * Error Reporting
* For uptime and if sites are working, Site 24x7 (https://www.site24x7.com/)
* Logs scattered across many machines
* A problem with data dog or the like is that you need to choose who is “worthy” to be included. Where being able to log the whole environment is much nicer, but that is resource intensive.
* People mention Honeycomb
    * Biggest issue is that it’s looking for full orchestrated container infra.
* People want a tool to throw everything at, it has been seconded as a concern.
* Graylog
    * Being used at the dev level where Data Dog costs are not work it
    * It’s a front end to elastic search, and a pain point is dealing with Java is not a favorite thing to do.
* Set up an Elk (Elasticsearch Logstash Kibana) Stack last year but couldn’t convince my boss to adopt it. (https://www.elastic.co/what-is/elk-stack)
    * Liked that it’s free and scalable
    * Was not able to convince my boss because he thought we would spend too much time maintaining it.
    * Wondering how much labor it is to maintain?
    * Cautionary talk of Elk stacks:
        * It is well documented and easy to stand up, a good eco-system
        * Until you have a disk failure
            * You now need to be really good at elastic search to come back from it
            * I am shaking at this, nobody deserves that.
            * Greylog is robust and has a good support model, you can use Logstatsh if you want
                * You can buy support for it which is good.
* Elastic search and management concerns
    * So many people manage Solr and the concerns aren’t that different?
    * Is it right that there was a desire to find a tool distinct from both Solr/Elastic not that Elastic is uniquely bad compared to say Solr
    * A desire for sane defaults and settings
    * Many people are using Solr and well, but there’s a lot of hidden steps or details we can’t tame or other people don’t see
* In terms of what to log and where
    * Using AWS Elastic search for stuff, have a tier that keeps logs for a day (QA/Dev) to handle retention and worry about a longer retention only for production.
* A lot of what we are discussing is logs to detect problems with applications but wondering if people use logs to gain understanding user patterns and analytics. 
    * Logging everything can capture more and be more effective than analytics.
* I’ve come across users wanting to not use logs to do analytics in favor of other tooling.
* Trying to track user behavior to see when users are struggling or finding an issue does not work the way we want it to.
* The point made about the value of logs as a valuable way to see user activity can also make them a dangerous source of user PII. How do those of us that ship them out look at cleaning those logs to mitigate that risk or have folks given up that fight?
    * Data Dog by default has a do not ship statement so you have to be explicit about what you do shape to them.
* For PII in logs there is the intent of being able to handle the log data before it gets sent out. You’re paying for 15 days of retention but you don’t know how long they are holding onto it.
    * Clean or sort out data before sending it out mentioned as a benefit of control of the data
* With Beats and Logstash you can do data sanitization.
* One thing we’ve been doing is working on a gem called ahoy to capture some of our analytics.
    * It’s a gem that dumps all these user inputs into a database that can then be analyzed.
* https://docs.meilisearch.com/
* We run a dockerized version of motomo.
* APM can be integrated with tools like Honeybadger and it is useful for looking at what is happening to a product/service.
* Collaboration and optimization: are we collaborating at the right at the right level?  If we are all using Elastic Search, why aren’t we doing it together?
* A lot of us are going to be handling some serious budgetary constraints soon and we’ll want to be able to help collaborate and that may be an important efficiency to help get through the hardships that are on the horizon. 
* The #devops slack channel has a bot that asks “what are you working on this week” which is a nice way to initiate collaboration.


###Alerting
* How do people stop the email (I get 100s of email every single day).
    * Put them on a slack channel and ignore the channel.
* Used to be a network admin and used a tool called tweet (old school late 90s tool) which can convert content to audio noises. Used Nagios with gentle sea sounds so the noise wasn’t stressful to be able to “hear” the state of the systems.
* https://sensu.io/ Plugged for helping the too many emails/slack messages as it is smart enough to know Person A has already been alerted about this
* In line with noisy alerts if they’re noisy all the time you don’t pay attention to them.
    * If things are too strict, you can modify things so more people than a single overwhelmed person pay attention
    * Eventually you become numbed to things and sometimes you need many alerts from many places to get your attention.
    * Maybe having different things go to different places (#channels) to avoid too much noise to any one place.
* Another tool mentioned https://mmonit.com/monit/
* Sort of joke, sort of true
    * Disregard most stuff, and I have a sense for some things being important. This is “zen”
        * This is **not advice**
    * You can be lucky to catch the right things, or if information floods us.
