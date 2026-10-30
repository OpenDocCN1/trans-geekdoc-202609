```
tf.feature_column.categorical_column_with_vocabulary_list(col,
list(xTrain[col].unique()))) 
return ret
```

The following is an input function for providing the input to a model from

```
def tfexamples_input_fn(examples, feature_spec, label,
mode=tf.estimator.ModeKeys.EVAL,
num_epochs=None, batch_size=64):
def ex_generator():
for i in range(len(examples)):
yield examples[i].SerializeToString()
dataset = tf.data.Dataset.from_generator(
ex_generator, tf.dtypes.string, tf.TensorShape([]))
if mode == tf.estimator.ModeKeys.TRAIN:
dataset = dataset.shuffle(buffer_size=2 * batch_size + 1)
dataset = dataset.batch(batch_size)
dataset = dataset.map(lambda tf_example:
parse_tf_example(tf_example, label, feature_spec))
dataset = dataset.repeat(num_epochs)
return dataset
```

Next, we will parse Tf.Example protos into the features for the input function.

```
def parse_tf_example(example_proto, label, feature_spec):
parsed_features = tf.io.parse_example(serialized=example_proto,
features=feature_spec)
target = parsed_features.pop(label)
```