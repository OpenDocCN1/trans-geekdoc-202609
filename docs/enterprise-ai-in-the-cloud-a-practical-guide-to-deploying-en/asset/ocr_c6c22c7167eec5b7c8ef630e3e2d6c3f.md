# Edge Computing

Here are some considerations for edge computing:

+   > It brings data processing and model training to edge devices such as IoT devices, sensors, or edge servers closer to the point of data generation or data source.

+   > It can be handy for use cases that require real-time processing of data with exceptionally low latencies, reduced bandwidth, and increased security and privacy.

> NOTE Hybrid and edge computing are especially useful in use cases such as remote healthcare monitoring, autonomous vehicles, and industrial IoT.

# Designing Models for the Edge

Designing models for the edge, you need to factor in some specific considerations, such as the following:

+   > **Model size:** The model should be small enough to fit on the edge device.

+   > **Model latency:** The model latency should be low enough to suit the requirements of the application.

+   > **Model accuracy:** The model should be accurate enough to meet the requirements of the application.

To meet these requirements, you may be required to adopt model compression techniques such as quantization and model pruning to reduce the model size. Moreover, the model should be designed to operate in offline or intermittent connectivity scenarios.

![](bbox=[0.125, 0.6, 0.88, 0.825])

FIGURE 13.16: Hybrid and edge computing in machine learning

+   > **Data synchronization, latency, and network connectivity:** In the case of hybrid and edge computing scenarios, data synchronization latency and network