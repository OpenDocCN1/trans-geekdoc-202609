
- 正则化是一组技术，通过缩小模型参数估计来防止过拟合。
- 线性模型有三种正则化技术：岭回归、LASSO 和 弹性网。
- 岭回归使用 L2 规范将参数估计向零收缩（除非它们最初就是零）。
- LASSO 使用 L1 规范将参数估计向零收缩（甚至可能完全为零，从而实现特征选择）。
- 弹性网结合了 L2 和 L1 正则化，其比例由超参数 alpha 控制。
- 对于这三种方法，lambda 超参数控制收缩的强度。

1. 将搜索空间扩展，包括 lambda 的取值范围从 0 到 50。

   ```r
   ridgeParamSpaceExtended <- makeParamSet(
     makeNumericParam("s", lower = 0, upper = 50)
   )
   parallelStartSocket(cpus = detectCores())

   tunedRidgeParsExtended <- tuneParams(
     ridge,
     task = iowaTask,
     # ~30 sec
     resampling = cvForTuning,
     par.set = ridgeParamSpaceExtended,
     control = randSearch
   )
   parallelStop()

   ridgeTuningDataExtended <- generateHyperParsEffectData(tunedRidgeParsExtended)
   plotHyperParsEffect(
     ridgeTuningDataExtended,
     x = "s",
     y = "mse.test.mean",
     plot.type = "line"
   ) + theme_bw()

   # the previous value of s was not just a local minimum,
   # but the global minimum
   ```

2. 绘制岭回归和 LASSO 模型的截距。

   ```r
   coefTibInts <- tibble(
     Coef = rownames(ridgeCoefs),
     Ridge = as.vector(ridgeCoefs),
     Lm = as.vector(lmCoefs)
   )
   coefUntidyInts <- gather(coefTibInts, key = Model, value = Beta, -Coef)
   ggplot(
     coefUntidyInts,
     aes(reorder(Coef, Beta), Beta, fill = Model)
   ) +
     geom_bar(stat = "identity", col = "black") +
     facet_wrap(~Model) +
     theme_bw() +
     theme(legend.position = "none")

   # the intercepts are different. The intercept isn't included when calculating
   # the L2 norm, but is the value of the outcome when all the predictors are zero.
   # As ridge regression changes the parameter estimates of the predictors,
   # the intercept changes as a result
   ```

3. 尝试不同方式绘制超参数调谐过程。

   ```r
   plotHyperParsEffect(
     elasticTuningData,
     x = "s",
     y = "alpha",
     z = "mse.test.mean",
     interpolate = "regr.kknn",
     plot.type = "contour",
     show.experiments = TRUE
   ) +
     scale_fill_gradientn(colours = terrain.colors(5)) +
     geom_point(x = tunedElasticPars$x$s, y = tunedElasticPars$x$alpha) +
     theme_bw()

   plotHyperParsEffect(
     elasticTuningData,
     x = "s",
     y = "alpha",
     z = "mse.test.mean",
     plot.type = "scatter"
   ) + theme_bw()
   ```

4. 使用堆叠条形图（dodged bars）而非 Facet 绘制模型系数。

   ```r
   ggplot(coefUntidy, aes(reorder(Coef, Beta), Beta, fill = Model)) +
     geom_bar(stat = "identity", position = "dodge", col = "black") +
     theme_bw()
   ```

5. 比较 LASSO 模型在高 lambda 下的表现，以及没有预测器的 OLS 模型的性能。

   ```r
   yieldOnly <- select(iowaTib, Yield)
   yieldOnlyTask <- makeRegrTask(data = yieldOnly, target = "Yield")

   lassoStrict <- makeLearner("regr.glmnet", lambda = 500)

   loo <- makeResampleDesc("LOO")

   resample("regr.lm", yieldOnlyTask, loo)

   Resample Result
   Task: yieldOnly
   Learner: regr.lm
   Aggr perf: mse.test.mean=179.3428
   Runtime: 0.11691

   resample(lassoStrict, iowaTask, loo)

   Resample Result
   Task: iowaTib
   Learner: regr.glmnet
   Aggr perf: mse.test.mean=179.3428
   Runtime: 0.316366

   # THE MSE VALUES ARE IDENTICAL. THIS IS BECAUSE WHEN LAMBDA IS HIGH ENOUGH,
   # ALL PREDICTORS WILL BE REMOVED FROM THE MODEL, JUST AS IF WE TRAINED A
   # MODEL WITH NO PREDICTORS
   ```

6. 使用 `plotres()` 函数绘制 glmnet 模型的诊断图。

   ```r
   install.packages("plotmo")

   library(plotmo)

   plotres(ridgeModelData)

   plotres(lassoModelData)

   plotres(elasticModelData)

   # THE FIRST PLOT SHOWS THE ESTIMATED SLOPE FOR EACH PARAMETER FOR DIFFERENT
   # VALUES OF (LOG) LAMBDA. NOTICE THE DIFFERENT SHAPE BETWEEN RIDGE AND LASSO
   ```

距离与树木回归：k-最近邻、随机森林和 XGBoost

**本章涵盖：**

- 使用 k-最近邻算法进行回归
- 使用基于树的算法进行回归
- 比较 k-最近邻、随机森林和 XGBoost 模型，用于预测燃料燃烧时释放的热量

你会发现这一章很轻松。这是因为你之前已经做过所有这些（大概）。在第3章，我向你介绍了 k-NN 算法作为分类工具。在第7章，我向你介绍了决策树，随后在第8章进一步扩展，涵盖随机森林和 XGBoost 用于分类。顺便提一下，这些算法也可以用于预测连续变量。因此，本章将帮助你将这些技能扩展到解决回归问题。

本章结束时，我希望你学会如何将 k-NN 和基于树的算法扩展以预测连续变量。正如你在第7章所学到的，决策树倾向于过拟合训练数据，因此通常通过集成技术显著改进。因此，本章你将训练一个随机森林模型和一个 XGBoost 模型，并将其性能与 k-NN 算法进行对比。

> **注意**
>
> 请回顾第7章，随机森林和 XGBoost 是两种基于树的学习者，它们通过创建许多树的集合来提高预测准确性。随机森林在数据的不同 bootstrap 样本上并行训练许多树，而 XGBoost 则训练顺序树，优先处理未被正确分类的案例。

图12.1 离开家的时间与上班通勤所需时间的示例关系。

图12.2 k-NN 算法用于分类：识别 k 最近邻并取多数投票。线条连接未标记数据与其最近的一个、三个和五个邻居。每种情形下的多数投票由每个黑色十字下方的形状指示。

图12.3 使用 k-NN 进行回归时的投票过程非常相似，只是我们取这 k 个投票的平均值作为新数据的预测值。
