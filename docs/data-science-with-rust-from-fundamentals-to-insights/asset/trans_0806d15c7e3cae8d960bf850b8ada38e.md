

接下来，我们将创建一个 Rust 程序来执行线性回归。

### 加载数据

在此示例中，我们将使用合成数据集。让我们考虑一个表示广告支出与销售额之间关系的简单数据集。

```rust
use ndarray::Array2;
use ndarray_linalg::LeastSquaresSvd;

fn main() {
    let x = array![[1., 1.],
        [1., 2.],
        [1., 3.],
        [1., 4.],
        [1., 5.]];
    let y = array![[3.], [6.], [7.], [8.], [11.]];
    let result = x.least_squares(&y).unwrap();
    let coefficients = result.solution;
    println!("Coefficients: {:?}", coefficients);
}
```

在此示例中，x 表示自变量（广告支出），y 表示因变量（销售额）。ndarray-linalg crate 的 least_squares 方法用于计算线性回归模型的系数。

### 4. 评估模型

模型训练完成后，评估其性能至关重要。常用指标包括决定系数（R^2）和均方误差（MSE）。以下是在 Rust 中实现这些评估的方法：

```rust
fn r_squared(y_true: &Array2, y_pred: &Array2) -> f64 {
    let ss_res = (y_true - y_pred).mapv(|x| x.powi(2)).sum();
    let y_mean = y_true.mean().unwrap();
    let ss_tot = (y_true - y_mean).mapv(|x| x.pow(2)).sum();
    1.0 - (ss_res / ss_tot)
}

fn main() {
    // (existing code to compute y_pred from the model)
    let y_pred = x.dot(&coefficients);
    let r2 = r_squared(&y, &y_pred);
    println!("R-squared: {}", r2);
}
```

### 5. 实际应用

线性回归在各个领域都有广泛应用：

- **金融**：基于历史数据预测股票价格。
- **市场营销**：根据广告支出估算销售额。
- **经济学**：了解利率对经济增长的影响。

### 6. 结论

## 逻辑回归：解码分类问题

### 简介

逻辑回归旨在预测给定输入属于特定类别的概率。与输出连续值的线性回归不同，逻辑回归输出 0 到 1 之间的概率值，然后用于将输入分类为两个类别之一。

逻辑回归模型由逻辑函数（也称为 Sigmoid 函数）定义：

```
[ \sigma(z) = \frac{1}{1 + e^{-z}} ]
```

其中 z 是输入变量的线性组合：

```
[ z = \beta_0 + \beta_1X_1 + \beta_2X_2 + \dots + \beta_nX_n ]
```

这里，β₀ 是截距，β₁、β₂、…、βₙ 是系数，X₁、X₂、…、Xₙ 是输入特征。

### 2. 理论基础

逻辑回归基于几个关键假设：

- **二元结果**：因变量是二元的。
- **误差独立**：观测值之间相互独立。
- **对数几率线性**：结果的对数几率是预测变量的线性组合。
- **样本量充足**：结果变量的每个类别中应有足够的病例。

这些假设是正确应用和解释逻辑回归模型的基础。

### 3. 在 Rust 中实现逻辑回归

要在 Rust 中实现逻辑回归，我们将使用 ndarray 和 ndarray-linalg crate 进行数值运算和线性代数，以及 linfa 机器学习 crate。让我们逐步介绍一个简单的实现。

### 设置环境

首先，确保在 Cargo.toml 文件中包含必要的依赖项：

```toml
[dependencies]
ndarray = "0.15"
ndarray-linalg = "0.14"
linfa = "0.2"
linfa-logistic = "0.2"
```

接下来，我们将创建一个 Rust 程序来执行逻辑回归。

### 加载数据

在此示例中，我们将使用一个合成数据集，表示客户是否会根据其年龄和收入购买产品。

