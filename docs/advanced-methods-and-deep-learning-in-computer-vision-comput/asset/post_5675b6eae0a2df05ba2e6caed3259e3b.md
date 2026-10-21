
![](img/fe161b7f6e96e35e7e853eece52c6dce_46_0.png)

FIGURE 1.14 Matching when one feature is occluded and another is added: (a) basic labeling of model (left) and image (right); (b) match graph; (c) placement of votes in parameter space (notation as in Fig. 1.13).

reduced. On the other hand, noise or clutter can add erroneous features. If the latter are at arbitrary distances from existing features, then the number of possible feature assignments will be increased but there will not be any more compatibilities in the match graph, so the latter will have only trivial additional complexity. However, if the extra features appear at allowed distances from existing features, this will introduce extra compatibilities into the match graph and make it more tedious to analyze. In the case shown in Fig. 1.14, both types of complication—an occlusion and an additional feature—arise: there are now 8 pairwise assignments and 6 maximal cliques, rather fewer overall than in the original case of Fig. 1.13. However, the important factor is that the largest maximal clique still indicates the most likely interpretation of the image, so the technique is inherently highly robust.

Fig. 1.15(a) shows a pair of cream biscuits which are to be located from their “docker” holes—this strategy being advantageous since it has the potential for highly accurate product location prior to detailed inspection. The holes found by a simple template matching routine are indicated in Fig. 1.15(a): the template used is rather small and, as a result, the routine is fairly fast but fails to locate all holes; in addition, it can give false alarms. Hence an “intelligent” algorithm must be used to analyze the hole location data. Analysis of the data in the above example yields two nontrivial maximal cliques, each corresponding correctly to one of the two biscuits in the image.

## 1.3.6 Using the generalized Hough transform (GHT) to save computation

In these examples, checking which subgraphs are maximal cliques is a simply-stated problem. Unfortunately, the execution time of an optimal maximal clique algorithm is bounded
not by a polynomial in M (for a match graph containing maximal cliques of up to M nodes) but by a much faster varying function. Specifically, the task of finding maximal cliques is known to be “NP-complete” and runs in exponential time. Thus, whatever the run-time may be for values of M up to about 6, it will typically be 100 times slower for values of M up to about 10, and 100 times slower again for M greater than ~14.

We shall now see how the GHT can be used as an alternative to the maximal clique approach. To apply the GHT, we first list all the features and then accumulate votes in parameter space at every possible position of a localization point L consistent with each pair of features (Fig. 1.16). To proceed it is necessary merely to use the interfeature distance as a lookup parameter in the GHT R-table. For indistinguishable point features this means that there must be two entries for the position of L for each value of the interfeature distance. The procedure is illustrated by the general quadrilateral example of Fig. 1.13: this leads to 7 peaks in parameter space, whose weights are 6, 1, 1, 1, 1, 1, 1 (see Fig. 1.13(c)). A similar situation applies for Fig. 1.14. Close examination of Figs. 1.13 and 1.14 indicates that every peak in parameter space corresponds to a maximal clique in the match graph. Indeed, there is a one-to-one relation between the two, so correct compatibilities all contribute both to a large maximal clique and to a large peak in parameter space. This situation still applies even when occlusions occur or additional features are present (see Fig. 1.14).

Finally, consider again the example of Fig. 1.15(a), this time obtaining a solution using the GHT. Fig. 1.15(b) shows the positions of candidate object centers as found by the GHT. The small isolated crosses indicate the positions of single votes, and those very close to the two large crosses lead to voting peaks of weights 10 and 6 at these respective positions. Hence object location is both accurate and robust, as required (Davies, 1988b).

We next compare the computational requirements of the maximal clique and GHT approaches to object location. For simplicity, imagine an image that contains just one wholly visible example of an object possessing n features and that we are trying to recognize it by seeking all possible pairwise compatibilities.

![](img/fe161b7f6e96e35e7e853eece52c6dce_47_0.png)

![](img/fe161b7f6e96e35e7e853eece52c6dce_47_1.png)

FIGURE 1.15 Location of cream sandwich biscuits; (a) two cream sandwich biscuits with crosses indicating the result of applying a simple hole detection routine; (b) the two biscuits reliably located by the GHT from the hole data in (a): the isolated small crosses indicate the positions of single votes. © AVC 1988.

![](img/fe161b7f6e96e35e7e853eece52c6dce_48_0.png)

FIGURE 1.16 Method for locating L from pairs of feature positions: each pair of feature points gives two possible voting positions in parameter space, when objects have no symmetries. When symmetries are present, certain pairs of features may give rise to up to 4 voting positions: this is confirmed on careful examination of Fig. 1.15(b).

