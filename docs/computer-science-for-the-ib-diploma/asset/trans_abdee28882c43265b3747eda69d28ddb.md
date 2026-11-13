

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_48_0.png)

一张分辨率为 2268 x 4032、色深为 24 位、文件大小为 1.77 MB 的高分辨率图片

当今大多数屏幕都是 24 位的，可显示 1680 万种颜色。每个像素包含三种光：红光、绿光和蓝光，即所谓的“RGB”，数值范围为 0 到 255（每个颜色通道 1 字节）。这对大多数应用来说已经足够，因为大多数人类眼睛只能区分约 1000 万种不同的颜色。超过 24 位的显示器通常只在精度至关重要的专业领域才需要。左侧是一张高分辨率图片。如果我们放大这张图片中的连衣裙，可以看到单个像素的分解以及不同颜色通道的数值。在处理图形时，这些数值通常以十六进制显示。如果我们以连衣裙左上角的像素为例：

```
R: 216, G: 190, B: 199 = #d8bec7
```

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_48_1.png)

上图的放大区域，显示每个像素的数值 – 使用 www.csfieldguide.org.nz/en/interactives/pixel-viewer 创建

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_48_2.png)

照片中连衣裙左上角像素的颜色值 – 使用 www.w3schools.com/colors/colors_rgb.asp 创建

我们还可以看到较低色深对同一张图片的影响：

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_49_0.png)

同一张图片使用多种色深：从 24 位到 0 位 – 使用 www.csfieldguide.org.nz/en/interactives/image-bit-comparer 创建

## 复习问题

- 1 一位图像使用 3 位色深，可表示八种不同颜色。
  如果位图使用 32 种不同颜色，需要多少位来表示这些颜色？

- 2 Raj 正在为一款游戏创建位图图形。图片尺寸为宽 10 像素、高 12 像素。
  图片中总共有多少个像素？

- 3 Alice 正在整理多年来创建的数字艺术作品集。
  在将艺术作品文件传输到新的云存储服务时，她注意到每个文件都比预想的要大。这是因为，除了实际图像数据外，文件还包含准确复现图像所需的额外信息。这个包含像素数据详细信息的附加信息称为什么？

- 4 确定一个支持 512 种不同颜色、尺寸为 800 x 600 像素的位图图像所需的存储容量。
  然后，如果文件元数据额外占用 25% 的空间，计算文件大小（以千字节 KB 为单位）。将答案表示为包含小数值的实数。

## 编程练习

以下是使用 Python 或 Java 深入探索图像的一些有趣方法。

- 1. 提取并打印 RGB 值。

```java
import java.awt.Color;
import java.awt.image.BufferedImage;
import java.io.File;
import java.io.IOException;
import javax.imageio.ImageIO;

public class ImageToRGB {
    public static void main(String[] args) {
        try {
            // Load the image
            BufferedImage image = ImageIO.read(new File("sample_image.jpg"));
            // Get image dimensions
            int width = image.getWidth();
            int height = image.getHeight();
            // Loop through each pixel
            for (int y = 0; y < height; y++) {
                for (int x = 0; x < width; x++) {
                    // Get the RGB value of the pixel
                    int pixel = image.getRGB(x, y);
                    Color color = new Color(pixel);
                    // Extract the red, green and blue components
                    int red = color.getRed();
                    int green = color.getGreen();
                    int blue = color.getBlue();
                    // Print the RGB values
                    System.out.println("Pixel at (" + x + ", " + y + "): R=" + red + ", G=" + green + ", B=" + blue);
                }
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

对于 Python，你需要先安装 Pillow 库。在终端中运行以下命令安装所需的库：
pip install pillow

使用此代码访问每个像素的 RGB 值
```python
from PIL import Image
# Load the image
image = Image.open("sample_image.jpg")
# Convert the image to RGB mode
image = image.convert("RGB")
# Get the image dimensions
width, height = image.size
# Extract and print RGB values
for y in range(height):
    for x in range(width):
        pixel = image.getpixel((x, y))
        red, green, blue = pixel
        print(f"Pixel at ({x}, {y}): R={red}, G={green}, B={blue}")
