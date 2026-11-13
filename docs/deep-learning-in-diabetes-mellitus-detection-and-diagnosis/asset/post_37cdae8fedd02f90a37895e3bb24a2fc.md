
a GRU, producing a condensed tensor h_T containing temporal patterns. In the end, the forecasted BG level ŷ_{T+W} is derived from h_T using f_out(·).

The mean square error (MSE) is utilized as the training loss, and the Adam optimizer (Kingma and Ba, 2015) is employed to optimize the learnable parameters.

Furthermore, FL is illustrated in Figure 3.2. Only the respective personalized models on the clients have access to personal data. After undergoing training for a predetermined number of epochs on the local devices, the trainable parameters of the individual method are transmitted to a central server, where a global approach is derived by summarizing these parameters. Subsequently, the personalized models on the clients are updated with the global model’s latest parameters, effectively synchronizing the personal and global learnings. This cycle continues until the models reach an optimal state. Through this methodology, participant privacy is robustly safeguarded, because personal data remains exclusively within their domain. At the same time, the server is able to aggregate global trends without compromising individual privacy. It’s worth noting that in our study, FL is emulated through a multi-process approach, treating each client and the server as separate processes.

![](img/7df621e14c1a5d96077d3e56e3977008_56_0.png)

### 3.2.5 Metrics

We consider three metrics in this work. RMSE is employed to thoroughly assess model performance, guiding the selection of optimal trainable parameters and attribute combinations. Besides, mean absolute relative difference (MARD) is also considered, making it ideal for evaluating predictions of lesser magnitudes. Moreover, mean absolute error (MAE) is used for an easy comparison with other models, especially since MAE is a standard metric used by all entries in the Ohio 2020 challenge.

## 3.3 EXPERIMENTS AND RESULTS

### 3.3.1 Impact of Attributes

To effectively leverage various attributes in the OhioT1DM dataset and experimental resources, we experimented with a select number of attribute combinations. Interestingly, we discovered that employing six specific attributes, including “glucose level”, “bolus”, “meal”, “sleep”, “exercise”, and “finger stick”, consistently yields noticeable improvements in most scenarios.

Therefore, our initial experiment aimed to determine the positive influence of each of these six attributes on RMTS-BGLP. In this experiment, we systematically excluded one attribute at a time (apart from “glucose level”) from the set of six attributes. We then compared the performance of GAM utilizing all six attributes against the performance of GRU using only BG. Next, if GAM with these six attributes outperforms the others, it indicates that each attribute contributes positively to RMTS-BGLP. Conversely, if GRU with only BG shows the least favorable outcomes, it suggests that the combination of these six attributes is effective. The results of this experiment are detailed in Tables 3.2 and 3.3.

Additionally, we aim to explain our decision to exclude certain attributes. To do this, we tested the inclusion of one additional attribute at a time to the existing set of six attributes. We then compared the results to the performance of GAM with just the original six attributes. If the addition of a new attribute does not lead to improvements over the GAM containing the six factors in most scenarios, we opted not to include other factors (see Tables 3.4 and 3.5).

In general, when the prediction window W is set to 6, the “GAM+6 attributes” model demonstrates superior performance in terms of both RMSE and MARD across various settings. The mean RMSE for “GAM+6 attributes” is 18.91 mg/dL (W=6), outperforming other models whose

TABLE 3.2 The Influence of "Glucose Level", "Bolus", "Meal", "Finger Stick", "Exercise", and "Sleep" (Measured by RMSE, W=6)

| Method | 559 | 563 | 570 | 575 | 588 | 591 | 540 | 544 | 552 | 567 | 584 | 596 | Average |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| GAM+6 attributes w/o meal | 19.51 | 17.84 | 16.94 | 22.52 | 17.32 | 21.04 | 21.20 | 16.26 | 16.26 | 21.57 | 22.23 | 16.82 | 19.13 |
| GAM+6 attributes w/o bolus | 19.74 | 18.00 | 16.74 | 22.40 | 17.08 | 20.89 | 21.70 | 15.62 | 16.70 | 21.98 | 23.13 | 16.40 | 19.20 |
| GAM+6 attributes w/o finger stick | 19.95 | 17.82 | 17.00 | 22.46 | 16.94 | 21.46 | 20.99 | 16.22 | 16.41 | 21.98 | 22.63 | 16.10 | 19.16 |
| GAM+6 attributes w/o sleep | 19.01 | 17.91 | 16.12 | 22.50 | 17.17 | 20.83 | 21.06 | 16.12 | 16.47 | 21.52 | 22.28 | 16.27 | 18.94 |
| GAM+6 attributes w/o exercise | 19.11 | 17.98 | 16.99 | 22.42 | 17.30 | 21.00 | 20.89 | 16.27 | 16.19 | 21.54 | 22.00 | 16.02 | 18.97 |
| GAM+6 attributes | 19.42 | 17.60 | 16.66 | 22.28 | 17.06 | 20.72 | 21.01 | 15.95 | 16.50 | 21.58 | 22.22 | 16.01 | 18.92 |
| GRU glucose level | 19.44 | 18.29 | 18.60 | 23.62 | 18.49 | 21.83 | 22.77 | 18.00 | 17.37 | 22.92 | 23.59 | 17.20 | 20.18 |

