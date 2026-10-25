| Ref. | Train metric | Test metric | PHM tasks | Signals |
|---|---|---|---|---|
| [186] | MSE | MSE | Degradation prediction | Far-field stress |
| [187] | Discretization error | MAE | Degradation prediction | Stress |
| [188] | RMSE | MRSE | Degradation prediction | Rise time, displacement |
| [93] | Negative log likelihood | Sensitivity analysis, MAE, and absolute error variance | Degradation prediction | Stress, temperature |

understanding of the different combinations of physics knowledge, metrics, and signals utilized can serve as a valuable guide for researchers and practitioners when selecting appropriate evaluation measures and sensor inputs for their respective PHM applications.

# 3. Synthetic review of PIML studies in PHM

The physics involved in research subjects in the field of PHM are often diverse and can be expressed in different forms such as algebraic equations, differential equations, simulation results, logic rules, and probabilistic relations along with limited monitoring

| Authors | Topics of interest | Main Challenges | Taxonomy |
|---|---|---|---|
| Rai, Rahul, and Chandan K. Sahu. [72] | • Cyber-physical system's dynamic behavior modeling | • Discretization approximation of the continuous system behavior in a chaotic environment.
• Scenario-oriented PIML hybrid framework.
• Efficient extraction of causal and model parameter relationships in big data. | • Physics-based data pre-processing.
• Physics-guided ML algorithm structure design.
• Physics-based ML regularization item. |
| Willard, J., Jia, X., Xu, S., Steinbach, M. [32] | • Engineering and environmental systems modeling.
• Model solving methods. | • Embedding incomplete physics knowledge.
• Keeping physical consistency in data mining.
• Sparse data and uncertainty quantitative information.
• Designing prior informed deep learning framework.
• ML training data scarcity.
• Keeping physical consistency.
• ML black-box nature explanation.
• Training data scarcity.
• Keeping physical consistency. | • Physics-based regularization item in ML algorithm.
• Physics-guided ML initialization.
• Physics-informed ML algorithm architecture design.
• Physics-informed Feature engineering.
• Physics-informed NN structure.
• Physics-informed loss function.
• Parallel/Series physics-ML combination structure.
• Physics-based regularization item in ML objective function.
• Physics-based data pre-processing.
• Physics-guided ML algorithm architecture design.
• Physics-based regularization item in ML algorithm. |
| Kim, S. W., Kim, I., Lee, J., Lee, S. [189] | • Physics-informed deep learning in dynamical systems behavior modeling.
• PHM is mentioned | | |
| Jan Hagendorfer, Elias. [190] | Condition monitoring | | |
| Finegan, D. P., Zhu, J., Feng, et al. [71] | Battery cell state prediction. | Keeping physical consistency. | • Physics-based data pre-processing.
• Physics-guided ML algorithm architecture design.
• Physics-based regularization item in ML algorithm. |
| Jianjing Zhang., Robert X. Gao. [191] | • Data curation and model interpretation for smart manufacturing.
• PHM is mentioned. | • Non-interpretable prediction logic in deep learning.
• Error or imbalance training data.
• Data and data labels scarcity. | • Physical model bias compensation and unknown parameters estimation via deep learning.
• Involving Physics-constraints into deep learning training.
• Physics-informed architecture
• Physics-informed loss function |
| Xu, Yanwen and Kohtz, et al. [29] | • Reliability analysis and risk assessment.
• Uncertainty quantification.
• PHM is mentioned. | • Scenario-oriented PIML hybrid framework and its computational efficiency.
• Incompleteness of physics knowledge and limited representatives of the training dataset.
• The need for accurate and reliable data to create an accurate digital twin model.
• Integrating data from different sources and formats.
• Selecting the appropriate modeling technique for a given physical system.
• Scaling up the digital twin model to larger and more complex systems.
• Validating the digital twin model against the physical system it represents. | • Modifying the loss function.
• Generating synthetic data.
• Pre-training on physics-based data.
• Correcting models with unmodeled physics.
• Correcting models with prediction residuals.
• Learning to predict inputs. |
| Thelen Adam, Zhang Xiaoge and Fink Olga, et al., [192,193] | • Physical system modeling | | |