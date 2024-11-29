# Monitoring and observability
=======================================
=======================================


In the fast-paced world of DevOps, ensuring your systems are running smoothly is just as important as deploying them. 

Monitoring and observability play a key role in ensuring that any issues are identified and fixed before they impact the users. 

Monitoring refers to tracking specific metrics over time, while observability helps you understand the internal state of the system based on the data it outputs.



### Metrics :-

Metrics are numerical data points that represent the health and performance of your system.

#### Real World Metrics Example :-

The "Metrics" in this context refer to the ongoing monitoring of a patient's vital signs (BP, Heart Rate, etc) with the nurse taking measurements and recording data at specific intervals. 

This information is then used by healthcare professionals, such as doctors, to ensure the patient receives the necessary care based on their current condition.

#### DevOps Metrics Example :-

In DevOps monitoring, metrics are crucial for tracking the performance, stability, and overall health of applications, infrastructure, and services. 

Examples of Metrics :-

Infrastructure :- CPU utilization, disk I/O, network latency.

Application :-  Response times, error rates, request rates.

Pipeline :-  Build success rates, time to recover from a failed deployment.

Security :-  Number of detected vulnerabilities, failed login attempts.


`In DevOps, Monitoring involves tracking key metrics, displaying them on dashboards, and setting up alerts to notify teams when something goes wrong.`


`Metrics are like vitals in healthcare, constantly monitored to ensure the HIMS system or patient remains healthy.`

`Alerts are triggered when something is wrong, similar to when a patient's vitals go out of range, or the system's CPU usage exceeds safe limits.`

`Dashboards are used to visualize complex data, making it easier for DevOps engineers to keep track of system performance, and for doctors to monitor patient health.`


Monitoring these metrics allows you to detect problems early, scale resources when needed, and make sure the application is always ready.


## What is Monitoring ?
============================

Monitoring is the process of collecting, analyzing, and using data to ensure that your system’s components (servers, networks, applications) are working correctly. 

This is usually done by tracking specific metrics like CPU usage, memory consumption, and network latency. 

Monitoring tools also set thresholds for these metrics, triggering alerts when they go out of the acceptable range.

#### Example of Monitoring in Action :-

Consider an e-commerce site. 

You have hundreds of users shopping, and the checkout page suddenly becomes very slow. 

Monitoring systems will track the response time for that page. 

If the time exceeds a certain threshold (say, 2 seconds), it will trigger an alert so the operations team can investigate and resolve the issue.


## What is Observability ?
===============================

Observability goes a step beyond monitoring by helping you understand why something went wrong. 

It uses data, logs, and traces to give you a holistic view of your system's internal state.

Observability allows you to troubleshoot complex problems, even if you haven't predicted a specific failure scenario beforehand.




## Differences Between Monitoring and Observability
============================================================

While monitoring answers the “what” of an issue (e.g., CPU usage is high).

observability answers the “why” (e.g., a specific microservice is causing a memory leak). 



## Prometheus
===================

Prometheus is an open-source monitoring and alerting tool widely used in DevOps to track system and application metrics. 

It collects, stores, and analyzes time-series data and is especially suited for cloud-native, containerized environments like Kubernetes.


#### Prometheus in DevOps Monitoring :-

`Data Collection` Prometheus scrapes metrics from various endpoints (servers, containers, applications) using HTTP. 

Metrics are in the form of time-series data (e.g., CPU usage over time).

`Storage` It stores the collected metrics in its time-series database, enabling efficient querying.

`Alerting` Prometheus integrates with the Alertmanager to send alerts when certain conditions are met, such as high CPU usage or service downtime.

`Visualization` Prometheus can be integrated with tools like Grafana to create dashboards for visualizing metrics and trends.



## Grafana
================

Grafana is an open-source platform for monitoring, visualizing, and analyzing data in real-time. 

Grafana is a powerful open-source platform used for monitoring and observability.

It connects to various data sources like Prometheus, Elasticsearch, and MySQL to display metrics on customizable dashboards.

Grafana helps DevOps teams monitor system performance, detect issues, and set alerts when specific thresholds (like CPU usage) are exceeded. 

Its real-time visualizations and interactive dashboards make it easy to track infrastructure and application health, enabling proactive monitoring and quick troubleshooting.

In addition to its powerful data visualization and analysis capabilities, Grafana is also highly extensible. It supports a wide range of plugins.


#### Why Use Grafana :-

`Unified View` Grafana allows you to combine data from different sources into a single view, providing a holistic view of your system’s health.

`Customizable` Its flexibility makes it easy to build dashboards tailored to specific needs.

`Extensible` Plugins and integrations expand Grafana’s capabilities.

`Collaborative` Team-based access control and sharing features make it ideal for collaborative work.

`Proactive Monitoring` With real-time visualizations and alerting, Grafana helps you catch and resolve issues before they impact end users.

#### What are the features of Grafana ?
 

It provides a variety of features that make it a popular choice for visualizing metrics and logs. Here are some of the key features of Grafana :-

`Data Source Integrations`

Supports a wide range of data sources, including Prometheus, Graphite, Elasticsearch, InfluxDB, MySQL, PostgreSQL, AWS CloudWatch, and more.

Allows combining data from multiple sources in a single dashboard.

`Dashboards and Visualizations`

