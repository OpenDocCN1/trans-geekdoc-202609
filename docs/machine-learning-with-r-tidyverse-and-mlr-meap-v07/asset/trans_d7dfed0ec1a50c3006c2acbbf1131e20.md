...[/content].

We need to translate all content, preserving symbols. Let's go through the text.

First part:

> **NOTE**  
> It’s important to note that each case in the data only appears in the test set once in this procedure.

We need to translate "NOTE" maybe keep as **NOTE**? The rule: bold needs translation and retain symbols. So **NOTE** should become **注意**? But we need to translate the content, not the markup. The content "NOTE" is inside bold markup. So we translate "NOTE" to Chinese, keep bold markup. So **注意**. Then the sentence: "It’s important to note that each case in the data only appears in the test set once in this procedure." Translate: "重要的是，数据中的每个案例只在本程序的测试集中出现一次。" Keep punctuation.

Next line: `![](img/a22105d68c35e8d5bd3c7bafb4644881_75_0.png)` This is an image link. According to rule: link need translate its content but keep URL. The content is the alt text? The markdown is `![](url)`. There's no link text, just image. The rule says link [link](url) need translate its content but keep URL. For image, it's similar: the content is maybe empty? But we can treat it as a link? Probably we keep the whole line unchanged because there is no textual content to translate. However rule: "链接（[link](https://example.org)）需要翻译其内容，但保留网址。" For image, there is no link text, just the URL. So we keep as is.

Next list items:

- The data are randomly split into *k*, equally-sized folds

Translate: "数据被随机分成 *k* 等大小的折" but need to keep *k* italic. So: "数据被随机分成 *k* 等大小的折" maybe "折" is not right; maybe "折" means "fold". In Chinese we might say "折" or "份". Use "折". Keep *k* italic.

- Each fold is used as the test set once, where the rest of the data make the training set

Translate: "每个折一次作为测试集，其余数据作为训练集". Keep *k* not present.

- For each fold, predictions are made on the test set

Translate: "对每个折，在测试集上进行预测"

- The predictions are compared to the true values

Translate: "预测结果与真实值进行比较"

Next bold **Figure 3.13 k-fold cross-validation (CV).** The data is randomly split into near equally-sized "folds". Each fold is used as the test set once, where the rest of the data are used as the training set. The similarity of the predictions to the true values of the test set is used to evaluate model performance.

We need to translate the whole paragraph, preserving the figure caption "Figure 3.13 k-fold cross-validation (CV)." The caption likely stays as is? The rule: translate content, but keep figure label? The caption includes "Figure 3.13 k-fold cross-validation (CV)." The "Figure 3.13" maybe not translated, but the rest "k-fold cross-validation (CV)" should be translated. Also "The data is randomly split into near equally-sized "folds"." translate.

Let's rewrite:

**Figure 3.13 k折交叉验证 (CV).** 数据被随机分成近乎等大小的“折”。每个折一次作为测试集，其余数据作为训练集。预测结果与测试集的真实值的相似度用于评估模型性能。

But need to keep bold markup for Figure caption? The original has **Figure 3.13 k-fold cross-validation (CV).** So we need to keep ** and translate the text inside. So **Figure 3.13 k折交叉验证 (CV).** The "Figure" maybe keep English? Usually translate "Figure" to "图". But the rule says translate content. So "Figure" should become "图". So **图 3.13 k折交叉验证 (CV).** Let's do that.

Next paragraph:

This approach will typically give a more accurate estimate of model performance because every case appears in the test set once, and we are averaging the estimates over many runs. But we can improve this a little by using *repeated* *k*-fold cross-validation, where after the procedure above, we shuffle the data around and perform it again.

Translate: "这种方法通常能给出更准确的模型性能估计，因为每个案例都会在测试集中出现一次，并且我们对多次运行的估计进行平均。但我们可以通过使用 *repeated* *k*-折交叉验证来稍微改进它，在上述程序之后，我们对数据进行打乱并再次执行。" Need to keep *repeated* and *k*-fold italic. So "*repeated* *k*-折交叉验证". Keep italic markup.

Next:

