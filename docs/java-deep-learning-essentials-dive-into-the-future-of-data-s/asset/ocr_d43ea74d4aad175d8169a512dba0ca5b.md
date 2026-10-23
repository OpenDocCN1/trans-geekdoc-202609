Caffe is a very powerful library that enables quick model building, training, and testing; however, it's a bit difficult to install the library to get a lot of benefits from it. As you can see from the installation guide at http://caffe.berkeleyvision.org/installation.html, you need to install the following in advance:

+   - CUDA
+   - BLAS (ATLAS, MKL, or OpenBLAS)
+   - OpenCV
+   - Boost
+   - Others: snappy, leveldb, gflags, glog, szip, lmdb, protobuf, and hdf5

Then, clone the repository from the GitHub page and create the Makefile.config file from Makefile.config.example. You may need Anaconda, a Python distribution, beforehand to run the make command. You can download this from https://www.continuum.io/downloads. After you run the make, make test, and make runtest commands (you may want to run the commands with a -jN option such as make -j4 or make -j8 to speed up the process) and pass the test, you'll see the power of Caffe. So, let's look at an example. Go to $CAFFE_ROOT, the path where you cloned the repository, and type the following commands:

```
```
$ ./data/mnist/get_mnist.sh
$ ./examples/mnist/train_lenet.sh
```
```

That's all you need to solve the standard MNIST classification problem with CNN. So, what happened here? When you have a look at train_lenet.sh, you will see the following:

```
```
#!/usr/bin/env sh

./build/tools/caffe train --solver=examples/mnist/lenet_solver.prototxt
```
```