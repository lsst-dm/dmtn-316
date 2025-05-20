# USDF Rubin Application Operations Support Model

```{abstract}
Support model for Rubin applications in the US Data Facility.  This includes Rubin application team roles, incident management, problem management, service management, and release management.
```

## Problem Addressed

A structured operating model is critical for ensuring the availability, reliability, and security of the Rubin Applications. By implementing standardized processes, roles and communication, USDF will minimize downtime, and optimize resource utilization.

Specifically the Rubin Application Operations Support Model is intended to:
* Provide role clarity
* Standardize processes to streamline work
* Improve ability to respond to issues

### Application Support Model

### Application Roles

Each Rubin application should have the following roles defined to manage and operate the application.  A person can have more than one role and may be condensed.  Below are the roles and responsibilities required for each role.

| Role | Responsibilities |
| ---- | ---------------- |
| Application Sponsor | Responsible for assigning resources |
| Application Owner | Responsible for the overall application functionality, data, and user experience |
| Database Administrator | Responsible the database’s design, performance, security, and maintenance.  Not required if there is no database |
| App Infrastructure | Responsible for the infrastructure configuration, deployment, and routine maintenance |
| Operations Support | Responsible for the support of the application.  Handles alerts, application monitoring, application incident response |

### SLAC and Rubin Team Infrastructure Roles

Below are the roles and responsibilities for the SLAC and Rubin Infrastructure teams.

| Role | Responsibilities |
| ---- | ---------------- |
| Infrastructure Services Support (Physical) | Responsible for physical datacenter, servers, storage, and networking.  This includes Weka and Ceph. |
| Applications and Users (Virtual) | Responsible for the virtual infrastructure, Kubernetes cluster, vClusters and Kubernetes Weka Storage.  The DBA is on this team and is responsible for Butler and providing subject matter expertise to help the App DBAs. |
| Astro Domain / Rubin Specific | Understanding Science Operations, Teams, and Roles.  They may also be application owners. |

### Application Tiering

Application tiering is needed to align the operations model to supporting key Rubin processes and capabilities.  This will be used as decision support for the following type of scenarios:
* When there are multiple issues occurring and the team is constrained on what they can work.  Higher level application tier applications will be prioritized.
* When there is a Kubernetes node hardware failure and there are limited resources to run everything
* During disaster recovery to prioritize which application needs to focuse on first to restore service

Below are the proposed application criticality levels.

| Tier | Definition | Impact of Failure | Examples |
| ---- | ---------- | ----------------- | -------- |
| Mission Critical | Most important application. Essential for success of Rubin | Required process will not run | Embargo Butler, Prompt Processing, PanDa, Sasquatch |
| Critical | Applications that are essential for day to day operations, but not as crucial as mission critical | Can cause significant delays, disruptions, or reduce productivity | ConsDB, Rubin Science Platform Nublado |
| Operational | Applications that support science functions, but are not considered essential for the immediate functioning of work | May cause disruptions, but not major ones |  Exposurelog, RubinTV, LFA |

The tiers for applications will be identified as part of the operations checklist activities.  The application tiering can change over time and will change for some applications after commissioning.

### Monitoring and Alerting

The USDF Grafana is used for monitoring and alerts.  Prometheus is the main source of application and infrastructure metrics.  Loki is used to capture logs from applications.   Below are are the requirements and design for monitoring and alerting.

## Monitoring and Alerting Requirements.

Below are the requirements for monitoring and alerting.

* Application issues should be identified proactively and not by end users.  This will take time to implement.  As new issues are reporting by end users part of the remediation process will be to create alerts if there is missing coverage.
* Application logs volumes should be reviewed to ensure they are not filling up log storage.  Debug level logs should only be enabled to troubleshoot issues.
* Sensitive data such as passwords should not be logged.
* A red/yellow/green stoplight dashboard is required to provide an at a glance view of the health of USDF applications.

## Monitoring and Alerting Design

* Alerts will be created for known application
* Application Alerts should be created in Grafana.  A Slack channel will be created for each application for these alerts.  Today all alerts goto `usdf-alerts`.    New Slack channels will be created for each application domain.  For example `usdf-alert-production-alerts`.  It is the responsibility of Operations Support to monitor and respond to these alerts.
* Tags for each application domain will be added to Grafana.  A red/yellow/green stoplight dashboard will be created to show alerts by application family to provide a summary view of USDF alerts.
* Dashboads will be created for each application domain to provide a summary view of health, performance, and issues.
* Squadcast will be used to provide alert management and route alerts.

### Operations Checklist

## Incident Management

### Reporting Incidents

Slack channels in the Rubin Observatory Slack instance are used to report incidents.  Below are the Slack channels, purpose of each, and who is responsible for monitoring the Slack channel.  Threads should be used to organize the discussion of individual issues.

| Slack Channel | Purpose | Responsible for Monitoring |
| ------------- | ------- | -------------------------- |
| usdf-on-sky-support | Channel for issues, questions, and support requests for USDF related to LSSTCam on-sky commissioning.  Should be limited to issues that have an impact on decisions about commissioning activities at the summit on (roughly) 12- to 48-hour timescales | |
| usdf-support | USDF user support channel. Intended for issues by end users  | |
| usdf-infra-support | USDF infrastructure support channel, i.e., intended for developers of USDF-hosted services to raise support issues related to USDF infrastructure | |
| usdf-rsp-support | USDF Rubin Science Platform support | |

To monitor the Slack channels a

## Problem Management

## Service Management

## Release Management