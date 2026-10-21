target under appearance changes. The two predictions can be combined in various ways, but already the adaptively weighted sum

\hat{y}_\beta(p) = \beta_d \hat{y}_d(p) + \beta_s \hat{y}_s(p) \quad (9.57)

results in a significant improvement over the ECO tracker. In each time step, the adaptive weights are computed by solving the quadratic programming problem

\min_{\xi,\beta} \quad -\xi + \mu(\beta_d^2 + \beta_s^2) \quad (9.58)
s.t. \quad \beta_d + \beta_s = 1, \quad \beta_d \ge 0, \quad \beta_s \ge 0 \quad (9.59)
\hat{y}_\beta(p^*) - \xi \Delta(p^* - p) \ge \hat{y}_\beta(p), \quad \forall p, \quad (9.60)

where p* is a candidate target state (e.g. position) that is sampled from local maxima in \hat{y}_d and \hat{y}_s, \mu is a regularization parameter, and \Delta(p) = 1 - exp(-4|p|^2/s) with s being the target size.

# 9.4.3 End-to-end learning DCFs

The approaches described in the previous section introduce feature adaptation in DCF-trackers with a deep backbone. The backbone is trained offline on image classification data, the tracker is trained online using the current sequence, and the adaptation procedure is an engineered optimization problem. If we want to aim at a learning approach to connect the backbone with the tracker instead, we need to make use of tracking-specific training data. The main difference between adaptation and learning is the data used for the optimization: In contrast to adaptation, learning attempts to generalize from training data to the test data during inference.

The key problem addressed by the adaptive combination of score maps in (9.57) is to generate uni-modal score functions with a maximum centered inside the bounding box. To combine the score functions from shallow and deep features is a well-working heuristic for this purpose, but a machine learning approach would directly address the objective itself. Thus the task is to learn, using the tracking training data, a predictor for the accuracy measure, the Jaccard index. Instead of picking all local maxima and optimizing the weights, the Jaccard index prediction allows to pick the candidate bounding box with the largest overlap.

This idea of overlap maximization is used in the ATOM-tracker (Danelljan et al., 2019b), which combines an online learned classifier (similar to a DCF) with a Jaccard index regressor that is trained on annotated tracking data, see Fig. 9.5. Obviously, the regressor network has to take into account the specific target given in the initial (reference) frame. This is achieved by modulating the coefficient vector of the current frame with the corresponding vector from the reference frame before feeding it into the predictor.

The two branches, for the reference frame and current frame, are very similar in structure. The main difference is that the test branch for the current frame does not have access to a bounding box, but uses the initial estimate from the DCF-like classifier instead. The whole regressor is trained end-to-end, where the classifier is not trained using the back-propagated loss, but using the MOSSE criterion for the target score function. Thus the classifier acts like