# 7

# CONCLUSION

In this thesis we revisited the core components of the deep learning toolkit and reevaluated them in the context of medical image image analysis. We identified three main areas where deep learning is falling short. In part I, we explored the benefit of integrating expert knowledge on structure and constraints in the model. Part II followed with a study on how deep learning modes can better leverage the vast amounts of unlabeled medical imaging data available. Finally, in part III, we explored how to extract better uncertainty estimates from the model to provide diagnostic risk. Let us now consider the research questions posed at the beginning of this work.

**Research Question 1**: Can roto-reflective equivariance improve accuracy and robustness of deep learning models in a large scale medical setting?

Certain medical imaging problems come with symmetry modes and nuisance factors found in the real world images typically studied in deep learning for computer vision. We explored this problem in the context of histopathology for the task of detecting metastatic tissue. Using the framework of CNNs, we designed a new architecture that captures the rotational symmetries of slide images. This new model outperforms traditional CNN architectures, even under strict equivalence of computational cost and parameter count. Moreover, the new model proved more robust to perturbations. We can conclude that in the right circumstances and especially in the face of limited data, incorporating expert knowledge in the form of model invariance improves the robustness and accuracy of deep learning models.

Looking forward, we consider that the research area of group equivariant neural networks have progressed since Cohen and Welling, 2016. Incorporating these novel methods to enable scale equivariance, continuous rotation equivariance and perhaps color equivariance, can potentially improve performance