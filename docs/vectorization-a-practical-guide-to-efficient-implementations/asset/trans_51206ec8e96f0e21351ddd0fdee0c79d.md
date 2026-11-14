
更加困难，可能导致错误信息的传播。利用先进人工智能技术（如面部和声音交换的 DeepFakes）的诈骗近年也有所上升。骗子可以假装成受害者正处于紧急状态的朋友和家人，并请求财务援助，这使得受害者更难识破骗局 [Butts, 2024]。

- **伦理与社会考量**：伦理问题涵盖广泛的议题，从人工智能被用于欺骗目的的潜在滥用，到人工智能生成艺术和文学作品的伦理影响。社会考量涉及人工智能对社会的更广泛影响，包括其对就业、隐私和社会动态的影响。值得注意的是，用于训练大规模模型的数据来源既不是未经创作者许可就从互联网“抓取”的，模型也不会向创作者提供适当的署名。使用抓取的内容来训练能够再生此类内容的人工智能模型是否构成合理使用，目前仍有争议。更近期地，纽约时报因使用受版权保护的材料来训练大语言模型而起诉了 OpenAI [Grynbaum and Mac, 2023]。

- **风险缓解**：应对这些挑战需要全面的风险缓解策略。这包括开发能够检测和抵消偏见的强健算法，为数据处理和模型训练实施严格的准则，并持续监控人工智能系统中的非预期行为。该领域的主要参与者，包括 Meta [Touvron et al., 2023b]、Google [Chowdhery et al., 2022] 和 OpenAI [OpenAI et al., 2023]，正在大力投资于该主题的研究。他们的努力不仅旨在进一步增强生成式模型的技术能力，还旨在确保模型的下游应用经过仔细评估，以符合人工智能安全标准。

- **政策与监管**：政策和监管在塑造人工智能技术安全发展与部署方面起着至关重要的作用。各国政府和监管机构越来越关注制定框架，以确保人工智能以安全、合乎伦理且对社会有益的方式发展。这包括围绕数据隐私、人工智能透明度和问责制的法规。全球各国政府机构，包括欧盟 [European Parliament, 2023]、美国 [iapp, 2024; Klobuchar, 2024]、中国 [Costigan, 2024] 和日本 [AP, 2024]，正在积极制定关于人工智能安全与监管的新立法和指南。

解决这些问题对于确保新的人工智能技术安全并造福社会至关重要。随着技术不断创新，我们将看到研究人员、行业领袖和政策制定者之间越来越多的合作，以应对人工智能安全与对齐的复杂局面。

## 11.8 结语

恭喜！你已学会如何将各种数学理论转化为代码。你已掌握使用 Python 中许多标准框架实现数据处理方法和机器学习模型的技能。你还学会了如何将代码向量化以提高效率和可扩展性。运用这些技能和知识，你还成功构建了许多实用的机器学习解决方案，解决了计算机视觉、音频处理和推荐系统等方面的问题，甚至制作了属于你自己的 mini-LLM！希望你喜欢这段旅程！

## 参考文献

Martin Abadi, Ashish Agarwal, Paul Barham, Eugene Brevdo, Zhifeng Chen, Craig Citro, Greg S. Corrado, Andy Davis, Jeffrey Dean, Matthieu Devin, Sanjay Ghemawat, Ian Goodfellow, Andrew Harp, Geoffrey Irving, Michael Isard, Yangqing Jia, Rafal Jozefowicz, Lukasz Kaiser, Manjunath Kudlur, Josh Levenberg, Dan Mane, Rajat Monga, Sherry Moore, Derek Murray, Chris Olah, Mike Schuster, Jonathon Shlens, Benoit Steiner, Ilya Sutskever, Kunal Talwar, Paul Tucker, Vincent Vanhoucke, Vijay Vasudevan, Fernanda Viegas, Oriol Vinyals, Pete Warden, Martin Wattenberg, Martin Wicke, Yuan Yu, and Xiaoqiang Zheng. Google 的 Transformer 教程. https://www.tensorflow.org/text/tutorials/transformer, 2023.

AP. 日本首相岸田公布生成式人工智能全球监管框架. https://apnews.com/article/oecd-ai-japan-kishida-artificial-intelligence-023ac08e04db5a2109cf35f88c9b1b02, 2024 年 5 月.

BBC News. Google 为照片应用的种族歧视失误道歉. https://www.bbc.com/news/technology-33347866, 2015 年 7 月.

Dylan Butts. DeepFake 诈骗已使企业损失数百万美元。专家警告情况可能会更糟. https://www.cnbc.com/2024/05/28/deepfake-scams-have-looted-millions-experts-warn-it-could-get-worse.html, 2024 年 5 月.

