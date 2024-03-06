# Monitoring

* Facilitator: Francis
* Note Takes: James, Carla 
* Gatekeeper: Nikitas

## Proposed Discussion Items

* Group: (Observability?) Monitoring, metrics, analytics, validation, e-resources (17)
    * Monitoring (x4)
    * Dashboard development
    * Analytics/metrics (beyond web analytics)
    * measuring usage of repository materials
    * What frameworks/software etc,people are using for statistics
    * How people validate their e-resources
    * What frameworks/software etc,people are using for statistics
    * NISO RP-26-2019 / NISO RP-26-2019, KBART Automation: Automated Retrieval of Customer Electronic Holdings KBART Automation (files publishers send out) / Automated Retrieval of Customer Electronic Holdings
    * Metadata transformation pipelines

## Notes

* Who has a monitoring problem?
    * Understanding which platforms are being used
    * More than basic analytics, capturing metrics for which platforms are being used
* Open Telemetry ([https://opentelemetry.io/](https://opentelemetry.io/)) 
    * Feels like a “push”-based system
    * Application and Open Telemetry communicate…
* [Prometheus](https://prometheus.io/)
    * A prometheus servers reach out to application to retrieve metrics and capture them in its system
* Splunk
    * Log analysis
    * Also, there are alerts which can be configured
        * One team does not read logs
    * Grafana ([https://grafana.com/](https://grafana.com/)) and Prometheus are used
        * Grafana visualizes the metrics, and provides visual indicators for anomalies (e. g. spikes and dips)
        * Should there be alerts or anomalies, this will trigger a discussion within a Slack Channel
    * There are time series logs of all metrics from server infrastructure
        * CPU, RAM, disk I/O, network I/O, queries-per-second (for specific services)
    * Is the cheaper alternative because its shared across the university
    * APM via logs (could be argued that its not as good as DataDogs APM)
* Datadog ([https://www.datadoghq.com/](https://www.datadoghq.com/)) 
    * Application Performance Metrics (APM)
        * For every “unit of interaction”, Datadog will tell you how much time was consumed within specific layers of the application, server, or network stack
    * 80% of time might be spent on a single method invocation within an application code base
        * Datadog provides this depth and level of detail
    * The service itself can be prohibitively expensive
    * Cost of Datadog is a perpetual fight in the department
    * The metrics have been used also to provide proof that third-party/vendor-hosted services are the source of slowness
* For those using Grafana and Prometheus, queries triggering alerts will be logged, and then the queries will be rerun
* New Relic
    * Another APM, very well praised (“[...] is amazing”)
    * Very expensive
    * Bought New Relic to solve specific problem and then canceled
* Splunk is used to partner across a University
    * When every IT department at the organizational level is required to use Splunk, costs can be saved
* Short-term intense monitoring and then moving to a more relaxed approach
    * Multiple teams have engaged in this strategy, one citing a major application migration as an example
    * Used Datadog for only a 2 week burst of activity
* APM services do not always only parse logs
    * They can have tracer libraries which are included within the application code base
    * (e. g. Datadog Ruby client: [https://docs.datadoghq.com/tracing/trace_collection/automatic_instrumentation/dd_libraries/ruby/](https://docs.datadoghq.com/tracing/trace_collection/automatic_instrumentation/dd_libraries/ruby/))
* ruby-prof
    * [https://github.com/ruby-prof/ruby-prof](https://github.com/ruby-prof/ruby-prof)
    * Free and good for estimating where time is consumed within the control flow for the application
    * Used within the production environment
* [OpenObserve](http://OpenObserve.ai)
    * [https://openobserve.ai/](https://github.com/openobserve/openobserve) 
    * Promise of Datadog but you have to manage it yourself
* What are you trying to track using these metrics?
    * If a team is trying to determine whether or not a feature set is being actively used, should they use APM?
        * Is Google Analytics better for these cases?
        * No, and GDPR (General Data Protection Regulation) introduces many problems from a legal standpoint
            * Anonymization is impossible for EU users when Google captures the information within the logs
        * One alternative is to use Matomo
            * [https://github.com/matomo-org/matomo](https://github.com/matomo-org/matomo)
            * Anonymization has been successfully implemented by at least one team
        * Plausible
            * Google analytics alternative
            * https://plausible.io/ 
* Sending logs to a separate vendors could be non starters at some institution
    * And then it would fall on devops to implement something locally
* Plausible ([https://plausible.io/](https://plausible.io/))
    * This is another alternative to Google Analytics
* Team Exercise
    * Identified applications, and then defined their core mission
    * Defined requirements to ensure that the applications are fulfilling their required needs
    * Which measurements can the team take in order to determine if they are fulfilling their respective missions?
        * Perhaps metrics can be retrieved in order to make these determinations, however, is everyone on the team comfortable with this approach?
* Impact Assessment
    * One team is interested in the demographics for usage on a given website?
        * Having this PII is a huge advantage
        * Student app where students can reserve spaces within the library
            * Using the PII, the vast majority of reservations were submitted through the app rather than a website
* Reports for Stakeholders
    * Stakeholders are interested in broad data (how many page views?)
    * Internally, would like to have more detailed reports (e. g. this library system experienced a sharp increase in activity)
        * Perhaps this is due to an increase in non-library users?
        * Require PII at some level in order to understand these trends
        * Then, anonymize the data after some threshold period of retention is exceeded
    * Funding issues drive the need for reports for stakeholders that could require some more personal information
* PII for EZProxy
    * Discard personal identifiers, but aggregate other PII in order to identify user demographics
    * EZParse is utilized by some to identify demographics within the users for certain library resources
* How do you deal with non-human user-agents (crawlers, bots)?
    * Try and use the logs to identify bots which are ignoring set robots.txt restrictions
    * There are bots which increase indexing, which then increase discoverability from search engines
        * Those bots which are truly impacting performance of servers are manually blocked
* Deprecating Services
    * One team was looking to deprecate a LibGuide
    * Yet, using analytics, it was determined that more than 20 visits for certain pages was a regular occurrence
* [Signal Sciences](https://www.signalsciences.com/products/)
    * Now owned by Fastly ([https://www.fastly.com/products/web-application-api-protection](https://www.fastly.com/products/web-application-api-protection))
    * Tool which was very good at permitting bots to crawl sites or applications, but provided set windows
    * Cost prohibitive
* How to manage crawlers?
    * throttling 
    * Try to think about the problems that monitor cause and address those crawlers, create static sitemap
* Fail2ban (Apache Plugin)
    * Another semi-automated tool for blocked crawlers and bots
* ByteSpider
    * Crawler from ByteDancer, blocking by user-agent was needed
* Geographic location of crawlers
    * Identify anomalous locations and regions to consider blocking
* Limiting Functionality to Authenticated Users
    * Cannot exploit the SMS or e-mail features unless you are logged in
* Cloudflare
    * Rebalance between server nodes and HTTPS load balancers in response to certain user-agents or IP addresses
    * Requires reshuffling DNS
    * Cloudflare can handle millions of transactions per second
    * Cost prohibitive
* Cost
    * 5/9 of availability will cost money
    * 3/9 will not cost nearly as much
* Misidentified as Bad Actors
    * Institutions after reorganizations have been identified as bad actors
    * This is due to using a specific vendor for load balancing
* Identifying Bots
    * User-Agents within the HTTP server logs
        * SemRush, Yandex…
    * More malicious actors will know how to mask this information
        * Really good packet-inspection is required, usually by a hosted service
    * There are also public lists of bot names
    * There are also libraries which consume these bot lists
        * Ruby Gem exists: [https://github.com/biola/Voight-Kampff](https://github.com/biola/Voight-Kampff)
    * [fail2ban probably uses these exact same lists](https://www.globalcallforwarding.com/wp-content/uploads/2022/04/high-availability-chart.png)
    * Resource for user agent strings:  \
[https://deviceatlas.com/blog/list-of-user-agent-strings](https://deviceatlas.com/blog/list-of-user-agent-strings) 
* [Cost Difference between 3/9 and 5/9](https://www.globalcallforwarding.com/wp-content/uploads/2022/04/high-availability-chart.png)
    * Trying to push this conversation more towards the institution
    * There are cases where teams wish to ensure that 100% uptime is not possible
        * 5/9 might not be possible given resources (3 minutes of downtime per year)
        * Propose that a policy be established by administration or managers if increased uptime is required

_Session concluded at 11:50 EST_
