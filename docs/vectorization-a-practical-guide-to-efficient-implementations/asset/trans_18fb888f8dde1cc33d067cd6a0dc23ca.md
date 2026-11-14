

```python
tf.zeros((4,), dtype=tf.float32),
self.embedding.weights[0].numpy()[[6, 8, 9], :].max(axis=0),
tf.zeros((4,), dtype=tf.float32),
]
assert np.allclose(emb, emb2)
```

## 9.7 案例研究：受音符时长限制的声乐时长

歌声合成（SVS）是文本转语音（TTS）问题的延伸，其中歌词和音符从文本转换为人工歌唱声音。输入的音符决定了生成人声歌唱的节奏（即速度和时间），并为 SVS 模型提供上下文信息，以使合成的歌唱符合人声作品的音乐性。在我之前完成的一个 SVS 项目中，我的模型在音素级别（即一次一个音节）预测了每个声乐单元的时长。例如，“I saw you smiling at me. Was it real or just my fantasy” 变为 [“I,” “saw,” “you,” “smi,” “ling,” “at,” “me,” “was,” “it,” “real,” “or,” “just,” “my,” “fan,” “ta,” “sy”]（《Eyes on Me》来自《最终幻想 VIII》主题曲，演唱者：王菲；图 9.13），其中每个音节的时长由模型输出预测。然而，由于音乐的本质，歌手的声乐时长和时间需要与乐谱的节奏或有时背景音乐伴奏保持一致。也就是说，如果乐谱所示的节奏要求演唱者在 16 个拍内唱完一句歌词，那么演唱者演唱的所有音节的总时长不能超过或少于 16 个拍（允许一定的表达性灵活性）。因此，需要对音素的预测时长施加时序约束。解决这个问题的一个简单方法是预先确定

![](img/e891acaacd4fb5b80dab2ed824618203_351_0.png)

图 9.13 我之前 SVS 项目中的“Eyes On Me”乐谱。

| 片段 | I saw | you smiling | at me | Was it real or | just my | fantasy <rest> |
|------|-------|-------------|-------|----------------|---------|----------------|
| 帧数 | 300 | 300 | 525 | 450 | 300 | 525 |

| 片段 | You'd always | be there in the | corner | of this | tiny | little | bar <rest> |
|------|--------------|-----------------|-------|---------|------|--------|------------|
| 帧数 | 300 | 375 | 450 | 150 | 375 | 150 | 525 |

图 9.14 按组示例的音符时长约束。

小节的总音符时长（又称 bar，表示包含固定拍数的音乐片段，例如每小节四拍）。以 Eyes on Me 为例，我们假设每小节有四拍，速度为每分钟 80 拍。这意味着对于上面涵盖总共四小节的句子/歌词，我们需要确保整句歌词在 (4 拍/小节) × (4 小节)/(80 拍/分钟) = 12 秒内唱完。此外，在 TTS 和 SVS 建模任务中，将时间序列的时序单位表示为“帧”更为常见，其中每个帧表示固定的时间长度，例如 5 ms。这是因为将音频信号建模为时频域中的频谱图更为典型，其中每个帧对应用于执行傅里叶变换的时间窗。因此，12 秒对应 2400 帧，或每拍 150 帧。最后，我们可以根据音符时长定义更细粒度的按单词分组的时序约束。在我们的特定示例中，让我们定义以下六个分组（如图 9.14 顶部所示）：

- 1. “I saw,” 对应总共 2 拍或 300 帧。
- 2. “you smiling,” 对应 2 拍或 300 帧。
- 3. “at me,” 对应 3.5 拍或 525 帧。
- 4. “Was it real or,” 对应 3 拍或 450 帧。
- 5. “just my,” 对应 2 拍或 300 帧。
- 6. “fantasy <rest>,” 对应 3.5 拍或 525 帧。

以下代码块实现了一个函数，可根据预测的帧数和分组内的总时长约束，调整每个音节/单词的预测时长：