TABLE 3.3 The Influence of "Glucose Level", "Bolus", "Meal", "Finger Stick", "Exercise", and "Sleep" (Measured by MARD, W = 6)

| Method | 559 | 563 | 570 | 575 | 588 | 591 | 540 | 544 | 552 | 567 | 584 | 596 | Average |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| GAM+6 attributes w/o meal | 8.83 | 7.75 | 5.38 | 9.74 | 7.55 | 12.17 | 10.87 | 7.74 | 9.20 | 10.91 | 10.91 | 8.78 | 9.15 |
| GAM+6 attributes w/o bolus | 8.89 | 7.75 | 5.37 | 9.55 | 7.49 | 12.03 | 11.09 | 7.49 | 9.36 | 11.11 | 11.47 | 8.59 | 9.18 |
| GAM+6 attributes w/o finger stick | 8.97 | 7.73 | 5.38 | 9.50 | 7.37 | 12.25 | 10.88 | 7.72 | 9.21 | 11.14 | 11.20 | 8.55 | 9.16 |
| GAM+6 attributes w/o sleep | 8.71 | 7.73 | 5.21 | 9.60 | 7.45 | 11.85 | 10.78 | 7.62 | 9.24 | 10.65 | 10.93 | 8.48 | 9.02 |
| GAM+6 attributes w/o exercise | 8.62 | 7.71 | 5.36 | 9.48 | 7.50 | 11.94 | 10.75 | 7.75 | 9.06 | 10.85 | 10.79 | 8.49 | 9.03 |
| GAM+6 attributes | 8.79 | 7.65 | 5.26 | 9.44 | 7.42 | 11.97 | 10.78 | 7.61 | 9.15 | 10.87 | 11.03 | 8.43 | 9.03 |
| GRU glucose level | 8.99 | 7.98 | 5.74 | 10.27 | 8.03 | 12.35 | 11.58 | 8.69 | 9.66 | 11.24 | 11.26 | 8.98 | 9.56 |

| Method | 559 | 563 | 570 | 575 | 588 | 591 | 540 | 544 | 552 | 567 | 584 | 596 | Average |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| GAM +6 attributes +basal | 19.23 | 19.76 | 19.42 | 22.34 | 17.56 | 20.92 | 20.69 | 16.06 | 16.86 | 21.84 | 25.07 | 16.01 | 19.64 |
| GAM +6 attributes +basis skin temperature | 19.27 | 17.95 | 16.21 | 22.71 | 16.99 | 21.13 | 20.96 | 16.42 | 16.49 | 21.74 | 22.61 | 16.01 | 19.04 |
| GAM +6 attributes +basis GSR | 19.40 | 18.03 | 16.60 | 22.45 | 17.09 | 21.22 | 20.77 | 16.34 | 16.63 | 21.72 | 22.68 | 16.20 | 19.09 |
| GAM +6 attributes +basis sleep | 19.06 | 17.78 | 16.54 | 22.07 | 17.23 | 20.83 | 21.28 | 15.82 | 16.44 | 21.45 | 22.00 | 15.93 | 18.87 |
| GAM +6 attributes +acceleration | 19.31 | 17.93 | 16.42 | 22.24 | 17.21 | 20.71 | 21.08 | 15.84 | 16.69 | 21.82 | 22.15 | 15.89 | 18.94 |
| GAM +6 attributes +work | 19.39 | 17.78 | 16.80 | 22.10 | 16.94 | 20.83 | 21.10 | 16.06 | 16.54 | 21.50 | 21.75 | 15.91 | 18.89 |
| GAM +6 attributes +basis steps | 19.05 | 17.68 | 16.43 | 22.38 | 17.26 | 20.77 | 21.17 | 15.85 | 16.36 | 21.72 | 22.18 | 16.04 | 18.91 |
| GAM +6 attributes +basis heart rate | 19.67 | 17.44 | 16.71 | 22.57 | 16.97 | 20.62 | 21.13 | 16.10 | 16.52 | 21.65 | 22.04 | 16.05 | 18.96 |
| GAM +6 attributes +basis air temperature | 19.31 | 17.68 | 16.23 | 22.32 | 17.18 | 20.72 | 21.03 | 15.98 | 16.16 | 21.66 | 22.06 | 16.13 | 18.87 |
| GAM +6 attributes +day of week | 18.85 | 17.68 | 16.74 | 22.69 | 16.98 | 20.73 | 21.08 | 15.82 | 16.23 | 21.90 | 22.49 | 16.32 | 18.96 |
| GAM +6 attributes +total seconds | 19.24 | 17.87 | 16.32 | 22.33 | 16.90 | 21.17 | 20.90 | 16.07 | 16.53 | 21.88 | 22.50 | 16.09 | 18.98 |
| GAM +6 attributes | 19.42 | 17.60 | 16.66 | 22.28 | 17.06 | 20.72 | 21.01 | 15.95 | 16.50 | 21.58 | 22.22 | 16.01 | 18.92 |

