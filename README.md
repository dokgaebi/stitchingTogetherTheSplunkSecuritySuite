# How-to-impliment-the-Splunk-Security-Suite
Splunk Security Suite

The splunk Security Suite consists of Splunk, Enterprise Security, UBA and Phantom.
As with all Splunk products these are highly customisable and can be used in a number of configurations.  Whilst this flexibility is a great strength it also adds confusion as to the best method to use the collective features and capabilities.  This project aims to offer ‘an optimal’ configuration to be used for security operations centres to implement the Splunk Security Suite.

Each Splunk security suite element has its own function, strengths and weaknesses.  To determine the optimal configuration we must first investigate these characteristics and aim to best utilise the strengths whilst avoiding the weaknesses.

Splunk & Enterprise Security
Splunk ES is a premium app added to the Splunk Enterprise platform.  Splunk ES offers the prebuilt Dashboards, Alerts in the form of notables and the Splunk CIM.  Splunk ES elements include:
Preconfigured Alerts (saved searches - notables)
Modular Macros for reuse in Searches
Apps to transform logs into the Splunk CIM format.
Analyst Dashboard
Threat Intelligence ingestion and incorporation
Flexible log ingestion
Powerful search language

Splunk UBA
Splunk UBA uses machine learning to baseline behaviours and creates anomalies from events that deviate from that baseline.  UBA threats are created when a number of anomalies combine into potentially malicious behaviour. Splunk UBA elements include:
ML generated threats sent to Splunk ES (or Splunk)
Dashboards useful for threat hunting
Dashboards for anomaly exploration
Dashboards for User investigation
Account to user aggregation
At event time IP to host to user correlation

Splunk Phantom
Splunk Phantom is Splunk’s SOAR offering.  Originally designed to be SIEM/Data source agnostic.  Using Python based apps and service APIs, Phantom is able to interact with most security tools and where existing connections are unavailable custom connections can be created.   Originally Phantom was limited to SOAR functions but now includes case management and is intended to be the primary interface for analysts.  Splunk Phantom elements include:
Automation through python coded ‘playbooks’
Python coded apps to connect to mist security tool APIs
Analyst interface for conducting investigations
Case management for including analyst notes, tracking actions and maintaining timelines
Workbooks for central store of SOC SOPs, that enforce required behaviour and store investigation actions, results and conclusions.



