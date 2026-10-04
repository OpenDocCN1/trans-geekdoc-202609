# Accessing security alerts from API

Although Azure Security Center has its own dashboard where you can visualize all security alerts, there are some specific scenarios in which you may want to consume the alert via API. This is a common scenario among organizations that want to build their own dashboards and programmatically manipulate all alerts.

In this chapter, you will learn how to leverage the built-in Security Center Representational State Transfer (REST) API and the Microsoft Graph Security API to retrieve alerts using HTTP requests.

# Understanding REST API

Representational State Transfer (REST) APIs are service endpoints that support sets of HTTP operations (methods), which provide create, retrieve, update, or delete access capabilities to the service's resources. A REST API request/response pair can be separated into five components—three for request and two for response—as shown in Figure 10-1.

![](bbox=[0.198, 0.613, 0.833, 0.836])