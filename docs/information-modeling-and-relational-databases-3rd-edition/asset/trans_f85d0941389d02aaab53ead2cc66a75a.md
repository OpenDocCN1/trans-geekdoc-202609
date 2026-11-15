

![](img/1344db3eba3d550e6edb009556fcd95c_442_0.png)

### FIG. 10.16 可选角色在 (a, c) ORM 和 (b, d) UML 之间的子集约束。

As an example, suppose the fact type Employee first visited Country is used to record the event when people first visit various countries, and suppose we always know the date when such visits started but only optionally know when they ended. For example, this could record details about your first visit to Belgium, your first visit to Japan, and so on. Fig. 10.17 shows one way to model this in ORM and UML, objectifying the m:n visit association and attaching fact types for the start date (mandatory) and end date (optional).

举个例子，假设事实类型“员工首次访问国家”用于记录人们首次访问各国的事件，并且我们总是知道此类访问开始的日期，但只可选地知道它们结束的日期。例如，这可以记录你首次访问比利时、首次访问日本等详细信息。图 10.17 展示了一种在 ORM 和 UML 中建模此情况的方法，将 m:n 访问关联对象化，并附加开始日期（强制）和结束日期（可选）的事实类型。

![](img/1344db3eba3d550e6edb009556fcd95c_442_1.png)

### FIG. 10.17 在 (a) ORM 和 (b) UML 中为时期事件记录一个开放期间。

Alternatively, these two temporal fact types could be replaced by a single fact type linking to Period as a compositely identified object type or class. Yet another alternative is to replace the FirstCountryVisit objectified association by a coreferenced entity type or class, as in Fig. 10.18. This alternative approach is suitable for industrial versions of ER that do not support objectification.

或者，可以将这两个时间事实类型替换为一个单一事实类型，将其链接到作为复合标识对象类型或类的 Period。另一种替代方案是将 FirstCountryVisit 对象化关联替换为共引用实体类型或类，如图 10.18 所示。这种替代方法适用于不支持对象化的 ER 的工业版本。

![](img/1344db3eba3d550e6edb009556fcd95c_443_0.png)

Now suppose the fact type Employee lived first in Country is used to record where people lived first (e.g., Einstein lived first in Germany). This fact type is n:1 rather than m:n. In ORM and UML, such associations may be objectified, and we may attach the temporal information as previously (see Fig. 10.19(a) and (b)).

现在假设事实类型“员工最初居住于国家”用于记录人们最初居住的地方（例如，爱因斯坦最初居住在德国）。这个事实类型是 n:1 而非 m:n。在 ORM 和 UML 中，此类关联可以对象化，并且我们可以像以前一样附加时间信息（参见图 10.19(a) 和 (b)）。

ORM currently allows objectification of any fact type. This is fine for a unary fact type, as it has a spanning uniqueness constraint (asserted or implied). However, objectification of a binary or longer fact type without spanning uniqueness constraint is best avoided. For example, it might result in fact types that are not atomic, and lead to awkwardness or confusion (Halpin, 2020). Moreover, remodeling to avoid such objections typically results in a better schema. For example, Fig. 10.19(c) is arguably simpler than Fig. 10.19(a). This schema is also easier to emulate in modeling approaches such as Barker ER that do not allow such objectification, as shown in Fig. 10.19(d).

ORM 目前允许对任何事实类型进行对象化。对于一元事实类型，这是可以接受的，因为它具有跨度唯一性约束（声明或隐含）。但是，最好避免对没有跨度唯一性约束的二元或更长事实类型进行对象化。例如，这可能会导致非原子的事实类型，并引起尴尬或混淆（Halpin, 2020）。此外，为了避免此类反对意见而进行的重新建模通常会产生更好的模式。例如，图 10.19(c) 可以说比图 10.19(a) 更简单。这个模式在 Barker ER 等建模方法中也更容易模拟，这些方法不允许此类对象化，如图 10.19(d) 所示。

![](img/1344db3eba3d550e6edb009556fcd95c_443_1.png)

