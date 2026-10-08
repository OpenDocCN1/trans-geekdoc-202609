
# The Novel in the Spanish Silver Age

Figure 32: Protagonist gender over decades

![](img/98c86d70e9e43286af05120dbff29113_151_0.png)

axis stands for distinct ordinal metadata,¹¹⁶ with the gender differentiated through box plots.

The novels have similar endings for both genders, being slightly more optimistic with women (not in ConSSA-canon). Women tend to be younger than their male counterparts, a wider range of social classes (with more cases in the upper than in the lower levels). They have a stronger tendency to live in cities, and are not meant to appear in boats. One interesting aspect is the fact that male protagonists from lower or upper social classes are outliers (cfr. Johnson 2008, 161).

The last plot, Figure 34, shows the development of the types of endings during these sixty years. The most common case is a sad ending, which is perceptible throughout the period. The decade with the largest percentage of sad endings is the 1880s (the one dominated by naturalism), with almost 80% of the texts. After the decade of 1910, the number of texts with a neutral ending (neither completely sad nor happy) increases and remains the second most frequent type of ending. In the canonical version, texts have a tendency to become happier until 1920 (p-value of 0.03 in a linear regression analysis, further details in the Jupyter Notebook), returning to more pessimistic endings later. It is surprising that neither Spanish

Figure 33: Box plots differentiating values by the protagonist gender

![](img/98c86d70e9e43286af05120dbff29113_152_0.png)

Figure 34: Type of ending over decades

![](img/98c86d70e9e43286af05120dbff29113_152_1.png)

Civil War not the First World War seem to have a clear effect on the endings of the novels.

The last element I would like to discuss is a specific value given in many categories: unknown. As explained in Section 3.2.3, this value represents the same uncertainty in the different metadata types: The information cannot be known by humans using only the text as a source. There is a hypothesis about this period commonly mentioned in the novels leave the realistic frame, becoming more abstract, and many of its aspects turn further fuzier (Garcia Lara 1986, 209; Gullón 1994, 199; Aubert 2001, 11; Navajas 2008, 18). A change from realist to modernist and avant-garde novels would take place and therefore many actual references to locations or periods get blurred. For example, there are specific references to places or years in novels such as Niebla by Un-muno (cfr. Overvaas 1993, 60). The unknown value of metadata could be seen as a formalization of this phenomenon. Thus, if the hypothesis is true, the later decades could contain more unknown values. The results do not show significance (p-value of 0.13 in a regression analysis, 0.22 for the canonized version) with a slightly positive slope (p-value 0.004 in ConSSA and 0.003 in ConSSA-canon). That means that although texts do show a certain tendency to become fuzier, there is no empirical data to assert that novels become less specific within this period.

This description demonstrated the potential of metadata as a solid bridge towards distant reading. In general, the novels of this period are highly realistic, national, contemporary, male-dominated, and endl. The development of the analyzed texts of this period shows clear tendencies in both versions of the corpus: Novels become more male-dominated and autobiographical, and slightly less pessimistic. Female protagonists tend to be younger, their stories usually take place in cities and their endings are slightly happier, while male protagonists have a stronger tendency to be part of the medium class and have a wider range of type of settings.

# 3.3 Filtering the Corpus through Classification: Are all Texts in CoNSSA Novels?

In the previous chapters, the criteria for the composition of the corpus and its annotation using metadata have been presented. In Section 3.1.5, a problem has been highlighted: The genre of 10% of the texts of the corpus is unclear and this number includes some of the most important works of this period (by Machado, Ramón Jiménez, Gómez de la Serna, Baroja, etc.). Are these novels, or do they belong to the essay, to journalistic texts, or to theater or poetry? This question should be answered before moving on to the analysis of subgenres in the rest of the publication. In a manner, this chapter proposes that 14 texts belong to the category of novels. To try to falsify this, I apply classification using CORDE as the data set, the largest existing historical corpus for Spanish, created by the Real Academia Española. First, I will evaluate the parameters (transformations of lexical information, algorithms, and number of lexical features) of the classification of the different genres in two different tasks: multi-label (each text belongs to each genre) or multi-class (each belongs to a single genre). Next, I will use the prediction function of the best combination of parameters to classify the genre of the texts of disputed genre, both as multi-label and multi-class tasks. Finally, I will discuss the results and modify the corpus for the rest of my research study.

