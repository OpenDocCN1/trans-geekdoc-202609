
![](img/fe161b7f6e96e35e7e853eece52c6dce_489_0.png)

(a) PM positions.

![](img/fe161b7f6e96e35e7e853eece52c6dce_489_1.png)

(b) Perimeter Monitoring (PM) task seen from the front camera p.o.v.

![](img/fe161b7f6e96e35e7e853eece52c6dce_489_2.png)

(c) PA positions.

![](img/fe161b7f6e96e35e7e853eece52c6dce_489_3.png)

(d) Pedestrian Avoidance (PA) task seen from the front camera p.o.v.

![](img/fe161b7f6e96e35e7e853eece52c6dce_489_4.png)

(e) U-turn positions.

![](img/fe161b7f6e96e35e7e853eece52c6dce_489_5.png)

(f) U-turn task seen from the front camera p.o.v.

FIGURE 13.5 The proposed tasks performed by the self-aware vehicle. The odometry data of the vehicle is displayed in blue on the left, whereas the red dots show where the pedestrian is located. On the right we propose some images from the front camera of the vehicle, while performing the three tasks.

## 13.4.3.1 Pedestrian avoidance task

Figs. 13.7 and 13.8 show the anomalies detected when filtering with the above-described framework on the odometry and on the video data, respectively. In the former case, anomalies at continuous and discrete levels are displayed only, while in the latter, anomalies at the observation level are shown too. Green areas refer to straight motion zones, yellow areas to curving motion zones, and blue areas to zones displaying abnormal actions (i.e., the pedestrian avoidance maneuver).

In Fig. 13.7 we distinguish three plots. The black plot displays the mean value of the GEs, that we call \tilde{e}_t. The red plot shows anomaly Db2 (Eq. (13.35)). To notice the similarity between these two plots, as they both represent a comparison between \pi(X_k) and \lambda(X_k). Both of them display high anomaly values corresponding to the Pedestrian avoidance motion and false positives due to slightly irregular curving actions. However, it is to note how Db1 gives better results, as it considers the full probability information of \pi(X_k) and \lambda(X_k), while \tilde{e}_t discards the covariance information \Sigma_{S_k} and only keeps the mean \mu_{S_k}.

FIGURE 13.6 Odometry and video Clustering.

(a) Odometry clustering.

(b) Video Clustering.

FIGURE 13.7 Odometry multilevel anomaly values for Pedestrian Avoidance task.

### Anomalies at the continuous level

### Anomalies at the discrete level

Finally, the blue plot in Fig. 13.7 is related to anomaly Db1 (Eq. (13.36)). This anomaly becomes particularly relevant at the center of the abnormal motion. For example, we could observe that around time t = 600, particles get assigned to clusters relative to the curve on the upper right of Fig. 13.6a, due to the motion mostly resembling this area. However, the likelihood of being in that area is quite low.

The second plot of Fig. 13.7 refers to the KLDA anomaly described in Eq. (13.34). Pedestrian avoidance zones clearly display a very high anomaly value, a consequence of abnormal passages between clusters.

Fig. 13.8 displays these same types of anomalies in the video data case. Additionally, the first plot shows anomalies at the observation level. Black and blue lines refer to the direct VAE reconstruction anomalies, signaling an unsuitable observation model. On the other hand, red and green anomalies are the image-level errors due to discrepancy between observation and prediction.

### Anomalies at the generalized observation level

### Anomalies at the continuous level

### Anomalies at the discrete level

![](img/fe161b7f6e96e35e7e853eece52c6dce_491_0.png)

FIGURE 13.8 Video multilevel anomaly values for Pedestrian Avoidance task.

### Anomalies at the continuous level

### Anomalies at the discrete level

![](img/fe161b7f6e96e35e7e853eece52c6dce_491_1.png)

FIGURE 13.9 Odometry multilevel anomaly values for pedestrian avoidance through U-turn task.

![](img/fe161b7f6e96e35e7e853eece52c6dce_493_0.png)

FIGURE 13.11 Examples of image-level anomalies. With the symbol \mathcal{R}\{X\} we express in a concise way the decoding of the latent variable X through the VAE decoder.

