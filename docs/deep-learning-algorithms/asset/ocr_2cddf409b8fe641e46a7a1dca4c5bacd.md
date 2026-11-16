\( L_\theta = \sum_{j=1}^K I(y_i = j) \log f_\theta^j(x_i) \)

where K is the number of classes, and \( I(y_i = j) = 1 \) if \( y_i = j \) and equals to 0 otherwise.

To train the model, we use gradient descent on the loss function L<sub>0</sub>. This is described by the following process:

+   1) We start from a random parameter \(\theta\) that can be arbitrarily chosen.
+   
+   2) We compute the gradient of the loss function \(\nabla_\theta L_\theta\). Computation of this gradient is discussed in the next section.
+   
+   3) We update the parameters by \(\theta \leftarrow \theta - \alpha \nabla_\theta L_\theta\). This changes \(\theta\) in the direction that minimizes the loss L<sub>0</sub>. \(\alpha\) is the learning rate that controls the step size. The larger the step size, the faster \(\theta\) changes. However, step size that is too large may lead to instability or even divergence. Therefore, the learning rate \(\alpha\) is an important hyperparameter that is selected based on the specific problem.
+   
+   4) We repeat from Step 2 until \(\theta\) stops changing.

The above algorithm reduces L<sub>0</sub> during each iteration. The hope is that when L<sub>0</sub> is minimized, f<sub>0</sub>(x<sub>i</sub>) will be close to y<sub>i</sub>, that is, the function f<sub>0</sub> we selected can correctly predict the label yi given xi on the training set.

However, even if f<sub>0</sub> correctly predicts every example we provided, this does not mean that f<sub>0</sub> will classify correctly on new data. For example, f<sub>0</sub> may have only memorized the training dataset. Therefore we need additional examples (x<sub>j</sub>, r<sub>j</sub>), j = 1, ..., M that the learner has not seen during training. The learner should only be able to classify these new examples correctly if it has learned the correct mapping between x and y. We can compute the testing accuracy by dividing the number of examples f<sub>0</sub> correctly classifies by the total number of examples. This is the final measurement of performance that we use to evaluate our learner.

# Deep Networks

In the previous section we left an open question: which class of functions \(\{f_\theta\}\) to select from during training. This section introduces an important function class of deep networks [19] [20] [21].

The key idea of deep learning is to compose very simple functions \( g_{\theta_d^1}^1, g_{\theta_d^2}^2, \cdots g_{\theta_d^d}^d \) into a very complex function \( f_\theta(x) = g_{\theta_d}^d (g_{\theta_d^2}^2 (\cdots g_{\theta_d^1}^1 (g_{\theta_d}(x)))) \). Each function