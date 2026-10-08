# The Novel in the Spanish Silver Age

While the first two will be tackled together in the next section, descriptive metadata will be explained separately in Section 3.2.5.

Following the TEI Guidelines, I have encoded directly the metadata about texts and the collections in the TEI Header. This strategy provides me with the opportunity to encode various aspects using a shared semantic frame within the DH community. It also offers the possibility to match each specific information through attributes, like @cert (about the certainty of a specific information) or @source (to refer to a specific origin of data).

Each category and possible value of metadata was defined in a hierarchical taxonomy as the TEI XML document, addressing also type of information (nominal, ordinal, interval, or binary). In the case of ordinal classes, the names of the possible values were also inserted with their numerical position. For example, five values for different types of endings of the novel, varying from zero (clearly) to five (clearly happy). This file has been used for several purposes: On the one hand, to validate the metadata of the whole corpus using a Schematic, or to recategorize the fields (for example employing the numerical values of ordinal categories, or transforming numerical information into binary fields) for specific visualizations as the ones at the end of this chapter or employ them as features (Chapters 7.1 and 8).



Each text and author have been identified using the complete name, short name, and the identifiers of the Spanish National Library (BNE) and the Virtual International Authority File (VIAF). In this way, every text and author can not only be tracked within the corpus, but also as a part of other digital collections. About the sources of the text, I have gathered references regarding three different kinds of editions implicated in the genetic process of each text (all of them encoded inside an element sourceDesc/bib with different @types):

+   - Edition-first: The first time the work was published as a book (the date should be between 1880 and 1939).
- Digital-source: The digital source. If the text was digitized by the CLiGS, it collects also the year and the exact program used (FineReader, Recognition Server).
- Print-source: The printed edition taken as the base for the digital version.