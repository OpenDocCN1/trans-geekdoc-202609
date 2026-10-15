
| 40 PCA + quadratic classifier || 3.3 |

| 1,000 RBF + linear classifier || 3.6 |

| K-NN, Tangent Distance, 16×16 || 1.1 |

| SVM deg 4 polynomial || 1.1 |

| Reduced Set SVM deg 5 polynomial || 1.0 |

| Virtual SVM deg 9 poly \[distortions\] || 0.8 |

| 2-layer NN, 300 hidden units || 4.7 |

| 2-layer NN, 300 HU \[distortions\] || 3.6 |

| 2-layer NN, 300 HU \[deskewing\] || 1.6 |

| 2-layer NN, 1000 hidden units || 4.5 |

| 2-layer NN, 1000 HU \[distortions\] || 3.8 |

| 3-layer NN, 300 + 100 hidden units || 3.05 |

| 3-layer NN, 300 + 100 HU \[distortions\] || 2.5 |

| 3-layer NN, 500 + 150 hidden units || 2.95 |

| 3-layer NN, 500 + 150 HU \[distortions\] || 2.45 |

| LeNet-1 \[with 16×16 input\] || 1.7 |

| LeNet-4 || 1.1 |

| LeNet-4 with K-NN instead of last layer || 1.1 |

| LeNet-4 with local learning instead of ll || 1.1 |

| LeNet-5 \[no distortions\] || 0.95 |

| LeNet-5 \[huge distortions\] || 0.85 |

| LeNet-5 \[distortions\] || 0.8 |

| Boosted LeNet-4 \[distortions\] || 0.7 |

From the beginning, MNIST was intended to be a benchmark used to compare the strengths of different methods. For several years, LeCun maintained an informal leaderboard on a personal website that listed the best accuracy numbers that different learning algorithms achieved on MNIST.

In its capacity as a benchmark, it became a showcase for the emerging kernel methods of the early 2000s that temporarily achieved top performance on MNIST \[[481](#references.xhtml#ref-481)\]. Today, it is not difficult to achieve less than 0.5 percent classification error with a wide range of convolutional neural network architectures. The best models classify all but a few pathological test instances correctly. As a result, MNIST is widely considered too easy for today’s research tasks.

MNIST wasn’t the first dataset of handwritten digits in use for machine learning research. Earlier, the US Postal Service (USPS) had released a dataset of 9,298 images (7,291 for training, and 2,007 for testing). The USPS data were actually a fair bit harder to classify than MNIST. A nonnegligible fraction of the USPS digits look unrecognizable to humans \[[482](#references.xhtml#ref-482)\], whereas humans recognize essentially all digits in MNIST.

### ImageNet

ImageNet is a large repository of labeled images that has been highly influential in computer vision research over the last decade. The image labels correspond to nouns from the WordNet lexical database of the English language \[[483](#references.xhtml#ref-483)\]. WordNet groups nouns into cognitive synonyms, called *synsets*. The words *car* and *automobile*, for example, would fall into the same synset. On top of these categories, WordNet provides a hierarchical tree structure according to a supersubordinate relationship between synsets. The synset for *chair*, for example, is a child of the synset for *furniture* in the WordNet hierarchy. WordNet existed before ImageNet and in part inspired the creation of ImageNet.

The initial release of ImageNet included about 5,000 image categories, each corresponding to a synset in WordNet. These ImageNet categories averaged about 600 images per category \[[484](#references.xhtml#ref-484)\]. ImageNet grew over time and its fall 2011 release had reached about 32,000 categories.

The construction of ImageNet required two essential steps: retrieving candidate images for each synset and labeling the retrieved images. This first step utilized online search engines and photo sharing platforms with a search interface, specifically Flickr. Candidate images were taken from the image search results associated with the synset nouns for each category.

For the second labeling step, the creators of ImageNet turned to Amazon’s Mechanical Turk platform (MTurk). MTurk is an online labor market that allows individuals and corporations to hire on-demand workers to perform simple tasks. In this case, MTurk workers were presented with candidate images and had to decide whether or not the candidate image was indeed an image corresponding to the category that it was putatively associated with.

It is important to distinguish between this ImageNet database and a popular machine learning benchmark and competition, called ImageNet Large Scale Visual Recognition Challenge (ILSVRC), that was derived from it \[[485](#references.xhtml#ref-485)\]. The competition was organized yearly from 2010 until 2017, reaching significant notoriety in both industry and academia, especially as a benchmark for emerging deep learning models.

When machine learning practitioners say “ImageNet” they typically refer to the data used for the image classification task in the 2012 ILSVRC benchmark. The competition included other tasks, such as object recognition, but image classification has become the most popular task for the dataset. Expressions such as “a model trained on ImageNet” typically refer to training an image classification model on the benchmark data set from 2012.

Another common practice involving the ILSVRC data is *pretraining*. Often a practitioner has a specific classification problem in mind whose label set differs from the 1,000 classes present in the data. It’s possible nonetheless to use the data to create useful features that can then be used in the target classification problem. Where ILSVRC enters real-world applications it’s often to support pretraining.

This colloquial use of the word ImageNet can lead to some confusion, not least because the ILSVRC-2012 dataset differs significantly from the broader database. It includes only a subset of 1,000 categories. Moreover, these categories are a rather skewed subset of the broader ImageNet hierarchy. For example, of these 1,000 categories only three are in the *person* branch of the WordNet hierarchy, specifically, *groom*, *baseball player*, and *scuba diver*. Yet, more than 100 of the 1,000 categories correspond to different dog breeds. The number is 118, to be exact, not counting wolves, foxes, and wild dogs, which are also present among the categories.

What motivated the exact choice of these 1,000 categories is not entirely clear. The apparent canine inclination, however, isn’t just a quirk either. At the time, there was an interest in the computer vision community in making progress on prediction with many classes, some of which are very similar. This reflects a broader pattern in the machine learning community. The creation of datasets is often driven by an intuitive sense of what the technical challenges are for the field. In the case of ImageNet, another important consideration was scale, both in terms of the number of images and the number of classes.

The large-scale annotation and labeling that went into ImageNet falls into a category of labor that Mary Gray and Siddharth Suri call *ghost work* in their book of the same name \[[486](#references.xhtml#ref-486)\]. They point out: “MTurk workers are the AI revolution’s unsung heroes.”

Indeed, ImageNet was labeled by about 49,000 MTurk workers from 167 countries over the course of multiple years.

### The Netflix Prize

The Netflix Prize was one of the most famous machine learning competitions. Starting on October 2, 2006, the competition ran for nearly three years, ending with a grand prize of $1 million, announced on September 18, 2009. Over the years, the competition saw 44,014 submissions from 5,169 teams.

The Netflix training data contained roughly 100 million movie ratings from nearly 500 thousand Netflix subscribers on a set of 17,770 movies. Each data point corresponds to a tuple <user, movie, date of rating, rating>. At about 650 megabytes in size, the dataset was just small enough to fit on a CD-ROM, but large enough to be pose a challenge at the time.
