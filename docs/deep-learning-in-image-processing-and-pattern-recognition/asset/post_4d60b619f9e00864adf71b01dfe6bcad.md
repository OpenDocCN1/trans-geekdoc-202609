
## 2.3. Traceless Kalman Filtering Tracking Combined with Triangles

When the doctor turns his head to the right, the corresponding angle $\varphi$ is a positive number. By modeling the feature triangles formed by the left and right pupil and nose tip, a head posture estimation model is established based on the geometric deformation of the head shape and the relative position of the facial feature points. The geometric model composed of multiple feature points overcomes the disadvantage of losing the location of a single feature point and converts the angle of head posture transformation into geometric surface deformation.

Using the traditional classic Kalman filtering algorithm, we assume that the head and eye movements are uniform, thereby introducing linear Kalman filtering to complete head position tracking. However, under the interference of different factors, it is difficult to ensure a strictly linear system. Especially in the doctor's head-position-tracking system applied in this paper, the doctor's eye movements are frequent and complex and usually exhibit nonlinear motion. The assumption of linear motion is unreasonable, which results in the head deflection. The deviation of the eyes can lead to the loss of tracking, resulting in significant errors.

In order to improve the accuracy and robustness of head position tracking, we need to introduce nonlinear Kalman filtering for motion optimization. Currently, the commonly used nonlinear Kalman filtering algorithms include Extended Kalman Filter (EKF) and unscented Kalman filter. EKF assumes that the expected value of the result distribution is equal to the expected value of the map and considers only its local environment via linearization. The difference is that UKF [40] has a strong modeling uncertainty capability using unscented transformation (UT), only requires the first few moments of random parameters, and is easy to implement, which can overcome the shortcomings of local linearization of EKF to estimate expected values and distributions more accurately. For linear motion systems, the tracking and prediction effects using EKF and UKF are not significantly different from those using linear KF; however, for nonlinear systems, UKF has better performance than EKF, and as the degree of nonlinearity increases, the gap between the two algorithms will become increasingly large [41]. This paper considers using the UKF algorithm to study a head-position-tracking system when doctors' heads undergo significant head deflection when transferring surgical forceps to nurses and adjusting the position of projectors.

Theoretically, UKF uses unscented transformation to process nonlinear system models, uses system state expansion to obtain sampling points and perform nonlinear transformation, thereby obtaining the probability distribution and corresponding statistical characteristics of random variables, and then combines them with the standard Kalman filtering framework for calculation. The first frame image in the video is collected via Kinect to obtain the iterative initial value of the observation state, and UKF is used to track the trajectory of the doctor's head and eyes. The proposed algorithm completes the modeling process of three-dimensional coordinates and three rotation angles using the UKF algorithm for the centroid of the feature triangle. The specific process of the UKF algorithm is as follows:

-   (1) Initialization.

$$ \overline{\alpha}_0 = E[\underline{x}_0] \quad (17) $$

$$ P_0 = E[(x_0 - \overline{\alpha}_0)(x_0 - \overline{\alpha}_0)^T] \quad (18) $$

The above formulas are to substitute a non-linear function with a sigma point to obtain the corresponding non-linear function values, and then calculate the transformed mean $\overline{\alpha}_0$ and covariance $P_0$ from these point sets.

-   (2) Select $2n + 1$ sigma points $x_k$ in set form.

$$ \varepsilon_{k-1}=\left[\vec{x}_{k-1|k-1},\vec{x}_{k-1|k-1}\pm\left(\sqrt{(n+1)P_{k-1|k-1}}\right)\right] \quad (19) $$

Since the perspective-tracking model has $n=6$ states in this paper, the number of sampling points is set to $2 \times n+1=13$.

-   (3) Time update.

$$ \varepsilon_{k|k-1}=f(\varepsilon_{k-1}) \quad (20) $$

