
```
if not self.C: #if its empty
    G = cvxopt.matrix(np.identity(n_samples) * -1)
    h = cvxopt.matrix(np.zeros(n_samples))
else:
    G_max = np.identity(n_samples) * -1
    G_min = np.identity(n_samples)
    G = cvxopt.matrix(np.vstack((G_max, G_min)))
    h_max = cvxopt.matrix(np.zeros(n_samples))
    h_min = cvxopt.matrix(np.ones(n_samples) * self.C)
    h = cvxopt.matrix(np.vstack((h_max, h_min)))

minimization = cvxopt.solvers.qp(P, q, G, h, A, b)

lagr_mult = np.ravel(minimization['x'])
```

#### Get indexes of non-zero lagr. multipliers
`idx = lagr_mult > 1e-11`
#### Get the corresponding lagr. multipliers
`self.lagr_multipliers = lagr_mult[idx]`
#### Get the samples that will act as support vectors
`self.support_vectors = X[idx]`
#### Get the corresponding labels
`self.support_vector_labels = y[idx]`

`self.intercept = self.support_vector_labels[0]`
for i in range(len(self.lagr_multipliers)):
    self.intercept -= self.lagr_multipliers[i] * self.support_vector_labels[i] * self.kernel(self.support_vectors[i], self.support_vectors[0])

def predict(self, X):
    y_pred = []
    for sample in X:
        prediction = 0
        # Determine the label of the sample by the support vectors
        for i in range(len(self.lagr_multipliers)):
            prediction += self.lagr_multipliers[i] * self.support_vector_labels[i] * self.kernel(self.support_vectors[i], sample)
        prediction += self.intercept
        y_pred.append(np.sign(prediction))
    return np.array(y_pred)

def main():
    #load dataset
    iris = load_iris()
    X = iris.data[:100,:]
    y = 2*iris.target[:100] - 1
```

Solves the quadratic optimization problem, using `cvxopt`

Lagrange multipliers

Extracts support vectors

Calculates the intercept with the first support vector

Iterates through list of samples and makes predictions

Maps to `{+1,-1}` labels

```
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.4)
clf = SupportVectorMachine(kernel=rbf_kernel, gamma = 1)
clf.fit(X_train, y_train)
y_pred = clf.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)
print ("Accuracy (scratch):", accuracy)

clf_sklearn = SVC(gamma = 'auto')
clf_sklearn.fit(X_train, y_train)
y_pred2 = clf_sklearn.predict(X_test)
accuracy = accuracy_score(y_test, y_pred2)
print ("Accuracy :", accuracy)

if __name__ == "__main__":
    main()
