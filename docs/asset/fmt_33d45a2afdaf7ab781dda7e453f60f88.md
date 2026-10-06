
## HAS-SPOUSE

```
HAS-SPOUSE
DOMAIN HUMAN-1
RANGE HUMAN-2
INVERSE SPO-OF
SEMANTIC-EXPANSION
PRECONDITION MARRY-1, MODALITY-1 ; 他们结婚了且没有离婚
MARRY-1 ; 他们结婚了
AGENT HUMAN-1, HUMAN-2
MODALITY-1 ; 没有离婚
TYPE EPISTEMIC
VALUE 0
SCOPE DIVORCE-1
DIVORCE-1
AGENT HUMAN-1, HUMAN-2 ; 由这些人执行
TIME > MARRY-1.TIME ; 在结婚之后
```

`HAS-SPOUSE` 的 `SEMANTIC-EXPANSION` 包含了比 `MARRY` 脚本更多的信息——即这些个体随后没有离婚。

## 知识库 55

回顾一下：本体之所以包含 `HAS-SPOUSE` 关系，是因为人们根据亲属关系来思考和论述世界。`HAS-SPOUSE` 与 `MARRY` 之间的关系必须在本体中显式记录，以支持结婚（一种 `EVENT` 事件）和已婚（一种表示为 `RELATION` 关系）之间的双向推理。

### 复杂属性可以对重复事件泛化

运动员有教练，人们有牙医，孩子们有保姆。这些社会关系——`HAS-COACH`、`HAS-DENTIST`、`HAS-BABYSITTER`——意味着重复的事件，在某些情况下，还涉及建立关系的正式过程，例如填写表格成为牙医的患者。在旅行期间看牙医进行急诊治疗并不意味着那个人是`某人的牙医`。

此类属性与它们隐含的事件序列之间的相关性在本体中可以用两种方式表达。一方面，它可以作为条件语句附加到事件描述中。如果我们假设需要多于一次教练实例才能推断出 `HAS-COACH` 关系（实际数字在不同人看来可能不同），那么它看起来如下：

```
COACHING-EVENT-1
AGENT COACH-1
BENEFICIARY ATHLETE-1
SEMANTIC-EXPANSION
If; If
SET; there is more than one coaching event
MEMBER-TYPE
COACHING-EVENT-1
CARDINALITY >1
COACHING-EVENT-1; in which
AGENT COACH-1; a particular coach coaches
BENEFICIARY ATHLETE-1; a particular athlete
Then; Then
HAS-COACH-1; that athlete has that coach
DOMAIN ATHLETE-1
RANGE COACH-1
```

此信息也存储在 `HAS-COACH` 描述的 `SEMANTIC-EXPANSION` 字段中，其中还列出了建立关系的另一种方式：通过雇用教练。

## 56

### 第 3 章

```
HAS-COACH-1; A particular athlete has a particular coach
DOMAIN ATHLETE-1
RANGE COACH-1
INVERSE
COACH-OF
SEMANTIC-EXPANSION
If; If
Either; the coach has coached the athlete more than once
SET
MEMBER-TYPE
COACHING-EVENT-1
CARDINALITY >1
COACHING-EVENT-1
AGENT COACH-1
BENEFICIARY ATHLETE-1
Or; or
HIRE-COACH; the athlete hired the coach
AGENT ATHLETE-1
THEME COACH-1
Then; Then
HAS-COACH-1; the athlete has the coach
DOMAIN ATHLETE-1
RANGE COACH-1
```

对于一个不涉及社会关系的示例，我们可以查看马里兰虚拟患者临床培训系统（第 8.5 节），在那里，患者症状被建模为属性，其值在交互模拟过程中发生变化。例如，`DIFFICULTY-SWALLOWING` 以患者为 `DOMAIN`，抽象值 `{0,1}` 为其 `RANGE`。在模拟运行开始时，在患者经历任何症状之前，`DIFFICULTY-SWALLOWING` 的值为 0；但如果患者患有导致吞咽困难的疾病，随着疾病的进展，该属性的值就会增加。该属性捕捉了医生如何思考、论述和推理这种症状。简而言之，他们进行了泛化——他们并不是根据患者在一天内、一个月或一年内无数次吞咽来思考的。然而，为了让属性 `DIFFICULTY-SWALLOWING` 具有意义，必须在本体中参考隐含的大量 `SWALLOW` 事件来描述描述：

