

```python
inputs_for_prd = sc.transform(inputs_for_prd) # 缩放，仅"transform"，不进行"fit"

# 创建测试集的数据结构
test_data_size = inputs_for_prd.shape[0]
X_test = []
# 没有 "y_test" = []，我们将对其进行预测

for i in range(60, test_data_size):
    X_test.append(inputs_for_prd[i-60, i])

# 将 X_test 转换为 NumPy 数组
X_test = np.array(X_test)

# 重塑
X_test = np.reshape(X_test, (X_test.shape[0], X_test.shape[1], 1))

# --- 进行预测 ---
y_pred = regressor_mn.predict(X_test)
predicted_stock_price = sc.inverse_transform(y_pred)

# --- 可视化结果 ---
print(f"--- 真实股票价格 ---\n")
print(f"{real_stock_price}    \n")
print(f"------------------------------------------------------\n")
print(f"--- 预测股票价格 ---\n")
print(f"{predicted_stock_price}    \n")
print(f"--------------------------------------\n")

plt.plot(real_stock_price, color='red', label='2017年1月的谷歌股价')
plt.plot(predicted_stock_price, color='blue', label='2017年1月的预测谷歌股价')
plt.title('谷歌股价预测')
plt.xlabel('时间')
plt.ylabel('谷歌股价')
plt.legend()
plt.show()

# prctrnn.py

# 第12章：第4部分

# 深度学习

# RNN：评估、改进和调优

# 评估与性能

### 12.4.1 评估模型性能

在之前的章节中，RNN 构建了一个回归器，我们正在尝试预测连续结果（谷歌股价）。对于回归，评估模型性能的方法是使用 **RMSE**（均方根误差）。它的计算方法是预测值与真实值之间平方差的平均根。

> RMSE 没有帮助：对于我们特定的股价预测问题，使用 RMSE 评估模型没有意义，因为我们更感兴趣预测的方向，而不是它们与真实股价的接近程度。我们希望预测的方向与真实股价的方向一致。预测值可能接近，但方向往往与真实股价相反。

如果你对用于计算 RMSE 的代码感兴趣，请看下文：

```python
import math
from sklearn.metrics import mean_squared_error
rmse = math.sqrt(mean_squared_error(real_stock_price, predicted_stock_price))
```

然后考虑这个 2007年1月谷歌股价范围（大约是800）的 RMSE，作为相对误差，而不是绝对误差。如果 RMSE 为 50，那么误差将会很大，但如果股价范围在 100 左右，它就会很小。

### 12.4.2 调优以改进 RNN

- [1]. 获取训练数据：我们在过去 5 年的谷歌股价上训练了模型，但使用过去 10 年的数据可能会更好。
- [2]. 增加时间步（Timesteps）：我们对过去 60 天的股价进行了建模以预测下一日的股价。你可以尝试增加时间步到 120（6个月）。
- [3]. 添加一些指标：如果你有与其他公司相关的财务见解，你可以将此股价作为真实指标添加。
- [4]. 添加 LSTM 层：我们构建了 4 层 LSTM，你可以尝试添加更多层。
- [5]. 在 LSTM 层中添加更多神经元：我们强调了需要大量的神经元来应对复杂问题，我们在每层 LSTM 中都选择了 50 个神经元。你可以尝试具有更多神经元的架构（或更多层）。

### 12.4.3 调优以改进 RNN

你可以对 RNN 模型进行一些参数调优。记住，这次我们处理的是回归问题，即预测连续的结果（谷歌股价）。回归的参数调优与你在第11章中学习的分类调优相同，唯一的不同是你需要替换：

```python
scoring = 'accuracy'
```
为：
```python
scoring = 'neg_mean_squared_error'
```
在 `GridSearchCV` 类中。

# 第12章：第4部分

# 深度学习

RNN: GRU

RNN 的变体

### 12.4.1 GRU：门控单元

- 门控单元（GRUs）是 Cho 等人在2014 年引入的一种 RNN 门控机制。GRU 是带有遗忘门的 LSTM，但参数比 LSTM 少。
- 发现 GRU 在多音音乐、语音建模和自然语言处理（NLP）某些任务上的性能与 LSTM 相似。
- 适用于较小数据集：已证明 GRUs 在较小且频率较低的数据集上表现出更好的性能。（img/0aa092657a6eb12dd65bbb7905a3_420_0.png) 类型 1 (img/0aa092657a6eb12dd65bbb7905a3_420_1.png) 类型 2 (img/0aa092657a6eb12dd65bbb7905a3_420_2.png) 类型 3 门控单元，全门控版本 (img/0aa092657a6eb12dd65bbb7905a3_420_3.png)

> 全门控单元有几种变体，包括使用之前的隐藏状态和各种组合的偏置，以及一种简化的最小门控单元。代码完全相同，我们只是将 LSTM 替换为 GRU。100 个 epoch，ADAM，

| 真实股票价格 | 预测股票价格 |
|---|---|
| 778.61 | 779.178 |
| 786.36 | 789.262 |
| 788.08 | 793.8223 |
| 795.26 | 794.0254 |
| 804.4 | 797.9517 |
| 807.86 | 804.1133 |
| 804.9 | 806.0781 |
| 807.14 | 807.5827 |
| 804.65 | 809.0453 |
| 805.07 | 810.9257 |
| 805.61 | 811.3199 |
| 801.25 | 812.4463 |
| 806.91 | 814.6460 |
| 809.25 | 816.9644 |
| 822.3 | 822.4189 |
| 829.62 | 826.0972 |
| 831.78 | 829.0862 |
| 834.71 | 834.26086 |
| 814.65 | 834.316 |
| 796.86 | 835.4504
Epoch 1/100, loss: 8.4504, val_loss: 8.3918
Epoch 2/100, loss: 8.3918, val_loss: 8.1623
Epoch 3/100, loss: 8.1623, val_loss: 8.0254
Epoch 4/100, loss: 8.0254, val_loss: 7.9517
Epoch 5/100, loss: 7.9517, val_loss: 7.1133
Epoch 6/100, loss: 7.1133, val_loss: 7.0781
Epoch 7/100, loss: 7.0781, val_loss: 7.5827
Epoch 8/100, loss: 7.5827, val_loss: 7.0453
Epoch 9/100, loss: 7.0453, val_loss: 7.9257
Epoch 10/100, loss: 7.9257, val_loss: 8.3199
Epoch 11/100, loss: 8.3199, val_loss: 8.4463
Epoch 12/100, loss: 8.4463, val_loss: 8.6460
Epoch 13/100, loss: 8.6460, val_loss: 8.9644
Epoch 14/100, loss: 8.9644, val_loss: 8.4189
Epoch 15/100, loss: 8.4189, val_loss: 8.0972
Epoch 16/100, loss: 8.0972, val_loss: 8.0862
Epoch 17/100, loss: 8.0862, val_loss: 8.2608
Epoch 18/100, loss: 8.2608, val_loss: 8.3450
Epoch 19/100, loss: 8.3450, val_loss: 8.2518
Epoch 20/100, loss: 8.2518, val_loss: 8.0254
