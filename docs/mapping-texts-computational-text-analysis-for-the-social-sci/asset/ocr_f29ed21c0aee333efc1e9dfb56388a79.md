In the US, the membership of the American Sociological Association (2021) was 53.9% women, 44.2% men, and 1.9% trans or non-binary in 2020. But, there are fewer authors classified as “female” and “male” in this volume of the *Annual Review of Sociology*, indicating that male sociologists may be overrepresented in major publications. Drawing on lessons learned in **Corpus Building**, though, we must also consider that the *Annual Review of Sociology* is not a typical scholarly journal because authors are invited.

Now, imagine we have tens of thousands of articles with tens of thousands of authors. Keeping in mind potential measurement error, automated gender tagging may be the only feasible option. Even so, we’ll want to keep Mullen et al.’s words of caution in mind and be sure to discuss these limitations when sharing our findings with our communities.

# Named-Entity Recognition

Sometimes we need to know who, or what, is being discussed across texts in a corpus. If we know a fair bit about our texts—or if we want mentions of specific entities—then perhaps we could build a custom dictionary consisting of entity names and use that to identify how frequently each text “name-drops” these entities. For example, how frequently do Republican presidents mention the Democratic Party in their State of the Union (SOTU) addresses (and vice versa)? We can just count the times the SOTUs mention these exact two-word phrases.

What if we know little about the people or organizations that texts in a corpus might be mentioning? Then we can use **named-entity recognition (NER)**. NER taggers input text documents and return the “entities” found in those texts: for example, people’s names, organizations, locations, and dates, to name a few. NER is useful for information extraction problems and also for helping construct dictionaries because it can be used to identify the people, places, things, etc., that are referenced most frequently in a corpus.

NER is increasingly used in the social sciences. We (Stoltz and Taylor 2017) used NER to identify protest events in newspaper data and run multilevel models with news stories nested within events. Mohr and colleagues (2013) used NER to locate the major geopolitical actors in US National Security Strategy documents. Van de Rijt and colleagues (2013) used NER in the Lydia text analysis system to model fame turnover in newspapers, and Shor and colleagues (2015) used the same system to study the gender gap in media coverage over time.7

+   THIS SECTION NEEDS:
+   * tidyverse
+   * entity
+   * tidytext

> 7 For more examples of NER applications in social science, see Shor and colleagues (2014), and Traag and colleagues (2015). For a discussion of using NER as a pre-processing strategy for further analysis, see D'Orazio and colleagues (2014:230–231).