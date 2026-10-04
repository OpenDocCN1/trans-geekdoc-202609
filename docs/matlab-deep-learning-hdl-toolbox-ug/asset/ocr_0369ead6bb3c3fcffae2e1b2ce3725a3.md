# Combination Layers

| Layer | Layer Type (HW) or Software(SW) | Layer Output Format | Description and Limitations | INT8 Compatible |
| --- | --- | --- | --- | --- |
| additionLayer | HW | Inherit from input. | An addition layer adds inputs from multiple network layers element-wise. These limitations apply when generating code for a network using this layer: * The maximum number of inputs to the addition layer is two when the input data type is int8. * Both input layers must have the same output layer format. For example, both layers must have conv output format or fc output format. | Yes |