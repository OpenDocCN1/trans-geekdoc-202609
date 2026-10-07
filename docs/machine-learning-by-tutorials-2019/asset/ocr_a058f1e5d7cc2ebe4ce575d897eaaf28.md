# Machine Learning

# Chapter 10: YOLO & Semantic Segmentation

![](bbox=[0.161, 0.103, 0.836, 0.273])

Viewing the grounding-truth boxes on the images

Now that the data is in order, you're ready to start training the model.

# Training the model

It takes just a single line of code to create

```
model = tc.object_detector.create(train_data, feature="image",nannotations="annotations")
```

If this is your first time training this model, Turi Create will first download
t pre-trained models for the Darknet feature extractor. and then it starts training:

Setting "batch_size" to 32
Using GPU to create model (GeForce GTX 1080 Ti)
Setting "max_iterations" to 13000
| Iteration | Loss | Elapsed Time |
|---|---|---|
| 1 | 11.276 | 12.7 |
| 36 | 10.892 | 22.8 |
| 71 | 10.506 | 32.8 |
| 107 | 10.517 | 43.1 |
| ... | | |
| 12999 | 2.186 | 3755.5 |

Needless to say, a GPU for training this model is a must. The trained
on Linux with an NVIDIA GPU, but Turi Create can also use your Mac's AMD GPU 1080 Ti, if
took over an hour to train this model. Training on the CPU takes — at
eight seconds per iteration, doing 13,000 iterations would need about 29 hours.

If you don't have 29 hours of patience, don't worry! We included the trained model
in this chapter's materials that you will use in the next section.

raywender.com

349