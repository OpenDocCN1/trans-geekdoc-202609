spatial resolution to generate pixel-wise predictions. The loss function for semantic segmentation is a sum over all pixels and classes, given as:

\( L = - \sum_{i=1}^N \sum_{c=1}^C y_{i,c} \log(p_{i,c}), \quad (412) \)

where \( y_{i,c} \) is the ground-truth binary label for pixel \( i \) and class \( c \), and \( p_{i,c} \) is the predicted probability. Advanced architectures also employ skip connections to preserve high-resolution spatial information, enabling sharper segmentation boundaries.

Depth estimation is essential for autonomous vehicles to understand the 3D structure of their surroundings. CNNs are used to predict depth maps from monocular images or stereo pairs. The depth estimation process is modeled as a regression problem, where the loss function is designed to minimize the difference between the predicted depth \( \hat{d}_i \) and the ground-truth depth \( d_i \). A commonly used loss function for this task is the scale-invariant loss:

\( L_{\text{scale-inv}} = \frac{1}{n} \sum_{i=1}^n \left( \log d_i - \log \hat{d}_i \right)^2 - \frac{1}{n^2} \left( \sum_{i=1}^n \left( \log d_i - \log \hat{d}_i \right) \right)^2 . \quad (413) \)

This loss ensures that the relative depth differences are minimized, which is critical for accurate 3D reconstruction. Lane detection, another critical application, uses CNNs to detect road lanes and boundaries. The task often involves predicting the lane markings as polynomial curves. CNNs process the input image to extract lane features, and post-processing involves fitting a curve, such as:

\( y = ax^2 + bx + c, \quad (414) \)

where \( a,b,c \) are the coefficients predicted by the network. The fitting process minimizes an error function, typically the sum of squared differences between the detected lane points and the curve:

\( E = \sum_{i=1}^N (y_i - (ax_i^2 + bx_i + c))^2 . \quad (415) \)

In autonomous vehicles, these CNN tasks are integrated into an end-to-end pipeline. The input data from cameras, LiDAR, and radar is first processed using CNNs to extract features relevant to the vehicle's perception. The outputs, including object detections, semantic maps, depth maps, and lane boundaries, are then passed to the planning module, which computes the vehicle's trajectory. For instance, detected objects provide information about obstacles, while lane boundaries guide path planning algorithms. The planning process involves solving optimization problems where the objective function incorporates constraints from the CNN outputs. For example, a trajectory optimization problem may minimize a cost function:

\( J = \int_0^T \left( w_1 \dot{x}^2 + w_2 \dot{y}^2 + w_3 c(t) \right) \, dt, \quad (416) \)

where \( \dot{x} \) and \( \dot{y} \) are the lateral and longitudinal velocities, and \( c(t) \) is a collision penalty based on object detections.

In conclusion, CNNs provide the computational framework for perception tasks in autonomous vehicles, enabling real-time interpretation of complex sensory data. By leveraging mathematical principles of convolution, loss optimization, and hierarchical feature extraction, CNNs transform raw sensor data into actionable insights, paving the way for safe and efficient autonomous navigation.