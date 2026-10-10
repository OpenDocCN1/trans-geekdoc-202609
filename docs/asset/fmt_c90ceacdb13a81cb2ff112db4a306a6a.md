
```python
from turtle import clone

import pandas as pd

import numpy as np

import torch

import torch.nn as nn

import torch.nn.parallel

import torch.optim as optim

import torch.utils.data

from torch.autograd import Variable
```

# 导入数据集

# 准备训练集和测试集

`training_set = pd.read_csv("/movie_lens_100k/u.base", delimiter="\t")`

`test_set = np.array(training_set, dtype="int")`

`ts_test = pd.read_csv("/movie_lens_100k/u.base", delimiter="\t")`

`test_set = np.array(ts_test, dtype="int")`

# 获取用户和电影的数量

`nb_users = int(max(training_set[:, 0]), max(test_set[:, 0]))`

`nb_movies = int(max(training_set[:, 1]), max(test_set[:, 1]))`

# 将数据转换为用户为行、电影为列的数组

```python
def convertdata(data):
    new_data = []
    for user_id in range(1, nb_users + 1):
        # 使用 "user_id, == user_id" 作为电影列 "data[:,,1]" 的条件
        movie_ids = data[:, 1][data[:, 0] == user_id] # 返回一个列表

# 使用 data[:, 0] = id_user 作为评分列 data[:, 2] 的条件
id_ratings = data[:, 2][data[:, 0]==id_user]

# 向量数量
ratings = np.zeros(nb_movies)
ratings[id_movies - 1] = id_ratings
new_data.append(list(ratings))
return
new_data
```

`train_set_cvnt = convert(train_set)`

`test_set_cvnt = convert(test_set)`

# 将数据转换为 Torch Tensor。以下是评分的 Tensor

`train_set_tensor = torch.FloatTensor(train_set_cvnt)`

`test_set_tensor = torch.FloatTensor(test_set_cvnt)`

# --- 创建 SAE 的神经网络架构

```python
class StackedAutoEncoders(nn.Module):
    def __init__(self):
        super(StackedAutoEncoders, self).__init__()
        self.fc1 = nn.Linear(nb_movies, 20)
        self.fc2 = nn.Linear(20, 10)
        self.fc3 = nn.Linear(10, 20)
        self.fc4 = nn.Linear(20, nb_movies)
        self.activation = nn.Sigmoid()

    def forward(self, x):
        x = self.activation(self.fc1(x))
        x = self.activation(self.fc2(x))
        x = self.activation(self.fc3(x))
        x = self.fc4(x)
        return x
```

`sae = StackedAutoEncoders()`

`criterion = nn.MSELoss()`

`optimizer = optim.RMSprop(sae.parameters(), lr=0.01, weight_decay=0.5)`

# --- 训练 SAE

`nb_epoch = 20`

```python
for epoch in range(1, nb_epoch + 1):
    train_loss = 0
    s = 0
    for id_user in Variable(train_set_tensor.unsqueeze(0)):
        target = id_user.clone()
        non_zero_ratings = torch.sum(target > 0)
        if non_zero_ratings > 0:
            output = sae(id_user)
            output[target == 0] = 0
            loss = criterion(output, target)
            mean_corrector = nb_movies/float(non_zero_ratings + 1e-10)
            loss.backward()
            train_loss += torch.sqrt(loss.data) * mean_corrector
            s += 1
        optimizer.step()
    train_loss_normalized = train_loss/s
    print(f'Epoch: {epoch}, loss = {train_loss_normalized}')
```

# 测试模型：使用测试集计算 "test_loss"

这里我们计算测试集的损失，并希望比真实评分更好。

- 类似于 RBM 模型，我们不需要循环，因为我们没有在训练模型。
- 我们不需要通过 epoch 来衡量测试集性能以衡量损失，显然只需要一个 epoch，因为我们要衡量全局损失，只需要内部循环，代码遍历数据中的所有用户。
- 对于目标向量，我们不选择测试集作为输入向量，而是使用训练集。因为 `test_loss` 计算测试集上的损失。我们将其初始化为 0。

```python
test_loss = 0
cnt = 0.0
for uid in range(nb_users):
    v = Variable(train_set[uid]).squeeze(0) # 来自训练集的输入向量
    vt = Variable(test_set[uid]).squeeze(0) # 来自测试集的目标向量
```

模型的输入是我们看过的电影的所有评分。我们在输入向量中训练测试集：

- 我们将此输入向量放入 AE 网络，AE 将查看电影评分并预测正评分，根据这些评分，它将预测用户未看到的电影评分（测试集中不存在的评分）。这就是预测。
- 这里使用测试集作为目标向量的意义：它包含了训练集中不存在的电影真实评分（我们使用 AE 生成了它们），因此我们可以比较预测和真实评分并衡量 `test_loss`。
- `test_loss` 将指示我们的模型在新数据上的表现。

例如，如果我们使用输入向量为看过的电影评分，那么当我们将此输入向量馈网络时，与动作电影相关的特定神经元将以较大的权重激活：为用户未看到的其他电影给出高分。

然后，我们将预测评分与测试集的评分进行比较，因为测试集包含了不属于训练集的评分。即这些用户在训练集中尚未看过的电影。

```python
test_loss = 0
cnt = 0.0
for uid in range(nb_users):
    v = Variable(train_set[uid]).squeeze(0)
    vt = Variable(test_set[uid]).squeeze(0)
    non_zero_ratings_t = torch.sum(vt.data)
    if non_zero_ratings_t > 0:
        t_output = sae(v)
        vt.require_grad = False
        loss_t = criterion(t_output[vt == 0], vt)
        mean_corrector_t = nb_movies/float(non_zero_ratings_t + 1e-10)
        cnt += np.sqrt(loss_t.data) * mean_corrector_t
    cnt += 1.0
```

