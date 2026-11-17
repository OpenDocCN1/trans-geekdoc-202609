
第 6 章介绍了一种用于有效识别哮喘发病的临床决策支持系统。它探讨了包括机器学习和数据分析在内的先进技术如何集成到临床工作流中，以增强哮喘的早期检测和管理。

第 7 章深入探讨了深度学习和计算机视觉在眼病早期诊断中的应用。它讨论了利用这些技术分析医学图像，从而实现对糖尿病视网膜病变和青光眼等疾病的早期检测和干预。

第 8 章探索了人机交互与人工智能的融合，从而促成了脑机交互的出现。它深入探讨了这一跨学科领域的进展，强调了其通过大脑与计算机之间的直接通信来彻底改变医疗保健的潜力。

第 9 章专注于标准化电子健康记录（EHR）数据的挖掘，并进行了深入探讨。本章考察了通过数据挖掘技术从标准化 EHR 数据中提取知识和洞察的过程。它探讨了与挖掘 EHR 数据相关的挑战和机遇，包括数据质量问题、数据集成挑战以及处理敏感患者信息的伦理考量。此外，本章还介绍了有效挖掘 EHR 数据以支持各种医疗保健应用（如临床决策、预测分析和人群健康管理）的创新解决方案和方法。

第 10 章深入探讨了数据库在流行病学形势中的关键作用。本章强调了数据库在流行病学研究中的重要性，全面概述了其在数据收集、管理和分析中的作用。它探讨了流行病学中常用的不同类型的数据库，包括疾病监测系统。此外，本章还讨论了与数据库实施相关的挑战和注意事项，例如数据标准化和隐私保护。

在本书中，我们旨在讨论技术和数据驱动方法在医疗保健领域的进步与潜力。

## 献辞

本书献给所有为本书贡献宝贵工作的作者。此外，本书还献给所有直接或间接支持编辑 吉塔·拉妮 博士、普拉迪普·库马尔·蒂瓦里 博士和 维杰亚帕尔·辛格·达卡 博士按时完成本书的每个人。

## 贡献者列表

- **阿努·塞尼**  
  GB Pant DSEU, Okhla-1 Campus, Delhi, India

- **E. 弗兰西·伊鲁达亚·拉妮**  
  Department of Electronics and Communication Engineering, Francis Xavier Engineering College, Tirunelveli, Tamil Nadu, India

- **E. 芬汀·伊鲁达亚·拉吉**  
  Department of Electrical and Electronics Engineering, Dr. Sivanthi Aditanar College of Engineering, Thoothukudi, Tamil Nadu, India

- **吉塔·拉妮**  
  Department of Computer and Communication Engineering, Manipal University Jaipur, Jaipur, India

- **赫塔·帕特尔**  
  Manipal University Jaipur, Jaipur, India

- **卡妮卡·索尼**  
  National Institute of Technology, Delhi, India

- **M. 基鲁蒂加·德维**  
  Department of Computer Science and Engineering, Sri Sai Ram Engineering College, Chennai, India

- **米特·奥扎**  
  Manipal University Jaipur, Jaipur, India

- **穆妮卡·阿加瓦尔**  
  Dayanand Sagar University, Bangalore, Karnataka, India

- **曼尼什·迪克希特**  
  Department of Computer Science and Engineering, Madhav Institute of Technology and Science, Gwalior, Madhya Pradesh, India

- **尼特什·普拉丹**  
  LNM Institute of Information Technology, Jaipur, India

- **尼哈·科利**  
  GD Goenka University, Gurugram, India

- **M.R. 普佳**  
  Vidyavardhaka College of Engineering, Mysuru, Karnataka, India

- **里蒂克**  
  GB Pant DSEU, Okhla-1 Campus, Delhi, India

- **拉吉尼**  
  GB Pant DSEU, Okhla-1 Campus, Delhi, India

- **舒施马·汉斯**  
  Amity University, Dubai Campus, Dubai, United Arab Emirates

- **苏尼塔·库马里**  
  GB Pant DSEU, Okhla-1 Campus, Delhi, India

- **萨尔达·杜贝**  
  Department of Computer Science and Engineering, Madhav Institute of Technology and Science, Gwalior, Madhya Pradesh, India

- **希瓦尼·巴特拉**  
  KIET Group of Institutions, Delhi-NCR, Ghaziabad, Uttar Pradesh, India

- **谢莉·萨奇德瓦**  
  National Institute of Technology, Delhi, India

