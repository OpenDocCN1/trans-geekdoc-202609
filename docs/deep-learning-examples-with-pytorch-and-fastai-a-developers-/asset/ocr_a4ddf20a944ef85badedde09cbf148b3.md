![](bbox=[0.194, 0.101, 0.71, 0.4])

```
learner.fit_one_cycle(5, slice(1e-2))
```

| epoch | train_loss | valid_loss | accuracy | multi | time |
|---:|---:|---:|---:|---:|---:|
| 0 | 0.550500 | 1.460057 | 0.668530 |  | 00:36 |
| 1 | 0.338241 | 0.258508 | 0.919412 |  | 00:34 |
| 2 | 0.309970 | 0.230138 | 0.914118 |  | 00:34 |
| 3 | 0.279830 | 0.210159 | 0.915882 |  | 00:34 |
| 4 | 0.254539 | 0.204521 | 0.923529 |  | 00:34 |

```
learner.show_results()
learner.save('13-planet-satellite-stage1')
```

We see that we can also use our custom UNET-model for building a multi-label classifier that really works. Great.

# # Chapter 16
# Object Detection

Object detection means we train a neural net to find different objects on a scene and draw bounding boxes around them.