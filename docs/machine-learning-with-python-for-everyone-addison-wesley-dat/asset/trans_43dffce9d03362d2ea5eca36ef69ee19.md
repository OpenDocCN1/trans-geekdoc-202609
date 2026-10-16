

```
In [30]:

fig, ax = plt.subplots(1, 1, figsize=(6, 4))

cv_prob_true = {}
for mod_name, model in classifiers.items():
    cv_probs = skms.cross_val_predict(model,
                                    iris_onec_ftrs, iris_onec_tgt,
                                    cv=10, method='predict_proba')
    cv_prob_true[mod_name] = cv_probs[:, 1]

fpr, tpr, thresh = metrics.roc_curve(iris_onec_tgt,
                                    cv_prob_true[mod_name])

auc = metrics.auc(fpr, tpr)
ax.plot(fpr, tpr, 'o--', label="{}:{:.3f}".format(mod_name, auc))

ax.set_title('ROC Curves')
ax.legend();
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_221_0.png)

基于ROC图，我们目前可能最关注我们的3-NN模型，因为它的AUC略高一些。我们将利用上一个示例中的 cv_prob_true 来创建提升曲线：

```
In [31]:

fig, (ax1,ax2) = plt.subplots(1, 2, figsize=(10, 5))

N = len(iris_onec_tgt)
xs = np.linspace(1/N, 1, N)

ax1.plot(xs, xs, 'b-')

for mod_name in classifiers:
    # negate so big values come first
    myorder = np.argsort(-cv_prob_true[mod_name])

    # cumulative sum then to percent (last value is total)
    realpct_myorder = iris_onec_tgt[myorder].cumsum()
    realpct_myorder = realpct_myorder / realpct_myorder[-1]

    ax1.plot(xs, realpct_myorder, '.', label=mod_name)

    ax2.plot(xs,
             realpct_myorder / np.where(xs > 0, xs, 1),
             label=mod_name)
ax1.legend()
ax2.legend()

ax1.set_title("Cumulative Response")
ax2.set_title("Lift versus Random");
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_222_0.png)

![](img/d94e4cd766940d79abed0bc6ba4e4344_222_1.png)

在这里，我们看到的增益与之前提升图中的相似。在定位大约40%的样本后，我们或许可以停止寻找更多的versicolor。我们在不同阶段有不同的领先者：GNB先下降，然后超越10-NN。GNB和3-NN都在定位40%的样本时达到峰值。10-NN似乎陷入低谷，直到x轴上的定位率接近100%时才达到100%的成功率（y轴）。

## 6.7.2 一个新的多分类问题

让我们把注意力转向一个新问题，并顺便处理——而不是忽略——多分类问题中的问题。我们的数据集由Cortez和Silva收集（完整参考文献见章末注释），我从UCI数据仓库下载了它：https://archive.ics.uci.edu/ml/datasets/student+performance。

该数据衡量学生在两门中学教育科目中的成绩：数学和语言。这两个科目分别记录在不同的CSV文件中；我们只查看数学数据。数据属性包括学生成绩、人口统计学、社会以及学校相关特征，这些数据是通过学校报告和问卷收集的。对于这里的示例，我预处理了数据，以（1）移除非数值特征，（2）生成用于分类的离散目标类别。复现我预处理过程的代码在章末展示。

```
In [32]:

student_df = pd.read_csv('data/portuguese_student_numeric_discrete.csv')
student_df['grade'] = pd.Categorical(student_df['grade'],
                                    categories=['low', 'mid', 'high'],
                                    ordered=True)
```

```
In [33]:

student_ftrs = student_df[student_df.columns[:-1]]
student_tgt  = student_df['grade'].cat.codes
```

我们先从一个简单的3-NN分类器开始，用准确率进行评估。我们已经讨论过它的局限性——但它仍然是一个让我们起步的简单方法和指标。如果目标类别不太不平衡，使用准确率或许没问题。

```
In [34]:

fig,ax = plt.subplots(1, 1, figsize=(3, 3))
model = neighbors.KNeighborsClassifier(3)
cv_auc = skms.cross_val_score(model,
    student_ftrs, student_tgt,
    scoring='accuracy', cv=10)
ax = sns.swarmplot(cv_auc, orient='v')
ax.set_title('10-Fold Accuracy');
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_224_0.png)

现在，如果我们想转向精确率，我们就必须超越sklearn提供的 cross_val_score 接口中的简单 scoring="average_precision" 参数。这个平均值实际上是对二分类问题的平均。如果我们有多个目标类别，就需要指定我们想要如何平均结果。我们在本章前面讨论过macro和micro策略。这里我们将使用macro，并将其作为参数传递给 make_scorer 调用。

```
In [35]:

