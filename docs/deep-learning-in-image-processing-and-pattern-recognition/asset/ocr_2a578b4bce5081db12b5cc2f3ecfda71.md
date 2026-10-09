UKF algorithm combined with feature triangles in this article is smaller than that of the KF algorithm with a single feature point. This is because when the head is deflected significantly and the face is occluded, the linear KF algorithm will cause feature point tracking loss and generate large errors. The improved UKF algorithm combined with feature triangles overcomes the shortcomings of linear KF and has strong noise resistance, which is suitable for nonlinear head-position-tracking models.

# Table 3. Error comparison of different tracking algorithms.

| Results | KF + Triangle | UKF + Triangle |
| :--- | :---: | :---: |
| X/cm | 1.53 | 1.39 |
| Y/cm | 1.76 | 1.44 |
| Z/cm | 1.39 | 1.17 |
| Pitch/\u00b0 | 1.67 | 1.24 |
| Yaw/\u00b0 | 1.38 | 1.12 |
| Roll/\u00b0 | 1.57 | 1.16 |

The main comparison in this article is between the true values provided in the public dataset and the predicted values obtained by the algorithm in this article, as well as the measured and predicted values obtained from the experimental dataset via camera calibration, model establishment, parameter conversion, and other work. KF and UKF tracking comparisons are conducted on the above data, and the issue of inaccurate feature point localization caused by the head deflection of doctors wearing masks is addressed, which makes traditional linear Kalman filtering algorithms unable to accurately track feature points. The improved feature triangle and UKF tracking algorithm in this paper can approximate the posterior mean and variance of the nonlinear system via traceless transformation to update the time and measurement of the doctor\u2019s head state.

However, the perspective tracking mentioned in previous literature mostly focuses on the driver\u2019s head posture, which is different from the application environment in this article. The improved feature triangle-based unscented Kalman perspective-tracking environment in this article can overcome the limitations of traditional Kalman filtering for large head deflection and pose estimation of masked faces, making it more suitable for head tracking from a doctor\u2019s perspective. Accurate tracking of pose information can be achieved on both the Bifi public dataset, and the dataset collected on the surgical simulation platform. Thus, the effectiveness of the algorithm proposed in this paper was verified from two aspects: the actual test dataset and the public test dataset.

# 5. Conclusions

Aiming at the problem that the head deflection of doctors wearing masks can easily lead to the loss of feature point positioning, and the linear Kalman filtering algorithm cannot accurately track feature points. This paper implements an improved perspective-tracking model that combines feature triangles and unscented Kalman filtering algorithm. From the real-time output data, it can be seen that the maximum angular error between the predicted value and the measured value of the improved unscented Kalman filter is 0.3\u00b0, and the maximum coordinate error is 1.74 cm, which meets the experimental requirements. Compared to the linear Kalman filtering algorithm, the tracking accuracy of the geometric triangle-based unscented Kalman filtering algorithm in this paper has been improved by 3.3%, and the accuracy has been improved by 4%. Compared to tracking the average of three feature points, the algorithm in this paper improves the accuracy of target tracking by 5.5% and accuracy by 1.8%, which can meet the needs of doctors for surgery.

**Author Contributions:** Conceptionalization, X.Y., YZ., H.W. and A.W.; methodology, X.Y. and Y.Z.; software, Y.Z.; validation X.Y.; writing\u2014review and editing X.Y., Y.Z., H.W. and A.W. All authors have read and agreed to the published version of the manuscript.