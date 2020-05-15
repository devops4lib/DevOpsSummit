# Session 4: Incident Response

Notetaker 1: Jeremy Prevost

Notetaker 2: James Griffin

## Initial Topics

- Managing your team members in an incident response
- Testing ability to restore services
- communication outward
- Response template / report outs
- How do we learn from incidents

## Managing your team members in an incident response
- Overview of what people are doing
    - Emergency services incident command system as background. First person in scene is incident commander until someone with more experience shows up. Are others in library tech doing similar / different things?
    - Small team: response may be reflected by how the problem was brought to the team (whoever noticed first is stuck with it, can hand off to others if they get stuck). Sometimes devs get first alert, sometimes operations depending on the system that triggered the alert. With only one person they sometimes need to take time away to focus on communication. Post mortem after event.
    - Process for not big down time, but possibly persistent / cross team: #incident_response slack channel. Post, start a zoom. Real time communication. Possibly implemented unevenly so it’s hard to know if it’s working well or not (different teams may be interpreting the process slightly different)
    - Incident response is a dedicated team (using ServiceNow). Initially started with library IT was part of central IT (no longer the case). Many ways to file a problem. Many of the issues coming in these channels are operations focused, more than developer. Developers will be called in if appropriate. Triage via managers. SLAs are used to prioritize. ITIL
    - Many ticketing systems, but for incidents focus on what needs to get done. ServiceNow used but not preferred). Nagios often is the starting point for a slack alert channel, hot words added to control level of noise being notified (slack feature, not nagios). When something important shows up, communication to move to a slack channel to chat. May move to zoom if real time is needed. Often leads to tweaks in monitoring to ensure improved response time in the future. See pager duty response plan (Note: we’ve talked about this in the past as well and it is indeed good).
        - Incident commander / deputy / scribe / liaison (internal / customer) / operations are some roles in the response plan. Commander is assigned based on-call schedule.
    - Lots of incidents lead to getting better at them! Lack of commander led to lots of people trying to help but nobody coordinating. Some use the Netflix Dispatch tool (please see below). This is really good at post mortems, but Netflix too has all of the gathering involved to create that while hopefully creating more clarity while incidents are ongoing.
    - Dedicated slack incident response channel helps prevent two people both trying to restart the same server at the same time, etc
    - Seems to be two types
        - We all come together as a team
        - Single person creating and assigning tickets
    - Other patterns for incident response are also followed
        - Experience with a group structured like a startup focused upon online learning
        - Many P1 incidents, separated security incidents from incidents for the application being maintained
        - All logs were sent into a Bucket from AWS CloudWatch
        - These were then fed into Splunk
        - Datadog and OpsGenie were also used in coordination with team
        - There was a business on-call person, a DevOps on-call person, and a single developer as an on-call person for an entire week
            - Only DevOps engineer would receive the OpsGenie notifications - 
            - Zoom/Skype was used to ensure that there was immediate communication, along with a Confluence page being created in order to detail the solution, as well as to identify precisely what the problem was, and how it was fixed
            - Project Manager sometimes involved in order to take over communication to organization.
        - There are cases where one DevOps engineer is a new member of a team
            - Every incident for new colleagues is a new opportunity to learn, particularly with regards to the diagnoses
            - Follow-up on incident reports is also essential, particularly if a report is drafted at the end
- Testing Service Restoration
    - Successes
        - Staging environment can be built by restoring backups
        - One can regularly destroy staging and test the restoration from the most recent backup
            - However, one oversight is that older backups were not tested (only the most recent was tested)
            - There are now procedures in place to restore older backups also
    - Strategies for restoration
        - Regularity
        - Automating the restoring process has been worthwhile (also documentation is needed)
            - AWS is used exclusively in one case
            - There are automated test suites, for a process implemented using Ansible Playbooks
        - How do you establish confidence in this restoration process? Can fire drills be used?
        - For some, twice per year there is a user submission in a production ETD system which is problematic in some way
            - This requires a developer to diagnose this issue
            - Cannot use production, so a snapshot is restored into a QA environment
            - Once the diagnosis is made, then the same changes will be applied in production
        - Can AWS provide one with the ability to test restoration across regions of service?
            - AMI snapshots are used in this strategy, and using these across regions can be very challenging
    - Hot Fixes in Production
        - A new QA environment can be spun up as a single instance on a VM
            - MongoDB, MySQL, and the app would be integrated into a single virtualized environment
                - This single VM would model the services distributed throughout the cluster, and would be used for diagnosing the incident
            - It would otherwise be cost prohibitive to recreate staging clusters on-demand for diagnosing bugs
- Incident Reports
    - Many produce incident reports, which include actionable items derived from these
        - How are these incident reports drafted? How are action items created?
    - For some, once the incident is fixed, there are few other follow-up action items
        - Many times there might be smaller tickets created, but these are usually addressed promptly
    - For others, a meeting will need to be scheduled
        - Business owner, the lead developer, the manager from the DevOps/operations team
            - There are times when a HR representative would attend in this case (as a stakeholder)
            - This followed the policy of the business owner
        - Following the meeting, an e-mail would be issued to the larger team in order to provide an explanation of the incident and service outage
    - Additional Post-Mortem Meetings
        - Things which we did well, things that we need to improve upon
        - Did we effectively communicate with stakeholders? Perhaps we tagged them on GitHub, but should have
    - Terminology
        - I’m seeing Post-Incident used frequently  instead of post-mortem
        - The Incident Command System calls it After Action Report
    - Incident Retrospective Meeting
        - A template is used to structure the meeting
            - Generate the report and action items from the exchanges during the meeting
            - These action items are prioritized, and a monthly discussion regarding their status is used to ensure that these get addressed
    - Some organizations have to work within a change management process
        - For one case, the change management meetings are held twice per week
        - A change management document is referenced and frequently updated to ensure that incident management can be addressed more efficiently

## References

### Acronyms and Term Definitions
- Incident Command System: https://www.fema.gov/incident-command-system-resources
- ServiceNow: Enterprise bug tracking, project, and IT process management platform: https://www.servicenow.com/products/service-portal.html
- SLA: Service Level Agreement
- ITIL: Information Technology Infrastructure Library (this is a process framework used to standardize IT organization management procedures - please see https://www.axelos.com/itil-update)
- Nagios: open source monitoring solution: https://github.com/NagiosEnterprises/nagioscore
- PagerDuty incident response templates: https://response.pagerduty.com/
- Dispatch: https://github.com/Netflix/dispatch
- ETD: Electronic theses and dissertations management system
- AMI: Amazon Machine Image
- “Before Liftoff!” by Henry Cooper
- Post Mortem sometimes called After Action Report or Post Incident
