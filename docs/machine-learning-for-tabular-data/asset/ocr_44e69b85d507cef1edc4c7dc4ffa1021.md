# CHAPTER 6 Advanced feature processing methods

Using a GPU with XGBoost, it becomes a little bit trickier with LightGBM. LightGBM doesn't have an option for GPU running but rather requires a special version of itself to be compiled for the purpose. Depending on your operating system (Windows, Linux/Ubuntu, MacOS), the compilation may be less or more challenging. Instructions are available at https://mg.bz/nk5 for POSIX systems and at https://mg.bz/vK8p for Windows systems. However, if you are any prerequisites ready on your system stated by the instructions at https://mg.bz/4ljag, you can just require to directly install it using the pip instruction on your shell or command prompt:

```
pip install lightgbm --install-option=--gpu
```

Once everything has been installed, you need to set the parameter device to GPU not except astonishing performance improvements. However, as by LightGBM authors (see https://mg.bz/vK8p), the best results are obtained on large-scale and dense datasets because of the inefficient data turnover that causes latencies working on smaller datasets. In addition, setting a lower number of bins for the histogram algorithm will make the GPU work more efficiently with the LightGBM. The suggestion is to set max_bin=15 and single precision, gpu_use_dp=false, for the best performances.

GPUs are quite useful for speeding up training, there are more options for prediction time. With tree structures readily available, as we have seen in the previous section, it has been possible for specific projects to use such information for rebuilding prediction trees using more programming languages as C, JAVA, or LLVM that can turn your model into pure assemble code. Such tree-compressing projects aim for fast prediction and easier deployment. Examples are Treelite (https://github.com/dmlc/treelite), which can read models produced by XGBoost, LightGBM, and Scikit-learn, and leaves (https://github.com/siboehm/leaves), which is a project for LightGBM only.

Starting from Treelite, this project serves to be a universal model exchange and serialization format for decision forests. It compiles your GBDT to C or Java with the least possible dependencies, so you can easily deploy it into any system. To have it tested, you must install a few packages at the command line: pip install tl2cgen

Listing 6.18 XGBoost prediction speedup by Treelite

```
import treelite
import treelite_runtime
import tl2cgen

xgb = XGBClassifier(booster='gtree',
                      objective='reg:logistic',
                      n_estimators=10,
                      max_depth=3)
```