```
DIFFICULTY-SWALLOWING-1
DOMAIN HUMAN-1; a particular person has
RANGE {0,1}; a particular value for DIFFICULTY-SWALLOWING
SEMANTIC-EXPANSION
If; If
```

## 知识库 57

```
DIFFICULTY-ATTRIBUTE-1; difficulty-attribute applies
DOMAIN SET-1; to a set of swallow events
RANGE `var1`; and has a particular value
SET-1; and that set
MEMBER-TYPE
SWALLOW-1; of swallow events
QUANT.8; is large
SWALLOW-1
AGENT HUMAN-1; and is carried out by this person
Then; Then
DIFFICULTY-SWALLOWING-1; the value of difficulty-swallowing is the
DOMAIN HUMAN-1; range of difficulty-attribute-1—that is,
RANGE `var1`; how difficult the swallowing is
```

这句话的意思是：“如果特定个人对大量 `SWALLOW` 事件的 `DIFFICULTY-ATTRIBUTE` 值为 `[某个值]`，那么该人的 `DIFFICULTY-SWALLOWING` 值为 `[相同的值]`。”

### 复杂属性可以作为基于事件链的捷径

继续从医学领域提取示例，当临床医生思考、论述和教学 `DISEASES` 时，以下属性非常有用：`HAS-TYPICAL-SYMPTOM`、`HAS-DIAGNOSTIC-TEST`、`SUFFICIENT-GROUND-TO-SUSPECT`、`SUFFICIENT-GROUND-TO-DIAGNOSE`、`SUFFICIENT-GROUND-TO-TREAT` 以及 `PREFERRED-ACTION-WHEN-DIAGNOSED`。这些实际上包含在之前提到的马里兰虚拟患者系统中，它们是对实际发生情况的逻辑捷径。虽然 `HAS-TYPICAL-SYMPTOM` 将疾病与症状联系起来，但实际上疾病与症状并没有直接关联：经历 `DISEASE` 的 `PATIENTs` 也可能经历给定的 `SYMPTOM`（`DISEASES` 和 `SYMPTOMs` 都是 `EVENTs`）。这一解释记录在 `HAS-TYPICAL-SYMPTOM` 属性的 `SEMANTIC-EXPANSION` 区域：

```
HAS-TYPICAL-SYMPTOM
DOMAIN DISEASE-1
RANGE SYMPTOM-1
SEMANTIC-EXPANSION
If
ANIMAL-1
EXPERIENCER-OF-DISEASE-1
Then
ANIMAL-1
EXPERIENCER-OF-SYMPTOM-1
SYMPTOM-1
LIKELIHOOD.8
```

## 58

### 第 3 章

将症状概率记录为 .8（在抽象尺度 `{0,1}` 上）传达了“典型”的概念。对于每种特定疾病，每种症状都有基于人群的概率，如果代理学习了，它将被记录。

### 复杂属性可以对其他属性泛化

在考虑家庭时，人们会考虑祖父母、外祖父母、堂兄弟姐妹、姨等。然而，所有这些都可以原始属性 `HAS-OFFSPRING` 和 `HAS-SPOUSE` 来解释。`HAS-GREAT-CHILD` 属性说明了属性如何以及需要通过原始属性进行解释。

```
HAS-GREAT-CHILD
DOMAIN HUMAN
RANGE HUMAN
INVERSE
GREAT-CHILD-OF
SEMANTIC-EXPANSION
If HUMAN-1 (HAS-GREAT-CHILD HUMAN-4)
Then HUMAN-1 (HAS-OFFSPRING-2)
And HUMAN-2 (HAS-OFFSPRING-3)
And HUMAN-3 (HAS-OFFSPRING-4)
```

