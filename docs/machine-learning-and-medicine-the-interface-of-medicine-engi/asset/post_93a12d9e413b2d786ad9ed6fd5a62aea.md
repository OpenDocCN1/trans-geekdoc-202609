
gies present in the reference reports. Furthermore, F1RG_ER ensures that the present, absent, and unknown pathologies are correctly related in the reports. Considering these findings, these two metrics are essential for model comparison. Although these metrics effectively and efficiently enhance RL training, models frequently produce reports with incomplete sentences. This deficiency is evident in numerous state-of-the-art proposals, and despite the efficacy of TA, it still occurs occasionally. It is evidenced at the end of the third report in Table 4. This phenomenon arises from models learning that specific syntactic structures can benefit chest RRG-oriented metrics like F1RG_ER, even if they do not constitute syntactically correct sentences. Moving forward, we advocate for further research into novel metrics using alternative deep learning algorithms, such as LLMs like GPT-4 [50] or LLaMA [51].

Several aspects of the proposed approach for real-world RRG scenarios merit attention, including multilingual support, standardization of reports, and improvements in picture archiving and communication systems (PACS). Since the decoder model primarily operates with English words, it encounters specific difficulties when used in other languages. Thus, it would be necessary to remove the last layer of the decoder model and adjust it based on the desired language; however, the rest of the model remains language-independent. Another challenge lies in the lack of standardization in report writing across different institutions, leading to variations in reporting guidelines. Consequently, RRG models can assist in integrating new reporting guidelines to standardize and unify databases for RRG. Furthermore, our approach can enhance PACS, which are commonly used in healthcare for securely storing and transmitting electronic images and clinical reports. Collaborating with expert radiologists, we can integrate RRG models to streamline processes within PACS, such as preparing automatic draft reports that radiologists can interactively correct. This approach can improve diagnostic efficiency and expert assistance times while enhancing the standardization and homogenization of reports.

The strengths and weaknesses of our model have been highlighted using different metrics. However, another essential aspect to analyze is the integration of the proposed workflow into the clinical setting. Given that the system relies on a VED deep learning model, its deployment only requires a computer with a GPU with at least 12 GB of memory. The model specializes in chest radiographs from different position views, such as antero-posterior, lateral, posteroanterior, and lateral decubitus. Therefore, it can integrate and analyze a wide variety of chest radiographs.

The scope of this work is focused on chest radiographs. However, our approach is not limited solely to its application in chest radiographs. The proposed approach is flexible and independent, allowing it to be applied to other radiological scenarios. Therefore, our approach can be seamlessly adapted for radiographs of different body parts. The only aspect requiring modification is the reward optimization during RL training. Since F1RG_ER primarily specializes in chest-related pathologies, this metric should be replaced with another relevant to the radiological scenario where our approach is intended for application. The remaining components, such as the encoder, decoder, TA, and decoding strategies, are independent of the radiological scenario. Despite the flexibility and independence of the approach, the major limitation for application to other radiological scenarios depends on the availability of training data. Acquiring large datasets to train VED models is crucial for improving the quality of reports and enhancing their applicability to different scenarios.

## 5. Conclusions

Chest RRG poses a challenge due to the limited data availability and the diverse nature of medical reports and variations in pathology expressions. Four transformer-based models were analyzed, highlighting the encoder as the key component, with SwinB being the best choice. This transformer encoder has not been previously explored in RRG. Regarding the decoder, a word-based approach trains faster and achieves more competitive results than a subword-based one.

Techniques like image data augmentation, hard negative mining, and TA were introduced. TA was shown to be an effective method to improve generalization and the quality of the generated reports regarding variability, quality, factual correctness, and completeness, which yields a model that outperforms the state of the art. Moreover, this approach paves the way for new TA approaches based on augmentation with more complex NLP techniques, such as LLM models.

Additionally, NLG-oriented metrics may not be optimal for measuring report quality, as they compare sentences and words without considering semantic meaning or alternative expressions of the same diagnosis. Thus, metrics based on NLP models specialized in chest radiology reports like F1cXb and F1RG_ER appear to be crucial in evaluating report quality.

### Author Contributions
Investigation, D.P.; methodology, D.P.; software, D.P.; supervision, A.A. and R.P.; writing—original draft, D.P.; writing—review and editing, A.A. and R.P. All authors have read and agreed to the published version of the manuscript.

### Funding
Work was partially supported by the Generalitat Valenciana under the predoctoral grant CIACIF/2022/289, with the support of valgrAI—Valencian Graduate School and Research Network of Artificial Intelligence and the Generalitat Valenciana, and cofunded by the European Union.

