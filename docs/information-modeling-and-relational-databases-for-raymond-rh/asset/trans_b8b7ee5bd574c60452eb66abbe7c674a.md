
*Sequences*（有序包），如奖项列表，可在 ORM 中使用键中的位置类型建模（例如：Lottery awarded prize of Rank to Person），在 UML 中使用 `{ordered, nonunique}` 设置建模。*Arrays*（索引序列）的建模方式类似。

*Nominalization*（名词化）将动词重构为名词短语。在信息建模中，关系的对象化通常是*情境名词化*，即生成的对象是一种事态（如事件或活动），它与被对象化的关系一一对应，但不等同于该关系。例如：Person sings Song；**that** Singing is delightful。

在对象化情况下，ORM 会在底层创建*链接事实类型*（例如：Singing is by Person，Singing is of Song）。在极少数情况下，对象化是*命题名词化*，即讨论的对象是一个命题；这是 UML 中定义关联类的方式。在信息建模中，命题名词化通常可用情境名词化替代。

ORM 2 允许一元事实类型（例如：President died）被对象化（例如：Death），并包含对象化指南以帮助决定何时对象化（例如：除非 *n*:1 关联可能演变为 *m:n* 关联，或对象化类型有多个直接关联的事实类型，否则不要对象化 *n*:1 关联）。带有跨越唯一性约束的事实类型也可被对象化（例如：Person speaks Language，且 Person visited Country in Year）。ORM 2 还允许对象化恰好有一个跨越 *n*−1 个角色的唯一性约束的事实类型（*n* ≥ 1），但此类情况最好用其他方式建模。

CWA 假定所有相关事实均已知（在模型中作为断言事实或派生事实出现），并蕴含*失败即为假*（找不到或无法证明某命题即意味着它为假）。OWA 允许某些相关事实未知，并蕴含*经典否定*（找不到或无法证明某命题即意味着其真值未知）。

SWA 允许某些相关事实作为派生事实未知，但作为断言事实则已知，并蕴含*半正否定*（断言事实类型的缺失实例为假，但无法派生出某事实实例或其否定即意味着其真值未知）。OWN 允许某些相关事实未知，但也允许断言否定；作为 OWA 的特例，它蕴含经典否定。

目前正在考虑为 ORM 2 的一元事实类型提供图形符号以区分不同的封闭/开放世界风味（例如：虚线表示开放）。即使没有这些符号，也可通过引入否定谓词的一元类型或转换为二元类型来建模不同方法。实践中，CWA 和 OWN 是最有用的方法，分别可在 UML 和关系模式中用强制性布尔属性和可选布尔属性来体现。

*First-order logic*（一阶逻辑）仅对个体量化，不对谓词量化。高阶逻辑对个体和谓词均量化。*Higher-order type*（高阶类型）包含本身即为类型的实例。*Categorization type*（分类类型，如 Gender）用于将另一类型（如 Person）分类为子类型。UML 允许称为“powertypes”（幂类型）的高阶类型用作分类类型。

例如，在 UML 中，子类型 Oak 可被视为等同于幂类型 TreeSpecies 的一个实例，后者用于对类型 Tree 进行分类。高阶类型有时也用于直接建模元结构，并允许跨层级/元层级的规则。

高阶逻辑的高效实现比一阶逻辑复杂得多。实践中，通常在信息建模中避免使用高阶构造（且我们建议如此）。例如，分类类型的实例可视为个体，信息性事实类型可用于分类，不同层级可在不同模型中处理。然而，若在信息建模中使用高阶逻辑，我们建议使用受限 Henkin 语义。

从子类型指向超类型的箭头显示了一种类型层级关系，它蕴含连接子类型和超类型实例的实例层级同一性关系。*Inclusive-or constraints*（包含或约束）、*exclusion constraints*（排斥约束）和*subset subsets*（子集子集）可应用于*实例层级链接事实类型*的*超类型角色*。

通常，包含或约束应用于由同一对象类型承载的两个或多个角色。然而，*包含或约束也可应用于由不同类型承载的角色*，只要这些类型兼容即可。

