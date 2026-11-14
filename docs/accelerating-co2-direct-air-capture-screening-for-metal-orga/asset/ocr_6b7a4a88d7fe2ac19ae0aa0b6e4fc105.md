# Article

# Accelerating CO₂ direct air capture screening for metal-organic frameworks with a transferable machine learning force field

Yunsung Lim, 1,3 Hyunsoo Park, 2,3 Aron Walsh, 2,* and Jihan Kim 1,4,*
1Department of Chemical and Biomolecular Engineering, Korea Advanced Institute of Science and Technology (KAIST), Daejeon 34141, Republic of Korea
2Department of Materials, Imperial College London, London SW7 2AZ, UK
3These authors contributed equally
4Lead contact
*Correspondence: a.walsh@imperial.ac.uk (A.W.), jihankim@kaist.ac.kr (J.K.)
https://doi.org/10.1016/j.matt.2025.102203

> **PROGRESS AND POTENTIAL** Capturing CO₂ directly from ambient air, known as direct air capture (DAC), is essential for achieving net-zero emissions. Metal-organic frameworks (MOFs) are promising porous solids for DAC, but existing computational methods either take a long time or lack the accuracy needed to model CO₂ and H₂O adsorption within the MOFs. As a result, high-throughput screenings via computational simulation struggle to identify the most effective materials for DAC. To overcome this challenge, we developed an artificial intelligence-accelerated adsorption simulation framework built on a machine learning force field (MLFF) that captures MOF-CO₂ and MOF-H₂O interactions both quickly and accurately. It enabled the screening of more than 8,000 MOFs, uncovering more than 100 high-potential candidates that conventional simulations missed. This computational platform can easily be adopted by researchers and industry to accelerate the discovery of porous materials for DAC and other gas separation needs. Our approach could enable more efficient, cost-effective carbon capture technologies and support global emission reduction goals.

# SUMMARY

Direct air capture (DAC) of CO₂ is necessary for climate change mitigation, but it faces challenges from low CO₂ concentrations and competition from water vapor. Metal-organic frameworks (MOFs) hold significant promise for DAC owing to their high surface area and adsorption-based capture processes. However, identifying optimal MOFs is hindered by structural complexity and vast chemical diversity. Here, we introduced a machine learning force field (MLFF) tailored for CO₂ and H₂O interactions in MOFs by fine-tuning a foundation model. To address smoothing issues and catastrophic forgetting, we curated the GoldDAC dataset and introduced a continual learning scheme. We further developed DAC-SIM, a molecular simulation package integrated with MLFF, including a Widom insertion. Then, we screened an extensive MOF database, uncovering high-performing MOFs and identifying chemical features for DAC applications. This approach overcomes prior limitations in describing MOF-CO₂ and MOF-H₂O interactions, providing a scalable and accurate framework for DAC research of porous materials.

# INTRODUCTION

The average global temperature has been steadily rising since the late 19th century and was approximately 1.2°C degree warmer in 2023 than the pre-industrial average.1 This warming is largely driven by greenhouse gas emissions, with CO₂ accounting for more than 60% of the effect.2 Among various strategies to manage CO₂ emission levels, direct air capture (DAC) offers a solution by capturing CO₂ directly from ambient air.3,4

This process is challenging due to trace amounts of CO₂ concentration (approximately 400 ppm) and low selective capturing of CO₂ over atmospheric water vapor.
To date, DAC technologies have predominantly relied on chemisorption of CO₂ using amines and solid alkali hydroxides, due to their strong affinity for CO₂.5,6 However, the regeneration of adsorbents is the dominant source of the total operational costs.7,8 To mitigate these issues, physisorption-based materials with weaker CO₂ interactions have been explored to reduce