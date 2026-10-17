
优化器的学习率决定了优化器在每次训练步骤中如何更新其权重。如果你将学习率设置得过高，优化器会对权重做出剧烈改变，并且可能永远无法收敛到解决方案。如果你将学习率设置得过低，优化器将进展缓慢，并且可能收敛到局部最小值而不是全局最小值。

典型的学习率从 0.0001 到 0.5 不等，但最佳学习率因应用而异。我建议从一个较高的值开始，并反复降低学习率，直到你对应用的准确性和性能感到满意。

### Check Weights and Gradients

机器学习应用经常失败，因为权重降为零（消失梯度问题）或变得非常大（爆炸梯度问题）。在两种情况下，你可能需要调整网络中的层数和/或每一层的激活函数。

值得庆幸的是，TensorFlow 允许你保存层的权重并使用 TensorBoard 可视化权重。Chapter 4 介绍了 TensorBoard 并解释了如何生成和打印用于可视化的摘要数据。Chapter 5 解释了如何使用 TensorBoard 可视化训练结果。

### About the Author

Matthew Scarpino 几乎 20 年来一直是程序员和工程师。除了为图像识别开发神经网络外，他还为国防高级研究计划局（DARPA）设计了模拟人类认知的电路。他目前是 plutocracy.com 的首席开发人员，该公司使用机器学习分析金融趋势。

