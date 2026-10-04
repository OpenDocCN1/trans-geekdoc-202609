

信息科学与技术系，金迪学院，古因迪安纳大学，钦奈，泰米尔纳德邦，印度

[vanajar@auist.net](mailto:vanajar@auist.net)

Andrea Rodríguez

媒体与界面实验室（LAMEIN）理学院与技术学院，图库曼国立大学，圣米格尔德图库曼，阿根廷

[aprodriguez@herrera.unt.edu.ar](mailto:aprodriguez@herrera.unt.edu.ar)

María de Lourdes Sánchez

先进信息技术研究小组（GITIA），国立技术大学，图库曼地区学院，圣米格尔德图库曼，阿根廷

[mls.ossoft@gmail.com](mailto:mls.ossoft@gmail.com)

Dhrubasish Sarkar

阿米蒂信息技术学院，阿米蒂大学，加尔各答，印度

[dhrubasish@inbox.com](mailto:dhrubasish@inbox.com)

Ramani Selvanambi

计算机科学与工程学院，维洛尔理工学院，维洛尔，泰米尔纳德邦，印度

[ramani.s@vit.ac.in](mailto:ramani.s@vit.ac.in)

Harbinder Singh

电子与通信工程，CEC Landran，旁遮普邦，印度

[harbinder.ece@gmail.com](mailto:harbinder.ece@gmail.com)

Simrandeep Singh

电子与通信工程，昌迪加尔大学，旁遮普邦，印度

[simrandeepsingh.cgc@gmail.com](mailto:simrandeepsingh.cgc@gmail.com)

Shweta Sinha

阿米蒂大学哈里亚纳邦，印度

[meshweta7@rediffmail.com](mailto:meshweta7@rediffmail.com)

Rajshree Srivastva

计算机科学与工程系，DIT大学，德拉敦，印度

[rajshree.srivastava27@gmail.com](mailto:rajshree.srivastava27@gmail.com)

Amit Thakkar

Smt. Kundanben Dinsha Patel 信息技术系，Chandubhai S. Patel 技术学院，查洛塔尔科学与技术大学，古吉拉特邦，印度

[amitthakkar.it@charusat.ac.in](mailto:amitthakkar.it@charusat.ac.in)

Diksha Thakur

电子与通信工程系，昌迪加尔大学，莫哈利，旁遮普邦，印度

[13dishathakur@gmail.com](mailto:13dishathakur@gmail.com)

Daiyaan Ahmed Shaik

计算机科学与工程学院，维洛尔理工学院，维洛尔，泰米尔纳德邦，印度

[daiyaanahmed.shaik2016@vitstudent.ac.in](mailto:daiyaanahmed.shaik2016@vitstudent.ac.in)

Adrián Will

先进信息技术研究小组（GITIA），国立技术大学，图库曼地区学院，圣米格尔德图库曼，阿根廷

[adrian.will@gitia.org](mailto:adrian.will@gitia.org)

# 1 人工智能在细胞粘附预测中应用于骨组织工程的综述

María de Lourdes Sánchez 先进信息技术研究小组（GITIA），国立技术大学，图库曼地区学院，圣米格尔德图库曼，阿根廷 Adrián Will 先进信息技术研究小组（GITIA），国立技术大学，图库曼地区学院，圣米格尔德图库曼，阿根廷 Andrea Paola Rodríguez Laboratorio Advanced Informatics Technology Research Group (GITIA)，国立技术大学，图库曼地区学院，圣米格尔德图库曼，阿根廷 Luis Octavio Gónzalez-Salcedo Grupo Materials Catalysis and Environmental Research Group，工程学院与行政学院，哥伦比亚国立大学 – 帕尔米拉总部，帕尔米拉，哥伦比亚

## Abstract

人工智能（AI）正在以快速的速度改变科学、技术以及社会的各个方面，催生了所谓的第四次工业革命。在本章中，我们回顾了有关人工智能在骨组织工程中的应用的文献，更具体地说是骨支架中细胞粘附的应用。所发现的工作非常少（仅有六项），我们根据所使用的 AI 技术对其进行分类。我们在本章中想要解决的问题是使用了哪些 AI 技术，以及它们具体用于什么。

本章表明，最常用的 AI 工具是人工神经网络，其类型各不相同，其次是细胞自动机和多智能体系统。预期用途各不相同，但主要与理解所涉及的变量和调整一个提供洞察力并允许支架设计过程更好、更明智的模型有关。

关键词：骨组织工程，人工智能，干细胞，支架，细胞粘附，

## 1.1 Introduction

再生医学是一个多学科专业，旨在维持、改善或恢复细胞、组织和器官的功能。它基于四个支柱：细胞治疗、器官移植、生物医学工程，最后是组织工程（[Rodríguez et al., 2013](#bodymatter-001.xhtml#b_9783110648195-001_ref_034)）。

骨组织工程（BTE）是再生医学的组成部分。其主要目标是修复受损骨骼的形状和功能。骨缺损的大小是一个关键因素，因为它不会自发再生，需要手术干预。在这方面，目前许多人正好受到骨骼或关节问题的困扰。在老年人中，这些影响约占可发展的慢性疾病的 50%，导致疼痛和身体残疾，在某些情况下需要手术、骨移植或植入物（[Moreno et al., 2016](#bodymatter-001.xhtml#b_9783110648195-001_ref_026)）。

此外，再生医学的一个问题是需要许多器官移植，但捐赠者非常少。这导致与组织工程的重要合作，形成了骨重建的有希望的策略，并在开发生物工程结构作为此目的的可能解决方案方面发挥作用（[Roseti et al.,2017](#bodymatter-001.xhtml#b_9783110648195-001_ref_035)）。

根据 [Moreno et al. (2016](#bodymatter-001.xhtml#b_9783110648195-001_ref_026)) 和 [Roseti et al. (2017](#bodymatter-001.xhtml#b_9783110648195-001_ref_035))，血液是最常移植的，其次是骨移植。尽管在临床环境中，描述和使用了十多年来的治疗方案取得了成功，但在将植入物置入体内后可能会出现一些不便，因为可能会发生感染（[Gaviria Arias et al., 2018](#bodymatter-001.xhtml#b_9783110648195-001_ref_018)）。

组织工程在克服这些限制方面发挥着主要作用，成为使用种植有生长因子和间充质干细胞（MSC）的多孔三维基质修复骨损伤的有利领域。这些基质使用不同的技术构建，被称为支架。一旦构建并植入，MSC 或其他类型的细胞（即前成骨细胞）会被接种在支架表面，并在生长因子的帮助下刺激和促进人体组织再生的自然过程，以产生新的骨骼（[Moreno et al., 2016](#bodymatter-001.xhtml#b_9783110648195-001_ref_026); [Suárez Vega et al., 2017](#bodymatter-001.xhtml#b_9783110648195-001_ref_036)）。

组织工程利用人体再生的自然能力，结合工程学和生物学来替代或修复受损组织（[Moreno et al., 2016](#bodymatter-001.xhtml#b_9783110648195-001_ref_026); [Granados et al., 2017](#bodymatter-001.xhtml#b_9783110648195-001_ref_021)）。

