![](bbox=[0.26, 0.15, 0.84, 0.55])

Figure 7. An overview of the M-TCN network.

![](bbox=[0.15, 0.6, 0.85, 0.78])

Figure 8. An overview of convolutions.

# 3.5. Training Procedure

The training procedure can be described as Algorithm 1.

Meaning represented by each parameter. min_lr: minimum learning rate; initial_lr: initial learning rate; factor: factor by which the learning rate will be reduced; wait: number of epochs with no improvement after which learning rate will be reduced; new_lr: new learning rate; epoch: number of epochs to train the model; best_score: minimum RMSE.