Now, let's discuss how to record *snapshots of states that can change over time*. Consider a medical clinic where patients are identified by patient numbers, have their birthdate recorded, and optionally have their weight, temperature, and allergies (if any) recorded. Fig. 10.20 models this domain in ORM, UML, and Barker ER.

现在，让我们讨论如何记录*随时间变化的状态的快照*。考虑一家医疗诊所，患者通过患者编号标识，记录其出生日期，并可选地记录其体重、体温和过敏症（如果有）。图 10.20 在 ORM、UML 和 Barker ER 中对该领域进行了建模。

![](img/1344db3eba3d550e6edb009556fcd95c_444_0.png)

### FIG. 10.20 (a) ORM、(b) UML 和 (c) Barker ER 中的简单患者模式。

The ORM and UML schemas include a derived fact type to compute a patient’s age. A textual derivation rule may be added to compute age from birthdate and current date (in ORM, the latter is obtained from the implicit, predefined fact type Date is today).

ORM 和 UML 模式包含一个派生事实类型，用于计算患者的年龄。可以添加一个文本派生规则，根据出生日期和当前日期计算年龄（在 ORM 中，后者是从隐式预定义事实类型 Date is today 中获得的）。

The fact type Patient was born on Date is a once-only fact type, and hence is *unchangeable* (ignoring the possibility of error correction). Each of the other fact types is *individually changeable* (its individual instances may change over time). The fact type Patient has Weight is *functional* for Patient (at any time, a patient has at most one weight) and is repeatable (patients may gain or lose weight, and later return to their previous weight).

事实类型“Patient was born on Date”是一次性事实类型，因此是*不可更改的*（忽略错误更正的可能性）。其他每个事实类型都是*单独可更改的*（其各个实例可能随时间而改变）。事实类型“Patient has Weight”对于 Patient 是*功能性的*（在任何时候，一个患者最多有一个体重）并且是可重复的（患者可能增加或减轻体重，后来恢复到之前的体重）。

In physics, kg (kilogram) is a unit of mass and weight is a force. In common speech, however, “weight” is typically used to mean mass, and we use it here in that sense, using kg instead of kg wt for the unit.

在物理学中，kg（千克）是质量单位，而重量是力。然而，在日常用语中，“weight”通常用来表示质量，我们在这里也是按此含义使用，使用 kg 而不是 kg wt 作为单位。

The temperature fact type is also functional and repeatable. The allergy fact type is *m:n* (many-to-many) and repeatable (patients may cease to be allergic to a given drug, but later become allergic to it again). The derived age fact type is functional and changeable even though it is not repeatable.

温度事实类型也是功能性和可重复的。过敏事实类型是*m:n*（多对多）并且可重复（患者可能停止对某种药物过敏，但后来又可能对其过敏）。派生年龄事实类型是功能性和可更改的，尽管它不可重复。

Being functional, the age and weight fact types are changeable only at the instance level—an old instance can change only by being replaced by a new instance. The nonfunctional allergy fact type is also *collectively changeable* (its population of instances may change over time by adding new instances or deleting old ones).

由于具有功能性，年龄和体重事实类型仅在实例级别可更改——旧实例只能通过被新实例替换来更改。非功能性的过敏事实类型也是*集体可更改的*（其实例群体可以通过添加新实例或删除旧实例而随时间而改变）。

The individual changeability of the age, weight, temperature, and allergy fact types follows from their *time-deictic* nature. Deixis (Greek for indicating, or point of reference) is the process whereby the referent of a linguistic structure depends on its communication (utterance or inscription) context and may be classified into five basic categories: time, place, person, discourse, and social. For example, the sentence “You are now reading this book” is person deictic (“you”), time deictic (“are”, “now”), and discourse deictic (“this book”).

