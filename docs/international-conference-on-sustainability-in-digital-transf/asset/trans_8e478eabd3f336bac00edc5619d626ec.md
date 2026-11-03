
作物在此期间得到照料，其生长情况通过浇水、施肥和使用生物农药等措施进行监测。

## D. 收获、播种、储存和分销

本步骤进行土壤准备和种子种植，并遵循一套指导原则。

收获是指从农场系统性地收集农业产出，随后进行必要的步骤以确保其妥善储存和后续分销。下一步是储存和分销，其中收获并加工的产品被包装、储存，然后通过各种分销渠道提供给公众和企业。

## E. 病虫害信息与防治

在本步骤中，使用了一个数据集，该数据集旨在帮助学术界和行业专业人士改进用于害虫识别和管理的机器学习算法。也对希望扩展其对印度独特害虫及其防治方法的了解的农业从业者和害虫控制专家有所帮助。

## F. 本体设计

任何领域的知识都可以通过本体来捕获。类及其关系使用 `OWL` 本体进行映射。在此基础上，利用已识别的类、子类和连接构建农业领域的本体。在本研究中，`Protégé` 中的数据集 [[16](#ch33.xhtml#ref33_16)] 被用于使用 `OWL` 描述逻辑语言（`OWL DL`）建立基于知识的存储库。类‘`Thing`’被选为起点，然后通过添加代表作物类型、生产方法、土壤类型等事物的进一步类来构建类层次结构。

所创建的知识库存储库被称为本体知识库（`OKB`），它由属性、对象属性、实例属性和公理组成。最后，用户或农民可以轻松访问该本体系统获取农业信息。

## 结果与实现

下文中的[图 33.2](#ch33.xhtml#fig33_2)显示了与名为‘`Agricultural_knowledge_base`’的设计本体相关的实体。

![图 33.2 设计本体的实体结构](images/fig33_2_C.jpg)

[图 33.2 设计本体的实体结构](#ch33.xhtml#R_fig33_2)

[图 33.3](#ch33.xhtml#fig33_3)显示了设计本体的类和子类。在此，`Agricultural_knowledge_base`是超类，由多个子类组成，分别是`pesticides`、`soil`、`pests`和`crops`。

![图 33.3 使用 PROTÉGÉ 4.3.1 设计的本体的全视图](images/fig33_3_C.jpg)

[图 33.3 使用 PROTÉGÉ 4.3.1 设计的本体的全视图](#ch33.xhtml#R_fig33_3)

[图 33.4](#ch33.xhtml#fig33_4)通过对象属性层次结构显示了设计农业本体的属性分布。与子类关联的属性是对称的、传递的、功能的和逆功能的。

![图 33.4 作为子类的土壤的对象属性层次结构](images/fig33_4_C.jpg)

[图 33.4 作为子类的土壤的对象属性层次结构](#ch33.xhtml#R_fig33_4)

[图 33.5](#ch33.xhtml#fig33_5)显示了注释属性，使得土壤类由属性园艺和农学进行注释。同样，标签由设计本体时使用的类和子类进行注释。`VersionInfo`是工具`PROTÉGÉ`的注释属性，为4.3.1。

![图 33.5 设计本体的注释属性层次结构](images/fig33_5_C.jpg)

[图 33.5 设计本体的注释属性层次结构](#ch33.xhtml#R_fig33_5)

前景模型提供了由构建本体给出的类的具体描述。在农业知识库本体中，我们将农业知识库指定为根类`Thing`的子类，其深度或级别为1。同样，子类`pesticides`及其实例的深度/复杂性为2级。`soil`的子类及其实例的深度为第三维度或更深。本体中的叶类最大深度或级别为5。这由[图 33.6](#ch33.xhtml#fig33_6)显示。以及[图 33.7](#ch33.xhtml#fig33_7)指标分布已显示。

![图 33.6 完整本体的强调模型](images/fig33_6_C.jpg)

[图 33.6 完整本体的强调模型](#ch33.xhtml#R_fig33_6)

![图 33.7 指标分布](images/fig33_7_C.jpg)

[图 33.7 指标分布](#ch33.xhtml#R_fig33_7)

## 结果与分析

[表 33.1](#ch33.xhtml#tab33_1)给出了在设计农业知识库中构建不相交类的描述。在当前本体中，包含了多个类，例如`soil`、`pests`、`crops`等。这些类的实例现在是互斥的，意味着两个类不可能共享一个实例。`owl:AllDisjointClasses`用于实现这一点。作为示例，子类被定义为不相交，确保`soil`的实例不能同时是`Pests`子类的实例。以下语法允许在`OWL DL`中表示这一点：

[表 33.1 不相交类。](#ch33.xhtml#R_tab33_1)

| 类 || 子类 || 不相交状态 |
| --- | --- | --- |
| `Pesticides` || `diazinon` || 与 `soil` 和 `pests` 不相交 |
| --- | --- | --- |
| `Pesticides` || `Carbaryl` || 与 `soil` 和 `pests` 不相交 |
| `Pesticides` || `chlorpyrifos` || 与 `soil` 和 `pests` 不相交 |
| `Pesticides` || `Permethrin` || 与 `soil` 和 `pests` 不相交 |
| `Pesticides` || `Malathion` || 与 `soil` 和 `pests` 不相交 |
| `Pesticides` || `acephate` || 与 `soil` 和 `pests` 不相交 |
| `Soil` || `Alluvial` || 与 `pesticides` 和 `pests` 不相交 |
| `Soil` || `Laterite` || 与 `pesticides` 和 `pests` 不相交 |
| `Soil` || `Black` || 与 `pesticides` 和 `pests` 不相交 |
| `Soil` || `Red` || 与 `pesticides` 和 `pests` 不相交 |
| `Pests` || `Spiniferus` || 与 `soil` 和 `pesticides` 不相交 |
| `Pests` || `lucorum` || 与 `soil` 和 `pesticides` 不相交 |
| `Pests` || `rubens` || 与 `soil` 和 `pesticides` 不相交 |
| `Pests` || `Jute_semilooper` || 与 `soil` 和 `pesticides` 不相交 |

Syntax

```
DisjointClasses (pesticides, soil, pests, crops): pesticides ∩ soil ∩ pests ∩ crops = { }
DisjoingInstances (diazinon, alluvial, jute semilooper, sowing): diazinon h alluvial h jute semilooper h sowing = { }
```

[表 33.2](#ch33.xhtml#tab33_2)列出了设计本体的指标如下：

[表 33.2 本体指标计数。](#ch33.xhtml#R_tab33_2)

| 参数 || 计数 |
| --- | --- |
| `Superclass` || 1 |
| --- | --- |
| `Classes` || 4 |
| `Sub-classes` || 21 |
| `Instances` || 2 |
| `Object property` || 4 |

## 结论与未来工作

本研究使用 Kaggle 数据集汇编了有关印度农业行业各个阶段的信息。通过问题范围识别以及本体集成到类、子类和关系中，我们分析了农民的信息需求。`OWL DL`本体设计语言用于创建农业知识库本体。它还详细说明了构建本体的整个过程，包括单个对象、注释和互斥类，所有这些对于从系统中有效提取数据都是必要的。

## 参考文献

1. [Abrahão, E., and Hirakawa, A. R.](#ch33.xhtml#R_ref33_1) (2017). 任务本体建模用于农业作业领域的技术知识表示。在第二次信息系统工程国际会议（ICISE），美国查尔斯顿，南卡罗来纳州，（第 12-16 页），doi: [10.1109/ICISE.2017.18.](http://dx.doi.org/10.1109/ICISE.2017.18)

