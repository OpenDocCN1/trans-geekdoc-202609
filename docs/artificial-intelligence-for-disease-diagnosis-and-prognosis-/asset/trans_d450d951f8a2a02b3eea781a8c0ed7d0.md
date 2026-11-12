

| 数据集 | 图像数量 | 图像类型 | 疾病类型 |
|---|---|---|---|
| PH2 | 200 | 皮肤镜 | 常见痣、黑色素瘤、不典型痣 |
| ISIC | 超过 20000 | 皮肤镜和临床 | 黑色素瘤、脂溢性角化症、良性痣 |
| HAM10000 | 10015 | 皮肤镜 | 色素性病变 |
| Dermnet | 23000 | 皮肤镜、临床和病理 | 23 个类别 |
| Dermofit 图像库 | 1300 | 临床 | 10 个类别 |
| Hallym | 152 | 临床 | 基底细胞癌 |
| AtlasDerm | 11057 | 临床 | 几乎所有类型 |
| Danderm | 超过 3000 | 临床 | 常见皮肤病 |
| Derm101 | 数千 | 临床 | 几乎所有类型 |
| 7 点标准评估数据集 | 超过 2000 | 皮肤镜和临床 | 黑色素瘤和非黑色素瘤 |
| SD-198 | 6584 | 临床 | 198 个类别 |
| DermIS | 数千 | 临床 | 几乎所有类型 |
| MoleMap | 102451 | 皮肤镜和临床 | 22 个良性类别和 3 个癌性类别 |
| Asan 数据集 | 17125 | 临床 | 针对亚洲人的 12 个类别 |
| 痤疮 | 3000 | 临床 | 7 类痤疮类型 |
| ACNE04 | 1457 | 临床 | 4 类痤疮分级 |

图 5.5 用于皮肤病诊断、分类和严重程度分级的部分公开可用数据集。

![](img/bffdb4a72252285ac92f0fad78a7f104_91_0.png)

图 5.6 皮肤病识别和分类系统领域中常用的预处理技术。

## 5.3 预处理

输入图像的质量对整个系统的性能有显著影响。因此，应用预处理技术来提高图像质量和清晰度是设计皮肤病识别和分类系统的重要步骤。该领域的一些常见预处理技术在图 5.6 中有所展示，并将在以下各节中详细说明。

### 5.3.1 图像大小调整和归一化

由于训练基于机器学习和深度学习系统的输入图像需要具有相同的尺寸，预处理的第一步是应用

```python
import cv2
import glob

for filename in glob.glob('images/*.jpg'): # path to your images folder
    print(filename)
    img=cv2.imread(filename)
    img_resize=cv2.resize(img, (360,360))
    cv2.imwrite(f'{filename}resized.jpg', img_resize)
```

图 5.7 调整图像大小的 Python 代码。

调整大小。然而，直接将图像调整为所需尺寸可能会导致图像畸变和信息丢失。因此，通常有用的解决办法是沿着图像的最短边以统一比例调整图像大小（需要保持宽高比）。图 5.7 展示了一个示例 Python 代码，其中 OpenCV 库作为 cv2 使用。此外，图像的强度通常会被归一化。在图像输入系统之前，通过从强度中减去均值然后除以标准差，对整个图像执行此操作。这种基于减去统一值的归一化方法可能无法有效地归一化图像，因为数据集中皮肤病图像存在较大的光照条件、肤色和视角变化，这会导致系统性能下降。[41] 通过基于从每张单独图像中获得的通道平均强度值进行归一化来解决了这个问题。由于皮肤病图像可能包含一些其他额外内容（如头发），可以使用阈值处理、形态学和深度学习技术将其移除，以进行更准确的分析。

### 5.3.2 色彩空间转换

色彩空间转换是指通过将图片从一个色彩空间转换到另一个色彩空间，将颜色的描述从一种图形基础转换到另一种图形基础，以使转换后的图片尽可能接近原图。如前所述，皮肤病图像通常使用数码相机或皮肤镜拍摄。将 RGB（红、绿、蓝）图像转换为标量图像是很常见的，因为处理标量值（单通道）更容易、更快、更方便，甚至更准确。例如，病变通常在蓝色通道中更明显，因此通常只保留蓝色通道，执行亮度变换并保留它。皮肤病变出现各种色调；但是，绝对颜色对图像分割没有帮助。病变内部或周围皮肤（尤其是病变边缘）的颜色变化，通常用于进行初步评估。因此，将 RGB 色彩坐标图像转换为其他色彩空间相对流行且有用。

**RGB 转灰度。** 基于红色（$R$）、绿色（$G$）和蓝色（$B$）三个通道的 RGB 图像包含额外信息，这些信息在处理中大多是多余的。这会导致更高的复杂性和存储空间，而性能可能仅略有提高。因此，将 RGB 图像转换为灰度图像是图像处理和

