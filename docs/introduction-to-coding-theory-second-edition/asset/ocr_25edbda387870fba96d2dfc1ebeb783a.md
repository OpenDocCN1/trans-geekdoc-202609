# Exercises 23.5

23.5.1. The alternating group A₄ is sharply 2-transitive on 4 letters. Use it to construct a projective plane of order 4.

# 23.6 Designs

Designs t − (v, k, λ) and Steiner systems S(t, k, v) were defined in Chapter 7, where we also saw the single most famous design, the large Witt design S(5, 8, 24). It is closely related to the binary Golay code (see Witt’s classical papers [221] and [222]) and to the Mathieu group M₂₄. We encountered many more examples of t designs in connection with codes, starting from the projective and affine geometries which are 2-designs. As t is the central parameter, it is a natural question to ask for which t it is possible to construct t-designs. The set of all k subsets of a v set clearly is a t design for all t ≤ k. These designs are called complete designs and are not terribly interesting. Noncomplete designs are also called nontrivial.

In the definition of designs it is customary to admit also repeated blocks. In this terminology the designs of our Definition 7.3 would be called simple designs. Allowing block repetition really simplifies the construction problem.

It was shown by R. M. Wilson [220], using methods from linear algebra, that nonsimple designs exist in abundance, for all t. The case of simple non-trivial designs is much harder. For a long time not a single example of a simple nontrivial t design for t > 5 was known and it was natural to conjecture they did not exist. The reason is a link with permutation groups. It is obvious that each t transitive permutation group on v points produces simple t designs for all block sizes k < v. Just choose an arbitrary k subset and choose as blocks the orbit of this base block under the group. In fact, it suffices for the group to be t homogeneous (transitive on unordered subsets of size t). In this way the symmetric and alternating groups produce the complete designs and the Mathieu groups produce, among others, the Witt designs.

As an important consequence of the classification of the finite simple groups, all t homogeneous permutation groups (simple or not) are known (if we really believe the classification of simple groups). It turns out that, aside from the symmetric and alternating groups, there is not a single t homogeneous permutation group for t > 5. This and the fact that no nontrivial simple t designs for t > 5 were known raised the suspicion that possibly such designs could not exist because for some unknown reason t designs could only be constructed from t homogeneous permutation groups.

An indication that this was unjustified came from coding theory. The