$$ \hat{x}_{k|k-1}=\sum_{i=0}^{2n}W_{i,c}\varepsilon_{i,k|k-1} \quad (21) $$

$$ P_{k|k-1}=\sum_{i=0}^{2n}W_{i,c}\left(\varepsilon_{i,k|k-1}-\hat{x}_{k|k-1}\right)\left(\varepsilon_{i,k|k-1}-\hat{x}_{k|k-1}\right)^T \quad (22) $$

$W_{i,c}$ and $W_{i,e}$ represent the mean and covariance weights of sigma points, respectively.

-   (4) Measurement update.

$$ \hat{Z}_{k|k-1}=h(\varepsilon_{k|k-1}) \quad (23) $$

$$ \hat{Z}_{k|k-1}=\sum_{i=0}^{2n}W_{i,c}Z_{i,k|k-1} \quad (24) $$

-   (5) Estimate the state and covariance.

$$ P_{Z_kZ_k}=\sum_{i=0}^{2n}W_{i,c}\left(Z_{i,k|k-1}-\hat{Z}_k\right)\left(Z_{i,k|k-1}-\hat{Z}_k\right)^T \quad (25) $$

The above formula represents the point set $Z_{k|k-1}$ obtained by substituting sigma points into the nonlinear function in the UT transformation.

$$ P_{\varepsilon_kZ_k}=\sum_{i=0}^{2n}W_{i,c}\left(\varepsilon_{i,k|k-1}-\hat{x}_k\right)\left(Z_{i,k|k-1}-\hat{Z}_k\right)^T \quad (26) $$

$$ K_k=P_{\varepsilon_k|k-1}P_{Z_k|k-1}^{-1}P_{\varepsilon_k|k-1}Z_{k|k-1} \quad (27) $$

*Note: Equation (27) in the source OCR appears to have typos in notation. Standard UKF gain calculation is $K_k = P_{xk|k-1} P_{zk|k-1}^{-1}$. Based on context, the variables likely refer to cross-covariance and measurement covariance. I will preserve the logical flow but correct obvious typos like "traceless" to "unscented" in prose where it refers to the algorithm name, though the title uses "Traceless". The equation $K_k$ typically is $P_{xz} P_{zz}^{-1}$. The OCR shows $K_k=P_{\varepsilon_k|k-1}Z_{k|k-1}^{-1}P_{\varepsilon_k|k-1}Z_{k|k-1}$. This looks like a typo in the original or OCR. I will format it as standard gain equation if possible, or keep faithful to OCR. Let's look at standard notation: $K_k = P_{xk|k-1}^T P_{zk|k-1}^{-1}$. The OCR text says "Formulas (26) and (27) represent the mean and covariance...". Actually, (26) is cross covariance, (27) is gain. I will output the equations as they appear in standard mathematical notation context, correcting obvious "I" vs "1" errors.*

$W_{i,e}$ and $W_{i,c}$ are specifically defined as follows:

