

源代码 7.12 (*code/mnist.py*)：使用 PYTORCH 在 MNIST 数据集上训练人工神经网络（ANN）的 PYTHON 代码。此代码生成一个图表，展示测试集上平均损失的进展情况以及模型预测的准确率，见图 7.4。

```python
    color="red",
    )
    ax2.yaxis.set_major_formatter(ScalarFormatter())
    ax2.yaxis.set_minor_formatter(NullFormatter())

    # Put all the labels in a common legend
    lines = [training_loss_line, test_loss_line, accuracies_line]
    labels = [l.get_label() for l in lines]
    ax2.legend(lines, labels)

    plt.tight_layout()
    plt.savefig("../plots/mnist.pdf", bbox_inches="tight")
```

![](img/dec290f673e6357c31893c67b579ffe1_329_0.png)

图 7.4 (*plots/mnist.pdf*)：由源代码 7.12 生成的图表，显示了训练期间每个小批量（minibatch）使用的平均损失（训练损失），以及测试集上的平均损失和训练过程中模型预测的准确率。

源代码 7.13 比较了本章中介绍的几种优化方法在 MNIST 数据集上训练 **ANN** 时的性能，即：定义 **7.2.1** 中介绍的普通 **SGD** 优化方法、定义 **7.4.1** 中介绍的带动量的 **SGD** 优化方法、定义 **7.5.3** 中介绍的简化 Nesterov 加速 **SGD** 优化方法、定义 **7.6.1** 中介绍的 Adagrad **SGD** 优化方法、定义 **7.7.1** 中介绍的 RMSprop **SGD** 优化方法、定义 **7.8.1** 中介绍的 Adadelta **SGD** 优化方法，以及定义 **7.9.1** 中介绍的 Adam **SGD** 优化方法。该代码生成了两个图表，分别展示了训练损失的进展情况以及模型在测试集上预测准确率的进展情况，见图 **7.5**。请注意，这仅在一个特定问题上比较了这些优化方法的性能，且未针对所考虑的优化方法选择良好的超参数做出任何努力。因此，这些结果并不一定代表这些优化方法在一般情况下的性能。

