
22 # （通常由整数索引）。
23 # torchvision.datasets 模块包含用于加载
24 # 流行机器学习数据集的函数，可能包括下载和数据
25 # 转换功能。

27 # 这里我们加载 MNIST 数据集，其中包含 28x28 灰度图像
28 # 为手写数字，带有相应的标签
29 # 取值在 {0, 1, ..., 9} 之间。

31 # 首先加载数据集的训练部分，如果本地
32 # 文件夹 ./data 中尚未存在，则从在线源下载数据
33 # 并将数据转换为 PyTorch Tensor。
34 mnist_train = datasets.MNIST(
35        "/data",
36        train=True,
37        transform=transforms.ToTensor(),
38        download=True,
39 )
40 # 接下来加载测试部分
41 mnist_test = datasets.MNIST(
42        "/data",
43        train=False,
44        transform=transforms.ToTensor(),
45        download=True,
46 )

48 # data.utils.DataLoader 类允许迭代数据集进行
49 # 训练和验证。它支持例如批量处理和
50 # 数据集洗牌等功能。

52 # 构建一个 DataLoader，在迭代时返回小批量
53 # 大小为 64 个实例，这些实例取自训练集的随机排列
54 #
55 train_loader = data.DataLoader(
56        mnist_train, batch_size=64, shuffle=True
57 )
58 # 测试数据集的加载器不需要洗牌
59 test_loader = data.DataLoader(
60        mnist_test, batch_size=64, shuffle=False
61 )

