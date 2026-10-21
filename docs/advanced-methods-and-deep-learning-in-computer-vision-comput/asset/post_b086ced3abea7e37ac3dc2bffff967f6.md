
model structure and train their models in an end-to-end fashion, which is more challenging, but provides dividends in performance (Zhang et al., 2017).

The remainder of this section is structured as follows: In Section 11.4.1 we detail a simple use of attributes for ZSL; in Section 11.4.1 we detail a more nuanced relative attribute formulation; in Section 11.4.2 we cover the use of shared semantic spaces in ZSL; in Section 11.4.3 we cover basic approaches to semantic vector space construction; in Section 11.4.4 we cover the incorporation of knowledge in the form of graphs for ZSL action classification.

## 11.4.1 Attributes in zero-shot learning

The use of attributes – including action centric attributes such as affordances covered in Section 11.2 – in recognition allows the construction of classifiers which are humanly interpretable and specifiable. Attributes mitigate the issue of opacity through use of an explicit predefined mid-level representation below the level of class categories.

Use of attributes allows an easy mechanism through which to learn visual representations from the available training data and to transfer those representations onto the classes for which no training data is available. Attributes are general in that they have presence across multiple class categories, and through taking multiple attributes with different distributions across classes allow representation of select classes.

The use of attributes in ZSL is as follows: Attribute detectors are trained over the seen set and associated attribute labels. These detectors are generalizable across both the seen and unseen set. Due to the different class coverage (e.g., object or action class) of different attribute categories, different combinations of attributes can represent different classes – class detectors can then be instantiated on top of attribute detectors. This instantiation follows a specification of which attributes are associated with which classes. When given a specification for unseen categories, detectors can be built even though no visual samples of the unseen categories have been encountered.

Conventional use of attributes in computer vision is binary: an attribute is represented as either present, or absent. This limits the representational power of attribute representations. However, binary representations can be generalized to scalar representations where each attribute is associated with a scalar degree rather than a binary category. This is both more flexible representationally, and allows the inclusion of attributes which do not so cleanly fall into a binary categorization. For example, while an attribute of “indoors / outdoors” often is clearly binary, an attribute of “moving fast / moving slow” has a more even distribution over gradations in visual input.

Parikh and Grauman (2011) presents one approach to generalizing binary attributes to scalar attributes. A challenge in generalizing from binary to scalar attributes is inconsistency in annotations, as different annotators may have different understandings of what different attributes’ degrees correspond to in the scalar representation. They resolve this challenge by requesting that annotators not assign scalar values to attributes, but rank images in terms of attribute degree. After images are ranked, scalar attribute values can be derived from their annotated relative attribute degrees.

For binary attributes, attribute detectors can be trained using conventional classifiers, but producing scalar attributes requires other methods. Parikh and Grauman (2011) train a ranking function over images for attributes over the seen set, and use that ranking function in the production of a scalar value.

Relative attribute representations allow for greater flexibility in class specifications. With consideration to the attribute of “moving fast / moving slow” one can specify that an unseen category “running” is faster than the seen category of “walking”, or that the unseen category of “standing” is slower than the seen category of “walking”. This is done without a need to define either a binary specification or intuit a scalar value with which to describe the unseen categories.

## 11.4.2 Shared embedding spaces

The generalization of binary attributes to scalar attributes increases their representational power. However, the increased representational power came at the cost of increased difficulty in annotating attributes and specifying classes. Relative Attributes (Parikh and Grauman, 2011) introduced one solution to these challenges.

Attributes can also be abstracted away. It need not be the case that visual representations move through humanly understandable attributes. Abstracting attributes away has a couple advantages:

- Avoid the imprecision introduced by passing through engineered, rather than learned, representations.
- Avoid the overhead and imprecision of annotating attributes.

The question is then how to construct a system such that training for classification of seen classes results in a classifier which works not only for seen classes, but for unseen classes as well, without leveraging an engineered mid-level representation which allows the specification of unseen classes in terms of that mid-level representation.

One approach that can be used is to define unseen classes in terms of their similarity relations to seen classes, where these relations are learned from text corpora. Extensive work exists in Natural Language Processing (NLP) producing semantic vector spaces which represent similarity relations among words – word2vec (Mikolov et al., 2013) is one popular example. The intuition is that terms in these spaces are located in proximity to other terms with which they share semantic similarity. Trained semantic spaces are publicly available – these can be taken and used without a need to produce them from scratch. See Section 11.4.3 for details on construction of such spaces.

Terms with semantic similarity often share similarity in the visual space as well – e.g., “jogging” is both semantically and visually part way between “running” and “walking”. And so, it is often the case that if the visual similarity to known categories can be determined, then the semantic similarity relations can be established as well. Then, from these semantic relations we can infer semantic categories of visual inputs.

To illustrate: Consider a set of seen classes including “running” and “walking”, and a set of unseen classes including “jogging”, a semantic vector space capturing semantic proximity between these categories, and a computer vision architecture, such as a CNN, which produces visual feature representations of input. Then, consider an input sample of unknown class. Say that the visual representation of this input as produced by the CNN is part way between the visual representation for “running” and for “walking”. We then go to the semantic language space and see that the label that is located part way between "running" and "walking" is jogging and assign this label to the input.

Most often, comparing similarities between samples of unknown class and known classes is not done in the visual space. It is more common to map the input into the semantic space and perform comparisons to known classes there. This requires embedding one space into another.

The mechanism of embedding one space into another can be as simple as a linear transformation applied over one space, which is then trained over a similarity loss between two spaces. DeViSe (Frome et al., 2013) is a good example of an architecture using this method. This involves two pretrained representations – visual features taken from, for instance, a CNN trained over classification, and word vectors in an embedding space, which may be produced through means discussed in Section 11.4.3.

One method of embedding visual features into the semantic space of the word vectors is then illustrated in Fig. 11.8. A layer of nodes is appended to the top of the pretrained CNN features, and then trained. The loss that this layer is trained over is the similarity (e.g., cosine similarity) between the output of this layer, and the vectors in the semantic embedding space corresponding to the labels of the visual input. This learns a simple linear mapping from visual feature vectors onto text derived semantic features.

More sophisticated mappings than linear translations are often used. Using multiple layers of neurons, in conjunction with nonlinear activations, produce nonlinear mappings (e.g., Kato et al., 2018 use such a method). Kodirov et al. (2017) use an autoencoder with semantic constraints to produce the embedding, and find that the constraint of visual reconstruction leads to better generalization to unseen classes in ZSL.

![](img/fe161b7f6e96e35e7e853eece52c6dce_414_0.png)

FIGURE 11.8 A simple approach to embedding visual representations into a semantic space, as is used by methods such as DeViSe (Frome et al., 2013). Two pretrained models are used: 1) pretrained visual features, such as produced by a CNN trained over a visual task, and 2) a semantic vector space as produced through methods discussed in Section 11.4.3. A simple linear transformation is produced through appending a layer of nodes on top of the visual features, and training them w.r.t. their similarity to the semantic word vector of the labels corresponding to visual input. Once this linear transformation is learned, it constitutes a mapping from the space of visual features into the semantic vector space.

Once both visual input and semantic representations are placed in the same space, then determining the class of novel visual input is as simple as representing visual input in that space and then finding the nearest semantic label in that same space.