model = neighbors.KNeighborsClassifier(3)
my_scorer = metrics.make_scorer(metrics.precision_score,
    average='macro')
cv_auc = skms.cross_val_score(model,
    student_ftrs, student_tgt,
    scoring=my_scorer, cv=10)
fig,ax = plt.subplots(1, 1, figsize=(3, 3))
sns.swarmplot(cv_auc, orient='v')
ax.set_title('10-Fold Macro Precision');
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_225_0.png)

遵循一个非常相似的策略，我们可以使用我们的Hand和Till M评估器。

```
In [36]:

htm_scorer = metrics.make_scorer(hand_and_till_M_statistic,
    needs_proba=True)

cv_auc = skms.cross_val_score(model,
    student_ftrs, student_tgt,
    scoring=htm_scorer, cv=10)

fig,ax = plt.subplots(1, 1, figsize=(3, 3))
sns.swarmplot(cv_auc, orient='v')
ax.set_title('10-Fold H&T Ms');
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_225_1.png)

现在，我们可以用几个不同的指标来比较几个不同的分类器。

```
In [37]:

classifiers = {'base'  : dummy.DummyClassifier(strategy="most_frequent"),
               'gnb'   : naive_bayes.GaussianNB(),
               '3-NN'  : neighbors.KNeighborsClassifier(n_neighbors=10),
               '10-NN' : neighbors.KNeighborsClassifier(n_neighbors=3)}
```

```
In [38]:

macro_precision = metrics.make_scorer(metrics.precision_score,
                                    average='macro')
macro_recall    = metrics.make_scorer(metrics.recall_score,
                                    average='macro')
htm_scorer = metrics.make_scorer(hand_and_till_M_statistic,
                                 needs_proba=True)

msrs = ['accuracy', macro_precision,
        macro_recall, htm_scorer]

fig, axes = plt.subplots(len(msrs), 1, figsize=(6, 2*len(msrs)))
fig.tight_layout()

for mod_name, model in classifiers.items():
    # abbreviate
    cvs = skms.cross_val_score
    cv_results = {msr:cvs(model, student_ftrs, student_tgt,
                        scoring=msr, cv=10) for msr in msrs}

    for ax, msr in zip(axes, msrs):
        msr_results = cv_results[msr]
        my_lbl = "{:12s} {: .3f} ({:.2f})".format(mod_name,
                                                msr_results.mean(),
                                                msr_results.std())
        ax.plot(msr_results, 'o-')
        ax.set_title(msr)
        # uncomment to see summary stats (clutters plots)
        #ax.legend(loc='lower center')
```

![](img/d94e4cd766940d79abed0bc6ba4e4344_227_0.png)

# accuracy

# make_scorer(precision_score, average=macro)

# make_scorer(recall_score, average=macro)

# make_scorer(hand_and_till_M_statistic, needs_proba=True)

看起来我们给自己出了一个相当难的问题。准确率、精确率和召回率似乎都非常糟糕。这提醒我们在解读Hand和Till M值时要谨慎。GNB有几个折的值不算糟糕，但GNB的折值中有一半最终接近0.6。还记得我们做的预处理吗？通过丢弃特征和离散化，我们把这个变成了一个非常难的问题。

我们知道情况不妙，但仍有一线希望——也许我们在某些类别上表现不错，只是整体上不佳？

```
In [39]:

fig, axes = plt.subplots(2, 2, figsize=(5, 5), sharex=True, sharey=True)
fig.tight_layout()

for ax, (mod_name, model) in zip(axes.flat,
                                 classifiers.items()):
    preds = skms.cross_val_predict(model,
                                   student_ftrs, student_tgt,
                                   cv=10)

    cm = metrics.confusion_matrix(student_tgt, preds)
    sns.heatmap(cm, annot=True, ax=ax,
                cbar=False, square=True, fmt="d",
                xticklabels=['low', 'med', 'high'],
                yticklabels=['low', 'med', 'high'])

    ax.set_title(mod_name)
axes[1, 0].set_xlabel('Predicted')
axes[1, 1].set_xlabel('Predicted')
axes[0, 0].set_ylabel('Actual')
axes[1, 0].set_ylabel('Actual');
```

