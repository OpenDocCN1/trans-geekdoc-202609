# 12.3.4 Self-supervised loss function

One distinctive property of features within the same event is that they are predictable given previous perceptual inputs and a stable event model. We rely on this property to detect event boundaries. Therefore, we can define a prediction error function that receives, as input, the model’s prediction $y'_t$, and the actual future sensory features $I'_t$ as targets. The resulting error, termed as the perceptual prediction error, is calculated as shown in Eq. (12.3).

$E_P(t) = \sum_{i=1}^{n} ||I'_t - y'_t||_{\ell_1}^2 \tag{12.3}$

The perceptual prediction error is reasonably indicative of the relevance of the recurrent model’s internal state to the actual event being observed. When the event changes by crossing an event boundary, the internal model becomes unusable, leading to incorrect predictions. The prediction quality increases after updating the internal model with a newer representation capable of predicting future features. Fig. 12.4 illustrates an instance of this effect. The minimization of the perceptual prediction error serves as the objective function for training the network.

# 12.3.5 Error gating

According to the Event Segmentation Theory, the perceptual features can become highly unpredictable at event boundaries since the working event model will need to be updated to process the new event. For example, in Fig. 12.4, we can see that the visual representation of the features learned by the encoder network for the activities take bowl and crack eggs are closer together than the features between the activities take bowl and spoon flour. At event boundaries, the diverging feature space becomes inexplicable by the recurrent internal model, causing a transient increase in the perceptual prediction error. We see that the perceptual prediction error (second plot from the bottom) matches well with the ground truth segmentation (second from the top) for the video “Make Pancake”. As illustrated, the error rates are higher at the event boundaries and lower within the “in-event” frames.

To model the prediction error and identify event boundaries, we can use a low pass filter to maintain a running average of the perceptual prediction error made over the last $n$ input time steps. An $n$ value of 5 is used here based on the average human perception response time ($\approx$ 200 ms) (Thorpe et al., 1996). We maintain a running average of the prediction error, called the prediction quality and given by

$P_q(t) = P_q(t-1) + \frac{1}{n}(E_P(t) - P_q(t-1)) \tag{12.4}$

where $P_q$ is the prediction quality and $E_P(t)$ is the prediction error from Eq. (12.3). A gating signal, $G(t)$, is triggered when the current prediction error exceeds the average prediction quality metric by at least 50%. Formally, we can define the gating function as

$G(t) = \begin{cases} 1, & \frac{E_P(t)}{P_q(t-1)} > \psi_e \\ 0, & \text{otherwise} \end{cases} \tag{12.5}$