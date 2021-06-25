# How-to-impliment-the-Splunk-Security-Suite
Splunk Security Suite

The splunk Security Suite consists of Splunk, Enterprise Security, UBA and Phantom.
As with all Splunk products these are highly customisable and can be used in a number of configurations.  Whilst this flexibility is a great strength it also adds confusion as to the best method to use the collective features and capabilities.  This project aims to offer ‘an optimal’ configuration to be used for security operations centres to implement the Splunk Security Suite.

Each Splunk security suite element has its own function, strengths and weaknesses.  To determine the optimal configuration we must first investigate these characteristics and aim to best utilise the strengths whilst avoiding the weaknesses.

Splunk & Enterprise Security
Splunk ES is a premium app added to the Splunk Enterprise platform.  Splunk ES offers the prebuilt Dashboards, Alerts in the form of notables and the Splunk CIM.  Splunk ES elements include:
-Preconfigured Alerts (saved searches - notables)
-Modular Macros for reuse in Searches
-Apps to transform logs into the Splunk CIM format.
-Analyst Dashboard
-Threat Intelligence ingestion and incorporation
-Flexible log ingestion
-Powerful search language
-Highly capable correlation searching
-Effective store and search for logs, device data, network data, user data, TI and reference tables/information
-Log storage and archiving structure that facilitates; rapid search, retrievable archives and long term archiving.

Splunk UBA
Splunk UBA uses machine learning to baseline behaviours and creates anomalies from events that deviate from that baseline.  UBA threats are created when a number of anomalies combine into potentially malicious behaviour. Splunk UBA elements include:
-ML generated threats (and/or anomalies) sent to Splunk ES (or Splunk)
-Dashboards useful for threat hunting
-Dashboards for anomaly exploration
-Dashboards for User investigation
-Account to user aggregation
-At event time IP to host to user correlation

Splunk Phantom
Splunk Phantom is Splunk’s SOAR offering.  Originally designed to be SIEM/Data source agnostic.  Using Python based apps and service APIs, Phantom is able to interact with most security tools and where existing connections are unavailable custom connections can be created.   Originally Phantom was limited to SOAR functions but now includes case management and is intended to be the primary interface for analysts.  Splunk Phantom elements include:
-Automation through python coded ‘playbooks’
-Python coded apps to connect to mist security tool APIs
-Analyst interface for conducting investigations
-Case management for including analyst notes, tracking actions and maintaining timelines
-Workbooks for central store of SOC SOPs, that enforce required behaviour and store investigation actions, results and conclusions.
-Note taking to be conducted on the SOAR platform using workbooks

Responsibilities for SOC Roles
A modern security operations centre has many responsibilities.  These responsibilities range from alarm triage to SOP creation and incident investigations.  To best utilise the Splunk Security Suite it is essential to first understand the tasks that it will be used to accomplish.  The roles incorporated into the operations of modern SOCs are:
Monitoring/Incident Response
-SOC L1
--Triage Alerts
-SOC L2
--Resolve understood incidents using SOPs
-SOC L3
--Investigate and resolve unknown incidents 
--Creating SOPs from investigations
--Refining alerts 
--Creating alerts
TI/Hunting
-Incorporate relevant TI into the SIEM
-Analyse TTP from TI to create new alerts and related SOPs
Risk/Vulnerability Management
-Conduct regular scans to detect known vulnerabilities within the network
-Resolve known vulnerability alerts using SOPs
-Analyse TTP and TI to create vulnerability scans, detections and remediation SOPs
Event/Incident Management
-Store all alerts for the required period in an easily searchable format
-Store all response notes for the same retention period as alerts, in a way that is easily searched and related to the original alert
-Be able to group alerts into incidents, whilst still maintaining the separate alert information
-Store response actions and resolution results with the case notes and alert information, to enable alert refinement, SOP creation and SOC metrics
-Generate metrics on SOC operations such as:
--Time to detection
--Time to assign
--Time to triage
--Time to resolve
--Number of alerts per period
--Number of escalations
--Number of false positives
--Number of addressed true positives
Log Management
-Store all device logs for a specified retention period in an easily searchable manner
-Archive all device logs that exceed the retention period, but are still under the time span for investigation relevance, in a manner that can be returned to an easily searchable format
-Provide long term storage for logs historical logs

Combining Roles and Capabilities
Combining each of the Splunk Security Suite’s elements strengths with each SOC Role’s requirements is core to this concept. This method will provide a theoretical best practice that SOCs can use a template for integration.  As reality often clashes with theory in many places, it may not be possible to use the structure exactly and areas will need to be adjusted to fit into each enterprise’s individual requirements and restrictions.
Concept of Operations

Concept of Operations

Splunk Enterprise forms the central core of the suite.  It is the repository for all logs, threat intel, vulnerability scans, network users and network devices.  It provides infrastructure for collection, storingage, archiving, effective searching and alerting.  Splunk Enterprise Security can be added to augment the existing capabilities providing pre-built searches, dashboards and macros.  
Splunk UBA augments the detection capabilities of Splunk Core (and SplunkES) by adding machine learning alerting to the existing correlated search alerting.  Whilst these new alerts can be viewed and worked within UBA it is best to forward the alerts to the central storage platform Splunk Enterprise.
Custom Alerts from Splunk Enterprise, Notables from SplunkES  and threats from UBA will all be searchable within Splunk Enterprise.  Scheduled searches can be used to forward the events to Splunk Phantom.  Searches should draw these events in logical groups that align with the associated response, such as by Mitre Attack Tactic or Technique, vulnerability scan result etc.  Aligning events in this manner enables Phantom to automatically apply the appropriate Workbook to the event.
Analysts will interact with events and external services through Splunk Phantom.  Having the SOAR tool be the central area of operations reduces the number of touch points that analysts must interact with.  Ideally all actions associated with routine operations should be conducted within Phantom, and as many non routine operations as possible.  It is unreasonable to expect that all investigatory tasks can be accomplished within a single tool, as such we can expect advanced investigation actions to require the use of many other tools as the incident requires.  However all case notes, records of actions  and results should be stored in Phantom as notes to ensure that all of the relevant information is stored in a single central searchable location.
Upon ingestion of an event Phantom shall apply the appropriate workbook for the analyst to follow, and conduct all routing enrichment actions.  The analyst will receive guidance on recommended actions from the workbook, execute appropriate automation playbooks and add other relevant workbooks as required.  Having workflows structured in this way ensures a more consistent format of actions, results and records.
Routine events will be resolved using the steps outlined in the associated workbooks.  Every event should be tagged with the appropriate information, highlighting potential water action steps and reporting metrics.  Workbooks and events will not be able to be closed unless all of the necessary tags and comments are included.  This enables effective after action analysis, metric collection and false positive notification.
If escalation is required the analyst will execute an escalation playbook that will assign the event to the appropriate team.  Investigations are conducted using whatever means are necessary, however as all actions conducted in Phantom are automatically recorded with the event and case notes, there is an advantage to conducting as much as possible there.  All external actions will need to have notes recorded in Phantom to maintain the record of actions.
