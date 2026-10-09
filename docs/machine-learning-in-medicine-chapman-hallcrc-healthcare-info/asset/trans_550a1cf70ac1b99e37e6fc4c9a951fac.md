
在日常活动序列中注入异常活动。我们特别旨在模拟重复、睡眠障碍和混乱等类型的异常行为。重复和睡眠障碍相关的异常行为发生在活动层面，而混乱相关的异常行为则发生在活动的子活动层面。然而，在这种方法中生成异常行为可能无法反映特定用户的异常行为，因为人们在不同时间会表现出不同的习惯。

其次，活动识别问题被模拟为一个序列标记问题，其中传感器测量的时间序列数据被视为一个序列。然后，利用循环神经网络（RNN）及其变体——即长短期记忆网络（LSTM）、门控循环单元（GRU）和原生版本（Vanilla）以及卷积神经网络（CNN）来建模日常生活模式。使用 RNN 和 CNN 的结果表明，捕捉活动实例及其时间和空间关系有助于理解日常生活模式及其与其他活动的关系。利用 RNN，我们能够将日常生活中的时间信息编码起来，以建模痴呆症支持的个人环境。利用 CNN，我们尝试从活动中提取有意义且富有成效的模式，并借助这些模式识别活动并检测异常。这些模型擅长检测与活动重复和睡眠干扰相关的异常。然而，它们能力不足以检测与混乱相关的异常，因为它们无法对活动中的子活动进行建模。RNN 和 CNN 无法在粒度级别上对日常活动进行建模，因此它们无法理解这些活动中哪些子活动被遗忘、重复或混淆。对这些子活动进行建模将有助于更好地理解活动识别。

## 10.6.2 未来工作

这项研究的一个可能扩展方向是考虑传感器的关闭（OFF）状态，并调查其对异常检测的影响。此外，可以考虑特定的特征或规则来判断某个传感器（例如，代表药品的物品传感器或用于检查冰箱门是否关闭的冰箱门传感器）是否处于关闭状态。可以提出新的特征来表示传感器事件，以覆盖老年人认知状态下的更多不同类型异常行为（例如忘记家中物品的位置，以及混淆如何正确使用厨房器具）。

当疾病进展缓慢时，我们提出的方法可能无法适应并检测异常行为。因此，可以收集观察到逐渐恶化的真实世界数据。此外，还可以考虑反映痴呆症特定习惯的不同类型异常行为。如果无法收集真实世界数据，可以提出模拟方法来人工生成这类行为。

# 参考文献