```python
import cv2
import glob
for filename in glob.glob('images/*.jpg'): # path to your images folder
    print(filename)
    input=cv2.imread(filename)

lab = cv2.cvtColor(input,cv2.COLOR_BGR2LAB) # lab color space conversion
cv2.imshow("l*a*b*",lab)

L,A,B=cv2.split(lab) # split of lab color conversion

cv2.imwrite('ael.jpg',L) # split of L
cv2.imwrite('aea.jpg',A) # split of A
cv2.imwrite('aeb.jpg',B) # split of B
cv2.imwrite("aelab.jpg",lab) # lab (together)

cv2.imshow("L_Channel",L) # For L Channel
cv2.imshow("A_Channel",A) # For A Channel (Here's what You need)
cv2.imshow("B_Channel",B) # For B Channel

cv2.waitKey(0)
cv2.destroyAllWindows()
```

图 5.8 从 RGB 到 L*a*b* 色彩空间转换的 Python 代码。

计算机视觉领域。RGB 图像通常根据两种方法转换为灰度图像：平均法和加权法。基于平均法的灰度值计算如下：

Grayscale = (R + G + B)/3

由此得到的值归一化为 0 到 255 之间。虽然这种方法简单，但不如人类视觉感知所期望的准确。人眼对 R、G、B 所有颜色的反应并不相同。这意味着我们的眼球对绿光、红光和蓝光的敏感度不同（从高到低依次排列）。因此，在计算灰度值时，这些光线需要有不同的权重，从而导致基于以下公式的加权方法：

Grayscale = 0.299R + 0.587G + 0.114B

RGB 转 L*a*b*。为了更好地可视化皮肤病区域，许多方法都采用了 RGB 到 L*a*b* 色彩空间转换。在 L*a*b* 色彩空间中，L*、a* 和 b* 分别代表亮度和色对立维度。L*a*b* 色彩空间的开发旨在模仿人类视觉，而不是 RGB 和 CMYK 色彩模型。通过修改和优化 a 和 b 分量中的输出曲线，L 分量与人类对亮度的感知非常接近，从而可用于改变亮度对比度或进行精确的色彩平衡调整。另一方面，RGB 或 CMYK 空间不反映人类视觉体验，而是显示物理设备的输出，只能通过编辑应用程序和使用合适的混合模式来修改。可以通过将图像的色彩空间从 RGB 更改为 L*a*b* 来克服这个问题。这种转换通过提供输入图像和皮肤病区域的更好表示来提高最终分类准确率。图 5.8 展示了一个用于 RGB 到 L*a*b* 色彩空间转换的示例 Python 代码。

### 5.3.3 对比度增强

当图像的强度值范围较小时，通常需要对比度增强。这发生在图像太暗或太亮的情况下。对比度是指暗区和亮区之间的差异。增加对比度包括使暗物体更暗、亮物体更亮。降低对比度则相反，使亮度和黑度的极端值更接近。增强意味着整体图像质量的提高。

**线性对比度增强。** 这种形式的对比度增强使用对比度拉伸方法。通过重新映射或扩展灰度级值，使直方图在整个范围内拉伸，从而改善图像的对比度。

**非线性对比度增强。** 非线性方法广泛用于基于医学图像的应用中。这种对比度增强主要涉及直方图均衡化和增加对比度的算法方法。这类方法中最显著的缺陷是由于输出图像中的数字多于输入图像中的每个值，导致物体精确亮度的丢失。图 5.9 展示了一个基于直方图均衡化的非线性对比度增强的示例 Python 代码。

```python
#Histogram Equalization Contrast Enhancement
def ehan(img):
    if(len(img.shape)==2): #gray
        outImg = ex.equalize_hist(img[...,:])*255
    elif(len(img.shape)==3): #RGB
        outImg = np.zeros((img.shape[0],img.shape[1],3))
        for channel in range(img.shape[2]):
            outImg[..., :, channel] = ex.equalize_hist(img[..., :, channel])*255
    outImg[outImg>255] = 255
    outImg[outImg<0] = 0
    return img.astype(np.uint8)

def main():
    img_name = sys.argv[1]
    image = Imageio.imread(img_name)
    result = ehan(img)
    plt.imshow(result)
    plt.show()

if __name__ == '__main__':
    main()
```

图 5.9 基于直方图均衡化的非线性对比度增强的 Python 代码。

### 5.3.4 去噪

图像去噪可以有多种方法。空间滤波和变换域滤波是两种最基本的图像处理技术。在空间滤波中，邻域和预定操作根据以该像素为中心的平方邻域内的像素值来调整每个像素的灰度值（例如，均值滤波器、中值滤波器、维纳滤波器、李滤波、各向异性扩散滤波器、总变分滤波器等）。

**高斯滤波器。** 基于高斯函数的模糊方法称为高斯模糊或高斯平滑，常被用于最小化

