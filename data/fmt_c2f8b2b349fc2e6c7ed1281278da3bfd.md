
```python
# -*- coding: utf-8 -*-
"""
############################################################################################################
#
# 文件：DLfunctions41.py
# 开发者：Tinniam V Ganesh
# 日期：2018 年 3 月 23 日
#
##########################################################################################################
@author: Ganesh
"""
import numpy as np
import matplotlib.pyplot as plt
import matplotlib
import matplotlib.pyplot as plt
from matplotlib import cm
import math

# 计算向量的 sigmoid
def sigmoid(Z):
    A = 1 / (1 + np.exp(-Z))
    cache = Z
    return A, cache

# 计算向量的 Relu
def relu(Z):
    A = np.maximum(0, Z)
    cache = Z
    return A, cache

# 计算向量的 tanh
def tanh(Z):
    A = np.tanh(Z)
    cache = Z
    return A, cache

# 计算向量的 softmax
def softmax(Z):
    # 获取未归一化的概率
    exp_scores = np.exp(Z.T)
    # 对每个样本进行归一化
    A = exp_scores / np.sum(exp_scores, axis=1, keepdims=True)
    cache = Z
    return A, cache

# 计算向量的稳定 Softmax
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
    s = 1 / (1 + np.exp(-Z))
    dZ = dA * s * (1 - s)
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
    # 计算 softmax
    exp_scores = np.exp(Z.T)
    # 对每个样本进行归一化
    probs = exp_scores / np.sum(exp_scores, axis=1, keepdims=True)
    # 计算分数上的梯度
    dZ = probs
    # dZ = pi - yi
    dZ[range(int(numTraining)), y[:, 0]] -= 1
    return dZ

# 计算稳定 Softmax 的导数
def stableSoftmaxDerivative(dA, cache, y, numTraining):
    # 注意：未使用 dA。dL/dZ = dL/dA * dA/dZ = pi-yi
    Z = cache
    # 计算稳定 softmax
    shiftZ = Z.T - np.max(Z.T, axis=1).reshape(-1, 1)
    exp_scores = np.exp(shiftZ)
    # 对每个样本进行归一化
    probs = exp_scores / np.sum(exp_scores, axis=1, keepdims=True)
    # print(probs)
    # 计算分数上的梯度
    dZ = probs
    # dZ = pi - yi
    dZ[range(int(numTraining)), y[:, 0]] -= 1
    return dZ

# 初始化模型
# 输入：特征数量
# 隐藏单元数量
# 输出单元数量
# 返回：nnParameters 字典
def initializeModel(numFeats, numHidden, numOutput):
    np.random.seed(1)
    W1 = np.random.randn(numHidden, numFeats) * 0.01  # 乘以 .01
    b1 = np.zeros((numHidden, 1))
    W2 = np.random.randn(numOutput, numHidden) * 0.01
    b2 = np.zeros((numOutput, 1))

# 创建神经网络参数字典
    nnParameters = {'W1': W1, 'b1': b1, 'W2': W2, 'b2': b2}
    return nnParameters

# 初始化 L 层模型
# **输入**：每层单元数列表
# **返回**：Z, cache
def initializeDeepModel(layerDimensions):
    np.random.seed(3)
    # 注意第 'l' 层的权重矩阵大小为 (l,l-1)
    # 偏置是大小为 (l,1) 的向量
    # 从 1 循环到 L 的层维度
    layerParams = {}
    for l in range(1, len(layerDimensions)):
        layerParams['W' + str(l)] = np.random.randn(layerDimensions[l], layerDimensions[l-1]) * 0.01  # 乘以 .01
        layerParams['b' + str(l)] = np.zeros((layerDimensions[l], 1))
    return layerParams

# 计算深度网络前向传播中第 'l' 层的激活值
# **输入**：
# - `A_prev` - 上一层的激活值
# - `W`, `b` - 权重和偏置矩阵及向量
# - `activationFunc` - 激活函数 - sigmoid, tanh, relu 等
# **返回**：`A`, `cache`
# **公式**：
# - `Z = W * X + b`
# - `A = sigmoid(Z)`, `A = Relu(Z)`, `A = tanh(Z)`
def layerActivationForward(A_prev, W, b, activationFunc):
    # 计算 Z
    Z = np.dot(W, A_prev) + b
    forward_cache = (A_prev, W, b)

    # 计算 sigmoid 的激活值
    if activationFunc == "sigmoid":
        A, activation_cache = sigmoid(Z)
    # 计算 Relu 的激活值
    elif activationFunc == "relu":
        A, activation_cache = relu(Z)
    # 计算 tanh 的激活值
    elif activationFunc == 'tanh':
        A, activation_cache = tanh(Z)
    elif activationFunc == 'softmax':
        A, activation_cache = stableSoftmax(Z)

    cache = (forward_cache, activation_cache)
    return A, cache

# 计算第 1..L 层的前向传播
# **输入**：
# - `X` - 输入特征
# - `parameters` - 权重和偏置
# - `hiddenActivationFunc` - 隐藏层激活函数 Relu/tanh
# - `outputActivationFunc` - 输出层激活函数 - sigmoid/softmax
# **返回**：`AL`, `caches`
# 前向传播在第 1..L-1 层使用 Relu/tanh 激活函数，在第 L 层使用 sigmoid 激活函数。
def forwardPropagationDeep(X, parameters, hiddenActivationFunc='relu', outputActivationFunc='sigmoid'):
    caches = []
    # 将 A 设为 X (A0)
    A = X
    L = int(len(parameters) / 2)  # 神经网络中的层数

    # 从第 1 层循环到第 L 层
    for l in range(1, L):
        A_prev = A
        # Zi = Wi x Ai-1 + bi and Ai = g(Zi)
        # A, cache = layerActivationForward(A_prev, parameters['W'+str(l)], parameters['b'+str(l)], activationFunc = "relu")
        A, cache = layerActivationForward(A_prev, parameters['W'+str(l)], parameters['b'+str(l)], activationFunc=hiddenActivationFunc)
        caches.append(cache)
        # print("l=",l)
        # print(A)

    # 因为这是二分类，在最后一层使用 sigmoid 激活函数
    AL, cache = layerActivationForward(A, parameters['W'+str(L)], parameters['b'+str(L)], activationFunc=outputActivationFunc)
    caches.append(cache)
    return AL, caches

# 计算代价
# **输入**：
# - `AL` - 最后一层的激活值
# - `Y`
# - `outputActivationFunc` - 输出层激活函数 - sigmoid/softmax
# **输出**：`cost`
def computeCost(AL, Y, outputActivationFunc="sigmoid"):
    if outputActivationFunc == "sigmoid":
        m = float(Y.shape[1])
        # 对 logprobs 进行逐元素相乘
        cost = -1/m * np.sum(Y * np.log(AL) + (1-Y) * (np.log(1-AL)))
        cost = np.squeeze(cost)
    elif outputActivationFunc == "softmax":
        # 注意：对 Y 进行转置以用于 softmax
        Y = Y.T
        m = float(len(Y))
        # 计算对数概率。根据输出 y 取正确类别的对数概率
        correct_logprobs = -np.log(AL[range(int(m)), Y.T])
        # 计算损失
        cost = np.sum(correct_logprobs) / m
    return cost

# 计算 1 个周期的反向传播
# **输入**：
# - 神经网络参数 - `dA`
# - `cache` - `forward_cache` & `activation_cache`
# - `Y`
# - `activationFunc` - relu, tanh, sigmoid, softmax
# **返回**：`dA_prev`, `dW`, `db`
# **公式**：
# - `dL/dWi = dL/dZi * Al-1`
# - `dl/dbl = dL/dZl`
# - `dL/dZ_prev = dL/dZl * W`
def layerActivationBackward(dA, cache, Y, activationFunc):
    forward_cache, activation_cache = cache
    A_prev, W, b = forward_cache
    numtraining = float(A_prev.shape[1])
    # print("n=",numtraining)
    # print("no=",numtraining)

    if activationFunc == "relu":
        dZ = reluDerivative(dA, activation_cache)
    elif activationFunc == "sigmoid":
        dZ = sigmoidDerivative(dA, activation_cache)
    elif activationFunc == "tanh":
        dZ = tanhDerivative(dA, activation_cache)
    elif activationFunc == "softmax":
        dZ = stableSoftmaxDerivative(dA, activation_cache, Y, numtraining)

    if activationFunc == 'softmax':
        dW = 1/numtraining * np.dot(A_prev, dZ)
        db = 1/numtraining * np.sum(dZ, axis=0, keepdims=True)
        dA_prev = np.dot(dZ, W)
    else:
        # print(numtraining)
        dW = 1/numtraining * (np.dot(dZ, A_prev.T))
        # print("dW=",dW)
        db = 1/numtraining * np.sum(dZ, axis=1, keepdims=True)
        # print("db=",db)
        dA_prev = np.dot(W.T, dZ)

    return dA_prev, dW, db

# 计算 1 个周期的反向传播
# **输入**：
# - `AL`：L 层网络的输出 - 权重
# - `Y` 真实输出
# - `caches` -- 包含以下内容的缓存列表：
#   - 每个 `layerActivationForward()` 的缓存，激活函数为 "relu"/"tanh" (即 `caches[l]`, l 取值范围为 range(L-1) 即 l = 0...L-2)
#   - `layerActivationForward()` 的缓存，激活函数为 "sigmoid" (即 `caches[L-1]`)
# - `hiddenActivationFunc` - 隐藏层激活函数 - relu/sigmoid/tanh
# - `outputActivationFunc` - 输出层激活函数 - sigmoid/softmax
# **返回**：
# - `gradients` -- 包含梯度的字典
#   - `gradients["dA" + str(l)] = ...`
#   - `gradients["dW" + str(l)] = ...`
#   - `gradients["db" + str(l)]`
```
