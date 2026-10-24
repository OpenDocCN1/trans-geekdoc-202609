![](bbox=[0.14, 0.11, 0.48, 0.25])

![](bbox=[0.53, 0.11, 0.79, 0.25])

![](bbox=[0.14, 0.25, 0.48, 0.39])

![](bbox=[0.53, 0.25, 0.82, 0.39])

**FIGURE 10.16**
An illustration of greedy supervised pretraining. The bias values are not shown in the figure. The learned weights to the output unit (except the last iteration) are ignored, shown as dashed lines. The learned weights for the hidden layer from the previous iterations are fixed (shown as red (gray in print version), bold lines) to pretrain the weights and bias values of the newly added hidden layer at each iteration. At each iteration, we simply run backpropagation on a two-layer feed-forward network (shown as a shadow box in (b)—(d)) to pretrain the parameters of the newly added hidden layer, with the output of the last hidden layer from the previous iteration as the input units.

algorithm to train this model, to find the model parameters for the three hidden units (U5, U6, and U7) in the second hidden layer and those for the output unit U10. Like before, we ignore the weights and bias values for the output unit U10 (shown as the dashed line in Fig. 10.16(c)). Then, in the third (final) iteration, we add another hidden layer, including units U8 and U9 from the third hidden layer of the original model. Again, we fix the model parameters for the hidden units we have pretrained so far (U3, U4, U5, U6, and U7) from the previous iterations (shown as red (gray in print version) bold lines in Fig. 10.16(d)), and we perform backpropagation algorithm to learn the weights for the two hidden units of the newly added layer (U8 and U9) and the output unit U10.

To summarize, greedy supervised training starts with a simple model with only one hidden layer. At each iteration, it incrementally adds one additional hidden layer, while keeping the model parameters of the hidden units learned from the previous iterations unchanged. It runs the backpropagation algorithm to find the model parameters of the newly added hidden units. It keeps doing this until all the hidden layers from the original model have been added. The model parameters from the last iteration are used as the initial model parameters of the original deep learning model. We call it a pretrained model. The method is greedy, since at each iteration, we always fix the model parameters of hidden units from the previous iterations unchanged. Since we always fix the model parameters of the hidden units from the previous iteration(s) unchanged, pretraining at each iteration is equivalent to training a two-layer neural