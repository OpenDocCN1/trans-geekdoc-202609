
当你尝试对多分类任务使用二二分类算法时，Scikit-Learn 会检测并自动运行 OvA（使用 OVo 的 SVM 分类器除外）。让我们用 `SGDClassifier` 来尝试一下：

```
>>> sgd_clf.fit(X_train, y_train) # using y_train, not y_train_5
>>> sgd_clf.predict(some_digit)
array([5], dtype=uint8)
```

这很简单！这段代码在训练集上使用从 0 到 9 的原始目标类别（y_train）训练了 `SGDClassifier`，而不是使用 5 对全（5-versus-all）的目标类别（y_train.5）。在底层，Scikit-Learn 实际上训练了 10 个二分类器，获取了它们对该图像的决策分数，并选择了分数最高的类别。

为了验证这一点，你可以调用 `decision_function()` 方法。它返回的不是每个实例一个分数，而是每个类别返回 10 个分数：

```
>>> some_digit_scores = sgd_clf.decision_function([some_digit])
>>> some_digit_scores
array([-19555.226784, -30880.9269175, -13326.66694897,
5732.5692379, -17680.6846644, 2412.53175101,
-25526.8649156, -12290.1570409, -7946.0520523,
-10631.35885499])
```

最高的分数确实对应类别 5：

```
>>> np.argmax(some_digit_scores)
5
>>> sgd_clf.classes_
array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9], dtype=uint8)
>>> sgd_clf.classes_[5]
5
```

当分类器被训练好后，它会将目标类别列表存储在 `classes_` 属性中，并按照每个类别在 `classes_` 中的索引进行排序。在这种情况下，数组索引恰好与类别本身匹配（例如，索引 5 对应类别 5），但通常情况下你不会这么幸运的。

![](img/0684d2da98e09085c0a622d4fd69aaad_128_0.png)

如果你想强制 Scikit-Learn 使用一对一（one-vs-one）或一对多（one-vs-all），你可以使用 `OneVsOneClassifier` 或 `OneVsRestClassifier`。例如，这段代码基于 `SGDClassifier` 使用 OvO 策略创建了一个多分类器：

```
array([5], dtype=uint8)
>>> len(ovo_clf.estimators_)
4
```

训练一个 `RandomForestClassifier` 同样简单：

```
>>> forest_clf.fit(X_train, y_train)
>>> forest_clf.predict([some_digit])
array([5], dtype=uint8)
```

这一次 Scikit-Learn 不需要运行 OvA 或 Ovo，因为随机森林分类器可以直接将实例分类为多个类别。你可以调用 `predict_proba()` 来获取分类器为每个实例分配给每个类的概率列表：

```
>>> forest_clf.predict_proba([some_digit])
array([[0., 0., 0.01, 0.08, 0., 0.9, 0., 0., 0., 0.01]])
```

你可以看到分类器对预测相当有把握：数组中索引 5 处的 0.9 意味着模型估计图像代表 5 的概率为 90%。它还认为该图像可能是 2、3 或 9，概率分别为 1%、8% 和 1%。

现在你想评估这些分类器。像往常一样，你想使用交叉验证。让我们使用 `cross_val_score()` 函数来评估 `SGDClassifier` 的准确率：

```
>>> cross_val_score(sgd_clf, X_train, y_train, cv=3, scoring="accuracy")
array([0.8489092, 0.87129356, 0.86988048])
```

它在所有字段上都超过了 85%。如果你使用随机分类器，你会得到100%的准确率，所以这并不是一个坏分，但你仍然可以做得。例如，对输入进行缩放（如第2章所述）可以将准确率提高到 89% 以上：

```
>>> from sklearn.preprocessing import StandardScaler
>>> scaler = StandardScaler()
>>> X_train_scaled = scaler.fit_transform(X_train.astype(np.float64))
>>> cross_val_score(sgd_clf, X_train_scaled, y_train, cv=3, scoring="accuracy")
array([0.8907059, 0.89693604])
```

## Error Analysis

当然，如果这是一个真实项目，你将遵循机器学习项目中的步骤（参见 ?：探索数据准备、尝试多个模型、筛选出最佳模型并使用 `GridSearchCV` 调优超参数，以及尽可能自动化，就像你在上一章中所做的那样）。在这里，假设你有一个很有前景的模型并想找到改进方法。一种方法是分析它犯的错误。

