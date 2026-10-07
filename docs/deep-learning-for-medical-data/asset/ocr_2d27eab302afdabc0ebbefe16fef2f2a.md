# CONCLUSION

mance further. However, the effectiveness of integrating expert knowledge as priors in a deep learning model remains a point of contention. As discussed in the bitter lesson, Sutton, 2019, expert knowledge might hamper a deep learning model from discovering efficient solutions to a decision problem. General methods that benefit from scale in data and compute have historically outperformed custom methods. GPT-style language models contain little to no expertise from linguistics, and have proven to be highly effective. Incorporating invariants should be evaluated on a case-by-case basis. And as the size of models and datasets grows, we might find that they provide a diminishing impact on performance.

**Research Question 2:** How can we motivate the deep learning research community to optimize models for real medical problems?

To aid the study of deep learning for medical problems, we proposed PCAM, a dataset derived from Camel16. This dataset is structured similarly to typical deep learning benchmarks such as CIFAR-10. We demonstrate improvement on the PCAM benchmark translates to improvements on the large-scale Camel16 benchmark. Since its release, PCAM has been the center of a Kaggle challenge, with 1149 teams competing to improve performance on the challenge. The accompanying paper has been cited 175 times since, and as the dataset has been used as a benchmark for groundbreaking research such as CLIP (Radford et al., 2021).

**Research Question 3:** Do medical imaging deep learning models benefit from contrastive predictive coding for self-supervised representation learning?

Next, we studied how contrastive representation can learn medical imaging. We identified that CPC on its own performs well, but suffers from nuisance factors in medical images. By carefully incorporating a set of augmentations specific to the medical tasks, we found improved representations which translated to better downstream prediction in both histopathology and X-ray data.

**Research Question 4:** Can we optimize deep learning models effectively without end-to-end backpropagation?

As the scale of deep learning architecture grows, the cost of building the model training infrastructure explodes. To enable synchronized gradient backpropagation across the full network, computational nodes need to be connected with high-bandwidth channels and physically colocated. We explore contrastive representation learning as a for training large models without the