

fresh arriving data. The module employs a meta-learning approach, for example, model-agnostic meta-learning [21] or online gradient boosting [22], in trying to support rapid model updates without full retraining from scratch. It is especially engineered to bypass concept drift, the changing statistical character of data in reaction to developing virus strains, human behavior adjustment, or the effects of public health interventions. Through learning to learn from small incremental updates, the system preserves high performance in dynamic environments. In addition, an active learning component is integrated that identifies areas or cases of high uncertainty and prioritizes them for enhanced data collection or notification. This responsive component allows for prompt decision-making, particularly in fast-moving public health crises.

### Detection and Early Warning System

This system converts predictive signals into operational intelligence by tracking disease trends and providing timely alerts. Relying on model predictions and corresponding confidence intervals, the system initiates warnings when estimated case numbers surpass adaptive thresholds derived from learned patterns of historical outbreaks, providing context-aware responsiveness. Its real-time estimates the effective reproduction number R(t) dynamically from estimated transmission parameters of the GNN-based spatiotemporal model, yielding a numerical estimate of the contagion risk. To support situational awareness, the system offers a spatiotemporal heatmap dashboard with predictive overlays to allow stakeholders to view current hotspots, future spread, and temporal dynamics across geographic scales. This general early warning capability supports informed public health policy and rapid intervention deployment.

## 4 Results and Findings

To effectively assess predictive models for the prediction of infectious diseases, both regression and classification metrics are needed. For continuous predictions of case counts, regression metrics like MAE, RMSE, MAPE, and the R² score (coefficient of determination) are applied. These are used to assess the accuracy, reliability, and explanatory power of the model. However, if the task is to classify outbreak and non-outbreak incidents, classification metrics come into play. Precision, recall, and F₁-score help to measure the model's performance in correctly labeling outbreaks, while AUC-ROC helps in appreciating its overall classification ability. Also, the precision-recall AUC is especially useful in imbalanced environments, where outbreaks are infrequent, such that the model will not be insensitive to minority class detection. Combining, these measures give a solid framework for evaluating model performance on both regression and classification problems.

To measure temporal accuracy quantitatively, average lead time (ALT) is employed to assess how far in advance a model can forecast the outbreak time. ALT is calculated as the divergence between the prediction time when the model forecasts a potential outbreak and the actual outbreak time, the day when cases cross a predefined level of detection, such as the peak day. This lead time is calculated for every outbreak in the test set, and the average of all N outbreaks produces the ALT. A larger ALT value means that the model consistently gives earlier warnings, which is essential for facilitating public health responses in a timely manner, for example, deploying resources, triggering containment actions, or alerting the public. Therefore, ALT is an important indicator of the effectiveness of a model in enabling proactive decision-making and mitigating the effect of infectious disease epidemics:

$$ALT = \frac{1}{N} \sum_{i=1}^{N} (\text{Prediction time} - \text{actual outbreak time})$$

Spatial accuracy is an important element of outbreak prediction models, and it is measured against the intersection over union (IoU) score. IoU measures how accurately a model can mark the affected geographic zones by comparing overlap between predicted and actual outbreak zones. It measures how much the intersection—the overlap of predicted and actual outbreak regions—is the union, the sum of the two regions. The higher the value of IoU, the more accurate is the spatial localization in the sense that the model is able to localize better the regions at risk. An IoU measure closer to 1 indicates good localization, and those close to 0 indicate poor correspondence between prediction and actuality. Correct positioning in space matters to guide directed interventions, maximize the use of resources, and minimize the disease transmission:

$$IoU = \frac{\text{Area of intersection}}{\text{Area of union}}$$

The performance of an outbreak prediction model as an early warning system is captured by the AQI, which is an aggregated index that weighs accuracy and reliability in real-time alerting. AQI encompasses three key elements: true positive alerts (TPAs), which are timely and correct early warnings that accurately forecasted the occurrence of actual outbreaks; false positives, which are false alarms that may generate unnecessary panic or misallocation of resources; and false negatives, which are false negatives that can be very serious public health threats due to unpreparedness. A high AQI therefore means that a model that not only captures emerging threats with adequate lead time but also suppresses false alerts and therefore is a reliable instrument for informing public health interventions and decision-making:

