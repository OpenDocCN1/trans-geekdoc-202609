
## Table 1.1 Example of the input matrix generation for a rainfall-runoff model (Ourthe river basin).

| Dates | Precipitation (mm) | Lag prec 1 day | Lag prec 2 day | Lag prec 3 day | Lag prec 4 day | Discharge (m³/s) |
|---|---|---|---|---|---|---|
| 01/01/2015 | 4.37 |  |  |  |  | 4.37 |
| 02/01/2015 | 11.72 | 4.37 |  |  |  | 11.72 |
| 03/01/2015 | 33.57 | 11.72 | 4.37 |  |  | 33.57 |
| 04/01/2015 | 32.20 | 33.57 | 11.72 | 4.37 |  | 32.20 |
| 05/01/2015 | 8.20 | 32.20 | 33.57 | 11.72 | 4.37 | 8.20 |
| 06/01/2015 | 0.56 | 8.20 | 32.20 | 33.57 | 11.72 | 0.56 |
| 07/01/2015 | 26.41 | 0.56 | 8.20 | 32.20 | 33.57 | 26.41 |
| 08/01/2015 | 28.84 | 26.41 | 0.56 | 8.20 | 32.20 | 28.84 |
| 09/01/2015 | 0.23 | 28.84 | 26.41 | 0.56 | 8.20 | 0.23 |
| 10/01/2015 | 0.77 | 0.23 | 28.84 | 26.41 | 0.56 | 0.77 |
| 11/01/2015 | 10.79 | 0.77 | 0.23 | 28.84 | 26.41 | 10.79 |
| 12/01/2015 | 1.27 | 10.79 | 0.77 | 0.23 | 28.84 | 1.27 |
| 13/01/2015 | 32.60 | 1.27 | 10.79 | 0.77 | 0.23 | 32.60 |
| 14/01/2015 | 37.05 | 32.60 | 1.27 | 10.79 | 0.77 | 37.05 |
| 15/01/2015 | 1.15 | 37.05 | 32.60 | 1.27 | 10.79 | 1.15 |
| 16/01/2015 | 0.16 | 1.15 | 37.05 | 32.60 | 1.27 | 0.16 |

new variable represents an increase in the degrees of freedom in the problem and an unnecessary increase in a model complexity, and possibly, may lead to overfitting.

In this problem of rainfall-runoff, as stated before, the size of the basin plays an important role in what is to be expected from the complexity of the model. Although average precipitation is considered, it is often not enough to include only one or two lagged variables in the model. Precipitation events taking place close to the discharge measurement point would lead to an increase in discharge with a lag, which could be much smaller than the average one, and events far from this point would have a larger lag. This leads to another type of problem, which is spatiotemporal in nature.

The correlation coefficient is commonly used to determine mathematical linear relations between two samples of random variables or time series. In the case of building a rainfall runoff model, the variables are lagged precipitation and discharge. The lag time, leading to a high correlation, would be the one to adopt as the most probable candidate for the final model.

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_35_0.png)

Figure 1.7 Autocorrelation for the discharge at Ourthe River basin (tributary of the Meuse).

Since the correlation coefficient can be misleading if not enough data are used, or there could be events with a different correlation structure, it could be useful to employ the two other analysis techniques: (1) to analyze the variation of the correlation coefficient with different sizes of data sets and (2) to perform the correlation analysis separately for certain events, for example, with the discharge in a particular range.

It should be noted that a number of ML models (e.g., recurrent neural networks; see below) are based on an architecture where the whole time series (or its part), representing an input variable, is fed into the model, and the choice of the previous (lagged) values and their weighting is done via an optimization process during the model training. In such cases, IVS is in choosing the right variables (rather than specific lagged values), without paying much attention to how they should be lagged in a model since this is done automatically.

### 1.3.3. Optimization

The third step shown in Figure 1.5 is the modeling process per se, which in principle is called learning and is an optimization process to choose the model parameters and the structure to fit the model output to the measured (target) values. Numerous single-objective and multiobjective optimization techniques are available for such purposes, and they are typically very specific to each of the techniques. It is not possible to state that one technique will always provide a better solution than another. This can be partly explained by the existence of random components in many algorithms.

### 1.3.4. Model Evaluation (Testing)

The final step in the training process is the evaluation of the model’s performance. After the model is optimized and, as such, probably selected after some validation iterations are done, the error of the model on test data is used to assess the resulting model performance.

It is worth mentioning that in process-based modeling in situations of poor data availability, data partitioning into training, validation, and test subsets is not always carried out, so proper model testing may be difficult to arrange. However, in machine learning exercises, the procedures of data partitioning are normally followed.

