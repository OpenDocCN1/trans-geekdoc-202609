
## 字符几何
| `xadvance` || 距离当前位置到字符空间末尾的距离 |

| `page` || 包含纹理的页面 |

| `chnl` || 包含数据的通道（1 = 蓝色，2 = 绿色，4 = 红色，8 = alpha，15 = 全部） |

ASCII 码 112 对应的字符是 p，因此 char 行展示了该字母的属性。 [图 7.2](#chapter7.xhtml#fig7_2) 描述了该行和字符的尺寸。

![图 7.2 字符几何。](images/fig7_2.jpg)

[图 7.2](#chapter7.xhtml#b7fig7_2) 字符几何。

该图说明了 `xoffset` 和 `xadvance` 之间的区别。两者都标识了从当前位置开始的水平距离。`xoffset` 指定从当前位置到字符应显示位置的距离。`xadvance` 表示从初始当前位置到下一个当前位置的距离。

## 字距调整

简单地将字符并排打印不足以产生专业的外观。不同的字符对需要不同的水平间距，而调整间距称为 *kerning*。对于像 Courier 这样的等宽字体来说这不是问题，但当常规字体在没有正确字距调整的情况下打印时，结果看起来会很突兀。

因此，Andreas Jonsson 的 Bitmap Generator 生成的 `*.fnt` 文件包含多行以 kerning 开头的行。以下是一个示例：

```
kerning first=111 second=120 amount=-1
```

这表示，如果第一个字符的 ID 为 111，第二个字符的 ID 为 120，则字符之间的间距应减少 1。换句话说，当字符 ‘o’ 在字符 ‘x’ 之前时，两者之间的空间应减少 1 以实现正确的字距调整。

## 示例应用—显示文本

`Ch07_Text` 应用演示了应用程序如何通过从纹理图集中读取矩形在画布上绘制文本。 [图 7.3](#chapter7.xhtml#fig7_3) 显示了生成的文本的外观。

![图 7.3 Ch07_Text 应用。](images/fig7_3.jpg)

[图 7.3](#chapter7.xhtml#b7fig7_3) Ch07_Text 应用。

`Ch07_Text` 应用的顶级目录包含六个文件。 [表 7.8](#chapter7.xhtml#tbl7_8) 列出了它们并提供了每个文件的描述。

[表 7.8](#chapter7.xhtml#b7tbl7_8) Ch07_Text 目录中的文件

| 文件 || 描述 |

| --- | --- |

| index.html || 创建网页并加载 JavaScript |

| --- | --- |

| ch07_text.js || 用于绘制文本的 WebGPU 代码 |

| lato.png || 包含 Lato 字符的纹理图集 |

| lato.fnt || 包含 Lato 字体数据的文本文件 |

| lato_data.json || Lato 字体数据（JSON 格式） |

| gen_text_json.py || 生成 JSON 文件的 Python 脚本 |

与其编写读取字体文件（`*.fnt`）的 JavaScript 代码，我编写了一个 Python 脚本（`gen_text_json.py`），它将 `*.fnt` 文件转换为 JSON 文件，该文件定义了一个包含每个字符属性的数组。这可以通过更改第一行的 `FONT_NAME` 变量轻松更改为读取另一种字体。

例如，`lato_data.json` 中的以下文本显示了包含 ID 为 85 的字符（字母 U）属性的文件部分：

```
{
    "id": 85,
    "x": 0,
    "y": 47,
    "width": 17,
    "height": 19,
    "xoffset": 1,
    "yoffset": 7,
    "xadvance": 20
    "kerning": { "38": -1, "44": -1, "46": -1, "47": -1, "65": -1 }
},
```

`kerning` 属性标识应如何根据下一个字符调整间距。例如，如果 “U” 后跟 “A”（ID = 65），则间距应调整 by -1 以正确设置字距。

`ch07_font.js` 文件包含应用程序的主要源代码。为了描述此代码，本讨论将其分为三个部分：

1. 创建顶点缓冲区
2. 创建索引缓冲区
3. 编写顶点和片段着色器

本节探讨每种操作并解释它们在代码中是如何执行的。

### 顶点缓冲区

从渲染角度来看，绘制一个字符需要两个连接的三角形。`topology` 属性设置为 `triangle-strip`，因此绘制两个连接的三角形需要四个顶点。每个顶点需要定义空间中的两个坐标（`x` 和 `y`）以及相应的纹理坐标（`u` 和 `v`）。因此，每个顶点在顶点缓冲区中由一组四个浮点值定义。每个字符需要四个顶点，总共 16 个浮点值。

在 `ch07_text.js` 中，形成浮点值数组是一个复杂的过程。数组名为 `vertexData`，它是用以下代码创建的：

```
// Define vertex data
const textMsg = "Hello, world!";
let leftX = -0.9;
const topY = 0.75;
const bottomY = 0.5;
const lineHeight = 32;
const scale = (topY - bottomY)/lineHeight;

// Create vertex data array
const vertexData = new Float32Array(16 * textMsg.length);

// Read character data
const fileResponse = await fetch("./lato_data.json’);
const charData = await fileResponse.json();

// Iterate through characters in message
for (let i = 0; i < textMsg.length; i++) {

    // Get index of message character
    let currentChar = charData[textMsg.charCodeAt(i) - 32];

    // Set texture coordinates
    vertexData[16 * i + 2] = currentChar.x/256.0;
    vertexData[16 * i + 3] = (currentChar.y + currentChar.height)/256.0;
    vertexData[16 * i + 6] = currentChar.x/256.0;
    vertexData[16 * i + 7] = currentChar.y/256.0;
    vertexData[16 * i + 10] = (currentChar.x + currentChar.width)/256.0;
    vertexData[16 * i + 11] = (currentChar.y + currentChar.height)/256.0;
    vertexData[16 * i + 14] = (currentChar.x + currentChar.width)/256.0;
    vertexData[16 * i + 15] = currentChar.y/256.0;
    // Set vertex coordinates
    if(i == 0) {
        vertexData[0] = leftX;
        vertexData[1] = bottomY;
        vertexData[4] = leftX;
        vertexData[5] = topY - currentChar.yoffset * scale;
    }
    else {
        vertexData[16 * i] = leftX + currentChar.xoffset * scale;
        vertexData[16 * i + 1] = bottomY;
        vertexData[16 * i + 4] = vertexData[16*i];
        vertexData[16 * i + 5] = topY - currentChar.yoffset * scale;
    }
    vertexData[16 * i + 8] = vertexData[16*i] + currentChar.width * scale;
    vertexData[16 * i + 9] = bottomY;
    vertexData[16 * i + 12] = vertexData[16 * i + 8];
    vertexData[16 * i + 13] = topY - currentChar.yoffset * scale;

    // Set kerning
    let kerning = 0;
    if(‘kerning’ in currentChar) {

        // Get next character
        if(i != textMsg.length-1) {
            let nextId = charData[textMsg.charCodeAt(i+1) - 32].id;

            // Apply kerning if needed
            if (nextId in currentChar.kerning) {
                kerning = parseInt(currentChar.kerning[nextId]);
            }
        }
    }

    // Update current horizontal position
    leftX += (currentChar.xadvance + kerning) * scale;
}

// Create vertex buffer
const vertexBuffer = device.createBuffer({
    label: "Vertex Buffer 0",
    size: vertexData.byteLength,
    usage:
        GPUBufferUsage.VERTEX |
        GPUBufferUsage.COPY_DST
});
// Write data to buffer
device.queue.writeBuffer(vertexBuffer, 0, vertexData);
renderPass.setVertexBuffer(0, vertexBuffer);
```

这段代码首先定义要打印的消息（`Hello, world!`）和应用程序使用的不同变量。`leftX` 变量标识渲染的第一个 x 坐标。由于它设置为 −0.9，因此第一个字符将开始于视口左侧边缘附近。

`topY` 和 `bottomY` 值标识该区域中顶点的最大和最小 y 坐标。根据字体文件中的说明，Lato 字体中的字符适用于 32 点行，因此 `lineHeight` 设置为 32。`scale` 用作显示坐标与字体尺寸之间的缩放因子，通过计算（`topY` – `bottomY`）/`lineHeight` 获得。
