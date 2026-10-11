
# 深度学习数据改进的进展

该领域仍有一些非常有趣的进展，其核心思想围绕着改进数据。例如，虽然数据增强已经存在一段时间，且对许多深度学习应用至关重要，但今年 Google 发布了 [auto-augment](https://ai.googleblog.com/2018/06/improving-deep-learning-performance.html?m=1)，这是一种利用深度强化学习自动增强训练数据的方法。一个更极端的想法是使用合成数据训练深度学习模型。这在实践中已尝试一段时间，并被许多人视为人工智能未来的关键。

NVIDIA 在其论文 [《使用合成数据训练深度学习》](https://arxiv.org/abs/1804.06516) 中提出了有趣的新观点。在我们的论文 [《向专家学习》](https://arxiv.org/abs/1804.08033) 中，我们也展示了如何利用专家系统生成合成数据，这些数据随后可用于训练深度学习系统，甚至在与真实世界数据结合后依然有效。最后，同样有趣的是利用弱监督来减少对大量人工标注数据的需求。[Snorkel](https://blog.acolyer.org/2018/08/22/snorkel-rapid-training-data-creation-with-weak-supervision/amp/?__twitter_impression=true) 是一个非常有趣的项目，旨在通过提供通用框架来促进这种方法。

## AI 领域的基础性突破

就 AI 更基础性的突破而言，这可能与我及我的关注点有关，但我没有看到太多。我不完全赞同 Hinton 的观点，他认为缺乏创新是因为该领域存在 **“少数资深大牛和海量年轻小伙子”** 的现象，尽管科学界确实存在一种趋势，即 [突破性研究多在较晚年龄完成](https://phys.org/news/2011-11-breakthrough-scientific-discoveries-longer-dominated.html)。

依我之见，目前缺乏突破的主要原因在于，现有方法及其变体仍有许多有趣的实际应用，因此很难冒险去尝试那些可能无法立即见效的新方法。当该领域的大多数研究由大公司赞助时，这一点更为相关。虽然这种做法高度依赖经验且使用已知方法，但它也为发现新方法敞开了大门，因为它证明了通常被视为最优的方法并非如此。另一篇极具探索性的论文是最近获得 NeurIPS 最佳论文奖的 [《神经常微分方程》](https://arxiv.org/abs/1806.07366)，它挑战了深度学习中的一些基本概念，包括层这一概念本身。

有趣的是，这篇论文的动机源于一个项目，作者们在其中研究医疗数据（更具体地说是电子健康记录）。如果不提及 AI 与医疗交叉领域的研究，我就无法结束这篇总结，因为那是我在 Curai 的工作重点。不幸的是，该领域进展太多，我需要另写一篇文章才能覆盖。因此，我仅推荐大家关注 [MLHC 会议](https://www.mlforhc.org/) 和 [ML4H NeurIPS 研讨会](https://ml4health.github.io/2018/) 发布的论文。我们 [Curai](https://www.curai.com/) 团队在这两个会议上都有论文被录用，所以你们可以在那里找到我们的论文，以及许多其他有趣的论文，从而了解我们领域的最新动态。

# 使用 Python 进行机器学习中的对象与类

Python 支持不同的编程范式，因为它是一门多范式语言。Python 中的对象具有属性和行为。在使用 Python 面向对象编程语言学习机器学习时，理解对象和类至关重要。

## 示例：汽车作为对象

- **属性**：`color`、`mileage`、`model`、`age`
- **行为**：`reverse`、`speed`、`turn`、`roll`、`stop`、`start`

## 类

类是创建对象的模板。

### 示例

```python
class Car:
```

### 重要提示

按照惯例，类名的首字母大写。按照惯例，类名使用单数形式。

## 语法

```python
class Name_of_Class:
```

通过简单地实例化类，我们可以从类构建对象。`class_name()` 运算符通过将对象赋值给空方法来创建对象。

## 对象/类实例化

从我们的 `Car` 类，我们可以拥有多个对象，如第一辆车、第二辆车或 SUV。

### 示例

1. 启动 IDLE。
2. 导航到“文件”菜单并点击“新建窗口”。
3. 输入以下内容：

```python
my_car = Car()
pass
```

### 练习

a. 为学生创建一个类和一个对象。
b. 为医院创建一个类和一个对象。
c. 为银行创建一个类和一个对象。
d. 为警察局创建一个类和一个对象。

### 带属性的示例

1. 启动 IDLE。
2. 导航到“文件”菜单并点击“新建窗口”。
3. 输入以下内容：

```python
class Car:
    category = "Personal Automobile"

    def __init__(self, model, insurance):
        self.model = model
        self.insurance = insurance

subaru = Car("Subaru", "Insured")
toyota = Car("Toyota", "Uninsured")

print("Subaru is a {}".format(subaru.__class__.category))
print("Toyota is a {}".format(toyota.__class__.category))
print("{} is {}".format(subaru.model, subaru.insurance))
print("{} is {}".format(toyota.model, toyota.insurance))
```

## 方法

定义在类主体内的函数称为方法，它们是基本函数。方法定义了对象的行为。

### 示例

1. 启动 IDLE。
2. 导航到“文件”菜单并点击“新建窗口”。
3. 输入以下内容：

```python
class Car:
    category = "Personal Automobile"

    def __init__(self, model, insurance):
        self.model = model
        self.insurance = insurance

    def ignite(self, ignition):
        return "{} ignites {}".format(self.model, ignition)

    def stop(self):
        return "{} is now stopping".format(self.model)

subaru = Car("Subaru", "Insured")
print(subaru.ignite("Fast"))
print(subaru.stop())
```

### 重要提示

方法 `ignite()` 和 `stop()` 被称为实例方法，因为它们是所创建对象的实例。

### 练习

a. 创建一个 `Dog` 类并实例化它。
b. 创建一个 Python 程序，显示 a 中两条狗的名字及其两个属性。

# 使用 Python 进行机器学习中的继承

在不修改现有类的情况下，利用现有类的细节创建新类的方式称为继承。新形成的类称为派生类或子类，而现有类称为父类或基类。

### 示例

1. 启动 IDLE。
2. 导航到“文件”菜单并点击“新建窗口”。
3. 输入以下内容：

![继承图](Images/image00222.gif)

### 解释

在上述程序中，我们创建了两个 Python 类。这些类分别是作为基类的 `Dog` 和作为派生类的 `Pitbull`。派生类继承了基类的函数。`__init__()` 方法和 `super()` 函数用于将基类中 `__init__()` 方法的内容引入派生类。

# 使用 Python 进行机器学习中的封装

Python 面向对象编程方法中的封装旨在帮助防止数据被直接修改。Python 中的私有属性以下划线单下划线或双下划线作为前缀来表示。

### 示例

1. 启动 IDLE。
2. 导航到“文件”菜单并点击“新建窗口”。
3. 输入以下内容：

```python
class Tv:
    def __init__(self):
        self.__Finalprice = 800

    def offer(self):
        print("Offering Price: {}".format(self.__Finalprice))

    def set_final_price(self, offer):
        self.__Finalprice = offer

t = Tv()
t.offer()
t.__Finalprice = 950
t.offer()

# using setter function
t.set_final_price(990)
t.offer()
```

### 解释