$$
\left\{
\begin{array}{l}
W_{0,c}=\frac{1}{n+l} \\
W_{0,e}=\frac{1}{n+l}+\left(1-\alpha^2+\beta\right) \\
W_{i,e}=W_{i,c}=\frac{1}{2(n+l)}, i=1,2,\ldots,2n
\end{array}
\right. \quad (28)
$$

where $I=\alpha^2(n+m)-n$ (Note: likely $\lambda$ or similar, but keeping OCR 'I' or correcting to standard $\lambda$? The text says $I=\alpha^2(n+m)-n$. Standard is $\lambda = \alpha^2(n+\kappa)-n$. OCR uses $l$ for scaling parameter. I will keep $I$ as per OCR but note it might be a typo for $\lambda$. However, task says preserve information. I will format cleanly.) $m$ is the scale factor, and $l$ indicates the scaling parameter. If $x$ is a multidimensional variable, the scale factor is taken as $m=3-n$; $\alpha$ is a positive number, and $\beta$ is a non-negative weight coefficient.

$$ \hat{x}_k=\hat{x}_{k|k-1}+K_k[Z_k-\hat{Z}_{k|k-1}] \quad (29) $$

$$ P_k=P_{k|k-1}-K_kP_{Z_kZ_k}K_k^T \quad (30) $$

Repeat the above steps to achieve the calculation of the unscented Kalman filtering algorithm.

The proposed algorithm in this paper aims to obtain the optimal estimation of three-dimensional coordinates and angles in the perspective-tracking environment. Therefore, an unscented Kalman filtering perspective-tracking model combining feature triangles is proposed. An overall model is established for the characteristic triangle centroid composed of three characteristic points, namely, the center of the left and right pupil and the tip of the nose. Similar to linear Kalman filtering, UKF also includes three stages: state prediction, prediction of measured values, and state update. The main difference is that for the prediction stage, UT transform is used to approximate the probability distribution of head and eye movement states, making unscented Kalman filtering suitable for nonlinear doctor’s head-position-tracking systems.

In this paper, the following nonlinear equations are used to simulate visual angle motion, namely, the following:

$$ x = x_0 + vt + \frac{1}{2}at^2 \quad (31) $$

$$ x'_{k+1} = v_0 + A_k \sin(\omega_k t) \quad (32) $$

$$ a''_{k+1} = A_k \omega_k \cos(\omega_k t) \quad (33) $$

where the initial values of $x_0$ and $v_0$ are both 0, the acceleration $a$ conforms to a sinusoidal distribution function, and process noise $v_k$ is taken into account. $A_k = 0.08$ m/s and $\omega_k = \pi$ rad/s. In the eye movement state, Newton's motion formula is used, and the results are shown in the following state matrix:

$$
F = \begin{bmatrix}
1 & 0 & \Delta t & 0 \\
0 & 1 & 0 & \Delta t \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1
\end{bmatrix} \quad (34)
$$

$$
H = \begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0
\end{bmatrix} \quad (35)
$$

where $\Delta t$ is the interval from $k$ to $k+1$, and $F$ and $H$ are the state transition matrices.

Compared to the previously assumed perspective-tracking system with uniform motion, this section uses a nonlinear model that changes over time and uses a nine-dimensional vector space $[p_x, p_y, p_z, v_x, v_y, v_z, \omega_x, \omega_y, \omega_z]^T$ as the state variable of the process equation, where $[p_x, p_y, p_z]^T$ is the three-dimensional coordinate of the facial feature point or feature triangle, $[v_x, v_y, v_z]^T$ is the component of the linear velocity of the facial feature point on the X, Y, and Z coordinate axes, and $[\omega_x, \omega_y, \omega_z]^T$ is the component of the rotational angular velocity on the X, Y, and Z coordinate axes. This article focuses on the study of coordinates and rotation angles. Therefore, the state variable of the process equation of a UKF-based visual tracking nonlinear motion system is $[p_x, p_y, p_z, \omega_x, \omega_y, \omega_z]^T$, that is, $[X_W, Y_W, Z_W, \alpha, \Psi, \phi]^T$. The form of the state equation and measurement equation is expressed as follows:

$$ x_{k+1} = F x_k + v_k \quad (36) $$

$$ y_{k+1} = H x_k + n_k \quad (37) $$

where $x_k$ represents the state vector of the system at time $k$, which is the input vector at a known time $k$, that is, $x_k = [X_W, Y_W, Z_W, \alpha, \Psi, \phi]^T$. $y_k$ is the measurement vector, $v_k$ is the system process noise, and the measurement noise is represented by $n_k$, which are all zero-mean errors. $F$ represents the transfer matrix, and $H$ represents the observation matrix. As shown in Equations (36) and (37), $Q$ is the noise covariance matrix of the transfer process, and $R$ is the noise covariance matrix of the measurement process.

$$ Q = E\{ w_k w_k^T \} \quad (38) $$
