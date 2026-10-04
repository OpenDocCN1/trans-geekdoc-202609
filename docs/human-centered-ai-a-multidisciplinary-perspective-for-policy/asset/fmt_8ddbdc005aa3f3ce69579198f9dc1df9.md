
In terms of *transparency* as well as *accountability*, applying the framework already allows for concluding that the AI system in its current form does not satisfy the requirement of XAI (or general explainability), as it provides no further insight into why the agent has chosen a particular fee for a given CPZ. Beyond that, it also lacks an implementation of the human-in-the-loop concept during the training and inference steps. As indicated by [Figure 25.3](#ch25.xhtml#fig25_3), in its current form, there is no human input into the system’s operation. Consequently, city administrations aiming to implement the policy would have to introduce XAI methods into the process and opt for a different RL algorithm, such as learning from human preferences ([Christiano et al., 2017](#ch25.xhtml#ref25_4)), that accommodates human feedback. Furthermore, as detailed in the previous section, the final policy implementing the proposed system would have to be accompanied by transparent communication regarding the deployment of the system and its functioning, as well as a petition mechanism for the public to facilitate accountability.

At this early stage of the policy cycle, the final layer of the process level serves primarily as a to-do list of how to design the software engineering workflows as well as the audit and communication processes defining the AI system. In the case of our test policy, *reliability* might be of particular interest since reliability from citizens’ perspectives might be at odds with the volatile nature of the system’s pricing strategy.

### Output Level

Proceeding to the output of the policy, [Figure 25.5](#ch25.xhtml#fig25_5) shows the immediate effects of the pricing system on the model environment across four dimensions in comparison with the existing static scheme. Generally, the AI-based policy appears to significantly improve upon the status quo in terms of its ability to keep the utilized capacity of the curbside parking space within the desired range since its pricing succeeds in balancing over- and underutilization. Hence, the *desired results in the targeted area* are attained. Regarding *anticipated side effects*, the simulation run confirms that the policy disproportionately limits the accessibility of parking in the modeled city center, thus exhibiting a bias toward low-income individuals. Moreover, the policy also produced *unanticipated side effects* in the simulated environment.

Overall, based on this high-level analysis, the proposed AI-based policy does not conform to the concept of HCAI, as its internal process lacks both transparency and accountability, while its output shows evident bias. However, the introduced framework points to clear starting points for changes to the policy program that may result in it conforming in future iterations. Nonetheless, it is worth pointing out that a valid interpretation of these results may also conclude that a proposed policy is generally not suited for the intended purpose. In this test case, managing demand with dynamic prices equal across all income cohorts will most likely always disproportionately disadvantage those of low income. Therefore, alternative policies, such as banning car traffic in the city center entirely, may prove more attractive to policymakers.

## Conclusion

This chapter introduced a framework of guidelines for developing Human-Centered AI-based public policies to contribute to a structured and careful deployment of AI in the public sector. Based on existing literature on HCAI and policy evaluation, the framework allows for determining whether a policy intervention currently being designed or already implemented satisfies the core constructs that define HCAI. To demonstrate its potential use, we applied the framework to a simple model policy in a simulation setting.

Crucially, there are several limitations of our work to note. Due to space limitations, the framework covers multiple theoretical constructs and topics that are subjects of entire branches of research (e.g., AI transparency or XAI) in a high-level fashion. Instead of producing a detailed manual to be deployed in practice immediately, our aim was to offer an overview of theoretical concepts that can comprise Human-Centered AI in the public sector, pointing toward the experts in the respective fields. Therefore, our framework can merely offer general guidelines, which may serve as a foundation for more elaborate and practical processes (such as step-by-step instructions) developed together with stakeholders and policy practitioners to enable responsible deployment of AI in the public sector.

Finally, to further the research into if and how the public sector should make use of AI, we require a better understanding of the ways in which public institutions are already deploying the technology. Hence, more studies investigating current policy programs based on AI (in line with [Kuziemski & Misuraca, 2020](#ch25.xhtml#ref25_18); [van Noordt & Misuraca, 2022](#ch25.xhtml#ref25_43)) are needed to ensure that frameworks such as the one proposed here can be refined to both better reflect the realities of public sector operations and holistically evaluate the outcomes of public policies relying on AI. Furthermore, more theoretical research into how the regulation of AI use in the public sector is to be designed is required. While there is a prevalence of proposals of voluntary standards in the literature, more severe and enforceable measures might be required, as “even seemingly trivial applications of AI by the public sector can be an instrument of exercising control over the citizens” ([Kuziemski & Misuraca, 2020](#ch25.xhtml#ref25_18)).

## Acknowledgement

This research was conducted as part of the grant “Consequences of Artificial Intelligence for Urban Societies (CAIUS)”, funded by Volkswagen Foundation. We would like to thank the editorial team, workshop participants, as well as our colleagues Lea Cohausz and Frederic Gerdon for their helpful feedback to an earlier version of this chapter.

## Notes

1. [This development can also be seen as part of the proliferation of (new) policy instruments in governments (](#ch25.xhtml#R_en25_1) [Zehavi, 2012](#ch25.xhtml#ref25_54)) in recent times.

2. [The field produced a plethora of various terms for describing its methods](#ch25.xhtml#R_en25_2), ranging from “policy analysis” and “policy appraisal” to “policy evaluation” ([Wollmann, 2017](#ch25.xhtml#ref25_52)).

3. [While this framework was designed to accommodate the particular challenges of deploying AI in the public sector](#ch25.xhtml#R_en25_3), it could in theory also be used in private enterprises.

4. [Additionally](#ch25.xhtml#R_en25_4), the public perception of AI in government may vary across different contexts, rendering some high-stake applications of AI potentially too unpopular to pursue ([Kern et al., 2022](#ch25.xhtml#ref25_17)).

5. [This could entail if a generative parametric model is used](#ch25.xhtml#R_en25_5), interpreting its parameters, or even publishing the whole training data as well as the algorithm used.

6. [See](#ch25.xhtml#R_en25_6) [Shneiderman (2022)](#ch25.xhtml#ref25_36) for a detailed description. Since there is some overlap between the author’s framework and the one described in this chapter, the following remarks will focus on where both complement each other.

7. [Policy evaluation traditionally also focuses on establishing a causal link between the observed results and the designed policy (see](#ch25.xhtml#R_en25_7) [Vedung (2013)](#ch25.xhtml#ref25_45)).

8. [Said usefulness directly depends on the quality and external validity of the model of reality used](#ch25.xhtml#R_en25_8). For the model city that is the subject of this test case, it is assumed that the used simulation provides enough external validity to allow drawing conclusions based on it.
