
### 保存和加载模型

保存模型以备将来使用：

```
model.save('simple_model.h5')
```

加载已保存的模型：

```
loaded_model = keras.models.load_model('simple_model.h5')
```

#### 示例：端到端二元分类

```
import numpy as np
import tensorflow as tf
from tensorflow.keras import layers

# Generate synthetic data
X_train = np.random.random((100, 10))  # 100 samples, 10 features
y_train = np.random.randint(2, size=(100, 1))  # Binary labels

# Define the model
model = tf.keras.Sequential([
    layers.Dense(64, activation='relu', input_shape=(10,)),
    layers.Dense(32, activation='relu'),
    layers.Dense(1, activation='sigmoid')
])

# Compile the model
model.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])

# Train the model
model.fit(X_train, y_train, epochs=10, batch_size=32)

# Evaluate the model
X_test = np.random.random((20, 10))
y_test = np.random.randint(2, size=(20, 1))
loss, accuracy = model.evaluate(X_test, y_test)
print(f"Test Loss: {loss}, Test Accuracy: {accuracy}")
```

总之，`TensorFlow` 和 `Keras` 简化了构建和训练神经网络的过程。凭借诸如用于简单架构的 `Sequential` API 和用于更复杂设计的 `Functional` API 等功能，这些库具有多功能且用户友好。通过遵循本分步指南，您可以快速为各种机器学习任务构建、训练和部署模型。

# 22.3 动手实践：你的第一个神经网络

构建你的第一个神经网络是进入深度学习世界令人兴奋的一步。神经网络可以解决分类、回归等各种问题。在本动手指南中，我们将逐步介绍使用 Python 和 TensorFlow/Keras 创建一个简单的前馈神经网络的过程。

### 设置环境

要构建神经网络，你需要安装 Python 和 TensorFlow。通过 pip 安装 TensorFlow：

```
pip install tensorflow
```

### 导入所需库

导入必要的模块：

```
import tensorflow as tf
from tensorflow.keras import layers, models
import numpy as np
```

### 定义问题

对于此示例，我们将构建一个神经网络，根据小型合成数据集将点分类为两个类别。这是一个二元分类问题。

### 生成数据集

使用 TensorFlow 或 NumPy 创建合成数据集：

```
from sklearn.datasets import make_moons

# Generate synthetic dataset
X, y = make_moons(n_samples=1000, noise=0.1)

# Split into training and testing sets
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)
```

### 构建神经网络

使用 Keras Sequential API 定义一个简单的前馈神经网络：

```
# Create the model
model = models.Sequential([
    layers.Dense(16, activation='relu', input_shape=(2,)),  # Input layer
    layers.Dense(8, activation='relu'),                     # Hidden layer
    layers.Dense(1, activation='sigmoid')                   # Output layer
])
```

### 编译模型

编译步骤通过指定以下内容来配置模型以进行训练：
- 损失函数：对于二元分类，使用 `binary_crossentropy`。
- 优化器：使用 `adam` 进行高效的梯度下降。
- 指标：在训练期间跟踪 `accuracy`。

```
model.compile(
    optimizer='adam',
    loss='binary_crossentropy',
    metrics=['accuracy']
)
```

### 训练模型

使用 `fit` 方法训练模型，指定：
- 训练数据（`X_train`, `y_train`）
- 训练轮数（例如 20）
- 批大小（例如 32）

```
history = model.fit(X_train, y_train, epochs=20, batch_size=32, validation_split=0.2)
```

### 评估模型

训练后，在测试数据集上评估模型：

```
loss, accuracy = model.evaluate(X_test, y_test)
print(f"Test Loss: {loss}, Test Accuracy: {accuracy}")
```

### 进行预测

预测新数据的类别概率：

```
predictions = model.predict(X_test)
# Convert probabilities to binary outputs
predicted_classes = (predictions > 0.5).astype(int)
```

### 可视化结果

使用 Matplotlib 可视化训练后模型的决策边界：

```
import matplotlib.pyplot as plt

# Plot decision boundary
def plot_decision_boundary(model, X, y):
    x_min, x_max = X[:, 0].min() - 1, X[:, 0].max() + 1
    y_min, y_max = X[:, 1].min() - 1, X[:, 1].max() + 1
    xx, yy = np.meshgrid(np.arange(x_min, x_max, 0.01),
                         np.arange(y_min, y_max, 0.01))
    Z = model.predict(np.c_[xx.ravel(), yy.ravel()])
    Z = Z.reshape(xx.shape)
    plt.contourf(xx, yy, Z, alpha=0.8)
    plt.scatter(X[:, 0], X[:, 1], c=y, edgecolor='k')
    plt.show()

plot_decision_boundary(model, X_test, y_test)
```

#### 完整代码示例

这是你的第一个神经网络的完整代码：

```
import numpy as np
import tensorflow as tf
from tensorflow.keras import layers, models
from sklearn.datasets import make_moons
from sklearn.model_selection import train_test_split
import matplotlib.pyplot as plt

# Generate dataset
X, y = make_moons(n_samples=1000, noise=0.1)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

# Build the model
model = models.Sequential([
    layers.Dense(16, activation='relu', input_shape=(2,)),
    layers.Dense(8, activation='relu'),
    layers.Dense(1, activation='sigmoid')
])

# Compile the model
model.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])

# Train the model
model.fit(X_train, y_train, epochs=20, batch_size=32, validation_split=0.2)

# Evaluate the model
loss, accuracy = model.evaluate(X_test, y_test)
print(f"Test Loss: {loss}, Test Accuracy: {accuracy}")

# Visualize decision boundary
def plot_decision_boundary(model, X, y):
    x_min, x_max = X[:, 0].min() - 1, X[:, 0].max() + 1
    y_min, y_max = X[:, 1].min() - 1, X[:, 1].max() + 1
    xx, yy = np.meshgrid(np.arange(x_min, x_max, 0.01),
                         np.arange(y_min, y_max, 0.01))
    Z = model.predict(np.c_[xx.ravel(), yy.ravel()])
    Z = Z.reshape(xx.shape)
    plt.contourf(xx, yy, Z, alpha=0.8)
    plt.scatter(X[:, 0], X[:, 1], c=y, edgecolor='k')
    plt.show()

plot_decision_boundary(model, X_test, y_test)
```

总之，构建你的第一个神经网络涉及理解层、激活函数和优化器等关键组件。通过遵循本指南，你已创建、训练并评估了一个用于二元分类的简单神经网络。这种基础知识将帮助你为多样化的机器学习问题构建更复杂的模型。

# 第23章 自然语言处理（NLP）

自然语言处理（NLP）是人工智能的关键领域，使计算机能够理解、解释和生成人类语言。本章从文本预处理和分词开始，涵盖为准备文本数据进行分析而必不可少的核心和高级技术。它探讨了分词为何至关重要以及高效处理语言时所面临的挑战。本章随后深入介绍使用 Python 进行情感分析，概述关键步骤、流行库和实用示例，包括使用预训练模型的使用。最后，一个动手部分提供了 NLP 技术的实际应用，使读者具备在现实场景中实施文本分析的技能。

## 23.1 文本预处理和分词

文本预处理和分词是自然语言处理（NLP）中的重要步骤。这些过程将原始文本转换为适合机器学习模型的结构化格式，使其能够有效地理解和分析语言数据。

### 23.1.1 文本预处理
