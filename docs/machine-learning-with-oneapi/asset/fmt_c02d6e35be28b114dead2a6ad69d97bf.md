
The recent advances in Deep Neural Networks (DNNs) have elevated the accuracy of computer vision algorithms to a higher level. Nevertheless, deploying and producing such accurate and useful models need adaptations for the computational methods as well as the hardware. `OpenVINO` allows optimization of the DNN model to be a streamlined, efficient process by way of integrating various tools. The `OpenVINO` toolkit is based on the latest generations of Artificial Neural Networks (ANN), such as CNN, as well as recurrent and attention-based networks.

The `OpenVINO` toolkit maximizes the performance and accelerates application development by employing a library of predetermined functions, as well as pre-optimized kernels. Also, the other computer vision tools, such as `OpenCV` (Open Source Computer Vision Library), `OpenCL` Kernels etc., are included in the `OpenVINO` toolkit. `OpenCL`™ (Open Computing Language) is a low-level API for heterogeneous computing that runs on GPUs.

## 12.2.2 Benefits of OpenVINO

The benefits include:
* Accelerating performance by enabling simple execution methods across different Intel processors and accelerators, such as `CPU`, `GPU`/Intel Processor Graphics, `VPU` (Vector Processing unit) and `FPGA`.
* Streamlining Deep Learning (`DL`) deployment by way of providing one centralized method for implementing dozens of `DL` models.
* Customizing `DL` model layers without the burden of framework overheads, implementing parallel programming of various accelerators.
* Allowing users to extend artificial intelligence (`AI`) within private applications.
* Optimizing `AI` all the way to the cloud with processes such as the `Model Optimizer`, `Intermediate Representation`, `nGraph` Integration and more.
* `nGraph` Library is an open-source C++ library and runtime / compiler suite for `DL` networks. This facilitates usage of preferred deep learning frameworks on any number of hardware architectures, for both training and inference.

## 12.2.3 What Is the Recent Version?

The recent version is the 2022.3 LTS (Long-Term Support) and it comes with excellent features. This makes it very easy for developers to innovate. The new release powers developers with more performance-oriented developments, many deeper learning models, enhanced device portability and, more importantly, improved inferencing performance with very limited code changes.

The recent version provides the developers with:
1. a. Broader Model and Hardware Support.
2. b. Expanded Model Coverage.
3. c. Improved API and More Integrations.

`OpenVINO` is cool and one can understand the cycle of innovation with `OpenVINO` clearly by referring to [Figure 12.10](#c12.xhtml#f12.10).

![Figure 12.10 OpenVINO cycle of innovation.](images/fig12.10.jpg)

[**Figure 12.10**](#c12.xhtml#re_f12.10) OpenVINO cycle of innovation.

`OpenVINO` has become so popular and is so celebrated because of its ability to convert and optimize models with such frameworks as `TensorFlow`, `PyTorch` or `Caffe`. Also, the deployment becomes easier as it can be done across a mix of Intel hardware as well as environments. One can also deploy on-premises, on-device or in the cloud, making it so flexible for developers to choose the best they wish to use. [Fig. 12.11](#c12.xhtml#f12.11) presents you with a clear view of how much more powerful and flexible `OpenVINO` is.

![Figure 12.11 The power of OpenVINO.](images/fig12.11.jpg)

[**Figure 12.11**](#c12.xhtml#re_f12.11) The power of OpenVINO.

One can see that it can be either a `CPU`, `GPU`, `VPU` or `FPGA`. That’s an amazing convenience which the developer receives.

## 12.2.4 How to Install?

One needs to understand that the `OpenVINO` installation package is distributed in two parts: `OpenVINO Runtime` and `OpenVINO Development Tools`. It is recommended to install these two in one go instead of just installing the `OpenVINO Runtime`.

What is `OpenVINO Runtime`? It includes a set of libraries for running machine learning model inference on the processors. What are the Development Tools? They are the utilities that help working with the `OpenVINO` and `OpenVINO` models. The tools include the `Model Optimizer`, `Benchmarking Tool`, `Accuracy Checker` and `Annotation Converter`.

One can follow the guidelines and instructions available @ [`https://docs.openvino.ai/2022.2/openvino_docs_install_guides_overview.html`](https://docs.openvino.ai) for a smooth installation.

## 12.2.5 Resources Link?

The first thought which hits the mind of developers with any new platform or tool is, “Do I have resources to make the learning and practice easier?” The reply is a strong YES with the `OpenVINO`.

One would fall in love with the tutorials crafted and presented in the link @ [`https://docs.openvino.ai/2022.2/tutorials.html`](https://docs.openvino.ai)

Developers get free hands to the `Jupyter Notebooks`, and the tutorials are presented in a very easy way for smooth, flawless learning and practice.

One could see that the examples are presented with the link to launch the notebook with ease. This is a fine feature which makes life of learners much easier.

On clicking the launch button (see [Figure 12.12](#c12.xhtml#f12.12)), immediately one can see that the `Binder` gets launched in the browser as shown in [Figure 12.13](#c12.xhtml#f12.13). No installations or anything else is required to run these sample codes with this approach. It may take a few minutes to launch the `Jupyter Notebook`. One can take a look at the log messages if the delay seems more than expected to understand what’s happening.

![Figure 12.12 Sample codes and Demo0073.](images/fig12.12.jpg)

[**Figure 12.12**](#c12.xhtml#re_f12.12) Sample codes and Demo0073.

![Figure 12.13 The Binder launch.](images/fig12.13.jpg)

[**Figure 12.13**](#c12.xhtml#re_f12.13) The Binder launch.

Notebooks with a `Binder` button can be run without installing anything. Once you have found the tutorial of your choice, just click the button next to the name of it and `Binder` will start it in a new tab of the browser. `Binder` is a free online service with limited resources.

Once launched, the screen, as seen in [Figure 12.14,](#c12.xhtml#f12.14) with the sample code chosen (in this case, it is an image classification tutorial), will be opened in the `Jupyter NBViewer` and can be explored further. One can even download the notebook as required.

![Figure 12.14 Jupyter Notebook – image classification example.](images/fig12.14.jpg)

[**Figure 12.14**](#c12.xhtml#re_f12.14) Jupyter Notebook – image classification example.

That’s it! We have come to the end of this book. We are certain that it was an enjoyable ride of learning!

## 12.2.6 Key Points to Remember

* `Intel Distribution for Python` is an optimized Python version and provides results superior to the stock Python version.
* After installation of the `Intel Distribution for Python`, one should confirm whether the installation is effective and can be done with command: `python`.
* `OpenVINO` (Open Visual Inference and Neural Network Optimization) is a cross-platform deep learning toolkit developed by Intel.
* Currently, the most recent `OpenVINO` version is the 2022.3 LTS and it comes with excellent features, which make it very easy for developers to innovate.
* `OpenVINO` has become so popular and celebrated because of its ability to convert and optimize models with frameworks as `TensorFlow`, `PyTorch` or `Caffe`.
* One can also deploy on-premises, on-device or in the cloud which reflects the flexibility offered by `OpenVINO`.
* All of the `OpenVINO` tutorials are outlined @ [`https://docs.openvino.ai/2022.2/tutorials.html`](https://docs.openvino.ai).
* The sample codes and tutorials can be launched through the `Binder` and developers can run the `Jupyter Notebook` as required.

## Exercises

1. Write any complex piece of code and try running the code with the stock Python and the `Intel Distribution for Python`. What’s the inference?
2. Install Intel Distribution of `OpenVINO`. Try running the sample codes.

# Index

* A
