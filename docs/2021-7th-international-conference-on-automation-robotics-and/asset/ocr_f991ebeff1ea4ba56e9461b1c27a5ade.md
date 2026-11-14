To evaluate our model, we used the group of the collection (2222 measurements) that we retained for testing. In “Fig. 5” we draw for each measurement the points in a X-Y plot. The coordinates of each point represent the actual distance of the user from Beacon A in X-axis and our model prediction in Y-axis.

In “Fig. 6” we show the distribution of the prediction error (\(\epsilon\)) for our model for each testing measurement.

![](bbox=[0.12, 0.2, 0.46, 0.41])

Fig. 6. Distribution of the prediction error (\(\epsilon\))

# B. Phase Two

In phase two we get the predicted distances from each Beacon as estimated using the corresponding model from phase one. With these predicted distances we create circles having as a center the known position of the Beacon and a radius equal to the predicted distance from the model. After that, we find the intersection points of all circles “Fig. 7” With blue color in “Fig. 7” we show the circles having as a center the five Beacons and radius the predicted distance from phase one, while the red dots are the intersection points.

![](bbox=[0.12, 0.605, 0.44, 0.86])

Fig. 7. Phase two and three point calculation

# C. Phase Three

In the last phase, we get as input the intersection points from phase two and finds the Geometric median from the intersection points. The geometric media point is defined as the predicted location.

In “Fig. 7” we indicate with the green cross the calculated geometric median point, which represents our location estimation and the cyan cross the real location.

# VI. RESULTS

From the results we present in this section, we can conclude that our system has been able to achieve good accuracy in predicting the real position of the user. In “Fig. 8”, we present the histogram of the distribution of the distance error (denoted with \(\epsilon\), in “Fig. 7”) between the actual and predicted positions. In “Table I” that follows we show the values of the error distribution. The error calculation is based on the set of 2222 measurements that was used for testing of the model estimation against the actual user position.

We observed that our system has an average accuracy of 69.58cm and can predict the location with less than a meter accuracy in 80,55% of all cases and with an accuracy of fewer than 1.5 meters in 93.92% of the cases.

![](bbox=[0.53, 0.42, 0.91, 0.635])

Fig. 8. Distance error (\(\epsilon\)) distribution

TABLE I. DISTANCE ERROR (E) DISTRIBUTION

| | 0-25 | 25-50 | 50-75 | 75-100 | 100-125 | 125-150 | >150 |
|---|---|---|---|---|---|---|---|
| Count | 324 | 570 | 488 | 408 | 200 | 97 | 135 |
| Percentage | 14.58 | 25.65 | 21.96 | 18.36 | 9.01 | 4.37 | 6.08 |

# VII. CONCLUSION

It is essential to develop a localization system that can achieve high levels of accuracy in building-scale real-world environments using low cost and ubiquitous technologies like those available in smartphones and Bluetooth devices. In this paper, we considered the challenges of developing a system by using RSSI from Bluetooth Beacons following a machine learning approach. We create a dataset with values from Bluetooth RSSI and train the neural network model to predict the distance from a specific Beacon. After that we use the