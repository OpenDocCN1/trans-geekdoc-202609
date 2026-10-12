
本层中仅有一个固定节点。通过使用公式[(7)](#B9780323852098000055.xhtml#fo0045) 对所有输入信号求和，在本层计算总体输出。

```
$O\_{i}^{5} = \\sum\\limits\_{i}\\overline{w\_{i}}f\_{i} = \\frac{\\sum\_{i}w\_{i}f\_{f}}{\\sum\_{i}w\_{i}}$
```

![si8\_e](images/B9780323852098000055/si8_e.png) (7)

## 5.2：测试阶段

在[图 9](#B9780323852098000055.xhtml#f0050)所示的测试阶段中，使用眼底相机从人眼中提取视网膜眼底图像。然后，利用基于数学形态学的边缘检测对人眼视网膜图像中的血管进行分割。接着，从分割后的图像中提取特征以执行测试。将提取的特征输入 ANFIS 训练模型，以判断给定图像是合法用户还是非法用户。

![图 9 ARBAS 测试阶段。](images/B9780323852098000055/f05-09-9780323852098.jpg)

图 9 ARBAS 测试阶段。

## 5.3：认证系统的性能指标

为了衡量生物识别认证系统的性能，准确率是衡量该系统成败最重要的因素之一。准确率是衡量系统准确匹配个体生物特征信息并避免错误匹配不同人员生物特征信息能力的指标。

为了评估使用生物识别技术的认证系统的性能并计算生物识别认证准确率，使用以下性能指标：

*   **真接受率**

    真接受率缩写为 `TAR`。也称为真匹配率（`TMR`）。它衡量生物识别认证系统正确接受授权用户访问尝试的概率。它表示授权人员实例被认证系统正确识别的百分比。为了使认证系统更成功，该指标必须最大化，计算方法见公式[(8)](#B9780323852098000055.xhtml#fo0050)。

```
$\\mathit{TAR} = \\frac{\\mathit{Number}\\mspace{6mu}\\mathit{of}\\mspace{6mu}\\mathit{authorized}\\mspace{6mu}\\mathit{user}\\mspace{6mu}\\mathit{instance}\\mspace{6mu}\\mathit{that}\\mspace{6mu}\\mathit{is}\\mspace{6mu}\\mathit{correctly}\\mspace{6mu}\\mathit{accepted}}{\\mathit{Total}\\mspace{6mu}\\mathit{number}\\mspace{6mu}\\mathit{of}\\mspace{6mu}\\mathit{authorised}\\mspace{6mu}\\mathit{user}\\mspace{6mu}\\mathit{instance}}$
```

![si9\_e](images/B9780323852098000055/si9_e.png) (8)

*   **真拒绝率**

    真拒绝率缩写为 `TRR`。也称为真非匹配率（`TNMR`）。它衡量生物识别认证系统正确拒绝未授权用户访问尝试的可能性。它表示未授权用户实例被认证系统正确拒绝的百分比。为了使认证系统更成功，该指标必须最大化，计算方法见公式[(9)](#B9780323852098000055.xhtml#fo0055)。

```
$\\mathit{TRR} = \\frac{\\mathit{Number}\\mspace{6mu}\\mathit{of}\\mspace{6mu}\\mathit{unauthorized}\\mspace{9mu}\\mathit{user}\\mspace{6mu}\\mathit{instance}\\mspace{6mu}\\mathit{that}\\mspace{6mu}\\mathit{is}\\mspace{6mu}\\mathit{correctly}\\mspace{6mu}\\mathit{rejected}}{\\mathit{Total}\\mspace{6mu}\\mathit{number}\\mspace{6mu}\\mathit{of}\\mspace{6mu}\\mathit{unauthorised}\\mspace{6mu}\\mathit{user}\\mspace{6mu}\\mathit{instance}}\\qquad$
```

![si10\_e](images/B9780323852098000055/si10_e.png) (9)

*   **假接受率**

    `FAR` 是假接受率的缩写。也称为欺诈率、假匹配率或第二类错误。它衡量生物识别认证系统错误接受未授权用户访问尝试的可能性。它表示未授权用户实例被认证系统错误接受的百分比。为了使认证系统更成功，该指标必须最小化。计算 `FAR` 的公式见公式[(10)](#B9780323852098000055.xhtml#fo0060)。

```
$\\mathit{FAR} = \\frac{\\mathit{Number}\\mspace{6mu}\\mathit{of}\\mspace{6mu}\\mathit{unauthorized}\\mspace{6mu}\\mathit{user}\\mspace{6mu}\\mathit{instance}\\mspace{6mu}\\mathit{that}\\mspace{6mu}\\mathit{is}\\mspace{6mu}\\mathit{incorrectly}\\mspace{6mu}\\mathit{accepted}}{\\mathit{Total}\\mspace{6mu}\\mathit{number}\\mspace{6mu}\\mathit{of}\\mspace{6mu}\\mathit{unauthorised}\\mspace{6mu}\\mathit{user}\\mspace{6mu}\\mathit{instance}}\\mspace{9mu}$
```

![si11\_e](images/B9780323852098000055/si11_e.png) (10)

*   **假拒绝率**

    `FRR` 是假拒绝率的缩写。也称为冒犯率、假非匹配率（`FNMR`）或第一类错误。它衡量生物识别认证系统错误拒绝授权用户访问尝试的概率。它表示授权用户实例被认证系统错误拒绝的百分比。为了使认证系统更成功，该指标必须最小化。计算 `FRR` 的公式见公式[(11)](#B9780323852098000055.xhtml#fo0065)。

```
$\\mathit{FRR} = \\frac{\\mathit{Number}\\mspace{6mu}\\mathit{of}\\mspace{6mu}\\mathit{authorized}\\mspace{6mu}\\mathit{user}\\mspace{6mu}\\mathit{instance}\\mspace{6mu}\\mathit{that}\\mspace{6mu}\\mathit{is}\\mspace{6mu}\\mathit{incorrectly}\\mspace{6mu}\\mathit{rejected}}{\\mathit{Total}\\mspace{6mu}\\mathit{number}\\mspace{6mu}\\mathit{of}\\mspace{6mu}\\mathit{authorised}\\mspace{6mu}\\mathit{user}\\mspace{6mu}\\mathit{instance}}\\mspace{45mu}$
```

![si12\_e](images/B9780323852098000055/si12_e.png) (11)

*   **等错误率**

    `EER` 是等错误率的缩写。它代表使用生物识别技术的认证系统的总体准确性。`EER` 值越低，使用生物识别技术的认证系统的准确性越高。当 `EER` 值与 `FRR` 和 `FAR` 相关联时，它们由 `FAR` 和 `FRR` 数值相等的点决定。也称为交叉错误率（`CER`）。

*   **FAR 和 FRR 如何相互影响？**

    [图 10](#B9780323852098000055.xhtml#f0055) 所示的图表展示了 `FAR` 和 `FRR` 如何相互影响。`FRR` 与 `FAR` 成反比，反之亦然。这可以通过一个称为置信阈值（有时称为灵敏度）的参数来控制。随着生物识别认证系统灵敏度值的增加（标记在图表的 X 轴上），`FAR` 将下降，同时 `FRR` 将上升。相反，当灵敏度值降低时，`FAR` 将上升，同时 `FRR` 将下降。`CER` 是图表中 `FAR` 曲线和 `FRR` 曲线相交的点，给出了使用生物识别技术的认证系统的总体准确性。为了提高使用生物识别技术的认证系统的准确性，可以增加灵敏度。

![图 10 FAR 与 FRR 对比。](images/B9780323852098000055/f05-10-9780323852098.jpg)

图 10 FAR 与 FRR 对比。

## 5.4：实验设置