Matthew 于 2018 年成为 Google 认证数据工程师。业余时间，他编程机器人并在 TensorFlow 博客 [`tfblog.com`](http://tfblog.com) 上撰写文章。

### Dedication

本书献给人工智能先驱 Frank Rosenblatt。尽管他的同时代人将他视为一个眼高手低的学者，但现代成就不仅证实了他最狂野的预测，而且还超越了它们。

### Author’s Acknowledgments

在 20 世纪 90 年代末，我在一家大学书店偶然发现了 *C For Dummies*，并深深爱上了它。Dan Gookin 不仅让 C 编程变得易于理解——他还让它变得 *funny*。我花了很多快乐的时光阅读他荒诞的解释并练习他奇思妙想的编程示例。

我不是 Dan Gookin 的一半，但我很想感谢执行编辑 Katie Mohr 给了我撰写 *For Dummies* 书籍的机会。作为一个新人，我有无数愚蠢的问题，范围从章节结构到表格字体再到方程格式。Katie 回复了每一个问题，而且她的愉快态度从未动摇过片刻。

本书的项目编辑 Kelly Ewing 做得非常出色。她不知疲倦地改进了文本的清晰度和质量，这本书从她细心的关注中受益匪浅。此外，我花了一些时间来适应 *For Dummies* 的编辑标准，我非常感激 Kelly 的耐心和帮助。

多产的作者 Guy Hart-Davis 从技术角度审阅了本书并提供了评论和支持。得益于他的反馈，我重写了许多段落，以更好地解释 TensorFlow 对机器学习的方法。此外，Guy 发现的许多技术错误比我愿意承认的要多。谢谢你，Guy！

我谨向整个 Wiley 出版团队表示深深的感谢。特别是，我要感谢 Lisa Stiers 校对文本的工作，以及 Tamilmani Varadharaj 作为制作编辑的工作。

最后但并非最不重要，我要感谢文学代理的佼佼者 Matt Wagner。从我的初始提案到出版的书籍，他一直担任代理、编辑、教练和外交官。尽管同时处理多个项目，他总是抽出时间来解答我的问题和疑虑。

##### 出版社致谢

高级收购编辑：Amy Fandrei

项目编辑：Kelly Ewing

校对编辑：Kelly Ewing

编辑助理：Serena Novosel

高级编辑助理：Cherie Case

审阅者：Guy Hart-Davis

制作编辑：Tamilmani Varadharaj

封面图片：© Funny Drew/Shutterstock

![](img/ad1.png)![](img/ad2.png)![](img/ad3.png)![](img/ad4.png)

随身携带 Dummies！

![Dummies Logo](http://www.dummies.com)

访问我们的 [网站](http://www.dummies.com)

![Facebook Logo](http://www.facebook.com/fordummies)

在 [Facebook](http://www.facebook.com/fordummies) 点赞我们

![Twitter Logo](http://www.twitter.com/fordummies)

在 [Twitter](http://www.twitter.com/fordummies) 关注我们

![YouTube Logo](http://www.youtube.com/user/fordummies)

在 [YouTube](http://www.youtube.com/user/fordummies) 观看我们

![LinkedIn Logo](http://www.linkedin.com/groups?home=&gid=3229946&trk=anet_ug_hm)

在 [LinkedIn](http://www.linkedin.com/groups?home=&gid=3229946&trk=anet_ug_hm) 加入我们

![Pinterest Logo](http://pinterest.com/fordummies/)

在 [Pinterest](http://pinterest.com/fordummies/) 为我们钉选

![Google Plus Logo](https://plus.google.com/105265587979403653723)

在 [google+](https://plus.google.com/105265587979403653723) 关注我们

![Newsletter Envelope Icon](http://www.dummies.com/go/newsletter)

订阅我们的 [newsletter](http://www.dummies.com/go/newsletter)

![Book Cover Icon](http://covers.dummies.com/)

创建你自己的 [Dummies book cover](http://covers.dummies.com/)

![Shopping Bag Icon](http://dummiesmerchandise.com)

[在线购物](http://dummiesmerchandise.com)

![For Dummies, A Wiley Brand](img/dummies-wordmark.png)

### 索引

##### A

1. `abs` 函数，36

2. 累积，动量算法，75–76

3. 激活函数

    1. 分类函数，126–127

    2. 概述，121，123–124

    3. 整流函数，124–126

    4. 饱和，136–137

    5. 使用反向传播训练，129

4. 激活参数，157，185

5. `activation_fn` 参数，138，144，145，147

6. `activity_regularizer` 参数，157

7. `AdagradOptimizer` 类，76–77

8. `AdamOptimizer` 类，77–78

9. 自适应梯度算法，76–77

10. `add` 函数，36

11. `add_event` 方法，60，61–62

12. `add_graph` 方法，60，62

13. `add_loss` 方法，185

14. `add_meta_graph` 方法，61，62，85

15. `add_meta_graph_and_variables` 函数，85，86

16. `add_n` 函数，36

17. `add_run_metadata` 方法，61

18. `add_session_log` 方法，61

19. `add_summary` 方法，60，61，64，89–90

20. `add_to_collection` 方法，47

21. `add_to_collections` 方法，47

22. `add_update` 方法，185

23. `add_variable` 方法，185

24. `adjust_brightness` 函数，169，170

25. `adjust_contrast` 函数，169，170，175

26. `adjust_gamma` 函数，169，170

27. `adjust_hue` 函数，169，170

28. `adjust_saturation` 函数，169，170

29. 高级打包工具 (`APT`)，20

30. `after_create_session` 方法，91

31. `after_run` 方法，91，92

32. `allocator_type` 字段，238

33. `allow_growth` 字段，237，238

34. `allow_soft_placement` 选项，227

35. AlphaGo 程序，Google，1，129

36. 应用组，`gcloud`，282

37. `apply_regularization` 函数，141

38. `arg_scope` 函数，143，147

39. `argmax` 函数，37，38

40. `argmin` 函数，37，38

41. `args` 字段，301

42. 参数作用域，143

43. 数组。 *参见* 张量

44. 人工神经网络 (`ANNs`)。 *参见* 神经网络

45. `as_cluster_def` 方法，270

46. `as_default` 方法，46–47

47. `as_graph_def` 方法，49

48. `as_text` 参数，86

49. assets 子目录，84

50. assets.extra 子目录，84

51. audio data field, 59

52. audio function, 58

53. auth group, gcloud, 282

54. author parameter, 292

55. author_email parameter, 292

56. averaging filter, 151–152

57. `avg_pooling2d` function, 159

58. `axes` parameter, 41, 134

59. `axis` parameter, 34, 35

60. axons, 119

##### B

1. backpropagation, 129–131

2. backpropagation through time (BPTT), 182–183

3. Bahdanau, Dzmitry, 196

4. basic math operations, 35–37

5. `BasicLSTMCell` class, 194–195, 196

6. `BasicRNNCell` class, 185–187

7. batch method, 209

8. batch normalization (BN), 134, 136–139, 147, 317

9. `batch_norm` function, 137–139, 147

10. `batch_normalization` function, 134–135

11. `batch_weights` parameter, 138

12. batches, 79–82, 209, 317

13. `batchSize` field, 304

14. `--batch-size` flag, 298

15. `Bazel` tool, Google, 229–230, 232, 233, 234–235

16. `before_run` method, 91

17. `begin` method, 91

18. `begin` parameter, 34

19. BellKor Pragmatic Chaos, 13

20. Bengio, Yoshua, 126, 196

21. Bergstra, James, 126

22. bias, 121, 122–123, 133, 194

23. `bias_initializer` parameter, 157, 197

24. `bias_regularizer` parameter, 157

25. `biases_initializer` parameter, 144, 145

26. `biases_regularizer` parameter, 144, 145

27. bicubic interpolation, 174

28. big data revolution, 12–13

29. bilinear interpolation, 173–174

30. billing, for GCP projects, 279

31. binary files, 205–208

32. binary logistic regression

    1. defined, 100

    2. example code, 108–110

    3. logistic function, 106–107

    4. maximum likelihood estimation, 107–108

    5. overview, 105

    6. setting up problem, 105–106

33. bizarro datasets, 221–224

34. BN (batch normalization), 134, 136–139, 147, 317

35. Boston dataset, 223–224, 257

36. box filter, 151–152

37. BPTT (backpropagation through time), 182–183

38. `bucketized_column` function, 255, 256

39. buckets, Google Cloud Storage, 283–285, 286–289

40. `BUILD` file, 229–230

41. `build_signature_def` function, 85

42. building TensorFlow. *See* source code, building TensorFlow from

##### C

1. `-c` flag, 287

2. `cache` method, 210, 211

3. `Caffe` framework, 14

4. `cast` function, 33

5. `cat` command, 287, 289

6. categorical columns, 254–256, 268

7. `_CategoricalColumn` class, 254

8. `ceil` function, 37, 38

9. `cell_clip` parameter, 195

10. cells, RNN

    1. basic RNNs, 185–187

    2. creating, 183–185

    3. GRU, 196–197

    4. LSTM, 183, 192–196

5. 多层，190–191

11. `cells` 参数，190

12. 人口普查数据，分析，264–269

13. `center` 参数，138，139

14. `central_crop` 函数，172，174

15. 微积分链式法则，131

16. Cheat Sheet，解释，3

17. `checkpoint_and_export` 参数，271

18. `checkpoint_path` 参数，250，251

19. `CheckpointSaverHook` 类，93，96

20. chief，在集群中，243，246

21. `ChiefSessionCreator` 子类，94

22. Cho，Kyunghyun，196

23. Chollet，François，15

24. CIFAR-10 数据集，160–166

25. 类，1，2，309–313。*另请参阅 specific classes*

26. 分类器函数，126–127

27. 分类器（估计器类）

    1. 组合线性-DNN，262–263

    2. `DNNClassifier` 类，260–262

    3. 概述，256–257

28. 对图像进行分类。*参见* convolutional neural networks；image classification；image filtering

29. 客户端，在集群中，238

30. `close` 方法，61，62，206

31. Cloud Console，Google，279，299

32. Cloud Storage，Google。*另请参阅* Google Cloud Platform

    1. 存储桶，283–285

    2. 部署应用程序到云，295–299

    3. `gsutil` 实用程序，286–290

    4. 对象和虚拟层次结构，285–286

    5. 概述，283

33. `cluster` 字段，269，270

34. `cluster_def` 选项，227

35. 集群

    1. `ClusterSpec`，创建，239–240

    2. 估计器，在中运行，269–270

    3. 示例代码，244–246

    4. 在 Google Cloud Platform 中，299–305

        1. 作业和任务，指定，241–244

        2. `MonitoredSessions`，243–244

        3. 概述，238–239

        4. 参数服务器，241，242

        5. 服务器，创建，240–241
