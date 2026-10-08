
## 12.5 CONFLICTS OF INTEREST

The authors state that they have no known competing financial interests or personal relationships that could have appeared to influence the work reported in this article.

Two authors (Van Thanh Tien Nguyen and Nhut T.M. Vo) are members of this book's editorial board but were not involved in the editorial review or the decision to publish this article. The authors state that the work has no potential conflict of interest. All authors have read and agreed to the published version of the manuscript.

## 13 Machine Learning Techniques for Multicriteria Decision-Making

Wasswa Shafik

### 13.1 INTRODUCTION

In an increasingly interconnected and complex world, decision-making often involves more than a single criterion or objective. Decision-making extends beyond mere quantitative analysis, as numerous factors of diverse nature and significance conflict to evaluating alternatives (Sookall & Fonou-Dombeau, 2023). Multicriteria decision-making (MCDM) emerges as a systematic and structured approach to navigating the intricate choices that require consideration of multiple, often conflicting criteria. By providing decision-makers with methodologies to effectively weigh and balance these criteria, MCDM offers invaluable insights and aids in making informed decisions that align with desired outcomes (Ahmed et al., 2023).

The essence of MCDM lies in acknowledging that decisions are rarely multidimensional. Whether it pertains to selecting an investment opportunity, determining the best course of action in project management, or making choices in environmental planning, decisions involve various considerations (Choudhary et al., 2023). For instance, selecting a location for a new factory, factors such as cost, proximity to suppliers and customers, environmental impact, and regulatory compliance all contribute to the decision-making process.

MCDM methods facilitate structuring these scenarios by providing a framework for objectively evaluating, comparing, and ranking choices. These methods incorporate both quantitative and qualitative criteria to capture the nuances and complexities of real-world decision scenarios (Bardini & DiCarlo, 2023). As technological advancements continue to enable the collection and analysis of amounts of data, the significance of MCDM in handling data-driven decisions has only increased.

MCDM techniques help in tackling the challenges posed by decisions influenced by various criteria, which might have different levels of importance or uncertainty. By delving into traditional approaches and contemporary integrations with machine learning (ML), we aim here to comprehensively understand MCDM’s evolution and adaptability (Maa Kouhou et al., 2023). As we navigate the intricate web of choices that shape our personal, professional, and societal landscapes, MCDM serves as a guiding compass, offering systematic pathways to decipher complexity and facilitate well-considered decisions. In the subsequent sections of this chapter, we categorize MCDM techniques, highlight their real-world applications through case studies, and explore the implications of integrating ML in this domain (Rathoriya et al., 2023). In an era where informed decisions are paramount, MCDM stands as a crucial tool in the decision-maker's toolkit, enhancing the ability to make choices with multiple objectives and criteria beyond traditional approaches (Nguyen & Vo, 2024).

In an era characterized by information abundance and interconnectedness, decision-makers face challenges beyond quantitative analysis. The analysis of an organization, the feasibility of a project, or the sustainability of a policy hinges on holistically evaluating and reconciling various criteria. MCDM emerges as a response to this complexity, offering a structured methodology to navigate the intricate decision-making landscape in scenarios involving multiple objectives, criteria, and stakeholders (Kayya et al., 2023). Traditional decision-making often falls short when confronted with the multifaceted nature of real-world choices. The oversimplification of complex scenarios can lead to suboptimal outcomes and missed opportunities. MCDM recognizes that decisions rarely conform to a single dimension and, therefore, encompasses a broader perspective (Deb et al., 2023). It encompasses objective and subjective factors, for quantitative metrics and qualitative considerations such as social, environmental, and ethical aspects.

The core of MCDM lies in seeking a balance between conflicting objectives. The challenge is not just to rank alternatives on individual criteria but to find a way to harmonize these criteria into a coherent decision framework (Joudar et al., 2023). MCDM provides tools for quantifying and managing trade-offs, ensuring that decisions reflect a comprehensive evaluation. Integrating technology and analytics to MCDM in this ever-evolving landscape, ML techniques have shown promise in handling vast data and deriving patterns from intricate decision spaces (Chowdhury et al., 2023). This fusion of MCDM and ML brings about the potential to enhance decision-making with predictive modeling, adaptive strategies, and insights from historical data.

### 13.1.1 THE CONTRIBUTION OF THE CHAPTER

This chapter makes a number of contributions. For one, we examine integrating ML techniques into the seven MCDM processes we will graphically present in Figure 13.1. We highlight the importance of MCDM across diverse domains, emphasizing the need for advanced techniques in complex decision scenarios. We delineate how ML techniques enhance MCDM, automating the analysis of large datasets to facilitate more informed and accurate decisions.

Our categorization of ML techniques into supervised, unsupervised, reinforcement, and deep learning also provides a structured framework for understanding their application in MCDM. We explore each technique comprehensively, supported by clear explanations and illustrative examples, aiding readers in grasping their utility, and real-world case studies showcase tangible benefits as improved accuracy and efficiency.

Machine Learning Techniques for Multicriteria Decision-Making

![](img/62c36bee0e5ae6b397770e7de372b0e7_197_0.png)

FIGURE 13.1 The seven multicriteria decision-making processes.

In the process, we briefly compare the ML techniques, outlining their strengths and limitations in diverse MCDM contexts to aid in technique selection. Finally, we propose future research directions, highlighting the potential of hybrid approaches that integrate different ML techniques to address evolving challenges in MCDM.

### 13.1. THE CHAPTER STRUCTURE

In Section 13.2, we define and elaborate on the fundamental concepts of MCDM, discussing the challenges and complexities associated with decision-making involving multiple criteria. Section 13.3 presents the role of ML in MCDM, discussing how ML can handle large-scale data, automate decision-making processes, and improve accuracy. In Section 13.4, we categorize different ML techniques based on their application in MCDM, and in Section 13.5, we review specific techniques within each category and how they can be applied to MCDM problems, for instance, decision trees for rule-based decision-making, clustering algorithms for grouping similar criteria, neural networks for complex decision patterns, and reinforcement learning for adaptive decision-making. In Section 13.6, we present challenges and considerations such as data quality, interpretability, and the need for domain expertise.

In Section 13.7, we give real-world case studies of successfully employing ML in MCDM, highlighting the benefits and outcomes achieved; in Section 13.8, we compare the strengths, weaknesses, and applicability of different ML techniques for MCDM depending on the specific problem context. Section 13.9 presents the future directions and proposes potential areas of research and development in integrating ML with MCDM; we discuss emerging trends, challenges to be addressed, and possibilities for hybrid approaches. Finally, Section 13.10 presents the conclusion, emphasizing the significance of using ML to enhance MCDM and make more informed decisions.