```

我们可以看到，基于我们实现的SVM分类准确率与sklearn模型的准确率一致！

### 5.4 逻辑回归

逻辑回归是一种分类算法。在从头实现逻辑回归之前，让我们深入了解其背后的一些理论！在分类的概率视角下，我们关心的是在给定输入数据`x`时，计算类别标签`C_k`的概率`p(C_k|x)`。考虑两个类别`C1`和`C2`，我们可以使用贝叶斯规则来计算后验概率。

$$p(C_1|x) = \frac{p(x|C_1)p(C_1)}{p(x|C_1)p(C_1) + p(x|C_2)p(C_2)}\tag{5.18}$$

这里，`p(C_k)`是类别先验概率。我们可以将右手边除以分子，得到如下结果。

$$p(C_1|x) = \frac{1}{1 + \frac{p(x|C_2)p(C_2)}{p(x|C_1)p(C_1)}} = \frac{1}{1 + \exp(-a)} = \sigma(a)\tag{5.19}$$

在这里，我们定义了以下内容。

$$a = \ln \frac{p(x|C_1)p(C_1)}{p(x|C_2)p(C_2)}\tag{5.20}$$

在多类别场景中（`K>2`），我们有以下公式。

$$p(C_k|x) = \frac{p(x|C_k)p(C_k)}{\sum_i p(x|C_i)p(C_i)} = \frac{\exp(a_k)}{\sum_i \exp(a_i)}\tag{5.21}$$

在公式5.21中，`a_k = \ln p(x|C_k) p(C_k)`。这个表达式也被称为softmax函数。softmax函数接受一个包含`K`个实数值的向量，并将其转换为一个包含`K`个实数值、总和为1的向量。因此，softmax函数的输出可以被解释为概率分布。现在，关键在于选择能够很好地建模数据的条件密度。在以`θ`为参数、类别标签为`y = C_k`的二分类逻辑回归中，我们有以下方程。

$p(C_k|x) = p(y|x, \theta) = \mathrm{Ber}\left(y \mid \sigma\left(\theta^T x\right)\right) \tag{5.22}$

我们可以按如下方式计算联合分布。

$p(x_i, y_i|\theta) = p(y_i|x_i, \theta) p(x_i|\theta) = \mathrm{Ber}\left(y \mid \sigma\left(\theta^T x\right)\right) p(x_i|\theta) \tag{5.23}$

由于我们不对数据的分布`p(x_i|\theta) = p(x_i)`进行建模，我们可以将对数似然写成如下形式。

$\log p(D|\theta) = \log \prod_{i=1}^n p(x_i, y_i|\theta) = \sum_{i=1}^n \log p(x_i, y_i|\theta)$

$= \sum_{i=1}^n \log \mathrm{Ber}\left(y \mid \sigma\left(\theta^T x\right)\right)$

$= \sum_{i=1}^n \log \left[ \sigma\left(\theta^T x_i\right)^{y_i} \left(1 - \sigma\left(\theta^T x_i\right)\right)^{1 - y_i} \right]$

$= \sum_{i=1}^n \left[ y_i \log \sigma\left(\theta^T x_i\right) + (1 - y_i) \log \left(1 - \sigma\left(\theta^T x_i\right)\right) \right] \tag{5.24}$

请注意，我们关心的是最大化对数似然，或者等效地，最小化损失或负对数似然（NLL）。

$\min_{\theta} \mathrm{Loss}(\theta) = \min_{\theta} \mathrm{NLL}(\theta) = \max_{\theta} \log p(D|\theta) \tag{5.25}$

我们计划通过随机梯度下降（SGD）来最小化逻辑回归损失，该过程可以写成如下形式。

$\theta_{k+1} = \theta_k - \eta_k g_k \tag{5.26}$

这里，`g_k`是梯度，`η_k`是步长。为了保证SGD的收敛性，必须满足以下方程中对学习率所表达的条件，即所谓的Robbins-Monro条件。

我们可以使用以下学习率调度，它满足方程 5.27 中的条件。

$$

\sum_{k=1}^{\infty} \eta_k = \infty

$$

$$

\sum_{k=1}^{\infty} \eta_k^2 < \infty \tag{5.27}

$$

我们可以使用以下学习率调度，它满足方程 5.27 中的条件。

$$

\eta_k = (\tau_0 + k)^{-\kappa} \tag{5.28}

$$

这里，\(\tau_0 \ge 0\) 减缓算法的早期迭代，而 \(\kappa \in (0.5, 1]\) 控制旧值被遗忘的速率。为了计算最陡下降方向 `g_k`，我们需要对损失函数 `NLL(θ)` 求导。

$$

\frac{d}{d\theta}\log p(D|\theta) = \sum_{i=1}^{n}\left[y_i\frac{d}{d\theta}\log\sigma\left(\theta^T x_i\right) + (1-y_i)\frac{d}{d\theta}\log\left(1-\sigma\left(\theta^T x_i\right)\right)\right]

$$

$$

= \sum_{i=1}^{n}\left[y_i\frac{\sigma\left(\theta^T x_i\right)\left(1-\sigma\left(\theta^T x_i\right)\right)}{\sigma\left(\theta^T x_i\right)}x_i + (1-y_i)\frac{\sigma\left(\theta^T x_i\right)\left(1-\sigma\left(\theta^T x_i\right)\right)}{1-\sigma\left(\theta^T x_i\right)}(-x_i)\right]

$$

$$

= \sum_{i=1}^{n}\left[y_i x_i\left(1-\sigma\left(\theta^T x_i\right)\right)-(1-y_i)x_i\sigma\left(\theta^T x_i\right)\right]

$$

$$

= \sum_{i=1}^{n}\left[y_i-\sigma\left(\theta^T x_i\right)\right]x_i

$$

$$

= \sum_{i=1}^{n}\left[y_i-\mu_i\right]x_i = -X^T(\mu - y) \tag{5.29}

$$

在方程 5.29 中，我们使用了事实 \(d/dx\,\sigma(x) = (1-\sigma(x))\sigma(x)\) 以及伯努利分布的均值 \(\mu_i = \sigma(\theta^T x_i)\)。请注意，有许多自动微分库可以避免手工推导梯度。此外，我们可以添加正则化来控制参数规模。我们的正则化目标和梯度如下。

$$

\min_{\theta}\text{Loss}(\theta) = \min_{\theta}\left[\text{NLL}(\theta) + \lambda\theta^T\theta\right]

$$

$$

g_k = X^T(\mu - y) + 2\lambda\theta \tag{5.30}

$$

我们现在准备为逻辑回归实现 SGD。让我们从图 5.10 所示的以下伪代码开始。

```text
1: class sgdlr
2: function lr_objective(θ, X, y, λ)
3: μ_i = sigmoid(θ^T X_i)
4: cost = - Σ_{i=1}^n [y_i log μ_i + (1 - y_i) log (1 - μ_i)] + λ θ^T θ
5: grad = X^T (μ - y) + 2λ θ ← Computes the gradient
6: return cost, grad
7: function fit(X, y):
8: η_i = (τ + i)^{-κ} ← Sets the learning rate
9: for i = 1, 2, … num_iter
10:   cost, grad = lr_objective(θ, X, y, λ)
11:   θ = θ - η_i grad ← Updates the theta
12: end for
13: return θ
14: function predict(X, θ):
15: ŷ = sigmoid (θ^T X) ← Makes a prediction
16: return ŷ
```

**Figure 5.10** 逻辑回归算法伪代码

`sgdlr` 类包含三个主要函数：`lr_objective`、`fit` 和 `predict`。在 `lr_objective` 函数中，我们计算正则化目标函数和目标的梯度，如文中所述。在 `fit` 函数中，我们首先设置学习率，并且在每次迭代中，我们沿着与梯度相反的方向更新 `theta` 参数。最后，在 `predict` 函数中，我们基于测试数据对标签进行二元预测。在下面的代码列表中，我们使用合成高斯混合数据集来训练逻辑回归模型。

### Listing 5.3 SGD 逻辑回归
