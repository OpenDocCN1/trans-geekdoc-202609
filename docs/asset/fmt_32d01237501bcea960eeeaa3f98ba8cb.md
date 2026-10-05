
# 边缘端 SLM 应用场景

- 在远程或移动设置的树莓派上部署 SLM，进行实时数据采集和分析。这可以用于农业中的作物健康监测、环境研究中的野生动物追踪，或灾害响应中的态势感知和资源管理。

## 3. 教育工具

- 创建交互教育工具，利用 SLM 提供即时反馈、语言翻译和辅导。这对于访问先进技术和互联网连接有限的开发地区特别有用。

## 4. 医疗健康应用

- 使用 SLM 进行医学诊断和患者监测。它们可以对症状进行实时分析并建议可能的治疗方案。这可以集成到远程医疗平台或便携健康设备中。

## 5. 本地商业智能

- 在零售或小型企业环境中实施 SLM，分析客户行为、管理库存并优化操作。本地处理数据的能力确保了隐私并减少了对外部服务的依赖。

## 6. 工业物联网

- 将 SLM 集成到工业物联网系统中，用于预测性维护、质量控制和流程优化。树莓派可以作为本地数据处理单元，降低延迟并提高自动化系统的可靠性。

## 7. 自动驾驶车辆

- 使用 SLM 处理来自车辆的传感器数据，实现实时决策和导航。这可以应用于无人机、机器人和自动驾驶汽车，以增强自主性。

## 8. 文化遗产与旅游

- 为 SLM 文化遗产地和博物馆提供交互且信息丰富的指南。游客可以使用这些系统获取实时信息和洞察，在没有互联网连接的情况下增强体验。

## 9. 艺术与创意项目

- 使用 SLM 分析并生成创意内容，如音乐、艺术和文学。这可以促进创意产业的创新项目，并允许展览和表演中产生独特的交互体验。

## 10. 定制化辅助技术

- 为残障人士开发辅助技术，通过实时文本转语音、语言翻译和其他无障碍工具提供个性化的自适应支持。

## 资源