Three example cases are shown. i) In the first row, an example of normal straight motion taken from the PA dataset is reported. ii) In the second row, we display a time instant previous to the start of the avoidance maneuver in the PA dataset. The presence of the pedestrian causes an anomaly that is strictly related to the observation model. A new VAE should be trained to learn the “pedestrian” concept. iii) In the third row, we have an anomaly due to performing a curve in the opposite direction w.r.t. training, in the U-turn dataset. To note how, despite not being optimal, the reconstruction is reasonable. On the other hand, the prediction model can capture the anomaly in a more evident way. This is because, when observing the curve-related part of the courtyard, we could expect to be moving left (see the red color of the predicted OF \mathcal{R}\{\hat{X}_t\}), but instead we perform a turn to the right.

## 13.4.3.4 Anomaly detection evaluation

To evaluate the anomaly detection method, the anomaly estimation obtained at the different abstraction levels is compared with the Ground Truth (GT). The GT of the PA and U-turn scenarios are built by hand, considering the vehicle’s motion for the odometry data. In the odometry U-turn case, the entire sequence from the beginning of the first U-turn to the end of the second one is considered abnormal, as the vehicle moves in the opposite direction w.r.t. training. For the video data, 10 frames before starting the abnormal maneuver are added to the positive GT to account for the pedestrian’s presence; additionally, a simple shadow detection method is used to account for abnormal shadow zones.

In Figs. 13.12 and 13.13, the Receiver Operating Characteristic (ROC) curves are shown for the anomaly results on odometry and video data, respectively. A ROC curve plots the values of True Positive Rate (TPR) and False Positive Rate (FPR) at different anomaly thresholds, where TPR = TP/(TP+FN) and FPR = FP/(FP+TN). In our case, TPR and FPR consist respectively in the percentage of times in which anomalies are correctly identified and in which they are incorrectly assigned. The AUC (Area Under the Curve) can be used as a measurement of the performance of the method. Another measure of performance is the accuracy (ACC), given by the sum of True Positives (TPs) and True Negatives (TNs). In the field of incremental self-aware systems, further evaluation methods could be used, e.g., how good are the anomalies to extract errors allowing to build better models.

![](img/fe161b7f6e96e35e7e853eece52c6dce_494_0.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_494_1.png)

FIGURE 13.12 ROC curves for odometry data.

![](img/fe161b7f6e96e35e7e853eece52c6dce_494_2.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_494_3.png)

FIGURE 13.13 ROC curves for video data.

In Fig. 13.12, the two continuous anomaly values (i.e., Db1 and Db2) are normalized and summed together to provide a single anomaly value, displaying much higher performance than its two separate components.

![](img/fe161b7f6e96e35e7e853eece52c6dce_496_0.png)

### Db2 anomaly for SP features in PA case

### Db2 anomaly for SP features in U-turn case

### Db2 anomaly for SV features in U-turn case

FIGURE 13.15 Control data (SP, SV, VP) anomaly at continuous level for U-turn case.

In all these works, anomalies on a maximum of three levels have been considered. However, higher abstraction levels and, consequently, higher levels of anomalies could be defined. An example in this direction is provided by Zaal et al. (2019): for each task, a graph is obtained connecting adjacent clusters; where a high anomaly on the graph is detected, an emergent concept is found.

## 13.5 Conclusions

In this chapter, we presented a framework to detect anomalies in time-series data for a Self-Aware system. Under the Self-Awareness framework, an agent dealing with multimedia data, including high and low dimensional data, is capable of detecting anomalies at hierarchical levels, which realize an essential step to continually learn a new dynamic model that encodes the emergent abnormal behavior. For the high dimensional data, a VAE is used to reduce the data-dimensionality. The features are extracted and incorporated in a generalized state vector, whereas in low dimensional data, features are extracted directly from observations and incorporated in a generalized state vector. Training the dynamic model as a probabilistic graphical model structured in a Dynamic Bayesian Network (DBN) forms the bridge between high and low dimensional data. It is shown how the messages passing inside the DBN can be exploited to define a hierarchy of anomalies based on probabilistic distances. A real data-set
