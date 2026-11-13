# 13.2.3 TPU training

Beyond just GPUs, there is a trend in the deep learning world toward moving work-
flows to increasingly specialized hardware designed specifically for deep learning
workflows (such single-purpose chips are known as ASICs, application-specific inte-
grated circuits). Various companies big and small are working on new chips, but today
the most prominent effort along these lines is Google's Tensor Processing Unit
(TPU), which is available on Google Cloud and via Google Colab.

Training on a TPU does involve jumping through some hoops, but it's worth the
extra work: TPUs are really fast. Training on a TPU V2 will typically be 15x
faster than training an NVIDIA P100 GPU. For most models, TPU training ends up
being 3x more cost-effective than GPU training on average.

# USING A TPU VIA GOOGLE COLAB

You can actually use an 8-core TPU for free in Colab. In the Colab menu, under the
Runtime tab, in the Change Runtime Type option, you'll notice that you have access
to a TPU runtime in addition to the GPU runtime.

When you're using the GPU runtime, your models have direct access to the GPU
without you needing to do anything special. This isn't true for the TPU runtime;
there's an extra step you need to take before you can start building a model: you need
to connect to the TPU cluster.

It works like this:

```
import tensorflow as tf
tpu = tf.distribute.cluster_resolver.TPUClusterResolver.connect()
print("Device:", tpu.master())
```

You don't have to worry too much about what this does—it's just a little incantation
that connects your notebook runtime to the device. Open Sesame.

Much like in the case of multi-GPU training, using the TPU requires you to open a
distribution strategy scope—in this case, a TPUStrategy scope. TPUStrategy follows
the same distribution template as MirroredStrategy—the model is replicated once
per TPU core, and the replicas are kept in sync.

Here's a simple example.

```
Listing 13.4 Building a model in a TPUStrategy scope
from tensorflow import keras
from tensorflow.keras import layers

strategy = tf.distribute.TPUStrategy(tpu)
print(f"Number of replicas: {strategy.num_replicas_in_sync}")

def build_model(input_size):
    inputs = keras.Input((input_size, input_size, 3))
    x = keras.applications.resnet.preprocess_input(inputs)
    x = keras.applications.resnet.ResNet50(
        weights=None, include_top=False, pooling="max") (x)
```