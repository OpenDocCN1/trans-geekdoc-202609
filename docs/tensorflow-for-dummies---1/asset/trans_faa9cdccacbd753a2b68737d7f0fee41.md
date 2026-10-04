

当对图像进行滤波时，必须对原始图像中的每个像素计算这个点积。这项操作提出了一个重要问题：如果像素位于图像的边界上，如何找到围绕 `m[i,j]` 的像素？

![technicalstuff](images/technicalstuff.png)与其为每个像素计算点积，许多工程师通过将图像和滤波器转换为频域来进行卷积。这种过程称为 *快速卷积*，涉及对图像和滤波器的每一行和每一列计算快速傅里叶变换 (`FFT`)。

像其他优秀的机器学习文献作品一样，本书使用术语卷积来指代计算 2-D 点积矩阵的过程。但其技术术语是 *互相关*。卷积在计算点积之前会反转其中一个操作数，而这里介绍的算法并不反转任一操作数。

### Averaging Filter

理解图像滤波的一个好方法是举例说明。本节重点介绍 [Figure 8-1](#13_9788126592555-ch08.xhtml#c08-fig-0001) 中描绘的颗粒状图像。

![FIGURE 8-1: The image’s mottled appearance is the result of noise.](images/9788126592555-fg0801.png)

[FIGURE 8-1:](#13_9788126592555-ch08.xhtml#rc08-fig-0001) 图像的斑驳外观是噪声的结果。

从数学上讲，图像的噪声可以被视为相邻像素之间不需要的差异。你可以通过用其自身和周围像素的平均值替换每个像素来减少这种差异。你可以通过使用以下类似的滤波器对图像进行卷积来实现这一点：

![images](images/eq08004.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi mathvariant="normal">kernel</m:mi><m:mo>=</m:mo><m:mrow><m:mo>|</m:mo><m:mrow><m:mtable><m:mtr><m:mtd><m:mrow><m:mfrac><m:mn>1</m:mn><m:mn>9</m:mn></m:mfrac></m:mrow></m:mtd><m:mtd><m:mrow><m:mfrac><m:mn>1</m:mn><m:mn>9</m:mn></m:mfrac></m:mrow></m:mtd><m:mtd><m:mrow><m:mfrac><m:mn>1</m:mn><m:mn>9</m:mn></m:mfrac></m:mrow></m:mtd></m:mtr><m:mtr><m:mtd><m:mrow><m:mfrac><m:mn>1</m:mn><m:mn>9</m:mn></m:mfrac></m:mrow></m:mtd><m:mtd><m:mrow><m:mfrac><m:mn>1</m:mn><m:mn>9</m:mn></m:mfrac></m:mrow></m:mtd><m:mtd><m:mrow><m:mfrac><m:mn>1</m:mn><m:mn>9</m:mn></m:mfrac></m:mrow></m:mtd></m:mtr><m:mtr><m:mtd><m:mrow><m:mfrac><m:mn>1</m:mn><m:mn>9</m:mn></m:mfrac></m:mrow></m:mtd><m:mtd><m:mrow><m:mfrac><m:mn>1</m:mn><m:mn>9</m:mn></m:mfrac></m:mrow></m:mtd><m:mtd><m:mrow><m:mfrac><m:mn>1</m:mn><m:mn>9</m:mn></m:mfrac></m:mrow></m:mtd></m:mtr></m:mtable></m:mrow><m:mo>|</m:mo></m:mrow></m:mrow></m:math>

用第 i 行第 j 列的像素表示为 `m[ij]`，你可以通过以下方式计算 `m[ij]` 的滤波值：

![images](images/eq08005.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mtable columnalign="left"><m:mtr><m:mtd><m:msub><m:mi>m</m:mi><m:mrow><m:mi>i</m:mi><m:mo>,</m:mo><m:mi>j</m:mi></m:mrow></m:msub><m:mrow><m:mo>(</m:mo><m:mrow><m:mi>f</m:mi><m:mi>i</m:mi><m:mi>l</m:mi><m:mi>t</m:mi><m:mi>e</m:mi><m:mi>r</m:mi><m:mi>e</m:mi><m:mi>d</m:mi></m:mrow><m:mo>)</m:mo></m:mrow><m:mo>=</m:mo><m:mfrac><m:mn>1</m:mn><m:mn>9</m:mn></m:mfrac><m:msub><m:mi>m</m:mi><m:mrow><m:mi>i</m:mi><m:mo>&#45;</m:mo><m:mn>1</m:mn><m:mo>,</m:mo><m:mi>j</m:mi><m:mo>&#45;</m:mo><m:mn>1</m:mn></m:mrow></m:msub><m:mo>+</m:mo><m:mfrac><m:mn>1</m:mn><m:mn>9</m:mn></m:mfrac><m:msub><m:mi>m</m:mi><m:mrow><m:mi>i</m:mi><m:mo>&#45;</m:mo><m:mn>1</m:mn><m:mo>,</m:mo><m:mi>j</m:mi></m:mrow></m:msub><m:mo>+</m:mo><m:mfrac><m:mn>1</m:mn><m:mn>9</m:mn></m:mfrac><m:msub><m:mi>m</m:mi><m:mrow><m:mi>i</m:mi><m:mo>&#45;</m:mo><m:mn>1</m:mn><m:mo>,</m:mo><m:mi>j</m:mi><m:mo>+</m:mo><m:mn>1</m:mn></m:mrow></m:msub><m:mo>+</m:mo><m:mfrac><m:mn>1</m:mn><m:mn>9</m:mn></m:mfrac><m:msub><m:mi>m</m:mi><m:mrow><m:mi>i</m:mi><m:mo>,</m:mo><m:mi>j</m:mi><m:mo>&#45;</m:mo><m:mn>1</m:mn></m:mrow></m:msub><m:mo>+</m:mo><m:mfrac><m:mn>1</m:mn><m:mn>9</m:mn></m:mfrac><m:msub><m:mi>m</m:mi><m:mrow><m:mi>i</m:mi><m:mo>,</m:mo><m:mi>j</m:mi></m:mrow></m:msub><m:mo>+</m:mo></m:mtd></m:mtr><m:mtr><m:mtd><m:mi mathvariant="normal">&#160;&#160;&#160;&#160;&#160;&#160;&#160;&#160;</m:mi><m:mfrac><m:mn>1</m:mn><m:mn>9</m:mn></m:mfrac><m:msub><m:mi>m</m:mi><m:mrow><m:mi>i</m:mi><m:mo>,</m:mo><m:mi>j</m:mi><m:mo>+</m:mo><m:mn>1</m:mn></m:mrow></m:msub><m:mo>+</m:mo><m:mfrac><m:mn>1</m:mn><m:mn>9</m:mn></m:mfrac><m:msub><m:mi>m</m:mi><m:mrow><m:mi>i</m:mi><m:mo>+</m:mo><m:mn>1</m:mn><m:mo>,</m:mo><m:mi>j</m:mi><m:mo>&#45;</m:mo><m:mn>1</m:mn></m:mrow></m:msub><m:mo>+</m:mo><m:mfrac><m:mn>1</m:mn><m:mn>9</m:mn></m:mfrac><m:msub><m:mi>m</m:mi><m:mrow><m:mi>i</m:mi><m:mo>+</m:mo><m:mn>1</m:mn><m:mo>,</m:mo><m:mi>j</m:mi></m:mrow></m:msub><m:mo>+</m:mo><m:mfrac><m:mn>1</m:mn><m:mn>9</m:mn></m:mfrac><m:msub><m:mi>m</m:mi><m:mrow><m:mi>i</m:mi><m:mo>+</m:mo><m:mn>1</m:mn><m:mo>,</m:mo><m:mi>j</m:mi><m:mo>+</m:mo><m:mn>1</m:mn></m:mrow></m:msub></m:mtd></m:mtr></m:mtable></m:math>

这种类型的滤波器称为 *盒式滤波器* 或 *平均滤波器*。卷积后，滤波后的像素形成 [Figure 8-2](#13_9788126592555-ch08.xhtml#c08-fig-0002) 中所示的图像：

![FIGURE 8-2: Convolution with the box filter reduces the amount of noise in the image.](images/9788126592555-fg0802.png)

[FIGURE 8-2:](#13_9788126592555-ch08.xhtml#rc08-fig-0002) 使用盒式滤波器进行卷积可减少图像中的噪声量。

盒式滤波器去除了图像的大量噪声，但也去除了不是噪声的细节。为了改进盒式滤波器，工程师们设计了一种更有效的降噪滤波器，称为 *高斯滤波器*。滤波器的元素由高斯曲线的值决定。

### Filters and features

图像滤波不仅仅是添加效果。一个关键的应用涉及在更大的图像中查找图像。考虑 [Figure 8-3](#13_9788126592555-ch08.xhtml#c08-fig-0003) 中介绍的 7-x-7 滤波器。

![FIGURE 8-3: The filter’s elements correspond to the pixels of the smiley face.](images/9788126592555-fg0803.png)

[FIGURE 8-3:](#13_9788126592555-ch08.xhtml#rc08-fig-0003) 滤波器的元素对应于笑脸的像素。

如果仔细观察滤波器矩阵，你会看到其元素标识了右侧灰度图像的像素值。换句话说，滤波器定义了它自己的小图像——一个笑脸。图像与其自身的点积会产生一个较大的值，因此如果图像包含一个 7-x-7 的笑脸，对该图像与此滤波器进行卷积将在笑脸所在的位置产生一个较大的值。

卷积的这一特性使得在更大的图像中定位图像成为可能。例如，一架飞机的图像应该有一个驾驶舱、两个机翼和一个机身。如果为驾驶舱使用一个滤波器，为机翼使用一个，为机身使用一个，则每个滤波器的高卷积值都表明飞机的存在。

这些感兴趣的子图像称为 *特征*，并且应用程序可以通过将图像与适当的滤波器进行卷积来检查特征是否存在于图像中。较高的卷积结果表明该特征存在于图像中。

### Feature detection analogy

当谈到图像滤波时，你很容易陷入数学中而忘记发生了什么。所以这里有一个奇怪的类比：想象你有一块放大镜和一张大型人群的高分辨率图像。当你将玻璃在图像上移动时，你可以更清楚地看到人群中的每个人。

假设你在玻璃上雕刻了你的脸。之后，你神奇地施法让玻璃显示一个数字，该数字标识雕刻与玻璃下方图像的匹配程度。最大的数字将出现在玻璃正好位于你脸上的时候。

