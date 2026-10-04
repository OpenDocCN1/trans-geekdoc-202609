

## 第 6 章 高级特征处理方法

'numeric__number_of_reviews' 'numeric_reviews_per_month'
'numeric__calculated_host_listings_count' 'numeric__availability_365'

我们可以通过运行以下命令以后向的方式复制实验：

```python
selector = SequentialFeaturesSelector(
    estimator=xgb,
    n_features_to_select="auto",
    tol=0.001,
    direction="backward",
    scoring='accuracy',
    cv=5
)
selector.fit(X, target_median)
selected_features = selector.support
selected_data = column_transform.get_feature_names_out()[selected_features]
print(selected_data)
```

> 指定特征选择的方向（在本例中为“backward”，后向）

结果选择包含九个特征，其中许多特征在正向选择得到的集中出现过：

```python
['low_card_categories_neighbourhood_group_Bronx',
'low_card_categories_neighbourhood_group_Manhattan',
'low_card_categories_neighbourhood_group_Queens',
'low_card_categories_neighbourhood_group_Staten Island',
'low_card_categories_room_type_Entire_home/apt',
'low_card_categories_room_type_Shared_room',
'high_card_categories__numeric__minimum_nights',
'numeric__neighbourhood__numeric_number_of_reviews' 'numeric_reviews_per_month',
'numeric__calculated_host_listings_count' 'numeric__availability_365']
```

根据我们的经验，选择正向还是后向选择取决于你可能需要从集中剔除某些略微重要的特征。通过正向添加，你可以确保只保留核心特征，但存在遗漏边缘相关特征的风险。通过后向消除，你可以确保集合都包含了所有特征的冗余。

除了选择正向或后向程序外，序列选择还将帮助你构建训练和预测模型，并且由于使用的特征数量有限，模型将更容易解释和维护。

## 6.3 优化超参数

特征工程可以提高你从经典机器学习模型获得的结果。创建新特征可以揭示数据中模型由于局限性而无法捕捉的潜在模式和关系。特征选择可以通过移除对问题无用且冗的特征来改进模型结果，从而减少数据中的噪声和虚假信号。最后，通过优化超参数，你可以获得进一步的性能提升，让你的经典学习模型在处理的表格数据问题上表现出色。

正如第 4 章过的，超参数是运行在所有机器学习算法底层的设置，决定了它们具体如何工作。从抽象的角度来看，每个机器学习算法都可能提供有限但宽泛的函数范围——即你将预测变量与结果联系起来的数学方法。开箱即用的机器学习算法可能较多或较少地符合你特定机器学习问题所需的函数形式。

例如，如果你正在使用梯度提升算法来解决分类问题，默认的迭代次数或树的生长方式可能符合问题的要求。你可能需要比默认值更少或更多的迭代和树生长。通过优化你的超参数，你可以找到与你的问题配合得更好的最佳设置。

然而，这不仅仅是不断调节算法提供的许多旋钮直到得到你想要的结果。有时旋钮太多而无法进行测试，即使你设法测试了足够数量，如果操作不当，也会导致对数据的过拟合，相反，获得更糟糕的结果。在定义一个或多个评估指标后进行系统性的搜索：

- 定义一个搜索空间，包含你想要探索影响的超参数以及待测试值的边界
- 构建适当的交叉验证方案，以确保你发现的解决方案泛化到现有数据之外
- 通过适当策略选择搜索算法，以更短的时间和更低的成本（例如在计算方面）找到你需要的解决方案

在接下来的章节中，在不同搜索策略的基础上，我们将讨论如何完成我们目前看到的某些经典机器学习算法的调优。

### 6.3.1 系统化搜索

网格搜索通过所有超参数值的可能组合来工作。对于你想测试的每个超参数，选取一个值序列并穷尽遍历它们的所有组合。最后，选择返回最佳结果的组合。

在列表 6.12 中，我们将其应用于逻辑回归模型，以选择正则化的类型以及 L1 和 L2 正则化值的设置。代码最重要的部分是搜索网格，它是包含一个或多个字典的列表。相反，每个字典都是一个搜索空间，一组超参数（字典的键）关联到一个值生成器列表，这些生成器是你想要测试的可能值（字典的值）。构建一个或多个搜索空间是所有优化方法中的常见做法，无论它们是否来自 Scikit-learn。只需注意 `model_name_of_the_hyperparameter` 中超参数名称的公式，因为我们正在优化一个流水线，并处理首先是流水线内部的然后是它们的参数。我们将在下一节通过更多解释返回这一点。

#### 列表 6.12 网格搜索

```python
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import KFold, GridSearchCV
from sklearn.metrics import make_scorer
from sklearn.pipeline import Pipeline
import numpy as np

accuracy = make_scorer(accuracy_score)
cv = KFold(n_splits=5, shuffle=True, random_state=0)

model = Pipeline([
    ('processing', StandardScaler()),
    ('model', LogisticRegression(solver='liblinear', max_iter=5000))
])

search_grid = {
    'model__penalty': [None, 'l1', 'l2', 'elasticnet'],
    'model__C': np.logspace(-4, 4, 10),
    'model__l1_ratio': [.1, .3, .5, .7, .9, .99]
}

search_func = GridSearchCV(estimator=model,
                             param_grid=search_grid,
                             scoring='accuracy',
                             cv=cv)

search_func.fit(X, target_median)

print(search_func.best_params_)
print(search_func.best_score_)
```

### 6.3.2 使用随机试验

- 你需要对连续超参数进行离散化
- 如果超参数与问题无关，你在测试无关特征的空间将浪费很多精力。

使用网格搜索的重要局限性是

由于每个元素中的

