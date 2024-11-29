## What is Monitoring ?


Monitoring is the process of collecting, analyzing, and using data to ensure that your system’s components (servers, networks, applications) are working correctly. 

This is usually done by tracking specific metrics like CPU usage, memory consumption, and network latency. 

Monitoring tools also set thresholds for these metrics, triggering alerts when they go out of the acceptable range.

#### Example of Monitoring in Action :-

Consider an e-commerce site. 

You have hundreds of users shopping, and the checkout page suddenly becomes very slow. 

Monitoring systems will track the response time for that page. 

If the time exceeds a certain threshold (say, 2 seconds), it will trigger an alert so the operations team can investigate and resolve the issue.

#### Common Monitoring Metrics :-

CPU and memory usage

Disk and network I/O

Database query response times

API response times

Uptime and downtime

## What is Observability ?

Observability goes a step beyond monitoring by helping you understand why something went wrong. 

It uses data, logs, and traces to give you a holistic view of your system's internal state. 

Observability allows you to troubleshoot complex problems, even if you haven't predicted a specific failure scenario beforehand.


#### Example of Observability in Action :-

Let’s return to our e-commerce example. 

If the checkout page is slow, observability will allow you to track the exact flow of requests through your system. 

You’ll be able to see whether the issue is related to a slow database query, increased latency between microservices, or high traffic in your payment gateway. 

This comprehensive insight allows for faster root-cause analysis.


#### It is built on three pillars :-

Metrics: Quantitative data points (e.g., CPU load, request latency).

Logs: Text-based records of events.

Traces: Detailed records of a request's path through the system.


## Tools for Monitoring and Observability

Prometheus

Grafana
