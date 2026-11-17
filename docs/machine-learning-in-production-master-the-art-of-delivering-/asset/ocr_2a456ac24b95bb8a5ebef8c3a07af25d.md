+   - Easy to implement

# Cons:

+   - Moderate latency
+   - Not suitable for ML-centric organizations

# Web service/REST API

Web service/REST API is the popular method for deploying models. Unlike batch predictions, it does not process a bunch of records; it processes a single record at a time. In near real-time, it takes the parameters from users or existing applications and makes predictions.

It can take inputs as well as return the outputs in JSON format. JSON is a popular and compatible format that makes it easy for software or website developers to integrate it into existing applications.

When an event gets triggered, REST API passes the input parameters to the ML model and returns the predictions.

# Pros:

+   - Easy to integrate
+   - Flexible
+   - Economical (pay-as-you-go plan)
+   - Near real-time predictions

# Cons:

+   - Scalability issues
+   - Prone to security threats

# Mobile and edge devices

When there are situations such as actions/ decisions that need to be taken immediately or there is no internet connectivity, the ML model needs to be deployed on these devices.

Edge devices include sensors, smartwatches, and cameras installed on robots.

This type of deployment is different from the preceding methods. In this, input data may not go to remote servers for making predictions. There are cloud service providers, such as Microsoft Azure, that offer the required infrastructure for this. Tiny Machine Learning (TinyML) is another such alternative capable of performing on-device sensor data analytics at an extremely low power.