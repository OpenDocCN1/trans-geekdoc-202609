+   * Adaptive learning rates: Adjusting the contribution of devices with high- or low-quality data.

+   * Security Enhancements
- Since attackers could tamper with model updates, the following techniques are applied:
- Secure Aggregation: Encrypting updates to prevent adversarial poisoning.
- Differential Privacy: Adding noise to updates to enhance data confidentiality.

# 7.4 Algorithm Aggregation Strategies in Federated Learning

In FML for predictive maintenance, the aggregation strategy plays a crucial role in combining local model updates from multiple edge devices into a robust global model. The choice of aggregation algorithm directly impacts model accuracy, convergence speed, communication efficiency, and the ability to handle data heterogeneity. This section elaborates on key aggregation strategies, their working principles, advantages, and associated challenges.

# 7.4.1 Federated Averaging

**Concept:** FedAvg is the most widely used aggregation strategy in FML. Instead of transmitting updates after every local training step, edge devices perform multiple local updates and then send only the final model parameters to the central server. The server computes a weighted average of these local models based on the number of data samples at each edge device: where parameters are:

+   * Global model parameters
* Local model parameters from device
* Number of training samples on device
* Total number of training samples across all devices
* Number of participating devices

**Advantages:**

+   * Simple and computationally efficient—requires only weighted averaging of local models.
* Reduces communication frequency by allowing multiple local updates before aggregation.