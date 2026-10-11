
#### 7.3.2 Intersection over union (IOU) and the loss function

The bounding boxes for each image are encoded by `7 × 7` grid cells. For the Chess dataset with 13 classes, there are `(13 + 5 × 2)` cubes for each grid cell. The last five cubes (from 18 to 22) of each grid cell in a model prediction are used for the bounding box of another predicted object. Each grid cell of the model's predictions could predict two bounding boxes. However, we only use one bounding box which had a higher IOU value with a true bounding box in the same grid cell for calculations of loss function values. We have to recap IOU for image classification in chapter [2](#Chapter_2.xhtml#bk978-0-7503-6244-3ch2).

Suppose we have two pieces of paper, and they have the same size: `10 × 10 cm²`. If the paper on top covers 1/4 the area of the other paper, the intersection area of the two pieces of paper is `25 cm²`. Then we can calculate the IOU of the two pieces of paper: `IOU = 25/(100 + 100 − 25) = 1/7`. In the case when they completely overlap each other, the IOU value is one. Computers do the job in a different way. Using the code on line 17 of Cell 04, we get a batch of transformed images and their bounding boxes encoded in grid cells for a batch of samples in a train dataloader. The batch of bounding boxes are our targets. Taking the batch of transformed images into the `ResNet18` model on line 15 of Cell 05, we can obtain the model's output `y_hat` with a shape of `N × 1127`, where `N` is the batch size: `8`. The `y_hat` and the targets are then taken into a loss class defined in Cell 06 (line 07) in section 7.3.3. From the codes on line 10, 12 and 14 of Cell 06, we have a batch of true bounding boxes, two batches of predicted bounding boxes. The following IOU function defined in `Utility_fn(1/5)` will use each bounding box's center coordinates (`x_c`, `y_c`), width (`w`) and height (`h`) to calculate IOU values according to the following formulae

$$
\begin{matrix} 
{x_{1\min} = x_{1c} - \frac{1}{2}w_{1}} \\ 
{y_{1\min} = y_{1c} - \frac{1}{2}h_{1}} \\ 
{x_{1\max} = x_{1c} + \frac{1}{2}w_{1}} \\ 
{y_{1\max} = y_{1c} + \frac{1}{2}h_{1}} 
\end{matrix}
\begin{matrix} 
{x_{2\min} = x_{2c} - \frac{1}{2}w_{2}} \\ 
{y_{2\min} = y_{2c} - \frac{1}{2}h_{2}} \\ 
{x_{2\max} = x_{2c} + \frac{1}{2}w_{2}} \\ 
{y_{2\max} = y_{2c} + \frac{1}{2}h_{2}} 
\end{matrix}
$$

graphic style="width:15.9375em;" xlink:href="bk978-0-7503-6244-3ch7ueqn6.gif" position="float"/

$$
\begin{matrix} 
{x_{3\min} = {\max}\left( {x_{1\min},x_{2\min}} \right)} \\ 
{y_{3\min} = {\max}\left( {y_{1\min},y_{2\min}} \right)} \\ 
{x_{3\max} = {\min}\left( {x_{1\max},x_{2\max}} \right)} \\ 
{y_{3\max} = {\min}\left( {y_{1\max},y_{2\max}} \right)} 
\end{matrix},
\begin{matrix} 
{w_{3} = x_{3\max} - x_{3\min}} \\ 
{h_{3} = y_{3\max} - y_{3\min}} \\ 
{A_{12} = w_{1}h_{1} + w_{2}h_{2}} \\ 
{{IOU} = \frac{w_{3}h_{3}}{A_{12} - w_{3}h_{3}}} 
\end{matrix}
$$

graphic style="width:19.875em;" xlink:href="bk978-0-7503-6244-3ch7ueqn7.gif" position="float"/

