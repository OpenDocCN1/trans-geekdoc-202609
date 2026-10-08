As can be observed, there is no clear tendency for the results, with simi-
results arising when using only either linguistic or literary features. It is
true that the subgenres with 40,000 tokens or fewer achieve higher results on
average (between 0.8 and 1), while novels with more than 50,000 tokens are
bet 0.7 and 0.95. Nevertheless, the data points are spread out and
the tendency is too flat to obtain a statistical value on a regression analysis
(p-value of 0.26). However, it could be worth examining this hypothesis with
larger collections of texts or non-literary genres.

# 7.2.5 Canonicity of the Texts

The next hypothesis relates to the degree of canonicity of the text. In the
French tradition, there is a common differentiation between *littérature blanche*
(literary 'white literature', with a similar meaning to the concepts of *high-brow
literature or literary fiction*) and *genre literature* (also called para-literature). These
concepts could explain observed results that some highly canonized-
grealist, naturalist, literary fiction) tend to be classified with a lower
accuracy than more popular subgenres, as adventure or erotic novels. In
other words, a correlation could exist between the canonicity of the text and
the classification results.

To measure this, the number of pages in the manual MDLe is used again as
a formalization of the canonization, with possible values between 0.2 pages
(paragraph) and any number of complete pages, to calculate the median of
all texts that populate the genre. All are between 0.2 and one page, with one
exception - the *novilas* tend to have three pages. This martir is mostly in two
texts (Niebla with ten pages, and *San Manuel bueno*, martir with eight pages).
This category is removed from the calculations for this hypothesis for two
asons. First, the correlation analysis is sensitive to outliers, and second,
the extreme value of the subgenre is mainly based on a couple of outlying
canonized novels. The correlation of the subgenre is shown in the
scatter plot.

The genres that occupy fewer pages in the manual (*greguería, episodic na-
cional, erotic, and war novels*) tend to have a classification result of over 0.95,
the middle range tends to lie between 0.95 and 0.82, and those subgenres pop-\ulated by texts that typically occupy a page in the manual lie between 0.93 and
0.72 (with the only exception being the dialogue novel). A regression analysis
gives a statistical tendency (p-value 0.005), i.e. the more canonized a subgenre