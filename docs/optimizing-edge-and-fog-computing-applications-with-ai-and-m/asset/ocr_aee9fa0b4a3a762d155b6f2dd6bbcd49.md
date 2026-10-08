# 7.5.3.2 Blockchain-Based Decentralized Aggregation

A blockchain ledger records model updates from each edge device in a secure, verifiableable manner. Smart contracts automate the aggregation process without requiring a central server.

+   - Advantage: Trustless, tamper-proof, and scalable across multiple industrial facilities.

+   - Challenge: Higher computational overhead for consensus mechanisms.

# 7.5.4 Federated Learning Training Cycle in Predictive Maintenance

+   1. Initialization—The aggregation server initializes a global predictive maintenance model.
2. Local Training—Each edge device trains a model using its own sensor data.
3. Secure Transmission—Local model updates (not raw data) are encrypted and sent to the aggregation server.
4. Aggregation—The server computes a new global model using FedAvg, FedSVR, or an ensemble strategy.
5. Redistribution—The updated global model is sent back to all edge devices for the next training cycle.
6. Continuous Improvement—The process repeats until model performance stabilizes.

# 7.6 Performance Metrics

Evaluating the effectiveness of FML in PdM requires a set of well-defined performance metrics. These metrics help assess the model’s predictive accuracy, communication overhead, and resource efficiency, ensuring its practical implementation in industrial environments.

# 7.6.1 Model Accuracy

Model accuracy serves as a fundamental benchmark for evaluating the reliability of an FML system in predicting equipment failures. The key aspects include:

+   - Precision and Recall: In PdM, false positives (incorrect failure predictions) and false negatives (missed failures) can have significant consequences. Precision measures how many predicted failures are actual failures, while recall assesses the model’s ability to detect all real failures.