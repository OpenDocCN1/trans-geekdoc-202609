Table 1. Dataset headers.

| Problem | Input 1 | Input 2 | Input 3 | Input 4 | Output |
| --- | --- | --- | --- | --- | --- | --- |
| Consumer num QoS level | Location | Avg temp. Cons. num | Season Base station | Special occasion Channel capacity | Consumer num QoS level [0-3] |

Table 2. Experimental results.

| Problem | Training time [s] | Performance |
| --- | --- | --- |
| Consumer number (QSVR regression) | 94 | MRE - 4.4 % |
| QoS determination (QSVC classification) | 81 | Accuracy - 94.8 % |

The use of quantum predictive components Diskit [19] for Python, a widely available source quantum computing library provided by IBM Research Group. offers a set of quantum kernels, while we make use of the following two: Quantum Support Vector Regressor (QSVR) – service count prediction at location within smart city, treated in form of regression-like problem; Classifier (QSVC) – in case of QoS determination, treated as classification.

In the regression problem we have the following inputs: location identifier, average temperature, normal number of year's season, special occasion flag (lockdown, holiday). In case of the one, the previously calculated value of CCI at locations where base stations are placed in synergy with predicted number of services consumer.

There are four categorical outcomes: 0 – defect/anomaly; 1 – low QoS; 2 – medium QoS; 3 – high QoS. In Table 1, the layout of dataset headers is presented. Table 2 summarizes experimental results in case of quantum predictive models, considering two different aspects of evaluation: time for training and prediction quality (for regression – mean relative error; for classification – accuracy). The free quantum computing surrounding of IBM Lab was used to execute the experiment.

The datasets were collected by exporting from the network simulation and planned framework, described in [16], and further divided into two subsets testing and training (75%). It can be noticed that quantum-based machine learning enhances prediction performance, compared against traditional methods from our past works [16,20]. However, more time was spent for training, considering that we did not leverage real quantum computing in our experiment.

# 4 CONCLUSION

In our work, the multi-branch SC under the performance of κ – fading and CCI was evaluated. We derived the formula for CCI graphically and analyzed the impact of two fading parameters, κ and μ, and as the input number of branches in SC. Then, the formula for CCI is used for quantum machine learning-Quality of Service (QoS) level and consumer number predictions inside network modeling, planning and simulation environment. Adoption of quantum machine learning leads to significant benefits against the known methods, but taking more time as real quantum computing hardware was not leveraged.

# ACKNOWLEDGMENT

This paper is made under project of Serbian Ministry of Science, Technological Development and Innovation, and project between Republics of Serbia and India “Development of Secure and Spectral Efficient Wireless Information and Power Transfer Systems for Large-Scale Wireless Networks” (Science and Technological Cooperation Projects 2022–2024).