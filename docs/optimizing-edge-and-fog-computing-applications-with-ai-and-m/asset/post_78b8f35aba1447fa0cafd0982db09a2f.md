
# Optimizing Edge and Fog Computing Applications with AI

- 13. Ahn, J., Lee, Y., Kim, N., Park, C. and Jeong, J. (2023). Federated learning for predictive maintenance and anomaly detection using time series distribution shifts in manufacturing processes. Sensors 23(17), 7331. https://doi.org/10.3390/s23177331
- 14. Pruckovskaja, V., Weissenfeld, A., Hestracher, C., Graser, A., Kafka, J., Leputsch, P., Schall, D. and Kommitz, J. (2023). Federated learning for predictive maintenance and quality inspection in industrial applications. arXiv preprint arXiv:2304.11011. https://arxiv.org/abs/2304.11011
- 15. Ke, A., Han, Y. and Kim, T-K. (2023). Enhancing anomaly detection in distributed power systems with encoder-based federated learning. PLoS One 18(8), e0290337.
- 16. Ahn, J., Lee, Y., Kim, N., Park, C. and Jeong, J. (2023). Federated learning for predictive maintenance and anomaly detection using time series distribution shifts in manufacturing processes. Sensors 23(17), 7331.
- 17. Liu, J., Lou, J., Xiong, L., Liu, J. and Meng, X. (2021). Projected averaging with heterogeneous differential privacy. Proceedings of the VLDB Entertainment 15(4), 828–840.
- 18. Le, K., et al. (2024). Efficient assembly normalization layers and regularization for federated generalization. Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition.
- 19. Ma, X., et al. (2022). State-of-the-art survey on solving non-iid data in federated learning. Generation Computer Systems 135, 244–258.
- 20. Yuan, X. and Li, P. (2022). On convergence of FedProx: Local dissimilarity invariant bounds, nonmonotonic and beyond. Advances in Neural Information Processing Systems 35, 10752–10765.
- 21. Gupta, P., Anand, A., Agarwal, P. and McArthur, G. (2024). Neural network inspired scalable task scheduling for cloud infrastructure. Internet of Things and Cyber-Physical Systems 4, 268–279.
- 22. Wang, H., et al. (2020). Federated learning with matched averaging, arXiv preprint arXiv:2002.06440.
- 23. Mustapha, S. D. S. and Gupta, P. (2024). DBSCAN inspired task scheduling for cloud infrastructure. Internet of Things and Cyber-Physical Systems 4, 32–39.
- 24. Gupta, P., Rawat, P. S., Kumar Saini, D., Vijayarthi, A. and Alharbi, M. (2023). Neural network inspired differential evolution task scheduling for cloud infrastructure. Alexandria Engineering Journal 37, 217–230.
- 25. Madhusdan, H. S., Gupta, P., Saini, D. K. and Tan, Z. (2023). Dynamic virtual machine allocation in cloud computing using elephant herd optimization scheme. Journal of Circuits, Systems and Computers 32(11), 2350188.
- 26. Rawat, P. S., Gaur, S., Barthwal, V., Gupta, P., Ghosh, D., Gupta, D. and Rodrigues, J. C. (2025). Virtual machine placement in cloud computing environment using PSO-ANN based hybrid technique. Alexandria Engineering Journal 110, 145–152.
- 27. HS, M. and Gupta, P. (2024). Federated learning inspired Antlion based orchestration for edge computing. PLoS One 19(6), Art. e0304067.
- 28. Svorobej, S., et al. (2019). Simulating fog and edge computing scenarios: An overview and research challenges. Future Internet 11(3), 55.
- 29. Becker, S., Stryp-Rekowski, K., Stoll, O. V. L. and Kao, O. (2022). Federated learning for autoencoder-based condition monitoring in the Industrial Internet of Things. In IEEE International Conference on Big Data (IEEE BigData 2022).
- 30. Yeganah, Y., et al. (2020). Inverse distance aggregation for federated learning with non-iid data. Domain Adaptation and Representation Transfer, and Distributed and Collaborative Learning: Second MICCAI Workshop, DART 2020, and First MICCAI Workshop, DCL 2020, Held in Conjunction with MICCAI 2020, Lima, Peru, October 4–8, 2020, Proceedings 2. Springer International Publishing.
- 31. Nguyen, J., et al. (2022). Federated learning with buffered asynchronous aggregation. International Conference on Artificial Intelligence and Statistics. PMLR.

# Chapter 7: Advanced Machine Learning Predictive Maintenance

## Machine Learning Aggregation Strategy for Decentralized Models

Predictive maintenance (PdM) is a critical application of machine learning (ML) aimed at predicting equipment failures, reducing downtime and improving efficiency. However, traditional ML approaches relying on centralized data present several challenges:

- Data Privacy Concerns: Industries are often unable to share data due to regulatory constraints.
- High Transmission Costs: Continuously sending large volumes of data to central servers becomes unsustainable.
- Scalability Limitations: As the number of connected devices grows, the burden on centralized systems increases.

To address these issues, federated learning (FL) has emerged as a promising alternative. It allows training to occur locally on devices, only sharing updates (e.g., gradients or weights) with a central server, ensuring data privacy. The choice of aggregation strategy significantly impacts the model performance, robustness, and adaptability. This document explores various aggregation strategies used in FL, their strengths, and applicability in real-world environments.

## Challenges in Federated Predictive Maintenance

While FL offers a decentralized approach, its implementation comes with challenges that must be addressed, such as data security and variability in sensor-generated data.

### 7.2.1 Data Privacy and Security

One of the primary motivations for using FL in predictive maintenance is the need to preserve data privacy and security. Industrial environments generate vast amounts of sensitive operational data, including performance metrics, error logs, and sensor readings. Sharing this data with a central server raises several concerns:

- Regulatory Compliance: Industries such as healthcare, manufacturing, and energy are subject to strict data protection regulations (e.g., GDPR and HIPAA) that prohibit the transfer of sensitive data outside the premises.
- Confidentiality Rules: Companies are often reluctant to share proprietary machine data due to competitive reasons, as it may contain trade secrets or insights into strategies.
- Risk of Cyberattacks: Centralized data storage makes systems vulnerable to cyber threats, including unauthorized access, data breaches, and industrial espionage.

FL mitigates these risks by allowing training to occur locally, but additional security measures, such as secure aggregation, encryption, and differential privacy, are necessary to prevent adversarial attacks and model inversion threats. In industrial settings, sensor data is collected from a variety of machines, each differing in:

- Sensor Types and Configurations: Different equipment manufacturers use different sensors, leading to variations in format, resolution, and measurement units.
- Data Sampling Rates: Some machines generate data at high frequency, while others log readings at irregular intervals.
- Data Quality and Noise: Variability in conditions, sensor aging, and calibration introduces inconsistencies in data quality.

This heterogeneity makes it challenging to train a generalizable federated model. If local data distributions differ significantly (non-IID data), the global model may fail to converge or favor certain machine types. Addressing this requires advanced aggregation techniques, adaptive learning rates, and personalized federated learning models.
