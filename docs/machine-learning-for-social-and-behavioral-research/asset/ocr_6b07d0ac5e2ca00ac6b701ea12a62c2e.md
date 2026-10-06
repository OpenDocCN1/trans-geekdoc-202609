# Introduction to Text Mining

# 11.3.1 Text Tokenization

From the previous discussion, we know we can identify gender based on gender pronouns. However, the gender pronouns are embedded in the text. Therefore, the first step of the analysis is to identify and take out the gender pronouns. In text mining, one can break down a block of text into individual words, e.g., based on white space in the text. The process is called tokenization (e.g., Stavrianou, Andritos, & Nicoloyannis, 2007; Weiss, Indurkhya, Zhang, & Damerau, 2010). For example, for the sentence “She is one of the best voice teachers I have ever had”, after tokenization, we get the individual words as listed in Table 11.1. For this particular example, we also change all upper case letters to lowercase letters as “She” becomes “she.” In many situations, this is useful since one can simply ignore cases to treat the words as the same. In this example, the punctuation marks are also removed.

# TABLE 11.1. Text Tokenization

| Word |
|---||
| 1 | she |
| 2 | is |
| 3 | one |
| 4 | of |
| 5 | the |
| 6 | best |
| 7 | voice |
| 8 | teachers |
| 9 | i |
| 10 | have |
| 11 | ever |
| 12 | had |

# Select the Gender Words

Since we are interested in identifying the gender of professors, only the words that reflect the gender information are useful. For example, for the words listed in Table 11.1, the word “she” provides relevant information for our analysis. Therefore, in this step, we would identify such words. After a quick review of part of the comments in the data, we found the gender words listed in Table 11.2. For example, “he,” “him,” and “his” are associated with the male professors while “she,” “her,” and “hers” are associated with the female professors. Note that, in writing, the contractions such as “he’s” and “she’s” are also used. Once the words are identified, we keep these words only in our data for further analysis.