$$AQI = \frac{\text{TP alerts}}{\text{TP} + \text{FP} + \text{FN}}$$

Table 1 compares the predictive performance of several models used for infectious disease forecasting, evaluated using both regression metrics (MAE, RMSE, and MAPE) for case count prediction and classification metrics (F1-score and AUROC) for outbreak detection. The comparative performance evaluation of different models for infectious disease prediction shows EpiCastNet performs better than all others on both regression and classification metrics. It has the smallest error values for case count prediction with a MAE of 18.3%, RMSE of 29.7%, and MAPE of 11.3%, proving very accurate numerical prediction. Further, EpiCastNet exhibits superior classification performance with the best F1-score (0.79) and AUROC (0.92), as it possesses a strong ability to effectively detect outbreaks. DL models such as the transformer and static GNN excel in both accuracy and outbreak detection compared to other models, far outperforming classical statistical models such as ARIMA and Prophet. In general, the research demonstrates how well recent state-of-the-art neural architectures, that is, EpiCastNet, perform at giving accurate and reliable early warning of infectious disease outbreaks.

Table 1: Performance analysis – regression metrics.

| Model | MAE↓ | RMSE↓ | MAPE↓ | F1-score↑ | AUROC↑ |
|:---|:---|:---|:---|:---|:---|
| ARIMA | 38.7 | 59.1 | 23.4% | 0.52 | 0.71 |
| LSTM | 29.4 | 45.8 | 18.7% | 0.63 | 0.81 |
| Prophet | 31.2 | 47.5 | 20.1% | 0.58 | 0.78 |
| Static GNN | 24.8 | 38.2 | 15.6% | 0.68 | 0.84 |
| Transformer | 22.5 | 34.6 | 14.2% | 0.71 | 0.86 |
| EpiCastNet | 18.3 | 29.7 | 11.3% | 0.79 | 0.92 |

![](img/106ef0dba620d314f9842503e8ef40c8_169_0.png)

Figure 2: Error metrics – EpiCastNet.

Figure 2 evaluates the performances of different forecasting models on the basis of two important measures of error: MAE and RMSE. The story graphically supports that EpiCastNet performs better than conventional as well as deep models, that is, ARIMA, LSTM, Prophet, Static GNN, and Transformer. EpiCastNet demonstrates lowest MAE (18.3) and RMSE (29.7), which indicates higher precision in prediction and credibility. ARIMA, however, records highest errors (MAE: 38.7 and RMSE: 59.1), followed closely by LSTM and Prophet. The performance is always improved with the models, with transformer and static GNN better than the traditional techniques. The results confirm the effectiveness of EpiCastNet in reducing the errors of prediction and infer its strong strength in predicting challenging tasks.

![](img/106ef0dba620d314f9842503e8ef40c8_170_0.png)

Figure 3: MAPE analysis – EpiCastNet.

Figure 3 shows a trend of MAPE across different forecasting models, where lower values indicate better performance. This trend is seen in the decreasing MAPE from simple to advanced models. The highest error is exhibited by ARIMA with 23.40%, followed by Prophet (20.10%) and LSTM (18.70%), meaning low precision in their predictions. Other advanced models like static GNN (15.60%) and transformer (14.20%) yield better predictive accuracy. EpiCastNet shows the best MAPE value of 11.30%, which reflects the best and most precise predictions among all the models tested. This highlights the effectiveness of EpiCastNet in reducing relative prediction errors.

Table 2: Temporal and spatial frequency.

| Model | ALT (days)↑ | IoU (spatial precision)↑ |
|---|---|---|
| ARIMA | 1.8 | 0.41 |
| LSTM | 3.4 | 0.52 |
| Prophet | 2.9 | 0.49 |
| Static GNN | 4.1 | 0.60 |
| Transformer | 4.7 | 0.63 |
| EpiCastNet | 6.2 | 0.72 |

