tf.math.reduce_max_39 ()
(TFOpLambda) 0 ['tf.cast_50[0][0]']
tf.math.reduce_sum_35 (None,)
(TFOpLambda) 0 ['tf.cast_48[0][0]']
tf.range_40
(None,) 0 ['tf.math.reduce_max_39[0][0]']
(TFOpLambda)
tf.cast_49
(None,) 0 ['tf.math.reduce_sum_35[0][0]']
(TFOpLambda)
tf.expand_dims_38
(1, None) 0 ['tf.range_40[0][0]']
(TFOpLambda)
tf.expand_dims_39
(None, 1) 0 ['tf.cast_50[0][0]']
(TFOpLambda)
input_23
[ (None, None, 256) ]
(InputLayer) []
tf.math.reduce_max_38 ()
0 ['tf.cast_49[0][0]']
(TFOpLambda)
tf.math.greater_equal_19
(None, None) 0 ['tf.expand_dims_38[0][0]',
'tf.expand_dims_39[0][0]']
(TFOpLambda)
tf.compat.v1.shape_22
(3,) 0 ['input_23[0][0]']
(TFOpLambda)
tf.range_38
(None,) 0 ['tf.math.reduce_max_38[0][0]']
(TFOpLambda)
tf.where_19
(None, None) 0 ['tf.math.greater_equal_19[0]
[0]', 'tf.expand_dims_38[0][0]']
(TFOpLambda)
tf.__operators__.
getitem_38
() 0 ['tf.compat.v1.shape_22[0][0]']
(SlicingOpLambda)
tf.expand_dims_36
(1, None) 0 ['tf.range_38[0][0]']
(TFOpLambda)
tf.expand_dims_37
(None, 1) 0 ['tf.cast_49[0][0]']
(TFOpLambda)
tf.reshape_74
(None,) 0 ['tf.where_19[0][0]']
(TFOpLambda)
tf.math.
greater_equal_18
(None, None) 0 ['tf.expand_dims_36[0][0]',
'tf.expand_dims_37[0][0]']
(TFOpLambda)