### Chapter Notes

本章涵盖内容广泛，是本书中技术挑战最大的一章。更多讨论参见以下研究论文，本章大部分材料均基于这些论文。这些论文也包含相关工作的详细参考。

概念连接参见 [Halpin (2002a)](#Ch010_401-479_B9780443237904000244.xhtml#bb0605)、[Halpin (2005c)](#Ch010_401-479_B9780443237904000244.xhtml#bb0635)。道义规则参见 [Halpin (2006a)](#Ch010_401-479_B9780443237904000244.xhtml#bb0650)、[Halpin (2007a)](#Ch010_401-479_B9780443237904000244.xhtml#bb0660)。数据建模中的时间问题参见 Halpin 在 *Business Rules Journal* 上的系列在线文章（[www.brcommunity.com/nphp](http://www.brcommunity.com/nphp)）。集合类型参见 [Halpin (2000b)](#Ch010_401-479_B9780443237904000244.xhtml#bb0590)。名词化和对象化参见 [Halpin (2005a)](#Ch010_401-479_B9780443237904000244.xhtml#bb0625)、[Halpin (2008)](#Ch010_401-479_B9780443237904000244.xhtml#bb0680)。高阶类型参见 [Halpin (2004a)](#Ch010_401-479_B9780443237904000244.xhtml#bb0615)、[Halpin (2005d)](#Ch010_401-479_B9780443237904000244.xhtml#bb0640)。超类型角色的进一步约束及跨不同类型承载角色的包含或约束参见 [Halpin and Curland (2013)](#Ch010_401-479_B9780443237904000244.xhtml#bb0745)。

## References[^(12)](#fn12)

*   [Bakema G., Zwart J., van der Lek H.](#Ch010_401-479_B9780443237904000244.xhtml#B-bb0030) *Fully communication oriented NIAM.* In: Nijssen G.M., Sharp J., eds. NIAM-ISDM 1994 Conf. Working Papers, Albuquerque, NM; 1994:L1–35.

*   [Balsters H., Halpin T.](#Ch010_401-479_B9780443237904000244.xhtml#B-bb0045) Formal semantics of dynamic constraints and derivation rules in ORM. *Int. J. Inform. Syst. Model. Des.* 2016;7(2) IGI Global.

*   [Falkenberg E.](#Ch010_401-479_B9780443237904000244.xhtml#B-bb0425) DETERM: deterministic event-tuned entity-relationship modeling. In: *Entity-Relationship Approach—ER’93.* Springer LNCS 823; 1993:230–241.

*   [Fitting M.](#Ch010_401-479_B9780443237904000244.xhtml#B-bb0465) Databases and higher types. In: Lloyd J., et al., eds. *Computational Logic–CL2000.* Springer-Verlag; 2000:41–52 LNAI 1861.

*   [Guarino N., Welty C.](#Ch010_401-479_B9780443237904000244.xhtml#B-bb0505) Evaluating ontological decisions with onto clean. *CACM.* 2002;45(2):61–65.

*   [Guizzardi G.](#Ch010_401-479_B9780443237904000244.xhtml#B-bb0510) *Ontological Foundations for Structural Conceptual Models.* CTIT PhD Thesis Series, No. 05-74 The Netherlands: Enschede; 2005.

*   [Guizzardi G., Wagner G., Guarino N., van Sinderen N.](#Ch010_401-479_B9780443237904000244.xhtml#B-bb0515) An ontologically well-founded profile for UML conceptual models. In: Persson A., Stirna J., eds. *Proc. 16th Int. Conf. on Advanced Inf. Sys. Engineering, CAiSE2004.* Springer LNCS 3084; 2004:112–126.

*   [Halpin T.](#Ch010_401-479_B9780443237904000244.xhtml#B-bb0590) *Modeling collections in UML and ORM.* In: Proc. EMMSAD’00: 5th Int. Workshop on Evaluation of Modeling Methods in Sys. Analysis and Design, Kista, Sweden; 2000 \*.
