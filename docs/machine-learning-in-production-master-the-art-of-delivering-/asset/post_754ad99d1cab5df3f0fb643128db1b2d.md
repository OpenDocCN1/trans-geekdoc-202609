
driver: bridge
ipam:
driver: default
config:
- subnet: 172.16.238.0/24

## main.py

This file contains code for the FastAPI app. In this code, add the following two lines to instrument the FastAPI app. In Prometheus, the instrumentation refers to the use of a library in application code (in this scenario, it is FastAPI) so that Prometheus can scrape metrics exposed by the app.

First, add `prometheus-fastapi-instrumentator` with version **5.7.1** to the `requirements.txt` file. Then, import the Prometheus FastAPI instrumentator as follows:

```
from prometheus_fastapi_instrumentator import Instrumentator
```

Then, at the end of the file, add the following line to instrument FastAPI app to the Prometheus FastAPI instrumentator:

```
Instrumentator().instrument(app).expose(app)
```

With this single line, FastAPI will be instrumented and all Prometheus metrics used in the FastAPI app can be scraped via the added **/metrics** endpoint.

You have already studied the rest of the files in the previous chapters. Refer to the previous chapters for files mentioned in the preceding directory structure.

You will need to run the docker containers by running the following docker-compose command in the terminal:

```
docker-compose up
```

Now you have access to three containers and their respective ports:

- FastAPI: Running at http://localhost:8000/
- Prometheus: Running at http://localhost:9090/
- Grafana dashboard: Running at http://localhost:3000/

On the FastAPI app, you can access the `/metrics` endpoint to view the data that Prometheus is scraping from it, as shown in the following figure:

# HELP python_gc_objects_collected_total Objects collected during gc
# TYPE python_gc_objects_collected_total counter
python_gc_objects_collected_total{generation="0"} 27968.0
python_gc_objects_collected_total{generation="1"} 5156.0
python_gc_objects_collected_total{generation="2"} 92.0
# HELP python_gc_objects_uncollectable_total Uncollectable object found during GC
# TYPE python_gc_objects_uncollectable_total counter
python_gc_objects_uncollectable_total{generation="0"} 0.0
python_gc_objects_uncollectable_total{generation="1"} 0.0
python_gc_objects_uncollectable_total{generation="2"} 0.0
# HELP python_gc_collections_total Number of times this generation was collected
# TYPE python_gc_collections_total counter
python_gc_collections_total{generation="0"} 325.0
python_gc_collections_total{generation="1"} 29.0
python_gc_collections_total{generation="2"} 2.0

### Figure 14.3: FastAPI metrics

You can access Prometheus UI on port 9090 and run the PromQL query. To get the total number of requests, execute **prometheus_http_requests_total**. You will get the HTTP status code, handler, instance, job name, and count, as shown in the following figure:

Use local time Enable query history Enable autocomplete Enable highlighting Enable linter prometheus_http_requests_total Execute

| series | value |
| :--- | :--- |
| prometheus_http_requests_total{code="200", handler="/api/v1/label/name/values", instance="localhost:9090", job="prometheus"} | 55 |
| prometheus_http_requests_total{code="200", handler="/api/v1/labels", instance="localhost:9090", job="prometheus"} | 54 |
| prometheus_http_requests_total{code="200", handler="/api/v1/metadata", instance="localhost:9090", job="prometheus"} | 58 |
| prometheus_http_requests_total{code="200", handler="/api/v1/query", instance="localhost:9090", job="prometheus"} | 28 |
| prometheus_http_requests_total{code="200", handler="/api/v1/query_range", instance="localhost:9090", job="prometheus"} | 5023 |
| prometheus_http_requests_total{code="200", handler="/api/v1/rules", instance="localhost:9090", job="prometheus"} | 19 |
| prometheus_http_requests_total{code="200", handler="/api/v1/series", instance="localhost:9090", job="prometheus"} | 2 |
| prometheus_http_requests_total{code="200", handler="/api/v1/status/buildinfo", instance="localhost:9090", job="prometheus"} | 3 |
| prometheus_http_requests_total{code="200", handler="/metrics", instance="localhost:9090", job="prometheus"} | 592 |
| prometheus_http_requests_total{code="200", handler="/static/filepath", instance="localhost:9090", job="prometheus"} | 1 |
| prometheus_http_requests_total{code="400", handler="/api/v1/query_range", instance="localhost:9090", job="prometheus"} | 2 |

