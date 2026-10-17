
# 5 应用人工智能案例——从数字到图像数据

## 5.4.1 回归

为了计算回归的指标，我们使用了 scikit-learn 的 `metrics` 模块。它拥有广泛问题的评估指标。参考 **5.1 简单线性回归**，我们使用线性回归预测波士顿数据集的价格。在将这些值传递给方法之前，我们确保它们是一维数组、长度相同且为数值。

```python
from sklearn.metrics import mean_squared_error, mean_absolute_error
mean_squared_error(y_test, prediction) #20.72
mean_absolute_error(y_test, prediction) #3.14
```

图 5.41 计算回归任务的平均绝对误差和均方误差

## 5.4.2 分类

与连续数据不同，分类的目标在本质上是类别的。分类的评估指标基于对正确预测和错误预测的计数。在上一章中，我们已经讨论了用于评估分类模型的一些评估指标。在本章中，我们将使用 scikit-learn 模块来计算这些评估指标。尽管深度学习框架对这些指标有自己的实现，但我们在这里不再介绍。例如，我们使用了第 5.3.2 节“深度学习方法：CNN”中的 PyTorch 模型。使用 PyTorch 进行推理并不像 TensorFlow 那么直接，我们将演示使用 PyTorch 进行推理，并利用结果计算分类问题的一些重要指标。随着训练开始，我们可以监控训练损失和验证损失的趋势。理想情况下，两种损失都会逐渐减少直到收敛。除了监控损失，我们可能还想监控训练和验证数据的其他评估指标，如准确率、精确率、召回率等。为了可视化，通用的方法是绘制损失和指标随训练步骤的变化。我们可以使用 matplotlib 来绘制验证损失和准确率，如图 5.42 所示。这是从 epoch 0 到 4 的 `val_loss` 变量。作为一个示例，仅展示了 5 个 epoch 的损失。可以通过编辑图 5.40 所示的代码创建这些变量来存储训练和验证损失。理想情况下，这两条线应该显示出下降趋势，且之间的差距最小。需要注意的是，该模型并未调优以获得良好。此外，此处显示的 epoch 数远少于通常使用的数量。

如前所述，推理 PyTorch 模型并不简单，因此在图 5.43 中，我们演示了显示推理的代码。注意最后两行，它们用于从张量（tensors）中提取值，因为 scikit-learn 不支持张量。

提取出真实值和预测值后，我们可以继续计算评估指标。视觉检查的广泛使用指标之一是混淆矩阵。要生成它，我们可以运行图 5.44 所示的代码。

我们可以计算 scikit-learn 提供的各种指标。例如，我们将查看计算准确率、精确率、召回率和 f1 分数（图 5.45）。

```python
fig, axs = plt.subplots(nrows = 1, ncols = 1)
axs.plot(val_loss_list, label = 'Validation loss')
axs.plot(train_loss_list, label = 'Training loss')
plt.legend()
plt.plot()
```

![](img/a499312facf6bd3577be03d7b7eddea9_120_0.png)

图 5.42 绘制验证损失和训练损失

## 5.5 总结

总之，本章提供了跨越不同数据类型的数据分析和机器学习技术的深度旅程。从关注金融和住房领域的数值数据分析开始。我们引入了简单线性回归的基本概念，然后探索了各种回归算法。转向文本数据，我们的注意力转向新数据以及浅学习技术在文本分类中的应用。本章还涉及文本数据分类的经典方法，并深入探讨了深度学习，重点是用于序列分析的长短期记忆（LSTM）网络。在整个章节中，我们强调了 TensorFlow 和 PyTorch 等流行深度学习框架的重要性。

转向视觉数据，我们的之旅继续深入探讨医学图像分析。我们演示了如何使用浅学习技术和强大的卷积神经网络（CNNs）对视觉数据进行分类。本章最后提醒了 TensorFlow 和 PyTorch 在视觉数据深度学习背景下的关键作用。为了更好地了解医学图像信息学领域的前沿文献，我们参考了 [9–21]，因为我们考虑了该领域所有可能的数据类型。

本质上，本章对数据分析和机器学习方法提供了一个全面且平衡的视角，适合广泛的读者。金融、住房和医学图像的真实案例研究增加了内容的实用相关性，使其对于希望在不同领域应用这些技术的数据科学家和机器学习爱好者来说，是一份引人入胜且信息丰富的资源。有关更详细的深度学习或基于 CNN 的机器学习模型，请参考我们之前的书籍 [9, 22]。

## References

- 1. P. Refailizadeh, L. Tang, H. Liu, Cross-validation, in Encyclopedia of Database Systems (Springer US, 2009), pp. 532–538. https://doi.org/10.1007/978-0-387-3940-9

- 2. H. Ahmed, I. Traore, S. Saad, Detecting opinion spans and fake news using text classification. Secur. Priv. 1(1) (2018). https://doi.org/10.1002/spy2

- 3. H. Ahmed, I. Traore, S. Saad, Detection of Online Fake News using N-Gram Analysis and Machine Learning Techniques (2017), pp. 127–138. https://doi.org/10.1007/978-3-319-691-5

- 4. U. Parida, M. Nayak, K. Nayak. Text categorization using random forest and Nave Bayes, in 2021 1st Odisha International Conference on Electrical Power Engineering, Communication and Computing Technology (ODICON) (IEEE, 2021), p. 1–4. https://doi.org/10.1109/ODICON5056.2021.942895

- 5. M. Sudhakar, Estimation of precision in news detection using Bert algorithm and comparison with random, in 2022 International Conference on Intelligent Computing and Control Technologies (ICICIT) (IEEE, 2022), p. 217–223. https://doi.org/10.1109/ICICIT5457.2022.991762

