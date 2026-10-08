# Applied Intelligent Decision Making in Machine Learning

# Recall

+   Dictionary look-up methodnRule-based method
MetaMap 2010
MetaMap 2013v2
Proposed Matrix-based method

FIGURE 8.5 Comparison between recall of different text classification methods.

dataset contains a large sequence of entities in problem concepts like "minimal right internal carotid artery disease" or "thrombosis of the right renal artery." A large sequence of entities is also found in treatment concepts like "a left carotid endarterectomy," "oxycodone-acetaminophen," "saphaneous vein graft → proximal descending artery," The system performed strict matching; in future, partial matching could be performed which might increase the recall of the system. The pruning of non-medical concepts was done using a UMLS database, large sequences of entities are not correctly matched in this database to medical words. This issue could be determined using relaxed matching of clinical concepts.

Text pre-processing included regular expressions for the identification of special characters, which are treated as word splitters, though only some words are identified in the gold-standard data which included these characters in between. Examples of composite words such as "severe 3 vessel disease,"saphaneous vein graft → obtuse marginal,"the patient’s pacing paces,"heel/shin," and "leg, erg & apos" are accurately predicted as concepts using the anticipated method.

# 8.6 CONCLUSIONS AND FUTURE WORK

In the proposed solution, medical concepts, as signs and symptoms of diseases, tests, and treatments, are identified using parallel matching of two matrices followed by a rule-based method. The pruning of non-medical concepts increased the performance of the system using concept mapping with semantics of UMLS. It is noted that the efficiency of the system is improved over MetaMap 2010, MetaMap 2013v2, and dictionary look-up methods. Recall could be further improved by adding new features like include prefix and suffix, stemming, word, semantics of words, or n-gram in the same method. Machine learning concepts are not used, which is the performance of the system is not dependent on the size of the dataset. The proposed system could be implemented on small and large datasets in an identical way,