Aakanksha Chowdhery, Sharan Narang, Jacob Devlin, Maarten Bosma, Gaurav Mishra, Adam Roberts, Paul Barham, Hyung Won Chung, Charles Sutton, Sebastian Gehrmann, Parker Schuh, Kensen Shi, Sasha Tsvyashchenko, Joshua Maynez, Abhishek Rao, Parker Barnes, Yi Tay, Noam Shazeer, Vinodkumar Prabhakaran, Emily Reif, Nan Du, Ben Hutchinson, Reiner Pope, James Bradbury, Jacob Austin, Michael Isard, Guy Gur-Ari, Pengcheng Yin, Toju Duke, Anselm Levskaya, Sanjay Ghemawat, Sunipa Dev, Henryk Michalewski, Xavier Garcia, Vedant Misra, Kevin Robinson, Liam Fedus, Denny Zhou, Daphne Ippolito, David Luan, Hyeontaek Lim, Barret Zoph, Alexander Spiridonov, Ryan Sepassi, David Dohan, Shivani Agrawal, Mark Omerick, Andrew M. Dai, Thanumalayan Sankaranarayana Pillai, Marie Pellat, Aitor Lewkowycz, Erica Moreira, Rewon Child, Oleksandr Polozov, Katherine Lee, Zongwei Zhou, Xuezhi Wang, Brennan Saeta, Mark Diaz, Orhan Firat, Michele Catasta, Jason Wei, Kathy Meier-Hellstern, Douglas Eck, Jeff Dean, Slav Petrov, and Noah Fiedel. PaLM：通过路径扩展语言建模, 2022 年 10 月.

Djork-Arné Clevert, Thomas Unterthiner, and Sepp Hochreiter. 基于指数线性单元（ELUs）的快速且准确的深度网络学习, 2016 年 2 月.

Johanna Costigan. 中国新的人工智能草案法律优先考虑行业发展. https://www.forbes.com/sites/johannacostigan/2024/03/22/chinas-new-draft-ai-law-prioritizes-industry-development/?sh=3ba2ac836095, 2024 年 3 月.

Zihang Dai, Zhilin Yang, Yiming Yang, Jaime Carbonell, Quoc V. Le, and Ruslan Salakhutdinov. Transformer-XL：超越固定长度上下文的注意力语言模型, 2019 年 6 月.

Jacob Devlin, Ming-Wei Chang, Kenton Lee, and Kristina Toutanova. BERT：用于语言理解的深度双向 Transformer 预训练, 2019 年 5 月.

Alexey Dosovitskiy, Lucas Beyer, Alexander Kolesnikov, Dirk Weissenborn, Xiaohua Zhai, Thomas Unterthiner, Mostafa Dehghani, Matthias Minderer, Georg Heigold, Sylvain Gelly, Jakob Uszkoreit, and Neil Houlsby. 一张图片抵得上 16x16 个词：用于大规模图像识别的 Transformer, 2021 年 6 月.

European Parliament. 欧盟人工智能法案：首部人工智能监管法规. https://www.europarl.europa.eu/topics/en/article/20230601STO93804/eu-ai-act-first-regulation-on-artificial-intelligence, 2023 年 12 月.

Facebook Research. LLaMA 对 RoPE 的重新表述. https://github.com/facebookresearch/llama/blob/main/llama/model.py#L1Y1#L80-L161, 2023.

Matthew Gault. 在 4chan 上训练的人工智能变成了“仇恨言论机器”. https://www.vice.com/en/article/k78zwx/ai-trained-on-4chan-becomes-hate-speech-machine, 2022 年 6 月.

Daria Grechishnikova. 将基于 Transformer 的神经网络用于蛋白质特异性从头药物生成视作机器翻译问题. 科学报告, 11(1):321, 2021 年 1 月. ISSN 2045-2322. doi: 10.1038/s41598-020-79682-4.

Michael M. Grynbaum 和 Ryan Mac. 纽约时报就人工智能使用受版权保护的作品起诉 OpenAI 和微软. https://www.nytimes.com/2023/12/27/business/media/new-york-times-open-ai-microsoft-lawsuit.html, 2023 年 12 月.

Albert Gu 和 Tri Dao. Mamba：具有选择性状态空间的线性时间序列建模, 2023 年 12 月.

Dan Hendrycks 和 Kevin Gimpel. 高斯误差线性单元（GELUs）, 2016 年 6 月.

Shion Honda, Shoi Shi, and Hiroki R. Ueda. SMILES Transformer：用于低数据药物发现的预训练分子指纹, 2019 年 11 月.
