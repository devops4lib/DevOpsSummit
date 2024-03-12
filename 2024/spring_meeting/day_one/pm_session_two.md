## Afternoon Session Two

* Topic group: Security topics
    * Secrets Management (x2) / Password Management
    * Tactics For Staying On Top Of CVEs (Common Vulnerabilities And Exposures)
    * "DevSecOps" - what is it? How is it different from DevOps?
    * Standards and practices regarding compliance with information security organizational and institutional policies.

### Session Notes:

DevSecOps - what is it?
* Working collaboratively on security issues between developers and systems teams
* Think earlier on, building into process
* Automation
    * Github, automated security alerts, somewhere in pipelines
        * Brakeman
        * Dependabot
        * Secrets detector, gitleaks
        * Web application firewalls against bots
    * Operating systems processes
        * Weekly scheduled job to patch systems
* Data protection rules; e.g. GDPR, HIPAA (patient data)
* Secrets management is part of security
    * Scout
    * Snyk

Frustrations in this space
* How do we reasonably incorporate security practices without being overly restrictive?
* How does one make exceptions and accept risks?
* Crowdstrike mandates -> the appeal is its reporting capabilities but has vulnerabilities
* Can we trust firewall?
    * Exceptions to port 80/443 access, fill out lots of forms
    * Central IT may not be able to help

Scanning Docker images/containers for vulnerabilities?
* Harbor for repository of images, scanning built in
* Trivy scans built containers

More strict requirements based on the sensitivity of data
* GDPR, HIPAA, etc.

Ransomware to destroy data
* Any vulnerable service can lead to cascading issues

ADR - architectural decision records
* Can fill in any gaps when individuals have to make big decisions for security or policy in absence of an organization wide policy

CVE Discovery
* tools in this space
    * Rapid7
    * Dependabot
    * Scout
    * Snyk
    * Trivy / Shiftleft
* REDCap software with patient data
    * Semi-open source from Vanderbilt
    * Severe security issues were found
    * Tension between revealing vulnerability but also needing to advocate for acting immediately when the news of the vulnerability is intentionally kept hidden
* Common practice is to warn communities that an important upgrade is coming, announcing solution around the same time as the vulnerability
* Cybersecurity agency name I missed that does scanning
* Sometimes software so far behind that the vulnerability hadn’t been introduced into the software yet
* End-of-life website
* Comparing list of components against registry
* Containers running for over two years, regularly rebuild them, initiating automated scans
* If you don’t run pipeline regularly you don’t know that there is a vulnerability - could have scheduled jobs to proactively run tests and rebuild containers, auto deploy to QA environments

Secrets Management
* Individuals vs shared credentials
* Try to avoid getting root credentials to avoid secret management?
* No individual or root passwords, log in with SSH keys
* Ansible Vault different from Hashicorp Vault
    * Hashicorp has some crazy features that makes it difficult to unlock (e.g., multiple people required to unlock)
* AWS secrets manager to lookup creds
* No secrets in your code repo
* Dealing with staff departures and they have a key
    * Citadel
    * Also rotate credentials in an automated fashion
* OIDC & Azure AD can both be used with HashiCorp Vault to unlock
* Two-factor authentication - using personal devices or working with shared accounts (service accounts)
* Password management lessons learned
    * Spreadsheet
    * If a tool is too difficult, people will try and work around it, harming an overall security model
* Automated credential “rolling” (generating and setting new credentials)
    * With some limits, e.g., vendor-established API keys
