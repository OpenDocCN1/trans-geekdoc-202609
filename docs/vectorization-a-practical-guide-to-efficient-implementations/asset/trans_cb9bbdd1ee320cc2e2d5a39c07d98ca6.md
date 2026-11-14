

```python
tf.reduce_max(tf.reduce_sum(mask, axis=1)), tf.int64
)
output = output[:, :tight_size, :]
mask = mask[:, :tight_size, :]

return output, mask

@property
def model(self):
    text_embeddings = Input((None, self.num_channels), tf.float32)
    spect_durations = Input((None,), dtype=tf.float32)
    model = Model(
        inputs=[text_embeddings, spect_durations],
        outputs=self.call(
            text_embeddings, spect_durations, training=False
        ),
    )
    return model
```

- __init__ **方法**: 初始化层子类
  - num_channels 存储嵌入维度大小，因为在后续的 call 方法中，我们需要重塑嵌入张量。确实也可以从输入中动态确定嵌入维度大小。
  - max_len 存储最大音频序列长度。如果用户指定了大于零的值，则输出将具有该序列长度，而不是从输入中动态确定。
- call 方法实现了 Length Regulator 模块的主要逻辑，给定一批标记序列嵌入，以及每个标记发音的时长（以 mel-频谱图帧数为单位）。
  - token_embedding 的形状为 [batch_size, seq_len, num_channels]，数据类型为 tf.float32。填充标记应对应值为 0 的嵌入向量。
  - spect_durations 的形状为 [batch_size, seq_len]。填充标记的时长为 0。
  - 第 44 行首先将时长四舍五入为整数。这是因为在推理时，FastSpeech2 模型的另一个模块也会预测标记的时长，而该时长不一定是整数。这一行确保在后续操作中，我们处理的是以整数表示的 mel-频谱图帧数。
  - 第 45 行和第 46 行计算每个标记嵌入需要重复多少次。这同样是推理时的考量：我们需要将序列中的任何标记至少重复一次。在推理时，我们会遇到两种时长可能为 0 的场景：
    1. 发音时长被预测为较短，因此在推理时被四舍五入为 0 时长。
    2. 我们正在处理序列末尾的填充。在这种情况下，填充标记的嵌入向量值应全为零。即使我们保留这些零填充，模型也应该能够学会不在其上生成任何音频。在 call 函数末尾，我们将进行额外的清理以移除这些填充。
  - 第 49–52 行存储一些形状，我们将稍后利用这些形状来重塑输入。这还包括预先计算音频的预期时长（max_durations）。
  - 第 54–56 行将一批标记序列嵌入重塑为形状 [batch_size x seq_len, num_channels]。这将 3D 张量转换为嵌入向量堆栈，随后我们将使用 tf.repeat 操作来重复/上采样这些向量。
  - 第 57 行将一批时长重塑为一维数组 [batch_size x seq_len]。这个新数组将指示 hidden_states（第 54–56 行）中的每个嵌入向量部分需要重复多少次。
  - 第 60 行执行平铺/重复操作。我们现在应该拥有一个形状为 [batch_size x time_len, num_channels] 的嵌入向量堆栈。
  - 第 63–73 行实现了散射逻辑，以将重复的嵌入向量堆栈重塑回形状 [batch_size, time_len, num_channels]。由于我们的重复嵌入向量组织为形状 [batch_size x time_len, num_channels]，我们需要重塑第一个维度并将其拆分为两个独立的维度，即 [batch_size, time_len]。由于这是一个 2D 矩阵，此处我们使用术语 row 表示批次维度，col 表示 time_len：
    - row_indices：这是批次维度的索引。它通过两个 tf.repeat 操作步骤构建。我们首先构建批次索引 [0, 1, ..., batch_size]。然后我们将每个批次索引按序列长度重复。这样，我们为每个标记嵌入分配一个批次索引，结果变为 [0, 0, ..., 1, 1, ..., batch_size, batch_size, ...]。最后，由于每个标记嵌入向量被重复 duration 次（第 60 行），我们也按相应次数对每个标记重复批次索引。这应该使我们得到一个数组，其长度与第 60 行获得的 hidden_states 的第二个维度（axis=1）相同。
    - col_indices：这是时间维度的索引，由我们的辅助函数 tf_ragged_range 构建。对于每个批次，我们逐个枚举向量，分配索引 [ 0, 1, 2, 3, ..., batch_0_duration, 0, 1, 2, 3, ..., batch_1_duration, ...]。我们之前计算的 batch_duration 变量告诉我们当前序列应该有多少帧。
  - 第 68-73 行利用我们计算的索引重新创建形状为 [batch_size, time_len, num_channels] 的张量。散射操作会自动保留零填充，以适应可变长度序列的表示。
  - 第 75-89 行实现了相同的散射逻辑，只不过现在作用于形状为 [batch_size, time_len, 1] 的张量。
  - 第 92-94 行移除 spect_durations 指示的预期时长之外的任何多余填充零。
- model 属性：我经常实现此方法以快速单元测试我的层实现。初始化层后，我会执行 print(layer.model.summary()) 来打印层摘要供我检查。如果抛出错误，那么即使我们已验证模型在 eager 模式下可以生成输出，该 Tensorflow/Keras 模型在图模式下也很可能无法训练。以下是 LengthRegulator 层摘要的输出：

模型: "model_8"