| Method | 559 | 563 | 570 | 575 | 588 | 591 | 540 | 544 | 552 | 567 | 584 | 596 | Average |
| :--- | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| GAM +6 attributes +basal | 8.75 | 8.51 | 7.15 | 9.48 | 7.71 | 12.05 | 10.70 | 7.64 | 9.40 | 10.99 | 13.94 | 8.36 | 9.56 |
| GAM +6 attributes +basis skin temperature | 8.67 | 7.68 | 5.29 | 9.81 | 7.38 | 12.05 | 10.84 | 7.76 | 9.38 | 10.74 | 11.10 | 8.47 | 9.10 |
| GAM +6 attributes +basis GSR | 8.88 | 7.76 | 5.27 | 9.85 | 7.51 | 12.00 | 10.76 | 7.65 | 9.46 | 10.86 | 11.16 | 8.52 | 9.14 |
| GAM +6 attributes +basis sleep | 8.47 | 7.71 | 5.28 | 9.36 | 7.46 | 11.80 | 10.84 | 7.59 | 9.11 | 10.55 | 10.96 | 8.40 | 8.96 |
| GAM +6 attributes +acceleration | 8.66 | 7.69 | 5.22 | 9.49 | 7.42 | 11.92 | 10.71 | 7.55 | 9.31 | 11.03 | 10.95 | 8.43 | 9.03 |
| GAM +6 attributes +work | 8.73 | 7.71 | 5.31 | 9.47 | 7.35 | 11.93 | 10.77 | 7.57 | 9.28 | 10.83 | 10.74 | 8.40 | 9.01 |
| GAM +6 attributes +basis steps | 8.64 | 7.63 | 5.27 | 9.49 | 7.44 | 11.85 | 10.77 | 7.50 | 9.16 | 10.87 | 10.92 | 8.46 | 9.00 |
| GAM +6 attributes +basis heart rate | 8.78 | 7.67 | 5.30 | 9.68 | 7.42 | 11.77 | 10.79 | 7.56 | 9.21 | 10.83 | 10.89 | 8.50 | 9.03 |
| GAM +6 attributes +basis air temperature | 8.61 | 7.68 | 5.42 | 9.56 | 7.43 | 11.87 | 10.73 | 7.57 | 9.12 | 10.91 | 10.83 | 8.54 | 9.02 |
| GAM +6 attributes +day of week | 8.59 | 7.69 | 5.32 | 9.54 | 7.37 | 11.96 | 10.83 | 7.53 | 9.14 | 10.99 | 11.17 | 8.53 | 9.06 |
| GAM +6 attributes +total seconds | 8.78 | 7.70 | 5.20 | 9.72 | 7.40 | 12.07 | 10.71 | 7.57 | 9.26 | 10.98 | 11.07 | 8.45 | 9.08 |
| GAM +6 attributes | 8.79 | 7.65 | 5.26 | 9.44 | 7.42 | 11.97 | 10.78 | 7.61 | 9.15 | 10.87 | 11.03 | 8.43 | 9.03 |