As mentioned before, in this chapter I use the largest historical corpus for Spanish: CORDE. In 2002, the Real Academia Española (RAE) launched two corpora: the first with historical texts (Corpus Diacrónico del Español, CORDE and the second with contemporary material (Corpus de Referencia del Español Actual, CREA). In the original plan, the contemporary corpus, CREA, would cover the most recent 25 years, while CORDE would assimilate the rest of the texts that could be considered historical (i.e. older than 25 years). Hence, the boundaries of both corpus would move each year. This plan was dropped with the creation of a new corpus, CORPES, covering the 21st century and adding new texts every year. As a result of this, the original corpus were frozen in their development.

In its final version, CORDE contains around 300 million tokens and more than 34,000 texts, with material from the Spanish-speaking corpora (74% coming from Spain), in different genres and topics (which will be explained later in more detail), including an important fraction of literary works. The texts were first published or written between 759 (with only two instances from the 8th century) and 1974 (Sánchez Sánchez and Domínguez Cortés 2007). Its goal is to offer a representative sample of the language for researchers (Sánchez Sánchez and Domínguez Cortés 2007, 143). The standard use of CORDE and CREA is through two websites, where the researcher can run queries in the corpora. Although accepted and used as a standard tool by Hispanists (Kabatek and Pusch 2011), some researchers have pointed out several bibliographical problems of the corpus, especially in the medieval section (recently discussed by Rodríguez Molina and Oviedo de Toledo Huerta 2017).

Until recently, the RAE has been reluctant to give access to the full version of the corpus or other formats of the data, arguing copyright issues relating to the editions of the texts. For this research, I contacted the department of the RAE responsible for these corpora, requesting the frequencies of each document with any annotation of the document (or metadata). They agreed, and for that I am deeply grateful and hope to give an example of the kind of analysis that could be undertaken not only through the browser interface. In fact, some months later, the institution opened the opportunity to request the frequencies and metadata, in this form:

```
<TITULO>El caballero de Medina</TITULO>
<AUTOR>Cruz, Ramón la</AUTOR>
<PAIS>España</PAIS>
```

# 3.3 Filtering the Corpus through Classification: Are all Texts in CoNSSA Novels?

<FEACHRE> 1764 </FEACHRE>
<TEMA>Verso dramático: Profano</TEMA>
<MEDIUM>Libro</MEDIUM>
Número de formas ortográficas: 2951
Número de elementos (tokens): 3940
Número de elementos distintos (types): 1086
400
236
153
...

From this material, the first step is to extract and clean the metadata, differentiating different types of information that have not been separately decoded The genre and subgenre information is mainly extracted from the first value of the TEMA element (in the previous example, its genre is Verso dramático), but also differentiates novels and letters (two genres that are encoded as the second value). Besides, some subgenres are merged to their small size, as short and long dramatic verse, combining them in a general dramatic verse category. The few steps for the normalization of the genre can be easily tracked on the Jupyter Notebook of this chapter. At the end, 19 different emerge:

- Artes y espectáculos
- Biografía-Autografía
- Ciencias exactas, físicas, naturales y aplicadas
- Ciencias sociales y humanidades
- Cartas y Relaciones
- Historia y documentos
- Novela y otras formas similares
- Prensa
- Prosa didáctica
- Prosa dramática
- Prosa lírica
- Prosa narrativa breve
- Prosa narrativa extensa
- Religión
- Sociedad
- Verso dramático
- Verso lírico
- Verso narrativo

Some of these labels do not constitute a genre per se, for e.g. arts and spectacles or religion, which constitute a group of technical texts on these topics.

¹ For example, the redaction or publication was sometimes encoded between two years, before or related to a specific year.
² It also contains an empty category that seems to be a mistake in the original data.
