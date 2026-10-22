
## 评估前沿模型

我们正生活在一个前沿大语言模型以快速竞赛速度发展的时代，模型发布频繁，基准性能稳步提升。然而，这引发了一个关键挑战：我们应如何有意义地评估进展，尤其是随着基准测试可能随时间饱和。此外，最近的研究强调了流行基准的局限性和潜在缺陷 [28]。我们在第 5 章的工作探讨了这一问题的某个方面，其中我们提出了一个框架来评估和理解模型差异。展望未来，如何以可扩展的方式捕捉这些差异仍然是一个问题，因为推理模型具有更长的输出，而智能体系统可能具有长轨迹。最终，研究社区需要找到公平可靠的方法来评估这些先进模型，这对于指导前沿模型未来的发展至关重要。

## 参考文献

- [1] Ashish Vaswani, Noam Shazeer, Niki Parmar, et al. 注意力就是一切. NeurIPS, 2017. 1, 2.2, 5.3
- [2] Alec Radford, Jeffrey Wu, Rewon Child, et al. 语言模型是无监督的多任务学习者. 技术报告, 2019. 1, 2.3, 4.5.2, 5.3, 5.3.2, 5.7.3
- [3] Tom B. Brown, Benjamin Mann, Nick Ryder, et al. 语言模型是少样本学习者. arXiv 预印本 arXiv:2005.14165, 2020. 1, 3.2, 4.2
- [4] OpenAI. GPT-4 技术报告. arXiv 预印本 arXiv:2303.08774, 2023. 1, 3.2, 4.2
- [5] OpenAI. 介绍 ChatGPT. OpenAI 网站, 2022. 1
- [6] DeepSeek-AI. DeepSeek-V3 技术报告. arXiv 预印本 arXiv:2412.19437, 2024. [cite: 298] 1, 1, 6.1
- [7] OpenAI. Sora. OpenAI 网站, 2024. 1
- [8] Alec Radford, Jong Wook Kim, Tao Xu, et al. 通过大规模弱监督的鲁棒语音识别. arXiv 预印本 arXiv:2212.04356, 2022. 1
- [9] Jason Wei, Xuezhi Wang, Dale Schuurmans, et al. 思维链提示激发大型语言模型的推理. Advances in Neural Information Processing Systems, 2022. 1, 4.2
- [10] Edward J. Hu, Yelong Shen, Phillip Wallis, et al. LoRA：大型语言模型的低秩适应. arXiv 预印本 arXiv:2106.09685, 2021. 1, 3.6, 5.7.3
- [11] Qingxiu Dong, Lei Li, Damai Dai, et al. 关于上下文学习的综述. arXiv 预印本 arXiv:2301.00234, 2022. 1
- [12] Carlos E. Jimenez, John Yang, Alexander Wettig, et al. SWE-bench：语言模型能否解决现实世界的 GitHub 问题？ arXiv 预印本 arXiv:2310.06770, 2024. 1
- [13] OpenAI. GPT-4o 系统卡. arXiv 预印本 arXiv:2410.21276, 2024. [cite: 291] 2.1, 1
- [14] Jin Xu, Zhifang Guo, Jinzheng He, et al. Qwen2.5-Omni 技术报告. arXiv 预印本 arXiv:2503.20215, 2025. 2.1
- [15] Anthropic. Claude-3.5-Sonnet. https://www.anthropic.com/news/claude-3-5-sonnet, 2024. [cite: 292] 1
- [16] xAI. Grok-2 Beta 发布. https://x.ai/blog/grok-2, 2024. [cite: 292] 1
- [17] Albert Gu and Tri Dao. Mamba：具有选择性状态空间的线性时间序列建模. arXiv 预印本 arXiv:2312.00752, 2023. 2.2
- [18] Jacob Devlin, Ming-Wei Chang, Kenton Lee, et al. BERT：深度双向变换器的预训练用于语言理解. arXiv 预印本 arXiv:1810.04805, 2018. 2.2, 2.3, 3.8.3, 4.7, 5.3.2, 5.4
- [19] Tri Dao and Albert Gu. Transformers 是 SSM：通过结构化状态空间对偶性的广义模型和高效算法. arXiv 预印本 arXiv:2405.21060, 2024. 2.2
- [20] Shen Nie, Fengqi Zhu, Zebin You, et al. 大型语言扩散模型. arXiv 预印本 arXiv:2502.09992, 2025. 2.2
- [21] Subham Sekhar Sahoo, Marianne Arriola, Yair Schiff, et al. 简单有效的掩码扩散语言模型. arXiv 预印本 arXiv:2406.07524, 2024. 2.2
- [22] Hugo Touvron, Thibaut Lavril, Gautier Izacard, et al. LLaMA：开放高效的基础语言模型. arXiv 预印本 arXiv:2302.13971, 2023. 2.2, 3.2, 3.5, 3.8.7
- [23] Hugo Touvron, Louis Martin, Kevin Stone, et al. Llama 2：开放基础和微调聊天模型. arXiv 预印本 arXiv:2307.09288, 2023. 2.2, 3.2, 3.5, 4.2
- [24] Niklas Muennighoff, Zitong Yang, Weijia Shi, et al. s1：简单测试时扩展. arXiv 预印本 arXiv:2501.19393, 2025. 1
- [25] Abhimanyu Dubey, Abhinav Jauhri, Abhinav Pandey, et al. Llama 3 模型群. arXiv 预印本 arXiv:2407.21783, 2024. 2.2, 4.8.1, 2
- [26] Long Ouyang, Jeff Wu, Xu Jiang, et al. 使用人类反馈训练语言模型遵循指令. arXiv 预印本 arXiv:2203.02155, 2022. 2.3, 4.8.2
- [27] Noam Shazeer. GLU 变体改进 Transformer. arXiv 预印本 arXiv:2002.05202, 2020. 2.2
- [28] Shivalika Singh, Yiyang Nan, Alex Wang, et al. 排行榜幻觉. arXiv 预印本 arXiv:2504.20879, 2025. 5.5, 6.1
- [29] Yuntao Bai, Saurav Kadavath, Sandipan Kundu, et al. 宪法 AI：来自 AI 反馈的无害性. arXiv 预印本 arXiv:2212.08073, 2022. 2.3
- [30] Kaiming He, Xiangyu Zhang, Shaoqing Ren, et al. 用于图像识别的深度残差学习. CVPR, 2016. 2.2, 4.3
- [31] Jimmy Lei Ba, Jamie Ryan Kiros, Geoffrey E. Hinton. 层归一化. arXiv 预印本 arXiv:1607.06450, 2016. (document), 2.2, 4.5.2, 4.8.6, 4.37
- [32] Long Ouyang, Jeff Wu, Xu Jiang, et al. 使用人类反馈训练语言模型遵循指令. arXiv 预印本 arXiv:2203.02155, 2022.
- [33] Pranab Sahoo, Ayush Kumar Singh, Sriparna Saha, et al. 大型语言模型提示工程的系统综述：技术与应用. arXiv 预印本 arXiv:2402.07927, 2024. 1
- [34] Chen Liang, Simiao Zuo, Minshuo Chen, et al. 预训练语言模型中的超级票据：从模型压缩到改进泛化. arXiv 预印本 arXiv:2105.12002, 2021.
- [35] Jason Wei, Karina Nguyen, Hyung Won Chung, et al. 测量短形式事实性 in
- [36] Colin Raffel, Noam Shazeer, Adam Roberts, et al. 使用统一文本到文本 Transformer 探索迁移学习的极限. *Journal of Machine Learning Research*, 2020. 2.2, 3.5, 4.8.12
- [37] Yinhan Liu, Myle Ott, Naman Goyal, Jingfei Du, Mandar Joshi, Danqi Chen, Omer Levy, Mike Lewis, Luke Zettlemoyer, and Veselin Stoyanov. RoBERTa：一种稳健优化的 BERT 预训练方法. *arXiv 预印本 arXiv:1907.11692*, 2019. 2.2
- [38] Dzmitry Bahdanau, Kyunghyun Cho, and Yoshua Bengio. 通过联合学习对齐和翻译的神经机器翻译. *arXiv 预印本 arXiv:1409.0473*, 2014. 2.2
- [39] Jianpeng Cheng, Li Dong, and Mirella Lapata. 用于机器阅读的长短期记忆网络. *Proceedings of the 2016 Conference on Empirical Methods in Natural Language Processing (EMNLP)*, 2016. 2.2
- [40] Zhouhan Lin, Minwei Feng, Cicero Nogueira dos Santos, et al. 一种结构化自注意力句子嵌入. *arXiv 预印本 arXiv:1703.03130*, 2017. 2.2
- [41] Rico Sennrich, Barry Haddow, Alexandra Birch, et al. 使用子词单元的稀有词神经机器翻译. *arXiv 预印本 arXiv:1508.07909*, 2015. 2.2
- [42] Dan Hendrycks and Kevin Gimpel. 高斯误差线性单元 (GELUs). *arXiv 预印本 arXiv:1606.08415*, 2016. 2.2
- [43] Prajit Ramachandran, Barret Zoph, and Quoc V. Le. 搜索激活函数. *arXiv 预印本 arXiv:1710.05941*, 2017. 2.2
- [44] Leo Gao, Stella Biderman, Sid Black, et al. The Pile：用于语言建模的 800GB 多样化文本数据集. *arXiv 预印本 arXiv:2101.00027*, 2021. 4.8.8, 4.8.12
- [45] Together Computer. RedPajama：重现 LLaMA 训练数据集的开源配方. <https://github.com/togethercomputer/RedPajama-Data>, 2023. 4.3, 4.8.12
- [46] Abhimanyu Dubey, Moitreya Chatterjee, Narendra Ahuja. 基于核心集的神经网络压缩. *ECCV*, 2018. 3.7, 3.8.3
- [47] Mohammad Babaeizadeh, Paris Smaragdis, Roy H. Campbell. NoiseOut：修剪神经网络的一种简单方法. *arXiv 预印本 arXiv:1611.06211*, 2016. 3.7, 3.8.3
- [48] Hengyuan Hu, Rui Peng, Yu-Wing Tai, et al. 网络修剪：面向高效深度架构的数据驱动神经元修剪方法. *arXiv 预印本 arXiv:1607.03250*, 2016. 3.7
- [49] Guneet S. Dhillon, Kamyar Azizzadenesheli, Zachary C. Lipton, et al. 用于鲁棒对抗防御的随机激活修剪. *International Conference on Learning Representations*, 2018. 3.7
- [50] Gongfan Fang, Xinyin Ma, Mingli Song, et al. DepGraph：迈向任意结构修剪. *Conference on Computer Vision and Pattern Recognition*, 2023. 3.7
- [51] Pavlo Molchanov, Arun Mallya, Stephen Tyree, et al. 神经网络修剪的重要性估计. *CVPR*, 2019. 3.7
- [52] Leo Gao, Jonathan Tow, Stella Biderman, et al. 少样本语言模型框架
