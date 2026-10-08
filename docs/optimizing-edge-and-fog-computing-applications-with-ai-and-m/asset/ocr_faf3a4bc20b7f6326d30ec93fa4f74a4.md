# 7.5.2 Local Training Mechanism

Each edge device, such as an IIoT node or factory server, independently trains a local predictive maintenance model using its own data. The training mechanism varies based on the following:

# 7.5.2.1 Model Type

+   ** Deep learning models (Convolutional Neural Networks [CNNs], Long Short-Term Memory networks [LSTMs]) [6,7]—Used for complex timeseries analysis and anomaly detection.
** Traditional ML models (Random Forest and Support Vector Machine [SVM]) – Used for structured, tabular data with historical failure records.

# 7.5.2.2 Hardware Capabilities

+   ** Powerful edge devices—Train deep learning models.
** Low-power IoT nodes—se lightweight models like decision trees or logistic regression.

# 7.5.2.3 Training Frequency

+   ** Batch training—Models trained at intervals (e.g., every 24 hours).
** Real-time adaptation—Models update dynamically based on streaming data.

Once training is complete, the edge device does not share raw data but instead transmits only model updates (gradients or weights) to the aggregation server.

# 7.5.3 Aggregation Server

The aggregation server plays a critical role in combining local model updates from multiple edge devices and redistributing the improved global model. It can be implemented using the following.

# 7.5.3.1 Centralized and on-premise Aggregation Server

A single cloud-based or on-premise coordinator server collects local updates, aggregates them (using FedAvg, FedProx, or FedSVR), and sends the new global model back to edge devices.

+   ** Advantage: Faster aggregation and simpler implementation.
** Challenge: Single point of failure, potential bottlenecks in large-scale deployments.