For example, a commonly chosen value of *k* for *k*-fold is ten. Again, this depends on the size of the data among other things, but is a reasonable value for many datasets. This means that we split the data into 10, near equal-sized chunks and perform the cross-validation. If we repeat this procedure five times, then we have ten-fold cross-validation repeated five times (this is *not* the same as 50-fold cross-validation) and the estimate of model performance will be the average of 50 different runs.

Translate: "例如，通常选择的 *k* 值为十。再次，这取决于数据的大小等因素，但在许多数据集中是一个合理的值。这意味着我们将数据分成 10 个近乎相等的块并进行交叉验证。如果我们重复此过程五次，则十折交叉验证被重复五次（这与 50 折交叉验证不同）并且模型性能的估计将是 50 次不同运行的平均值。" Keep *k* and *k*-fold italic.

Next:

Therefore, if you have the computational power, it is usually preferred to use repeated *k*-fold cross-validation instead of ordinary *k*-fold and this is what we’ll be using through many examples in this book.

Translate: "因此，如果你有计算能力，通常更倾向于使用 *repeated* *k*-折交叉验证而不是普通 *k*-折交叉验证，而这正是我们在本书的许多示例中使用的方法。" Keep *repeated* and *k*-fold italic.

Now the section "## PERFORMING K-FOLD CROSS-VALIDATION"

We need to translate the heading? The heading is "## PERFORMING K-FOLD CROSS-VALIDATION". Should we translate? The rule: translate content, keep formatting. The heading text is content, so translate to "## 执行 K 折交叉验证". Keep "##". So:

## 执行 K 折交叉验证

Next paragraph:

"We perform k-fold cross-validation in the same way as we did for hold-out (see code listing 3.6). This time, when we make our resampling description, we tell it we’re going to use repeated k-fold cross validation ("RepCV"), and tell it how many folds we want to split the data into. The default number of folds is 10, which is often a good choice, but I wanted to show you how you can explicitly control the splits. Next, we tell the function that we want to repeat the 10-fold cross-validation 50 times with the reps argument. This gives us 500 performance measures to average across! Again, we ask for the classes to be stratified among the folds."

Translate:

"我们以同样的方式执行 K 折交叉验证，如在保留出 (hold-out) 时所做（参见代码列表 3.6）。这次，当我们制作抽样描述时，告诉它我们要使用 *repeated* *k*-折交叉验证（"RepCV"），并指定我们想要将数据分成多少折。默认的折数是 10，通常是个好选择，但我想展示你如何明确控制折数。随后，我们使用 `reps` 参数告诉函数重复 10 折交叉验证 50 次。这将产生 500 个性能度量供平均！此外，我们要求类在折之间进行分层。"

Need to keep inline code `reps` and "RepCV". Also code listing 3.6 maybe keep as is.

Next:

### Listing 3.6 Creating a k-fold cross validation resampling description

Translate heading: "### 列表 3.6 创建 K 折交叉验证抽样描述". Keep "###". Also keep the code block unchanged.

Next code block:

```r
kFold <- makeResampleDesc(method = "RepCV", folds = 10, reps = 50,
                           stratify = TRUE)

kFoldCV <- resample(learner = knn, task = diabetesTask,
                    resampling = kFold, measures = list(mmce, acc))
```

We keep unchanged.

Next paragraph:

"Now let’s extract the averaged performance measures."

Translate: "现在让我们提取平均的性能度量。"

Next code block:

```
kFoldCV$aggr

mmce.test.mean   acc.test.mean
     0.1022788      0.8977212
```

We keep unchanged.

Next paragraph:

"So the model correctly classified 89.8% of cases on average, much lower than when we predicted the data we used to train the model! Re-run the `resample()` function here a few times and compare the average accuracy after each run. The estimate is much more stable than when we repeat hold-out cross-validation."

Translate: "因此，模型在平均意义上正确分类了 89.8% 的案例，这远低于我们使用训练数据进行预测的情况！请在此处多次运行 `resample()` 函数并比较每次运行后的平均准确率。与重复保留出交叉验证相比，该估计更为稳定。"

Next:

> **TIP**  
> We’re usually only interested in the average performance measures, but you can access the performance measure from every iteration by running:
>
> ```r
> kFoldCV$measures.test
> ```

Translate: "**TIP** 我们通常只关心平均的性能度量，但如果你想查看每次迭代的度量，可以运行：" Keep **TIP** bold and translate to "提示". So **提示**.

