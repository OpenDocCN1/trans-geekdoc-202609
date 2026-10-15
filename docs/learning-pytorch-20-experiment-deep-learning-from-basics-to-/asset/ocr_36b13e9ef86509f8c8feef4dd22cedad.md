```
source ~/.bashrc
```

# Verify the Installation

To verify the installation, use the following command:

```
nvcc -V
```

You should see "Cuda compilation tools, release 11.8, V11.8.xxxxx" if CUDA is installed correctly.

# Install PyTorch 2.0

Now, we will install PyTorch 2.0. First, we recommend creating a Python virtual environment to avoid package conflicts. Use the following commands:

```
sudo apt-get install python3-venv
```

```
python3 -m venv pytorch_env
```

```
source pytorch_env/bin/activate
```