

## 解决 ML 中的漂移问题

Once you detect the drift in the ML model, it can be addressed in the following ways:

### 数据质量问题

If there is an issue with input data, then it can be easily fixed. For instance, high-resolution images were provided for training face recognition models; however, low-resolution images were passed to the deployed model.

### 重新训练模型

After detecting the data or concept shift, retraining the model with recent data can improve its performance. Sometimes production data is not sufficient to train the model. In that case, you can combine historical data with recent production data and give more weight to recent data.

Here are four strategies for retraining the model:

- **定期重新训练**: Scheduling it at a fixed time, for instance, every Monday at 10 PM
- **数据或事件驱动**: When new data is available
- **模型或指标驱动**: When accuracy is lower than a threshold or SLA
- **在线学习**: Where the model continuously learns in real-time or near real-time on the latest data

### 重建或调优模型

If retraining the model doesn’t work, then you may need to consider rebuilding it or tuning it on recent data. You can automate this using a pipeline.

## 使用 Prometheus 和 Grafana 进行运营监控

Prometheus is an open-source system used for event monitoring and alerting. It scrapes the real-time data instrumented jobs and stores it with a timestamp in the database. The word **instrument** refers to the use of a client library that allows Prometheus to track and scrape its metrics and store them locally. Prometheus offers client libraries that can be used to instrument your application. In this scenario, you will be using the Prometheus Python client in the FastAPI application to expose its metrics that need to be tracked.

A Prometheus server scrapes and stores metrics from instrumented jobs in time series format. This data can be fetched using PromQL - query language, and it can be used to visualize the metrics. It comes with an alert manager to handle alerts.

According to GrafanaLabs, Grafana is an open-source interactive visualization and monitoring platform that enables users to visualize metrics, logs, and traces collected from deployed applications. Grafana is easy to integrate with most common databases, such as Prometheus, Influx DB, ElasticSearch, MySQL, and PostgreSQL.

As Grafana is an open source tool, hence you can write an integration plugin from scratch to connect with multiple data sources. The Grafana dashboard fetches the data from connected data sources and allows you to pick up the visualization type from plenty of visualization options, such as heat maps, bar charts, and line graphs. You can easily run the query, visualize metrics, and set up alerts for critical events.

In this scenario, you will be using Grafana and Prometheus. Both Prometheus and Grafana are open-source tools. As a matter of fact, Prometheus and Grafana are popular combinations in the industry for monitoring systems. Grafana dashboard will be used for visualization and alert management. It will fetch the data from the Prometheus database for querying metrics and will display the intuitive visualization on the dashboard.

Prometheus and Grafana can be separately installed and configured on a local machine or a remote server. However, you will be using docker images of Prometheus and Grafana by executing the docker-compose.yaml file.

To maintain consistency, similar files from the previous chapters with minor modifications will be used. The files required for Prometheus and Grafana dashboards are added as shown in the following file structure:

- .gitignore
- config.monitoring
- datasource.yml

```
|-- docker-compose.yml
|-- Dockerfile
|-- fastapi-dashboard.json
|-- LICENSE
|-- main.py
|-- prometheus.yml
|-- pytest.ini
|-- README.md
|-- requirements.txt
|-- runtime.txt
|-- start.sh
|-- test.py
|-- tox.ini
|-- app
|   |-- MANIFEST.in
|   |-- README.md
|   |-- requirements.txt
|   |-- setup.py
|   |-- tox.ini
|   └-- prediction_model/
        |-- pipeline.py
        |-- predict.py
        |-- train_pipeline.py
        |-- VERSION
        |-- __init__.py
        |-- config/
        |   |-- config.py
        |   └-- __init__.py
        |-- datasets/
        |   |-- test.csv
        |   |-- train.csv
        |   └-- __init__.py
```

```
|-- processing/
|   |-- data_management.py
|   |-- preprocessors.py
|   |-- __init__.py
|-- trained_models/
|   |-- classification_v1.pkl
|   |-- __init__.py
|-- tests/
|   |-- pytest.ini/
|   |-- test_predict.py
```

### config.monitoring

The extension of this file is .monitoring. In this file, configure the admin password and user permission for sign up.

```
1. GF_SECURITY_ADMIN_PASSWORD=pass@123
2. GF_USERS_ALLOW_SIGN_UP=false
```

The Docker container currently allows new Grafana users to sign up, so anyone can create an account and view the dashboard. Therefore, for security purposes, the admin password and allowing new users to sign up should be set to false.

### prometheus.yml

This file contains Prometheus configurations, such as `scrape_configs` and `scrape_intervals`.

```
1. # Global config
2. global:
3.   scrape_interval: 15s
4.   evaluation_interval: 15s
5.   external_labels:
6.     monitor: "app"
7.
8.   rule_files:
9.
10. scrape_configs:
11.   - job_name: "prometheus"
12.
13. static_configs:
14.   - targets: ["localhost:9090"]
15.
16.   - job_name: "app"
17. dns_sd_configs:
18.   - names: ["app"]
19.   port: 8000
20.   type: A
21.   refresh_interval: 5s
```

In this file, the scrape interval is set to 15 seconds (**15s**) in the global config, which means it will scrape the metrics data after every 15 seconds. It is targeting an app, that is, the FastAPI app here. Port is the app’s port, that is, **8000**, and the refresh interval is set to 5 seconds (**5s**).

### Dockerfile

This Dockerfile will install the dependencies, set the working directory, expose ports, and finally, run the ML app.

```
1. FROM python:3.7-slim-buster
2.
3. ENV PYTHONPATH "${PYTHONPATH}:src/"
4.
5. WORKDIR /app/
6.
7. COPY . .
8.
9. RUN chmod +x /app
10.
11. COPY ./start.sh /start.sh
12.
13. RUN chmod +x /start.sh
14.
15. # Expose the port that uvicorn will run the app on
16. ENV PORT=8000
17. EXPOSE 8000
18.
19. RUN pip install --upgrade pip
20.
21. RUN pip install --upgrade -r requirements.txt --no-cache-dir
22.
23. CMD ["/start.sh"]
```

### docker-compose.yaml

This docker-compose file will set up and run three services:

- The app, that is, FastAPI app: For the ML model. It will run on port **8000**.
- Prometheus server: It will run on port **9090**.
- Grafana dashboard: It will run on port **3000**.

In the following file, you can see that the Grafana service depends on the Prometheus service:

```
1. version: "2.2"
2.
3. services:
4.   app:
5.     build: .
6.     restart: unless-stopped
7.     container_name: app
8.     ports:
9.     - 8000:8000
10.    networks:
11.      example-network:
12.        ipv4_address: 172.16.238.10
13.
14.   prometheus:
15.     image: prom/prometheus:latest
16.     restart: unless-stopped
17. container_name: prometheus
18. ports:
19.   - 9090:9090
20. volumes:
21.   - ./prometheus.yml:/etc/prometheus/prometheus.yml
22. command:
23.   - "--config.file=/etc/prometheus/prometheus.yml"
24. networks:
25.   example-network:
26.     ipv4_address: 172.16.238.11
27.
28. grafana:
29. image: grafana/grafana:latest
30. restart: unless-stopped
31. user: "472"
32. container_name: grafana
33. depends_on:
34.   - prometheus
35. ports:
36.   - 3000:3000
37. volumes:
38.   - ./datasource.yml:/etc/grafana/provisioning/datasource.yml
39. env_file:
40.   - ./config.monitoring
41. networks:
42.   example-network:
43.     ipv4_address: 172.16.238.12
44.
45. networks:
46.   example-network:
47.     # name: example-network
```

