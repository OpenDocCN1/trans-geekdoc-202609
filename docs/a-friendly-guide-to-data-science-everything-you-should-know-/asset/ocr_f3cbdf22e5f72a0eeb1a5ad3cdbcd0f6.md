# CHAPTER 17 MAKING THE COMPUTER LITERATE: TEXT AND SPEECH PROCESSING

![](bbox=[0.136, 0.106, 0.863, 0.347])

Figure 17-1. Two clouds with words and without highlighting of plurals

The word cloud on the left includes some “duplicates” because it treats “word” and “words” as separate words. Other pairs that show up in that one are “language” and “languages” and “system” and “systems.” In the one on the left, “words,” and “word” are both smaller than “text” and “speech,” but still big. But in the right, they’re counted together as “word,” that becomes the most common word in the cloud.

# Common NLP Representations and Tasks

All of the above preprocessing steps help turn text into data that can be fed into machine learning algorithms to accomplish things. In this section, I'll cover many of the different tasks that people can do with NLP. But first, a word about general tools. Large language models (LLMs) have completely revolutionized NLP. Prior to this, there were a variety of techniques used to accomplish the various tasks with text data. LLMs are not always used nowadays for a variety of reasons, and people do NLP use a lot of the “traditional” techniques because they're still incredibly useful and sometimes the only option for a particular domain—and they require a lot less compute than LLMs. I'll talk more about LLMs specifically in a section below, but just be aware that large language models