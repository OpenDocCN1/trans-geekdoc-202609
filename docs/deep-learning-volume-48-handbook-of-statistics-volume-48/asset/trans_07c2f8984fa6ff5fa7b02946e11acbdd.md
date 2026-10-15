
将实际智能纳入机器并使其像人类一样思考和表现是不可能的。在本章中，我们介绍了一种新型机器——EDLM（精确深度学习机）。这种 EDLM 可以以概率 1 达到目标，可能是对 20 世纪中叶由艾伦·图灵等人设计的原始人工智能模型的最佳替代，这些模型至今尚未与现实接触。在当前语境下，实现目标被定义为准确检测给定的对象。

### 关键词

人工智能；概率 1；对象检测

### MSC

68T07；68T05

## 1: Introduction

不可能训练人工智能的计算机来像人类一样思考和表现。计算机的训练涉及让机器读取数据并理解基于规则的逻辑指令。机器可以被设计成能够从机器被提供的有限规则组合中构建进一步的规则。这种设计涉及编程能够指示机器构建新性能规则的算法。无论机器是否能在没有已提供规则列表的具体指令的情况下自行提出新规则，仍然是一个疑问。因为目前的所谓高级机器尚未展示出无需以某种形式的机器训练算法指示的自我思考能力。迄今为止，人类智能还没有证据表明可以将或植入类似人类的智能到计算机中。