```python
import tensorflow as tf

def scatter_batch_2d(index, inputs, out=None, mode="add"):
    """Batch-wise scattering over a 2D matrix."""
    # Determines the length of each row for the output
    row_length = tf.cast(tf.reduce_max(index), tf.int32) + 1
    row_length = tf.maximum(tf.shape(inputs)[1], row_length)
    # start and end index of each row
    # row 0: inc[0]:inc[1], row 1: inc[1]:inc[2], ...
    inc = row_length * tf.range(tf.shape(inputs)[0]+1)
    # Compute flat indices for each element
    indices = tf.cast(index, inc.dtype) + tf.reshape(inc[:-1], (-1, 1))
    # Flatten to column vector
    indices = tf.reshape(indices, (-1, 1))
    # Flatten updates
    updates = tf.reshape(inputs, (-1,))
    if out is None: # create from zeros
        shape = (inc[-1], )
        out = tf.scatter_nd(indices, updates, shape)
    else:
        out = tf.reshape(out, (-1, ))
        if mode == "add":
            out = tf.tensor_scatter_nd_add(out, indices, updates)
        elif mode == "sub":
            out = tf.tensor_scatter_nd_sub(out, indices, updates)
        elif mode == "min":
            out = tf.tensor_scatter_nd_min(out, indices, updates)
        elif mode == "max":
            out = tf.tensor_scatter_nd_max(out, indices, updates)
        elif mode == "update":
            out = tf.tensor_scatter_nd_update(out, indices, updates)
    # reshape: (batch_size, row_length)
    out = tf.reshape(out, (tf.shape(index)[0], -1))

    return out

def apply_duration_constraints(dur_pred, dur_true, index, rounding):
    """
    Apply duration constraints for each phoneme.

    Inputs:
    * dur_pred: predicted duration of each phoneme.
    * dur_true: total duration within the grouping.
    * index: index to indicate which group each phoneme belongs to.
    """
    # Sum together total predicted duration within the group
    pred = scatter_batch_2d(index, dur_pred)
    # Broadcast the total values across all phonemes within the group
    pred = tf.gather(pred, index, axis=1, batch_dims=1)
    label = tf.gather(dur_true, index, axis=1, batch_dims=1)
    # Compute ratio: constraints / total
    ratio = tf.math.divide_no_nan(
        tf.cast(label, tf.float32), tf.cast(pred, tf.float32))
    # ratio = label / pred = dur_adj / dur_pred
    # dur_adj = dur_pred * (label / pred)
    dur_adj = ratio * tf.cast(dur_pred, tf.float32)
    # Rounding: will be off by at most 1 frame
    dur_adj = tf.cast(tf.round(dur_adj), dur_true.dtype)
    # Costly! Correct rounding error,
    # if 1 frame fewer, add 1 frame to the smallest duration
    # if 1 frame more, subtract 1 frame from the largest duration
    if rounding == "strict":
        # Compute grouping statistics and broadcast to phoneme level
        min_dur = tf.ones_like(dur_adj) * tf.reduce_max(dur_adj)
        min_dur = scatter_batch_2d(index, dur_adj, out=min_dur, mode="min")
        min_dur = tf.gather(min_dur, index, axis=1, batch_dims=1)
        max_dur = tf.zeros_like(dur_adj)
        max_dur = scatter_batch_2d(index, dur_adj, out=max_dur, mode="max")
        max_dur = tf.gather(max_dur, index, axis=1, batch_dims=1)
        total_adj = scatter_batch_2d(index, dur_adj)
        total_adj = tf.gather(total_adj, index, axis=1, batch_dims=1)
        # Adjust
        adjustment = label - total_adj
        cond_fewer = tf.math.logical_and(
            adjustment > 0, # missing 1 frame
            dur_adj == min_dur # need to adjust on min_dur
        )
        cond_more = tf.math.logical_and(
            adjustment < 0, # extra 1 frame
            dur_adj == max_dur # need to adjust on max_dur
        )
        # combine two conditions
        cond = tf.math.logical_or(cond_fewer, cond_more)
        dur_adj = tf.where(cond, dur_adj + adjustment, dur_adj)
    return dur_adj
```

- 第 3–35 行实现了函数 `scatter_batch_2d`。这是对第 3 章案例研究中我们实现的一个函数的修改。除了使用 `tf.scatter_nd` 进行散射外，我们还使用 `tf.tensor_scatter_nd*` 添加了额外的累积模式，包括 "add"、"sub"、"min"、"max" 和 "update"。

- 第 48 行：这将相同分组内的预测时长累积（求和）在一起。例如，给定分组索引 = [0, 0, 1, 1, 1] 和 dur_pred = [1, 2, 3, 4, 5]，结果为 pred = [1+2, 3+4+5] = [3, 12]。

- 第 50 行：这将分组内的时长总和广播回各个音节。遵循上一步的示例，pred = [3, 12] 现在根据分组索引 = [0, 0, 1, 1, 1] 广播回每个音节，变为 [3, 3, 12, 12, 12]。

- 第 51 行：这也将每个组的总时长约束 dur_true 广播到每个音节。pred 和 label 应具有相同的长度。

- 第 53–58 行：计算比率，然后调整预测时长。由于我们假设组间预测时长与时长

