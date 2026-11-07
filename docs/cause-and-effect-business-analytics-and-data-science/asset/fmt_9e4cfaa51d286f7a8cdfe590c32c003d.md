
The previous section introduced causal measurement at the population or group level, which enables the selection of the best treatment for part or all of the overall population. Researchers and practitioners have not stopped at estimating the overall treatment effect for the population or a group (or for the “average” person). With the advances of Machine Learning and predictive analytics, along with randomized experiments and causal inference, researchers have taken a further step to estimate treatment effects at the individual level. This increasingly popular subfield known as uplift modeling was separately created in the late 1990s and early 2000s by researchers and practitioners such as Radcliffe and Surrey (1999) and Lo (2002) with the objective of finding individuals who are truly positively influenced by a treatment or intervention through Machine Learning and predictive modeling by uncovering heterogeneous treatment effects in available data. This technique enables us to potentially identify the “persuadables” and thus optimize target selection in order to maximize treatment impact; see [Siegel (2011](#chapter1.xhtml#ref1_27), 2013b). Motivated by the trend of personalization in many industries, this subfield has gained tremendous attention in recent years with seemingly unlimited applications such as personalized marketing (original usage of uplift), personalized medicine, political elections, personalized insurance, and healthcare programs, with growing numbers of publications and presentations from both industry practitioners and academics across the globe. Independently, researchers from Economics, Epidemiology, and Statistics have considered similar or related methodologies applied to Social Sciences and Medical Sciences, for example, [Athey and Imbens (2015)](#chapter1.xhtml#ref1_3), [Yong (2015)](#chapter1.xhtml#ref1_37), and Zink et al. (2015).

The most prominent application of uplift modeling so far is perhaps in political elections. In the 2012 Obama re-election campaign, the campaign team had a limited budget to spend on targeting voters. Their analytics team designed an intelligent approach – instead of communicating with those who would almost surely vote for Obama or his opponent (as it would be ineffective to market to these two groups), they applied uplift modeling to uncover the swing voters who are most “persuadable” by marketing communication, enabling their campaign to maximize overall impact, as documented in Stedman (2013) and [Siegel (2013a)](#chapter1.xhtml#ref1_28). This success has led to wider applications of uplift modeling in political elections. As in marketing and sales campaigns, where traditional predictive modeling focuses on predicting the outcome, uplift modeling estimates the effectiveness of the treatment or intervention at the individual level, allowing one to focus resources on the subjects that are likely to be positively impacted by the treatment.

[Figure 1.7](#chapter1.xhtml#fig1_7) provides a classification framework for uplift modeling and causal inference. The vertical axis extends from association only (what may be correlated) to causal measurement (which are causing which), while the horizontal axis moves from population (or group or subpopulation) level summary statistics to personalized level modeling. We will describe the four quadrants of [Figure 1.7](#chapter1.xhtml#fig1_7) in the following:

![Figure 1.7 Framework for causal and association analysis. ⏎](images/fig1_7.jpg)

Figure 1.7 Framework for causal and association analysis. [⏎](#chapter1.xhtml#b1fig1_7)

### Reporting/Summary Statistics
This is a subset of Descriptive Analytics in [Figure 1.2](#chapter1.xhtml#fig1_2), where the past data (sales reports, financial reports, and summaries of other historical data) are summarized visually or statistically to describe what happened in the population (or subpopulation) as a whole.

### Causal Inference
As described in [Section 1.2](#chapter1.xhtml#sec1_2), this type of analytics extends beyond association or correlation-based summary statistics and provides insight into the causal link between a treatment or intervention and an outcome for the overall population (or a group). The estimate is known as the Average Treatment Effect (`ATE`) in academia or simply “lift” in business.

### Response Modeling or Propensity Modeling
Using historical customer data at the individual level, the traditional usage of analytics is to apply predictive modeling, also known as supervised learning, to target customers who are likely to take a desirable action regardless of whether or not they receive an intervention or treatment, as documented in marketing analytics textbooks such as [Jackson and Wang (1996)](#chapter1.xhtml#ref1_12) and Roberts and Berger (1999). Such a model is known as a Response Model or Propensity Model, which almost guarantees, by design, that the model targets are better than random targets in terms of response rate by design. It improves efficiency by increasing the proportion of responders within the treatment group. It extends Reporting/Summary Statistics from the population or group level to the individual level, leading to targeting at a personalized level.

### Uplift Modeling
While response or propensity modeling aims at predicting the outcome, uplift modeling is about predicting the lift between treatment (contacted) and control (uncontacted)

Table 1.1 Example of Possible Campaign Result from Traditional Predictive Modeling [⏎](#chapter1.xhtml#b1tbl1_1)

|  || Model Targets (Top Three Deciles) (%) || Random Targets (%) |

| --- | --- | --- |

| Treatment || 2.5 || 1.0 |

| --- | --- | --- |

| Control || 2.5 || 1.0 |

| Lift || 0.0 || 0.0 |

[Chapter 2](#chapter2.xhtml) of this book describes the traditional predictive modeling approach before we dive into causal inference and uplift modeling in subsequent chapters.

## 1.4 Organization of This Book
This book discusses two major topics, Causal Business Analytics and Uplift Analytics, with a range of methodologies illustrated with practical business problems and data. The first topic is about applying proper causal analytics methodologies, known as causal inference in academia, in the business setting. As mentioned in [Section 1.2](#chapter1.xhtml#sec1_2), there are many textbooks on causal inference from various academic fields, but there has not been one seen so far that touches on practical business applications with a wide range of methodologies. The second topic is the emerging field of uplift analytics – given its relatively emerging state, there are very few books on this topic. Our coverage on uplift is broad: From experimental design for uplift to model measurement, predictive modeling for uplift, and prescriptive uplift analytics (treatment optimization).