此外，由于 `HAS-OFFSPRING` 自身使用 `BEAR-OFFSPRING` 和 `MARRY` 事件进行语义扩展，代理在需要时具有推理这些事件的知识。

### 标量属性的抽象值可以计算

以不精确的方式思考和论述世界是自然的：*高个子*、*快速比赛*。抽象值允许我们表示相应的不精确含义：*高个子*——`HUMAN (HEIGHT .8)`、*快速*——`RACE (VELOCITY .8)`、*价格适中的午餐*——`MEAL (COST .5)`。然而，在某些情况下，不精确的描述需要具体化以满足推理需求。例如，如果我们要求机器人 `LEIA` 挖一个与大包装箱一样大的洞，它需要将该描述转换为实际的 `LENGTH`、`WIDTH` 和 `DEPTH`。为了代理进行此类计算，它必须知道所指对象的实际尺寸。

```
PACKING-BOX
LENGTH sem 6–24 (MEASURED-IN INCH)
WIDTH sem 6–24 (MEASURED-IN INCH)
HEIGHT sem 6–24 (MEASURED-IN INCH)
```

# 实际尺寸的计算

从相对值（始终被理解为近似值）出发计算是直观的：11

一个大箱子（抽象值为 `.8`）长、宽、高约为 20.4 英寸

一个小箱子（抽象值为 `.2`）长、宽、高约为 9.6 英寸

从抽象值计算实际值的函数被记录为附加到 `SIZE` 属性上的 `SEMANTIC-EXPANSION`，这正是此类泛化的来源。我们可以看到，这在一个完全不同的领域也效果得很好——人的身高。如果我们说人的典型身高范围是 4′10″ (58″) 到 6′4″ (76″)，那么一个高个子（比例尺上的 `.8`）大约是 6 英尺，而矮个子大约是 5′1″。

虽然通用公式很有用，但它们在所有情况下并不好用，例如当极高值或极低值显著偏离正常范围时。12 考虑汽车：一辆劳斯莱斯 Boat Tail 车型售价 2800 万美元，而最便宜的新款起亚售价低于 17,000 美元，你还可以花几百美元买一辆旧破车。13 本体允许使用面（facets）显式记录此类值：`sem` 用于正常值，`relaxable-to` 用于极端值，这可以通过围绕 `sem` 值范围进行定位来改进相对计算。但如果代理需要能够对此类值进行更精确的推理——类似于人类的方式——那么也可以将理解的值显式地列为给定属性的语义扩展。

### 复杂属性可以具有间接语义扩展

本节的一个反复出现的主题是，本体应该记录人们如何思考世界，这从他们讨论问题的方式可以清楚地看出。想象一位医生正在向学生讲解食管弛缓症并说：“食管弛缓症患者抱怨吞咽困难。”学生从中获得的是，食管弛缓症的一个典型症状是吞咽困难。在本体术语中，这是：

```
ACHALASIA
HAS-TYPICAL-SYTOM
DYSPHAGIA
```

但学生如何从实际说的话中提取意图含义呢？

* 他们知道语言结构“Patients with NP com-DISEASE complain of NP”意味着患者*报告*了症状，而不是他们在对症状进行 `SYMPTOM` 式抱怨。（构造表示中的下标指示了对组成部分含义的本体约束。）
* 他们知道如何对泛指进行推理：如果某种疾病的患者报告了某种症状，那么这种症状就是该疾病的典型。

问题是，如何最好准备代理来进行这种推理？最快且最可靠的方法是将属性值的典型思考和讨论方式作为正式表示，记录在 `PROPERTY` 的 `SEMANTIC-EXPANSION` 区域。表达 `HAS-TYPICAL-SYTOM` 的典型方式包括以下等。

* Patients with NP complain of NP (`DISEASE SYMPTOM`)
* NP suggests NP (`SYMPTOM DISEASE`)
* NP is suggestive of NP (`SYMPTOM DISEASE`)
* NP is key to diagnosing NP (`SYMPTOM DISEASE`)

