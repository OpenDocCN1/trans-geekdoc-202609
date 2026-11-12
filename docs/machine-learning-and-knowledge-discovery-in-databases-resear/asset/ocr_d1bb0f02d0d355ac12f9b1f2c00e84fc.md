![](bbox=[0.12, 0.08, 0.9, 0.21])

Fig. 4. Comparison of the generalization performance across the evaluated datasets. LCBM consistently provides the highest generalization accuracy across concept-based models, closing the gap with end-to-end black box ones.

(paired digits summed as labels). CIFAR-10 and CIFAR-100 contain 10 and 100 natural image classes, with models extracting 15 and 20 macro-class concepts, respectively [17]. Tiny ImageNet includes 200 classes but is tested on 30 concepts for added challenge [42]. Skin Lesions classifies dermatoscopic images into 4 macro categories [37]. Finally, CUB-200 [39] covers 200 bird species with species and attribute annotations.

Metrics. We use specific metrics to address each research question. All results are reported with the mean and standard deviation, computed over the test sets by repeating the experiments with three different initialization seeds.

+   1. Generalization: To assess the classification generalization performance, we compute the Task Accuracy.

+   2. Concept Representation Evaluation: We employ the Information Plane approach [36] to analyze the information retained in the different concept representations. The information plane reports the evolution of the mutual information between the concept representation and both the input x (I(C, X)) and the label y (I(C, Y)) as the training epoch increases. For models reconstructing the input from the concepts, we assess the Input Reconstruction Error by computing the Mean Squared Error (MSE) between the inputs x and their reconstructions \(\hat{x}\).

+   3. Concept Interpretability: For datasets with annotated concepts, we assess their alignment with the learnt concepts using the macro Concept F1 Score (best-match approach) and the Concept Alignment Score (CAS) [8] for concept representation alignment. Additionally, we conducted a user study with 72 participants, each answering 18 questions. The study evaluated Plausibility by asking users to (i) select an image that best represents a given concept and (ii) identify an intruder image among those representing a single concept. It also assessed Human Understanding by having participants assign a name to a set of images illustrating a concept. Finally, we provide qualitative insights through Concept Dictionaries, showcasing images with the strongest activations for each concept.

+   4. Model Interpretability: We perform Concept Interventions [16] to observe how model predictions change when concept predictions are modified. As posi-