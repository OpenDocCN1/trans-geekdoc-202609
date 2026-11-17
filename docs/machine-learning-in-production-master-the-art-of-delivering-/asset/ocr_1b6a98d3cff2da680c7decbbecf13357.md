# Operational monitoring with Prometheus and Grafana

Prometheus is an open-source system used for event monitoring and alerting. It scrapes the real-time data instrumented jobs and stores it with a timestamp in the database. The word **instrument** refers to the use of a client library that allows Prometheus to track and scrape its metrics and store them locally. Prometheus offers client libraries that can be used to instrument your application. In this scenario, you will be using the Prometheus Python client in the FastAPI application to expose its metrics that need to be tracked.

A Prometheus server scrapes and stores metrics from instrumented jobs in time series format. This data can be fetched using PromQL - query language, and it can be used to visualize the metrics. It comes with an alert manager to handle alerts.

According to GrafanaLabs, Grafana is an open-source interactive visualization and monitoring platform that enables users to visualize metrics, logs, and traces collected from deployed applications. Grafana is easy to integrate with most common databases, such as Prometheus, Influx DB, ElasticSearch, MySQL, and PostgreSQL.

As Grafana is an open source tool, hence you can write an integration plugin from scratch to connect with multiple data sources. The Grafana dashboard fetches the data from connected data sources and allows you to pick up the visualization type from plenty of visualization options, such as heat maps, bar charts, and line graphs. You can easily run the query, visualize metrics, and set up alerts for critical events.

In this scenario, you will be using Grafana and Prometheus. Both Prometheus and Grafana are open-source tools. As a matter of fact, Prometheus and Grafana are popular combinations in the industry for monitoring systems. Grafana dashboard will be used for visualization and alert management. It will fetch the data from the Prometheus database for querying metrics and will display the intuitive visualization on the dashboard.

Prometheus and Grafana can be separately installed and configured on a local machine or a remote server. However, you will be using docker images of Prometheus and Grafana by executing the docker-compose.yaml file.

To maintain consistency, similar files from the previous chapters with minor modifications will be used. The files required for Prometheus and Grafana dashboards are added as shown in the following file structure:

+   - .gitignore
+   - config.monitoring
+   - datasource.yml