
*   [McGee, M. J., Max, R., Stepehn, C. B., Shanathan Sritharan, Andrew J. Boyle, Nicholas, J., James, W. L., and Aaron, L. S.](#ch21.xhtml#R_ref21_7) (2022). Remote monitoring in patients with heart failure with cardiac implantable electronic devices: A systematic review and meta-analysis. Open Heart, 9(2), 6–11. [https://doi.org/10.1136/openhrt-2022-002096](https://doi.org/10.1136/openhrt-2022-002096).

*   [Pap, I. A., Stefan, O., Ioan, O., and Alexandru, A.](#ch21.xhtml#R_ref21_8) (2018). IoT-based ehealth data acquisition system. 2018IEEE Int. Conf. Automat. Qual. Test. Robot. AQTR 2018 - THETA 21st Ed., Proc., 1–5. [https://doi.org/10.1109/AQTR.2018.8402711](https://doi.org/10.1109/AQTR.2018.8402711).

*   Performance, Hyperledger, Scale Working Group, and others. (2018). Hyperledger blockchain performance metrics white paper. [https://www.Hyperledger.Org/resources/publications/blockchain-Performance-Metrics](https://www.Hyperledger.Org). Accessed on 31(1), 2020.

*   Pongnumkul, S., Chaiyaphum, S., and Suttipong, T. (2017). Performance analysis of private blockchain platforms in varying workloads. 201726th Int. Conf. Comp. Comm. Netw. (ICCCN), IEEE, 1–6.

*   Tanwar, S., Karan, P., and Richard, E. (2020). Blockchain-based electronic healthcare record system for healthcare 4.0 applications. J. Inform. Sec. Appl., 50, 102407.

*   Woznica, A. and Michal, K. (2022). Performance and scalability evaluation of a permissioned blockchain based on the hyperledger fabric, Sawtooth and Iroha. Comp. Sci. Inform. Sys., 19(2), 659–678. [https://doi.org/10.2298/CSIS210507002W](https://doi.org/10.2298/CSIS210507002W).

*   [Zhang, X., Kantilal, P. R., Ismail, K., and Mohammad, S.](#ch21.xhtml#R_ref21_13) (2021). Research on vibration monitoring and fault diagnosis of rotating machinery based on internet of things technology. Nonlin. Engg., 10(1), 245–254.

# 22 Developing spell check and transliteration tools for Indian regional language – Kannada

Chandrika Prasad^([^(22)](#fn22))

Department of Computer Science and Engineering, M S Ramaiah Institute of Technology, (Affiliated to Visvesvaraya Technical University Belagavi, Karnataka), Bangalore, Karnataka, India

DOI: [10.1201/9781003471059-22](https://dx.doi.org/10.1201/9781003471059-22)

## Abstract

**Kannada is one of the major regional languages of Karnataka, a prominent state of India. The text processing tasks are very important and highly required for the development of the language in this digital world. Spell checking is one of the needs in creating an effective document. Even though one can find several tools on the internet, it allows you to type or paste the Kannada text on the text editor and submit the text then the result will appear on the another editor. The proposed work delineates on developing an efficient interactive spell checking and transliteration tools for the Kannada language based on the Blooms filter algorithm, Symspell technique and International Phonetic Alphabet (IPA) representation. This work carried out with an intention to provide handy text processing tools to the public. The proposed work has been tested on several datasets and found to be useful with more than 85% and 87.29% accuracy for both spell check and transliteration tools, respectively.**

**Keywords: Blooms filter, Symspell algorithm, Levenshtein distance, transliteration, international Phonetic Alphabet, candidate words**

## Introduction

One of the key uses of natural language processing is the spell checker. It aids the user in producing a document free of errors. In several languages, the work of spell checking has already been extensively developed. MS-word is a widely used editor that gives users all the tools they need to create effective documents, especially in English. India contains more than 100 local languages, although only 22 are regarded as regional. Text processing is still in its infancy in many languages, notably Kannada. While there are a few transliteration tools available, there are no editors where users can freely enter and create documents that are error-free.

According to the literary survey, more than 1.35 billion people on the world speak and understand English, hence it is safe to assume that English is widely accepted all around the globe. The population of India is around 1.4 billion surpassing China and hence becoming the most populated country in the world. Around 57 million Kannada speakers exist in India making it one of the most used languages for communication in India. The government has come up with various solutions to enable even the most remote parts of the country to access information. Hence the need to convert language into native tongue arises.

Proper names such as name, place, object and, etc., are the fields in all government forms and offices, it’s practically impossible to ask the public to only fill it in English. This paper provides solution for these identified challenges.

Since its impossible to create a corpus for each engkan translation, hence we go for the transliteration approach where the pronunciation is preserved.

### Dictionary based tool

Set of Kannada words from different internet sources are collected and stored as a database. A list of misspelled words and its equivalent correct words are mapped and stored as dictionary. The module invokes a routine which performs look up operation in the dictionary and predicts the possible word for the misspelled Kannada word using efficient techniques like Bloom filter and Symspell algorithms.

### Kannada transliteration

Transliteration is the process of converting text from one writing system to another. One widely used method of transliteration is to use the International Phonetic Alphabet (IPA), which provides a standard-ized set of symbols for representing the sounds of human language. IPA-based transliteration allows for a more accurate representation of the sounds of one language in another, which can be useful for language learners, linguists, and others who need to work with multiple writing systems. The IPA is based on the principle of one sound, one symbol, which means that each symbol represents a single sound. It allows for a standardized representation of the sounds of a language, regardless of the writing system used. The IPA includes symbols for consonants, vowels, and other sounds, as well as diacritic marks that indicate variations in pronunciation, such as stress and tone. While IPA-based transliteration can be more precise than other methods, it can also be more complex and time-consuming, especially for those who are not familiar with the IPA. Additionally, not all languages have a one-to-one correspondence between their sounds and IPA symbols, which can lead to some ambiguity in transliteration. Despite these challenges, IPA-based transliteration remains a valuable tool for those who need to work with multiple languages and writing systems.

In the proposed work, both dictionary and transliteration tools are developed, the implementation part will focus more on these two models.

## Related work

A comprehensive survey is done on various languages to understand the methodology/ technique used by researchers.

The researchers have explored methodologies ([Randhawa et al., 2014](#ch22.xhtml#ref22_1)) used for developing spell check tool for various Indian regional languages including the performance analysis. This helps a researcher to understand the pros and cons of available techniques. A spell checker tool on Bangla is explored in ([Chaudhuri et al., 2002](#ch22.xhtml#ref22_2)). Researchers have handled the errors based on the phonetic in two stages using phonetically similar character error correction and reversed word dictionary and error correction. Experiment is conducted on three million words which are arranged in Trie data structure and obtained satisfied results.