Next code block unchanged.

Next section: "## HOW TO CHOOSE THE NUMBER OF REPEATS"

Translate heading: "## 如何选择重复次数"

Paragraph:

"Your goal when cross-validating your model is to get as accurate and stable an estimate of model performance as possible. Broadly speaking, the more repeats you can do, the more accurate and stable these estimates will become. At some point though, having more repeats won’t improve the accuracy or stability of the performance estimate."

Translate: "在交叉验证模型时，你的目标是获得尽可能准确和稳定的模型性能估计。广义地说，重复次数越多，这些估计越准确和稳定。不过，在某些时候，增加重复次数并不会提升估计的准确性或稳定性。"

Next:

"So how do we decide on how many repeats to perform? A sound approach is to choose a number of repeats that is computationally reasonable, run the process a few times and see if the average performance estimate varies a lot. If not, great. If it does vary a lot, you should increase the number of repeats."

Translate: "那么我们该如何决定进行多少次重复呢？一个合理的做法是选择一个在计算上可行的重复次数，运行几次并观察平均性能估计是否波动很大。如果不波动，太好了。如果波动很大，则应增加重复次数。"

Next:

## EXERCISE 3.3

Translate heading: "## 练习 3.3"

Paragraph:

"Define two new resampling descriptions, one that performs 3-fold cross-validation repeated 5 times, and one that performs 3-fold cross-validation repeated 500 times (don't overwrite your existing description). Use the `resample()` function to cross validate the k-NN algorithm using both of these resampling descriptions. Repeat the resampling 5 times for each method and see which one gives more stable results."

Translate: "定义两个新的抽样描述，一个是执行 3 折交叉验证重复 5 次，另一个是执行 3 折交叉验证重复 500 次（不要覆盖已有的描述）。使用 `resample()` 函数对 k-NN 算法分别使用这两种抽样描述进行交叉验证。对每种方法重复 5 次，观察哪种方法给出更稳定的结果。"

Next:

"Now, let's build the confusion matrix based on the repeated k-fold cross-validation:"

Translate: "现在，基于重复的 K 折交叉验证构建混淆矩阵："

Next code block:

```r
calculateConfusionMatrix(kFoldCV$pred, relative = TRUE)
```

Keep unchanged.

Next text:

**Relative confusion matrix (normalized by row/column):**

Translate: "**相对混淆矩阵（按行/列归一化）：**"

Then the table. Need to translate the table content? The table headers and values are English terms like "Chemical", "Normal", "Overt", "-err.-". Should we translate the labels? The rule says translate content, but table content may be considered part of the content. Should we translate the labels? Probably yes, translate the Chinese equivalents. Let's translate:

- Chemical -> 化学
- Normal -> 正常
- Overt -> 过量? maybe "过量" but context maybe "Overdose"? Not sure. Could be "过量" or "过高". Let's assume "过量". But maybe "Overt" refers to "overt" as a class name, maybe keep as is? The instruction: translate content, but keep table format. I'd translate the Chinese labels but keep the English terms? The example earlier translated "Feynman's learning method" etc. For table, likely we translate the class names. Let's translate:

Chemical -> 化学
Normal -> 正常
Overt -> 过量 (or "显性"? Not sure). Let's choose "过量". 
-err.- -> "-err.-" maybe stands for "error"? Could translate to "-错误-"? But maybe keep as is. The dash and period maybe keep. Let's translate to "-错误-"? Hmm. The original column header is "-err.-". Might be "error". Let's translate to "-错误-". But keep the dash format. Maybe "-err.-" is a class name, maybe keep unchanged. However to be safe, translate to Chinese: "-错误-". Let's do that.

Rows:

- Chemical row: "0.81/0.78" etc. Those are numbers, keep.

- Normal row: "0.04/0.07" etc.

- Overt row: "0.16/0.14" etc.

- -err.- row: "0.22" etc.

We need to keep the table formatting with markdown.

Absolute confusion matrix:

Similarly translate class names.

Absolute confusion matrix:

| | 化学 | 正常 | 过量 | -错误- |
|---|---:|---:|---:|---:|
| 化学 | 1463 | 179 | 158 | 337 |
| 正常 | 136 | 3664 | 0 | 136 |
| 过量 | 269 | 0 | 1381 | 269 |
| -错误- | 405 | 179 | 158 | 742 |