`eval_loss = test_loss/cnt`

`print(f"Evaluation Loss = {eval_loss}")`

- 预测发生在这里：`test_output = sae(v)`。AE 模型在训练后只是向前执行一步。
- 我们的 `forward` 函数返回评分向量，因此通过在这里对输入调用我们的对象，我们将获得用户未看电影的预测评分，这将进入 `test_output`。
- 我们使用 `vt.require_grad = False` 是因为我们不需要相对于目标的梯度。

为了计算测试集中的真实评分与训练集预测评分之间的损失。

我们还需要测试集的 `mean_corrector`。

```python
mean_corrector = nb_movies/float(non_zero_ratings + 1e-10)
```

最后我们计算 `test_loss` 并增加计数器 `cnt`。

```python
test_loss += torch.sqrt(loss_t.data) * mean_corrector
```

循环结束后，我们计算归一化损失并打印结果：

```python
eval_lossSS = test_loss/cnt
print(f"Evaluation or Test = {eval_lossSS}")
```

构建了一个稳健的推荐系统。测试损失为 0.05 星，小于一颗星。所以例如，如果你使用推荐系统来选择今晚要看的电影，假设我们给这部电影打了四星，那么这个推荐系统会预测你对这部电影的评分会在三到五星之间。

```python
nb_movies = int(max(max(train_set, [1]), max(test_set, [1])))
```

```python
# 将数据转换为数组，行表示用户，列表示电影
def convert(data):
    new_data = []
    for id_user in range(1, nb_movies + 1):
        # 使用 data[:,id_user] 作为电影列 "data[:, 1]" 的过滤条件
        id_movies = data[:, 1][data[:, 0]==id_user] # 返回一个列表
        # 使用 data[:,id_user] 作为评分列 "data[:, 2]" 的过滤条件
        ratings = data[:, 2][data[:, 0]==id_user]
        # 零向量
        ratings = np.zeros(nb_movies)
        ratings[id_movies - 1] = id_ratings
        new_data.append(list(ratings))
    return new_data
```

`trn_set_cvt = convert(train_set)`

`tst_set_cvt = convert(test_set)`

```python
# 将数据转换为 Torch Tensors。以下是评分的张量
train_set_tensor = torch.FloatTensor(trn_set_cvt)
tst_set_tensor = torch.FloatTensor(tst_set_cvt)
```

```python
# 构建 SAE 神经网络的架构 ----- 
class StackedAutoEncoders(nn.Module):
    def __init__(self):
        super(StackedAutoEncoders, self).__init__()
        self.fc1 = nn.Linear(nb_movies, 20)
        self.fc2 = nn.Linear(20, 10)
        self.fc3 = nn.Linear(10, 20)
        self.fc4 = nn.Linear(20, nb_movies)
        self.activation = nn.Sigmoid()

    def forward(self, x):
        x = self.activation(self.fc1(x))
        x = self.activation(self.fc2(x))
        x = self.activation(self.fc3(x))
        x = self.fc4(x)
        return x
```

```python
sae = StackedAutoEncoders()
criterion = nn.MSELoss()
optimizer = optim.RMSprop(sae.parameters(), lr=0.01, weight_decay=0.5)
# 训练 SAE 模型 -----
```

`b_movies = 200`

```python
for epoch in range(1, nb_epoch+1):
    train_loss = 0.0
    for id_user in range(nb_users):
        input = Variable(train_set_tensor[id_user]).unsqueeze(0)
        target = input.clone()
        non_zero_ratings = torch.sum(target.data, 0)
        if non_zero_ratings > 0:
            output = sae(input)
            output.grad = False
            output[target == 0] = 0
            loss = criterion(output, target)
            mean_corrector = nb_movies/float(non_zero_ratings + 1e-10)
            loss.backward()
            train_loss += np.sqrt(loss.data)*mean_corrector
        s += 1.0
        optimizer.step()
```

```python
train_normalized = train_loss/s
print(f"Epoch: {epoch}, loss = {train_loss_normalized}")
```

# 在测试集上测试 SAE 模型 -

# 在测试集上评估 SAE

`test_set_ratings_list = []`

`predicted_rating_list = []`

```python
test_loss = 0
cnt = 0
for u in range(nb_users):
    u_id = u # 根据上下文假设的变量名
    v = Variable(train_test_set[u_id]).unsqueeze(0) # 来自训练集的输入向量
    vt = Variable(test_test_set[u_id]).unsqueeze(0) # 来自“测试集”的标签向量
    non_zero_ratings_ts = torch.sum(vt.data)
    if non_zero_ratings_ts > 0:
        test_output = sae(vt)
        vt.requires_grad = False
        test_output[vt == 0] = 0 # 避免测试集中未评分的电影
        loss = criterion(test_output, vt) # 比较
        mean_corrector_ts = nb_movies/float(non_zero_ratings_ts + 1e-10)
        test_loss += np.sqrt(loss.data.mean() - mean_corrector_ts)
        cnt += 1
```

# 创建原始与预测评分的列表：Tensor 到 NumPy 数组的转换

# 现在我们使用 detach() 将张量转换为 NumPy 数组

# 因为我们的张量需要 "grad"

# 我们已经这样做过了

```python
original_ratings = vt.detach().numpy()
test_ratings_list.append(original_ratings)
predicted_ratings = output.detach().numpy() # 在测试集上的预测
```

```python
eval_loss = test_loss/cnt
print(f"Evaluation loss: {eval_loss}")
```
