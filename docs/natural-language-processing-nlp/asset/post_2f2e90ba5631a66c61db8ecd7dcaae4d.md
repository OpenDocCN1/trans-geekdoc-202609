
### 15.1.2 Proper Nouns

If a proper noun is used as a referring expression, it often corefers with another proper noun, so that the coreference problem is simply to determine whether the two names match. Subsequent proper noun references often use a shortened form, as in the running example (Figure 15.1):

(15.12) Apple Inc Chief Executive [Tim Cook] has jetted into China ... [Cook] is on his first business trip to the country ...

A typical solution for proper noun coreference is to match the syntactic head words of the reference with the referent. In § 10.5.2, we saw that the head word of a phrase can be identified by applying head percolation rules to the phrasal parse tree; alternatively, the head can be identified as the root of the dependency subtree covering the name. For sequences of proper nouns, the head word will be the final token.

There are a number of caveats to the practice of matching head words of proper nouns.

- In the European tradition, family names tend to be more specific than given names, and family names usually come last. However, other traditions have other practices: for example, in Chinese names, the family name typically comes first; in Japanese, honorifics come after the name, as in Nobu-San (Mr. Nobu).
- In organization names, the head word is often not the most informative, as in Georgia Tech and Virginia Tech. Similarly, Lebanon does not refer to the same entity as Southern Lebanon, necessitating special rules for the specific case of geographical modifiers (Lee et al., 2011).
- Proper nouns can be nested, as in [the CEO of [Microsoft]], resulting in head word match without coreference.

Despite these difficulties, proper nouns are the easiest category of references to resolve (Stoyanov et al., 2009). In machine learning systems, one solution is to include a range of matching features, including exact match, head match, and string inclusion. In addition to matching features, competitive systems (e.g., Bengtson and Roth, 2008) include large lists, or gazetteers, of acronyms (e.g, the National Basketball Association/NBA), demonyms (e.g., the Israelis/Israel), and other aliases (e.g., the Georgia Institute of Technology/Georgia Tech).

### 15.1.3 Nominals

In coreference resolution, noun phrases that are neither pronouns nor proper nouns are referred to as nominals. In the running example (Figure 15.1), nominal references include: the firm (Apple Inc); the firm's biggest growth market (China); and the country (China).

## 河东市地热资源开发利用与保护合同

为加强地热资源管理，合理开发利用和保护地热资源，促进地热资源可持续利用，根据《中华人民共和国矿产资源法》《矿产资源开采登记管理办法》等法律法规，结合河东市实际，订立本合同。

第一条 地热资源属于国家所有，不因其所依附的土地所有权或者使用权的不同而改变。勘查、开采地热资源必须依法取得探矿权、采矿权。

第二条 市自然资源和规划主管部门负责全市地热资源开发利用与保护的监督管理工作。市水利、生态环境、住建等有关部门按照各自职责，协同做好地热资源相关工作。

| 序号 | 项目名称 | 开发单位 | 开采规模 | 审批状态 |
|------|----------|----------|----------|----------|
| 1 | 河东新区地热供暖项目 | 河东新能源有限公司 | 10万m³/a | 已批准 |
| 2 | 温泉度假村地热利用项目 | 温泉旅游开发公司 | 5万m³/a | 已批准 |
| 3 | 农业温室地热项目 | 绿源农业科技有限公司 | 3万m³/a | 审核中 |

第三条 开采地热资源应当遵循综合利用、梯级开发的原则，提高地热资源利用率。鼓励采用先进技术和工艺，实现地热资源的高效利用和尾水回灌。

第四条 开采地热资源必须符合地热资源开发利用规划和年度开采计划，不得超采、滥采。开采单位应当安装计量设施，建立开发利用台账，定期向主管部门报送开采利用情况。

第五条 开采地热资源应当按照规定缴纳资源税和矿业权出让收益。地热资源开发利用实行有偿使用制度，具体标准按照国家及省有关规定执行。