Need to ensure the dash column header maybe keep as "-err.-"? We'll translate to "-错误-". Let's keep as "-错误-".

Now next paragraph:

> Notice that the number of cases is much larger. This is because we repeated the procedure 50 times!

Translate: "请注意，案例数量要大得多。这是因为我们重复了 50 次！"

Next:

"Leave-one-out cross-validation can be thought of as the extreme of k-fold cross-validation: instead of breaking the data up into folds, we simply reserve a single observation as a test case, train the model on the whole of the rest of the data, then pass the test case through it and record the relevant performance metrics. Now, we do the same but select a different observation as the test case. We continue doing this until every observation has been used as the test case once, where we take the average of the performance metrics. You can see a scheme of leave-one-out cross-validation in figure 3.14."

Translate: "留一出交叉验证可以被视为 K 折交叉验证的极端：与其把数据分成折，我们只保留单个观测作为测试案例，在其余全部数据上训练模型，然后将测试案例送入模型并记录相关的性能指标。我们重复此过程，但每次选择另一个观测作为测试案例。直到每个观测都作为测试案例一次，我们取性能指标的平均值。你可以在图 3.14 中看到留一出交叉验证的方案。"

Next:

"Now because the test set is only a single observation, leave-one-out cross-validation tends to give quite variable estimates of model performance (because the performance estimate of each iteration depends on correctly labeling that single test case). But, it can give less variable estimates of model performance than k-fold, when your dataset is small. When you have a small dataset, splitting it up into k folds will leave you with a very small training set. The variance of a model trained on a small dataset tends to be higher because it will be more influenced by sampling error/unusual cases. Therefore, leave-one-out cross-validation is useful for small datasets where splitting it into k-folds would give variable results. It is also computationally less expensive than repeated k-fold cross-validation."

Translate accordingly.

Next:

"## Leave-one-out CV"

Translate heading: "## 留一出交叉验证"

Next image: `![](img/a22105d68c35e8d5bd3c7bafb4644881_78_0.png)` keep unchanged.

Next caption:

**Figure 3.14 Leave-one-out cross-validation (CV).** Leave-one-out CV is the extreme of k-fold, where we reserve a single case as the test set, and train the model on the remaining data. The similarity of the predictions to the true values of the test set is used to evaluate model performance.

Translate: "**图 3.14 留一出交叉验证 (CV)。** 留一出交叉验证是 K 折交叉验证的极端，我们保留单个案例作为测试集，在其余数据上训练模型。预测结果与测试集的真实值的相似度用于评估模型性能。"

Next bullet list:

- Use all of the data except a single case as the training set

Translate: "- 使用除单个案例外的全部数据作为训练集"

- Predict the value of the single test case

Translate: "- 预测单个测试案例的值"

- Repeat until every case has been the test case

Translate: "- 重复直至每个案例都成为测试案例"

- The predictions for each case are compared to the true values

Translate: "- 对每个案例的预测与真实值进行比较"

Next quote:

> A supervised learning model which has not been cross-validated is virtually useless, because you have no idea whether the predictions it will make on new data will be accurate or not!

Translate: "受监督学习模型如果没有进行交叉验证，几乎是毫无用处的，因为你无法判断它在新数据上做出的预测是否准确。"

Next paragraph:

"Creating a resampling description for leave-one-out is just as simple as for hold-out and k-fold cross-validation. We specify leave-one-out cross-validation when making the resample description by supplying "LOO" as the argument to method. Because the test set is only a single case, we obviously can’t stratify with leave-one-out. Also, because each case is used as the test set once, with all the other data being used as the training set there’s no need to repeat the procedure."

Translate: "创建留一出交叉验证的抽样描述与保留出和 K 折交叉验证一样简单。我们在制作抽样描述时通过将 `method` 参数设置为 \"LOO\" 来指定留一出交叉验证。由于测试集只包含单个案例，我们无法对留一出进行分层。此外，因为每个案例只作为测试集一次，其余数据全部用作训练集，因此无需重复该过程。"

Next code block:

```r
LOO <- makeResampleDesc(method = "LOO")
```

Keep unchanged.

Now we need to wrap everything in [content]...