```rust
use ndarray::array;
use linfa::traits::*;
use linfa_logistic::LogisticRegression;

fn main() {
    // Example data: age, income, purchased (0 or 1)
    let x = array![[25.0, 50000.0],
        [35.0, 80000.0],
        [45.0, 120000.0],
        [50.0, 60000.0],
        [23.0, 40000.0]];

    let y = array![0, 1, 1, 0, 0];

    // Fit the logistic regression model
    let model = LogisticRegression::default().fit(&x, &y).unwrap();

    // Predict the probability of purchase
    let predictions = model.predict(&x);
    println!("Predictions: {:?}", predictions);
}
```

在此示例中，x 表示输入变量（年龄和收入），y 表示二元结果（是否购买）。linfa-logistic crate 的 fit 方法用于训练逻辑回归模型。

### 4. 评估模型

评估逻辑回归模型的性能涉及准确率、精确率、召回率和 F1 分数等指标。以下是在 Rust 中实现这些评估的方法：

```rust
fn accuracy(y_true: &Array1, y_pred: &Array1) -> f64 {
    let correct_predictions = y_true.iter().zip(y_pred.iter()).filter(|&(a, b)| a == b).count();
    correct_predictions as f64 / y_true.len() as f64
}

fn main() {
    // (existing code to compute y_pred from the model)
    let accuracy_score = accuracy(&y, &predictions);
    println!("Accuracy: {}", accuracy_score);
}
```

### 5. 实际应用

逻辑回归在各个领域都有广泛应用：

- **医疗保健**：根据诊断变量预测患者患病的可能性。
- **市场营销**：确定客户是否会响应营销活动。
- **金融**：根据申请人特征评估贷款违约的概率。

### 6. 结论

逻辑回归是二元分类问题的重要工具，可提供可解释且可操作的见解。Rust 的高效性和性能使其成为实现逻辑回归模型的绝佳选择，这些模型可以轻松处理大型数据集。掌握扎实的逻辑回归知识后，您将充分准备好应对数据科学项目中广泛的分类挑战。

## 决策树：分支通向清晰决策

### 简介

决策树是一种可用于分类和回归任务的监督学习算法。其核心思想是根据特征值将数据集拆分为子集，从而创建一种树状决策模型。每个内部节点代表一个特征（或属性），每个分支代表一条决策规则，每个叶节点代表结果或类别标签。

- **关键概念：**
  - **根节点**：决策树中最顶层的节点，代表整个数据集。
  - **分割**：根据特定标准将节点划分为两个或多个子节点的过程。
  - **决策节点**：具有进一步子节点的节点。
  - **叶/终端节点**：不再进一步分割并代表最终分类或预测的节点。
  - **剪枝**：从树中移除不必要的节点，以防止过拟合并提高泛化能力。

### 2. 理论基础

决策树的构建涉及在每个节点选择最佳特征来拆分数据。这种选择通常基于基尼不纯度或信息增益等不纯度度量。

- **基尼不纯度**：衡量如果按照数据集中类别标签的分布随机标记，随机选择的元素被错误分类的概率。[ Gini(D) = 1 - \sum_{i=1}^C p_i^2 ] 其中 p_i 是元素被分类到类别 i 的概率。
- **信息增益**：衡量分割后数据集的熵或不确定性的减少量。[ IG(D, A) = Entropy(D) - \sum_{v \in Values(A)} \frac{|D_v|}{|D|} Entropy(D_v) ] 其中 D 是数据集，A 是属性，D_v 是属性 A 取值为 v 的 D 的子集。

### 3. 在 Rust 中构建决策树

要在 Rust 中构建决策树，我们将使用 linfa-trees crate（Linfa 框架的一部分，为 Rust 提供机器学习工具）。让我们逐步介绍该过程。

### 设置环境

首先，更新 Cargo.toml 文件以包含必要的依赖项：

```toml
[dependencies]
ndarray = "0.15"
linfa = "0.2"
linfa-trees = "0.2"
```

### 加载数据

为简单起见，我们将使用合成数据集。该数据集将表示根据申请人的信用评分和收入来判断贷款申请是否获批。

```rust
use ndarray::array;
use linfa::traits::*;
use linfa_trees::DecisionTree;
```

