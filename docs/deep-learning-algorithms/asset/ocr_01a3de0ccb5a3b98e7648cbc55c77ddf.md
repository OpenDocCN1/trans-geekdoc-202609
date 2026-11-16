Each grid cell in an image will predict B bounding boxes that encloses an object to predict the object localization and class. In addition, there is a confidence with each bounding box. Confidence score has nothing to do with the class of object. It just depicts how certain it is that the predicted box actually encloses the real object.

Confidence = Pr(object) × IOU, (3)

where Pr(object) represents the probability of the object of interest. If there is an object in the grid cell, the Pr(object) is 1; otherwise, it is 0.

Usually, loss function is in the form of the sum of squared errors as shown below [33]. It consists of three parts which are localization errors, confidence errors, and probabilities errors.

Loss = \sum_{i=0}^{S^2} \sum_{j=0}^{B} [(x_i - \hat{x}_i)^2 + (y_i - \hat{y}_i)^2 + (w_i - \hat{w}_i)^2 + (h_i - \hat{h}_i)^2] + \sum_{i=0}^{S^2} \sum_{j=0}^{B} (C_i - \hat{C}_i)^2 + \sum_{i=0}^{S^2} \sum_{C \in classes} (P_i(c) - P_i(\hat{c}))^2, (4)

where x_i, y_i are the ground truth coordinates of objects center; w_i, h_i are the width and height of the ground truth bounding box; \hat{x}_p \hat{y}_i are the predicted coordinates of the objects center; \hat{w}_p \hat{h}_i are the width and height of predicted bounding box. Above Figure 10 shows one set of output with confidence values from different classes.

![](bbox=[0.156, 0.562, 0.843, 0.762])

Figure 5. Fully connected neural net and locally connected neural net [32].