- 6. T. Shak, X. Tao, C. Dunn, Y. Li. Sentiment and opinion mining over educational data: a survey. Nat. Lang. Process. (2023), https://doi.org/10.1016/j.ipl.2023

- 7. Y. Li, Research and application of deep learning in medical imaging, in 2022 Second International Conference on Electronics, Applications (IPECA) (IEEE, 2022), p. 994–999. https://doi.org/10.1109/IPECA53709.2022

- 8. X. Wang, Y. Peng, Chest-ray, in 2017 IEEE Conference on Computer Vision and Pattern Recognition (CVPR), p. 3462–3471. https://doi.org/10.1109/CVPR.2017

- 9. KC Santos, Covid-19 Virus Analyzing Chest Images Using Deep Ensemble Neural Network. Int. J. Art. Intell. Tools 31(08), 2250349 (2022)

- 10. KC Santos, Covid-19 images: how big is? J. Med. Syst. 45(4), 71 (2021)

- 11. D. Ruikar, KC Santos, CT fractures, J. Med. Syst. 45(4), 51 (2021)

- 12. Aamir, KC Santos, Explainable AI for glaucoma prediction to understand risk factors in treatment planning. IEEE Trans. Med. Health Info 27(3), 1214–1215 (2023)

- 13. KC Santos, S. Rajaraman, Deep learning for tuberculosis abnormalities in chest-rays. Int. J. Mach. Learn. 14(8), 2659 (2023)

- 14. KC Santos, D. Ghosh, A systematic review of deep learning for tuberculosis using X-rays from 2020 to 2022. Healthcare 11(7), 2388 (2023)

- 15. KC Santos, N. Nakami, A systematic review of COVID-19 screening using chest CT. (2022)

- 16. KC Santos, M. Mamun, A systematic review on cough sound for covid-19 diagnosis. Peer Comput. Sci. 8,9 (2022)

## 附录：代码清单

### 图 5.38 用于加载和预处理的 Dataset 类

```python
class Dataset(torch.utils.data.Dataset):
    def __init__(self, df, path, transforms=None):
        self.df = df
        self.path = path
        self.image_paths = self.df['Image Index']
        self.labels = self.df['Finding Labels']
        self.transforms = transforms

    def __len__(self):
        return len(self.df)

    def __getitem__(self, index):
        '生成一个数据样本'
        # 选择样本
        image_path = self.image_paths[index]
        label = self.labels[index]
        image = cv2.imread(os.path.join(self.path, label))
        if self.transforms:
            image = self.transforms(image)
        return image, 0 if label=='No Finding' else 1

transform = transforms.Compose([
    transforms.ToTensor(),
    transforms.Normalize(
        (0.5, 0.5, 0.5),
        (0.5, 0.5, 0.5)
    ),
    transforms.Resize([128, 128]),
])
df = pd.read_csv(os.path.join(PATH, 'dataset.csv'))
ds = Dataset(df, os.path.join(PATH, 'images'), transform)
train_dataset, test_dataset = torch.utils.data.random_split(ds, [0.8, 0.2])
```

### 图 5.39 模型定义与初始化

```python
import torch.nn as nn
import torch.nn.functional as F
device = torch.device('cuda:0' if torch.cuda.is_available() else 'cpu')

class Net(nn.Module):

    def __init__(self):

        super().__init__()

        self.conv1 = nn.Conv2d(3, 6, 5)

        self.pool = nn.MaxPool2d(2, 2)

        self.conv2 = nn.Conv2d(6, 16, 5)

        self.f1 = nn.Linear(16 * 29 * 29, 120)

        self.f2 = nn.Linear(120, 84)

        self.f3 = nn.Linear(84, 1)

    def forward(self, x):

        x = self.pool(F.relu(self.conv1(x)))

        x = self.pool(F.relu(self.conv2(x)))

        x = torch.flatten(x, 1)

        x = F.relu(self.f1(x))

        x = F.relu(self.f2(x))

        x = torch.sigmoid(self.f3(x))

        return x

net = Net()

net.to(device)

criterion = nn.BCELoss()

optimizer = optim.Adam(net.parameters(), lr=0.001)
```

### 图 5.40 训练循环

```python
batch_size = 4
trainloader = torch.utils.data.DataLoader(
  train_dataset,
  batch_size=batch_size,
  shuffle=True,
  num_workers=2)

testloader = torch.utils.data.DataLoader(
  test_dataset,
  batch_size=batch_size,
  shuffle=False,
  num_workers=2)

for epoch in range(EPOCHS):
  running_loss = 0.0
  accuracy=[]
  for i, data in enumerate(trainloader, 0):
    net.train()
    net.to(device)
    inputs, labels = data[0].to(device), data[1].to(device)
    optimizer.zero_grad()
    outputs = net(inputs)
    acc = (outputs.round()) == labels.float().mean()

    accuracy.append(acc)
    loss = criterion(outputs, labels.unsqueeze(1).float())
    loss.backward()
    optimizer.step()
    if i % 100 == 0:
      print(...)
```

### 图 5.43 PyTorch 中的推理

```python
net.eval()
net.to(device)
val_loss = 0
correct = 0
gt_list = []
prediction_list = []
with torch.no_grad():
    acc = []
    for i, data in enumerate(testloader):
        inputs, labels = data[0].to(device), data[1].to(device)
        output = net(inputs).argmax(dim = -1)
        prediction_list.extend(output)
        gt_list.extend(labels)

gt_list = [x.item() for x in gt_list]
prediction_list = [x.item() for x in prediction_list]
```
