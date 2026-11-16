![](bbox=[0.15, 0.105, 0.85, 0.305])

Figure 4.12. Box and Whisker diagram of errors for the proposed models.

to the reality that the LSTM layers could consider temporal information in the calculations.

Figure 4.12 shows the Box and Whisker diagram of errors for the proposed models [25]. Each diagram shows the estimation errors for testing data through their quartiles. Red markers show outliers. It can be seen easily from the figure that the error distribution becomes narrower and more centered around zero as we go through the steps.

Figure 4.13 also depicts the error distribution over systolic and diastolic BP values. The peak values diminish considerably for the methods based on CNN and LSTM networks.

Table 4.5 evaluates the performance of all models based on another new standard. The British Hypertension Standard assigns a grade for a BP monitoring device considering the cumulative percentage of absolute error values under different thresholds [26]. As table 4.5 indicates, the performance improves when more suitable steps are taken to develop the models. Both systolic and diastolic BPs acquire Grade A when we estimate BP based on the CNN–LSTM architecture.

# 4.5.1 Comparison with other methods

Table 4.6 compares the best results obtained in this chapter based on the end-to-end CNN–LSTM architecture with some other studies. The table encompasses sample models based on both methods based on hand-crafted features (or mentioned as physiological model parameters in some studies) and models based on machine-learned representations of the bio-signals. The table also indicates the number of patients and also the tools used to implement the models.

For a fair comparison of different methods, we should apply the methods on the same data and under similar criteria. However, the table provides some insight into several other models and their relative performance. Considering the number of subjects, the table confirms that our CNN–LSTM architecture provides relatively accurate estimations for both systolic and diastolic BPs.