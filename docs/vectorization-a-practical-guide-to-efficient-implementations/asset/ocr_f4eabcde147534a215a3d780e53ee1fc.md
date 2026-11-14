```
import tensorflow as tf
# 6 valid values total
x = tf.ragged.constant([[1, 3], [2], [], [6, 8, 9], []]).to_sparse()
# After embedding lookup, we have a matrix of (7, 8)
emb = tf.random.uniform((len(x.values), 8))
# Summarized correctly: (5, 8)
emb_sum_correct = tf.sparse.segment_sum(
    emb, x.indices[:, 1], x.indices[:, 0], num_segments=tf.shape(x)[0]
)
# Summarized incorrect: (4, 8)
emb_sum_wrong = tf.sparse.segment_sum(
    emb, x.indices[:, 1], x.indices[:, 0]
)
# Summarized wrong using tf.math.segment_max: (4, 8)
emb_max_wrong = tf.math.segment_max(
    emb, x.indices[:, 0]
)
# Need to pad the empty entries occurring at the end
pad_size = tf.shape(x)[0] - tf.shape(emb_max_wrong)[0]
emb_max_correct = tf.pad(emb_max_wrong, [[0, pad_size], (0, 0)])
```

+   • model property (Lines 86–96): This property is used to check if our implementation can be compiled as a graph. We can print the model architecture using print(layer.model.summary()) which gives us the following:

| Layer (type) | Output Shape | Param # | Connected to |
|---|---|---|---|
| items (InputLayer) | [(None, None)] | 0 | [] |
| weights (InputLayer) | [(None, None)] | 0 | [] |
| input.values_6 (InstanceProperty) | (None,) | 0 | ['items[0][0]' ] |
| input.values_7 (InstanceProperty) | (None,) | 0 | ['weights[0][0]' ] |
| embedding_16 (Embedding) | (None, 4) | 4000 | ['input.values_6[0][0]' ] |
| tf.__operators__ .getitem_12 (SlicingOpLambda) | (None, 1) | 0 | ['input.values_7[0][0]' ] |
| input.indices_3 (InstanceProperty) | (None, 2) | 0 | ['items[0][0]' ] |