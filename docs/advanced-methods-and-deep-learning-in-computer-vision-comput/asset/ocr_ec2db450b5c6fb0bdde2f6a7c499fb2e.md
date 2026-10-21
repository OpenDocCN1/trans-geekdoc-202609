![](bbox=[0.15, 0.12, 0.85, 0.32])

FIGURE 8.1 Different settings for domain adaptation, according to how source and target class sets are related.

# 8.2.1 Domain adaptation problem formulation

Domain Adaptation (DA) is a special case of transfer learning, called Transductive Transfer Learning, in which the source and target tasks coincide (𝒯_S = 𝒯_T), whereas the discrepancy lies in the domain difference (𝒟_S ≠ 𝒟_T). In addition, domain adaptation is commonly intended in a homogeneous fashion, when the domain shift happens at a statistical level (P(X_S, Y_S) ≠ P(X_T, Y_T)) rather than being due to distinct input spaces (𝒳_S and 𝒳_T belong to the same semantic domain, e.g., urban scene images) (Wang and Deng, 2018).

Recently, some researches have considered more challenging scenarios than the standard homogeneous DA, allowing for separate sets of semantic classes in the source and target domains (𝒞_S and 𝒞_T). Depending on how the source 𝒞_S and target 𝒞_T sets are related, it is possible to identify multiple DA scenarios (Fig. 8.1):

+   - Closed Set DA: it corresponds to the homogeneous case, where semantic classes are completely shared between source and target domains (𝒞_S = 𝒞_T).
+   - Partial DA: in this setup there exist some source classes that do not appear in the target domain (𝒞_S ⊃ 𝒞_T).
+   - Open Set DA: conversely to partial DA, here the presence of some target private classes is admitted, for which no training examples in the source domain are available (𝒞_S ⊂ 𝒞_T).
+   - Open-Partial Set DA: the source and target domains include separate sets of semantic classes (Saito et al., 2020), with a subset of those in common (𝒞_S ≠ 𝒞_T, 𝒞_S ∩ 𝒞_T ≠ ∅). However, elements belonging to the class subset exclusive to the target domain have only to be acknowledged as not part of the shared classes.
+   - Boundless DA: this setup is very similar to the open set one, but objects of target private classes must be explicitly classified rather than only be associated to a general unknown target class. This setting has been recently introduced (Bucher et al., 2020) and it represents the most ambitious one, since it admits complete unawareness beforehand about semantic content of target data.