### Institutional Review Board Statement
Not applicable.

### Informed Consent Statement
Not applicable.

### Data Availability Statement
The data used in this study are publicly available.

### Conflicts of Interest
The authors declare no conflicts of interest.

## References

- 1. Zhao, J.; Lv, Y.; Zeng, Q.; Wan, L. Online Policy Learning-Based Output-Feedback Optimal Control of Continuous-Time Systems. IEEE Trans. Circuits Syst. II Express Briefs 2024, 71, 652–656. [CrossRef]
- 2. Gale, W.; Oakden-Rayner, L.; Carneiro, G.; Bradley, A.P.; Palmer, L.J. Producing radiologist-quality reports for interpretable artificial intelligence. arXiv 2018, arXiv:1806.00340.
- 3. Li, Y.; Liang, X.; Hu, Z.; Xing, E.P. Hybrid Retrieval-Generation Reinforced Agent for Medical Image Report Generation. In Proceedings of the Advances in Neural Information Processing Systems, Montreal, BC, Canada, 3–8 December 2018; pp. 1530–1540.
- 4. Wang, X.; Peng, Y.; Lu, L.; Lu, Z.; Summers, R.M. TieNet: Text-Image Embedding Network for Common Thorax Disease Classification and Reporting in Chest X-Rays. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, Salt Lake City, UT, USA, 18–23 June 2018; pp. 9049–9058.
- 5. Liu, G.; Hsu, T.M.H.; McDermott, M.; Boag, W.; Weng, W.H.; Szolovits, P.; Ghassemi, M. Clinically Accurate Chest X-ray Report Generation. In Proceedings of the 4th Machine Learning for Healthcare Conference, Ann Arbor, MI, USA, 9–10 August 2019; pp. 249–269.
- 6. Liu, F.; Wu, X.; Ge, S.; Fan, W.; Zou, Y. Exploring and Distilling Posterior and Prior Knowledge for Radiology Report Generation. In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, Nashville, TN, USA, 20–25 June 2021; pp. 13753–13762.
- 7. Liu, F.; You, C.; Wu, X.; Ge, S.; Wang, S.; Sun, X. Auto-Encoding Knowledge Graph for Unsupervised Medical Report Generation. In Proceedings of the Advances in Neural Information Processing Systems, Online, 6–14 December 2021; pp. 16266–16279.
- 8. Windsor, R.; Jamaludin, A.; Kadir, T.; Zisserman, A. Vision-Language Modelling For Radiological Imaging and Reports In The Low Data Regime. In Proceedings of the Medical Imaging with Deep Learning, Nashville, TN, USA, 10 July 2023; pp. 53–73.
- 9. Chen, Z.; Song, Y.; Chang, T.H.; Wan, X. Generating Radiology Reports via Memory-driven Transformer. arXiv 2020, arXiv:2010.16056.
- 10. Chen, Z.; Shen, Y.; Song, Y.; Wan, X. Cross-modal Memory Networks for Radiology Report Generation. arXiv 2022, arXiv:2204.13258.
- 11. Miura, Y.; Zhang, Y.; Tsai, E.B.; Langlotz, C.P.; Jurafsky, D. Improving Factual Completeness and Consistency of Image-to-Text Radiology Report Generation. arXiv 2021, arXiv:2010.10042.
- 12. Delbrouck, J.B.; Chambon, P.; Bluethgen, C.; Tsai, E.; Almisa, O.; Langlotz, C.P. Improving the Factual Correctness of Radiology Report Generation with Semantic Rewards. arXiv 2022, arXiv:2210.12186.
- 13. Zhang, T.; Kishore, V.; Wu, F.; Weinberger, K.Q.; Artzi, Y. BERTScore: Evaluating Text Generation with BERT. arXiv 2020, arXiv:1904.09675.
- 14. Jain, S.; Agrawal, A.; Saporta, A.; Truong, S.Q.; Duong, D.N.; Bui, T.; Chambon, P.; Zhang, Y.; Lungren, M.P.; Ng, A.Y.; et al. RadGraph: Extracting Clinical Entities and Relations from Radiology Reports. arXiv 2021, arXiv:2106.14463.
- 15. Schlegl, T.; Waldstein, S.M.; Vogl, W.D.; Schmidt-Erfurth, U.; Langs, G. Predicting Semantic Descriptions from Medical Images with Convolutional Neural Networks. In Proceedings of the Information Processing in Medical Imaging, Isle of Skye, UK, 28 June–3 July 2015; pp. 437–448.
