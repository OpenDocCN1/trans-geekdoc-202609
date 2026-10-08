# Generative Models

The loss function takes both style and content layers, as shown here:

```
loss = sum(style_loss(11[0], 12[0])*w
for 11,12,w in zip(style_layers, style_targs, style_wgts)
loss += metrics.mse(content_layer, content_targ)/10
grads = K.gradients(loss, model.input)ansfer_fn = K.function(model.Input, [loss]+grads)
evaluator = Evaluator(transfer_fn, shp)
```

We will run the solver for 10 iterations as before, using the following code:

```
iterations=10
x = rand_img(shp)
x = solve_image(evaluator, iterations, x)
```

The loss values should be printed as shown here:

```
Current loss value: 2557.953125
Current loss value: 732.533603071
Current loss value: 488.321166992
Current loss value: 385.8271789955
Current loss value: 330.915924072
Current loss value: 293.2381896997
Current loss value: 262.066864014
Current loss value: 239.341857911
Current loss value: 218.086700439
Current loss value: 203.045217991
```

These results are remarkable. Each one of them does a fantastic job of recreating the original image in the style of the artist. The generated image will look like the following:

![](bbox=[0.313, 0.633, 0.663, 0.853])