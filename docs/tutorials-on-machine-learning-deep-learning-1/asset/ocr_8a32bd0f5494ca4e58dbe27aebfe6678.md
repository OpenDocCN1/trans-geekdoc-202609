# Chapter 14: Part 4
Deep Learning

BM project - part 1: Building RBM class
Data preprocessing & Building RBM class

# 14.4.0.1 Objectives

Boltzmann Machines can be seen from two different points of view:

+   [1]. An Energy-Based Model
[2]. A Probabilistic Graphical Model

In the Intuition Lectures we focused on the Energy-Based Model point of view, and then for the Practical Lectures we will focus more on the Probabilistic Graphical Model point of view.

+   In last two parts (Boltzmann Machines and AutoEncoder) of this book, we will create two types of Recommender Systems:
[1]. One that predicts binary ratings 'Like' or 'Not Like'. We will build it in this section with a Boltzmann Machine.
[2]. Another one that predicts ratings from 1 to 5. We will build it in next chapter with an AutoEncoder.

We will implement these two Deep Learning models with PyTorch, a highly advanced Deep Learning platform more powerful than Keras.

# 14.4.0.2 Installing PyTorch

Using Anaconda (conda)

| PyTorch Build | Stable (1.12.0) | Preview (Nightly) | LTS (1.8.2) |
|---|---|---|---||
| Your OS | Linux | Mac | Windows |
| Package | Conda | Pip | LibTorch | Source |
| Language | Python | | C++ / Java |
| Compute Platform | CUDA 10.2 | CUDA 11.3 | CUDA 11.6 | ROCm 5.1.1 - CPU |

Run this Command: conda install pytorch torchvision torchaudio cpuonly -c pytorch

Using pip:

| PyTorch Build | Stable (1.12.0) | Preview (Nightly) | LTS (1.8.2) |
|---|---|---|---||
| Your OS | Linux | Mac | Windows |
| Package | Conda | Pip | LibTorch | Source |
| Language | Python | | C++ / Java |
| Compute Platform | CUDA 10.2 | CUDA 11.3 | CUDA 11.6 | ROCm 5.1.1 - CPU |

Run this Command: pip3 install torch torchvision torchaudio

pip3 install torch torchvision torchaudio