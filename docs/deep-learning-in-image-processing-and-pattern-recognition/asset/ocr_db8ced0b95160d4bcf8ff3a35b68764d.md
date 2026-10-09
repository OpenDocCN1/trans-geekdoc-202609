various inputs. The existing CA channel attention mechanism divides the input feature map into horizontal and vertical parts and calculates the corresponding weights, respectively. However, this method cannot balance the global information and leads to the neglect of important spatial information.

In order to overcome the limitations of the existing CA attention module, this paper makes the following improvements:

+   1.  Add the GMP pathway to the GAP pathway of the original CA attention mechanism. The input feature map contains many targets with different sizes, so it is a better choice to average the pool first and then maximize the pool. This is because average pooling can capture all the information in the feature map, smooth the image and reduce noise better. Then, the maximum pooling is carried out, which can emphasize the most prominent features of the target while retaining the size transformation and further extracting effective information about the target.
2.  Calculate the weight by processing the input feature map. Adaptive average pooling and full connection layer operation are performed on the input feature map to generate a two-dimensional Softmax vector, which is used to represent the mixed proportion of horizontal and vertical attention weights. This method can effectively balance the global and local information, as shown in Figure 6.

![](bbox=[0.08, 0.38, 0.47, 0.67])

![](bbox=[0.49, 0.38, 0.88, 0.67])

**Figure 6.** CA attention and improved CA attention: (a) CA attention; (b) improved CA attention.

# 3.4. Loss Function

The loss function in the YOLOv7 network model is shown in Formula (1):

$L_{object Loss} = L_{box Loss} + L_{conf Loss} + L_{class Loss}$ (1)

where $L_{loc Loss}$ represents positioning loss, $L_{conf Loss}$ represents confidence loss and $L_{class Loss}$ represents classification loss. The coordinate loss is calculated using CIoU [38]. In order to describe the aspect ratio of the real frame and the predicted frame, when the aspect ratio is the same, the penalty item value is 0, which means that the difference in the aspect ratio is calculated as the penalty item, but it cannot represent the real difference between the length and width. Different from the CIoU loss function, the SIoU [39] loss function calculates the relationship of length and width of the real box and the prediction box separately, rather than calculating the difference of the aspect ratio, avoiding the loss of penalty terms when