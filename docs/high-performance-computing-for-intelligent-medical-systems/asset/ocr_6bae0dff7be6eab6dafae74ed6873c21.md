layers. More convolutional layers brought no more significant improvement. Batch normalization layers are introduced between CNN layers. They help the training process to speed up and make the network less sensitive to initial conditions. We have employed two average pooling layers for downsampling the data. They carry out the task by dividing the input data into rectangular regions (1 x 6 sections in our work), and then, calculating the average value for each region. A drop-out layer is also added to the network to help it avoid overfitting. The layer sets its input values randomly equal to zero during the training phase. We have chosen the ReLu function as the non-linear function after each convolutional layer to perform threshold operation. Equation (4.12) describes the function.

```
\( f(x) = \left\{ \begin{array}{ll} x, \ x \geqslant 0; \\ 0 \quad x < 0. \end{array} \right. \) (4.12)
```

+   • **Performance:** The performance of the CNN network is shown in table 4.3. As the results indicate, the performance is improved dramatically. Now, both estimations meet the requirements of the AAMI standard. Figure 4.9 also depicts the regression plot for the estimation results. The high correlation coefficients prove the effectiveness of the new approach based on the abilities of CNN networks for both appropriate feature learning and parameter estimation.

+   • **Temporal information loss:** The CNN network performs the estimation in each time step based on the PPG segment corresponding to that time step. Therefore, it fails to include temporal information carried in the PPG waveform. Undoubtedly, the BP fluctuations do not happen abruptly in each time step. They depend heavily on the previous values of BP too. Despite this fact, the CNN network carries out the estimation merely based on the current information provided to the network. In other words:

```
\( \text{BP}(t_k) = f(x_k) \) (4.13)
```

Therefore, if we include temporal variations of the PPG waveform in the estimation procedures, we can expect even further estimation improvement. In the next subsection, we propose a way for embedding this crucial information in the estimation process.

| Blood pressure | R | ME | MAE | RMSE | STD | Subjects # | AAMI |
|---|---|---|---|---|---|---|---|
| Systolic BP | 0.91 | -0.01 | 5.40 | 7.86 | 7.86 | 200 | √ |
| Diastolic BP | 0.89 | -0.01 | 3.13 | 4.24 | 4.24 | 200 | √ |