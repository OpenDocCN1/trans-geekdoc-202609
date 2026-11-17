


p = sigmoid(np.dot(X,w_0)+b_0)
if (LC):
    v = p*(1.-p)*np.tanh(a*(y-p))
    v = v.T
    v_stacked = np.tile(v[:, np.newaxis],
        (1, X.shape[1]) )
    X_multiplied = -X * v_stacked
    dw = np.sum(X_multiplied, axis=0)
    db = np.sum(p*(1.-p)*np.tanh(a*(y-p)) * (-1))
else:
    v = y-p
    v_stacked = np.tile(v[:, np.newaxis],
        (1, X.shape[1]) )
    X_multiplied = -X * v_stacked
    dw = np.sum(X_multiplied, axis=0)
    db = np.sum((y-p)*(-1))
return dw, db

c) 运行以下代码以执行 LCLR 和 CELR。最初，代码设置为在泰坦尼克号训练集上运行 LCLR。该代码假设已成功完成本章的问题 1。

```python
X = train_df.drop(["Survived"],axis=1)
y = train_df["Survived"]
LC = True
CE = False
reg_type = LC #LC or CE
if(reg_type):
    print("Running LC logistic regression (LCLR)")
    adam = AdamOptim(learning_rate=0.005)
else:
    print("Running CE logistic regression (CELR)")
    adam = AdamOptim(learning_rate=0.005)
a = 10.0
w = np.array([-0.1,-0.1,-0.1,0.1,0.1,0.1,-0.1])
b = 0.0
t = 0
loss = []
print("Iteration =", t, "Loss =",
    format(Loss_function(w,b,reg_type), '.3f'))
converged, iter_count = False, 4500
while not converged:
    loss.append(Loss_function(w,b,reg_type))
    dw, db = dLoss_function(w,b,reg_type)
```

```python
w_old = w
w, b = adam.update(t,w=w, b=b, dw=dw, db=db)

t += 1
if (t%1000 == 0):
    print("Iteration =", t, "Loss =",
        format(Loss_function(w,b,reg_type), '.3f'))
if (t > iter_count):
    converged = True
print("Iteration =", t, "Loss =",
    format(Loss_function(w,b,reg_type), '.3f'))
print(w)
print("intercept ", format(b, '.6f'))
```

- d) 绘制损失函数与迭代次数的图表，以确认已发生收敛。

```python
plt.plot(loss)
plt.xlabel('Iteration')
plt.ylabel('loss')
plt.show()
```

- e) 预测结果。

```python
pT = 0.5
z = np.dot(X,w)+b
p = sigmoid(z)
pred = p > pT
```

- f) 运行以下代码以获取准确率、精确率、召回率、F1 分数和 AUROC 的指标。

```python
from sklearn import metrics
if (reg_type):
    print("Log-cosh metrics")
else:
    print("Cross-entropy metrics")
print("Confusion Matrix:")
table = metrics.confusion_matrix(pred,y)
print(table)
accuracy = np.mean(pred == y)
precision = metrics.precision_score(y,pred)
recall = metrics.recall_score(y,pred)
f1 = metrics.f1_score(y,pred)
auroc = metrics.roc_auc_score(y, pred)
print("accuracy =", format(accuracy, '.3f'))
print("precision =", format(precision, '.3f'))
print("recall =", format(recall, '.3f'))
print("F1 score =", format(f1, '.3f'))
print("AUROC score =", format(auroc, '.3f'))
```

- g) 为 CELR 重新运行该序列。将结果与 LCLR 进行比较。

- h) 使用两种方法的可用代码，按照本章步骤复现第 12.3 节和第 12.4.1 节的结果。

假设你已成功完成这些项目，即可使用这些技术进行稳健的数据科学工作，以及/或在稳健机器学习领域解决新的研究问题。恭喜你，祝好运！

## 参考文献

- Aggarwal, C.C. (2017). _异常值分析_, 第2版. Springer.
- Cryer, J.D. 和 Chan, S.-K. (2008). _时间序列分析：R 语言应用_, 第2版. Springer.

## 索引

### a

- a
- 绝对序统计量 110
- Adam 优化器 296
- aLASSO 惩罚 145, 357
- 异常值定义 2
- 异常值检测 106, 303
- AUROC 272, 326, 357

### b

- b
- 后向传播 258, 260
- 批量梯度下降 264
- 偏差 43, 148, 253
- 偏差-方差权衡 146, 162, 227, 341
- 二分类 211
- 箱线图 98, 113

### c

- c
- 类别损失
- 交叉熵 283
- log-cosh 283
- 中央极限定理 43, 84
- 质心 20, 140
- 检验函数 190
- 聚类 14
- DBSCAN 308
- k-means 19
- k-中位数 21
- MADmax 316
- 多重共线性 134
- 凸性性质 47, 50, 60, 72, 217
- 相关系数 345
- 双曲余弦分布 75, 77
- 协方差矩阵 13, 17, 80, 134, 165, 205
- 交叉熵逻辑回归 (CELR) 225, 346
- 交叉熵损失 215, 258, 261
- 交叉熵神经网络 (CENN) 252, 264
- 交叉问题 189
- 累积分布函数 (CDF) 13, 40, 77, 111

### d

