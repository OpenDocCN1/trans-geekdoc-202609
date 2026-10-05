# 266 CHAPTER 9 NEURAL NETWORK INTERPRETATION

is the CAV $v_c^C$. In practice, we can use a SVM or a logistic regression model as the binary classifier. Lastly, given an input $x$, we can measure its “conceptual sensitivity” by calculating the directional derivative of the prediction in the direction of the CAV:

$$S_{C,k,l}(x) = \nabla h_{l,k}(f_l(x)) \cdot v_c^C$$

where $f_l$ maps the input $x$ to the activation vector of layer $l$ and $h_{l,k}$ maps the activation to the log output of class $k$.

Mathematically, the sign of $S_{C,k,l}(x)$ only depends on the angle between the gradient of $h_{l,k}(f_l(x))$ and $v_c^C$. If the angle is greater than 90 degrees, $S_{C,k,l}(x)$ will be positive, and if the angle is less than 90 degrees, $S_{C,k,l}(x)$ will be negative. Since the gradient $\nabla h_{l,k}$ points to the direction that maximizes the output the rapidly, conceptual sensitivity $S_{C,k,l}$ intuitively, indicates whether $v_c^C$ points to to the similar direction that maximizes $h_{l,k}$. Thus, $S_{C,k,l}(x) > 0$ can be interpreted as concept C encouraging the model to classify $x$ into class k.

# 9.3.2 Testing with CAVs (TCAV)

In the last paragraph, we have learned how to calculate the conceptual sensitivity of a single data point. However, our goal is to provide a global explanation that indicates an overall conceptual sensitivity of an entire class. A straightforward approach by TCAV is to calculate the ratio of inputs with positive conceptual sensitivities to the number of inputs for a class:

$TCAV_{C,k,l} = \frac{|x \in X_k : S_{C,k,l}(x) > 0|}{|X_k|}$

Going back to our example, we are interested in how the concept of “striped” influences the model while classifying as “zebra”. We collect data that are labeled as “zebra” and calculate conceptual sensitivity for each input. Then the TCAV score of “striped” is the number of “zebra” images that have positive conceptual sensitivities divided by the total number of “zebra” images. In other words, a TCAV with $C ==striped$ and $k ==zebra$ equal to 0.8 indicates that 80% of predictions for “zebra” class are positively influenced by the concept of “striped”.

This looks great, but how do we know TCAV score is meaningful? After all, a CAV is trained by user-selected and random datasets. If datasets used to train the CAV are bad, the explanation can be misleading and useless. And thus, we perform a simple statistical significance test to help TCAV become more reliable. That is, instead of training only one CAV, we train multiple CAVs using random datasets while keeping the concept stable. A meaningful concept should generate CAVs with consistent TCAV scores. More detailed test procedure is shown in the following:

+   1. Collect $N$ random datasets, where it is recommended that $N$ is at least 10.