- [10-Ollama_Python_Library 笔记本](https://github.com/Mjrovai/EdgeML-with-Raspberry-Pi/blob/main/OLLAMA_SLMs/10-Ollama_Python_Library.ipynb)
- [20-Ollama_Function_Calling 笔记本](https://github.com/Mjrovai/EdgeML-with-Raspberry-Pi/blob/main/OLLAMA_SLMs/20-Ollama_Function_Calling.ipynb)
- [30-Function_Calling_with_images 笔记本](https://github.com/Mjrovai/EdgeML-with-Raspberry-Pi/blob/main/OLLAMA_SLMs/30-Function_Calling_with_images.ipynb)
- [40-RAG-simple-bee 笔记本](https://github.com/Mjrovai/EdgeML-with-Raspberry-Pi/blob/main/OLLAMA_SLMs/40-RAG-simple-bee.ipynb)
- [calc_distance_image python 脚本](https://github.com/Mjrovai/EdgeML-with-Raspberry-Pi/blob/main/OLLAMA_SLMs/calc_distance_image.py)

# 视觉语言模型 (VLM)

![DALL·E 提示词 - 一个包含视觉任务的树莓派设置。图像显示了一个连接到摄像头的树莓派，周围视觉显示了各种计算机视觉任务，包括目标检测、图像描述、分割和视觉定位。树莓派放置在桌子上，显示器显示了与这些任务相关的边界框和注释。背景应该是一个家庭工作空间，有开发者和爱好者通常使用的工具和设备。](img/file1048.jpg)

DALL·E 提示词 - 一个包含视觉任务的树莓派设置。图像显示了一个连接到摄像头的树莓派，周围视觉显示了各种计算机视觉任务，包括目标检测、图像描述、分割和视觉定位。树莓派放置在桌子上，显示器显示了与这些任务相关的边界框和注释。背景应该是一个家庭工作空间，有开发者和爱好者通常使用的工具和设备。

## 介绍

在本次上手实验中，我们将持续探索边缘侧的 AI 应用，从 `Florence-2`（微软最先进的视觉基础模型）的基础设置开始，到在树莓派等设备上的高级实现。我们将学习如何使用视觉语言模型 (VLMs) 在树莓派上执行描述、目标检测、定位、分割和 OCR（光学字符识别）等任务。

### 为什么在边缘端使用 Florence-2？

[Florence-2](https://arxiv.org/abs/2311.06242) 是微软根据 MIT 许可证开源的一款视觉语言模型，它通过将轻量级架构与强大的能力相结合，显著推进了视觉语言模型的发展。得益于在海量 `FLD-5B` 数据上的训练（该数据集包含 1.26 亿张图像和 54 亿个视觉注释），它实现了与更大的模型相当的性能。这使得 Florence-2 成为部署在电力和计算资源受限的边缘端的理想选择。

在本教程中，我们将探索如何使用 `Florence-2` 用于实时计算机视觉应用，例如：

- 图像描述
- 目标检测
- 分割
- 视觉定位

> **视觉定位 (Visual grounding)** 涉及将文本描述与图像中的特定区域关联起来。这使得模型能够理解提示中描述的特定物体或实体位于图像的什么位置。例如，如果提示是"一辆红汽车"，模型将识别并突出图像中发现红汽车的区域。视觉定位对于需要文本与视觉内容精确对齐的应用非常有帮助，例如人机交互。

在本教程中，我们将探索如何使用 `Florence-2` 用于实时计算机视觉应用，例如：我们将学习如何使用视觉语言模型 (VLMs) 在树莓派上执行描述、目标检测、定位、分割和 OCR 等任务。

在实验实验中，我们将通过以下方式：

- 图像描述
- 目标检测
- 分割
- 视觉定位
- 在树莓派上运行 `Florence-2`
- 各种视觉任务

### Florence-2 模型架构

Florence-2 由两个主要部分组成：**图像编码器**和**多模态编码器解码器**。

![Florence-2 架构](media/file1049.jpg)

- **图像编码器**：基于 ViT（视觉 Transformer）。
- **多模态编码器解码器**：处理视觉和文本输入。

> **视觉定位 (Visual grounding)** 涉及将文本描述与图像中的特定区域关联起来。这使得模型能够理解提示中描述的特定物体或实体位于图像的什么位置。例如，如果提示是"一辆红汽车"，模型将识别并突出图像中发现红汽车的区域。

## 技术概述

Florence-2 引入了几个使其与众不同的特征：

### 架构

- **轻量级设计**：提供两个版本：
  - `Florence-2-Base`：2.3 亿参数
  - `Florence-2-Large`：7.1 亿参数
- **统一表示**：通过单一架构处理多种视觉任务。
- **ViT 视觉编码器**：将图像转换为视觉标记。
- **基于 Transformer 的多模态编码器解码器**：处理视觉嵌入。

### 训练数据集 (FLD-5B)

- 1.26 亿张独特图像
- 54 亿个全面的注释，包括：
  - 5 亿文本注释
  - 13 亿区域-文本注释
  - 36 亿文本-短语-区域注释
- 使用专家模型的自动标注流水线
- 高质量标签的迭代优化过程

### 主要能力

Florence-2 在多个视觉任务上表现出色：

#### 零样本性能

- 图像描述：在 COCO 上获得 135.6 CIDEr 分
- 视觉定位：在 Flickr30k 上达到 84.4% 的召回率 1
- 目标检测：在 COCO val2017 上达到 37.5 mAP
- 引用表达式：在 RefCOCO 上达到 67.0% 的准确率

#### 微调后性能

- 尽管规模较小，但能与专家模型竞争
- 在特定基准测试中优于更大的模型
- 能够高效适应新任务

### 实际应用

Florence-2 可应用于多个领域：

1. **内容理解**
   - 用于无障碍的自动图像描述
2. **电子商务**
   - 产品图像分析
   - 视觉搜索
   - 自动产品标记
3. **医疗保健**
   - 医学图像分析
   - 诊断辅助
   - 研究数据处理
4. **安全与安防**
   - 目标检测与跟踪
   - 异常检测
   - 场景理解

### 将 Florence-2 与其他 VLM 进行比较

Florence-2 以其出色的零样本（zero-shot）能力在视觉语言模型中脱颖而出。与 [Google PaliGemma](https://huggingface.co/blog/paligemma) 等依赖大量微调来适应各种任务的模型不同，正如我们在本实验室中看到的，Florence-2 可以开箱即用。它还可以与 GPT-4V 和 Flamingo 等更大的模型竞争，这些模型通常拥有多得参数，但性能有时只能达到 Florence-2 的水平。例如，尽管 Florence-2 的参数量是 Kosmos-2 的两倍，但它实现的零样本结果却更好。

在基准测试中，Florence-2 在 COCO 图像描述和指代表达理解任务中展现了卓越的性能。在 [COCO 数据集](https://docs.ultralytics.com/datasets/detect/coco/) 的目标检测和分割任务中，它优于 PolyFormer 和 UNINEXT 等模型。对于性能和资源效率都至关重要的现实应用来说，这是一个极具竞争力的选择。

# 设置与安装

我们选择的边缘设备是树莓派 5 (Raspi-5)。其强大的平台配备了 Broadcom `BCM2712`，这是一颗 2.4 GHz 四核 64 位 Arm Cortex-A76 CPU，具有加密扩展功能和增强的缓存能力。它拥有 VideoCore VII GPU、双带 HDR 的 4Kp60 HDMI® 输出口以及一个 4Kp60 HEVC 解码器。内存选项包括 4 GB 和 8 GB 高速 LPDDR4X SDRAM，我们选择 8 GB 版本来运行 Florence-2。它还通过 microSD 卡槽提供扩展存储，并带有一个 `PCIe 2.0` 接口用于连接 `M.2 SSD`（固态硬盘）等快速外设设备。

> 对于实际应用，SSD 是比 SD 卡更好的选择。

我们建议在本实验室安装 Active Cooler，这是一种专为树莓派 5 (Raspi-5) 设计的夹式散热解决方案。它将铝制散热片与温控风扇结合在一起，使 Raspi-5 在运行 Florence-2 等重负载下仍保持舒适运行。

![Active Cooler](img/file1052.jpg)

## 环境配置

为了在树莓派 5 上运行 [Microsoft Florence-2](https://huggingface.co/microsoft/Florence-2-base)，我们需要几个库：

1. **[Transformers](https://huggingface.co/docs/transformers/en/index)**：
   - Florence-2 使用 Hugging Face 的 `transformers` 库进行模型加载和推理。该库提供了处理预训练视觉语言模型的架构，使得能够轻松执行图像描述、目标检测等任务。本质上，`transformers` 帮助与模型交互、处理输入提示词并获取输出。
2. **PyTorch**：
   - PyTorch 是一个深度学习框架，提供了运行 Florence-2 模型所需的底层架构，包括张量操作、GPU 加速（如果可用 GPU）以及模型训练/推理功能。Florence-2 模型在 PyTorch 中训练，我们需要它来利用其函数、层和计算能力，在树莓派上进行推理。
3. **Timm** (PyTorch Image Models)：
   - Florence-2 使用 `timm` 来访问视觉模型的高实现。
4. **Einops**：
   - Florence-2 使用 `einops` 进行灵活的张量操作，这对于高效处理张量维度非常有用。

`AutoModelForCausalLM.from_pretrained()` 从 Hugging Face 上的 Microsoft 仓库加载预训练的 Florence-2 模型。`torch_dtype` 根据可用的硬件（GPU/CPU）进行设置，`trust_remote_code=True` 允许使用模型可能提供的任何自定义代码。

`.to(device)` 将模型移动到适当的设备（CPU 或 GPU）。在我们的案例中，它将被设置为 `CPU`。

### 处理器初始化

- `AutoProcessor.from_pretrained()` 加载用于 Florence-2 的处理器。该处理器负责将文本和图像输入转换为模型可以处理的格式（例如：对文本进行编码、归一化图像等）。

### 定义提示词 (Prompt)

```python
prompt = "<OD>"
```

- **提示词定义**：使用字符串 `"<OD>"` 作为提示词。这指的是"目标检测（Object Detection）"，指示模型检测图像中的物体。

#### 下载和加载图像

```python
import requests
from PIL import Image

url = "https://example.com/image.jpg"
response = requests.get(url, stream=True)
image = Image.open(response.raw)
```

- **下载图像**：`requests.get()` 函数从指定的 URL 获取图像。`stream=True` 参数确保图像是流式传输的，而不是一次性完全下载。
- **打开图像**：`Image.open()` 打开图像以便模型对其进行处理。

#### 处理输入

```python
inputs = processor(text=prompt, images=image, return_tensors="pt")
inputs = inputs.to(device, torch_dtype)
```

- **处理输入数据**：`processor()` 函数处理文本（`prompt`）和图像（`image`）。`return_tensors="pt"` 参数将处理后的数据转换为 PyTorch 张量，这是将数据输入模型的必要条件。
- **将输入移动到设备**：`.to(device, torch_dtype)` 将输入移动到正确的设备（CPU 或 GPU）并分配相应的数据类型。

### 生成输出

```python
generated_ids = model.generate(
    input_ids=inputs["input_ids"],
    pixel_values=inputs["pixel_values"],
    max_new_tokens=1024,
    do_sample=False,
    num_beams=3
)
```

- **模型生成**：使用 `model.generate()` 根据输入数据生成输出。
  - `input_ids`：代表提示词的 Token 形式。
  - `pixel_values`：包含处理后的图像数据。
  - `max_new_tokens=1024`：指定响应中生成的新 Token 最大数量。这限制了响应的长度。
  - `do_sample=False`：禁用采样；相反，生成过程使用确定性方法（束搜索）。
  - `num_beams=3`：开启三束宽度的束搜索，通过在生成过程中考虑多种可能性来提高输出质量。

#### 解码生成的文本

```python
generated_text = processor.batch_decode(generated_ids, skip_special_tokens=False)
```

- **批量解码**：`processor.batch_decode()` 将生成的 ID（Token）解码为可读的文本。`skip_special_tokens=False` 参数意味着输出将包含可能是响应部分的任何特殊 Token。

#### 对生成内容进行后处理

```python
parsed_answer = processor.post_process_generation(generated_text, task="<OD>", image_size=image.size)
```

- **后处理**：调用 `processor.post_process_generation()` 对生成的文本进行进一步处理，根据任务（目标检测使用 `"<OD>"`）和图像大小对其进行解释。
- 该函数从生成的文本中提取特定信息，例如检测到的物体的边界框（bounding boxes），使得输出对于视觉任务更有用。

#### 打印输出

```python
print(parsed_answer)
```

- 最后，`print(parsed_answer)` 显示输出，可能包括目标检测结果，例如图像中检测到的物体的边界框坐标和标签。

#### 结果

运行代码，我们得到的解析后的答案（Parsed Answer）：

```python
{'<OD>': {'bboxes': [[0.1, 0.2, 0.5, 0.7], ...], 'labels': ['cat', 'dog', ...]}}
```

首先，让我们检查图像：

```python
image.show()
```

![检测结果](img/file1056.png)

根据目标检测结果，我们可以看到：

```python
print(parsed_answer['<OD>'])
```

似乎检测到了几个物体。我们还可以编写代码在寻找物体时画出边界框：

```python
def plot_bbox(image, detections):
    # 绘制边界框的代码
    pass
```

> **Box (x0, y0, x1, y1)**：位置 Token 对应于框的左上角和右下角。

运行

```python
plot_bbox(image, parsed_answer['<OD>'])
```

我们得到：

![边界框可视化](img/file1057.png)

## 2. 表格

```python
# 表格处理代码
```

### 更详细的描述 (Caption)

#### 1. 狗和猫

```python
# 描述代码
```

#### 2. 表格

```python
# 表格描述代码
```

> 我们可以注意到，描述任务越详细，延迟就越长，出错的可能性也越高（例如，"图像显示花园里有四只猫和一只狗"，而不是两只狗三只猫）。

### 目标检测 (Object Detection)

我们可以使用提示词 `<OD>` 运行之前的相同函数进行目标检测。

```python
prompt = "<OD>"
# 运行检测
```

让我们看看结果：

```python
print(parsed_answer)
```

只有通过标签 `['cat', 'cat', 'cat', 'dog', 'dog']` 才能看到图像中的主要物体被捕获。让我们应用之前使用的函数来绘制边界框：

```python
plot_bbox(image, parsed_answer['<OD>'])
```

![猫狗检测结果](img/file1059.png)

我们也对表格图像进行操作：

```python
# 表格图像检测
```

![表格检测结果](img/file1060.png)

### 密集区域描述 (Dense Region Caption)

可以在图像的特定子区域中，将经典的目标检测与描述任务相结合：

```python
# 密集区域描述代码
```

![密集区域描述结果](img/file1061.png)

### 描述到短语定位 (Caption to Phrase Grounding)

```python
# 短语定位代码
```