- 1. C. Patterson. The state of the art of dementia research: New frontiers 2018. Tech. rep. Alzheimer's Disease International (ADI), 2018.
- 2. M. S. Albert et al. “The diagnosis of mild cognitive impairment due to Alzheimer's disease: Recommendations from the National Institute on Aging”. In: *Alzheimer's & Dementia* vol. 7, no. 3 (2011), pp. 270–279. doi: 10.1007/s00406-012-0349-0.
- 3. W. Thies and L. Bleiler. “2013 Alzheimer's disease facts and figures”. In: *Alzheimer's & Dementia: the Journal of the Alzheimer's Association* vol. 9, no. 2 (2013), pp. 208–245.
- 4. Office for National Statistics. Overview of the UK population: March (2017).
- 5. Alzheimer. Alzheimer's disease (2017). url: www.alz.org (visited on 08/04/2017).
- 6. M. Amiribesheli and A. Bouchachia. “Smart homes design for people with dementia”. In: *2015 International Conference on Intelligent Environments* (2015), pp. 156–159. doi: 10.1109/IE.2015.33.
- 7. M. P. Cutchin. “The process of mediated aging-in-place: A theoretically and empirically based model”. In: *Social Science and Medicine* vol. 57, no. 6 (2003), pp. 1077–1090. doi: 10.1016/S0277-9536(02)00486-0.
- 8. A. Wimo, B. Winblad, and L. Jonsson. “The worldwide societal costs of dementia: Estimates for 2009”. In: *Alzheimer's & Dementia* vol. 6, no. 2 (2010), pp. 98–103.
- 9. M. R. Hodges et al. “Automatic assessment of cognitive impairment through electronic observation of object usage”. In: *Pervasive Computing*. Berlin, Heidelberg: Springer Berlin Heidelberg (2010), pp. 192–209.
- 10. K. Wild. “Aging changes”. In: *Gerotechnology* vol. 9, no. 2 (2010), pp. 121–125.
- 11. M. Amiribesheli, A. Bennismore, and A. Bouchachia. “A review of smart homes in healthcare”. In: *Journal of Ambient Intelligence and Humanized Computing* vol. 6, no. 4 (2015), pp. 495–517. doi: 10.1007/s12652-015-0270-2.
- 12. A. R. M. Forkan et al. “A context-aware approach for long-term behavioral change detection and abnormality prediction in ambient assisted living”. In: *Pattern Recognition* vol. 48, no. 3 (2015), pp. 628–641. doi: 10.1016/j.patcog.2014.07.007.
- 13. J. Lundström, E. Järpe, and A. Verikas. “Detecting and exploring deviating behaviour of smart home residents”. In: *Expert Systems with Applications* vol. 55 (2016), pp. 429–440. doi: 10.1016/j.eswa.2016.02.030. url: http://www.sciencedirect.com/science/article/pii/S0957417416300616.
- 14. D. J. Patterson et al. “Fine-grained activity recognition by aggregating abstract object usage”. In: *Ninth IEEE International Symposium on Wearable Computers (ISWC'05)* (2005), pp. 44–51. doi: 10.1109/ISWC.2005.22.
- 15. H. L. Chieu, W. S. Lee, and L. P. Kaellbling. “Activity recognition from physiological data using conditional random fields”. In: *SMA Symposium*. Singapore - MIT Alliance (2006).
- 16. T. van Kasteren et al. “Accurate activity recognition in a home setting”. In: *Proceedings of the 10th International Conference on Ubiquitous Computing*. UbiComp ’08 (2008), pp. 1–9. doi: 10.1145/1409635.1409637. url: http://doi.acm.org/10.1145/1409635.1409637.
- 17. G. Viroene. “Assessing everyday life behavioural rhythms for the older generation”. In: *Pervasive and Mobile Computing* vol. 5, no. 5 (2009), pp. 606–622. doi: 10.1016/j.pmcj.2009.06.008.
- 18. A. R. M. Forkan et al. “A context-aware approach for long-term behavioural change detection and abnormality prediction in ambient assisted living”. In: *Pattern Recognition* vol. 48, no. 3 (2015), pp. 628–641. doi: 10.1016/j.patcog.2014.07.007.
- 19. J. Lundström, E. Farpe, and A. Verikas. “Detecting and exploring deviating behaviour of smart home residents”. In: *Expert Systems with Applications* vol. 55 (2016), pp. 429–440. doi: 10.1016/j.eswa.2016.02.030. url: http://www.sciencedirect.com/science/article/pii/S0957417416300616.
- 20. T. Van Kasteren, G. Englebiene, and B. J. A. Kroese. “Human activity recognition from wireless sensor network data: Benchmark and software”. In: *Activity Recognition in Pervasive Intelligent Environments* (2011), pp. 165–186. doi: 10.2991/978-94-91216-053_8.
- 21. N. Twomey et al. “Unsupervised learning of sensor topologies for improving activity recognition in smart environments”. In: *Neurocomputing* vol. 234.C (Apr. 2017), pp. 93–106. ISSN: 0925-2312. doi: 10.1016/j.neucom.2016.12.049. url: https://doi.org/10.1016/j.neucom.2016.12.049.
- 22. S. S. Akter and L. B. Holder. “Activity recognition using graphical features”. In: *2014 13th International Conference on Machine Learning and Applications*. Springer International Publishing (2014), pp. 165–170.
- 23. M. Seeley Adriana, M. Schmitter-Edgecombe, A. Crandall, and D. J. Cook. “Naturalistic assessment of everyday activities and prompting technologies in mild cognitive impairment”. In: *Journal of the International Neuropsychological Society* vol. 2013, no. 4 (2013), pp. 442–452. doi: 10.1017/S135561771200149X.
- 24. N. K. Suryadevara et al. “Forecasting the behavior of an elderly using wireless sensors data in a smart home”. In: *Engineering Applications of Artificial Intelligence* vol. 26, no. 10 (2013), pp. 2641–2652. doi: 10.1016/j.engappai.2013.08.004.
- 25. P. Dawadi, D. J. Cook, and M. Schmitter-Edgecombe. “Smart home-based longitudinal functional assessment”. In: *Proceedings of the 2014 ACM International Joint Conference on Pervasive and Ubiquitous Computing: Adjunct Publication*. UbiComp ’14 Adjunct. New York, NY: ACM (2014), pp. 1217–1224. doi: 10.1145/2638728.2638813. url: http://doi.acm.org/10.1145/2638728.2638813.
