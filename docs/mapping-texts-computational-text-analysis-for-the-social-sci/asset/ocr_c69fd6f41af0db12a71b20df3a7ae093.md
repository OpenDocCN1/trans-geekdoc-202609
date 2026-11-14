directions get at immigration/citizenship juxtaposition, centroids get closer to immigration/not-immigration or citizenship/not-citizenship oppositions. Here, theoretical motivation and subject expertise will drive which strategy is most appropriate for our research aims.

# Word Mover’s Distance

Word embeddings most readily lend themselves to word- and meaning-level analyses. Often we want to learn something about documents or authors. For instance, can we measure the extent any document writes about the same things and in the same way as the other documents in the corpus?

We use Word Mover’s Distances (WMDs) for this (Kusner et al. 2015).67 WMD is a measure of the minimum cost it would take to move all words in one document to the locations of the words in another document.68

More specifically, the WMD between document i and document j is the minimum sum of the products of two numbers for each pair of words across the two documents: the cosine distance and the cell entry for that word pair in what is known as a “flow matrix.”69 WMD finds the cell entries under the constraints that (1) the sum of the row word is the relative frequency of that word in i and (2) the sum of the column word is the relative frequency of that word in j. Finding the minimum cost is computationally demanding so Kusner and colleagues (2015:4) propose relaxed Word Mover’s Distance (RWMD). However calculated, the result is a distance score where larger values indicate less context similarity between the two documents and smaller values indicate more context similarity. We’ll stick with RWMD given the computational complexity of WMD (cf. Brunila and LaViolette 2021).

Say we want the contextual similarities between our news articles—all mentioning “immigrant” and “immigration” at least once—and a collection of press releases by a group of civil society organizations devoted to immigration-related issues.70 Following our earlier work (Stoltz and Taylor 2021), let’s examine the extent left-wing and right-wing news sources use language similar to these immigration-focused civil society organizations.

We’ve already wrangled articles and pretrained vectors; now we need to wrangle the press releases. Let’s load and wrangle them using the same preprocessing workflow we used for the All the News (ATN) articles.

67 There are other strategies. See Lix and colleagues (2022) for one approach.
68 It is an offshoot of Earth Mover’s Distance (EMD), which compares how similar two probability distributions are.
69 Finding this matrix is called a transportation problem.
70 The press releases are provided with text2map.corpora and scraped from the website from two right-wing organizations (the Center for Immigration Studies and the Federation of American Immigration Reform) and two left-wing organizations (The National Network for Immigrant and Refugee Rights and the Women’s Refugee Commission).