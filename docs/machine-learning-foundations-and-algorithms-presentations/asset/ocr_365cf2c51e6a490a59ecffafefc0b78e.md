# # Problems with standard SGD

(1) Loss changes quickly in one direction and
slowly in another (poor conditioning)

+   - Very slow progress along shallow dimension,
jitter along steep direction

![](bbox=[0.569, 0.252, 0.931, 0.403])

(2) Loss function has local minima and plateaus

+   - Zero gradient, gradient descent gets stuck

(3) Loss function is noisy

+   - Due to minibatches...

![](bbox=[0.679, 0.723, 0.833, 0.97])