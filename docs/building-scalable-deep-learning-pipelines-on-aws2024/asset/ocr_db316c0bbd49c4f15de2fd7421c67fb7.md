# # Installing PyTorch

With the virtual environment activated, install PyTorch using pip. You can choose the appropriate command based on your system configuration and requirements. For example, to install PyTorch with Compute Unified Device Architecture (CUDA) support for GPU acceleration, you can use the following command:

```
```
[In]: pip install torch torchvision torchaudio
```
```

After the installation is complete, you can verify it by running a Python script that imports PyTorch:

```
```
[In]: python -c "import torch; print(torch.__version__)"
[Out]: 2.2.2+cu121
```
```

This command prints the installed version of PyTorch, which in this case is 2.2.2. This includes CUDA support for GPU acceleration, as indicated by the “+cu121” suffix.

> > **Note** CUDA (Compute Unified Device Architecture) is a parallel computing platform and application programming interface (API) model created by NVIDIA. It allows software developers to harness the computational power of NVIDIA GPUs (Graphics Processing Units) for general-purpose processing tasks, including deep learning and scientific simulations.

# # Installing TensorFlow

Install TensorFlow and Keras using pip as follows:

```
```
[In]: pip install tensorflow keras
```
```