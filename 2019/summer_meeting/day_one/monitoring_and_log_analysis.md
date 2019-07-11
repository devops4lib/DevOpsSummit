# DevOps4Lib 2019 Summer Summit
## Monitoring/Log Analysis


Notetaker: James
Gatekeeper: Dan
Timekeeper: Cole


*Session started at 14:00 EDT*

## Monitoring, log analysis, and alerting
Can start with a problem statement, or with what we do well...
* What we do well and what we would like to improve
  * Who is feeling good about their monitoring situation?
  * Who is feeling anxious?
    * At least one attendee
 * Log Analysis
    * 5 felt as if there was work to do
    * Less happiness felt regarding this
### Log Analysis
* Princeton ships to Datadog
* Assumes that this separate service handles the data and invests heavily
* Some are not in the position to ship logs yet
  * For some, logs can pile in the Docker Container environment until they are otherwise purged
  * What is the plan for how this is going to be handled in the future?
  * Penn is considering Graylog (https://www.graylog.org/), have it in an environment where developers cannot access using SSH
  * Princeton/Francis has had good experience with Graylog
    * ElasticSearch can hit a wall
    * How ephemeral should the logs be?
    * It becomes expensive to maintain and recover a failing ElasticSearch cluster
      * This is often used to counter concerns regarding the shipping of logs to a third-party service provider
    * MIT did not consider building the entire cluster given similar concerns
      * Logs.io was chosen as opposed to hosting an ES cluster
    * How long does everyone retain their logs?
      * Francis retained 6 weeks of logs at Virginia Tech.
      * Princeton retains 2 weeks using Datadog
      * MIT retains 2 weeks
        * This still enabled incident response
        * Does not provide statistical analysis
      * Log retention for incident response vs. historical analysis
        * This is an important distinction
        * MIT has been working to ensure that this can be determined with stakeholders early in the process
      * No one seems to be using Splunk
        * It is highly recommended, but it can be costly
      * Princeton has so many logs
        * Solr is overwhelming in scale
      * Princeton is considering just abandoning this outright
      * MIT found this to be troubling as well, did experiment with tuning down the logging
      * Science History Institute found the warnings useful, but far, far too repetitive

### Knowing what to log
* Ideally, it would be best to have developers determine a useful level of logging for the production environment
* Datadog offers various different views for the levels of logs, the longest running applications, the longest running processes…
  * This definitely intersects with Application Performance Monitoring
* Without good searching support for logging, it definitely can work against operations professionals
* Princeton does not find logging to come from the applications, but from system services like Solr and NGINX

### Log Shipping and Centralizing the Logs
* Essential for forging linear paths for certain logs to be analyzed and stored
* Want to avoid cases where there are failures for large batches of logs uploaded to a service provider
* How to handle cases where a certain threshold of error messages indicate a failure
  * EBSCO API: Want to track that there are multiple error messages within a certain time window
    * Otherwise, ignore given that these messages can be generated without incurring service downtime
  * Logs.io does support shipping reports when suspicious errors are logged
    * This is helpful for identifying attacks against servers
  * Datadog provides Princeton with a threshold for log alerts beyond a certain ceiling

### Monitoring
* Does anyone have any monitoring problems?
* What are people doing generally for monitoring?
  * Some us ping monitoring
  * Now, with PostgreSQL, have streaming replication
  * Grafana (https://grafana.com/) and Prometheus (https://prometheus.io/)
    * Scraping the logs in order to determine the health of services
    * Need to avoid filling /var
  * Prometheus
    * Scrapes metrics between services at set intervals
    * Not engineered for accuracy in the logs
    * Generates metrics for alerts and ensuring that the service is available
  * Grafana
    * Used for data visualization
  * NetData (https://www.netdata.cloud/)
    * Used at Princeton and is configured for reporting with Slack
    * Useful given that servers have it installed by default
      * Helpful in order to ensure that random alerts can be easy to track
    * Some are shipping NetData metrics to Prometheus
  * Logging application-specific alerts
    * Want to avoid situations where the application is down but the server is up
    * Datadog provides some automation
      * Uses AI to mine for certain trends or anomalies
      * Finding changes in the average latency for page loads
    * Skylight (https://www.skylight.io/)
      * Used for Rails
      * Provides some basic reports for performance monitoring (e. g. slowest endpoints)
      * “Pain” ranking for these types of performance problems
    * Cleaning log data for security-sensitive information
      * Can be undertaken at the level of the VM before it is shipped
      * Clients may also have this logic included (depending upon the service)
    * Retaining Metrics
      * One is never going to find a problem unless they are actively following the metrics constantly
### Alerting
* So much of these is around communicating structures and escalation paths
* Some are alerting by e-mail and text messaging, but the majority are alerted by Slack
* Slack Channels
  * Many have more than one channel where alerts are published
  * Some dedicate channels for interrelated, grouped services (e. g. web services running a digital repository ecosystem)
  * Some have more important alerts publishing into a channel reserved for developers (hence, trivial alerts can be ignored but major failures receive immediate notice)
* Runner/Triaging Application Errors
  * Princeton has a weekly runner role
  * A team member will follow Honeybadger errors captured from applications
  * They attempt to diagnose and resolve the issue within 15 minutes
    * If this is not possible, they at least create an issue on GitHub
    * This is to ensure they are productive with other team members on sprints
  * The role is a rotating one, hence this should not fall to any single team member consistently
* Noisy Alerting
  * There are alerts where developers or operations professionals simply do not respond
    * “That’s a normal alert, it always does that”
    * If the team does not respond to an alert, this alert should not be issued
* Prometheus
  * Collect metrics and determine rules for sending alerts
  * Alert Manager (within the Prometheus stack) is used to configure how often the alerts are sent
    * Suppressing alerts when certain conditions are reached
    * How frequently to send the next alert
    * etc.
* Datadog
  * Princeton might need a runner for alerts more generally
  * It becomes problematic to contextualize certain alerts without configuration of specific monitors on the service
* What are the expectations for alerts generally?
  * Is there one person who should triage them?
  * Should there be a team member who leads the diagnosis?
  * Some rely on an ad-hoc method where a developer will attempt to resolve the problem
    * If they cannot resolve it quickly, they might simply delegate it to someone else
  * Need to avoid cases in large teams where there is an unspoken assumption that someone (not themselves) will address the problem
* Google SRE Procedures (https://landing.google.com/sre/books/)
  * Penn is looking to implement these practices
    * Different Slack Channels for different projects
* Onboarding and Documentation
  * Want to avoid having only a small circle of people with access to Datadog, Honeybadger, other hosted services
  * Need to ensure that instructions are included in the issue for the problem
  * Runbooks
    * Have a set of documented steps for resolving specific steps
    * These runbooks should be managed under version control
  * Alert should link to a page/issue in the repository where team members can access the instructions for resolving the underlying problem
* Alert Infrastructure
  * Alerting infrastructure must be one of the most stable and valuable elements of the overall infrastructure
  * Alert Manager in Prometheus does provide some features which ensures that cascading failures could be avoided

*Session Concluded at 14:55 EDT*

