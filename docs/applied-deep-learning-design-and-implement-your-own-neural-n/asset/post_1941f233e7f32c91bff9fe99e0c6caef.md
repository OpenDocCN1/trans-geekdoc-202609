
## Web resources

- A gentle introduction to object recognition with deep learning https://machinelearningmastery.com/object-recognition-with-deep-learning/.
- Deep learning in object detection and recognition https://www.springer.com/gp/book/9789811051517.
- What is computer vision and object detection? https://www.imageannotation.ai/blog/computer-vision-and-object-detection
- Object detection and face recognition algorithms https://medium.com/swlh/object-detection-face-recognition-algorithms-146fec385205

## Questions

- 1. Explain computer vision and its tasks.
- 2. Differentiate between image processing and computer vision.
- 3. What is image segmentation? Explain different types of image segmentation.
- 4. What are anchor boxes?
- 5. Explain the YOLO algorithm with an example.
- 6. Explain the RCNN algorithm with an example.
- 7. Explain the fast RCNN algorithm with an example.
- 8. Explain the mask RCNN algorithm with an example.
- 9. Differentiate between RCNN, Fast RCNN, and Faster RCNN.
- 10. What is RoI align?

## Multiple choice questions

- 1. Which permits people to identify people and detect objects reliably?
  - a. Vision
  - b. Hear
  - c. Speech
  - d. Perception
- 2. How many recognitions are there in computer vision?
  - a. 2
  - b. 3
  - c. 1
  - d. 4
- 3. What gives a framework to study object recognition?
  - a. Unsupervised Learning
  - b. Semi-Supervised learning
  - c. Supervised learning
  - d. None of the mentioned
- 4. YOLO stands for.
  - a. You Only Look Once.
  - b. Yours Look Only Once
  - c. Your Object Look One
  - d. None of the mentioned
- 5. RCNN stands for?
  - a. Region-based convolution neural network.
  - b. Rationalized convolution neural network.
  - c. Random CNN
  - d. None of the mentioned
- 6. In fast RCNN, we use a robust loss function as?
  - a. Cross Entropy.
  - b. MSE.
  - c. Smooth
  - d. None of the mentioned
- 7. Mask RCNN is used for?
  - a. Object Detection.
  - b. Image classification.
  - c. Image Segmentation.
  - d. None of the mentioned

## Answers

| 1 | a |
|---|---|
| 2 | b |
| 3 | c |
| 4 | a |
| 5 | a |
| 6 | c |
| 7 | c |

## Hands on session (object localization and detection)

- 1. Implement the YOLO algorithm for object detection.

