When the doctor turns his head to the right, the corresponding angle $\varphi$ is a positive number. By modeling the feature triangels formed by the left and right pupil and nose tip, a head posture estimation model is established based on the geometric deformation of the head shape and the relative position of the facial feature points. The geometric model composed of multiple feature points overcomes the disadvantage of losing the location of a single feature point and converts the angle of head posture transformation into geometric surface deformation.

# 2.3. Traceless Kalman Filtering Tracking Combined with Triangles

Using the traditional classic Kalman filtering algorithm, we assume that the head and eye movements are uniform, thereby introducing linear Kaman filtering to complete head position tracking. However, under the interference of different factors, it is difficult to ensure a strictly linear system. Especially in the doctor's head-position-tracking system applied in this paper, the doctor's eye movements are frequent and complex and usually exhibit nonlinear motion. The assumption of linear motion is unreasonable, which results in the head deflection. The deviation of the eyes can lead to the loss of tracking, resulting in significant errors.

In order to improve the accuracy and robustness of head position tracking, we need to introduce nonlinear Kaman filtering for motion optimization. Currently, the commonly used nonlinear Kalman filtering algorithms include Extended Kalman Filter (EKF) and unscented Kalman filter. EKF assumes that the expected value of the result distribution is equal to the expected value of the map and considers only its local environment via linearization. The difference is that UKF [40] has a strong modeling uncertainty capability using unscented transformation (UT), only requires the first few moments of random parameters, and is easy to implement, which can overcome the shortcomings of local linearization of EKF to estimate expected values and distributions more accurately. For linear motion systems, the tracking and prediction effects using EKF and UKF are not significantly different from those using linear KF; However, for nonlinear systems, UKF has better performance than EKF, and as the degree of nonlinearity increases, the gap between the two algorithms will become increasingly large [41]. This paper considers using UKF algorithm to study a head-position-tracking system when doctors' heads undergo significant head deflection when transferring surgical forceps to nurses and adjusting the position of projectors.

Theoretically, UKF uses traceless transformation to process nonlinear system models, uses system state expansion to obtain sampling points and perform nonlinear transformation, thereby obtaining the probability distribution and corresponding statistical characteristics of random variables, and then combines them with the standard Kalman filtering framework for calculation. The first frame image in the video is collected via Kinect to obtain the iterative initial value of the observation state, and UKF is used to track the trajectory of the doctor's head and eyes. The proposed algorithm completes the modeling process of three-dimensional coordinates and three rotation angles using the UKF algorithm for the centroid of the feature triangle. The specific process of the UKF algorithm is as follows.

+   (1) Initialization.

```
\overline{\alpha}_0 = E[\underline{x}_0] (17)
```

```
P_0 = E[(x_0 - \overline{\alpha}_0)(x_0 - \overline{\alpha}_0)^T] (18)
```

The above formula is to substitute a non-linear function with a sigma point to obtain the corresponding non-linear function values, and then calculate the transformed mean $\overline{\alpha}_0$ and covariance $P_0$ from these point sets.

+   (2) Select $2n + 1$ sigma points $x_k$ in set form.