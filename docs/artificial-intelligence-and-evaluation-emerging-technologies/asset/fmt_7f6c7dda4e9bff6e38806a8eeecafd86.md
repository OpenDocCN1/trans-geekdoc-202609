
## Second portfolio identification using supervised NLP

The list of 372 projects (of which 131 were identified as being DB-informed) that had previously been manually reviewed was used as a training sample for an ensemble of supervised text classification models.

## Supplementary keyword searches

Additionally, IEG developed a more general search taxonomy.

## Final portfolio identification

Cut-off values for the model-generated probabilities and the "relevance scores" were used to generate a long list of projects which were to be manually reviewed by team members to determine which ones were DB-informed. That is, a project could be included in this long list because of a high probability assigned by the models or because of a high number of results from the keyword searches in the PDOs and full documents. The cut-off values for the model probabilities and term frequencies were determined by the team while keeping in mind the trade-off between the completeness of the portfolio identification and the time required for manual review. As a result of this step, an additional 226 projects were identified for manual screening, from which another 138 DB-informed projects were identified and added to the final portfolio.

### What We Can Learn

First, the approach played a pivotal role in the team's precise identification of the evaluand, laying the groundwork for the relevance and effectiveness assessments in the evaluation's portfolio analysis. By leveraging text mining and machine learning techniques, the team was able to double the size of the evidence base (of relevant projects and their documentation), which would have likely been impossible with traditional portfolio identification approaches. Doubling the evidence base enhanced the breadth and validity of findings from subsequent analyses.

Second, IEG experienced that developing a sizeable and high-quality training dataset can be challenging. Resource limitations impose constraints on both the size and quality of the training data that can be produced. Consequently, this impacts the precision and accuracy of outputs from supervised NLP models, which typically demand ample high-quality training data.

Third, close communication between the data scientist and evaluators is essential to develop a shared understanding around the application. Over time, as evaluators and data scientists develop a better understanding of each other's work, jointly working on data science applications becomes easier.

Fourth, investment of time and resources in innovative data science applications eventually pays off. The classification models developed for this task were reused in another IEG evaluation (World Bank, [2022](#c5.xhtml#re_TNFUK_05_AREV_C005-CIT000047), p. 93). Furthermore, the same model development could be applied to other tasks in other evaluations.

Fifth, this particular exercise constituted an early pilot in IEG in the use of supervised text classification for portfolio identification, which helped to demonstrate the utility of the approach.

## Example 2: Portfolio Monitoring and Analysis Using NLP: Human Capital Project Just-in-time Note

### Context of Use

This analysis was conducted as part of an evaluative exercise titled "Monitoring a multifaceted agenda: A Just in Time Note on the footprint of the Human Capital Project on the Human Development portfolio." This note aimed to trace the footprint of the Human Capital Project (HCP).

More specifically, the analysis sought to test two main hypotheses. If the HCP has provided an impetus to pursue specific human capital outcomes and embed multisectoral activities in the HD portfolio to advance the human capital agenda, then the following patterns might be observed: a quantitative increase in the number of operations that pursue specific human capital outcomes that are at the core of the HCP, and a qualitative shift in the design of HD operations with further emphasis on key human capital outcomes and cross-cutting themes that are promoted by the HCP (e.g., gender equality, digital solutions, human capital measurement, and institutional strengthening). Within this conceptual framework, the analysis aimed to answer the following questions: (a) did the size of the HD portfolio increase with the introduction of HCP, (b) did the design of the HD portfolio become more focused on pursuing specific human capital outcomes core to the HCP agenda, and (c) did the HD portfolio become more focused on cross-cutting themes core to the HCP agenda?

A potential approach to gather data to answer these questions is traditional PRA. This approach relies on WB sector and theme codes (World Bank, [2016](#c5.xhtml#re_TNFUK_05_AREV_C005-CIT000045)) to identify projects with the desired focus and then proceeds with a manual review of each project. This conventional approach can be effective for portfolio monitoring tasks on topics that are well aligned with the WB's sector or theme taxonomies.

However, for many PRA tasks there is no crisp alignment with the existing sector or theme taxonomies, making conventional approaches either particularly inefficient and costly (due to the need for extensive manual review) or inaccurate (due to inconsistency in coding). This approach tends to yield both errors of inclusion and errors of exclusion. Besides this issue of alignment, there are also other issues with the tagging of WB projects to the sector and theme taxonomies that lead to inaccurate data. For example, one major issue is the lack of incentives for teams working in one domain to tag their projects to other domains that are outside of their purview. Over the years, IEG evaluations have documented various instances where this incompleteness in the tagging of projects to the sector and theme codes has been addressed using search taxonomies to identify projects by string searches.

### How the Application Contributes to Answering the Questions/Doing the Task

Given the increasing cross-sectoral and multidimensional nature of the HCP portfolio, the reliance on sector and thematic codes using a traditional PRA approach would not have been sufficient to accurately and efficiently identify the HCP footprint on the HD portfolio. To circumvent the limitations of traditional PRA, IEG developed a novel approach which builds on a rigorous application of supervised NLP to identify trends in the HCP portfolio.

### How It Was Done

The HD portfolio under consideration consisted of 984 lending operations. To be able to answer the questions outlined above, the portfolio was segmented into two time periods, a before-HCP period (FY15-FY18) and an after-HCP period (FY18-FY20). It was also segmented into two country groupings: countries that had joined the HCP by October 2018 (HCP countries) and countries that had still not joined by then (non-HCP countries). [Figure 5.2](#c5.xhtml#f5.2) illustrates the composition of the HD portfolio selected for this application.

![Figure 5.2 Initial portfolio composition. ¶ Source: Independent Evaluation Group.](images/fig5.2.jpg)

[*Figure 5.2*](#c5.xhtml#re_f5.2) Initial portfolio composition. ¶ *Source*: Independent Evaluation Group.

The sequential steps used to complete this task are outlined below. [Figure 5.3](#c5.xhtml#f5.3) illustrates this process schematically.

![Figure 5.3 Text classification process. ¶ Source: Independent Evaluation Group.](images/fig5.3.jpg)

[*Figure 5.3*](#c5.xhtml#re_f5.3) Text classification process. ¶ *Source*: Independent Evaluation Group.

### Initial portfolio split

This portfolio was split into two sets: (a) a set of 183 projects, which was manually coded and used to build training and testing sets for the NLP model, and (b) a set of 801 uncoded projects for which the team aimed to predict codes by applying an NLP classification model.
