
In the US, the membership of the American Sociological Association (2021) was 53.9% women, 44.2% men, and 1.9% trans or non-binary in 2020. But, there are fewer authors classified as “female” and “male” in this volume of the *Annual Review of Sociology*, indicating that male sociologists may be overrepresented in major publications. Drawing on lessons learned in **Corpus Building**, though, we must also consider that the *Annual Review of Sociology* is not a typical scholarly journal because authors are invited.

Now, imagine we have tens of thousands of articles with tens of thousands of authors. Keeping in mind potential measurement error, automated gender tagging may be the only feasible option. Even so, we’ll want to keep Mullen et al.’s words of caution in mind and be sure to discuss these limitations when sharing our findings with our communities.

## Named-Entity Recognition

Sometimes we need to know who, or what, is being discussed across texts in a corpus. If we know a fair bit about our texts—or if we want mentions of specific entities—then perhaps we could build a custom dictionary consisting of entity names and use that to identify how frequently each text “name-drops” these entities. For example, how frequently do Republican presidents mention the Democratic Party in their State of the Union (SOTU) addresses (and vice versa)? We can just count the times the SOTUs mention these exact two-word phrases.

What if we know little about the people or organizations that texts in a corpus might be mentioning? Then we can use **named-entity recognition (NER)**. NER taggers input text documents and return the “entities” found in those texts: for example, people’s names, organizations, locations, and dates, to name a few. NER is useful for information extraction problems and also for helping construct dictionaries because it can be used to identify the people, places, things, etc., that are referenced most frequently in a corpus.

NER is increasingly used in the social sciences. We (Stoltz and Taylor 2017) used NER to identify protest events in newspaper data and run multilevel models with news stories nested within events. Mohr and colleagues (2013) used NER to locate the major geopolitical actors in US National Security Strategy documents. Van de Rijt and colleagues (2013) used NER in the Lydia text analysis system to model fame turnover in newspapers, and Shor and colleagues (2015) used the same system to study the gender gap in media coverage over time.7

- THIS SECTION NEEDS:
  - tidyverse
  - entity
  - tidytext

> 7 For more examples of NER applications in social science, see Shor and colleagues (2014), and Traag and colleagues (2015). For a discussion of using NER as a pre-processing strategy for further analysis, see D'Orazio and colleagues (2014:230–231).

In what follows, we'll first address—in a general sense—how NER works. We'll then provide a demonstration of NER tagging in R.

## How Named-Entity Recognition Works

Consider the following text (adapted from Mack 2019). NER taggers that are optimized correctly should return these “named entities” and the entity tags to which they belong, like so:

> Star Trek: Picard, which debuted in January 2020 [Date/Time] on CBS [Organization] All Access, saw Patrick Stewart [Person] reprise his role as the noble leader more than 20 years after Star Trek: Next Generation ended. The trailer for the new show showed Picard retired at a vineyard on Earth [Location], but feeling out of place and longing for space travel.

In this example, there are four entity taggers: ones that identify person names, organization names, dates/times, and locations, respectively. These are common entity tags, but this varies by the specific NER tagger used. entity also has taggers for money and percentages. The Stanford NLP Group’s CoreNLP library comes with more, including nationality, religion, and even cause of death (Manning et al. 2014).

How NER algorithms “learn” to identify entity tags varies. They all rely on training data. These training data are sentences that have already been tagged by a human (or set of humans). For example, training data for a “person name” tagger would look like this:8

8 The training data format must match the software being used. For the OpenNLP library, there must be one annotated sentence per line (Apache 2020).

```
The CEO of Apple, <START:person> Tim Cook <END>, unveiled the new iPhone. Mr. <START:person> Cook <END> was joined on the stage by Chief Operating Officer, <START:person> Jeff Williams <END>.
```

The training file would need to contain at least 15,000 line-separated annotated sentences (Apache 2020).

So, the training documents are parsed by sentence, separated by line breaks, and the names are hand-labeled. A model then iterates through pre-specified context variables—what is called a “feature set” (Apache 2020).9 Some context variables might include: Is the word capitalized? Does the word follow a prefix such as “Mr.”, “Mrs.”, or “Dr.”?

9 NER models typically have pre-specified context variables, but we can provide custom feature sets.

10 The OpenNLP NER tool uses generalized iterative scaling for this.

The algorithm uses co-occurrences between the tagged words and the context variables to develop a weight for each variable indicating the strength of the association between that variable and a class—here, either “is a person” or “is not a person.”10 The output of any NER model are weights—that is, the “importance”—for each of the context variables.

The trained NER model can then be used to predict the entity classes in new, unannotated texts.11 The NER model we'll use is **pretrained**. So, no annotated training data are necessary. The OpenNLP NER model appears to have been12 trained on 318 *Wall Street Journal* articles forming the training set for a series of NLP evaluation tasks at the Sixth Message Understanding Conference (MUC-6) (Nouvel et al. 2016:61).

11 This is done with maximum entropy (“maxent”) modeling in the case of OpenNLP.

12 The OpenNLP training data was difficult to ascertain. We sleuthed the MUC-6 data from a 2010 discussion post by Joern Kottmann on the OpenNLP SourceForge repository.

## Named Entities in R

The package we'll use for named entity recognition is entity.13 It is an R “wrapper” for the Java-based OpenNLP library maintained by the Apache Software Foundation.14 Let's use the *Star Trek: Picard* paragraph as a quick illustration (output in the margin):

```
para <- "Star Trek: Picard, which debuted in January 2020 on CBS All Access, saw Patrick Stewart reprise his role as the noble leader more than 20 years after Star Trek: Next Generation ended. The trailer for the new show showed Picard retired at a vineyard on Earth, but feeling out of place and longing for space travel."

person_entity(para)
organization_entity(para)
location_entity(para)
date_entity(para)
```

All entities were identified and correctly tagged.

Let's work through a larger example with the CMU Political Blogs Corpus (Eisenstein and Xing 2010). These blog posts from six political blogs were collected in 2008. Three of the sources are liberal-oriented (*Digby*, *ThinkProgress*, and *Talking Points Memo*) and the other three are conservative-oriented outlets (*American Thinker*, *Hot Air*, and Michelle Malkin's blog).

13 If entity won't download from CRAN, try installing from the maintainer's GitHub: trinker/entity.

14 We also need Java installed on our machine.

```
[1] "Patrick Stewart"
[1] "CBS"
[1] "Earth"
[1] "January 2020"
```

We'll use a random sample of 100 blog posts. When we read it into R, we'll also assign it to an object with a shorter name to save some space, but this is not necessary. Let's look at a portion of one of the shorter posts, which comes from *Hot Air*:15

15 We could not track down the original author of this blog post.

```
data("corpus_cmu_blogs100", package = "textmap.corpora")
blogs <- corpus_cmu_blogs100 # rename it so it's tidier
blogs$text[[46]]
```

[1] "John Edwards got shunned by Democrats at this convention for his extramarital affair with Rielle