- **T. 卢尔图·普什普拉杰**  
  Department of Chemistry, Tirunelveli Dakshina Mara Nadar Sangam College, Tirunelveli, Tamil Nadu, India

- **维杰亚帕尔·辛格·达卡**  
  Department of Computer and Communication Engineering, Manipal University Jaipur, Jaipur, India

- **维奈·库马尔**  
  KIET Group of Institutions, Delhi-NCR, Ghaziabad, Uttar Pradesh, India

- **瓦沙利亚·阿利亚**  
  GD Goenka University, Gurugram, India

## 第 1 章

### 医疗保健中联邦学习的作用：综述

吉塔·拉尼³，米特·奥扎¹，赫塔·帕特尔¹，维杰亚帕尔·辛格·达卡³，*和舒施马·汉斯²

¹ Manipal University Jaipur, Jaipur, India ² Amity University, Dubai Campus, Dubai, United Arab Emirates ³ Department of Computer and Communication Engineering, Manipal University Jaipur, Jaipur, India

**摘要：** 在现代，通过采用新兴技术和人工智能的先进应用，自动化医疗诊断呈现出繁荣之势。这些技术需要大量数据来训练模型并精确预测疾病或障碍。多个组织可以为此类系统提供数据，但在共享数据的同时保持数据隐私是一项重大挑战。此外，在医疗保健领域为机器学习和深度学习模型的性能提升提供大型数据集，同时保持患者医疗保密性的完整性，也是一个令人担忧的问题。因此，迫切需要保护医疗数据的隐私。这需要使用最前沿的技术，其中共享原始数据的需求被完全消除，同时每个组织都能获得用于处理数据的定制基础设施。跨孤岛联邦学习模型基于从多个客户端去中心化收集数据权重的概念，然后在中央服务器上进行建模和聚合处理，从而在真正意义上保持数据隐私。本稿的作者们对联邦学习中不同的基于深度学习的模型进行了详细的比较研究，并探讨了它们如何高效地将肺部 X 射线图像分为三类：Covid-19、肺炎和正常。这项研究可以为期待在医疗保健领域应用基于深度学习的模型的跨孤岛联邦学习的研究人员提供基准。

**关键词：** Covid-19，诊断，深度学习，联邦，医疗，机器学习，分割，X 射线。

### 引言

当 Covid-19 大流席卷全球时，除了常规 RT-PCR 检测外，找出各种检测新型病毒存在的方法变得至关重要。全球的科学家和研究人员已经研究、开发并提出了许多检测新型 Covid-19 病毒的方法。许多研究人员还通过机器学习技术，利用肺部 CT 扫描和 X 射线提供了多种检测 Covid-19 和肺炎的方法。但是，通过这些机器学习和深度学习模型进行准确预测以进行检测，需要大量数据集来训练模型。在实际场景中，由于系统限制，这些大型数据集要么不可行，要么会损害患者的医疗保密性。尽管我们可以使用市场上许多图像标注工具，但可行性问题依然存在。这是因为这类工具和服务非常昂贵，并且还需要专家监督和精通，尤其是当它们用于疾病诊断时。除了金钱障碍，可行性问题还指由于传输大型数据集进行集中化而产生的通信开销 [1]。此类问题存在于医疗保健领域以及所有需要模型在不侵犯用户隐私的前提下，借助多个客户端的数据进行学习和训练的领域。

传统机器学习和深度学习在医疗保健领域的应用已经被各种研究人员用于肿瘤预测 [2]、Covid-19 筛查 [3, 4]、疾病预测 [5]、心血管疾病预测 [6]、冠状动脉疾病预测 [7]、糖尿病预测 [8]、青光眼检测 [9] 等。2016 年，Google 也遇到了类似的用户隐私问题，当时该团队创造了“联邦学习”这一术语，倡导一种先进且新颖的方法，利用移动设备的分布式数据进行训练。此外，该方法展示了如何仅通过使用本地移动设备的参数聚合来更新中央模型 [10]。联邦学习本质上仅基于本地机器学习模型传递的参数来训练中央模型。除了仅共享参数外，参数在传递前还会被加密，从而提高数据隐私性。联邦学习与分布式学习的区别在于，联邦学习的主要目标是在不同客户端的大型数据集上进行训练，而无需传输原始数据。而分布式学习则侧重于在客户端之间分配计算资源 [11]。将这种联邦学习与跨孤岛迁移学习相结合，为基于大量训练数据集而无需实际交换或传输数据的更准确创新打开了无限可能性。在跨孤岛