```python
YOLO algorithm code:
import struct
import numpy as np
from keras.layers import Conv2D
from keras.layers import Input
from keras.layers import BatchNormalization
from keras.layers import LeakyReLU
from keras.layers import ZeroPadding2D
from keras.layers import UpSampling2D
from keras.layers.merge import add, concatenate
from keras.models import Model

def _conv_block1(inp1, convs1, skip=True):
    x = inp1
    count = 0
    for conv in convs1:
        if count == (len(convs1) - 2) and skip:
            skip_connection = x
        count += 1
        if conv['stride'] > 1: x = ZeroPadding2D(((1,0),(1,0)))(x)
        # peculiar padding as darknet prefer left and top
        x = Conv2D(conv['filter'],
                conv['kernel'],
                strides=conv['stride'],
                padding='valid' if conv['stride'] > 1 else 'same',
                name='conv_' + str(conv['layer_idx']),
                use_bias=False if conv['bnorm'] else True)(x)
        if conv['bnorm']: x = BatchNormalization(epsilon=0.001,
                name='bnorm_' + str(conv['layer_idx']))(x)
        if conv['leaky']: x = LeakyReLU(alpha=0.1, name='leaky_' +
                str(conv['layer_idx']))(x)
    return add([skip_connection, x]) if skip else x

def make_yolov3_model():
    input_image = Input(shape=(None, None, 3))
    # Layer 0 => 4
    x = _conv_block1(input_image, [{'filter': 32, 'kernel': 3,
            'stride': 1, 'bnorm': True, 'leaky': True, 'layer_idx': 0},
            {'filter': 64, 'kernel': 3, 'stride': 2,
            'bnorm': True, 'leaky': True, 'layer_idx': 1),
            {'filter': 32, 'kernel': 1, 'stride': 1, 'bnorm': True, 'leaky': True, 'layer_idx': 2},
            {'filter': 64, 'kernel': 3, 'stride': 1, 'bnorm': True, 'leaky': True, 'layer_idx': 3}])

    # Layer 5 => 8
    x = _conv_block1(x, [{'filter': 128, 'kernel': 3, 'stride': 2, 'bnorm': True, 'leaky': True, 'layer_idx': 5}),
    {'filter': 64, 'kernel': 1, 'stride': 1, 'bnorm': True, 'leaky': True, 'layer_idx': 6},
    {'filter': 128, 'kernel': 3, 'stride': 1, 'bnorm': True, 'leaky': True, 'layer_idx': 7}])

    # Layer 9 => 11
    x = _conv_block1(x, [{'filter': 64, 'kernel': 1, 'stride': 1, 'bnorm': True, 'leaky': True, 'layer_idx': 9},
    {'filter': 128, 'kernel': 3, 'stride': 1, 'bnorm': True, 'leaky': True, 'layer_idx': 10}])

    # Layer 12 => 15
    x = _conv_block1(x, [{'filter': 256, 'kernel': 3, 'stride': 2, 'bnorm': True, 'leaky': True, 'layer_idx': 12},
    {'filter': 128, 'kernel': 1, 'stride': 1, 'bnorm': True, 'leaky': True, 'layer_idx': 13},
    {'filter': 256, 'kernel': 3, 'stride': 1, 'bnorm': True, 'leaky': True, 'layer_idx': 14}])

    # Layer 16 => 36
    for i in range(7):
        x = _conv_block1(x, [{'filter': 128, 'kernel': 1, 'stride': 1, 'bnorm': True, 'leaky': True, 'layer_idx': 16+i*3},
        {'filter': 256, 'kernel': 3, 'stride': 1, 'bnorm': True, 'leaky': True, 'layer_idx': 17+i*3}])
    skip_36 = x

    # Layer 37 => 40
    x = _conv_block1(x, [{'filter': 512, 'kernel': 3, 'stride': 2, 'bnorm': True, 'leaky': True, 'layer_idx': 37},
    {'filter': 256, 'kernel': 1, 'stride': 1, 'bnorm': True, 'leaky': True, 'layer_idx': 38},
    {'filter': 512, 'kernel': 3, 'stride': 1, 'bnorm': True,
    'leaky': True, 'layer_idx': 39}])

    # Layer 41 => 61
    for i in range(7):
        x = _conv_block1(x, [{'filter': 256, 'kernel': 1, 'stride': 1, 'bnorm': True, 'leaky': True, 'layer_idx': 41+i*3},
        {'filter': 512, 'kernel': 3, 'stride': 1, 'bnorm': True,
        'leaky': True, 'layer_idx': 42+i*3}])
    skip_61 = x

    # Layer 62 => 65
    x = _conv_block1(x, [{'filter': 1024, 'kernel': 3, 'stride': 2,
        'bnorm': True, 'leaky': True, 'layer_idx': 62},
        {'filter': 512, 'kernel': 1, 'stride': 1, 'bnorm': True, 'leaky': True,
        'layer_idx': 63},
        {'filter': 1024, 'kernel': 3, 'stride': 1, 'bnorm': True,
        'leaky': True, 'layer_idx': 64}])

    # Layer 66 => 74
    for i in range(3):
        x = _conv_block1(x, [{'filter': 512, 'kernel': 1, 'stride': 1, 'bnorm': True, 'leaky': True, 'layer_idx': 66+i*3},
        {'filter': 1024, 'kernel': 3, 'stride': 1, 'bnorm': True,
        'leaky': True, 'layer_idx': 67+i*3}])

    # Layer 75 => 79
    x = _conv_block1(x, [{'filter': 512, 'kernel': 1, 'stride': 1, 'bnorm': True, 'leaky': True, 'layer_idx': 75},
        {'filter': 1024, 'kernel': 3, 'stride': 1, 'bnorm': True,
        'leaky': True, 'layer_idx': 76},
        {'filter': 512, 'kernel': 1, 'stride': 1, 'bnorm': True,
        'leaky': True, 'layer_idx': 77},
        {'filter': 1024, 'kernel': 3, 'stride': 1, 'bnorm': True,
        'leaky': True, 'layer_idx': 78},
        {'filter': 512, 'kernel': 1, 'stride': 1, 'bnorm': True,
        'leaky': True, 'layer_idx': 79}], skip=False)

    # Layer 80 => 82
    yolo_82 = _conv_block1(x, [{'filter': 1024, 'kernel': 3,
        'stride': 1, 'bnorm': True, 'leaky': True, 'layer_idx': 80},
        {'filter': 255, 'kernel': 1, 'stride': 1, 'bnorm': False,
        'leaky': False, 'layer_idx': 81}], skip=False)

    # Layer 83 => 86
    x = _conv_block1(x, [{'filter': 256, 'kernel': 1, 'stride': 1,
    'bnorm': True, 'leaky': True, 'layer_idx': 84}], skip=False)
    x = UpSampling2D(2)(x)
    x = concatenate([x, skip_61])

    # Layer 87 => 91
    x = _conv_block1(x, [{'filter': 256, 'kernel': 1, 'stride': 1,
    'bnorm': True, 'leaky': True, 'layer_idx': 87},
    {'filter': 512, 'kernel': 3, 'stride': 1, 'bnorm': True,
    'leaky': True, 'layer_idx': 88},
    {'filter': 256, 'kernel': 1, 'stride': 1, 'bnorm': True,
    'leaky': True, 'layer_idx': 89},
    {'filter': 512, 'kernel': 3, 'stride': 1, 'bnorm': True,
    'leaky': True, 'layer_idx': 90},
    {'filter': 256, 'kernel': 1, 'stride': 1, 'bnorm': True,
    'leaky': True, 'layer_idx': 91}], skip=False)

    # Layer 92 => 94
    yolo_94 = _conv_block1(x, [{'filter': 512, 'kernel': 3, 'stride':
    1, 'bnorm': True, 'leaky': True, 'layer_idx': 92},
    {'filter': 255, 'kernel': 1, 'stride': 1, 'bnorm': False,
    'leaky': False, 'layer_idx': 93}], skip=False)

    # Layer 95 => 98
    x = _conv_block1(x, [{'filter': 128, 'kernel': 1, 'stride': 1,
    'bnorm': True, 'leaky': True, 'layer_idx': 96}], skip=False)
    x = UpSampling2D(2)(x)
    x = concatenate([x, skip_36])

    # Layer 99 => 106
    yolo_106 = _conv_block1(x, [{'filter': 128, 'kernel': 1,
    'stride': 1, 'bnorm': True, 'leaky': True, 'layer_idx': 99},
    {'filter': 256, 'kernel': 3, 'stride': 1, 'bnorm': True,
    'leaky': True, 'layer_idx': 100},
    {'filter': 128, 'kernel': 1, 'stride': 1, 'bnorm': True,
    'leaky': True, 'layer_idx': 101},
    {'filter': 256, 'kernel': 3, 'stride': 1, 'bnorm': True,
    'leaky': True, 'layer_idx': 102},
    {'filter': 128, 'kernel': 1, 'stride': 1, 'bnorm': True,
    'leaky': True, 'layer_idx': 103},
    {'filter': 256, 'kernel': 3, 'stride': 1, 'bnorm': True,
    'leaky': True, 'layer_idx': 104}])
```
