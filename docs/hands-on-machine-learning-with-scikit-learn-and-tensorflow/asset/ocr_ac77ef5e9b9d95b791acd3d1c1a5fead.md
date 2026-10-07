```
loc_output = keras.layers.Dense(4)(avg)
model = keras.models.Model(inputs=base_model.input,
outputs=[class_output, loc_output])
model.compile(loss=["sparse_categorical_crossentropy", "mse"],
              loss_weights=[0.8, 0.2], # depends on what you care most about
              optimizer=optimizer, metrics["accuracy"]
```

But now we have a problem: the flowers dataset does not have bounding boxes around the flowers. We need to add them themselves. This is one of the hardest and most costly part of a Machine Learning project: getting the labels. A good idea is to spend time looking for the right tools. To annotate images with bounding boxes, you may need to use an open source labeling tool like VGG Image Annotator, LabelImg, OpenLabeler or ImgLab, or perhaps a commercial tool like LabelBox or Supervise. You may also consider crowdsourcing platforms such as Amazon Mechanical Turk or CrowdFlow if you have a very large number of images to annotate. However, it is a lot of work to set up a crowdsourcing platform, prepare the form to be sent to the workers, to supervise them and ensure the quality of the bounding boxes is good, make sure it is worth the effort: if there are just a few thousand images to label, and you don't plan to do this, it may be better to do it yourself. Adiana Kovashka et al. wrote a [paper2](https://example.com/paper2) about crowdsourcing in Computer Vision, I recommend you check it out, if you do not plan to use crowdsourcing.

So let's suppose you obtained the bounding boxes for every image in the flowers dataset (for now we will assume there is a single bounding box per image), then you need to create a dataset whose items will be batches of preprocessed images along with their class labels and their bounding boxes. Each item should be a tuple of the form: (class_labels, bounding_boxes). Then you are ready to train your model!

The bounding boxes should be normalized so that the horizontal and vertical coordinates, as well the height and width range from 0 to 1. Also, it is common to predict the square root of the height and width rather than the height and width, a 10 pixel error for a bounding box will not be penalized as much as a 10 pixel error for a small bounding box.

![](bbox=[0.163, 0.623, 0.249, 0.703])

The MSE works fairly well as a cost function to train the model, but it is not a great metric to evaluate how well the model can predict bounding boxes. The most common metric for this is the Intersection over Union (IoU): it is the area of overlap between the predicted bounding box and the target bounding box, divided by

> 2 "Crowdsourcing in Computer Vision," A. Kovashka et al. (2016).

470 | Chapter 14: Deep Computer Vision Using Convolutional Neural Networks

WOW! eBook
www.wowebook.com