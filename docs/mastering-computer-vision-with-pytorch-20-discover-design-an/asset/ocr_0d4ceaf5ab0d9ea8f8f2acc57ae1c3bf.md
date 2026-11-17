3. To activate the environment, run:
source pytorch_env/bin/activate

# For Mac

+   1. If not already installed, install virtualenv with pip:
+   pip install virtualenv

+   2. Navigate to the directory where you want to create the virtual environment, then run:
+   virtualenv pytorch_env

+   3. To activate the environment, run:
+   source pytorch_env/bin/activate

Once the environment is activated, the name of the environment will appear on the left side of the terminal prompt. This indicates that the environment is ready to use.

# Installing PyTorch

With the virtual environment set up, you can now install PyTorch. PyTorch provides pre-built binaries that can be installed via pip or conda. In this book, we will use pip.
For the latest version of PyTorch, run the following command:

```
pip install torch torchvision torchaudio
```

If you need a specific version of PyTorch, for instance, version 2.0, use the == operator:

```
pip install torch==2.0 torchvision==0.11.1 torchaudio==0.10.1
```

# CPU vs. GPU (CUDA) Installation:

If you have a compatible NVIDIA GPU and want to take advantage of CUDA for faster computation, you can install PyTorch with CUDA support. Here are examples for both CPU-only and GPU (CUDA) installations: