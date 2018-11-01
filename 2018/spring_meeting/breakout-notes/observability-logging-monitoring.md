#Observability, Logging, and Monitoring
##Logging
Everybody logs - how do we make them usable?

Q: Who feels like they do logging really well...?

...NYPL implemented a logging standard across languages [See here](https://github.com/nypl/ruby_nypl_log_formatter)
* Standardized formatter, js, ruby
* Rails app log is opinionated, but others go into the standard log format
* JSON format
* Standard capitalization
* Standard keys
* Spec defined using RFC words - MUST, OUGHT, SHOULD
* Flexibility - Also allow arbitrary keys
* Helps debug distributed applications across multiple services
* Common keys across apps like UUIDs
* Logs aggregated - cloudwatch, loggly
* Query using JSON, JQuery notation
* Build alerts on top of logs
* Consolidated time series information - Compute statistics across logs
* Contentious point - syslog defines ints mapped to log levels, but no other languages respects it
* Where do the logs go? Depends on service (aws/cloudwatch vs www.loggly.com)
* Both services provide visualizations
* Push notifications from SNS, use a lambda to open JIRA ticket…
* Apache logs go to log.ly
* Loggly has an API, but nypl has syslog forward to loggly
* ECS and lambdas have stdout sent to cloudwatch
* Spec is open, ruby gem is open (subclasses the ruby standard logger), maybe js npm module?


Lograge ruby gem for making Rails logs not suck

Q: What Makes A Log Not Suck?
* Easy to filter to what you want to see
* Log only appropriate information (you ain’t gonna need it)
* Good logs tell you what happened, not just that something went wrong.
* Really good logs can tell you what’s about to go wrong

Q: What’s the difference between good logging and instrumentation?
* Instrumentation is what you want to display, profile. you can do this with logging if it's your only tool.
* Instrumentation is not info/debug-level messages

Having the logs constantly displayed on a monitor is good for awareness of your application

##Monitoring
Q: Is there anyone that has defined a good monitoring solution around DB’s, applications, etc.?
* “Slow Jam” tool starts a timer whenever a request starts, builds a profile of slow-running method calls and what data was involved, uses statsd (from etsy) as a common protocol 
    Q: does it monitor the datapoint for alerts?
        No, that uses ELB
* https://pypi.org/project/slowjam/#description

Recommended to not run your own statsd, buy service from data dog

Alerting
NYPL queries logs for alertable information
Stanford runs puppet tied to nagios (nagios stands for Not Awesome)
* Nagios NRPE (remote plugin executor) triggers commands on remote box to check logs, db, etc.
* Use honeybadger for observability (email, api alert, etc)
DynaTrace good for tracing all levels of the stack, heavyweight logs, highly configurable
Skylight for Rails apps, free for open source
Rollbar for exceptions, generous free tier
Sentry provides logging API for every language, good for stripping PII

Implementing logging and alerting can immediately lead to fixing bugs, but if you have a culture of ignoring logs, they quickly become useless.
If error reporting is turned on when there are too many errors -- are you prepared to deal with the consequences?  
If there are too many false positives in logs/alerts, it’s ultimately counterproductive.
Maybe it doesn’t need to be an alert, just aggregated and logged (CPU utilization etc.)
Send critical alerts to a Slack channel that buzzes phones
Amazon only alerts on customer-facing issues… What are our institutional goals? Optimize alerting for those.
Stanford has noisy alerts, even in the middle of the night if you’re on call, as long as they’re actionable -- because there isn’t good logging…  tried to parse nagios logs for historical data? But that’s not the point of nagios

Get you a tool that can do both (data dog)

Sometimes the monitoring service is erroneous/fails… employ multiple services to corroborate

AI for logging?  Log it all and let AI sort it out?

Q: What are the different levels of alerting?
 *   Email
 *   Phone
 *   Slack
 *   Pages

Stanford employs an SLA hierarchy, categorize alerts by SLA: low, medium(10/7), high(24/7)
New applications are assigned an SLA… political/organizational decisions
Response times… 24hrs, 6hrs, 30min


Q: Are there alerts for when things go right?
Well, there’s Dead Man’s Snitch, which alerts if something that’s expected to go right, doesn’t.
 * Long running processes issue alerts on successful completion
 * A feel-good alerting channel sounds nice…
 * Alerting on anything out of the ordinary 
 * “This job has gone X days since the last incident”

Personally Identifiable Information
Does your org require scrubbing PII, does your org have record retention policies?
What is considered PII?
Log disks encrypted, dumped after 30 days
If search terms are in the URL, and URLs are tracked by Google Analytics, and Google tracks user identity… it becomes PII
Have a privacy policy for GDPR
What about data from third party services that comes to us containing PII?


##Metrics