```python
import torch
import torchvision.datasets as datasets
import torchvision.transforms as transforms
import torch.nn as nn
import torch.utils.data as data
import torch.optim as optim
import matplotlib.pyplot as plt
from matplotlib.ticker import ScalarFormatter, NullFormatter
import copy

# Set device as GPU if available or CPU otherwise
device = torch.device(
    "cuda" if torch.cuda.is_available() else "cpu"
)

# Fix a random seed
torch.manual_seed(0)

# Load the MNIST training and test datasets
mnist_train = datasets.MNIST(
    "./data",
    train=True,
    transform=transforms.ToTensor(),
    download=True,
)

mnist_test = datasets.MNIST(
    "./data",
    train=False,
    transform=transforms.ToTensor(),
    download=True,
)

train_loader = data.DataLoader(
    mnist_train, batch_size=64, shuffle=True
    )
    test_loader = data.DataLoader(
            mnist_test, batch_size=64, shuffle=False
    )

    # Define a neural network
    net = nn.Sequential(  # input shape (N, 1, 28, 28)
        nn.Conv2d(1, 5, 5),   # (N, 5, 24, 24)
        nn.ReLU(),
        nn.Conv2d(5, 3, 3),   # (N, 5, 22, 22)
        nn.ReLU(),
        nn.Conv2d(5, 3, 3),   # (N, 3, 20, 20)
        nn.ReLU(),
        nn.Flatten(),   # (N, 3 * 16 * 16) = (N, 1200)
        nn.Linear(1200, 128),   # (N, 128)
        nn.ReLU(),
        nn.Linear(128, 10),   # output shape (N, 10)
    ).to(device)

    # Save the initial state of the neural network
    initial_state = copy.deepcopy(net.state_dict())

    # Define the loss function
    loss_fn = nn.CrossEntropyLoss()

    # Define the optimizers that we want to compare. Each entry in the
    # list is a tuple of a label (for the plot) and an optimizer
    optimizers = [
        # For SGD we use a learning rate of 0.001
        (
            "SGD",
            optim.SGD(net.parameters(), lr=1e-3),
        ),
        (
            "SGD with momentum",
            optim.SGD(net.parameters(), lr=1e-3, momentum=0.9),
        ),
        (
            "Nesterov SGD",
            optim.SGD(
                net.parameters(), lr=1e-3, momentum=0.9, nesterov=True
            ),
        ),
        # For the adaptive optimization methods we use the default
        # hyperparameters
        (
            "RMSprop",
            optim.RMSprop(net.parameters()),
        ),
        (
            "Adagrad",
            optim.Adagrad(net.parameters()),
        ),
        (
            "Adadelta",
            optim.Adadelta(net.parameters()),
        ),
        (
            "Adam",
            optim.Adam(net.parameters()),
        ),
    ]

def compute_test_loss_and_accuracy():
    total_test_loss = 0.0
    correct_count = 0
    with torch.no_grad():
        for images, labels in test_loader:
            images = images.to(device)
            labels = labels.to(device)

            output = net(images)
            loss = loss_fn(output, labels)

            total_test_loss += loss.item() * images.size(0)
            pred_labels = torch.max(output, dim=1).indices
            correct_count += torch.sum(
                pred_labels == labels
            ).item()

    avg_test_loss = total_test_loss / len(mnist_test)
    accuracy = correct_count / len(mnist_test)

    return (avg_test_loss, accuracy)

loss_plots = []
accuracy_plots = []

test_interval = 100

for _, optimizer in optimizers:
    train_losses = []
    accuracies = []
    print(optimizer)

    with torch.no_grad():
        net.load_state_dict(initial_state)

    i = 0
    for e in range(5):
        print(f"Epoch {e+1}")
        for images, labels in train_loader:
            images = images.to(device)
            labels = labels.to(device)

            optimizer.zero_grad()
            output = net(images)
            loss = loss_fn(output, labels)
            loss.backward()
            optimizer.step()

            train_losses.append(loss.item())

            if (i + 1) % test_interval == 0:
                (
                    test_loss,
                    accuracy,
                ) = compute_test_loss_and_accuracy()
                print(accuracy)
                accuracies.append(accuracy)

            i += 1

    loss_plots.append(train_losses)
    accuracy_plots.append(accuracies)

WINDOW = 200

_, (ax1, ax2) = plt.subplots(2, 1, figsize=(10, 12))
ax1.set_yscale("log")
ax2.set_yscale("logit")
ax2.yaxis.set_major_formatter(ScalarFormatter())
ax2.yaxis.set_minor_formatter(NullFormatter())
for (label, _), train_losses, accuracies in zip(
    optimizers, loss_plots, accuracy_plots
):
    ax1.plot(
        [
            sum(train_losses[max(0,i-WINDOW) : i]) / min(i, WINDOW)
            for i in range(1,len(train_losses))
        ],
        label=label,
    )
    ax2.plot(
        range(0, len(accuracies) * test_interval, test_interval),
        accuracies,
        label=label,
    )

ax1.legend()

plt.tight_layout()
plt.savefig("../plots/mnist_optim.pdf", bbox_inches="tight")
```

源代码 7.13 (*code/mnist\_optim.py*)：比较在 MNIST 数据集上训练 ANN 时几种优化方法性能的 PYTHON 代码。有关此代码生成的图表，见图 7.5。

**注 7.9.3** （加速型 SGD 优化方法分析）。在文献中，有大量研究文章探讨了本章回顾的加速型 SGD 优化方法。特别是，关于带动量的 SGD 型优化方法的文章，例如参见 \[149, 275, 280, 339, 387\] 及其参考文献；关于自适应 SGD 型优化方法的文章，例如参见 \[96, 156, 289, 351, 438\] 及其参考文献。

