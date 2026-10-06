```
library(tensorflow)
tf$constant("Hello World")
# tf.Tensor(b'Hello World', shape=(), dtype=string)
```

The first time in a session you run TensorFlow related code with the CPU version, you may get warning messages like the following, which can safely ignore.

```
# tensorflow/stream_executor/platform/default/dso_loader.cc:55
# Could not load dynamic library 'cudart64_101.dll'
# dlerror: cudart64_101.dll not found
```

If you want to install the GPU version, first, you need to make sure you have a compatible video card. More information on how to install the GPU version is available here https://keras.rstudio.com/reference/install_keras.html and here https://tensorflow.rstudio.com/installation/gpu/local_gpu/