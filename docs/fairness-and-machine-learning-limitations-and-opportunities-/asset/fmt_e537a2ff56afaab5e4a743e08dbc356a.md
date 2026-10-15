
Observational studies and observational fairness criteria continue to be important. Such studies are typically carried out by algorithm developers or decision makers, often in collaboration with external researchers \[[374](#references.xhtml#ref-374), [375](#references.xhtml#ref-375)\]. It is relatively rare for observational data to be made publicly available. A rare exception, the COMPAS dataset, involved a Freedom of Information Act request.

Finally, it is worth reiterating that quantitative studies are narrow in what they can conceptualize and measure \[[376](#references.xhtml#ref-376)\]. Qualitative and ethnographic studies of decision makers thus provide an invaluable complementary perspective. To illustrate, we’ll discuss a study by Samir Passi and Solon Barocas that reports on six months of ethnographic fieldwork in a corporate data science team \[[170](#references.xhtml#ref-170)\]. The team worked on a project in the domain of car financing that aimed to “improve the quality” of leads (leads are potential car buyers in need of financing who might be converted to actual buyers through marketing). Given such an amorphous high-level goal, formulating a concrete and tractable data science problem is a necessary and nontrivial task—a task that is further complicated by the limitations of the data available. The paper documents how there is substantial latitude in problem formulation, and spotlights the iterative process that was used, which resulted in a series of proxies for lead quality. The authors show that different proxies have different fairness implications: one proxy would maximize people’s lending opportunities and another would alleviate dealers’ existing biases, both potentially valuable fairness goals. However, the data scientists were not aware of the normative implications of their decisions and did not explicitly deliberate them.

## Looking Ahead

In this chapter, we cover traditional tests for discrimination as well as fairness studies of various algorithmic systems. Together, these methods constitute a powerful toolbox for interrogating a single decision system at a single point in time. But there are other types of fairness questions we can ask: What is the cumulative effect of the discrimination faced by a person over the course of a lifetime? What structural aspects of society result in unfairness? We cannot answer such questions by looking at individual systems. The next chapter is all about broadening our view of discrimination and then using that broader perspective to study a range of possible fairness interventions.

## Chapter Notes

To understand social science audit studies in more depth, see the paper by Devah Pager \[[296](#references.xhtml#ref-296)\]. S. Michael Gaddis provides a more recent introduction and survey \[[377](#references.xhtml#ref-377)\].

Auditing of algorithmic systems is a young, quickly evolving field: a 2014 paper issued a call to action toward this type of research \[[378](#references.xhtml#ref-378)\]. Most of the studies that we cite postdate that piece. For a more recent practitioner-focused overview, Sasha Costanza-Chock, Inioluwa Deborah Raji, and Joy Buolamwini compile best practices for auditors and provide recommendations for policymakers based on interviews with over 150 auditors \[[279](#references.xhtml#ref-279)\]. Briana Vecchione, Karen Levy, and Solon Barocas draw lessons for algorithm audits and justice from the history of audits in the social sciences \[[379](#references.xhtml#ref-379)\]. Miles Brundage, Shahar Avin, Jasmine Wang et al. put third-party audits in the context of many other ways of supporting verifiable claims about the impacts of AI systems \[[380](#references.xhtml#ref-380)\].

For in-depth treatments of the history and politics of information platforms, see *The Master Switch* by Tim Wu \[[381](#references.xhtml#ref-381)\], *The Politics of “Platforms”* and *Custodians of the Internet* by Tarleton Gillespie \[[382](#references.xhtml#ref-382), [383](#references.xhtml#ref-383)\], and *The New Governors* by Kate Klonick \[[384](#references.xhtml#ref-384)\].

# 8 A Broader View of Discrimination

Machine learning systems don’t operate in a vacuum; they are adopted in societies that already have many types of discrimination intertwined with systems of oppression such as racism. This is at the root of fairness concerns in machine learning. In this chapter we take a systematic look at discrimination in society. This gives us a more complete picture of the potential harmful impacts of machine learning. We see that while a wide variety of fairness interventions are possible—and necessary—only a small fraction of them translate to technical fixes.

## Case Study: The Gender Earnings Gap on Uber

We’ll use a paper that analyzes the gender earnings gap on Uber \[[385](#references.xhtml#ref-385)\] as a way to apply some of the lessons from the previous two chapters while setting up some of the themes of this chapter. The study was coauthored by current and former Uber employees.

The authors start with the observation that female drivers earn 7 percent less on Uber per active hour than male drivers. They conclude that this gap can be explained by three factors: gender differences in drivers’ choices of where to drive, men’s greater experience on the platform, and men’s tendency to drive faster. They find that customer discrimination and algorithmic discrimination do not contribute to the gap. We take the paper’s technical claims at face value, but use the critical framework we’ve introduced to interpret the findings quite differently from the authors.

First, let’s understand the findings in more detail.

The paper analyzes observational data on trips in the United States, primarily in Chicago. [Figure 8.1](#chapter_8.xhtml#fig8-1) is a causal graph showing what we consider to be the core of the causal model studied in the paper (the authors do not draw such a graph and do not pose their questions in a causal framework; we have chosen to do so for pedagogical purposes). A full graph would be much larger than the figure; for example, we’ve omitted a number of additional controls, such as race, that are presented in the appendix.

![Figure 8.1Our understanding of the causal model implicit in the Uber study.](images/fig8-1.png)

[Figure 8.1](#chapter_8.xhtml#fig8_1)Our understanding of the causal model implicit in the Uber study.

We’ll use this graph to describe the findings. At a high level, the graph describes a joint distribution whose samples are trips. To illustrate, different trips corresponding to the same driver will have the same *residence* (unless the driver moved during their tenure on the platform), but different *experience* (measured as number of prior trips).

Drivers’ hourly earnings are primarily determined by the algorithm that allocates trip requests from riders to drivers. The allocation depends on demand, which in turn varies by location and time of the week (the week-to-week variation is considered noise). Uber’s algorithm ignores driver attributes including experience and gender, hence there are no arrows from those nodes to *trip request*. In addition, a few other factors might affect earnings. Drivers who drive faster complete more trips, drivers may strategically accept or cancel trips, and riders might discriminate by canceling trips after the driver accepts.

The paper uses a technique called *Gelbach decomposition* to identify the effect of each of several variables on the hourly earnings. Decomposition is a set of techniques used in economics for quantifying the contribution of various sources to an observed difference in outcomes. Although the authors don’t perform causal inference, we will continue to talk about their findings in causal terms for pedagogical purposes. The difference is not salient to the high-level points we wish to make.
