![](bbox=[0.15, 0.07, 0.85, 0.25])

Fig. 6. Different terminologies' focus.

+   2. “Physics based” focuses on the integration of physics models or constraints in the model-data hybrid framework [68,162], incorporating physical principles in feature engineering, system modeling, and constraint-based approaches [101].

+   3. “Physics aware” emphasizes perceiving the intrinsic behavior and structural features of the system [95], aligning the ML algorithm structure or interaction structure with the physical system to achieve consistency in physics.

+   4. “Physics guided” expands the focus of “Physics aware”on visually representing degradation states or using physics knowledge to guide the data processing [79,163], the design of ML structures, algorithmic weights and biases [92], or empirical loss functions [89].

+   5. “Physics-informed” refers to the broadest framework [164] that covers the entire machine learning process, incorporating physics knowledge in various aspects along the machine learning pipelines.

Therefore, in this review, the term “PIML” (Physics-informed Machine Learning) is chosen as the discussed terminology to encompass the integration of physics knowledge within machine learning approaches.

# 2.3.2. Application areas, main motivations, and methods’ evaluation metrics

Fig. 7 presents the distribution of application areas and data sources of the studies on PIML in PHM. From Fig. 7 (a), one can see that most of the current PIML studies in PHM focus on materials damage (41.2%) because there already exists in this area numerous studies in mathematical and physical modeling of material dynamic behaviors. These studies provide a solid foundation for the rapid development of PIML models. Other applications such as aviation structure and equipment (20.0%), production equipment (13.0%), bearing and gearbox (15.0%), and power grid (9%) also attract more attention from the research community in recent years. Besides, considering data sources Fig. 7 (b), we find that most data sources for PIML studies come from simulation (30%). Also, the most used benchmark-marking datasets are Turbo engine simulation dataset (C-MAPSS and AGTF30) and battery dataset (Oxford and NASA). The studies of PIML models for real systems are limited to small experimental platforms (16%). Those observations can be explained by the lack of exploitable physics-based knowledge of real systems that are usually difficult to model. Fig. 8 shows the number of publications concerning PIML in PHM per year. It highlights an increasing interest of the research community in this topic. One can see that the number of publications per year significantly increased after 2020. The research in materials, bearings, gears, aerospace structures, and power systems has garnered significant attention.

Fig. 9 presents statistical results of relevant research with respect to data quality. One can see that a large proportion of PIML

![](bbox=[0.11, 0.7, 0.89, 0.89])

Fig. 7. Statistical results of main application areas and data sources of PIML in PHM.