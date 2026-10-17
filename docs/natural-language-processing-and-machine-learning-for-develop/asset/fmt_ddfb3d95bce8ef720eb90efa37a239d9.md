
This chapter focuses on NLP concepts, and while some NLP algorithms are mentioned in this chapter, the relevant code samples are provided Chapter [5](#ch05.xhtml) and Chapter [6](#ch06.xhtml). Depending on your NLP background, you might decide to read the sections in a nonsequential fashion. If your goal is to proceed quickly to code samples, you can skip some sections in this chapter, and later you can return to read those omitted sections.

The first part of the chapter provides an abbreviated tour of several languages that belong to major human language groups, illustrating some of the facets of human languages that can make NLP a truly challenging endeavor. However, please keep in mind that this section contains many details that will *appeal primarily to language aficionados.* This section contains grammatical details that differentiate various languages from each other that highlight the complexity of generating native-level syntax as well as native-level pronunciation. Depending on your level of interest, feel free to read the portions of this section that interest you and then proceed to the next section of this chapter.

Also keep in mind that the discussion regarding regional accents and slang contain anecdotal observations based on the experiences of the author: there is no scientifically rigorous basis or any studies to support those observations, which means that they are not necessarily true in a general case. However, you might find some of the sections somewhat interesting (and in some cases, they might be similar to your own experiences).

Indeed, various subsections reflect the author’s experiences in multilingual environments while living and working in various countries: in particular, this includes Italian, Spanish, French, and Japanese, as well as language dialects (the Venetian dialect and Venezuelan criollo), the challenges facing nonnative-English speakers, and also the fascinating Japanese language.

The second part of the chapter introduces you to NLP and a brief history of the major stages of NLP. You will also learn about NLP applications, NLP use cases, NLU, and NLG. Then you will learn about word sense disambiguation. This section only provides a very brief description of these topics, some of which can fill entire books and full-length courses.

The third part of this chapter discusses various NLP techniques and the major steps in an NLP-related process. You will also learn about standard NLP-related tasks, such as text normalization, tokenization, stemming, lemmatization, and the removal of stop words. As you will see, some of these tasks (e.g., tokenization) involve implicit assumptions that are not true for all languages.

The final section introduces Named Entity Recognition (NER) and topic modeling, which pertains to finding the main topic(s) in a text document.

Last, please keep in mind that the first portion of this chapter contrasts some grammatical aspects of languages from an informal perspective; if you are interested in a formal linguistic analysis, you can find such details through an online search.

## **The Origin of Languages**

Someone once remarked that “the origin of language is an enigma,” which is viscerally appealing because it has at least a kernel of truth. Although there are multiple theories that attempt to explain how and why languages developed, none of them has attained universal consensus. Nevertheless, there is no doubt that humans have far surpassed all other species in terms of language development.

There is also the question of how the vocabulary of a language is formed, which can be the confluence of multiple factors, as well as meaning in a language. According to Ludwig Wittgenstein (1953), who was an influential philosopher in many other fields, language derives its meaning from use.

One theory about the evolution of language in humans asserts that the need for communication between humans makes language a necessity. Another explanation is that language is influenced by the task creating complex tools, because the latter requires a precise sequence of steps, and ultimately spurred the development of languages.

Without delving into their details, the following list contains some theories that have been proposed regarding language development. Keep in mind that they vary in terms of their support in the academic community:

*   Strong minimalist thesis

*   The FlintKnapper

*   The Sapir-Whorf hypothesis

*   Universal grammar (Noam Chomsky)

The strong minimalist thesis (SRT) asserts that language is based on something called hierarchical syntactic structure.

The FlintKnapper asserts that the ability to create complex tools involved an intricate sequence of steps, which in turn necessitated communication between people.

In simplified terms, the Sapir–Whorf hypothesis (also called the linguistic relativity hypothesis, which is a slightly weaker form) posits that the language we speak influences how we think. Consider how our physical environment can influence our spoken language: Eskimos have several words to describe snow, whereas people in some parts of the Middle East have never seen a snow storm.

Universal grammar is a genetic-based theory by Noam Chomsky in which he asserts that all humans have an innate capacity to learn languages (provided that they are raised in a reasonably normal environment). This innate capacity is not bound to a grammar or vocabulary of any human language, and diverges from earlier “tabula rasa” (blank slate) theories regarding the human mind at birth. While Chomsky’s theory has appealing aspects, there are critic of UG, which you can read here if you are interested in the details:

*[https://en.wikipedia.org/wiki/Universal\_grammar](https://en.wikipedia.org/wiki/Universal_grammar)*

Indeed, despite the grammatical diversity of human languages and the rich set of sounds that are possible in human languages, consider the following fact: a healthy newborn infant from one country can be placed in any other country and learn to speak the common language of that country, regardless of the genetic makeup of the infant.

Hence, humans have a universal capacity to learn languages, and seem to have an innate ability to learn multiple languages. This capacity to learn languages separates us from animals because the latter are unable to create a language that is close to the complexity of human languages. Noam Chomsky explains that this capability exists in humans because of a broader skill: humans have a recursive-like capacity to mentally combine objects in order to create new objects.

If the origin of languages is a topic that appeals to you, there are many resources available through an Internet search that provide a myriad of detailed explanations from which you can select the theories that seem most plausible to you.

### **Language Fluency**

As mentioned in the previous section, human infants are capable of producing the sounds of any language, given enough opportunity to imitate those sounds. Alas, they tend to lose some of that capacity as they become older, which might explain why some adults speak another language with an accent (of course, there are plenty of exceptions).

Interestingly, babies respond favorably to the sound of vowel-rich parentese, and yet a study in 2018 suggests that babies prefer the sound of other babies instead of their mother:

*[https://eurekalert.org/pub_releases/2018-05/asoa-ftm042618.php](https://eurekalert.org/pub_releases/2018-05/asoa-ftm042618.php)*

*[https://getpocket.com/explore/item/babies-prefer-the-sounds-of-other-babies-to-the-cooing-of-their-parents]*