`HAS-TYPICAL-SYTOM` 的 `SEMANTIC-EXPANSION` 区域列出了此类表述的正式含义表示，这些表示也记录在代理的词汇表中，以便代理将语言输入与本体知识联系起来。以第一个为例：

```
HAS-TYPICAL-SYTOM
SEMANTIC-EXPANSION
If; If;
DECLARATIVE-SPEECH-ACT-1
AGENT-PATIENT-1; patients say
THEME SYMPTOM-1; that there is a symptom
SYMPTOM-1 EXPERIENCER-PATIENT-1; that they are experiencing
PATIENT-1; and the same patients
CARDINALITY > 114; (表示复数)
EXPERIENCER-OF-DISEASE-1; have a par ticular disease
Then; Then
DISEASE-1; the disease
HAS-TYPICAL-SYTOM SYMPTOM-1; has this as a typical symptom
```

我们记录语义扩展是因为在将来，让 LEIA 从如此少量的疾病中学习是有意义的。

## 知识库

回到混合问题，可以使用数据驱动工具在将来聚类意义表示，然后让 LEIA 在将来聚类实体。

### 定性属性可以带有定量含义使用

例如，`NEAR` 是一个比较两个对象位置的关联。尽管它没有断言它们之间的任何特定距离，但隐含的距离取决于对象的大小。在接下来的示例中，隐含的距离最好分别用英寸、英尺、少量英里来衡量。

* (3.1) 铅笔在笔记本附近。
* (3.2) 汽车在停止牌附近。
* (3.3) 她的房子在高中附近。
* (3.4) 我的家乡离你的家乡近。

对于代理来说，理解此类计算很重要，原因与机器人 `LEIA` 类似。如果告诉机器人 `LEIA` 站在门附近，这意味着距离几英寸远还是几加码远？让机器人进行这种计算的方法是制定“邻近”的语义。以下是初步近似：对于所比较的每个 `OBJECTs`，取决于已知的 `LENGTH`、`WIDTH`、`DEPTH`、`HEIGHT` 的值。取它们的平均值。

```
NEAR <= 1.5 * average
```

这个计算是一个模型——一个简单的模型——它为上述示例中的三个产生了合理的结果：铅笔在笔记本附近小于 13.8 英寸；汽车在停止牌附近小于 13.8 英尺；家乡离另一个家乡近小于 17.5 英里。18 然而，对于房子在高中附近的例子，这个公式并不适用：

### 总结为什么属性如此重要——且绝非易事

LEIA 本体中属性机制的能力是建模像人类一样学习、推理和通信的代理的关键。它允许对复杂属性与习惯或反射动作之间的内在类比进行形式化。当一个动作变成习惯或反射性时，人们就不再思考它——除非关于这种情况触发了特殊的关注。因此，我们每天下班回家都走同一条路线，除非交通拥堵导致我们重新规划，并且我们会驾驶手动挡位汽车，直到有人要求我们教他们如何开车。同样，我们使用复杂的属性作为学习和推理的捷径，但在需要时也可以解释它们。例如，我们思考自己的祖母时，并不会去思考一系列出生和结婚事件，但如果被要求，我们可以根据这些事件来解释这种关系。由于认知建模涉及对人们似乎知道什么以及似乎如何推理的假设，因此有充分理由将人们关注的任何属性纳入本体论，并以某种方式解释它们，使智能体能够以人类相同的方式对它们进行推理。

### 3.2.2 本体论实例 (Ontological Instances)

本体论实例是本体论概念的可记忆的事件，用于在更大的本体论描述中进行引用（coreference）和具体化（reification）。（`Reification` 是用复杂结构填充属性的槽位。）例如，虽然说 `CARs` 具有 `TIRE` 作为其部分是正确的，但指明有四个会提供更多信息量。

```
CAR
HAS-OBJECT-AS-PART sem TIRE-1
TIRE-1
CARDINALITY value 4
```

**知识库 63**

本体论实例使用的另一个示例涉及典型的事件序列。例如，在某人问了一个一个是非问题后，另一个人通常会回答。这种问-答组合是相邻对（adjacency pair）的一个例子——该主题将在第 6 章进一步讨论。
