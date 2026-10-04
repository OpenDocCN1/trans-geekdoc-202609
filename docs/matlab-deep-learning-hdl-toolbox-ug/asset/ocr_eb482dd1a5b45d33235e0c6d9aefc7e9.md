# Activation Normalization

Based on the neural network that you provide, the Activation Normalization module serves the purpose of adding the ReLU nonlinearity, a maxpool layer, or performs Local Response Normalization (LRN). You see that the processor has two Activation Normalization units. One unit follows the Generic Convolution Processor. The other unit follows the Generic FC Processor.

# Conv Controller (Scheduling)

Depending on the number of convolution layers that you have in your pretrained network, the Conv Controller (Scheduling) acts as ping-pong buffers. The Generic Convolution Processor and Activation Normalization can process one layer at a time. To process the next layer, the Conv Controller (Scheduling) moves back to the BRAM and performs the convolution and activation normalization for all convolution layers in the network.

# Generic FC Processor

The Generic FC Processor performs the equivalent operation of one fully-connected layer (FC). Using another AXI4 Master interface, the weights for the fully-connected layer are provided by the Generic FC Processor. The Generic FC Processor then performs the fully-connected layer operation on the input image and provides the activations for the Activation Normalization module. This processor is also generic because it can support tensors and shapes of various sizes.

# FC Controller (Scheduling)

The FC Controller (Scheduling) works similar to the Conv Controller (Scheduling). The FC Controller (Scheduling) coordinates with the FIFO to act as ping-pong buffers for performing the fully-connected layer operation and Activation Normalization depending on the number of FC layers, and ReLU, maxpool, or LRN features that you have in your neural network. After the Generic FC Processor and Activation Normalization modules process all the frames in the image, the predictions or scores are transmitted through the AXI4 Master interface and stored in the external DDR memory.

# Deep Learning Processor Applications

One application of the deep learning processor IP is the MATLAB deep learning processor: To create this, integrate the deep learning processor IP with the HDL Verifier™ MATLAB as AXI Master IP by using the AXI4 slave interface. Through a JTAG or PCI express interface, you can import pretrained neural networks from MATLAB, execute the operations specified by the network in the deep learning processor IP, and return the classification results to MATLAB.

For more information, see “MATLAB Controlled Deep Learning Processor” on page 3-2.