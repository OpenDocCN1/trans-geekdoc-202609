# Deep Learning Quantization

# Calibration

# Workflow

Collect the dynamic ranges of the weights and biases in the convolution and fully connected layers of the quantized network and the dynamic ranges of the activations in all layers.

The calibrate method uses the collected dynamic ranges to generate an exponents file. The dldhl.Workflow class compile method uses the exponents file to generate a configuration file that contains the weights and biases of the quantized network.

This workflow is the workflow to calibrate your quantized series deep learning network.

![](bbox=[0.138, 0.323, 0.366, 0.905])

11-12