首先，你可以查看混淆矩阵。你需要使用 `cross_val_predict()` 进行预测，然后调用 `confusion_matrix()` 函数，就像你之前做的那样：

```
>>> y_train_pred = cross_val_predict(sgd_clf, X_train_scaled, y_train, cv=3)
>>> conf_mx = confusion_matrix(y_train, y_train_pred)
array([[5578, 0, 22, 7, 8, 45, 35, 5, 22, 1],
 [ 0, 6410, 35, 26, 4, 44, 4, 198, 13, 0],
 [ 28, 27, 5232, 100, 74, 27, 68, 37, 35, 11],
 [ 23, 18, 11, 5254, 209, 26, 38, 73, 15, 0],
 [ 11, 14, 45, 12, 5219, 11, 33, 29, 17, 2],
 [ 26, 16, 31, 73, 54, 4884, 76, 14, 8, 2],
 [ 31, 17, 45, 428, 5556, 3, 123, 1, 0, 0],
 [ 20, 10, 53, 27, 50, 13, 3696, 173, 22, 0],
 [ 17, 64, 47, 91, 3, 125, 24, 14, 8, 1],
 [ 24, 18, 29, 67, 16, 39, 1, 174, 329, 5]])
```

这些数字太多了。使用 Matplotlib 的 `matshow()` 查看混淆矩阵的图像表示更方便：

```
plt.matshow(conf_mx, cmap='gray')
plt.show()
```

![](img/0684d2da98e09085c0a622d4fd69aaad_130_0.png)

这个混淆矩阵看起来还可以，大部分图像都在对角线上，这意味着它们被正确分类了。5 比其他数字稍暗，这可能意味着数据集中 5 较少，或者分类器对 5 的性能不如其他数字好。事实上，你可以验证这两种情况。

让我们关注错误图。首先，你需要将混淆矩阵中的每个值除以对应类别的图像数量，这样就可以比较错误率而不是错误的绝对数量（后者会让大量的类别看起来很糟糕）；现在让我们将对角线填充为零以只保留错误，并绘制结果：

```
np.fill_diagonal(norm_conf_mx, 0)
plt.matshow(norm_conf_mx, cmap='gray')
plt.show()
```

现在你可以清楚地看到分类器犯的错误类型。记住行代表实际类别，而列代表预测类别。类别 8 的列非常亮，这告诉许多图像被误分类为 8。然而，类别 8 的行并不差，说明实际 8 通常被正确分类为 8。正如你所看到的，混淆矩阵并不一定对称。你还可以看到 3 和 5 经常混淆（两个方向）。

分析混淆矩阵通常会给你关于如何改进分类器的见解。观察此图，你的努力应该放在减少 8 上。例如，你可以尝试收集更多像 8 但不是 8 的数字数据，以便分类器将它们与真实的 8 区分开；或者你可以构建有助于分类器的新特征——例如编写算法来计算闭合环的数量（例如，8 有两个，6 有一个，5 没有）。或者对图像进行预处理（例如使用 Scikit-Image、Pillow 或 OpenCV），使某些模式脱颖而出，例如闭合环。

分析单个错误也是了解分类器在做什么以及为什么失败的好方法，但它更困难且更耗时。

例如，显示 3 和 5 的示例（`plot_digits()` 函数）只是使用了 Matplotlib 的 `show()` 函数；详情请参此 Jupyter 笔记本：

```
cl_a, cl_b = 3, 5
X_aa = X_train[y_train == cl_a] & (y_train_pred == cl_a)
X_ab = X_train[y_train == cl_a] & (y_train_pred == cl_b)
X_ba = X_train[y_train == cl_b] & (y_train_pred == cl_a)
X_bb = X_train[y_train == cl_b] & (y_train_pred == cl_b)

plt.figure(figsize=(8,8))
plt.subplot(221); plot_digits(X_aa[:25], images_row=5)
plt.subplot(222); plot_digits(X_ab[:25], images_row=5)
plt.subplot(223); plot_digits(X_ba[:25], images_row=5)
plt.subplot(224); plot_digits(X_bb[:25], images_row=5)
plt.show()
```
