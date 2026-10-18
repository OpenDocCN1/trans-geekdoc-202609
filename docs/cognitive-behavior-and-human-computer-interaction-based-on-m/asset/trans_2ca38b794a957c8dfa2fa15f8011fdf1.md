

12. Howard, A., Zhu, M., Chen, B., Kalenichenko, D., Wang, W., Weyand, T., Andreetto, M., Adam, H., MobileNets: Efficient Convolutional Neural Networks for Mobile Vision Applications. *ArXiv*, abs/1704.04861, 1–9, 2017.

13. Deng, J., Dong, W., Socher, R., Li, L., Li, K., Fei-Fei, L., ImageNet: A large-scale hierarchical image database. *2009 IEEE Conference on Computer Vision and Pattern Recognition*, pp. 248–255, 2009.

14. Jain, A.K., Ross, A., Prabhakar, S., An introduction to biometric recognition. *IEEE Trans. Circuits Syst. Video Technol*., 14, 1, 4–20, 2004.

15. Burr, W., Dodson, D., Polk, W., *Electronic Authentication Guideline*, USA, 2006.

16. Abadi, M., Barham, P., Chen, J., Chen, Z., Davis, A., Dean, J., Devin, M., Ghemawat, S., Irving, G., Isard, M., Kudlur, M., Levenberg, J., Monga, R., Moore, S., Murray, D.G., Steiner, B., Tucker, P., Vasudevan, V., Warden, P., Wicke, M., Yu, Y., Zheng, X., TensorFlow: a system for large-scale machine learning. *Proceedings of the 12th USENIX conference on Operating Systems Design and Implementation*, pp. 265–283, 2016.

# 8

Feature Optimized Machine Learning Framework for Unbalanced Bioassays

**Dinesh Kumar**^([1](#c08.xhtml#rfn-1)[\*](#c08.xhtml#rfn-st1)), **Anuj Kumar Sharma**^([2](#c08.xhtml#rfn-2)), **Rohit Bajaj**^([3](#c08.xhtml#rfn-3)) and **Lokesh Pawar**^([3](#c08.xhtml#rfn-3))

^([1](#c08.xhtml#fn-1))Department of CSE, Guru Kashi University, Bathinda, India

^([2](#c08.xhtml#fn-2))Department of CSE, BRCMCET, MD University, Rohtak, India

^([3](#c08.xhtml#fn-3))Department of CSE, Chandigarh University, Chandigarh, India

[\*](#c08.xhtml#fn-st1)*Corresponding author*: [kdinesh.gku@gmail.com](mailto:kdinesh.gku@gmail.com)

> *Abstract*

> 在本研究中，我们讨论了活检；活检是由外科医生进行的一种医疗程序，用于检测患者体内疾病的扩散情况。我们在标准数据库上应用了特定的机器学习方法，以获取更准确的数据。本文旨在发现数据库的精确度得到了提高。作者收集了外科医生提供的活检数据库，并使用名为“类平衡”（class balance）的工具执行类平衡过程。随后，我们应用了四种机器学习算法，分别是多层感知机（Multilayer Perceptron）、袋装法（Bagging）、随机委员会（Random Committee）和 J48。类平衡器（Class Balancer）是一种简单的过滤器，用于为每个实例分配权重，使得数据集中每个类的实例具有相同的值，从而保持数据集中所有实例的总和不变。通过特定实验观察到，多层感知机（Multilayer Perception）和袋装法（Bagging）算法表现出色，提高了准确率，降低了误差，并提高了 TP（真阳性率）。本研究论文将提供一种提高数据准确性的有效方法。

> ***Keywords*:** Bagging, 活检, J48, 机器学习, 多层感知机, 随机委员会

## 8.1 Introduction

活检是由外科医生进行的一种医疗检测过程，以便我们了解受感染组织的情况。在医学上，如果特定组织或体液存在问题，我们会切除该部分并在实验室中进行检测以了解问题所在。当组织的初始阶段不正常时，医生通常倾向于进行活检。如果用简单的话来定义活检，那么从体内取出组织称为活检。活检主要用于癌症，但也有助于其他情况。活检通常用于癌症 \[4, 26\]、黑色素瘤和肝硬化。活检并非复杂的程序，但它取决于患者的状况；在某些情况下，它是切除少量组织，而在某些情况下，它是切除器官并在实验室中进行检测。活检为确定最恶性肿瘤提供了方法。当整个区域从患者体内切除时，受感染组织通常在病理学家的指导下使用显微镜进行检查，这被称为切除性活检（excisional biopsy）。切开性活检（incisional biopsy）是指只切除特定区域，而不是像切除性活检那样切除整个部分。切开性活检也称为穿刺活检（core biopsy）。当使用针头抽取体液且不会扰乱整个结构时，这个过程称为穿刺活检 \[11, 25\]。当怀疑患有疾病时，可以应用多种活检方法。切除性活检是试图切除整个病变。在测量病变周围未受累组织时，会分析样本的切缘以检查疾病是否已扩散到活检区域之外。“清晰切缘”或“阴性切缘”意味着在活检样本的边缘未发现疾病。“阳性切缘”意味着发现了疾病，可能需要更广泛的切除，具体取决于诊断结果。对活检的病理学评估可以确定病变是良性还是恶性，并有助于区分各种类型的恶性肿瘤。与取样病变的活检不同，更大的切除样本（称为切除术，resection）可能会送交病理学家，通常由试图从患者体内切除已知病变的专科医生进行。例如，病理学家会检查乳房切除术样本，无论之前的非切除性乳房活检是否已经确诊了乳腺癌。在某些情况下，从组织表层（例如口腔内）刮取细胞就足以提供良好的评估样本。这种“刮取活检”可能会让人感到不适，但并不疼痛，因此不需要麻醉。宫颈筛查测试是指使用铲子或类似小刷子的工具，轻轻从女性宫颈（子宫颈部）取出一组细胞样本。然后在放大镜下检查这些细胞是否有任何异常变化（异型增生）。如果细胞显示出异常变化，则可能意味着它们具有破坏性，或者它们变得致癌的可能性增加。当您的宫颈筛查测试结果出来后，您的全科医生将能够与您讨论治疗方案，或是否需要进一步检查。您获得活检结果的速度取决于您进行手术的医院以及您病例的紧急程度。常规宫颈涂片检测的结果通常需要 10 到 14 天才能出来，而如果您的主治医生怀疑存在严重疾病（例如癌症）而进行的活检结果，可能在几天内即可得出。在医疗程序中进行活检的情况下，结果通常在极短时间内即可获得，以便在手术进行期间给予正确的治疗。

## 8.2 Related Work

