# 3 Applications and Examples

# MATLAB Controlled the deep learning networks

To rapidly prototype the deep learning networks on FPGAs from MATLAB, use a MATLAB controlled deep learning processor. The processor integrates the generic deep learning processor with the HDL Verifier MATLAB as AXI Master IP. For more information on:

+   - Generic deep learning processor IP, see "Deep Learning Processor Applications" on page 2-3 .
- MATLAB as AXI Master IP, see "Set Up for MATLAB AXI Master" (HDL Verifier) .

You can use this processor to run neural networks with various inputs, weights, and biases on the same FPGA platform because the deep learning processor core can handle tensors and shapes of any sizes. Before you use the MATLAB AXI Master, make sure that you have installed the HDL Verifier support packages for the FPGA boards. This figure shows the MATLAB controlled deep learning processor architecture.

![](bbox=[0.095, 0.363, 0.853, 0.606])

To integrate the generic deep learning processor IP with the MATLAB as AXI4 Slave interface of the deep learning processor IP core. By using a JTAG or PCI express interface, the IP respond to or write commands from MATLAB. Therefore, you can use the MATLAB controlled deep learning processor to deploy the deep learning neural network to the FPGA boards from MATLAB, perform operations specified by the network architecture, and then return the predicted results to MATLAB. Following example illustrate how to deploy the pretrained network, AlexNet, on an Intel® Arria® 10 SoC development kit.

3-2