# Deep Learning on FPGA Workflow

This figure illustrates deep learning on FPGA workflow.

![](bbox=[0.96, 0.206, 0.9, 0.427])

To use the workflow:

+   1 Load deep learning neural network

You can load the various deep learning neural networks such as AlexNet, VGG and GoogleNet onto the MATLAB framework. When you compile the network, the network parameters are saved into a structure that consists of NetConfigs and LayerConfigs. NetConfigs consists of the weights and biases of the trained network. LayerConfig consists of various configuration details of the trained network.

+   2 Modify pretrained neural network on MATLAB using transfer learning

The internal network developed on the MATLAB framework is trained and modified according to the parameters of the external neural network. Also see “Get Started with Transfer Learning”.

+   3 Compile user network

Compilation of the user network usually involves validating the architecture, types of layers present , data type of input and output parameters, maximum number of activations. This FPGA solution supports network architecture with data types single and int8. For details, see “Product Description”. If the network features are different, the compiler produces an error and stops. The compiler also performs sanity check by using weight compression and quantization.

+   4 Deploy on target FPGA board

By using specific APIs and the NetConfigs and layerConfigs, deploying the compiled network connects the user-trained network into a fixed bitstream and then programs the bitstream on the target FPGA.

+   5 Predict outcome

To classify objects in the input image, use the deployed framework on the FPGA.