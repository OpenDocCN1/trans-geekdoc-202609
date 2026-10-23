| Layer | Output shape | Params | Trainable |
|---|---|---:|---|
| ResizeToOrig | 16 x 96 x 224 x 224 | 0 | False |
| MergeLayer | 16 x 99 x 224 x 224 | 0 | False |
| Conv2d | 16 x 99 x 224 x 224 | 88,308 | True |
| ReLU | 16 x 99 x 224 x 224 | 0 | False |
| Conv2d | 16 x 99 x 224 x 224 | 88,308 | True |
| Sequential | 16 x 99 x 224 x 224 | 0 | False |
| ReLU | 16 x 99 x 224 x 224 | 0 | False |
| AdaptiveAvgPool2d | 16 x 99 x 1 x 1 | 0 | False |
| AdaptiveMaxPool2d | 16 x 99 x 1 x 1 | 0 | False |
| Flatten | 16 x 198 | 0 | False |
| BatchNorm1d | 16 x 198 | 396 | True |
| Dropout | 16 x 198 | 0 | False |
| Linear | 16 x 512 | 101,376 | True |
| ReLU | 16 x 512 | 0 | False |
| BatchNorm1d | 16 x 512 | 1,024 | True |
| Dropout | 16 x 512 | 0 | False |
| Linear | 16 x 18 | 9,216 | True |

Total params: 41,517,300