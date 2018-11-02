Do we have a problem statement? 

## Observability

- Coined by Charity Majors https://charity.wtf/
- Frequently used in distributed systems to have an overview of your ecosystem

Profiling can be added in this. (the ability to (graph) trace all the calls made in an application)

* Skylight.io is a Ruby application profiler
* Jaeger Golang application profiler  https://www.jaegertracing.io


## Logging

* Elasticsearch is hard to administer (breaks -seems to- on major upgrades) jvm headaches etc.
* Logz.io (is a hosted ELK service) and/or AWS Elastic
* Are people using Syslog-ng for centralized logs
* Just in time analysis for when things break 
* Logs for slowly executed attacks (for forensic investigation needs) 
* Save aggregated statistics (or generate a report)

## Monitoring

* Nagios used by Penn State. New Relic unsuccessful in making the case for moving to a NR solution. NR would be a good option if Penn State needed up to the second
* Honeybadger for exception tracking for Temple and Princeton
* Pingdom 
* Logging alerts (Penn State wrote a script to grab last 5 lines of logs and ships to slack)


## Alerting

Logging alerts (Penn State wrote a script to grab last 5 lines of logs and ships to slack)


## Metrics

Prometheus (operator makes a native service object in Kubernetes cluster to monitor itself) 
