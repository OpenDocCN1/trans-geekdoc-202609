
A structural factor that exacerbates all of the mechanisms of discrimination we discussed is the segregation of society along the lines of group identity. Segregation arguably enables interpersonal discrimination because increased contact among groups decreases prejudice toward outgroups—the controversial contact hypothesis \[[465](#references.xhtml#ref-465)\].

At a structural level, segregation sustains inequality because an individual’s opportunities for economically productive activities depend on her social capital, including the home, community, and educational environment. A strand of the economics literature has built mathematical models and simulations to understand how group inequalities—especially racial inequalities—arise and persist indefinitely even in the absence of interpersonal discrimination, and despite no intrinsic differences between groups. In the extreme case, if we imagine two or more groups belonging to noninteracting economies that grow at the same rate, it is intuitively clear that differences can persist indefinitely. If segregation is imperfect, do gaps eventually close? This is sensitive to the assumptions in the model. In Lundberg and Startz’s model the gaps close eventually, although extremely slowly \[[466](#references.xhtml#ref-466)\]. In Bowles and Sethi’s model, they don’t under some conditions \[[468](#references.xhtml#ref-468)\]; one reason is that the disadvantaged group might face higher costs of labor-market skill acquisition due to lower social capital \[[469](#references.xhtml#ref-469)\].

In the United States, after the civil rights legislation of the 1960s and 1970s, residential segregation by race has been decreasing, albeit slowly. On the other hand, residential segregation by income appears to be increasing \[[470](#references.xhtml#ref-470)\].

### The Role of Feedback Loops

There is a classic economic model of feedback loops in the context of a labor market \[[315](#references.xhtml#ref-315)\]. There are two groups of workers and two types of jobs: high- and low- skilled, with high-skilled jobs requiring certain qualifications to be performed effectively. Under suitable assumptions (especially, employers cannot perfectly observe worker qualifications before hiring them, but only after providing costly on-the-job skills training) there exists an economic equilibrium in which the following feedback loop sustains itself:

1.  The employer practices wage discrimination between the two groups.

2.  As a result, the disadvantaged group achieves lower returns to investment in qualifications.

3.  Workers, assumed to be rational, respond to such a differential by investing differently in acquiring qualifications, with one group acquiring more qualifications.

4.  The employer—again, under certain rationality assumptions—wage discriminates because of the observed difference in qualifications.

The significance of this model is that it can explain the persistence of inequality (and discrimination) without assuming intrinsic differences between the groups, and without employers discriminating between equally qualified workers. It should be viewed as showing only the possibility of such feedback loops. Like any theoretical model, a claim that such a feedback loop explains some actually observed disparity would require careful empirical validation.

# 9 Datasets

It has become commonplace to point out that machine learning models are only as good as the data they’re trained on. The old slogan “garbage in, garbage out” no doubt applies to machine learning practice, as does the related catchphrase “bias in, bias out.” Yet, these proverbs still understate—and somewhat misrepresent—the significance of data for machine learning.

It’s not only the output of a learning algorithm that may suffer with poor input data. A dataset serves many other vital functions in the machine learning ecosystem. The dataset itself is an integral part of the problem formulation. It implicitly sorts out and operationalizes what the problem is that practitioners end up solving. Datasets have also shaped the course of entire scientific communities in their capacity to measure and benchmark progress, support competitions, and interface between researchers in academia and practitioners in industry.

If so much hinges on data in machine learning, it might come as a surprise that there is no simple answer to the question of what makes data good for what purpose. The collection of data for machine learning applications has not followed any established theoretical framework, certainly not one that was recognized a priori.

In this chapter, we take a closer look at popular datasets in the field of machine learning and the benchmarks that they support. We use this to tease apart the different roles datasets play in scientific and engineering contexts. Then we review the harms associated with data and discuss how they can be mitigated based on the dataset’s role. We conclude with several broad directions for improving data practices.

We limit the scope of this chapter in some important ways. Our focus will be largely on publicly available datasets that support training and testing purposes in machine learning research and applications. Our focus excludes large swaths of industrial data collection, surveillance, and data-mining practices. It also excludes data purposely collected to test specific scientific hypotheses, such as experimental data gathered in a medical trial.

## A Tour of Datasets in Different Domains

The creation of datasets in machine learning does not follow a clear theoretical framework. Datasets aren’t collected to test a specific scientific hypothesis. In fact, we will see that there are many different roles data play in machine learning. As a result, it makes sense to start by looking at a few influential datasets from different domains to get a better feeling for what they are, what motivated their creation, how they organized communities, and what impact they had.

### TIMIT

Automatic speech recognition is a machine learning problem of significant commercial interest. Its roots date back to the early twentieth century \[[471](#references.xhtml#ref-471)\].

Interestingly, speech recognition also features one of the oldest benchmarks datasets, the TIMIT (Texas Instruments/Massachusetts Institute for Technology) data. The creation of the dataset was funded through a 1986 program on speech recognition by the Defense Advanced Research Projects Agency (DARPA). In the mid-eighties, artificial intelligence was in the middle of a “funding winter,” where many governmental and industrial agencies were hesitant to sponsor AI research because it often promised more than it could deliver. DARPA program manager Charles Wayne proposed that a way round this problem was to establish more rigorous evaluation methods. Wayne enlisted the National Institute of Standards and Technology to create and curate shared datasets for speech, and he text, and he graded success in his program based on performance on recognition tasks on these datasets.

Many now credit Wayne’s program with kick-starting a revolution of progress in speech recognition \[[472](#references.xhtml#ref-472)–474\]. According to Kenneth Ward Church,

It enabled funding to start because the project was glamour-and-deceit-proof, and to continue because funders could measure progress over time. Wayne’s idea makes it easy to produce plots which help sell the research program to potential sponsors. A less obvious benefit of Wayne’s idea is that it enabled hill climbing. Researchers who had initially objected to being tested twice a year began to evaluate themselves every hour \[[473](#references.xhtml#ref-473)\].
