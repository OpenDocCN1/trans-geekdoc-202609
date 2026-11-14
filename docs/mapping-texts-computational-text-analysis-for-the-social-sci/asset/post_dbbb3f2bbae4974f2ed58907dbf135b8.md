
may look like an “error” to some is intentional and thus meaningful to that language community.18

18 Of course, there are unintended misspellings as well as errors arising from optical character recognition (see Acquiring Texts) and encoding problems (see Wrangling Words).

## Genres and Topics

As we delimit further, we arrive at more specific conventions regarding the content of a given text. Knowing that a given selection is science fiction, for instance, we can make inferences about the content of the text, but likely not the media—this could be subtitles of a popular streaming series or chapters from a book series. At the level of genres and topics, we no longer attempt to impose a mutually exclusive classification scheme atop our text. Any selection of text may be placed in multiple genres or engage with several topics at once (Fowler 1982:37).19 Even within this dimension of variation are levels of generality. Fiction and non-fiction are among the most general. Philosophers and literary theorists have debated this distinction for millennia, but it still provides useful guardrails when building a corpus.20 This is because genres and topics tell us something about the community and context of a text—hints about the intents and desires of authors and audiences. They inform the “substantive hunch” (Martin 2001) that animates our analysis.

19 As Derrida (1980) explains: “Every text participates in one or several genres, there is no genreless text.”

20 Aristotle (1907:35) states: “The work of Herodotus might be put into verse, and it would still be a species of history, with meter no less than without it.... Poetry, therefore, is a more philosophical and a higher thing than history: for poetry tends to express the universal, history the particular.”

## Registers and Styles

In the same way as genres and topics cut across media, domain, etc., so do register and style. Register is commonly equated with formality. For example, in Turkish and French it is common to speak in the plural to indicate a level of social distance, and in Shakespeare, “thou” is informal and singular while “you” is formal and plural. In addition to formality, register typically includes perspective—first-, second-, third-person, but may also incorporate broader linguistic elements such as grammar and vocabulary.

The sociologist Basil Bernstein studied the distinct class-related “registers” of talk, which he divided into elaborated and restricted “codes.” In extreme cases of restricted codes of talk, what is being said is “wholly predictable for speakers and listeners” (2003:126). His examples here are religious services or types of storytelling. He argued that the identity of working-class folk in London in the 1950s was so thoroughly shared—because “of their common occupational function and social status”—this “reduces the need to verbalize intent so that it becomes explicit” (2003:111–3). Speaking is fast and condensed. So, he concludes that working-class people speak in a more restricted register than those in the middle class.

What is the difference between register and style then? To simplify a large literature: style is usually reserved for the more idiosyncratic linguistic regularities associated with an author—or perhaps an organization or other collective producer.

## REDRAWING BOUNDARIES

Depending on our research query, and the sources of variation we are using to balance or delimit, it is perfectly reasonable to redraw the boundaries of existing corpora by removing documents or including documents from multiple sources (see Tables 2.1 and 2.2). This highlights the place of inference in scholarly text analysis.

## Table 2.2: Selection of Text Sources

| News and Online Media | Political, Legal, Scholarly | Non-Fiction and Fiction |
| :--- | :--- | :--- |
| NYT's annotated corpus | State of the Unions | Movie subtitles |
| NYT California Digital Newspapers | European Parliament | Google Books N-Grams |
| Lexis Nexus and ProQuest | Campaign speeches | Hathi Digital Trust |
| All the News Corpus | Caselaw Access Project | North American Slave Narratives |
| Reddit, Twitter, Facebook blogs, forums, emails | PubMed | Malawi Diaries |
| Wikipedia, Fandom, SongGenius | JSTOR | Woman Suffrage Movement Biographies |
| | arXiv, SocArxiv, PsyArxiv | US Novel corpus |

Say we randomly sample US TV scripts in the 2000s. We find Asian and Pacific Islander Americans (APIAs) characters have fewer speaking roles. We could, perhaps, infer this to all US TV scripts in the 2000s. If, instead, we are interested in the depictions of APIAs characters in US media, such as the “model minority myth,” we may restrict our selection to shows with “recurring [APIAs] characters that develop in depth and complexity over time” (Deo et al. 2008:150). If we wish to focus on *influential depictions*, we may further delimit our selection to the most popular shows airing during “primetime.” This is not a random sample. This is a purposive selection. The first follows a similar logic to that of sampling in traditional survey research, while the second follows the approach common to case studies.21

21 Small (2009), drawing on, Mitchell (1983), Yin (2009) and Zmaniecki (1934), calls this **statistical inference** as contrasted with **logical inference**.

But first, we must consider how a given source relates to our research question. In this sense, corpus building is selecting a case. In practice, this is an ouroboros, with no clear start and finish (Nelson 2020; Brandt and Timmermans 2021; Wagner-Pacifici et al. 2015; Pardo-Guerra and Pahwa 2022; Ignotow and Mihalcea 2016:25–27). Luckily, computational methods are perhaps uniquely suited for the iteration that text analysis demands.

## 3

## Computing Basics

> The Analytical Engine has no pretensions whatever to originate anything. It can do whatever we know how to order it to perform. —A. Lovelace

Computing is about conventions more than numbers. Here, we present those conventions, explain computing concepts, define some jargon we'll use, and highlight common errors. This chapter will also give those without programming experience a place to start. For those already familiar with R, we also lay out all the packages we'll need to install.

## BRASS TACKS

Computers are simple creatures. Ambiguity is the computer’s natural enemy. Code is a set of instructions designed to stamp out ambiguity. The computer follows our instructions and, if all is clear, it performs whatever task we intended. Like natural languages, programming languages have family trees, meaning they are related to, and draw on, earlier languages.1 We can classify programming languages by their general features. R is an object-oriented, procedural, and functional programming language: we perform data procedures on objects using functions. These objects are different data types arranged in data structures. Functions are either included in base R, created during the session, or available in “packages.” Packages must be installed on our machines and loaded during each session.

1 For example, R (Team 2021) is the open-source progeny of S, itself influenced by Fortran and Scheme (of the Lisp family).

## Coding Environments

Computers comprise three “layers.” At the top is the GUI or Graphical User Interface. Whenever we point and click with our touchpad, mouse, or touchscreen, we interact with the GUI. Binary—zeros and ones—is at the bottom; computer hardware understands this layer. Several intermediaries exist between these two layers. Most programming languages used by social scientists and other computational scholars, like R or Python, are called “high-level” because they sit closer to the GUI.
