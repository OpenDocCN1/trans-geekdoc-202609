
进入`/path/to/xxx`目录，找到`xxx.json`。

在表达式`cvar = avar + bvar`中，加法运算符（`+`）将`avar`与`bvar`相加，得到它们的和`cvar`

在`List.of(arg0, arg1, arg2)`中，`List`接口的工厂方法`of()`接受一系列的元素，返回包含它们的只读列表。

之后我们这样调用`cmd`命令：`cmd arg0 arg1 arg2`。

```
if (condVar > someVal) {console.log("xxx")}
```

ProPublica`\[[133](#references.xhtml#ref-133)\]` implicitly adopted equality of false positive rates as a fairness criterion in its article on COMPAS scores. Northpointe, the maker of the COMPAS software, emphasized the importance of calibration by group in their rebuttal`\[[134](#references.xhtml#ref-134)\]` to ProPublica’s article. Similar arguments were made quickly after the publication of ProPublica’s article by bloggers including Abe Gong. There has been extensive scholarship on actuarial risk assessment in criminal justice that long predates the ProPublica debate; Richard Berk, Hoda Heidari, Shahin Jabbari et al.`\[[135](#references.xhtml#ref-135)\]` provide a survey with commentary.

Variants of the trade-off between separation and sufficiency were shown by Alexandra Chouldechova`\[[136](#references.xhtml#ref-136)\]` and Jon Kleinberg, Mullainathan, and Raghaven`\[[137](#references.xhtml#ref-137)\]`. Each of them considered somewhat different criteria to trade-off. Chouldechova’s argument is very similar to the proof we presented that invokes the relationship between positive predictive value and true positive rate. Subsequent work`\[[138](#references.xhtml#ref-138)\]` considers trade-offs between relaxed and approximate criteria. The other trade-off results presented in this chapter are new to this book. The proof of the proposition relating separation and independence for binary classifiers, as well as the counterexample for ternary classifiers, is due to Shira Mitchell and Jackie Shadlen, pointed out to us in personal communication.

Table 3.5List of statistical nondiscrimination criteria

| Name || Criterion || Note || Reference |
| --- | --- | --- | --- |
| Independence || Indep. || Equiv. || Calders et al. (2009) \[[127](#references.xhtml#ref-127)\] |
| --- | --- | --- | --- |
| Group fairness || Indep. || Equiv. || |
| Demographic parity || Indep. || Equiv. || |
| Conditional statistical parity || Indep. || Relax. || Corbett-Davies et al. (2017) |
| Darlington criterion (4) || Indep. || Relax. || Darlington (1971) \[[123](#references.xhtml#ref-123)\] |
| Equal opportunity || Separ. || Relax. || Hardt, Price, Srebro (2016) \[[114](#references.xhtml#ref-114)\] |
| Equalized odds || Separ. || Equiv. || Hardt, Price, Srebro (2016) \[[114](#references.xhtml#ref-114)\] |
| Conditional procedure accuracy || Separ. || Equiv. || Berk et al. (2017) \[[135](#references.xhtml#ref-135)\] |
| Avoiding disparate mistreatment || Separ. || Equiv. || Zafar et al. (2017) \[[131](#references.xhtml#ref-131)\] |
| Balance for the negative class || Separ. || Relax. || Kleinberg et al. (2016) |
| Balance for the positive class || Separ. || Relax. || Kleinberg et al. (2016) |
| Predictive equality || Separ. || Relax. || Corbett-Davies et al. (2017) |
| Equalized correlations || Separ. || Relax. || Woodworth et al. (2017) \[[132](#references.xhtml#ref-132)\] |
| Darlington criterion (3) || Separ. || Relax. || Darlington (1971) \[[123](#references.xhtml#ref-123)\] |
| Cleary model || Suff. || Relax. || Cleary (1966) \[[121](#references.xhtml#ref-121)\] |
| Conditional use accuracy || Suff. || Equiv. || Berk et al. (2017) \[[135](#references.xhtml#ref-135)\] |
| Predictive parity || Suff. || Relax. || Chouldechova (2016) \[[136](#references.xhtml#ref-136)\] |
| Calibration within groups || Suff. || Equiv. || Chouldechova (2016) \[[136](#references.xhtml#ref-136)\] |
| Darlington criterion (1), (2) || Suff. || Relax. || Darlington (1971) \[[123](#references.xhtml#ref-123)\] |

The credit score case study is from Moritz Hardt, Eric Price, and Nati Srebro`\[[114](#references.xhtml#ref-114)\]`. However, we highlight the independence criterion in our plots, whereas the authors of the paper highlight the equality of opportunity criterion instead. The numbers about the racial composition of the dataset come from the “Estimation sample” column of table 9 on the webpage for the Federal Reserve report`\[[116](#references.xhtml#ref-116)\]`.

### A Dictionary of Criteria

For convenience we collect some demographic fairness criteria below that have been proposed in the past (not necessarily including the original reference). We will match them to their closest relative among the three criteria independence, separation, and sufficiency. This table is meant as a reference only and is not exhaustive. There is no need to memorize these different names.

# 4 Relative Notions of Fairness

In chapter 3, we considered a range of statistical criteria that help to highlight group-level differences in both the treatments and the outcomes that might be brought about by the use of a machine learning model. But why should we be concerned with group-level differences? And how should we decide which groups we should be concerned with? In this chapter, we’ll explore the many different normative reasons we might have to object to group-level differences. This is a subtle, but important, shift in focus from chapter 2, where we considered some of the normative reasons why *individuals* might object to decision-making schemes that distribute desirable resources or opportunities. In this chapter, we’ll focus on why we might be concerned with the uneven allocation of resources and opportunities across *specific groups* and *society overall*. In particular, we’ll review the normative foundations that ground claims of discrimination and calls for distributive justice. We’ll then try to connect these arguments more directly to the statistical criteria developed in chapter 3, with the aim of giving those criteria greater normative substance.

A point of terminology: we use the terms *unfairness* and *discrimination* roughly synonymously. Linguistically, the term “discrimination” puts more emphasis on the agency of the decision maker. We also specifically avoid using the terminology “disparate treatment” and “disparate impact” in this chapter as these are legal terms of art with more precise meanings and legal significance; we’ll address these in chapter 6.

## Systematic Relative Disadvantage

Discussions of discrimination in the context of machine learning can seem odd if you consider that the very point of many machine learning applications is to figure out how to treat different people differently—that is, to discriminate between them. However, what we call discrimination in this chapter is not different treatment in and of itself, but rather treatment that systematically imposes a disadvantage on one social group relative to others. The systematicity in the differences in treatment and outcomes is what gives discrimination its normative force as a concept.

To better appreciate this point, consider three levels at which people might be subject to unfair treatment. First, a person might be subject to the prejudice of an individual decision maker—for example, a specific hiring manager whose decisions are influenced by racial animus. Second, a person might encounter systematic barriers to entering certain occupations, perhaps because members of the group to which they belong are not viewed as fit to be engineers, doctors, lawyers, and so on, regardless of their true capabilities or potential. For example, in some occupations women might have limited employment opportunities across the board due to their gender. Finally, certain personal characteristics might be an organizing principle for society overall such that members of certain groups are systematically excluded from opportunities across multiple spheres of life. For example, race and gender might limit people’s access not only to employment, but to education, credit, housing, and so on.