```

- 2. 应用灰度滤镜。

警告：
此代码按像素处理图像，这意味着它会遍历图像中的每个像素来应用灰度滤镜。对于非常大的图像（例如高分辨率照片），此过程可能计算密集且完成需要大量时间。在将其应用于较大文件之前，建议先在较小的图像（例如 100x100 像素）上测试此代码以观察其行为。

```python
from PIL import Image
# Load the image
image = Image.open("sample_image.jpg")
# Convert the image to RGB mode
image = image.convert("RGB")
# Get the image dimensions
width, height = image.size
# Create a new image to store the grayscale result
grayscale_image = Image.new("RGB", (width, height))
# Apply a grayscale filter
for y in range(height):
    for x in range(width):
        pixel = image.getpixel((x, y))
        red, green, blue = pixel
        grayscale = int(0.3 * red + 0.59 * green + 0.11 * blue)
        grayscale_image.putpixel((x, y), (grayscale, grayscale, grayscale))
# Save the grayscale image
grayscale_image.save("grayscale_image.jpg")
```

## Java

```java
import java.awt.Color;
import java.awt.image.BufferedImage;
import java.io.File;
import java.io.IOException;
import javax.imageio.ImageIO;
public class ImageToGrayScale {
    public static void main(String[] args) {
        try {
            // Load the image
            BufferedImage image = ImageIO.read(new File("sample_image.jpg"));
            // Get image dimensions
            int width = image.getWidth();
            int height = image.getHeight();
            // Create a new image to store the grayscale result
            BufferedImage grayscaleImage = new BufferedImage(width, height,
            BufferedImage.TYPE_INT_RGB);
            // Apply a grayscale filter
            for (int y = 0; y < height; y++) {
                for (int x = 0; x < width; x++) {
                    // Get the RGB value of the pixel
                    int pixel = image.getRGB(x, y);
                    Color color = new Color(pixel);
                    // Extract the red, green and blue components
                    int red = color.getRed();
                    int green = color.getGreen();
                    int blue = color.getBlue();
                    // Compute the grayscale value
                    int grayscale = (int) (0.3 * red + 0.59 * green + 0.11 * blue);
                    // Create a new Color object with the grayscale value
                    Color grayColor = new Color(grayscale, grayscale, grayscale);
                    // Set the new pixel value in the grayscale image
                    grayscaleImage.setRGB(x, y, grayColor.getRGB());
                }
            }
            // Save the grayscale image
            ImageIO.write(grayscaleImage, "jpg", new File("grayscale_image.jpg"));
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

## 音频

- **幅度**：声音波形变化的幅度，表示声音的响度或强度。
- **采样**：以固定间隔测量信号幅度，将连续模拟信号转换为一系列离散数字值的过程。
- **kHz（千赫兹）**：频率单位，等于每秒 1000 个周期，通常用于测量音频信号的采样率。

音频的模拟形式是一种连续信号，通过气压变化表示声波。这些声波可以通过输入设备（如麦克风）捕获，麦克风将声波转换为数字信号并以二进制形式存储。此过程涉及多个步骤：

### 模拟-数字转换（ADC）

声音是连续的模拟信号。ADC 在离散间隔对声音的幅度（响度）进行采样，该过程称为采样。发生此过程的速率以赫兹（Hz）为单位进行测量——赫兹越高，每秒记录的样本越多。CD 质量音频使用 44.1 kHz，但专业音质音频在 48 kHz 时采样。

然后将该样本存储并以二进制数值表示。精度由位深度决定。位深度越大，可用于描述样本的可能值就越多。例如，CD 质量声音的位深度为 16 位，可提供 2^16 个值，即 65,536 个值。使用 24 位的专业音频拥有 2^24 个值，即 16,777,216 个值。

一秒钟的 44.1 kHz、16 位立体声（即两个声道）音频包含：

- 每秒 44,100 个样本
- 每个样本由 16 位表示
- 每秒总存储需求为 44,100 样本/秒 × 16 位/样本 × 2 声道 = 每秒 1,411,200 位，即每秒 176,400 字节。

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_53_0.png)

蓝色连续波形表示模拟信号，它是声音的平滑连续表示。数字信号由按固定间隔（采样率）采集的离散样本组成，说明了连续模拟信号如何转换为数字形式中的一系列离散点。

### 存储格式

有多种不同类型的文件格式用于存储音频。最常见的是 WAV、AIFF、MP3 和 FLAC。它们主要取决于是否压缩。未压缩格式存储原始二进制数据，而压缩格式使用算法来减小文件大小以便存储或传输。就像图像压缩一样，音频

