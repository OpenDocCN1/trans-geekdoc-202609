

为 null。具体而言，它使用 `isNaN()` 来识别空值，使用 `cast("int")` 将布尔结果转换为整数（0 或 1），并使用 `pyspark.sum` 计算每列缺失值的总和。每列的缺失值计数都以其原始列名作为别名。

在计数过程之后，该方法打印一个标题，指示将显示缺失值计数，然后使用 `show()` 方法显示缺失值计数 DataFrame。每一行对应数据集中的一列，每行中的值表示该列中缺失值的数量。

如果数据未加载（即 `self.data` 为 `None`），该方法会打印一条消息，声明数据未加载，告知用户在进行缺失值分析之前需要加载数据集。这确保了关于数据集状态的清晰度，并防止在未加载的数据上进行分析。

## 步骤 6：count_zeros 方法定义

在此阶段，我们在 `PimaDatasetExplorer` 类中定义 `count_zeros` 方法，其目的是统计数据集中每列零值出现的次数，然后展示这些计数（我们将在讨论输出时解释其目的）：

```python
[In]: def count_zeros(self):
        """
        Counts the number of zero values for each
        column in the
        dataset and displays the counts.
        """
        if self.data is not None:
            zero_counts = self.data.select([
                pyspark_sum((col(c) == 0).cast("int")).
                alias(c)
                for c in self.data.columns
            ])
        print("Zero Counts:")
        zero_counts.show()
    else:
        print("Data not loaded.")
```

在文档字符串之后，该方法开始检查数据集是否已加载。此检查通过验证 `self.data` 是否为非 `None` 来执行。如果数据集已加载，该方法将继续执行零值计数。对于计数零值，该方法构建了一个名为 `zero_counts` 的 DataFrame。它利用列表推导式遍历数据集中的每一列（`c`）。在此推导式中，使用 PySpark 函数来评估值是否等于零。具体而言，`(col(c) == 0)` 评估列中的值是否等于零，`cast("int")` 将布尔结果转换为整数（0 或 1），`pyspark_sum` 计算每列零值的总和。每列的零值计数都以其原始列名作为别名。

在执行完计数操作后，该方法打印一个标题，宣布将显示零值计数。然后使用 `show()` 方法显示零值计数 DataFrame。显示的 DataFrame 中的每一行对应数据集中的一列，每行中的值指示该列中零值的数量。

如果数据集未加载（即 `self.data` 为 `None`），该方法会打印一条消息，表明数据未加载。此消息作为提醒，在尝试进行零值分析之前先加载数据集。

## 步骤 7：data_summary 方法定义

`PimaDatasetExplorer` 类中的 `data_summary` 方法提供了糖尿病数据集中相关特征的摘要：

```python
[In]: def data_summary(self):
    """
    Displays a summary of the dataset, excluding certain
    columns, and filtering out rows with zero values in
    specific columns.

    Note: The 'SkinThickness' and 'Insulin' columns are
    excluded from the summary because they contain a
    large number of zero values, which are considered
    invalid because these measurements should not be zero
    in a living person and could
    skew the results.
    """
    if self.data is not None:
        print(
            "Data Summary ("
            "excluding 'Outcome', 'SkinThickness', 'Insulin')"
        )
        columns_to_exclude = [
            'Outcome',
            'SkinThickness',
            'Insulin'
        ]
        summary_cols = [
            c for c in self.data.columns
            if c not in columns_to_exclude
        ]
        filtered_data = self.data.filter(
            (col("Glucose") != 0)
            & (col("BloodPressure") != 0)
            & (col("BMI") != 0)
        )
        filtered_data.select(summary_cols).\
            describe().show()
    else:
        print("Data not loaded.")
```

让我们逐步分解该方法：

- 它以描述其目的的文档字符串开始。
- 然后它验证数据集是否已加载，确保 `self.data` 不为 `None`。如果数据集已加载，该方法将继续生成数据摘要。
- 为了生成摘要，该方法首先打印一个标题，指示将显示数据集的摘要。然后定义一个名为 `columns_to_exclude` 的列表，包含要从摘要中排除的列名（'Outcome', 'SkinThickness', 'Insulin'）。
- 接下来，该方法使用列表推导式构建一个名为 `summary_cols` 的列表。此列表包含数据集中的所有列（`self.data.columns`），但不包括 `columns_to_exclude` 中指定的列。
- 随后，该方法过滤数据集（`self.data`），以排除特定列（'Glucose', 'BloodPressure', 'BMI'）值为零的行。这是通过使用 PySpark 中的 `filter()` 方法实现的，条件确保指定的列中没有值为零的情况。
- 在过滤数据集之后，该方法仅选择 `summary_cols` 中指定的列，并使用 `describe()` 方法生成描述性统计。这些统计提供了对数据分布的中心趋势、离散程度和形状的见解。
- 最后，该方法通过调用生成的摘要 DataFrame 上的 `show()` 方法来显示摘要。
- 如果数据集未加载（即 `self.data` 为 `None`），该方法会打印一条消息，表明数据未加载。

## 步骤 8：count_outcome 方法定义

在此，我们定义 `count_outcome` 方法，它是 `PimaDatasetExplorer` 类的一部分。该方法用于统计糖尿病数据集中每种结果值出现的次数：

```python
[In]: def count_outcome(self):
        """
        Counts the occurrences of each outcome value in the dataset.
        """
        if self.data is not None:
            print("Outcome Counts:")
            outcome_counts = self.data.filter(
                (col("Glucose") != 0)
                & (col("BloodPressure") != 0)
                & (col("BMI") != 0)
            ).groupBy("Outcome").count()
            outcome_counts.show()
        else:
            print("Data not loaded.")
```

让我们将其分解：

- 该方法以文档字符串开始，简要解释其目的。
- 然后它检查数据集是否已加载，确保 `self.data` 不为 `None`。如果数据集已加载，该方法将继续统计结果出现的次数。
- 为了统计每种结果值出现的次数，该方法构建了一个名为 `outcome_counts` 的 DataFrame。它过滤数据集以排除特定列（`'Glucose', 'BloodPressure', 'BMI'`）值为零的行（无效数据）。这是通过使用 PySpark 中的 `filter()` 方法实现的，确保指定的列中没有值为零的情况。
- 在过滤数据集之后，该方法按 `Outcome` 列（目标变量）对数据进行分组，并使用 `groupBy()` 和 `count()` 函数计算每种结果值的出现次数。
- 计算计数完成后，该方法打印一个标题，指示将显示结果计数。然后使用 `show()` 方法显示结果计数 DataFrame。显示的 DataFrame 中的每一行代表一个结果值，相应的计数指示该结果值在数据集中出现的次数。
- 如果数据集未加载（即 `self.data` 为 `None`），该方法会打印一条消息，表明数据未加载。

## 步骤 9：explore_feature_distributions 方法定义

在此步骤中，我们定义 `explore_feature_distributions` 方法，该方法旨在通过直方图分析和可视化数据集中每个特征分布：

```python
[In]: def explore_feature_distributions(self):
      """
      Plots histograms for the distribution of each
      feature in the
      dataset.
      """
      if self.data is not None:
          print("Feature Distributions:")
          for column in self.data.columns:
              if column not in ['SkinThickness',
                                 'Insulin']:
                  print(f"Feature: {column}")
                  if column in [
                      "Glucose",
                      "BloodPressure",
                      "BMI"
                  ]:
                      filtered_data = self.data.filter(
                          (col(column) != 0)
                          & (col("Glucose") != 0)
                          & (col("BloodPressure") != 0)
                          & (col("BMI") != 0)
                      )
```

