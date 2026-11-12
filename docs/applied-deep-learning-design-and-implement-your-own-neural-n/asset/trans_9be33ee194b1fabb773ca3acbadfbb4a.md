

## Web 资源

- 基于深度学习的物体识别温和介绍 https://machinelearningmastery.com/object-recognition-with-deep-learning/.
- 物体检测与识别中的深度学习 https://www.springer.com/gp/book/9789811051517.
- 什么是计算机视觉和物体检测？ https://www.imageannotation.ai/blog/computer-vision-and-object-detection
- 物体检测和人脸识别算法 https://medium.com/swlh/object-detection-face-recognition-algorithms-146fec385205

## 问题

- 1. 解释计算机视觉及其任务。
- 2. 区分图像处理和计算机视觉。
- 3. 什么是图像分割？解释不同类型的图像分割。
- 4. 什么是锚框？
- 5. 用示例解释 YOLO 算法。
- 6. 用示例解释 RCNN 算法。
- 7. 用示例解释 Fast RCNN 算法。
- 8. 用示例解释 Mask RCNN 算法。
- 9. 区分 RCNN、Fast RCNN 和 Faster RCNN。
- 10. 什么是 RoI Align？

## 选择题

- 1. 哪项可使人们可靠地识别人并检测对象？
  - a. 视觉
  - b. 听觉
  - c. 语音
  - d. 感知
- 2. 计算机视觉中有多少种识别？
  - a. 2
  - b. 3
  - c. 1
  - d. 4
- 3. 什么为研究物体识别提供了框架？
  - a. 无监督学习
  - b. 半监督学习
  - c. 监督学习
  - d. 以上皆非
- 4. YOLO 代表。
  - a. You Only Look Once.
  - b. Yours Look Only Once
  - c. Your Object Look One
  - d. 以上皆非
- 5. RCNN 代表？
  - a. Region-based convolution neural network.
  - b. Rationalized convolution neural network.
  - c. Random CNN
  - d. 以上皆非
- 6. 在 Fast RCNN 中，我们使用一个强损失函数作为？
  - a. Cross Entropy.
  - b. MSE.
  - c. Smooth
  - d. 以上皆非
- 7. Mask RCNN 用于？
  - a. Object Detection.
  - b. Image classification.
  - c. Image Segmentation.
  - d. 以上皆非

## 答案

| 1 | a |
|---|---|
| 2 | b |
| 3 | c |
| 4 | a |
| 5 | a |
| 6 | c |
| 7 | c |

## 实操课程（目标定位和检测）

- 1. 为物体检测实现 YOLO 算法。

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
