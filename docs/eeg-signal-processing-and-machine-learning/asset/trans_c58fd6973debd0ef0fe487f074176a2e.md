

# 参考文献

84. Waldorp, L.J., Huizenga, H.M., Nehorai, A., and Grasman, R.P. (2002). Model selection in electromagnetic source analysis with an application to VEFs. *IEEE Transactions on Biomedical Engineering* 49 (10): 1121–1129.

85. Waldorp, L.J., Huizenga, H.M., Nehorai, A., and Grasman, R.P. (2005). Model selection in spatio‐temporal electromagnetic source analysis. *IEEE Transactions on Biomedical Engineering* 52 (3): 414–420.

86. Akaike, H. (1973). Information and an extension of the maximum likelihood principle. *Proceedings of the 2nd International Symposium on Information Theory, Supplement Problem Controls in Information Theory*, 267–281.

87. Chow, G.C. (1981). A comparison of information and posterior probability criteria for model selection. *Journal of Econometrics* 16: 21–33.

88. Huzenga, H.M., Heslenfeld, D.J., and Molennar, P.C.M. (2002). Optimal measurement conditions for spatiotemporal EEG/MEG source analysis. *Psychometrika* 67: 299–313.

89. Seber, G.A.F. and Wild, C.J. (1989). *Nonlinear Regression*. Toronto, Canada: Wiley.

90. Andrés Muñoz‐Gutiérrez, P., Giraldo, E., Bueno‐López, M., and Molinas, M. (2018). Localization of active brain sources from EEG signals using empirical mode decomposition: a comparative study. *Frontiers in Integrative Neuroscience* 12: 55. https://doi.org/10.3389/fnint.2018.00055.

91. Michel, C.M. and Brunet, D. (2019). EEG source imaging: a practical review of the analysis steps. *Frontiers in Neurology* 10: 325.

92. Sun, M. and Sclabassi, R.J. (2000). The forward EEG solutions can be computed using artificial neural networks. *IEEE Transactions on Biomedical Engineering* 47 (8).

93. Abeyratne, U.R., Zhang, G., and Saratchand, P. (2001). EEG source localization: comparative study of classical and neural network methods. *International Journal of Neural Systems* 11 (4): 349–359.

