
图像噪声。该方法产生一种平滑模糊，类似于通过透明屏幕观看图像时看到的效果，而不是由失焦镜头生成的效果或标准照明下物体投射的阴影。高斯平滑也被用作计算机视觉方法中改善各种尺寸图像结构的预处理步骤。图5.10展示了基于高斯滤波器的去噪Python代码示例。

```python
import cv2
import glob

for filename in glob.glob('images/*.jpg'): # path to your images folder
    print(filename)
    img = cv2.imread(filename)
    img_resize = cv2.resize(img, (360, 360)) # image scaling
    new_image_gauss = cv2.GaussianBlur(img_resize, (360, 360), 0) # Add Gaussian Blur
    new_image = cv2.medianBlur(img_resize, figure_size) # Add Median Blur
# Outputs
cv2.imwrite(f'{filename}resize.jpg', img_resize)
cv2.imwrite(f'{filename}gaussian.jpg', new_image_gauss)
cv2.imwrite(f'{filename}median.jpg', new_image)
```

图5.10 基于高斯和中值滤波器的去噪Python代码。

### 5.3.5 去模糊

模糊大多发生在图像获取过程中。它是由源图像与相机之间缺乏对焦或运动引起的，在用于后续处理之前需要将其消除。去模糊策略包括Lucy-Richardson算法、逆滤波器、Wiener滤波器去模糊方法和神经网络方法。Wiener滤波器已被用作医疗应用中最强大和最流行的去模糊技术之一，该技术还可去除噪声。

## 5.4 分割

该程序旨在区分皮肤的患病部分和健康部分。应使用高度准确的分割算法来准确识别疾病区域。基于K-means聚类方法的基于颜色的分割方法是产生满意结果的最佳方法。聚类是一种根据图像像素与选定中心点之间的欧几里得距离将图像划分为K个簇组的方法。

该过程首先计算图像的直方图以获取中心点的数量作为K，该数量代表簇的数量。然后，如果像素值与中心点值之间的差异最小，则在空间或颜色空间中应用聚类。所需的簇数量（即K）使用K-means或Fuzzy C-means方法确定。比较这两种方法，Fuzzy C-means方法更灵活，因为它能识别与分区中许多簇交互的项目。由于图像中的项目往往具有相似的特性，聚类方法对其敏感。因此，将RGB图像转换为L*a*b颜色以更好地解释颜色的强度。然后，使用聚类方法对患病区域进行分割。

![](img/bffdb4a72252285ac92f0fad78a7f104_96_0.png)

图5.11 基于机器学习和深度学习的分类系统的一般比较[8]。

## 5.5 基于机器学习的识别

如图5.11（顶部）所示，输入图像在预处理并分割皮肤疾病区域后，会经过手工特征提取和基于机器学习的分类两个主要步骤。这两个步骤将在以下部分中详细说明。

### 5.5.1 特征提取

从图像中收集的信息称为特征。特征是从图片中提取的数值信息，人类难以理解和相互关联。从图片中检索到的特征维度通常远低于原始图像。

一般来说，根据应用程序，可以从图像中提取两种特征：局部特征和全局特征。图像检索、目标检测和分类都使用全局特征，而皮肤疾病诊断和识别则使用局部特征。结合全局特征和局部特征可以提高识别准确性，但也会增加计算成本。从大量文本数据中发现和提取图像特征的技术称为机器学习中的特征提取。

**GLCM特征。** 在统计纹理分析中，纹理特征源于图像中定义位置处相对强度组合的统计分布。统计特征根据每个组合中的强度点数量分为一阶、二阶和高阶统计特征。GLCM方法是获取二阶统计纹理特征的一种技术。该方法已广泛应用于各种领域。三阶及高阶纹理考虑三个或多个像素之间的连接。这些在理论上是可以设想的，但由于计算所需时间和结果解释的困难，它们并未广泛使用。

GLCM的每一行和每一列对应图像中的灰度级数（G）数量。矩阵元素P（i，j |Δx，Δy）包括在特定距离（d）和特定角度（θ）下灰度级“i”和“j”变化的二阶统计概率值。该矩阵元素是两个像素，

```python
import matplotlib.pyplot as plt
import cv2
from skimage.feature import graycomatrix, graycoprops

# segmented images
image = cv2.imread(filename)
PATCH_SIZE = 21
# select some patches from disease areas of the image
disease_locations = [(280, 454), (342, 223), (444, 192), (455, 455)]
disease_patches = []
for loc in disease_locations:
    # disease_patches.append(image[loc[0]:loc[0] + PATCH_SIZE, loc[1]:loc[1] + PATCH_SIZE])
    # select some patches from affected areas of the image
    aff_locations = [(38, 34), (139, 28), (37, 437), (145, 379)]
    aff_patches = []
    for loc in aff_locations:
        aff_patches.append(image[loc[0]:loc[0] + PATCH_SIZE, loc[1]:loc[1] + PATCH_SIZE])
# compute some GLCM properties each patch
xs = []
ys = []
for patch in (disease_patches + aff_patches):
    glcm = graycomatrix(patch, distances=[5], angles=[0], levels=256,
                        symmetric=True, normed=True)
    xs.append(graycoprops(glcm, 'dissimilarity')[0, 0])
    ys.append(graycoprops(glcm, 'correlation')[0, 0])
```

图5.12 GLCM特征提取Python代码。

按像素距离（Δx，Δy）分隔，在特定邻域中出现，一个具有强度“i”，另一个没有，在该邻域中。

使用大量的强度级别G需要存储大量临时数据，即为每个(Δx，Δy)或（d，θ）组合存储一个G×G矩阵。由于其维度很高，GLCM对其计算所依据的纹理样本数量非常敏感。图5.12展示了一个GLCM特征提取的*Python*代码示例。

**HOG。** 从图像数据中提取特征时，方向梯度直方图（HOG）常被用作特征提取。它通常用于计算机视觉应用，例如皮肤疾病检测和识别。

即使没有相关梯度或边缘坐标的确切信息，局部强度梯度或边缘方向的分布也常常能相当有效地表示局部项目的外观和结构。这一断言导致了HOG方法的定义，该方法已广泛用于人体识别，并在尺度不变特征变换[18]中使用了其成熟版本。特征表示基于对称为“单元”的微小空间区域内像素的梯度方向进行累积，随后构建一个1D直方图，其串联提供将用于未来目的的特征向量。令*L*为描述所考虑图像的强度（灰度）函数。图像被分割为大小为N×N像素的单元，每个像素的梯度\(\theta_{x,y}\)方向（图5.13a）通过以下方程确定（图5.13b,c）：

```
\(\theta_{x,y} = \tan^{-1} \frac{L(x, y + 1) - L(x, y - 1)}{L(x + 1, y) - L(x - 1, y)}\) (5.3)
```

随后，属于同一单元*j*的方向\(\theta_{j,i}\)，i = 1...N<sub>2</sub>，被量化并累积到一个M-bin直方图中（图5.13d,e）。最后，所有
