| Layer (type) | Output Shape | Param # |
| --- | --- | --- |
| input (InputLayer) | [(None, 15, 37)] | 0 |
| dense (Dense) | (None, 15, 128) | 4736 |
| tf.nn.softmax (TFOpLambda) | (None, 15, 128) | 0 |
| dropout (Dropout) | (None, 15, 128) | 0 |
| bidirectional (Bidirectionall) | (None, 256) | 263168 |
| dropout_1 (Dropout) | (None, 256) | 0 |
| dense_1 (Dense) | (None, 128) | 32896 |
| dense_2 (Dense) | (None, 15) | 1935 |

Total params: 302,735
Trainable params: 302,735
Non-trainable params: 0

Figure 17. A configuration of the teacher model training in the knowledge distillation process.

![](bbox=[0.185, 0.43, 0.391, 0.621])

Figure 18. An architecture of the student model training in the knowledge distillation process.

| Layer (type) | Output Shape | Param # |
| --- | --- | --- |
| input (InputLayer) | [(None, 15, 37)] | 0 |
| flatten (Flatten) | (None, 555) | 0 |
| dense (Dense) | (None, 256) | 142336 |
| dropout (Dropout) | (None, 256) | 0 |
| dense_1 (Dense) | (None, 15) | 3855 |

Total params: 146,191
Trainable params: 146,191
Non-trainable params: 0

Figure 19. A configuration of the student model training in the knowledge distillation process.