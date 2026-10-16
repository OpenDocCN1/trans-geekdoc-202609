
[Table 12.2](#C19_chapter12.xhtml#t12_2) 总结了机器学习在神经外科中的潜在应用，涵盖多个领域并以多种方式影响这些领域。然而，在将其应用于神经外科情境时，机器学习仍处于相对初级阶段。尽管机器学习在神经外科已成为热门话题和研究重点，但文献现状仍存在诸多差距，使得整体水平远未完整。因此，当前关于机器学习的讨论不可避免地需要涉及未来，而未来前景充满希望。对于神经病变的诊断、治疗和预后，我们将讨论机器学习在神经外科实践中的未来作用，包括颅内（例如）和颅外（如脊髓）过程。

TABLE 12.2 Summary of the Potential Applications of Machine Learning to Neurosurgical Practice, Sorted by Diagnostic and Intraoperative Applications ([Section 12.2](#C19_chapter12.xhtml#secc012_2)) and Prognostication ([Section 12.3](#C19_chapter12.xhtml#secc012_3))

| **Area of Neurosurgery** || **Diagnosis and Intraoperative Management** || **Prognosis** |

| --- | --- | --- |

| Epilepsy || Segmentation and classification of temporal lobe epilepsy || Prediction of seizure freedom in temporal lobe epilepsy |

| --- | --- | --- |

| Neurovascular || Identification of patients within the 4.5-hour time window for acute ischemic stroke || Prediction of outcomes after mechanical thrombectomy \[[80](#C19_chapter12.xhtml#ref12_80)\] |

| Neuro-oncology || Classification, grading, and segmentation of intracranial neoplasms || Prediction of survival after surgical treatment, prediction of cancer recurrence after gamma knife radiosurgery for metastases |

| Traumatic brain Injury || Intracranial pressure monitoring || Prediction of mortality and unfavorable outcome after surgery |

| Spinal cord injury || Spinal cord segmentation, diagnosis of spinal cord injury, intraoperative monitoring of somatosensory evoked potentials || Prediction of functional outcomes, health-related quality-of-life outcomes, prolonged opioid use, and discharge disposition after surgery |

The core advantages of ML stem from its ability to analyze large and complex datasets with many predictors, its ability to determine important predictors computationally without a priori specification, and its ability to capture nonlinear relationships \[[73](#C19_chapter12.xhtml#ref12_73), [74](#C19_chapter12.xhtml#ref12_74), [75](#C19_chapter12.xhtml#ref12_75)\]. As described earlier, many studies have been conducted that leverage these ML features to develop powerful diagnostic and prognostic tools. As ML continues to grow in popularity \[[2](#C19_chapter12.xhtml#ref12_2)\], the applications of ML to the areas described in the previous sections will become more robust and take a bigger place in clinical practice. Moreover, with the advent of tools such as natural language processing (NLP) and computer vision \[[6](#C19_chapter12.xhtml#ref12_6)\], artificial intelligence tools beyond ML could begin to impact neurosurgical practice in a variety of other ways (e.g. NLP for extracting information from imaging reports \[[76](#C19_chapter12.xhtml#ref12_76)\] and computer vision for analysis of hand function after SCI \[[77](#C19_chapter12.xhtml#ref12_77)\]).

However, in addition to a more broadened scope of ML and artificial intelligence, the path forward requires future studies in ML to achieve greater methodological robustness and reproducibility before ML can be confidently introduced to neurosurgery. To achieve robustness, future literature on ML would benefit from following the 2016 guidelines created by Luo and colleagues \[[75](#C19_chapter12.xhtml#ref12_75)\], which describe a systematic approach to developing ML models. Strategies proposed by the guidelines to ensure robust analysis include using separate training and testing sets to minimize overfitting, using calibration and discrimination metrics, and, when possible, using external datasets for further validation of the model. For reproducibility, ML algorithms by their nature are difficult to express on paper, as they are frequently far too complex to describe via an equation. For this reason, we would benefit from using web-based applications to make their ML models more easily applied. This will inevitably aid the reproducibility and external validation of those studies, allowing those algorithms to eventually become an integral part of future neurosurgical practice.

## [12.6 Limitations](#C19_chapter12.xhtml#rsecc012_6)

Despite its promise, ML carries important limitations that ought to be considered when implementing it into practice. First, compared to logistic regression models, which can be written neatly in equation form, many ML models are more difficult to express in closed form due to their inherent complexity. This makes their interpretation difficult and less intuitive, which is why the development of web-based applications for ML programs developed in future neurosurgical research is crucial to overcome this inherent disadvantage. Second, as a data-driven tool, ML is inherently limited by the quality and quantity of the underlying data \[[78](#C19_chapter12.xhtml#ref12_78)\]. Small, poor-quality datasets will result in worse ML models than larger, high-quality datasets. Additionally, biases within data can make ML algorithms less generalizable. For example, an algorithm making diagnostic predictions based on data from a single hospital site may be more likely to suggest a diagnosis primarily seen at that center, making it less applicable to data from other centers. Third, there are significant medico-legal challenges that can potentially arise from the widespread and unregulated implementation of ML \[[79](#C19_chapter12.xhtml#ref12_79)\]. These challenges can arise from the ‘black-box’ interpretation of some ML algorithms, which makes it difficult to decipher the parts of the underlying data that the algorithm used to generate an output. For instance, if a user did not have a priori knowledge of the fact that an ML algorithm used the name of the hospital (an otherwise irrelevant variable) as an important predictive variable for a surgical outcome, then that user could be led into utilizing the algorithm inappropriately in multiple contexts. Careful consideration of these issues will also be vital toward properly implementing ML in the future as an adjunct to clinical decision-making in neurosurgery.

## [References](#C19_chapter12.xhtml#rreferences-9)

1.  [1.](#C19_chapter12.xhtml#rref12_1) O. Khan, J. H. Badhiwala, J. R. F. Wilson, F. Jiang, A. R. Martin, and M. G. Fehlings, “Predictive Modeling of Outcomes after Traumatic and Nontraumatic Spinal Cord Injury Using Machine Learning: Review of Current Progress and Future Directions,” (in English), *Neurospine*, vol. 16, no. 4, pp. 678–685, Dec 2019.

2.  [2.](#C19_chapter12.xhtml#rref12_2) J. T. Senders et al., “An Introduction and Overview of Machine Learning in Neurosurgical Care,” *Acta Neurochirurgica (Wien)*, vol. 160, no. 1, pp. 29–38, Jan 2018.

3.  [3.](#C19_chapter12.xhtml#rref12_3) A. V. Karhade et al., “Development of Machine Learning Algorithms for Prediction of 30-Day Mortality after Surgery for Spinal Metastasis,” *Neurosurgery*, vol. 85, no. 1, pp. E83–E91, Jul 1, 2019.

4.  [4.](#C19_chapter12.xhtml#rref12_4) M. I. Jordan and T. M. Mitchell, “Machine Learning: Trends, Perspectives, and Prospects,” (in English), *Science*, vol. 349, no. 6245, pp. 255–260, Jul 17, 2015.

5.  [5.](#C19_chapter12.xhtml#rref12_5) M. Wiering and M. van Otterlo, “Reinforcement Learning: State-of-the-Art,” (in English), *Reinforcement Learning: State-of-the-Art*, vol. 12, pp. 1–638, 2012.

