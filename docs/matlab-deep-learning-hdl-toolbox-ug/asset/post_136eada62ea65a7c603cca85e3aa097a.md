
# See Also

"Deep Learning on FPGA Solution and Workflows" on page 4-4

# Deep Learning on FPGA Solution and Workflows

The figure illustrates the MATLAB solution for implementing deep learning on FPGA.

![](img/747bfd4f288a7e0917a1f27637cc5c2d_23_0.png)

The FPGA deep learning solution provides an end-to-end solution that allows you to estimate, compile, profile and debug your custom pretrained series network. You can also generate a custom deep learning processor IP. The estimator is used for estimating the performance of the deep learning framework in terms of speed. The compiler converts the pretrained deep learning network for the current application for deploying it on the intended target FPGA boards.

To learn more about the deep learning processor IP, see "Deep Learning Processor IP Core" on page 12-2.

FPGAs provide advantages, such as:

- High performance
- Flexible interfacing
- Data parallelism
- Model parallelism
- Pipeline parallelism

# Deep Learning on FPGA Workflows

To run certain Deep Learning on FPGA tasks, see the information listed in this table.

| Task | Workflow |
|---|---|
| Run a pretrained series network on your target FPGA board. | "Prototype Deep Learning Networks on FPGA and SoCs Workflow" on page 5-2 |
| Obtain the performance of your pretrained series network for a preconfigured deep learning processor. | "Estimate Performance of Deep Learning Network" on page 8-3 |
| Customize the deep learning processor to meet your area constraints. | "Estimate Resource Utilization for Custom Processor Configuration" on page 8-9 |
| Generate a custom deep learning processor for your FPGA. | "Generate Custom Bitstream" on page 9-2 |
| Learn about the benefits of quantizing your pretrained series networks. | "Quantization of Deep Neural Networks" on page 11-2 |
| Compare the accuracy of your quantized pretrained series networks against your single data type pretrained series network. | "Validation" on page 11-14 |
| Run a quantized pretrained series network on your target FPGA board. | "Code Generation and Deployment" on page 11-17 |

# Workflow and APIS

- "Prototype Deep Learning Networks on FPGA and SoCs Workflow" on page 5-2
- "Profile Inference Run" on page 5-4
- "Multiple Frame Support" on page 5-6

# Prototype Deep Learning Networks on FPGA and SoCs Workflow

To prototype and deploy your custom series deep learning network, create an object of class dlhdl.Workflow. Use this object to accomplish tasks such as:

- Compile and deploy the deep learning network on specified target FPGA or SoC board by using the deploy function.
- Retrieve the bitstream resource utilization using the getBuildInfo function.
- Execute the deployed deep learning network and predict the classification of input images by using the predict function.
- Calculate the speed and profile of the deployed deep learning network by using the predict function. Set the Profile parameter to on.

This figure illustrates the workflow to deploy your deep learning network to the FPGA boards.

![](img/747bfd4f288a7e0917a1f27637cc5c2d_27_0.png)

# See Also

dldl.Target | dldl.Workflow

# More About

- “Get Started with Deep Learning FPGA Deployment on Xilinx ZCU102 SoC” on page 10-5

# Profile Inference Run

View the network prediction and performance data for the layers, convolution module and fully connected modules by our pretrained series network. The example shows how to retrieve the prediction and profiler results for the ResNet-18 network.

1. Create an object of class Workflow using the dhdl.Workflow class.
2. Set a pretrained deep learning network and bitstream for the workflow object.
3. Create an object of class dhdl.Target and specify the target vector and interface.
4. To deploy the network on a specified target FPGA board, call the deploy method for the workflow object.
5. Call the predict function for the workflow object. Provide an array of images as the InputImageParameter. Provide arguments to turn on the profiler.

The labels classifying the images are stored in a structure struct and displayed on the screen. The performance parameters of speed and latency are returned in a structure struct.

Use this image to run the code:

![](img/747bfd4f288a7e0917a1f27637cc5c2d_29_0.png)

```
snet = resnet18;
ht = dhdl.Target('Xilinx', 'Interface', 'Ethernet');
hw = dhdl.Workflow('Net', snet, 'Bitstream', 'zcu102_single', 'Target',ht);
hw.deploy;
image = read('zebra.jpg');
inputImg = resize(image, [224, 224]);
nimshow(inputImg);
[prediction, speed] = nw.predict(single(inputImg), 'Profile', 'on');
val, idx = max(prediction);
snet.Layers(end).ClassNames(idx)
```

```
### Finished writing input activations.
### Running simple input activations.
```

Deep Learning Processor | Performance Results

| LastFrameLatency(Cycles) | LastFrameLatency(seconds) | FrameNum | Total Latency | Frames/s |
| --- | --- | --- | --- | --- |
| Network | 23659630 | 0.10754 | 1 | 23659630 | 9.3 |
| convl | 2224115 | 0.01011 | | | |
| pool | 572867 | 0.00260 | | | |
| res2a branch2a | 972699 | 0.00442 |
| res2a branch2b | 972568 | 0.00442 |
| res2a | 209312 | 0.00095 |
| res2b branch2a | 972723 | 0.00442 |
| res2b branch2b | 973082 | 0.00442 |
| res2b | 209756 | 0.00095 |
| res3a branch2a | 747587 | 0.00340 |
| res3a branch2b | 904291 | 0.00411 |
| res3a branch3 | 537603 | 0.00435 |
| res3b branch2a | 104750 | 0.00411 |
| res3b branch2b | 904389 | 0.00411 |
| res3b | 904367 | 0.00408 |
| res4a | 104886 | 0.00221 |
| res4a branch2b | 485602 | 0.00400 |
| res4a branch1 | 800081 | 0.00221 |
| res4b branch2a | 486429 | 0.00224 |
| res5a branch2a | 747587 | 0.00340 |
| res5a branch2b | 904291 | 0.00411 |
| res5a branch3 | 537603 | 0.00435 |
| res5b branch2a | 104750 | 0.00411 |
| res5b branch2b | 904389 | 0.00411 |
| res5b | 904367 | 0.00408 |