- d
- 数据集
  - 波士顿房价 82, 337
  - 糖尿病 108, 115, 123, 167, 199
  - MNIST 288
  - 瑞士 81, 109, 123, 142, 153, 199, 205, 206
  - 合成数据集 16, 231, 266
  - 泰坦尼克号 346
  - 葡萄酒 323
- DBSCAN 308
- 决策树 243
- 丢弃法 255

### e

- e
- 探索性数据分析 (EDA) 7, 101, 338, 346
- 弹性网惩罚 143
- 时代 264
- 估计量
  - 渐近正态性 43
  - 偏差 43
  - 一致性 43
- 估计量（续）
  - 定义 36
  - 性质 43
- 欧几里得距离 12
- 可解释人工智能 (XAI) 359
- 逻辑回归 360
- 神经网络 365

### f

- f
- F1 分数 269, 357
- 假阳性率 (FPR) 271, 326
- 正向传播 259
- 全连接神经网络 253

### g

- g
- 高斯分布 12
- 高斯混合 16, 17
- 梯度下降
  - 基本步骤 47
  - 动量 257, 293
  - rmsprop 294
  - 预热 295

### h

- h
- 厚尾分布 79
- 异方差性 188
- 直方图 100, 113, 305, 340
- 齐方差性 188
- Huber 方法
  - 基本方法 58
  - 连续性 59
  - 默认 δ = 1.345 59
  - 不连续性 61
- 双曲函数 71
- 超参数
  - 聚类 14
  - 定义 8
  - Huber 120
  - log-cosh 120
  - 岭 165

### i

- i
- 内点定义 2
- 隔离森林 311
- 迭代箱线图 114

### k

- k
- k 折交叉验证 171
- k-means 19
- k-中位数 21, 316, 317
- k 近邻中位数 (k-NM) 320
- k 近邻 (k-NN) 241, 304
- k 随机验证 171, 178

### l

- l
- L1 损失函数 40
- L1-范数 11
- L2 损失函数 40
- L2-范数 11
- 拉格朗日乘数 135, 237
- 拉普拉斯分布 41, 76, 79, 86
- LASSO 惩罚 137
- 大数定律 43
- LC-aLASSO 153, 176
- LC-ridge 174
- 学习率 ℓ 48, 257
- 最小绝对偏差 (LAD) 40, 54, 191
- 最小二乘估计 (LSE) 40, 52, 63
- 最小二乘神经网络 (LSNN) 342
- 轻尾分布 79
- 似然函数 46, 204
- 线性回归 36, 95, 107
- 指标 116
- Lloyd 风格迭代 15, 19
- 位置模型 55, 56
- log-cosh
  - 一般形式 85
  - 线性回归 74
  - 最大似然估计 83
  - 神经网络 251, 264
  - 统计性质 83
- log-cosh 逻辑回归 (LCLR) 225, 346
- log-cosh 神经网络 (LCNN) 252, 264, 281, 342, 343
- 逻辑回归 211, 346, 350, 360
- 对数似然 44, 84
- 损失函数
  - 定义 36
  - Huber 58
  - L1 40, 46, 187
  - L2 40, 46
  - log-cosh 69, 192
  - 分位数损失函数 190
  - LS-LASSO 153, 176
  - LS-ridge 140, 166, 170
- 历史 251
- 神经元 251, 253
- 训练 257
- XAI 365
- 标准化中位数绝对偏差 (MADN)
  - 10, 11, 27, 80, 104, 124, 317

### o

- OAR 图 110, 113
- 序统计量 9, 110
- 普通最小二乘法 (OLS) 53
- 异常值定义 2
- 异常值检测
  - 箱线图 98
  - 聚类 25
  - 直方图 100
- 异常值编辑规则 102, 109
  - 1.5-IQR 105, 109
  - 3-MADN 27
  - 3-sigma 25, 102
  - 4.5-MAD 104
- 异常值移除 105
  - 异常值检测 106
  - 迭代箱线图 114
  - 修剪 105
  - 威莎化 105
- 过拟合 161, 228

### m

- MADmax 316
- 曼哈顿距离 12
- 最大似然
  - 基本步骤 44
  - L1 46
  - L2 46
  - log-cosh 75, 83
- SMRQ 202
- 均值与中位数 9
- 均方误差 (MSE) 117, 119, 165, 169
- 中位数绝对偏差 (MAD) 11, 104, 318
- 中位数绝对误差 (MAE) 116, 118, 169, 171, 342, 344
- M-估计
  - 定义 49
  - Huber 58
  - log-cosh 71
- M-估计量 190, 194
- 小批量梯度下降 265
- 模型复杂度 162, 175
- 动量 293
- 多分类 281
- 多重共线性 133
- 多元线性模型 42, 52

### p

- 多项式展开 161, 232
- 精确率 269, 326, 329, 352
- 概率密度函数 (PDF) 13, 40, 75, 86, 202
- p 值 152

### q

- QP 图 196, 199, 201
- QQ 图 111
- 四分图 113
- 二次风险 163
- 分位数回归 187
  - 检验函数 190
  - 交叉问题 189

### n

- 神经网络 251, 281
  - 激活 255
  - 架构 254, 289, 339
  - 反向传播 260
  - 正向传播 259

