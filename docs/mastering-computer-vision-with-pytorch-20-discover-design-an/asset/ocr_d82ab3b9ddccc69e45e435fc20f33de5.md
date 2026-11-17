```
results.show()
```

![](bbox=[0.18, 0.13, 0.82, 0.5])

Figure 9.6: Output of YOLO v5 model on sample image from PASCAL VOC 2012

The results.show() method conveniently displays the image with bounding boxes, class labels, and confidence scores.

# Training and Evaluation YOLOv5 on
the PASCAL VOC Dataset

Training YOLOv5 on a custom dataset like PASCAL VOC involves preparing your dataset in the appropriate format and configuring a training script. YOLOv5 expects the dataset to be in a specific directory structure and annotation format (YOLO format).

**Prepare your dataset:** Convert the PASCAL VOC annotations to YOLO format and organize your dataset directory as follows:

```
dataset/
```