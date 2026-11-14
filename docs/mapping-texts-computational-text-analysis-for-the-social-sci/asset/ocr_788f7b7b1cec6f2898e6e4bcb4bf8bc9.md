the increasing availability of large amounts of texts, scholars quickly encounter the problem of excess (Chakrabarti and Frye 2017). This becomes untenable with tens of thousands or millions of documents. Furthermore, we encounter conceptual drift (Chakrabarti and Frye 2017). As we read more documents, we may alter our understanding of a concept. As a result, our labeling of documents read earlier misaligns with our labeling of documents read later. Re-reading and re-labeling are one solution to this problem. Multiple re-readings, however, become impractical with thousands or millions of documents. This is where automated techniques can augment interpretive coding.

4 Despite differences, both typically include selecting a vocabulary.

There are two automated approaches we’ll discuss here: (1) discrete indicators and (2) weighted indicators. Both rely on dictionary and rule-based procedures to tag or weight a given document by its engagement with a concept or entity of interest.4

Most researchers use keywords with search engines to collect primary documents and scholarly literature. Once collected, we use the “find” function to search for keywords in texts. Both tasks use vocabulary and rule-based string matching. If we are interested in, say, “political attitudes of working-class youth in Seattle,” we’d collect recent scholarly articles discussing “political attitudes and class,” or “political attitudes of youth” or “political attitudes and Seattle,” etc. We may actively discard articles without such keywords or allow the databases’ search engine to omit these. Even if somewhat unsystematic, these are deductive procedures.

5 We reserve “entity” for more concrete referents, like people or organizations as in Named-Entity Recognition.

Content analysts use several terms to denote a unit of meaning in text. These include themes, thematic units, categories, codes, labels, expressions, and more. Researchers may arrange these into a hierarchical classification scheme with, for example, higher-order categories encompassing lower-order themes. We’ll simplify things by using concepts or categories for deductive approaches and topics or themes for inductive approaches.5 We do not wish to overlook the potential theoretical use of keeping these many terms distinct; however, the strategy used to measure a unit of meaning often remains the same: Are certain terms, phrases, or relations denoting a given meaning present and, if so, to what extent?

+   THIS SECTION NEEDS:
+   * tidyverse
+   * quanteda
+   * Matrix
+   * irr

# DISCRETE INDICATORS

A basic discrete indicator is noting the absence or presence of certain concepts or entities in texts. For example, do articles in sociology journals mention “nuance” or not (Healy 2017:120). We call this “binary” as we can use a zero for absent or a one for present (or Boolean and use