### Figure 14.4: Prometheus UI—Query execution

Prometheus allows you to view these query results in graphical format by switching to the Graph tab in Prometheus web UI.

You have seen Prometheus web UI, and PromQL is fetching the metric data as well. Now, in the next part, you will connect Prometheus to the Grafana dashboard as a data source. Metrics data fetched from the Prometheus server will be visualized on the Grafana dashboard. Go to Grafana dashboard web UI and click on the add your first data source option, as shown in the following figure:

![](img/cc4299656808e62a294f1843a1e18e72_422_0.png)

### Figure 14.5: Grafana–Adding data source

Next, select the Prometheus database from the Time series databases, as shown in the following figure:

![](img/cc4299656808e62a294f1843a1e18e72_422_1.png)

### Figure 14.6: Grafana–Prometheus data source

In the settings, provide Prometheus as a name in the Name field. Then, mention http://prometheus:9090 in the URL field, as shown in the following figure, as Prometheus service is running on port 9090:

![](img/cc4299656808e62a294f1843a1e18e72_423_0.png)

### Figure 14.7: Grafana–Prometheus configuration

Finally, proceed with the basic configuration; however, you can also configure other fields. Scroll to the bottom of the page and hit the **Save & test** button, as shown in the following figure:

![](img/cc4299656808e62a294f1843a1e18e72_423_1.png)

### Figure 14.8: Grafana–saving and testing Prometheus configuration

If it is configured properly, you should see the integration status success message after you save and test the configuration.

Once Prometheus integration is done, create a new dashboard with the **New Dashboard** option in Grafana web UI, as shown in the following figure:

![](img/cc4299656808e62a294f1843a1e18e72_423_2.png)

### Figure 14.9: Grafana–creating a new dashboard

The Grafana dashboards can be created from scratch or by importing JSON files from storage. Grafana also lets you import the dashboard via Grafana.com, as shown in the following figure:

![](img/cc4299656808e62a294f1843a1e18e72_424_0.png)

### Figure 14.10: Grafana–uploading JSON file

In this scenario, import a JSON file from the directory. You can refer to one of the original public Grafana instances, hosted by Grafana Labs, using the following link: https://play.grafana.org/d/000000012/grafana-play-home?orgId=1

For various dashboard visualizations and sources, refer to the following link https://grafana.com/grafana/dashboards/.

Next, provide the dashboard name and Prometheus source, as shown in the following figure:

![](img/cc4299656808e62a294f1843a1e18e72_424_1.png)

### Figure 14.11: Grafana–Prometheus as a data source

Finally, open the newly created dashboard from the web UI. After importing the dashboard from the JSON file, you can customize the dashboard by changing the chart type, as shown in the following figure.

![](img/cc4299656808e62a294f1843a1e18e72_425_0.png)

### Figure 14.12: Grafana-Dashboard

The next step is to send alerts for critical events. Grafana includes built-in support for the Prometheus Alert manager. Grafana provides mainly three strategies for setting alerts:

- **Cloud Alert manager**: Cloud Alert manager runs in Grafana Cloud. It supports alerts from Grafana, Mimir, and Loki.
- **Grafana Alert manager**: Grafana Alert manager is an internal Alert manager. It is pre-configured and supports alerts from Grafana; however, it cannot receive alerts outside Grafana.
- **An external Alert manager**: You can configure Grafana to use an external alert manager. This is useful when you are looking for a centralized alert manager that can receive alerts from different sources.
