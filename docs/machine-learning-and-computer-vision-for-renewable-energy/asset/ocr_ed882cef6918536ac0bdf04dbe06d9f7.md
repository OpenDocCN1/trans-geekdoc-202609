# Electricity Production Prediction by Microsoft Azure

# Figure 19. Combining data within one date

![](bbox=[0.21, 0.16, 0.81, 0.655])

These operations are shown in Figure 20 and Figure 21 in the Execute Python Script block. The result of both scripts is shown in Figure 22 (excerpts from different time periods are shown). In addition, the script shown in Figure 21, allows to plot the distribution of energy production by the measurement date (Figure 23).

The next operation involves dividing the data into training and testing the model in the ratio of 75% and 25%, respectively. For this, the Split Data block is used (Figure 24).

The output of the left port of the Split Data block and the output of the Linear Regression analysis block are fed to the input of the Train Model creation block. The level of AES energy production is chosen as the target criterion for the Train Model block (Figure 25).

The Score Model block with default settings is used to obtain a prediction of the level of energy production. The forecast result (Scored Labels column) is shown in Figure 26. As can be seen from the figure, the accuracy of the forecast is quite high.