

## Java

```
import java.util.Scanner;
public class CaesarCipher {
    public static String caesarCipherEncrypt(String message, int key) {
        StringBuilder encryptedMessage = new StringBuilder();
        for (char ch : message.toCharArray()) {
            if (Character.isLetter(ch)) { // Check whether the character is
                // a letter
                char shift;
                if (Character.isUpperCase(ch)) {
                    shift = 'A'; // Determine the ASCII offset for uppercase
                    // letters
                } else {
                    shift = 'a'; // Determine the ASCII offset for lowercase
                    // letters
                }
                // Shift the character and wrap around the alphabet if
                // necessary
                char encryptedChar = (char) ((ch - shift + key) % 26 + shift);
                encryptedMessage.append(encryptedChar);
            } else {
                encryptedMessage.append(ch); // Non-letter characters remain
                // unchanged
            }
        }
        return encryptedMessage.toString();
    }
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        // User input
        System.out.print("Enter the message to encrypt: ");
        String message = scanner.nextLine();
        System.out.print("Enter the key (an integer): ");
        int key = scanner.nextInt();
        // Encrypt the message
        String encryptedMessage = caesarCipherEncrypt(message, key);
        System.out.println("Encrypted message: " + encryptedMessage);
    }
}
```

- 1. 研究这段代码的工作原理后，为接收加密消息的人编写解密函数。
- 2. 编写一个能够对加密消息进行暴力破解的函数，以便识别使用的密钥。

**暴力破解**：一种通过系统地尝试每一个可能的密钥直到找到正确密钥来破解密码的方法。

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_46_0.png)

第一个数字图像：Russel Kirch 的儿子 Walden，1957 年

- **模拟信号**：一种表示变化物理量的连续信号，例如声音波，其在某个范围内平滑变化；数字则表示离散的二进制值（0 和 1），能够实现精确且抗干扰的处理。
- **位图**：一种由像素网格组成的数字图像，每个像素持有特定的颜色值，以光栅化格式表示图像。
- **像素**：即“画素元素”（picture element）的缩写；数字图像或显示器的最小单位，表示图像中具有特定颜色和强度的单个点。

## 图像

1957 年，Russel Kirch 扫描了一张他儿子 Walden 的模拟照片，将图片转换为数字文件。这是有史以来创建的第一张数字图像。这是视觉技术演进过程中的一个重要里程碑，彻底改变了我们拍摄、存储和处理图像的方式。早期数码相机和扫描仪的发展使设备能够将光转换为数字数据，开启了如今已司空见惯的趋势，而从胶片到数字的转变则改变了众多行业，从摄影和医学成像到电信和娱乐。

## 位图图像

位图图像，也称为“栅格”图像，是数字图形最基本的形式之一。它们通过使用像素网格来复制图像，每个像素都分配了特定的颜色和强度。

页面底部有一个分辨率为 13x10（宽 13 像素，高 10 像素）的位图图像。每个像素使用 1 位数据进行“描述”：即 1 或 0。在此示例中，1 表示黑色，0 表示白色（单色图像），用于描述颜色的位数称为“位深”或颜色深度。因此，在本示例中，我们有一个 13x10 且颜色深度为 1 位的图像。

要计算此图像的大小，公式为：

```
image size = width (pixels) x height (pixels) x colour depth (bits per pixel)
13 x 10 x 1 = 130 bits (or 130 / 8 = 16.25 bytes)
```

然而，实际上，此计算并不完全准确，因为图像还需要更多数据来存储元数据和其他头信息。这可能包括尺寸、颜色深度和其他属性等信息，这些信息使 CPU 能够准确读取图像数据，从而在屏幕上正确显示图像。

| 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 | 1 | 1 | 1 | 0 | 1 | 1 | 0 | 0 |
| 0 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 1 | 0 |
| 0 | 0 | 0 | 0 | 1 | 1 | 0 | 1 | 1 | 1 | 0 | 0 | 0 |
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

- 图像分辨率：数字图像中包含的像素数量，通常以像素尺寸（宽 × 高）表示，有时也以像素密度（PPI / DPI）表示用于打印质量。
- 颜色深度：也称为“位深”；用于表示数字图像中每个像素颜色所用的位数，决定了可以显示的颜色范围和精度。
- 元数据：描述其他数据的信息，提供关于数据内容、结构和属性的上下文和细节。在数字图像的上下文中，元数据包括图像尺寸、颜色深度、创建日期、作者、相机设置和其他属性等信息，这些信息有助于有效地管理、理解和使用图像。

要提高位图图像的质量，我们有两个选择：可以增加像素数量（分辨率），也可以增加颜色深度。

### 分辨率 – 增加像素数量：

增加位图图像中的像素数量可以提高图像质量。更高的分辨率可以提供更大的细节和清晰度，而分辨率较低的图像可能会导致细节丢失并出现像素化外观。然而，像素数量不是唯一的考虑因素：显示图像的屏幕大小也很重要。PPI（每英寸像素数）较高的图像比 PPI 较低的图像看起来更清晰。想象一下，将分辨率为 1024×768 的图像显示在手机上与在电影屏幕上显示的对比。由于像素密度更高，手机上的更高 PPI 会提供更清晰的图像。更高分辨率图像的权衡是更大的文件大小，这可能会影响存储和传输效率。

### 常见图像分辨率

| 分辨率名称 | 像素尺寸 | 常见用途 |
|---|---|---|
| VGA | 640 × 480 | 早期计算机屏幕，基本 Web 图形 |
| SVGA | 800 × 600 | 标准计算机显示器，Web 图形 |
| HD (720p) | 1280 × 760 | HD 视频，基本高清电视 |
| Full HD (1080p) | 1920 × 1080 | Full HD 视频，现代显示器和电视 |
| 2K | 2048 × 1080 | 数字电影，一些显示器 |
| Quad HD (1440p) | 2560 × 1440 | 高分辨率显示器，游戏，专业用途 |
| 4K (Ultra HD) | 3840 × 2160 | 超高清电视，高端显示器，视频 |
| 8K | 7680 × 4320 | 尖端电视，专业视频 |

### 颜色深度 – 增加颜色数量：

当我们增加颜色深度时，可以表示更广泛的颜色范围，从而产生更生动、更准确的图像。如果图像的颜色深度较低，可能会导致色带现象，即渐变呈现为明显的阶梯而不是平滑过渡。然而，与图像分辨率一样，我们也必须考虑文件大小对存储和传输时间的影响。颜色深度越高，文件大小越大。

要计算可用颜色的数量，我们计算 2 的图像颜色深度次方；例如，对于具有 8 位颜色深度的图像：

2^8 = 256

### 常见颜色深度

| 颜色深度（每像素位数） | 颜色数量 | 常见用途 |
|---|---|---|
| 1 位 | 2 | 简单图形，单色显示器 |
| 4 位 | 16 | 早期计算机图形，图标 |
| 8 位 | 256 | GIF 图像，简单 Web 图形 |
| 16 位 | 65,536 | 高彩色图像，某些视频格式 |
| 24 位（真彩色） | 1680 万 | 大多数图像和视频的标准，数码摄影 |
| 30 位（深色） | 10 亿以上 | 专业摄影，高端显示器和电视 |
| 36 位 | 680 亿以上 | 医学成像，专业图形 |
| 48 位 | 万亿 | 高端个人应用，详细科学成像 |

