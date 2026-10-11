
一个示例是：

```
ConceptDriftStream -s (generators.AgrawalGenerator -f 7)
-d (generators.AgrawalGenerator -f 2) -w 1000000 -p 900000
```

其中 `ConceptDriftStream` 的参数为：

*   `-s`：初始流生成器
*   `-d`：漂移或变化后的流生成器
*   `-p`：变化的中心位置
*   `-w`：变化周期的宽度

### 练习 3.3

比较霍夫丁树与朴素贝叶斯分类器的准确率，针对速度变化为 0.001、包含 1,000,000 个实例的 `RandomRBFGenerator` 流，使用交织测试-再-训练评估。

此示例所需的任务为：

```
EvaluateInterleavedTestThenTrain -l bayes.NaiveBayes
-s (generators.RandomRBFGeneratorDrift -s 0.001)
-i 1000000 -f 10000
```

```
EvaluateInterleavedTestThenTrain -l trees.HoeffdingTree
-s (generators.RandomRBFGeneratorDrift -s 0.001)
-i 1000000 -f 10000
```

两个分类器的对比显示在 [图 3.6](#chapter_3.xhtml#fig3-6)。

![图 3.6 练习 3.3，在非平稳流上比较霍夫丁树和朴素贝叶斯分类器。](images/Fig3-6.png)

[**图 3.6**](#chapter_3.xhtml#rfig3-6)

练习 3.3，在非平稳流上比较霍夫丁树和朴素贝叶斯分类器。

### 练习 3.4

比较上一练习中流使用三种不同分类器的准确率：

*   叶节点采用多数类的霍夫丁树
*   霍夫丁自适应树
*   ADWIN 装袋 (`OzaBagAdwin`) 基于十棵霍夫丁树

此示例所需的任务为：

```
EvaluateInterleavedTestThenTrain -l (trees.HoeffdingTree -l MC)
-s (generators.RandomRBFGeneratorDrift -s 0.001)
-i 1000000 -f 10000
```

```
EvaluateInterleavedTestThenTrain -l trees.HoeffdingAdaptiveTree
-s (generators.RandomRBFGeneratorDrift -s 0.001)
-i 1000000 -f 10000
```

```
EvaluateInterleavedTestThenTrain -l meta.OzaBagAdwin
-s (generators.RandomRBFGeneratorDrift -s 0.001)
-i 1000000 -f 10000
```

这三个分类器的对比显示在 [图 3.7](#chapter_3.xhtml#fig3-7)。我们观察到，由于数据流在演化和变化，两种自适应分类器的表现比标准霍夫丁树好得多。

![图 3.7 练习 3.4，比较三种不同的分类器。](images/Fig3-7.png)

[**图 3.7**](#chapter_3.xhtml#rfig3-7)

练习 3.4，比较三种不同的分类器。

## 3.3 使用命令行

使用命令行的一个简便方法是复制并粘贴 GUI 中 `Configure` 行的文本。例如，假设我们想从命令行执行任务

```
EvaluatePrequential -l trees.HoeffdingTree -i 1000000 -w 10000
```

我们可以简单地写成

```
java -cp moa.jar -javaagent:sizeofag.jar moa.DoTask
"EvaluatePrequential -l trees.HoeffdingTree -i 1000000 -w 10000"
```

注意某些参数缺失，因此将使用默认值。我们将在以下段落中解释该行命令。

类 `moa.DoTask` 是在命令行运行任务的主类。它将接受一个任务名称及其相应的任何参数。第一个使用的任务是 `LearnModel` 任务。`-l` 参数指定学习器，本例中为 `HoeffdingTree` 类。`-s` 参数指定学习所用的流，本例中为 `generators.WaveformGenerator`，这是一个数据流生成器，产生一个识别三种波形类型的三分类学习问题。`-m` 选项指定用于训练学习器的最大示例数，本例中为 1,000,000 个示例。`-O` 选项指定一个文件以输出结果模型：

```
java -cp moa.jar -javaagent:sizeofag.jar moa.DoTask
LearnModel -l trees.HoeffdingTree
-s generators.WaveformGenerator -m 1000000 -O model1.moa
```

这将创建一个名为 `model1.moa` 的文件，其中包含训练期间生成的决策树模型。

下一个示例将评估该模型，以查看其在使用不同随机种子生成的示例集上的准确率。`EvaluateModel` 任务获得加载上一步生成的模型、生成随机种子为 2 的新波形流、并在 1,000,000 个示例上测试所需的参数：

```
java -cp moa.jar -javaagent:sizeofag.jar moa.DoTask
"EvaluateModel -m file:model1.moa
-s (generators.WaveformGenerator -i 2) -i 1000000"
```

注意我们正在使用括号嵌套参数。任务描述外加了引号，否则操作系统可能会对括号的含义感到困惑。

评估后显示以下统计信息：

```
classified instances = 1,000,000
classifications correct (percent) = 84.474
Kappa Statistic (percent) = 76.711
```

请注意，上述两步可以合二为一，避免创建外部文件，如下所示：

```
java -cp moa.jar -javaagent:sizeofag.jar moa.DoTask
"EvaluateModel -m (LearnModel -l trees.HoeffdingTree
-s generators.WaveformGenerator -m 1000000)
-s (generators.WaveformGenerator -i 2) -i 1000000"
```

任务 `EvaluatePeriodicHeldOutTest` 将在周期性间隔使用保留测试集拍摄性能快照的同时训练模型。以下命令创建一个*逗号分隔值* (CSV) 文件，在 `WaveformGenerator` 数据上训练 `HoeffdingTree` 分类器，使用前 100,000 个示例进行测试，总共训练 100,000,000 个示例，并每 1,000,000 个示例测试一次：

```
java -cp moa.jar -javaagent:sizeofag.jar moa.DoTask
"EvaluatePeriodicHeldOutTest -l trees.HoeffdingTree
-s generators.WaveformGenerator
-n 100000 -i 10000000 -f 1000000" > dsresult.csv
```

这些是我们如何从命令行使用 MOA 的示例。在本书第二部分中，我们将讨论此处出现的分类器。在第三部分中，我们将解释此处使用的生成器，并了解如何从用 Java 编写的源代码中使用 MOA API。

# 第二部分：流挖掘

# 4 流与素描

流可以被视为数据的一次性读取序列。流上的算法必须在我们称为*数据流公理*的条件下工作，这些公理已在第二章中说明：

1.  只允许对流进行一次遍历；每个流项目只能被观察一次。
2.  每个项目的处理时间必须很低。
3.  内存使用也必须很低，当然要低于流长度的亚线性级别；这意味着只能显式存储少量流项目。
4.  算法必须能够随时提供答案。
5.  流随时间演化，即它们是非平稳数据源。

本章关注的是满足前四条公理的算法设计。我们对流、生成流项目的过程或其可能遵守的任何统计规律*不做任何概率假设*。流是*对抗性*生成的，即遵循对算法最困难的模式。因此，公理 5 在本章中无关紧要。相比之下，在第五章中，我们将定义一种更良性的流生成模型，其中项目根据某个随机过程生成，因此遵守统计规律。这一假设让我们能够形式化公理 5，且隐含在大多数可用的流机器学习和数据挖掘算法中。

许多流问题的解决方案都使用流*素描*或*摘要*的概念。素描是一种数据结构及其伴随算法，它们读取流并存储足够的信息，以便能够回答关于流的一个或多个预定义查询。我们将把素描视为流上高层学习和挖掘算法的构建模块。从这个角度来看，使用少量内存的要求尤为迫切，因为挖掘算法通常不会创建单个素描，而是创建许多素描，以同时跟踪数据上的许多不同统计量。

## 4.1 设置：近似算法
