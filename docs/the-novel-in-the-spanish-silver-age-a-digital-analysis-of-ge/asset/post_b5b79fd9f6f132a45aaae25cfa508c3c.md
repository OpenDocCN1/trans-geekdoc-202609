
direct speech can be formalized in rules using exclusively typographical features, while in other periods the readers have to apply their understanding of the text to distinguish them from each other. The Spanish novels from the analyzed period do have clear typographical rules. Therefore, I decide to use a rule-based approach and annotate it in TEI elements, as presented above.

## 4.2 Transformations of Lexical Data and Linguistic Annotation

In the previous chapter, a set of linguistic annotation layers were introduced. The Machine Learning tasks require an even more specific operationalization of each of these in every text. Normally, the first step is to count each feature in the entire document. This is the basis of the so-called Bag of Words document model (BoW), or the more general Bag of Features. The information about the position in the text of the words (beginning of the text, end of a sentence) is ignored, and at least a second step is applied, namely a division through the entire length of the document to obtain the relative frequency, a typical measure, for example, in Corpus Linguistics.

The same model and transformation could be used for other annotations: relative frequency of direct speech in the text, relative frequency of each TEitag, etc. Further transformations are usual in different areas: z-score transformation in stylometry, tf-id or binary frequency in Computer Sciences, or logarithmic transformations in Statistics. The different fields tend to consider only their typical traditions and consider evaluate other options. This can be observed that from all the papers about computational analysis mentioned in Chapter 2.2, none evaluated transformations, and in many of the researchers provide neither their decisions nor their reasons.¹ The target group of this chapter is researchers who are active in DH and come from different areas which have common interests with my research: Computer Science, Computational Linguistics, Literary Studies, and linguistics.

- Some authors were contacted personally by email and needed to check their code to confirm the transformation they had used.

For that, the goal of this chapter is to obtain common knowledge about an aspect that has been overlooked until now. 

So, if the different communities only use their typical transformation and ignore the rest, why do I dedicate an entire chapter to exploring this? First, because this is an interdisciplinary work and part of it should be to contrast theories and practices in several areas and, if possible, evaluate which could bring more benefit to the research goal. One, specific specific transformation could bring major advantages to the classification of genre; perhaps a traditional transformation to one of the fields, or perhaps a new modification or concatenation. This is what happened when the stylometrist John Burrows applied a transformation to textual frequency that was standard in Statistics (z-scores) but had been rarely used in Literary Studies or Linguistics. This led to one of the most milestones of stylometry in particular, and Digital Humanities in evaluation. Burrows (2002) in Chapter 6.1 will show that none of these transformations will have the same importance for genres as z-scores for stylometric analysis of authorship. However, some of them will clearly yield higher results than others. In addition to analyzing the accuracy of the transformations, the reason why some lead to a better classification will also be analyzed. A series of characteristics of these transformations will be evaluated in Section 6.1.4 to explore the possible causes of this difference. These characteristics are described in this chapter in detail. For example, some of these transformations still contain information about frequency (relative or logarithmic frequency), others transform the numerical differences into categorical information (binary), while others transform the data in a way that no longer correlates with the original frequency (tf-id or z-scores).

In any case, why do these fields transform the original frequencies from the tests? Compared to other kinds of information (like colors in pictures or characteristics in living beings), linguistic data tends to follow a pattern distribution known as Zipfian distribution. This was explained by the researcher Zipf, who in the 1930s stated (1932) the empirical law that the rank of a word in this distribution multiplied by its frequency gives a constant (Carstensen et al. 2009, 230). The correlation between the rank and the frequency of each word is, in theory, a perfect line with a slope of -45° when both variables are log-transformed (Lestrade 2017). This law means that the most frequent word of any corpus will be twice as frequent as the second one, and three times as frequent as the third one. This distribution is "about prevalent in social sciences as Gaussian distributions are in the natural sciences (Pustet 2004).

This raises the question of what the theoretical criteria are the transformations should present in order to deliver higher results. It is thought that a transformation that modifies the Zipfian distribution towards Gaussian would be desirable. Another aspect is it expected that losing the original frequency will also be an advantage as happened with binary transformations (z-scores) in Computer Science (tf-idf). 

The transformations described here are often used in the Humanities. For this reason, I will introduce, plot, describe, and explain each of them, relating their characteristics. In Section 4.2.3 I will propose new transformations based on the variations or concatenations.

## 4.2.2 Classic Transformation of Frequency

### 4.2.1 Term Frequency

The most basic representations of the frequency of words are the term frequency, total frequency, or raw frequency. All of these relate to the number of times each word appears in every text. This basic representation is seldom used because of its dependency on the length of the text: The larger a text is, the higher the term frequency will be. In the following figure, there are four different plots, showing several aspects of this representation of data in two novels: *Los pazos de Ulloa*, by Bazán, and *Tirano Banderas*, by Valle-Inclán.

Figure 39: Plots showing raw frequency in two novels

Visualization of Raw Frequency

Sub-figure A:

Sub-figure B:
Histogram of 2000 MFWs
mean = 39.21
standard deviation = 288.91

Sub-figure C:
Box Plots of 2000 MFWs
Median = 7.0
IQR = 11.0

Sub-figure D:
Scatter Plot of Frequencies
Correlation (Pearson's r) = 1.0
p-value = 0.0

The first plot (Sub-figure A) shows the frequencies of the 20 top tokens (from the typographical character for the comma to the word *una*) and their frequency in the two novels. As is observed, there are more than 7000 commas in the first text, and around 400 in the second (a much shorter novel).

This plot shows an important characteristic of counting and transforming tokens in a corpus: The words are counted in each text, but the counting process takes the entire corpus into consideration. The 13th token (−, an em
