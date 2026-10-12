
# Production Maintenance

This chapter will focus on aspects we must consider while our services operate in production. A service that is now stable and operating in production doesn’t mean it will keep operating correctly. Production services left unattended are like neglected gardens — they wither over time. Many things are changing under our noses — new vulnerabilities discovered, new customers bringing new cases we didn’t experience, scaling effects, and so on. Maintenance is the lifeline of resilience!

Maintenance does not only include the bugs and issues in the code. It includes culture. A good culture will solve issues faster without blaming a specific person for the problem.

Maintenance includes observing the systems and monitoring what is happening through telemetry. Telemetry data can be logs, metrics, and tracing. We should strive to have observability, which will allow us to gain control over our system. When we observe a problem or bug, we’ll want to solve it and seek a solution - troubleshooting. This chapter will dive into the troubleshooting process and what is included inside.

When using a microservices system, the power of distributed maintenance is crucial, and without it, the microservices architecture is much less powerful.

## Structure

In this chapter, we will discuss the following topics:

*   Monitoring
*   Observability
    *   Logs
    *   Metrics
    *   Tracing
*   Production Troubleshooting
    *   The Power of Theory
*   Profiling
    *   PGO
    *   Performance Issues
*   Alerting
    *   Performance Metrics

## Monitoring

Monitoring allows stakeholders to deeply understand how remote environments work, such as production or staging. It is the continuous process of observing, collecting, and analyzing data on a system’s performance, health, and behavior. This ensures the system operates well and as expected.

Monitoring **continuously observes** and analyzes the performance, health, and availability of applications, infrastructure, and services to detect and respond to real-time issues and ensure optimal operation. It involves collecting metrics, logs, and other data to provide insights into the system’s behavior and identify potential problems or improvements.

Monitoring helps us detect trends and anomalies across the system and services. By setting predefined thresholds and conditions for data that interest us, we can define alerts or notifications based on monitoring.

Usually, we can view the monitoring output through dashboards explaining what is happening.

![](OEBPS/images/Figure-10.1.jpg)

**Figure 10.1:** Monitoring Dashboard Example

The preceding figure shows an example of a monitoring dashboard.

Monitoring and APM are concepts that are often used interchangeably. APM, which stands for Application Performance Monitoring, is a subset of monitoring used to track a specific application’s performance. APM tracks whether the application is stable and available, as well as error rate, latency, and so on. Monitoring is a broader topic that can describe things other than performance, like trends, number of paying customers, geographic specification data, SLO (service level objective), and more. Examples of famous monitoring tools in the market are `Prometheus`, `DataDog`, and `NewRelic`.

## Observability

Observability is the ability to measure the current state of a system and aggregate all the data into a historical view. Observability uses three types of telemetry data - logs, metrics, and tracing. This is also the historical order in which they were introduced.

We can refer to observability as a system property, like functionality or testability.

Observability lets us understand **why and how** the system behavior is as it is, which differs from monitoring, which lets us understand **what** is happening through analysis.

We’ll use the power of observability to solve real and potential problems. Without observability, we can’t maintain our system and can’t perform troubleshooting, which will be discussed later in this chapter.

A good analogy for telling the difference between monitoring and observability is to treat our system as a patient. Monitoring is like viewing a patient’s vital signs (heartbeat, blood pressure, temperature, injuries, and others). On the other end, to heal the patient, we need to look at his historical medical issues and investigate specific theories regarding why he is ill.

When deploying microservices architecture, we must create a monitoring system. Creating a monitoring system while using `Kubernetes` includes three parts:

*   **Centralized Monitoring System:** A unified platform aggregating data from various sources, providing tools for viewing and analyzing. We can use OSS tools like `Prometheus` and `Grafana` or SaaS tools like `DataDog` and `NewRelic`.
*   **Agents:** They report all the telemetry data to the centralized monitoring system, which is usually a `DaemonSet` sitting on each node.
*   **SDK:** For each language we use, we must implement logic that supports telemetry data reporting through functions, middlewares, and so on.

Let’s explore the three telemetry data types.

## Logs

Logs are records of events, actions, or messages a software application or system generates for troubleshooting, monitoring, and analysis. Logs can be used to give information and report warnings or errors. With logs, we can understand **what happened and when it happened**, like leaving breadcrumbs in the code. Logs should be composed in human-readable JSON format and not just plain text, although this is an option. Log comprises metadata (date, service, and so on), log level, and the log itself. Usually, the log metadata is injected into the log manually or during the usage of the SDK. Here are the common log levels:

*   **Info:** Useful information; usually, we don’t care too much about them. It is typically the default log level.
*   **Debug:** This log is intended for logging information details for debugging purposes. It will be deleted sometime in the future.
*   **Warning:** Anything that can potentially cause errors in the system. It can be delays, high latency, and so on. These kinds of logs never require immediate remediation.
*   **Error:** This log indicates something terrible happened and usually requires user intervention. It usually requires immediate attention.
*   **Fatal:** An error that forces the service to go down or restart. It is an extreme situation that will require an instant reaction.

Here are a few examples of logs:

*   `[INFO] User was logged into the system. { “name”: “John”, “company”: “Nick”}`
*   `[DEBUG] Query was executed. { “query”: “SELECT * FROM accounts”, “execution_time”: “15s”}`
*   `[WARNING] Event took a lot of time to proceed. { “event_id”: “12345”, “time”: “30s”}`
*   `[ERROR] Unable to connect to the external API. Retrying in 2 seconds.`
*   `[FATAL] Server got panic. Shutting down the application`

One of Golang’s core packages is `log`, which contains log functionality. An alternative with more advanced options is the package `github.com/sirupsen/logrus`.

## Metrics

A metric is a quantitative measurement represented as a data point. Metrics can include tags. Tags represent metadata on the metric; examples include account name, user name, environment, app version, and so on. We can build graphs in different layout forms in any monitoring system based on the metrics data points over time. We can also create partition graphs using the metrics tags and defined aggregated time durations of the metrics.

There are a variety of metrics types. Here, we’ll mention the three leading types.

*   **Counter:** This cumulative metric represents a value that can increase or be restarted to zero. Examples of metrics of a counter can be the number of failed requests, the number of total requests, the amount of users that used the system, and so on.
