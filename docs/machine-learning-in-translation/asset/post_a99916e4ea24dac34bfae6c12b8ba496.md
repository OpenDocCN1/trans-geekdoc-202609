
human TQA, and, as discussed previously, each industry standard has its own specific focus. Thus there is no one-size-fits-all solution that applies to all scenarios in TQA for MT.

For this reason, this chapter focuses on fundamental considerations that can support users making decisions about customizing their TQA strategies. For example, the application of MQM can be considered a specific scenario to make the assessment results more comparable across various projects and companies, whereas BLEU is used for MT system development and customization. Furthermore, this chapter focuses on the assessment of translated content. Theoretically speaking, all TQA metrics are potentially applicable to scenarios with both human and machine translation. As long as the approach, whether based on automated or human metrics, is utilized consistently, the assessment result will be useful.

## 5.2 Fundamental TQA considerations

### 5.2.1 Retrospective and prospective approaches

House (2014) proposed that there are different ways of assessing (retrospectively) the quality of a translation and different ways of ensuring (prospectively) the production of a translation of specified qualities. This dichotomy is based on time. When the element of time is incorporated into TQA, two fundamental aspects are introduced: quality assessment metrics, including automated and human direct assessment, for the evaluation of completed translations, and methods that help predict the quality of translation. The latter can support the development of effective, situation-driven editing strategies for translation tasks.

### 5.2.2 Linguistic relationships

Among assessment theories in translation studies (e.g., Chesterman, 1994; House, 2014), a relevant consideration in the context of MT is the concept of linguistic relationships. As Chesterman (1994, p. 153) points out, quality assessment was initially retrospective; it evaluated the relationship between the translated text and its source text, and the source text (plus its author) was taken to be the ‘authority’. The goal of translation was a relation of equivalence between source and target text – however equivalence was defined. Chesterman (1994) incorporates the concept of norms (see also Toury, 1995) into his framework and proposes an approach to quality assessment that aims to compare “a given product (or process) to the accepted relevant norms” (p. 153). He points out that this mode of assessment is “objective, text-based, formal, eminently practical, and furthermore manifestly realistic” (p. 153).

As to what norms are considered to be accepted and relevant, specific circumstances must be considered. An extreme case might be the quality assessment of a localized website based upon the customer conversion rate. In this case, business considerations, rather than linguistic features, are prioritized. There are other norms that can be considered, e.g., ISO 17100:2015(en) and ISO/TS 11669:2012(en) focus on services and projects, respectively. This chapter focuses on linguistic relationships, which are the basis of automated and many human assessment metrics.

The concept of linguistic relationships entails a comparison of a text against a reference. Generally speaking, the basis for an automated evaluation metric is a previously completed human translation, as the purpose of machine translation is to generate output that is understandable and readable by humans. By comparing the output of a machine translation engine against a human reference translation, it is feasible to measure factors such as linguistic quality, word order, and other textual features.

Linguistic comparison turns out to be very applicable to the use of automated metrics for MT quality assessment. This approach turns a TQA problem into a linguistic analysis task: evaluating the nature of the relationships between the linguistic features of two sets of texts. As Miller and Beebe-Center (1956) pointed out in their pioneering work:

> The excellence of a translation should be measured by the extent to which it preserves the exact meaning of the original. But so long as we have no accepted definition of meaning, much less of exact meaning, it is difficult to use such a measure. As a practical alternative, therefore, we must search for more modest, yet better defined, procedures. (p. 1973)

They then propose comparing criteria in test translations using a variety of statistical indices. The simplest thing to try first is to ask if they use the same words (p. 76).

The linguistic comparison approach in TQA is language independent. Even though the comparison is linguistic, comparing similarities of words in the reference translation and the MT result, the method of comparison is statistical: how many words or phrases are exactly the same, for instance, between a human translation and an MT result for the same source text? What is important is the statistic; the comparison provides an impression of the quality of the MT results without the need to understand the language(s). The statistical approach can be applied to any language pair.

To some degree, linguistic comparison in MT evaluation emphasizes linguistic more than translational aspects, in the sense that the approach can be applied to natural language processing tasks beyond MT quality assessment. For example, Yeong et al. (2019) employ Bleualign, which uses BLEU scores as a similarity metric to match sentences in the alignment task.

Most automated metrics are based on linguistic comparison and thus evaluative – when a framework is used to compare and find relationships, it usually involves a judgment as to which is better than the other. This might explain why the term MT quality evaluation is widely used in the community of MT system development. In natural language processing research, quality assessment is broadly known as evaluation and includes both human judgment-based and automated methods, and prioritizes how the progress of an intelligent system, such as machine translation, is measured (see Smith, 2019).

### 5.2.3 Different automation scenarios in TQA

Machine translation quality assessment can be carried out by humans and machines. If it is conducted solely by machines, using fully automated metrics for MT (e.g., BLEU and TER), there is no need to incorporate a human-oriented assessment framework, such as MQM. These error categories are designed primarily for humans, following their thinking patterns, to categorize and annotate errors appearing in translations. These human judgment-based quality frameworks can be considered human metrics, even though further data collection and analysis, e.g., categorizing and counting errors and generating a final quality score, can be automated. This distinction is important, as the methods and procedures of applying an automated metric are different from those involving human judgments of translation quality.

### 5.2.4 Factors in the TQA workflow

Many factors in the TQA workflow may affect the quality of an MT system, or an MT-driven localization process. One approach to TQA is to assess relevant aspects at various MT implementation stages, including the following:

- before MT: the quality of MT-related strategic decisions for a specific use case in terms of translation purposes, audience, available human resources and linguistic assets, language pairs, and domain identification.
- during the pre-processing stage: the quality of preparations for the use of MT in terms of source text extraction, segmentation, data cleaning, and data synthesis.
- during the MT stage: the quality of implementation of other MT-related tasks, such as translation memory incorporation and terminology integration.
- during the post-translation stage: the quality of post-editing, in-context review, terminology, and translation memory updates.

Each step includes numerous options to consider. For example, in order to convert a source text to a machine-friendly format, it needs to be segmented at a predefined linguistic level, such as sentences. For some content formats, this task can be easily done in some languages by referring to punctuation. However, under some circumstances, it is hard for a machine to decide on the boundaries of a piece of text input, for example, in pdf formatting and other forms of graphic design, there are layers that are hidden intentionally from human eyes. What a machine perceives varies from what humans see. For example, with a brochure containing pictures and text, a design objective is to make the content appealing, rather than ensuring
