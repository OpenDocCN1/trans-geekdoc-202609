

# 附录 8 – 梯度检验

## 8.1 Python

```python
# -*- coding: utf-8 -*-
############################################################################################################
#
# File: DLfunctions8.py
# Developer: Tinniam V Ganesh
# Date : 6 May 2018
#
##########################################################################################################

import numpy as np
import matplotlib.pyplot as plt
import matplotlib
import matplotlib.pyplot as plt
from matplotlib import cm
import math
import sklearn
import sklearn.datasets

# 计算向量的 Sigmoid 函数值
def sigmoid(Z):
    A = 1/(1+np.exp(-Z))
    cache = Z
    return A, cache

# 计算向量的 Relu 函数值
def relu(Z):
    A = np.maximum(0, Z)
    cache = Z
    return A, cache

# 计算向量的 tanh 函数值
def tanh(Z):
    A = np.tanh(Z)
    cache = Z
    return A, cache

# 计算向量的 Softmax 函数值
def softmax(Z):
    # 获取未归一化的概率
    exp_scores = np.exp(Z.T)
    # 对每个样本进行归一化
    A = exp_scores / np.sum(exp_scores, axis=1, keepdims=True)
    cache = Z
    return A, cache

# 计算向量的数值稳定 Softmax 函数值
def stableSoftmax(Z):
    # 以数值稳定的方式计算向量 x 的 softmax。
    shiftZ = Z.T - np.max(Z.T, axis=1).reshape(-1, 1)
    exp_scores = np.exp(shiftZ)
    # 对每个样本进行归一化
    A = exp_scores / np.sum(exp_scores, axis=1, keepdims=True)
    cache = Z
    return A, cache

# 计算 Relu 的导数
def reluDerivative(dA, cache):
    Z = cache
    dZ = np.array(dA, copy=True)  # 只是将 dz 转换为正确的对象。
    # 当 z <= 0 时，也应将 dz 设为 0。
    dZ[Z <= 0] = 0
    return dZ

# 计算 Sigmoid 的导数
def sigmoidDerivative(dA, cache):
    Z = cache
    s = 1/(1+np.exp(-Z))
    dZ = dA * s * (1-s)
    return dZ

# 计算 tanh 的导数
def tanhDerivative(dA, cache):
    Z = cache
    a = np.tanh(Z)
    dZ = dA * (1 - np.power(a, 2))
    return dZ

# 计算 Softmax 的导数
def softmaxDerivative(dA, cache, y, numTraining):
    # 注意：未使用 dA。dL/dZ = dL/dA * dA/dZ = pi-yi
    Z = cache
    # 计算 Softmax
    exp_scores = np.exp(Z.T)
    # 对每个样本进行归一化
    probs = exp_scores / np.sum(exp_scores, axis=1, keepdims=True)
    # 计算分数上的梯度
    dZ = probs
    # dZ = pi- yi
    dZ[range(int(numTraining)), y[:, 0]] -= 1
    return dZ

# 计算稳定 Softmax 的导数
def stableSoftmaxDerivative(dA, cache, y, numTraining):
    # 注意：未使用 dA。dL/dZ = dL/dA * dA/dZ = pi-yi
    Z = cache
    # 计算稳定 Softmax
    shiftZ = Z.T - np.max(Z.T, axis=1).reshape(-1, 1)
    exp_scores = np.exp(shiftZ)
    # 对每个样本进行归一化
    probs = exp_scores / np.sum(exp_scores, axis=1, keepdims=True)
    # 计算分数上的梯度
    dZ = probs
    # dZ = pi- yi
    dZ[range(int(numTraining)), y[:, 0]] -= 1
    return dZ

# 初始化模型
# 输入：特征数量
# 隐藏单元数量
# 输出单元数量
# 返回：权重和偏置矩阵及向量
def initializeModel(numFeats, numHidden, numOutput):
    np.random.seed(1)
    W1 = np.random.randn(numHidden, numFeats) * 0.01  # 乘以 .01
    b1 = np.zeros((numHidden, 1))
    W2 = np.random.randn(numOutput, numHidden) * 0.01
    b2 = np.zeros((numOutput, 1))
    # 创建神经网络参数字典
    nnParameters = {'W1': W1, 'b1': b1, 'W2': W2, 'b2': b2}
    return nnParameters

# 为 L 层初始化模型
# 输入：每层单元数量的列表
# 返回：所有层的初始权重和偏置矩阵
def initializeDeepModel(layerDimensions):
    np.random.seed(3)
    # 注意第 'l' 层的权重矩阵大小为 (l,l-1)
    # 偏置是大小为 (l,1) 的向量
    # 从 1 循环到 L
    layerParams = {}
    for l in range(1, len(layerDimensions)):
        layerParams['W' + str(l)] = np.random.randn(layerDimensions[l], layerDimensions[l-1]) * 0.01  # 乘以 .01
        layerParams['b' + str(l)] = np.zeros((layerDimensions[l], 1))
        np.savetxt('W' + str(l) + '.csv', layerParams['W' + str(l)], delimiter=',')
        np.savetxt('b' + str(l) + '.csv', layerParams['b' + str(l)], delimiter=',')
    return layerParams

# 为 L 层进行 He 初始化模型
# 输入：每层单元数量的列表
# 返回：所有层的初始权重和偏置矩阵
# He 初始化将随机数乘以 sqrt(2/layerDimensions[l-1])
def HeInitializeDeepModel(layerDimensions):
    np.random.seed(3)
    # 注意第 'l' 层的权重矩阵大小为 (l,l-1)
    # 偏置是大小为 (l,1) 的向量
    # 从 1 循环到 L
    layerParams = {}
    for l in range(1, len(layerDimensions)):
        layerParams['W' + str(l)] = np.random.randn(layerDimensions[l], layerDimensions[l-1]) * np.sqrt(2/layerDimensions[l-1])
        layerParams['b' + str(l)] = np.zeros((layerDimensions[l], 1))
    return layerParams

# 为 L 层进行 Xavier 初始化模型
# 输入：每层单元数量的列表
# 返回：所有层的初始权重和偏置矩阵
# Xavier 初始化将随机数乘以 sqrt(1/layerDimensions[l-1])
def XavInitializeDeepModel(layerDimensions):
    np.random.seed(3)
    # 注意第 'l' 层的权重矩阵大小为 (l,l-1)
    # 偏置是大小为 (l,1) 的向量
    # 从 1 循环到 L
    layerParams = {}
    for l in range(1, len(layerDimensions)):
        layerParams['W' + str(l)] = np.random.randn(layerDimensions[l], layerDimensions[l-1]) * np.sqrt(1/layerDimensions[l-1])
        layerParams['b' + str(l)] = np.zeros((layerDimensions[l], 1))
    return layerParams

# 初始化速度
# 输入：parameters
# 返回：v - 初始速度
def initializeVelocity(parameters):
    L = len(parameters) // 2  # 创建一个整数
    v = {}
    # 使用与 W 相同的维度初始化速度
    for l in range(L):
        v["dW" + str(l+1)] = np.zeros((parameters['W' + str(l+1)].shape[0], parameters['W' + str(l+1)].shape[1]))
        v["db" + str(l+1)] = np.zeros((parameters['b' + str(l+1)].shape[0], parameters['b' + str(l+1)].shape[1]))
    return v

# 初始化 RMSProp 参数
# 输入：每层单元数量的列表
# 返回：s - 初始 RMSProp
def initializeRMSProp(parameters):
    L = len(parameters) // 2  # 创建一个整数
    s = {}
    # 使用与 W 相同的维度初始化速度
    for l in range(L):
        s["dW" + str(l+1)] = np.zeros((parameters['W' + str(l+1)].shape[0], parameters['W' + str(l+1)].shape[1]))
        s["db" + str(l+1)] = np.zeros((parameters['b' + str(l+1)].shape[0], parameters['b' + str(l+1)].shape[1]))
    return s

# 初始化 Adam 参数
# 输入：每层单元数量的列表
# 返回：v 和 s - Adam 参数
def initializeAdam(parameters):
    L = len(parameters) // 2  # 神经网络中的层数
    v = {}
    s = {}
    # 初始化 v, s。
    for l in range(L):
        v["dW" + str(l+1)] = np.zeros((parameters['W' + str(l+1)].shape[0], parameters['W' + str(l+1)].shape[1]))
        v["db" + str(l+1)] = np.zeros((parameters['b' + str(l+1)].shape[0], parameters['b' + str(l+1)].shape[1]))
        s["dW" + str(l+1)] = np.zeros((parameters['W' + str(l+1)].shape[0], parameters['W' + str(l+1)].shape[1]))
        s["db" + str(l+1)] = np.zeros((parameters['b' + str(l+1)].shape[0], parameters['b' + str(l+1)].shape[1]))
    return v, s

# 计算深层网络前向传播中第 'l' 层的激活值
# 输入：A_prev - 上一层的激活值
# W,b - 权重和偏置矩阵及向量
# keep_prob
# activationFunc - 激活函数 - sigmoid, tanh, relu 等
# 返回：A, cache
# :
# Z = W * X + b
# A = sigmoid(Z), A= Relu(Z), A= tanh(Z)
def layerActivationForward(A_prev, W, b, keep_prob=0, activationFunc="relu"):
    # 计算 Z
    Z = np.dot(W, A_prev) + b
    forward_cache = (A_prev, W, b)
```

```matlab
contour(X1, X2, vals, "linewidth", 4);
print -dpng "fig-o1.png"
end
```