年龄、体重、体温和过敏事实类型的单独可更改性源于其*时间指示*性质。Deixis（希腊语，意为指示或参考点）是语言结构的指称对象取决于其交流（口语或书面）语境的过程，可以分为五个基本类别：时间、地点、人物、话语和社会。例如，句子“你现在正在阅读这本书”是人物指示（“you”）、时间指示（“are”、“now”）和话语指示（“this book”）。

In time (or temporal) deixis, the meaning of a communication act depends on the time in which it was performed. Temporal deictic references may appear via temporal adverbs (e.g., “now”, “currently”, “today”, “tomorrow”, “yesterday”), tense (e.g., “is eating”, “was eating”, “will eat”), combinations of deictic modifiers and time units (e.g., “last year”, “this week”, “next month”), or other temporal phrases (e.g., “two days ago”, “within a month”). In information modeling, time-deictic aspects of predicates are usually restricted to tense and temporal adverbs.

在时间（或时间性）指示中，交流行为的意义取决于其发生的时间。时间指示性引用可以通过时间副词（例如，“now”、“currently”、“today”、“tomorrow”、“yesterday”）、时态（例如，“is eating”、“was eating”、“will eat”）、指示修饰语和时间单位的组合（例如，“last year”、“this week”、“next month”）或其他时间短语（例如，“two days ago”、“within a month”）出现。在信息建模中，谓词的时间指示性方面通常局限于时态和时间副词。

In Fig. 10.20(a), the birthdate predicate is in past tense (was born on) while the other four predicates are in present tense (has, has, has, is allergic to). Because one cannot change the past, instances of the birthdate fact type are unchangeable. If we wish our information model to remember instances of birthdate facts, these facts also cannot be deleted. In contrast, instances of the four present tense fact types are changeable and may be replaced by other instances. Consider the following fact instance:

- Patient 101 has Weight 80kg

在图 10.20(a) 中，出生日期谓词是过去时（was born on），而其他四个谓词是现在时（has, has, has, is allergic to）。因为无法改变过去，出生日期事实类型的实例是不可更改的。如果我们希望信息模型记住出生日期事实的实例，这些事实也不能删除。相比之下，四个现在时事实类型的实例是可更改的，并可以被其他实例替换。考虑以下事实实例：

- Patient 101 has Weight 80kg

This is shorthand for “Patient 101 currently has Weight 80kg”, which itself is shorthand for “Patient 101 has Weight 80kg at time t, where t is the time at which the sentence was communicated”. Originally, t is a valid time (e.g., the time at which the patient’s weight was actually measured). Typically, the fact is then entered into the information model at some later transaction time and remains there until it either is updated by a more recent measurement or is deleted. From the viewpoint of the information model, the fact really means “When last inspected, Patient 101 had Weight 80kg”. For such reasons, the fact is known as a snapshot fact.

这是“Patient 101 currently has Weight 80kg”的简称，而它本身是“Patient 101 has Weight 80kg at time t, where t is the time at which the sentence was communicated”的简称。最初，t 是有效时间（例如，患者体重实际测量的时间）。通常，该事实随后在某个较晚的事务时间被输入到信息模型中，并保留在那里，直到它被较新的测量更新或被删除。从信息模型的角度来看，该事实的真正含义是“上次检查时，Patient 101 的体重为 80kg”。出于此类原因，该事实被称为快照事实。

In practice, if the delay between valid and transaction times is minor, and the property (e.g., weight, allergy) is reevaluated on a suitably regular basis (which may be very infrequent if the property changes only slowly over time), then business users are willing to treat snapshot facts as if they were current.

在实践中，如果有效时间和事务时间之间的延迟较小，并且属性（例如，体重、过敏）以适当的定期频率重新评估（如果属性随时间缓慢变化，频率可能非常低），那么业务用户愿意将快照事实视为当前事实。

Now, let’s discuss how to record the history of functional, changeable fact types. If a fact type is individually changeable, and we need to maintain a history (full or partial) of its instances, then we should add or adapt a fact type to achieve this, using a temporal object type of the desired temporal granularity.

