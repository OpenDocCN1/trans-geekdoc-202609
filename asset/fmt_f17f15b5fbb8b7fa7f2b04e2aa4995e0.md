
你保存的模型在 iOS App 中使用是可以接受的，但你始终应该考虑考虑另外一个更简单的步骤。对于应用程序来说，下载大小至关重要。你的模型以 32 位浮点数存储权重和偏置，但如果你将它们全部转换为 16 位，性能上不会损失太大。这会让你的模型下载大小减半，这非常棒，尤其是当你开始制作比本章中制作的模型更大的模型时。

运行以下代码进行调用，定义一个你可以使用的函数，用于将 Core ML 模型从 32 位转换为 16 位浮点数：

```
convert_to_fp16(model_filename):
    basename = model_filename[:-len("model")]
    spec = coremltools.utils.load_spec(model_filename)

    spec_16bit = coremltools.utils.
        convert_neural_network_weights_to_fp16(spec)
    coremltools.utils.save_spec(
        spec_16bit, f"{basename}16Bit.mlmodel")
```

这利用了 `coremltools` 中的函数来加载现有 ML 模型，将其权重转换为 16 位浮点数，然后将新版本保存到磁盘。它派生了一个文件名，因此不会覆盖原始模型。

现在，为每个模型调用该函数以创建 16 位版本：

```
convert_to_fp16("Es2EnCharEncoder.mlmodel")
convert_to_fp16("Es2EnCharDecoder.mlmodel")
```

如果一切运行正常，你现在在 notebooks 文件夹中应该会有四个模型文件：`Es2EnCharEncoder16bit.mlmodel`、`Es2EnCharDecoder.mlmodel`、`Es2EnCharEncoder16Bit.mlmodel` 和 `Es2EnCharDecoder16Bit.mlmodel`。保留两个版本很好，以防你想比较它们的性能，但本章的其余部分将使用 16 位权重的模型。

最后一点：当你在 iOS App 中使用模型时，你需要执行与在此处相同的独热编码，将输入序列从西班牙语字符转换为编码器期望的整数，然后将解码器的数值输出转换为英语字符。

为了确保使用正确的值，请运行以下代码来保存你一直使用的字典：

![](img/5720be5c3cca252e12448e68d25607b5_511_0.png)

```
import json
with open("EsCharToInt.json", "w") as f:
    json.dump(in_token2int, f)
with open("intToEnchar.json", "w") as f:
    json.dump(out_int2token, f)
```

使用 Python 的 `json` 包，你将 `in_token2int` 和 `out_int2token` 保存为 JSON 文件。在下一节中，你将在 iOS App 中使用这些文件以及编码器和解码器模型的 ML 版本。

# 在 iOS 中使用你的模型

本章的大部分内容关于理解和构建用于翻译自然语言的序列到序列模型。那是困难的部分——现在你需要编写一些代码在 iOS 中使用你训练好的模型。然而，有一些细节可能会引起困惑，所以先不要停止关注！

你将继续完成上一章的项目，因此请在 Xcode 中打开它。如果你跳过了那一章，可以使用本章资源中的 SMDB 启动项目。

将你的 Core ML 模型文件——`Es2EncharEncoder16Bit.model` 和 `Es2EnDecoder16Bit.model` 拖入 Xcode 以将它们添加到 SMDB 项目中。或者，如果你倾向于使用更大的版本，请使用名称相同但去掉“16Bit”的模型。请记住，如果你选择不使用 16 位版本，你需要从任何包含它的代码指令删除删除16Bit。

在项目导航器（Project Navigator）中选择 `Es2EncharEncoder16Bit.model` 以查看有关编码器的详情。你会看到以下内容，这会让你想起在序列分类章节中看到的模型。

## 机器学习模型

| | |

|---|---|

| 名称 | Es2EnCharEncoder16Bit |

| 类型 | 神经网络 |

| 大小 | 734 KB |

| 作者 | unknown |

| 描述 | 未包含描述 |

| 许可证 | unknown |

## 模型类

- `Es2EnCharEncoder16Bit`
  - 自动生成的 Swift 模型类

## 模型评估参数

| 名称 | 类型 | 描述 |

|---|---|---|

| 输入 | | |

| encodedSeq | MultiArray (Double 101) | |

| encoder_lstm_in | MultiArray (Double 256)? | |

| encoder_lstm_c_in | MultiArray (Double 256)? | |

| 输出 | | |

| ignored | MultiArray (Double 256) | |

| encoder_lstm_h_out | MultiArray (Double 256) | |

| encoder_lstm_c_out | MultiArray (Double 256) | |

## 查看编码器 mlmodel 文件

如你所示，摘要包含了 `encodedSeq`、`encoder_lstm_in`、`encoder_lstm_c_in`、`ignored`、`encoder_lstm_h_out` 和 `encoder_lstm_c_out`。这是编码器的摘要。

最重要的是 `encodedSeq`，它是一个 Double 101 的 `MultiArray`。`encoder_lstm_in` 和 `encoder_lstm_c_in` 是 Double 256 的 `MultiArray`，并且是可选的。`ignored`、`encoder_lstm_h_out` 和 `encoder_lstm_c_out` 都是 Double 256 的 `MultiArray`。

在项目导航器中选择 `Es2EncharEncoder16Bit.model` 以查看关于编码器的详情。

### 机器学习

