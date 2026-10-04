

# 第 6 章 高级特征处理方法

```python
origin='<',
gain=66.1962891,
count=3756,
threshold=1.88965869

LeafNode(
index=7,
origin='<',
count=3528)
```

图 6.8 将得到的输出与 XGBoost 包中 `plot_tree` 提供的完整树的可视化进行了比较。

![](img/def89cc476fa39f4c54bd34e78d91674_256_0.png)

**图 6.8 XGBoost 的 plot_tree 输出**

在模型构建的 10 棵树中，第一棵树以及从样本到预测叶节点节点的 8 条不同路径中的第一条路径代表了它。从视觉上看，它是最左侧的那条。该路径由不同的节点顺序组成。代码记录了特征名称、来自上一个节点的划分分支（在 XGBoost 中，`minor` 始终代表左分支，`major` 等于右分支）、切分阈值、相对于目标函数的增益（gain），以及在数据集划分后样本数量的减少量。所有这些信息允许你完美地复制 XGBoost 模型中每棵树的结果。

我们也可以从 LightGBM 中提取树结构，尽管这种方法略有不同，因为 LightGBM 包遵循的是一些不同的约定。例如，XGBoost 将负小于阈值的部分划分在左侧；而 LightGBM 则对每个节点使用 `minus` 或 `major-equal` 以及阈值定义规则，并在条件为真时向左侧划分，为假时向右侧划分。

### 列表 6.17 提取 LightGBM 树结构

```python
from lightgbm import LGBMClassifier, plot_tree

lgbm = LGBMClassifier(boosting_type='gbdt',
    n_estimators=10,
    max_depth=3)

model_pipeline = Pipeline([
    ('processing', column_transform),
    ('lightgbm', lgbm)
])

model_pipeline.fit(X=data, y=target_model)
model = model_pipeline['lightgbm']

tree_info = model.Booster.dump("tree_info")
treestructure = tree_info[0]['tree_structure']
plot_tree(
    model=model.Booster,
    tree_index=0,
    dpi=600
)
```
# 从 LightGBM 模型 booster 中提取树信息

# 从树信息中提取第一棵树的结构

# 使用 plot_tree 函数绘制集成模型中的第一棵树

```python
Split = namedtuple(
    "SplitNode",
    "feature origin decision_type threshold gain count"
)
Leaf = namedtuple("LeafNode", "index origin count value")
```
# 从 LightGBM 树结构中的划分节点中提取各种信息

```python
def extract_lggbm_node_info(tree):
    return [tree['split_feature'], tree['origin'], tree['decision_type'],
            tree['threshold'], tree['split_gain'], tree['internal_count']]
```
# 从 LightGBM 树结构中的叶节点中提取信息

```python
def extract_lggbm_leaf_info(tree):
    return [
        tree['leaf_index'],
        tree['origin'],
        tree['count'],
        tree['leaf_value']
    ]

def traverse_lggbm_tree(tree):
    if 'origin' in tree:
        tree['origin'] = "*"
        if not 'left_child' in tree and not 'right_child' in tree:
            return [Leaf(*extract_lggbm_leaf_info(tree))]
        left_branch = tree['left_child']
        right_branch = tree['right_child']
        left_branch['origin'] = 'yes'
        right_branch['origin'] = 'no'
        left_paths = traverse_lggbm_tree(left_branch)
```
# 递归遍历 LightGBM 结构到路径

![](img/def89cc476fa39f4c54bd34e78d91674_257_0.png)

# 第 6 章 高级特征处理方法

```python
        right_paths = traverse_lggbm_tree(right_branch)
        node_info = [Split(extract_lggbm_node_info(tree))]
        return [node_info + path for path in left_paths + right_paths]

paths = traverse_lggbm_tree(tree_structure)
print(paths[0])
```

此探索结果报告了从集成模型中第一棵决策树结构中的路径：

```python
[SplitNode(
feature=5,
origin='',
decision_type='<',
threshold=1.00000001800250295e-35,
gain=20002.19921875,
count=4895),
SplitNode(
feature=2,
origin='yes',
decision_type='<',
threshold=1.00000001800250295e-35,
gain=97.0563027343375,
count=21486),
SplitNode(
feature=13,
origin='',
decision_type='<',
threshold=1.00000001800250295e-35,
gain=97.0563027343375,
count=21486),
...
```