现在，让我们讨论如何记录功能性、可更改事实类型的历史。如果一个事实类型是单独可更改的，并且我们需要维护其实例的历史（完整或部分），那么我们应该添加或调整一个事实类型以实现此目的，使用所需的时间粒度的时间对象类型。

In ORM and UML, one simple way to do this is to insert into a “key” of the original, snapshot fact type a role that is played by the temporal object type, rephrasing the predicate as appropriate. A key of a fact type is a set of its roles that is exactly spanned by a uniqueness constraint. For example, in Fig. 10.20(a) the key of the weight fact type is the role played there by Patient.

在 ORM 和 UML 中，实现这一点的一种简单方法是将时间对象类型扮演的角色插入到原始快照事实类型的“键”中，并根据需要重新措辞谓词。事实类型的键是由唯一性约束恰好跨越的其角色集合。例如，在图 10.20(a) 中，体重事实类型的键是 Patient 在那里扮演的角色。

Suppose we wish to maintain a history of patient weights where for each patient, at most one weight measurement is performed per day. Because our temporal granularity is 1 day, we choose Date as the object type and insert its relevant role into the binary fact type to produce the ternary fact type Patient on Date had Weight and expand the key uniqueness constraint to cover this role, as shown in Fig. 10.21(a).

假设我们希望维护患者体重的历史记录，其中每个患者每天最多进行一次体重测量。由于我们的时间粒度为 1 天，我们选择 Date 作为对象类型并将其相关角色插入到二元事实类型中，以产生三元事实类型“Patient on Date had Weight”并扩展键唯一性约束以涵盖该角色，如图 10.21(a) 所示。

![](img/1344db3eba3d550e6edb009556fcd95c_446_0.png)

### FIG. 10.21 在 ORM 中维护患者体重历史的不同选项。

The uniqueness constraint verbalizes as **For each Patient and Date, that Patient on that Date had at most one Weight**. If now or later you may wish to add details about the weight measurement (e.g., who performed the measurement), it is better to introduce a WeightMeasurement type either by objectification (Fig. 10.21(b)) or by coreferencing (Fig. 10.21(c)).

唯一性约束表述为**对于每个 Patient 和 Date，该 Patient 在该 Date 上最多有一个 Weight**。如果现在或将来您希望添加关于体重测量的详细信息（例如，谁执行了测量），最好通过对象化（图 10.21(b)）或共引用（图 10.21(c)）引入 WeightMeasurement 类型。

For easy reference, you could also introduce a measurement number to provide a simple identifier, as in Fig. 10.21(d), which includes an external uniqueness constraint to ensure that the patient and date combination provides a secondary identifier. If you wish to change the rules to allow the same patient to have more than one weight measurement on the same date, the external uniqueness constraint should be removed from Fig. 10.21(d).

为了方便参考，您还可以引入测量编号以提供一个简单标识符，如图 10.21(d) 所示，其中包含一个外部唯一性约束，以确保患者和日期的组合提供次要标识符。如果您希望更改规则以允许同一患者在同一天有多个体重测量，则应从图 10.21(d) 中删除外部唯一性约束。

In UML and Barker ER, it would be unusual to include Date as a class or entity type, so a WeightMeasurement type would normally be used. If no weight measurement number is introduced to identify weight measurements, the schemas shown in Fig. 10.22(a) and (b) may be used.

在 UML 和 Barker ER 中，将 Date 作为类或实体类型包括在内是不寻常的，因此通常会使用 WeightMeasurement 类型。如果未引入体重测量编号来识别体重测量，则可以使用图 10.22(a) 和 (b) 中所示的模式。

In Fig. 10.22(b), the combination of the two {id} markers on the dateTaken attribute and the association end connected to the Patient class indicate a composite identification scheme for WeightMeasurement, corresponding to the external uniqueness constraint in Fig. 10.21(c).

在图 10.22(b) 中，dateTaken 属性上的两个 {id} 标记与连接到 Patient 类的关联端的组合指示了 WeightMeasurement 的复合标识方案，对应于图 10.21(c) 中的外部唯一性约束。