| 层 (类型) | 输出形状 | 参数数 | 连接到 |
|---|---|---|---|
| input_24 (InputLayer) | [(None,None)] | 0 | [] |
| tf.math.round_11 (TFOpLambda) | (None, None) | 0 | ['input_24[0][0]'] |
| tf.cast_47 (TFOpLambda) | (None, None) | 0 | ['tf.math.round_11[0][0]'] |
| tf.math.reduce_sum_36 (TFOpLambda) | (None,) | 0 | ['tf.cast_47[0][0]'] |
| tf.math.maximum_22 (TFOpLambda) | (None, None) | 0 | ['tf.cast_47[0][0]'] |
| tf.cast_50 (TFOpLambda) | (None,) | 0 | ['tf.math.reduce_sum_36[0][0]'] |
| tf.cast_48 (TFOpLambda) | (None, None) | 0 | ['tf.math.maximum_22[0][0]'] |
| tf.math.reduce_max_39 (TFOpLambda) | () | 0 | ['tf.cast_50[0][0]'] |
| tf.math.reduce_sum_35 (TFOpLambda) | (None,) | 0 | ['tf.cast_48[0][0]'] |
| tf.range_40 (TFOpLambda) | (None,) | 0 | ['tf.math.reduce_max_39[0][0]'] |
| tf.cast_49 (TFOpLambda) | (None,) | 0 | ['tf.math.reduce_sum_35[0][0]'] |
| tf.expand_dims_38 (TFOpLambda) | (1, None) | 0 | ['tf.range_40[0][0]'] |
| tf.expand_dims_39 (TFOpLambda) | (None, 1) | 0 | ['tf.cast_50[0][0]'] |
| input_23 (InputLayer) | [(None, None, 256)] | 0 | [] |
| tf.math.reduce_max_38 (TFOpLambda) | () | 0 | ['tf.cast_49[0][0]'] |
| tf.math.greater_equal_19 (TFOpLambda) | (None, None) | 0 | ['tf.expand_dims_38[0][0]', 'tf.expand_dims_39[0][0]'] |
| tf.compat.v1.shape_22 (TFOpLambda) | (3,) | 0 | ['input_23[0][0]'] |
| tf.range_38 (TFOpLambda) | (None,) | 0 | ['tf.math.reduce_max_38[0][0]'] |
| tf.where_19 (TFOpLambda) | (None, None) | 0 | ['tf.math.greater_equal_19[0][0]', 'tf.expand_dims_38[0][0]'] |
| tf.__operators__.getitem_38 (SlicingOpLambda) | () | 0 | ['tf.compat.v1.shape_22[0][0]'] |
| tf.expand_dims_36 (TFOpLambda) | (1, None) | 0 | ['tf.range_38[0][0]'] |
| tf.expand_dims_37 (TFOpLambda) | (None, 1) | 0 | ['tf.cast_49[0][0]'] |
| tf.reshape_74 (TFOpLambda) | (None,) | 0 | ['tf.where_19[0][0]'] |
| tf.math.greater_equal_18 (TFOpLambda) | (None, None) | 0 | ['tf.expand_dims_36[0][0]', 'tf.expand_dims_37[0][0]'] |
| tf.range_39 (TFOpLambda) | (None,) | 0 | ['tf.__operators__.getitem_38[0][0]'] |
| tf.__operators__.ne_17 (TFOpLambda) | (None,) | 0 | ['tf.reshape_74[0][0]'] |
| tf.compat.v1.shape_23 (TFOpLambda) | (2,) | 0 | ['tf.cast_48[0][0]'] |
| tf.where_18 (TFOpLambda) | (None, None) | 0 | ['tf.math.greater_equal_18[0][0]', 'tf.expand_dims_36[0][0]'] |
| tf.math.reduce_max_37 (TFOpLambda) | () | 0 | ['tf.math.reduce_sum_35[0][0]'] |
| tf.repeat_44 (TFOpLambda) | (None,) | 0 | ['tf.range_39[0][0]', 'tf.math.reduce_sum_36[0][0]'] |
| tf.compat.v1.boolean_mask_17 (SlicingOpLambda) | (None,) | 0 | ['tf.reshape_74[0][0]', 'tf.__operators__.ne_17[0][0]'] |
| tf.math.reduce_sum_37 (TFOpLambda) | () | 0 | ['tf.math.reduce_sum_36[0][0]'] |
| tf.range_37 (TFOpLambda) | (None,) | 0 | ['tf.__operators__.getitem_38[0][0]'] |
| tf.__operators__.getitem_39 (SlicingOpLambda) | () | 0 | ['tf.compat.v1.shape_23[0][0]'] |
| tf.reshape_72 (TFOpLambda) | (None,) | 0 | ['tf.where_18[0][0]'] |
| tf.math.maximum_23 (TFOpLambda) | () | 0 | ['tf.math.reduce_max_37[0][0]'] |
| tf.stack_17 (TFOpLambda) | (None, 2) | 0 | ['tf.repeat_44[0][0]', 'tf.compat.v1.boolean_mask_17[0][0]'] |
| tf.ones_8 (TFOpLambda) | (None, 1) | 0 | ['tf.math.reduce_sum_37[0][0]'] |
| tf.repeat_42 (TFOpLambda) | (None,) | 0 | ['tf.range_37[0][0]', 'tf.__operators__.getitem_39[0][0]'] |
| tf.reshape_69 (TFOpLambda) | (None,) | 0 | ['tf.cast_48[0][0]'] |

