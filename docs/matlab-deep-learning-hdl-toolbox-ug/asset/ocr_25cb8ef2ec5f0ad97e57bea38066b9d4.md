# Quantization Workflow Prerequisites

This table lists the products required to quantize and deploy deep learning networks.

| Execution Environment | FPGA | GPU | CPU |
| --- | --- | --- | --- |
| Development Host Requirements | | | |
| Setup Toolkit Environment | hdlsettooltip (HDL Coder) | "Setting Up the Prerequisite Products" (GPU Coder) | "Prerequisites for Deep Learning with MATLAB C" (MATLAB Coder) |
| | The **Calibrate** workflow requires the MinGW C+ + compiler or other compilers. For a list of supported compilers, see https://www.mathworks.com/support/requirements/supported-compilers.html | | |
| | Note The **Calibrate** workflow does not support the MinGW C compiler. | | |
| Required Products | • Deep Learning Toolbox<br>Deep Learning HDL Toolbox | Deep Learning Toolbox | Deep Learning Toolbox |
| Required Support Packages | • Deep Learning Toolbox Model Quantization Library<br>Deep Learning HDL Support Package for Xilinx FPGA and SoC Devices<br>Deep Learning Toolbox Support Package for Intel FPGA and SoC Devices | Deep Learning Model Quantization Library | Deep Learning Model Quantization Library |
| Supported Networks and Layers | "Supported Networks, Layers, Boards, and Tools" on page 7-2 | "Supported Networks, Layers, and Classes" (GPU Coder) | "Networks and Layers Supported for Code Generation" (MATLAB Coder) |