第六条 违反本合同规定，未取得勘查许可证或者采矿许可证擅自开采地热资源的，由市自然资源和规划主管部门依法责令停止开采，赔偿损失，并处以罚款；构成犯罪的，依法追究刑事责任。

第七条 本合同自签订之日起生效。合同双方应当严格履行本合同的各项条款，因履行本合同发生争议的，由双方协商解决；协商不成的，可依法向人民法院提起诉讼。

network, ψ_E(i, e) = Feedforward([v_e; u_i]). If i is added to entity e, then its representation is updated recurrently, v_e ← f(v_e, u_i), using a recurrent neural network such as a long short-term memory (LSTM; chapter 6). Alternatively, we can apply a pooling operation, such as max-pooling or average-pooling (chapter 3), setting v_e ← Pool(v_e, u_i). In either case, the update to the representation of entity e can be thought of as adding new information about the entity from mention i.

### 15.4 Evaluating coreference resolution

The state of coreference evaluation is aggravatingly complex. Early attempts at simple evaluation metrics were found to be susceptible to trivial baselines, such as placing each mention in its own cluster, or grouping all mentions into a single cluster. Following Denis and Baldridge (2009), the CoNLL 2011 shared task on coreference (Pradhan et al., 2011) formalized the practice of averaging across three different metrics: MUC (Vilain et al., 1995), B-CUBED (Bagga and Baldwin, 1998a), and CEAF (Luo, 2005). Reference implementations of these metrics are available from Pradhan et al. (2014) at https://github.com/conll/reference-coreference-scorers.

### Additional resources

Ng (2010) surveys coreference resolution through 2010. Early work focused exclusively on pronoun resolution, with rule-based (Lappin and Leass, 1994) and probabilistic methods (Ge et al., 1998). The full coreference resolution problem was popularized in a shared task associated with the sixth Message Understanding Conference, which included coreference annotations for training and test sets of thirty documents each (Grishman and Sundheim, 1996). An influential early paper was the decision tree approach of Soon et al. (2001), who introduced mention ranking. A comprehensive list of surface features for coreference resolution is offered by Bengtson and Roth (2008). Durrett and Klein (2013) improved on prior work by introducing a large lexicalized feature set; subsequent work has emphasized neural representations of entities and mentions (Wiseman et al., 2015).

### Exercises

1. Select an article from today’s news, and annotate coreference for the first twenty noun phrases and possessive pronouns that appear in the article, include ones that are nested within larger noun phrases. Then specify the mention-pair training data that would result from the first five of these candidate entity mentions.
2. Using your annotations from the preceding problem, compute the following statistics: Compare the ratio of the counts of the original 5-gram to the summed counts of the 5-grams created by substitution. Is this ratio a good predictor of whether it is referential?

## Chapter 16 Discourse

Applications of natural language processing often concern multi-sentence documents: from paragraph-long restaurant reviews, to 500-word newspaper articles, to 500-page novels. Yet most of the methods that we have discussed thus far are concerned with individual sentences. This chapter discusses theories and methods for handling multi-sentence linguistic phenomena, known collectively as **discourse**. There are diverse characterizations of discourse structure, and no single structure is ideal for every computational application. This chapter covers some of the most well studied discourse representations, while highlighting computational models for identifying and exploiting these structures.

### 16.1 Segments

A document or conversation can be viewed as a sequence of **segments**, each of which is **cohesive** in its content and/or function. In Wikipedia biographies, these segments often pertain to various aspects to the subject’s life: early years, major events, impact on others, and so on. This segmentation is organized around **topics**. Alternatively, scientific research articles are often organized by **functional themes**: the introduction, a survey of previous research, experimental setup, and results.

Written texts often mark segments with section headers and related formatting devices. However, such formatting may be too coarse-grained to support applications such as the retrieval of specific passages of text that are relevant to a query (Hearst, 1997). Unformatted speech transcripts, such as meetings and lectures, are also an application scenario for segmentation (Carletta, 2007; Glass et al., 2007; Janin et al., 2003).