## 第 15 章：自然语言转换，第一部分

移除所有内容。

- 2. 然后，你使用 `Util.swift` 提供的辅助函数 `initMultiArray` 来创建一个填充了值的 `MLMultiArray`。注意这些维度：第一个是序列的长度——即你编码了多少个字符。第二个始终为一；这个维度的存在是 Core ML 专注于计算机视觉设计的副作用。它不会影响你分配的空间，但如果没有它，你的应用程序将会崩溃。第三个维度是输入词表的大小，因为每个字符都需要被独热编码（one-hot encoded）为指定长度的向量。

- 3. 最后，遍历清理后的文本并在数组中设置相应的项。使用这个多维 `MLMultiArray`，因为它是一个标准的平坦数组，它的内存就是这样排列的。记住它是被 0 填充的，所以你只需要担心把 1 放进去，最终就能得到正确的独热编码向量。

编码器的输入到此为止。现在添加另一个函数，这次用于处理编码后的输入并为你的解码器生成初始输入：

```swift
func getDecoderInput(encoderInput: MLMultiArray) -> Es2EncharDecoder16BitInput {
  // 1
  let encoder = Es2EncharEncoder16Bit()
  let encoderOut = try! encoder.prediction(
    encodedSeq,
    encoder_lstm_in: nil, encoder_lstm_c_in: nil)
  // 2
  let decoderIn = initMultiArray(
    shape: [NSNumber(value: intToEnchar.count)])
  // 3
  return Es2EncharDecoder16BitInput(
    encodedChar: decoderIn,
    decoder_lstm_h_in: encoderOut.encoder_lstm_h,
    decoder_lstm_c: encoderOut.encoder_lstm_c)
}
```

这是该函数生成你传递给解码器模型的方式：

- 1. 首先，创建你的编码器模型并将 `encoderInput` 传递给它的预测函数。这返回一个 `Es2EncharEncoder16BitOutput` 对象，其中包含了编码器处理输入序列后的最后一个状态。

- 2. 你创建一个填充了 0 的 `MLMultiArray`，大小足够容纳一个独热编码的字符。注意 `intToEnchar.count`，因为解码器的词表与编码器不同。目前先保持它全为 0。

- 3. 最后，创建并返回一个 `Es2EncharDecoder16BitInput` 对象，使用你刚刚构建的空 `MLMultiArray` 作为 `encodedChar` 字段的存储。

![](img/5720be5c3cca252e12448e68d25607b5_516_0.png)

你将为传递给解码器的每个字符复用这个对象，但现在将其初始输入状态设置为来自 `encoderOut` 的状态。记住，这就是你之前在 Jupyter notebook 中做的操作：将输入文本传递给解码器，并使用编码器的输出作为解码器的初始 `h` 和 `c` 状态。

在编写翻译逻辑的核心之前，在 `NLPHelper.swift` 中添加以下常量：

```swift
let maxOutSeqLen = 87
let startTokenIdx = 0
let stopTokenIdx = 1
```

这些是在 Jupyter notebook 中为同名常量找到的值。快速回顾一下：

- `maxOutSeqLen`: 定义翻译的最大长度。如果解码器生成了许多 token 但没有预测出 STOP token，你将停止以避免无限循环。

- `startTokenIdx`: `intToEnChar` 中 START token 的整型值。用于独热编码。

- `stopTokenIdx`: `intToEnChar` 中 STOP token 的整型值。用于独热编码。

`project.swift` 已经包含一个名为 `spanishToEnglish` 的空函数，你将在其中整合目前添加的所有内容来翻译诗句。这段逻辑本质上是复制了你之前在 Python 中编写的 `translate_sequence` 函数，但我们稍后会讨论细节。

在函数开头添加以下代码：

```swift
// 1
guard let encoderIn = getEncoderInput(text) else {
    return nil
}
// 2
let decoderIn = getDecoderInput(encoder: encoderIn)
// 3
let decoder = Es2EnCharDecoder16Bit()
var translatedText = [Character]()
var doneDecoding = false
var decodedIdx = startTokenIdx
```

以下是你目前为止所做的工作：

![](img/5720be5c3cca252e12448e68d25607b5_517_0.png)

- 1. 首先，你调用 `getEncoderInput` 对输入文本进行独热编码，如果失败则退出函数。

- 2. 使用 `getDecoderInput` 和 `encoderIn` 为解码器创建初始输入。

- 3. 然后你创建了解码器模型，以及一些你将用于跟踪翻译进度的变量。注意你将 `decodedIdx` 初始化为 START token 的索引。

现在在 `spanishToEnglish` 内部，在你刚刚添加的内容之后、`return` 语句之前添加以下代码：

```swift
while !doneDecoding {
  // 1
  decoderIn.encodedChar[decodedIdx] = 1
  // 2
  let decoderOut = try! decoder.prediction(input: decoderIn)
  // 3
  decoderIn.decoder_lstm_h = decoderOut.decoder_lstm_h
  decoderIn.decoder_lstm_c = decoderOut.decoder_lstm_c
  // 4
  decodedIdx = argmax(decoderOut.nextProbs)
  if decodedIdx == stopTokenIdx {
    doneDecoding = true
  } else {
    translatedText.append(intToEnchar[decodedIdx]!)
  }
  if translatedText.count >= maxOutSeqLen {
    doneDecoding = true
  }
}
```
