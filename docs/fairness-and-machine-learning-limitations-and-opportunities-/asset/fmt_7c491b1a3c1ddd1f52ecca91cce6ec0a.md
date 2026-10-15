
A first prototype of the TIMIT dataset was released in December 1988 on a CD-ROM. An improved release followed in October 1990. TIMIT already featured the training/test split typical for modern machine learning benchmarks. There’s a fair bit we know about the creation of the data due to its thorough documentation \[[475](#references.xhtml#ref-475)\].

TIMIT features a total of about five hours of speech, composed of 6,300 utterances, specifically, ten sentences spoken by each of 630 speakers. The sentences were drawn from a corpus of 2,342 sentences such as the following.

She had your dark suit in greasy wash water all year.(sa1)

Don’t ask me to carry an oily rag like that. (sa2)

This was easy for us. (sx3)

Jane may earn more money by working hard. (sx4)

She is thinner than I am. (sx5)

Bright sunshine shimmers on the ocean. (sx6)

Nothing is as offensive as innocence. (sx7)

The TIMIT documentation distinguishes between eight major dialect regions in the United States, documented as `New England, Northern, North Midland, South Midland, Southern, New York City, Western, Army Brat (moved around)`. Of the speakers, 70 percent are male and 30 percent are female. All native speakers of American English, the subjects were primarily employees of Texas Instruments at the time. Many of them were new to the Dallas area where they worked.

Racial information was supplied with the distribution of the data and coded as “White,” “Black,” “American Indian,” “Spanish American,” “Oriental,” and “Unknown.” Of the 630 speakers, 578 were identified as White, twenty-six as Black, two as American Indian, two as Spanish-American, three as Oriental, and seventeen as unknown ([table 9.1](#chapter_9.xhtml#tab9-1)).

[Table 9.1](#chapter_9.xhtml#tab9_1)Demographic information about the TIMIT speakers

|  || Male || Female || Total (%) |

| --- | --- | --- | --- |

| White || 402 || 176 || 578 (91.7) |

| --- | --- | --- | --- |

| Black || 15 || 11 || 26 (4.1) |

| American Indian || 2 || 0 || 2 (0.3) |

| Spanish American || 2 || 0 || 2 (0.3) |

| Oriental || 3 || 0 || 3 (0.5) |

| Unknown || 12 || 5 || 17 (2.6) |

The documentation notes:

In addition to these 630 speakers, a small number of speakers with foreign accents or other extreme speech and/or hearing abnormalities were recorded as “auxiliary” subjects, but they are not included on the CD-ROM.

It comes as no surprise that early speech-recognition models had significant demographic and racial biases in their performance.

Today, several major companies, including `Amazon`, `Apple`, `Google`, and `Microsoft`, all use speech-recognition models in a variety of products, from cell phone apps to voice assistants. There is no longer a major open benchmark that would support training models competitive with the industrial counterparts. Industrial speech recognition pipelines are generally complex and use proprietary data sources that we don’t know a lot about. Nevertheless, today’s speech-recognition systems continue to exhibit performance disparities along racial lines \[[476](#references.xhtml#ref-476)\].

### UCI Machine Learning Repository

The UCI Machine Learning Repository currently hosts more than 500 datasets, mostly used for different classification and regression tasks. Most datasets are relatively small, consisting of a few hundred or a few thousand instances. The majority are structured tabular data sets with a handful or a few tens of attributes.

The UCI Machine Learning Repository contributed to the adoption of the train-test paradigm in machine learning in the late 1980s. Pat Langley recalls:

The experimental movement was aided by another development. David Aha, then a PhD student at UCI, began to collect data sets for use in empirical studies of machine learning. This grew into the UCI Machine Learning Repository (`[http://archive.ics.uci.edu/ml/`](http://archive.ics.uci.edu/ml/)), which he made available to the community by FTP in 1987. This was rapidly adopted by many researchers because it was easy to use and because it let them compare their results to previous findings on the same tasks \[[477](#references.xhtml#ref-477)\].

The most popular dataset in the repository is the Iris dataset, containing taxonomic measurements of 150 iris flowers, fifty from each of three species. The task is to classify the species given the measurements.

As of October 2020, the second most popular dataset in the UCI repository is the Adult dataset. Extracted from the 1994 Census database, it features nearly 50,000 instances describing individuals in the United States, each having fourteen attributes. The task is to classify whether an individual earns more than or less than $50,000. The Adult dataset remains popular in the algorithmic fairness community, largely because it is one of the few publicly available datasets that features demographic information including `gender` (coded in binary as male/female), as well as `race` (coded as Amer-Indian-Eskimo, Asian-Pac-Islander, Black, Other, and White).

Unfortunately, the data has some idiosyncrasies that make it less than ideal for understanding biases in machine learning models. Due to the age of the data, and the income cutoff at $50,000, almost all instances labeled `Black` are below the cutoff, as are almost all instances labeled `female`. Indeed, a standard logistic regression model trained on the data achieves about 85 percent accuracy overall, while the same model achieves 91 percent accuracy on `Black` instances, and nearly 93 percent accuracy on `female` instances. Likewise, the ROC curves for the latter two groups enclose actually more area than the ROC curve for male instances. This is an atypical situation: more often, machine learning models perform worse on historically disadvantaged groups.

### MNIST

The MNIST dataset contains images of handwritten digits. Its most common version has 60,000 training images and 10,000 test images, each having 28×28 black and white pixels ([figure 9.1](#chapter_9.xhtml#fig9-1)).

![Figure 9.1A sample of MNIST digits.](images/fig9-1.png)

[Figure 9.1](#chapter_9.xhtml#fig9_1)A sample of MNIST digits.

MNIST was created by researchers Burges, Cortes, and LeCun from an earlier dataset released by the National Institute of Standards and Technology (NIST). The dataset was introduced in a research paper in 1998 to showcase the use of gradient-based deep learning methods for document recognition tasks \[[478](#references.xhtml#ref-478)\]. Since then cited over 30,000 times, MNIST became a highly influential benchmark in the computer vision community. Two decades later, researchers continue to use the data actively.

The original NIST data had the property that training and test data came from two different populations. The former featured the handwriting of two thousand American Census Bureau employees, whereas the latter came from 500 American high school students \[[479](#references.xhtml#ref-479)\]. The creators of MNIST reshuffled these two data sources and split them into training and test set. Moreover, they scaled and centered the digits. The exact procedure to derive MNIST from NIST was lost, but recently reconstructed by matching images from both data sources \[[480](#references.xhtml#ref-480)\].

The original MNIST test set was of the same size as the training set, but the smaller test set became standard in research use. The 50,000 digits in the original test set that didn’t make it into the smaller test set were later identified and dubbed *the lost digits*. \[[480](#references.xhtml#ref-480)\]

Table 9.2A snapshot of the original MNIST leaderboard from February 2, 1999Source: Internet Archive (retrieved December 4, 2020).

| Method || Test error (%) |

| --- | --- |

| linear classifier (1-layer NN) || 12.0 |

| --- | --- |

| linear classifier (1-layer NN) \[deskewing\] || 8.4 |

| pairwise linear classifier || 7.6 |

| K-nearest-neighbors, Euclidean || 5.0 |

| K-nearest-neighbors, Euclidean, deskewed || 2.4 |
