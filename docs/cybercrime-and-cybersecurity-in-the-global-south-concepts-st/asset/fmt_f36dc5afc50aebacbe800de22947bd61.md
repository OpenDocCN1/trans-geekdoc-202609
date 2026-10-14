
| Ryan Cleary || Cyber-punks_Coders_Writers || Individual Aggressor || ConspiracyUnauthorized Impairment of Protected Computers || DDoS || Design Vulnerability |

| *Note*: **Class: *Subclass*** |

### 12.6.3 Evaluating Our CCO

To evaluate our CCO, as per the recommendation of [Peffers et al. (2007)](#ch12.xhtml#ref12_54), we compare the solution objectives with results of the artefact demonstration, shown in [Tables 12.2](#ch12.xhtml#table12_2), [12.3](#ch12.xhtml#table12_3) and [12.4](#ch12.xhtml#table12_4).

[Table 12.4 Evaluation of Our Artefact – Comparing the Solution Objectives with Our Artefact’s Demonstration Results](#ch12.xhtml#R_table12_4)

| **Solution Objective** || **Artefact Demonstration Result** |
| --- | --- |
| An explicit, shared conceptualization of cybercrimes classification for use by crime stakeholders || In developing our artefact, potential cybercrime classification characteristics and relationships were identified by police practitioners and researchers, representing a shared conceptualization of cybercrime classification. Since an ontology is a formal explicit specification of characteristics/concepts in a domain and the relationships that hold among them, our artefact then is an explicit, shared conceptualization of cybercrime classification. |
| A more comprehensive and holistic artefact that incorporates multiple cybercrime perspectives || Since our artefact consists of a more extensive set of cybercrime classification characteristics than prior works, and same successfully and accurately classified an `Attack_Event`, we argue that our artefact is more comprehensive and holistic. In fact, the results from sub-Section 6.2, Classifying and storing two real-world cyberattack events, support our claim. |
| A flexible artefact, better able to classify current and future `Attack_Events` || We use the characteristic structure design approach when developing our artefact. This permits the characterizing/classifying of any `Attack_Event` without regard for changing conditions and evolving technology, thus, is not easily outdated. Further, our artefact can easily and tidily classify blended `Attack_Events`, a limitation of some previously proposed classification schemes. |
| A formal CCO that could allow cybercrime agents (human or artificial) to share knowledge || An ontology facilitates knowledge sharing between human and artificial agents by providing a consensual and formal conceptualization of a given domain. *Formal* refers to the fact that an ontology should be machine-readable. Our artefact: (1) consists of a set of consensual characteristics that describe the cybercrime classification domain; (2) specify the semantics of the domain in terms of the conceptual relationships between characteristics; and (3) is formal, since it is implemented in Protégé OWL. |
| An extensible artefact that can easily accommodate new concepts and potential new relationships || As above, our artefact’s design is based on the characteristic structure design approach, which classifies properties about the `Attack_Event` and not the actual `Attack_Event` itself. Characteristic structure is analogous to the nucleotides of deoxyribonucleic acid (DNA) in that one or more of the characteristics of the `Attack_Event` can be linked together to describe the item that is being placed in a ontology. Thus, our artefact is extensible; new characteristics and potential new relationships are easily incorporated. |

## 12.7 Conclusion and Future Work

It is anticipated that cyber `Attack_Events` will become more prevalent in the future, thus every contribution towards improving our understanding of `Attack_Events` is critical. In this chapter, we present a knowledge-based artefact for classifying `Attack_Events`. Our CCO provides an explicit, formal specification of a shared conceptualization of cybercrime classification. We propose that any `Attack_Event`, known or new, can be successfully classified using these characteristics: `Attacker`, `Vulnerability`, `Tool_and_Technique`, `Objective`, `Offence`, `Location`, `Complainant`, `Target`, `Victim` and `Impact`.

While prior works have proposed classification schemes, our work offers improvement in several key areas, including: (1) it is flexible and extensible; (2) it offers a more robust classification scheme; (3) it effectively illustrates complex interactions between the ontological characteristics via associations that formally describe their relationships; and (4) because our artefact is ontological, it supports inferencing of new knowledge relating to cybercrime classification.

We have successfully demonstrated how our CCO can be used to classify and store two real-world `Attack_Events`. Our demonstration shows that all previously proposed classification schemes are able to classify cybercrimes but the classifications are incomplete. That is, they do not capture all pertinent information required to completely and effectively classify cybercrimes, however, ours do. Further, we show that given the same pair of concepts in our classification model and another study’s model, ours is able to answer queries relating to the concepts, yet, the others could not.

While we have designed a more robust cybercrime classification scheme, there are several issues that should be addressed in future research including:

*   The veracity of our artefact could be further validated by classifying additional cases of `Attack_Events`, of different types. For instance, `Attack_Events` involving groups as well as those exploiting vulnerabilities could be classified.
*   Also while we have applied the guideline of the DSRM to evaluate our artefact, it would be useful to conduct a more robust evaluation that involves implementing a prototype in a police organization for use by its CSIRT to classify reported cyber `Attack_Events`.
*   Further evaluation might also involve other researchers using measures such as those discussed in [Maes and Poels (2006)](#ch12.xhtml#ref12_45) and [Rao and Osei-Bryson (2007)](#ch12.xhtml#ref12_57) to assess stakeholders’ perceptions of the quality of the CCO; such studies could be done in various organizational settings.
*   The use of text mining and artificial intelligence technologies for automatic or semi-automatic instantiation of the contents of our CCO ontology as well as enrichment of our CCO ontology using news reports and other data (e.g. social media data) could also be explored by other researchers since various ontology population and enrichment methods have for some time been suggested (Richard [Gil & Martin-Bautista, 2014](#ch12.xhtml#ref12_23); [Petasis et al., 2011](#ch12.xhtml#ref12_55)).

Our work has implications for both research and practice. Our work can facilitate effective collaboration and meaningful discussions between scholars and practitioners of the domain since consensual definitions provide a common language; an agreed-upon classification scheme can improve cross-jurisdictional cooperation, information sharing and support the prosecution process of cyber criminals; assist law enforcement to investigate, fight and prevent cybercrimes by improving their understanding of the different aspects of cybercrime; and, disaggregating `Attack_Events` can invoke different policy responses, thereby, assisting policy makers to develop appropriate cyber policies and legal responses. Our ontology then should prove to be a more useful tool for cybercrime stakeholders.

## Acknowledgement

The material in this chapter previously appeared in Donalds, C., & Osei-Bryson, K. M. (2019). Towards a cybercrime classification ontology: A knowledge-based approach. *Computers in Human Behavior*, *92*, 403–418. doi:[https://doi.org/10.1016/j.chb.2018.11.039](https://doi.org/10.1016/j.chb.2018.11.039)

## References