The IOU function's inputs are the parameters of true bounding boxes and predicted bounding boxes. They have the same structure: `[…, x_c, y_c, w, h]`. The three dots indicate an image's index in a batch of dataloader, row index and column index of a grid cell on an image's `7 × 7` grid cells. The intersection area of two rectangles is still a rectangle. The coordinates of the top-left corner and the lower-bottom corner of the intersection could be obtained from the above formulae in which the variables’ subscript number 1, 2, and 3 are used for a predicted bounding box, a true bounding box and their intersections respectively. To use these formulae, we should have each bounding box's four parameters at the same scale. However, each bounding box's center coordinates are normalized by `64`, and the width and height of the box are normalized by `448`. A constant `self.S` on line 10, 12 and 14 in Cell 06 is used to set them to the same scalar. To calculate the IOU of two bounding boxes in different grid cells of an image, we also need to consider each grid cell's row index and column index to `y_c` and `x_c` respectively. Please pay attention to the data structure: `boxes_preds[…, 0:1]` in the IOU function. With this kind of tensor structure, we keep the original tensor's shape, so we can do calculations for 4D tensors without for-loops to save computation time. If the data structure is like this `boxes_preds[…, 0]`, we will lose the last dimension of the original tensor, and waste time in many for-loops. The average IOU values of all classes on all images of a dataset is the mAP metrics or index. Aladdin Persson has very helpful YouTube videos about [IOU](https://www.youtube.com/watch?v=XXYG5ZWtjj0…list=RDCMUCkzW5JSFwvKRjXABI-UTAkQ…index=3), [mAP](https://www.youtube.com/watch?v=FppOzcDvaDI…list=RDCMUCkzW5JSFwvKRjXABI-UTAkQ…index=2), Non Max Suppression ([NMS](https://www.youtube.com/watch?v=YDkjWEN8jNA…list=RDCMUCkzW5JSFwvKRjXABI-UTAkQ…index=4)) and [more](https://www.youtube.com/watch?v=n9_XyCGr-MI). Some of the following codes were inspired by his [GitHub](https://github.com/aladdinpersson/Machine-Learning-Collection/tree/a2ee9271b5280be6994660c7982d0f44c67c3b63/ML/Pytorch/object_detection/YOLO) codes with MIT license.

![](images/bk978-0-7503-6244-3ch7uf10a_pr.gif)

![](images/bk978-0-7503-6244-3ch7uf10b_pr.gif)

During model training, five parts of the following loss function (Redmon *et al* [2016](#Chapter_7.xhtml#bk978-0-7503-6244-3ch7bib6)) are optimized by the mean squared error algorithm. It is easy to see that the first part is for errors of center coordinates of the bounding boxes, and the second part is for errors of square roots of sizes (widths and heights) of bounding boxes. The square roots of sizes are used to balance errors between bigger and smaller bounding boxes. Because the size values of bounding boxes are less than `1.0` in YOLO encoding, the square root operations will amplify size errors nonlinearly, and errors from smaller sizes are amplified more. From the values of `(0.1)^(1/2)` and `(0.01)^(1/2)`, you would have an idea why not directly use the sizes of bounding boxes in the second part of the loss function. A bigger hyperparameter `λ[coord] = 5` is used to enhance the bounding boxes' coordinate errors and size errors.

$$
\begin{matrix} 
{L = \lambda_{coord}\sum\limits_{i = 0}^{48}{\sum\limits_{j = 0}^{1}{1_{ij}^{obj}\left\lbrack {\left( {x_{i} - {\widehat{x}}_{i}} \right)^{2} + \left( {y_{i} - {\widehat{y}}_{i}} \right)^{2}} \right\rbrack}} + \lambda_{coord}\sum\limits_{i = 0}^{48}{\sum\limits_{j = 0}^{1}{1_{ij}^{obj}\left\lbrack {\left( {\sqrt{w_{i}} - \sqrt{{\widehat{w}}_{i}}} \right)^{2} + \left( {\sqrt{h_{i}} - \sqrt{{\widehat{h}}_{i}}} \right)^{2}} \right\rbrack}}} \\ 
{+ \ \sum\limits_{i = 0}^{48}{\sum\limits_{j = 0}^{1}{1_{ij}^{obj}\left( {{\widehat{C}}_{i} - C_{i}} \right)^{2}}} + \lambda_{noobj}\sum\limits_{i = 0}^{48}{\sum\limits_{j = 0}^{1}{\left( {1 - 1_{ij}^{obj}} \right)\left( {{\widehat{C}}_{i} - C_{i}} \right)^{2}}} + \sum\limits_{i = 0}^{48}{1_{ij}^{obj}\sum\limits_{c \in {classes}}\left( {p_{i}\left( c \right) - {\widehat{p}}_{i}\left( c \right)} \right)^{2}}} 
\end{matrix}
$$

graphic style="width:33.8125em;" xlink:href="bk978-0-7503-6244-3ch7ueqn8.gif" position="float"/
