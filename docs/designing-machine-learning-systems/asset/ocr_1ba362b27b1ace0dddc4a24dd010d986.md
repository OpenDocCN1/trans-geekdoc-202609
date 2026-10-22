Here is a case study to show how well weak supervision works in practice. In a study with Stanford Medicine,¹³ models trained with weakly supervised labels obtained by a single radiologist after eight hours of writing LFs had comparable performance with models trained on data obtained through almost a year of hand labeling, as shown in Figure 4-5. There are two interesting facts about the results of the experiment. First, the models continued improving with more unlabeled data even without more LFs. Second, LFs were being reused across tasks. The researchers were able to reuse six LFs between the CXR (chest X-rays) task and EXR (extremity X-rays) task.¹⁴

![](bbox=[0.13, 0.25, 0.84, 0.5])

Figure 4-5. Comparison of the performance of a model trained on fully supervised labels (FS) and a model trained with programmatic labels (DP) on CXR and EXR tasks. Source: Dunnmon et al.¹⁵

My students often ask that if heuristics work so well to label data, why do we need ML models? One reason is that LFs might not cover all data samples, so we can train ML models on data programmatically labeled with LFs and use this trained model to generate predictions for samples that aren’t covered by any LF.

Weak supervision is a simple but powerful paradigm. However, it’s not perfect. In some cases, the labels obtained by weak supervision might be too noisy to be useful. But even in these cases, weak supervision can be a good way to get you started when

13 Jared A. Dunnmon, Alexander J. Ratner, Khaled Saab, Matthew P. Lungren, Daniel L. Rubin, and Christopher Ré, “Cross-Modal Data Programming Enables Rapid Medical Machine Learning,” Patterns 1, no. 2 (2020): 100019, https://oreil.ly/nKi8E.

14 The two tasks in this study use only 18 and 20 LFs respectively. In practice, I’ve seen teams using hundreds of LFs for each task.

15 Dummmon et al., “Cross-Modal Data Programming.”