在统计机器学习方面取得了进展（[Angelino et al., 2017](#Ch001_1-8_S0169716122000554.xhtml#bb0010); [Fokoué and Titterington, 2003](#Ch001_1-8_S0169716122000554.xhtml#bb0060); [Matsui, 2010](#Ch001_1-8_S0169716122000554.xhtml#bb0075); [Tadaki, 2012](#Ch001_1-8_S0169716122000554.xhtml#bb0125); [Tollenaar and van der Heijden, 2013](#Ch001_1-8_S0169716122000554.xhtml#bb0135)），在机器学习中数学结构 well‑defined（[Blum et al., 1989](#Ch001_1-8_S0169716122000554.xhtml#bb0025); [Cucker and Smale, 2002](#Ch001_1-8_S0169716122000554.xhtml#bb0050); [Govindaraju and Rao, 2013](#Ch001_1-8_S0169716122000554.xhtml#bb0065); [Niyogi et al., 2011](#Ch001_1-8_S0169716122000554.xhtml#bb0090); [Smale and Zhou, 2007](#Ch001_1-8_S0169716122000554.xhtml#bb0100); [Van Messem, 2020](#Ch001_1-8_S0169716122000554.xhtml#bb0140)），在数据科学方面取得了进展（[Baladram et al., 2020](#Ch001_1-8_S0169716122000554.xhtml#bb0020); [Brunton and Kutz, 2022](#Ch001_1-8_S0169716122000554.xhtml#bb0030); [Chen, 2015](#Ch001_1-8_S0169716122000554.xhtml#bb0040); [Nazarathy and Klok, 2021](#Ch001_1-8_S0169716122000554.xhtml#bb0085); [Yeturu, 2020](#Ch001_1-8_S0169716122000554.xhtml#bb0145)），以及在机器学习中对数据结构的理解不断深化（[Calma et al., 2018](#Ch001_1-8_S0169716122000554.xhtml#bb0035); [Ferraz et al., 2021](#Ch001_1-8_S0169716122000554.xhtml#bb0055); [Poggio and Smale, 2003](#Ch001_1-8_S0169716122000554.xhtml#bb0095); [Srinivasa Rao and Diamond, 2020](#Ch001_1-8_S0169716122000554.xhtml#bb0110); [Srinivasa Rao and Vazquez, 2020](#Ch001_1-8_S0169716122000554.xhtml#bb0115), [2022](#Ch001_1-8_S0169716122000554.xhtml#bb0120)）。本文引入的精确深度学习（exact deep learning）用于训练机器，可能是目前最接近人工智能（AI）模型的替代方案。到目前为止，研究人员尚未成功实现艾伦·图灵等人原本设想的自主思考机器（[COE, n.d](#Ch001_1-8_S0169716122000554.xhtml#bb0045).）。

具有所有可能不同对象信息的深度学习机器对于成功的机器学习至关重要。只有对完整主题的部分信息，或对部分不同主题的完整信息都不足以保证准确的机器学习，也无法使机器实现给定的目标。本章中，我们展示了一种名为 EDLM（精确深度学习机）的新型机器，它能够以概率 1 的方式实现机器所接收的目标。我们在此提供一个案例场景，并说明在给定假设和限制下，EDLM 可以扩展到许多其他情况。EDLM 的核心思想将在下一节的定理中解释。

## 2: EDLM constructions

Theorem 1: EDLM theorem

Suppose an object can be described within a finite number of distinct attributes and these attributes are not dynamic over time. Then, machines trained with attribute information can detect the object with probability one.

Proof

Let *O* be the object that is to be detected accurately by a machine. Suppose *O* is uniquely described by exactly *a*‑attributes, say, *y*[1], *y*[2], … *y*[*a*]![si2_e](images/S0169716122000554/si2_e.png) which are distinct. It is given that the attributes to describe *O* do not change with time or these attributes are not dynamic over time. Here attributes can be treated as the description of an object that is enough to define that particular object. That means *a*‑attributes are enough to describe the object *O*. Suppose the machine is trained with a triplet of information, say, {*O*, *A*(*y*), *Y* (*c*)}, where *O* is the object to be detected by the machine, *A*(*y*) is the set of attributes that completely describe *O*, and *Y* (*c*) is the set of values that each attribute can pick. The object *O* is described based on the set of predecided finite numerical values. The set *A*(*y*) = {*y*[1], *y*[2], … *y*[*a*]}![si3_e](images/S0169716122000554/si3_e.png). The set *Y* (*c*) consists of all possible values of each of the attribute *y*[*j*] for *j* = 1, 2, … , *a*![si4_e](images/S0169716122000554/si4_e.png). The attribute *y*[*j*] can choose any one of the *c*[*c*[*j*]*j*]![si5_e](images/S0169716122000554/si5_e.png) possibilities for *j* = 1, 2, …, *a*![si6_e](images/S0169716122000554/si6_e.png). That is,

``` 
$\\begin{matrix} {Y(c) = \\begin{Bmatrix} {y\\_{1} = \\lbrack c\\_{11},c\\_{21},\\ldots,c\\_{c\\_{1}1}\\rbrack} \\\\ {y\\_{2} = \\lbrack c\\_{12},c\\_{22},\\ldots,c\\_{c\\_{2}2}\\rbrack} \\\\ \\vdots \\\\ {y\\_{a} = \\lbrack c\\_{1a},c\\_{2a},\\ldots,c\\_{c\\_{a}a}\\rbrack} \\\\ \\end{Bmatrix}} \\\\ \\end{matrix}
``` 
```

![si7_e](images/S0169716122000554/si7_e.png)  (1)

In Eq. ([1](#Ch001_1-8_S0169716122000554.xhtml#fo0010)) the quantities *c*[*c*[*j*]*j*]![si5_e](images/S0169716122000554/si5_e.png) for *j* = 1, 2, …, *a*![si6_e](images/S0169716122000554/si6_e.png) need not be identical. This implies that the number of possible values for *y*[1], *y*[2,]… *y*[*a*]![si10_e](images/S0169716122000554/si10_e.png) need not be the same. The object *O* will be described by {*O*, *A*(*y*), *Y* (*c*)} with each *y*[*j*] choosing only one of the values \[*c*[1*j*], *c*[2*j*], …, *c*[*c*[*j*]*j*]\]![si11_e](images/S0169716122000554/si11_e.png) for *j* = 1, 2, …, *a*![si6_e](images/S0169716122000554/si6_e.png). Suppose “0” indicates the absence of *c*[*c*[*j*]*j*]![si5_e](images/S0169716122000554/si5_e.png) and “1” indicates the presence *c*[*c*[*j*]*j*]![si5_e](images/S0169716122000554/si5_e.png) in *y*[*j*]. All the attributes of *Y* (*c*) can be listed for the absence or presence of values of each attribute as follows:

``` 
$\\begin{aligned} {y\\_{1} =} & {\\lbrack c\\_{11}(0,1),c\\_{21}(0,1),\\ldots,c\\_{c\\_{1}1}(0,1)\\rbrack} \\\\ {y\\_{2} =} & {\\lbrack c\\_{12}(0,1),c\\_{22}(0,1),\\ldots,c\\_{c\\_{2}2}(0,1)\\rbrack} \\\\ & \\vdots \\\\ {y\\_{a} =} & {\\lbrack c\\_{1a}(0,1),c\\_{2a}(0,1),\\ldots,c\\_{c\\_{a}a}(0,1)\\rbrack} \\\\ \\end{aligned}
``` 
```

![si15_e](images/S0169716122000554/si15_e.png)  (2)