The error measure (metrics) used in the training (learning) process of the ML model (typically based on the mean squared error) should not be seen as the only way of model performance estimation. Commonly, visual comparison, additional tests on extreme phenomena (crash tests), and a benchmark or reference model are used to assess the quality of the model as well. It is difficult to choose only one performance measure for a good model, so model training can be posed also as a problem of multiobjective optimization; on multiobjective machine learning, see, for example, Corzo and Solomatine (2006); and on multitask learning, a good introductory overview is given by Ruder (2017). In such cases, the modeling results should preferably be a matter of further discussions with stakeholders about the selection of a single model out of a Pareto-optimal set of models generated as a result of multiobjective optimization (training).

### 1.3.5. Uncertainties in the Process of Building a Model

Modeling leads to a generation of new knowledge and new insights into the modeled processes, and typically involves cycles of progressive refinement and improvement, and even reformulations of the initial modeling goals. Some of possible questions raised during modeling experiments, and the related cycles, are shown in Figure 1.8. Each of these questions is associated with an uncertain variable in the process. Uncertainty in data inevitably propagates to models’ outputs. Changes in data partitioning also lead to different model parameterizations. Changes in the input variables set can lead to different model outputs and hence varying performance. Many ML models require random initializations of parameters, so that multiple runs may lead to different results. Finally, the idea of having one objective function in the optimization process, where the real problem can normally have multiple objectives, makes the model biased to a certain modeling objective. For example, a ML model built for high flow might not be optimal for low flows and vice versa. Since there is no perfect measure for performance, there is uncertainty associated with the choice of what is defined as optimal in the modeling process.

In ML theory and practice, all these problems have been studied, are quite well understood, and adequate techniques have been developed. For example, n-fold cross-validation is used to deal with uncertainties in data partitioning. Uncertainty is reduced if instead of using a single model, multiple (ensemble) models are built, based on different parameter (weights) randomizations, and then aggregated using (dynamic) weighting. The problem of multiregimes of the modeled system and seasonality is solved by modular or committee systems (Corzo & Solomatine, 2007b, 2007a; Kayastha et al., 2013). For problems related to the IVS, feature engineering offers a number of techniques (see Guyon & Elisseeff 2003; Bowden et al., 2005a, 2005b; Galleli & Castelleti, 2013). Robustness

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_38_0.png)

Figure 1.8 Possible cycles in ML model building.

class index. For example, in the case of flood forecasting, a ML numerical prediction model can be trained to predict the discharge values, but the final result will be presented as a binary class: “no flood” (if discharge is below a predefined threshold), and “flood” (otherwise).

There are also other ways of encoding classes: data are transformed, and the problem is formulated as having N binary outputs where N is the number of classes. For example, in case of two possible outcomes (like no flood and flood), output vectors (real-valued) would be either (0, 1) for flood conditions or (1, 0) for no-flood conditions. A regression ML model is trained to reproduce real-valued vectors. If, for the new inputs, this model gives an output vector close to (0, 1), for example (0.11, 0.85), then it is interpreted as flood, and if it is close to (1, 0), for example (0.15, 0.91), it is interpreted as no-flood.

However, in water resources, a much more widely spread type of problem is a regression (numerical prediction) problem, which aims to predict a continuous output, such as the discharge of a river or the water level in a reservoir. For example, in the case of water resource management, a ML model is employed to predict the reservoir inflows, water demand, and water availability, and then to use the predictions to optimize the water allocation.

This section investigates the use of machine learning techniques in water resources, emphasizing their relevance and efficacy. It begins by looking into artificial neural networks (ANNs) with a focus on the popular multilayer perceptron (MLP) ANN. MLP ANNs are popular in water resources research due to their capacity to handle complicated interactions and big data sets. The section gives a review of MLP ANN architecture and training procedures, emphasizing its applicability to water resource modeling. Following that, the subject shifts to regression and model trees, as well as bagging and boosting strategies for developing ensemble models. These methods provide modular solutions as well as statistical tools for increasing model stability, accuracy, and generalization. In regression and model trees, the combination of decision trees with linear models allows for flexible modeling of nonlinear connections, while bagging and boosting approaches improve performance by combining numerous models. The section also discusses the recent spike in interest in deep learning, particularly in relation to water resources. Deep learning, as represented by recurrent neural networks, exhibits exceptional ability in managing time series data and capturing complicated patterns. Long short-term memory (LSTM) networks, in particular, have shown considerable potential in hydrological modeling by overcoming long-term dependency concerns. The section emphasizes the significance of using deep learning methods into water management and forecasting. Overall, this in-depth