94. Zhang, Q., Bai, X., Akutagawa, M. et al. (2002). A method for two EEG sources localization by combining BP neural networks with nonlinear least square method. *7th International Conference on Control, Automation, Robotics And Vision (ICARCV'02)*, (December 2002). Singapore.

95. Li, Z., Akutagawa, M., and Kinouchi, Y. (2005). Brain source localization for two dipoles using a combined method from 32‐channel EEGs. *Proceedings of the 2005 IEEE Engineering in Medicine and Biology 27th Annual Conference Shanghai, China* (1–4 September 2005).

96. Li, J‐W., Wang, Y‐H., Wu, Q. et al. (2008). EEG source localization of ERP based on multidimensional support vector regression approach. *Proceedings of the Seventh International Conference on Machine Learning and Cybernetics, Kunming* (12–15 July 2008).

97. Li, J‐W., Wang, Y‐H., Wu, Q. et al. (2009). Support vector machine method using in EEG signals study of epileptic spike. *Proceedings of the Eighth International Conference on Machine Learning and Cybernetics, Baoding* (12–15 July 2009).

98. McNay, D., Michielssen, E., Rogers, R.L. et al. (1996). Multiple source localization using genetic algorithms. *Journal of Neuroscience Methods* 64 (2): 163–172.

99. Abeyratne, U.R., Kinouchi, Y., Oki, H. et al. (1991). Artificial neural networks for source localization in the human brain. *Brain Topography* 4 (1): 3–21.

100. Van Hoey, G., De Clercq, J., Vanrumste, B. et al. (2000). EEG dipole source localization using artificial neural networks. *Physics in Medicine and Biology* 45: 997–1011.

101. Robert, J.S., Sonmez, M., and Sun, M. (2013). EEG source localization: a neural network approach. *Neurological Research* 23: 457–464.

102. Wentrup, M.G., Gramann, K., Wascher, E., and Buss, M. (2005). EEG source localization for brain‐computer‐interfaces. *Proceedings of the IEEE EMBS Conference*, 128–131. AU: Please provide the year for Ref. [30].

103. Ding, L., Worrell, G.A., Lagerlund, T.D., and He, B. (2006). 3D source localization of Interictal spikes in epilepsy patients with MRI lesions. *Physics in Medicine and Biology* 51: 4047–4062.

# 11 癫痫发作预测、检测与定位

## 11.1 简介

癫痫发作可能是测量大脑电位的主要动因，这导致了脑电图（EEG）系统的发明和 EEG 模式的分析。癫痫的基本概念在公元前 4500–1500 年的吠陀时期，在古印度医学中得到了完善和发展。在《查拉卡本集》（约公元前 400 年，现存最古老的完整阿育吠陀医学体系描述）的阿育吠陀文献中，癫痫被描述为*“apasmara”*，意为“意识丧失”。公元前 460–379 年间，希波克拉底将癫痫描述为“大脑紊乱”。“epilepsy”（癫痫）一词源自希腊语*“epilambanein”*，意为“抓住或发作”。然而，我们现在知道，癫痫发作是大脑细胞（神经元）群体中突发的、通常短暂的、过度的电放电所致，且大脑的不同部位都可能成为这种放电的部位。因此，癫痫发作的临床表现各异，取决于大脑中紊乱最初开始的部位以及扩散的范围。可能出现短暂症状，如意识或知觉丧失，运动、感觉（包括视觉、听觉和味觉）、情绪或精神功能障碍。

《查拉卡本集》文献包含了关于癫痫各个方面的大量论述，包括症状学、病因学、诊断和治疗。另一个古老且详细的癫痫记录保存在伦敦大英博物馆的一块巴比伦泥板上。这是一部巴比伦医学教科书的一章，由 40 块泥板组成，可追溯至公元前 2000 年。该泥板准确记录了我们今天所认识的许多不同发作类型。然而，与《查拉卡本集》的阿育吠陀医学相反，它强调癫痫的超自然本质，每种发作类型都与一个精灵或神的名字相关联——通常是邪恶的。因此，治疗主要是一种精神事务。巴比伦的观点是希波克拉底著名论文（可追溯至公元前五世纪）中描述的希腊*“神圣疾病”*概念的先驱。“seleniazetai”一词也常被用来描述癫痫患者，因为人们认为他们受月相或月神（塞勒涅）的影响，因此产生了*“月灾”*或*“癫狂”*（拉丁化版本）的概念。然而，希波克拉底认为癫痫不是神圣的，而是大脑的疾病。他推荐物理治疗，并指出如果疾病变成慢性，则无法治愈。

阿维森纳（980–1037 年），一位著名的波斯医生和哲学家，考虑了不同类型的癫痫及其特定治疗方法。他将癫痫的病因分为两类：一类由脑部疾病引起，另一类与其他器官的疾病相关。他认为胃等器官可以影响大脑并导致癫痫 [1]。

然而，癫痫是一种脑部疾病的观念直到公元十八和十九世纪才开始扎根。中间的 2000 年主要被超自然观点所主导。例如，在欧洲，自中世纪以来，圣瓦伦丁一直是癫痫患者的守护圣人。在此期间，癫痫患者受到恐惧、怀疑和误解，并遭受巨大的社会耻辱。癫痫患者被视为弃儿并受到惩罚。然而，其中一些人取得了成功，并享誉全球。这些人中包括尤利乌斯·凯撒、俄罗斯沙皇彼得大教皇庇护九世、作家费奥多尔·陀思妥耶夫斯基和诗人拜伦勋爵。