Create and customize dashboards with a rich set of visualizations like graphs, charts, heatmaps, tables, and more.

Provides a drag-and-drop interface for easy dashboard creation.

Offers templating features to create reusable and dynamic dashboards.

`Alerting`

Define alert rules based on Prometheus, Graphite, and other data sources.

Configure alert notifications to various channels, including email, Slack, PagerDuty, Microsoft Teams, and more.

Manage alerts with the Alerting UI, providing an overview of alert states and history.

`Annotations`

Add annotations to graphs to mark events, deployments, or other significant occurrences.

Integrate with external sources to automatically generate annotations based on events or alerts.

`User Management`

Role-based access control (RBAC) to manage user permissions and access to dashboards and data sources.

Supports single sign-on (SSO) with OAuth, LDAP, and other authentication methods.

`Plugins`

Extend Grafana’s functionality with plugins for data sources, panels, and apps.

Community and commercial plugins available to enhance capabilities.

`Explore Mode`

Ad-hoc querying and troubleshooting interface for deep dives into data.

Allows switching between different data sources and running queries interactively.

`Reporting`

Generate and schedule PDF reports of dashboards.

Share reports with stakeholders via email or other distribution methods.

`Annotations and Events`

Annotate charts with key events, making it easier to correlate events with metrics.

`Time Series Analysis`

Advanced time series analysis features, including transformations, calculations, and aggregations.

Support for multiple time ranges and comparison of different time periods.

`Variable Support`

Create dashboard variables to filter and interact with data dynamically.

Use variables in queries to create dynamic and interactive dashboards.

`Teams and Organizations`

Organize users into teams and manage permissions at the team level.

Create and manage multiple organizations within a single Grafana instance.

`Provisioning`

Automate the creation and management of dashboards, data sources, and alerts using configuration files.

Support for declarative configuration management with YAML or JSON.

`API and SDK`

REST API for programmatic access to Grafana resources, including dashboards, data sources, and users.

SDKs available for building custom integrations and plugins.

`Kiosk Mode`

Display dashboards in a full-screen, read-only mode suitable for wall displays or NOC screens.
Customizable Themes:

Support for light and dark themes.

Customizable color schemes and branding options.

#### What type of monitoring can be done via Grafana ?


`Infrastructure Monitoring`

Server Metrics: Monitor CPU usage, memory utilization, disk I/O, network traffic, and other vital server metrics.

Network Devices: Keep track of network switches, routers, and other network devices using SNMP or other network monitoring protocols.

Virtual Machines and Containers: Monitor the performance and resource usage of virtual machines (VMs) and containerized applications (e.g., Docker, Kubernetes).

`Application Performance Monitoring (APM)`

Application Metrics: Collect and visualize metrics like response time, request rates, error rates, and other performance indicators from your applications.

Transaction Tracing: Use distributed tracing tools integrated with Grafana to monitor and trace application transactions and identify bottlenecks.

Service Health: Monitor the health and status of microservices and other application components.

`Database Monitoring`

Database Performance: Track query performance, slow queries, connection counts, and other key database metrics.

Resource Utilization: Monitor CPU, memory, and disk usage of database servers.

Replication and Clustering: Keep an eye on replication lag, cluster health, and other relevant metrics for distributed databases.

`Log Monitoring and Analysis`

Log Aggregation: Aggregate and visualize logs from various sources using Grafana's integration with the ELK Stack (Elasticsearch, Logstash, Kibana) or Loki.

Log Search and Filtering: Search, filter, and analyze log data to identify patterns, anomalies, and troubleshoot issues.

Error and Event Tracking: Monitor logs for specific error messages or events and set up alerts for critical conditions.

`Business Metrics Monitoring`

Key Performance Indicators (KPIs): Visualize business metrics such as sales figures, customer engagement, financial metrics, etc.

Custom Metrics: Track custom metrics relevant to your business processes using data sources like MySQL, PostgreSQL, or Google Sheets.

`Security Monitoring`

Intrusion Detection: Monitor security events and logs from firewalls, IDS/IPS, and other security tools.

Compliance Monitoring: Ensure compliance with security policies by monitoring relevant metrics and logs.

Threat Detection: Detect and respond to security threats by setting up alerts for suspicious activities.

`User Experience Monitoring`

Real User Monitoring (RUM): Track metrics related to real user experiences, such as page load times, user interactions, and errors.

Synthetic Monitoring: Use synthetic tests to monitor the performance and availability of applications from various locations.

`Cloud Monitoring`

Cloud Services: Monitor metrics from cloud services like AWS, Azure, and Google Cloud using their respective monitoring services (e.g., CloudWatch, Azure Monitor).

Resource Utilization: Track the utilization of cloud resources like virtual machines, storage, databases, and networking.

`IoT Monitoring`

Sensor Data: Collect and visualize data from IoT sensors and devices.

Device Health: Monitor the health and status of IoT devices.

`Environmental Monitoring`

Data Center Environment: Monitor temperature, humidity, power consumption, and other environmental factors in data centers.

Building Management: Track metrics related to building management systems, such as HVAC, lighting, and energy usage.


#### Visualizations :-

Visualizations in Grafana are graphical representations of metrics that allow users to interpret and understand data more easily. 

Grafana offers a wide range of visualization options, including line graphs, bar charts, pie charts, tables, heatmaps, gauges, and more. 
