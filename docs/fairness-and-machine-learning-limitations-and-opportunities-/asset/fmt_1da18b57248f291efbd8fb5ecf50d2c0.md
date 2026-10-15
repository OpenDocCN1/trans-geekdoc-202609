
Although the language of counterfactuals appears here, the notion of but-for causation may not effectively correspond to a correct causal counterfactual. Expanding on how to interpret but-for causation, the court noted:

a but-for test directs us to change one thing at a time and see if the outcome changes. If it does, we have found a but-for cause.

Changing one attribute while holding all others fixed is not in general a correct way of computing counterfactuals in a causal graph. This important issue was central to an major discrimination lawsuit.

### Harvard College Admissions

In a trial dating back to 2015, the plaintiff Students for Fair Admissions (SFFA) alleged discrimination in Harvard undergraduate admissions against Asian Americans. Plaintiff SFFA is an offshoot of a legal defense fund which aims to end the use of race in voting, education, contracting, and employment.

The trial entailed unprecedented discovery regarding higher education admissions processes and decision making, including statistical analyses of individual-level applicant data from the past five admissions cycles.

The plaintiff’s expert report by Peter S. Arcidiacono, professor of economics at Duke University, claims:

Race plays a significant role in admissions decisions. Consider the example of an Asian-American applicant who is male, is not disadvantaged, and has other characteristics that result in a 25% chance of admission. Simply changing the race of the applicant to white—and leaving all his other characteristics the same—would increase his chance of admission to 36%. Changing his race to Hispanic (and leaving all other characteristics the same) would increase his chance of admission to 77%. Changing his race to African-American (again, leaving all other characteristics the same) would increase his chance of admission to 95%. (EXPERT REPORT OF PETER S. ARCIDIACONO Students for Fair Admissions, Inc. v. Harvard No. 14-cv-14176-ADB \[D. Mass\])

The plaintiff’s charge, summarized above, is based technically on the argument that conditional statistical parity is not satisfied by a model of Harvard’s admissions decisions. Harvard’s decision process isn’t codified as a formal decision rule. Hence, to talk about Harvard’s decision rule formally, we first need to model Harvard’s decision rule. The plaintiff’s expert did so by fitting a logistic regression model against Harvard’s past admissions decisions in terms of variables deemed relevant for the admission decision.

Formally, denoting by *Ŷ* the model of Harvard’s admissions decisions, by *X* a set of applicant features deemed relevant for admission, and by *A* the applicant’s reported race, we have that

![](images/pg142-1.png)

for some groups *a, a*′ and some significant value of *δ >* 0.

The violation of this condition certainly depends on which features we deem relevant for admissions, formally, which features *X* we should condition on. Indeed, this point is to a large extent the basis of the response of the defendant’s expert, David Card, professor of economics at the University of California, Berkeley. Card argues that under a different reasonable choice of *X*, one that includes among other features the applicant’s interview performance and the year they applied, the observed disparity disappears.

The selection and discussion of what constitute relevant features is certainly important for the interpretation of conditional statistical parity. But arguably a bigger question is whether a violation of conditional statistical parity constitutes evidence of discrimination in the first place. This isn’t merely a question of having selected the right features to condition on.

What does the plaintiff’s expert report mean by “changing his race”? The literal interpretation is to “flip” the race attribute in the input to the model without changing any of the other features of the input. But a formal interpretation in terms of attribute swapping is not necessarily what triggers our moral intuition. As we know now, attribute flipping generally does not produce valid counterfactuals. Indeed, if we assume a causal graph in which some of the relevant features are influenced by race, then computing counterfactuals with respect to race would require adjusting downstream features. Changing the race attribute without a change in any other attribute only corresponds to a counterfactual in the case where race does not have any descendant nodes—an implausible assumption.

Attribute flipping is often mistakenly given a counterfactual causal interpretation. Obtaining valid counterfactuals is in general substantially more involved than flipping a single attribute independently of the others. In particular, we cannot meaningfully talk about counterfactuals without bringing clarity to what exactly we refer to in our causal model and how we can produce *valid* causal models. We turn to this important topic next.

## Validity of Causal Modeling

Consider a claim of employment discrimination of the kind: *The company’s hiring practices discriminated against applicants of a certain religion.* Suppose we want to interrogate this claim using the formal machinery developed in this chapter. At the outset, this requires that we formally introduce an attribute corresponding to the “religious affiliation” of an individual.

Our first attempt is to model *religious affiliation* as a personal trait or characteristic that someone either does or does not possess. This trait, call it *A*, may influence choices relating to one’s appearance, social practices, and variables relevant to the job, such as the person’s level of education *Z*. So, we might like to start with a model such as [figure 5.12](#chapter_5.xhtml#fig5-12).

![Figure 5.12Religion as a root node.](images/fig5-12.png)

[Figure 5.12](#chapter_5.xhtml#fig5_12)Religion as a root node.

Religious affiliation *A* is a source node in this figure, which influences the person’s level of education *Z*. Members of certain religions may be steered away from or encouraged toward obtaining a higher level of education by their social peer group. This story is similar to how in our Berkeley admissions graph *sex* influences *department choice*.

This view of religion places the burden on understanding the possible indirect pathways, such as *A → Z → Y*, through which religion can influence the outcome. There may be insufficient understanding of how a religious affiliation affects numerous other relevant variables throughout life. If we think of religion as a source node in a causal graph, changing it will potentially affect all downstream nodes. For each such downstream node we would need a clear understanding of the mechanisms by which religion influences the node. Where would such *scientific knowledge* of such relationships come from?

But the causal story around religion might also be different. It could be that obtaining a higher level of education causes an individual to lose their religious beliefs. In fact, this modeling choice has been put forward in technical work on this topic \[[32](#references.xhtml#ref-32)\]. Empirically, data from the United States General Social Survey show that the fraction of respondents changing their reported religion at least once during a four-year period ranged from about 20 percent to about 40 percent \[[189](#references.xhtml#ref-189)\]. Identities associated with sexuality and social class were found to be even more unstable. Changing one’s identity to better align with one’s politics appeared to explain some of this shift. From this perspective, religious affiliation is influenced by level of education and so the graph might look like [figure 5.13](#chapter_5.xhtml#fig5-13).

![Figure 5.13Religion as ancestor.](images/fig5-13.png)

[Figure 5.13](#chapter_5.xhtml#fig5_13)Religion as ancestor.