For an object possessing n features, the match graph contains n² nodes (i.e., possible assignments), and there are n²C₂ = n²(n² − 1)/2 possible pairwise compatibilities to be checked in building the graph. The amount of computation at this stage of the analysis is O(n⁴). To this must be added the cost of finding the maximal cliques. Since the problem is NP-complete, the load rises at a rate which is close to being exponential in n².

Now consider the cost of getting the GHT to find objects via pairwise compatibilities. As has been seen, the total height of all the peaks in parameter space is equal to the number of pairwise compatibilities in the match graph. Hence the computational load is of the same order, O(n⁴). Next comes the problem of locating all the peaks in parameter space. For an N × N image only N² points have to be visited in parameter space and the computational load is O(N²), though keeping a running record of the maximum location during voting can reduce it considerably (Davies, 1988b).

## 1.3.7 Part-based approaches

Whereas the object location approaches described above tend to rely on objects following quite well-defined geometric models, a totally distinct approach is to use methods such as deformable models to locate and recognize them. The aim of such approaches is to take account of variations in appearance resulting from changes in illumination, viewpoint, and properties such as shape and color. This is particularly important when searching for faces or pedestrians in road scenes, to take two important examples. Methods in this category include rigid templates (Dalal and Triggs, 2005), bag-of-features (Zhang et al., 2007), deformable templates (e.g., Cootes and Taylor, 2001), and part-based models (e.g., Amit and Trouvé, 2007; Leibe et al., 2008). Deformable parts models are trained using collections of parts arranged in deformable configurations. This approach came to the fore in 2010 with the work of Felzenszwalb et al. (2010) when it was shown to lead to efficient, accurate, state-of-the-art results on difficult data sets.

Deformable parts models (DPMs) are based on the idea that objects can be considered as collections of parts. Thus, to detect objects such as faces, it should only be necessary to locate the parts and examine their interrelationships. This can be carried out by identifying parts and their bounding boxes and then making proposals for combining them into larger
bounding boxes representing objects. Basically, once object bounding boxes have been found, these regions are protected from further analysis by nonmaximum suppression. In practice, this means giving each potential bounding box a score, keeping the highest score and skipping any that overlap an already existing bounding box by a critical percentage, e.g., 50%. This highly successful approach achieved state-of-the-art results on the PASCAL VOC 2006, 2007, and 2008 benchmarks (Everingham et al., 2006; 2007; 2008) and “established itself as the de-facto standard for generic object detection” (Mathias et al., 2014). Mathias et al. tested the DPM approach very thoroughly and showed that it could achieve top performance for face detection.

Interestingly, the DPM approach permitted the location of overtly 3-D objects—but without their 3-D geometry having to be taken directly into account, this being achieved by sufficiently varied training on the relevant types of object. Another welcome capability is that the approach can also be very effective for locating articulated objects.

The DPM approach is highly significant as it formed the basis for deep learning approaches with even higher performance ratings—as achieved by Bai et al. (2016) and other workers. (See Part F for deep learning methods.)

## 1.4 Part C – 3-D object location and the importance of invariance

### 1.4.1 Introduction to 3-D vision

In the earlier parts of this chapter, it has generally been assumed that objects are essentially flat and are viewed in such a way that there are only three degrees of freedom—namely, the two associated with position, and a further one concerned with orientation. While this approach was adequate for carrying out many useful visual tasks, it is inadequate for interpreting most outdoor or indoor scenes or even for helping with quite simple robot assembly and inspection tasks. Indeed, over the past few decades a considerable amount of theory has been developed and backed up by experiment, to find how scenes composed of real 3-D objects can be understood in detail.

In general, this means attempting to interpret scenes in which objects may appear in totally arbitrary positions and orientations—corresponding to six degrees of freedom. Interpreting such scenes, and deducing the translation and orientation parameters of arbitrary sets of objects, takes a substantial amount of computation—partly because of the inherent ambiguity in inferring 3-D information from 2-D images. However, a variety of approaches is available for proceeding with 3-D vision, and subtle combinations of them will often be needed to successfully interpret 3-D scenes.

Before proceeding further, we present the imaging equation for a general point (X, Y, Z) in a scene, under what is known as ‘perspective projection’; this yields the image point:

(x, y) = (f X / Z, f Y / Z)  (1.49)

where f is the focal length of the lens being used.

We can now introduce the approach adopted by the human visual system—that of binocular vision. The camera system that is used for this purpose is depicted in Fig. 1.17. With