63 # 定义一个具有 3 个卷积层的神经网络，每个层
64 # 后跟一个 ReLU 激活函数，然后是两个仿射层，
65 # 第一个层后跟一个 ReLU 激活函数
66 net = nn.Sequential(  # 输入形状 (N, 1, 28, 28)
67    nn.Conv2d(1, 5, 5),   # (N, 5, 24, 24)
68    nn.ReLU(),
69    nn.Conv2d(5, 5, 5),   # (N, 5, 20, 20)
70    nn.ReLU(),

### 7.9. *自适应矩估计 SGD 优化*
*(Adam)*

71    nn.Conv2d(5, 3, 5), # (N, 3, 16, 16)
72    nn.ReLU(),
73    nn.Flatten(), # (N, 3 * 16 * 16) = (N, 768)
74    nn.Linear(768, 128), # (N, 128)
75    nn.ReLU(),
76    nn.Linear(128, 10), # 输出形状 (N, 10)
77 ).to(device)
78
79 # 定义损失函数。对于每一个自然数 d，对于
80 # R^d 中的标准基向量 e_1, e_2, ..., e_d，对于
81 # d 维交叉熵损失函数 L，以及
82 # d 维 softmax 激活函数 A，这里定义的函数 loss_fn
83 # 满足对于所有 x 属于 R^d 和所有自然数
84 # i 属于 [0,d]，有
85 #   loss_fn(x, i) = L(A(x), e_i)。
86 # 函数 loss_fn 还接受输入批次，在这种情况下
87 # 它将返回相应输出的平均值。
88 loss_fn = nn.CrossEntropyLoss()
89
90 # 定义优化器。我们使用 Adam SGD 优化方法。
91 optimizer = optim.Adam(net.parameters(), lr=1e-3)
92
93 # 该函数计算模型在整个
94 # 测试集上的平均损失以及模型预测的准确率。
95 def compute_test_loss_and_accuracy():
96     total_test_loss = 0.0
97     correct_count = 0
98     with torch.no_grad():
99         # 在每次迭代中，test_loader 将产生一个
100         # 带有相应标签的小批量图像
101         for images, labels in test_loader:
102             # 将数据移动到设备上
103             images = images.to(device)
104             labels = labels.to(device)
105             # 计算神经网络在当前的
106             # 小批量上的输出
107             output = net(images)
108             # 计算交叉熵损失的平均值
109             loss = loss_fn(output, labels)
110             # 对于累积的 total_test_loss，我们将 loss
111             # 乘以批次大小（如上文指定，通常为 64，
112             # 但对于最后一个批次可能会更小）。
113             total_test_loss += loss.item() * images.size(0)
114             # 对于每个输入，预测的标签是输出向量中
115             # 最大分量所在的索引。
116             pred_labels = torch.max(output, dim=1).indices
117             # pred_labels == labels 按分量比较两个向量
118             # 并返回一个布尔向量。
119             # 对该向量求和即可统计 True
120             # 条目的数量。
121             correct_count += torch.sum(
122                 pred_labels == labels
123             ).item()
124     avg_test_loss = total_test_loss / len(mnist_test)
125     accuracy = correct_count / len(mnist_test)
126     return (avg_test_loss, accuracy)
127
128
129 # 初始化一个列表，用于保存在训练期间每个
130 # 批次计算出的损失
131 train_losses = []
132
133 # 每 10 个批次，我们将计算整个测试集上的
134 # 损失以及模型在整个测试集上的预测准确率。
135 # 我们这样做是为了在生成的图表中展示
136 # 人工神经网络的泛化能力。
137 # 然而，如此频繁地计算这些损失和准确率，且使用
138 # 相对较大的数据点集合（与训练
139 # 集相比）计算成本极高（大部分训练
140 # 运行时间将花费在计算这些值上），因此
141 # 在正常神经网络训练期间不建议这样做。
142 # 通常，测试集仅在最后用于判断
143 # 最终训练好的网络的性能。经常使用第三个
144 # 数据点集合，称为验证集（不用于直接训练
145 # 网络也不用于最终评估），用来
146 # 判断过拟合或调整超参数。
147 test_interval = 10
148 test_losses = []
149 accuracies = []
150
151 # 我们运行 5 个 epoch 的训练，即 5 次完整的
152 # 遍历训练集。
153 i = 0
154 for e in range(5):
155     for images, labels in train_loader:
156         # 将数据移动到设备上
157         images = images.to(device)
158         labels = labels.to(device)
159
160         # 将梯度置零
161         optimizer.zero_grad()
162         # 计算神经网络在当前的
163         # 小批量上的输出
164         output = net(images)
165         # 计算交叉熵损失
166         loss = loss_fn(output, labels)
167         # 计算梯度
168         loss.backward()
169
170     # 更新神经网络的参数
171     optimizer.step()
172
173     # 将当前损失追加到训练损失列表中。
174     # 注意，跟踪训练损失的
175     # 计算成本基本上为零（因为我们本来就要
176     # 计算这些值），因此通常在神经网络训练中
177     # 进行此操作以衡量训练
178     # 进度。
179     train_losses.append(loss.item())
180
181     if (i + 1) % test_interval == 0:
182         # 计算测试集上的平均损失和
183         # 模型的准确率，并将这些值追加到
184         # 相应的列表中
185         test_loss, accuracy = compute_test_loss_and_accuracy()
186         test_losses.append(test_loss)
187         accuracies.append(accuracy)
188
189         i += 1
190
191 fig, ax1 = plt.subplots(figsize=(12, 8))
192 # 我们在同一图表中绘制训练损失、测试损失和准确率
193 # 但使用两个不同的 y 轴
194 ax2 = ax1.twinx()
195
196 # 对损失使用对数刻度
197 ax1.set_yscale("log")
198 # 对准确率使用 logistic 刻度
199 ax2.set_yscale("logit")
200 ax2.set_ylim((0.3, 0.99))
201 N = len(test_losses) * test_interval
202 ax2.set_xlim((0, N))
203 # 绘制训练损失
204 (training_loss_line,) = ax1.plot(
205     train_losses,
206     label="Training loss (left axis)",
207 )
208 # 绘制测试损失
209 (test_loss_line,) = ax1.plot(
210     range(0, N, test_interval),
211     test_losses,
212     label="Test loss (left axis)",
213 )
214 # 绘制准确率
215 (accuracies_line,) = ax2.plot(
216     range(0, N, test_interval),
217     accuracies,
218     label="Accuracy (right axis)",
