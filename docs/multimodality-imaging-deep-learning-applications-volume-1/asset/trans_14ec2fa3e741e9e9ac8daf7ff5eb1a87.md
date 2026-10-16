
患有心源性栓塞症状或长期症状（六个月）的患者被排除在试验之外。欧洲颈动脉手术协作组（ECST）揭示，手术可降低患有70%至99%狭窄的患者的总体中风风险。手术对轻度狭窄（0%–29%）的患者有害（European Carotid Surgery Trialists’ Collaborative Group 1991），而对患有30%–49%或50%–69%狭窄的患者则影响甚微（European Carotid Surgery Trialists’ Collaborative Group 1996）。欧洲颈动脉手术协作组1998年建议对大多数80%狭窄的患者进行颈动脉内膜切除术。我们早期研究发现，70%至99%狭窄的患者手术效果显著，50%至69%狭窄的患者效果较好（[20](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib20), [35](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib35)）。中风很少与导致小于50%狭窄的颈动脉斑块相关。如果将这些斑块纳入，将引入噪声和偏见。我们根据这些数据排除了狭窄小于50%的斑块。超声技师并不了解斑块的分类或特征，因为他们常规检查狭窄的存在并评估斑块。然而，处理图像的人员对分类保持盲视，因此他们不知道斑块是否具有症状性。

#### 6.2.3 超声数据获取与预处理

超声检查在英国伊丽莎白女王医院心血管研究与诊断实验室进行。使用的设备是ATL HDI 3000（Advanced Technology Laboratories, Seattle, WA, USA），配备双频扫描仪和4–7 MHz（多频率）线性宽带探头，分辨率为20像素/毫米。

为实现满意的图像标准化（如我们先前研究所述），满足以下条件：（i）超声束在血液中传播时未受衰减，因此使用动态范围；（ii）帧进行平均处理；（iii）在动脉腔内垂直放置斜向组织的时间增益补偿曲线。这样可确保前后壁的 adventitia 都呈现高亮度。（iv）调整增益，（v）在后处理时使用线性传递曲线，（vi）将超声束与动脉壁保持90度角，（vii）选择最低深度，使斑块占据图像相当大的部分，（viii）将探头校准以识别斑址旁的 adventitia 为高亮区域，用于数据标准化。队列来源于十年前，但机器分辨率自那时起有所提升。然而，如果探头方向保持一致，机器学习更有可能获得更好的结果。随着特征更分散，分离指数（APSI）将得到改善。在深度学习（DL）中，架构更有可能得到改进，因为要达到相同性能需要更小的层数。

#### 6.2.4 斑块轮廓划定

与早期研究一致（[20](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib20), [35](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib35)），使用 Plaque Texture Analysis 软件（Iconsoft International Ltd, Greenford, London, UK）进行标准化和斑块 ROI 选择。标准化后血液的中位灰度强度范围为0–5，而 adventitia 层的范围为180–190，与我们早期研究一致（[20](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib20), [35](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib35)）。在标准化图像中，斑块通过使用鼠标勾绘并保存为新文件（在 ROI 选择的情况下）。软件允许用户选择斑块的前壁或后壁。在选择钙化斑块时，未考虑声影。图 [6.1](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6fig1) 展示了这些切除部分。

![Figure 6.1. Left: Symptomatic. Right: Asymptomatic. Rows 1, 3, 5, and 7 are original carotid plaque scans. Rows 2, 4, 6, and 8 are pre-processed plaque delimited cut sections by the vascular surgeon (AN%). (Reproduced with permission from \[49\]. Copyright 2021 Springer.)](images/bk978-0-7503-2244-7ch6f1_online.jpg)

**Figure 6.1.** Left: Symptomatic. Right: Asymptomatic. Rows 1, 3, 5, and 7 are original carotid plaque scans. Rows 2, 4, 6, and 8 are pre-processed plaque delimited cut sections by the vascular surgeon (AN%). (Reproduced with permission from \[[49](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib49)\]. Copyright 2021 Springer.)

#### 6.2.5 超声斑块数据增强

我们采用标准化的“数据增强”方法，因为深度学习系统通常需要更大的数据库（数万至数百万）。这需要对已划定的斑块进行随机几何变换，如（i）倾斜和（ii）旋转。原始队列包含346例斑块，其中196例为症状性，150例为无症状。根据上述增强方法，新建队列包含2311例斑块，其中1191例为症状性，1120例为无症状。196例症状性斑块被转换为1191例（804例为新增且提升至1000，然后原始196例被加入，总计1196例）。因图像失真和不适当被消除5幅图像，最终得到1191例。对于无症状斑块的扩增，采用类似方法。因此，在150例斑块上叠加使总数达到1000例，再加入150例原始斑块，总计1150例。有30例倾斜图像被认为不满意并从最终统计中移除，剩余1120例无症状斑块。

#### 6.2.6 超算机规格

我们的深度学习模型在 NVIDIA-DGX v100-1 Tesla 上实现，如图 [6.2](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6fig2)(a) 所示，这是一款突破性的系统。它在深度学习训练方面具有无与伦比的性能。它配备八个 NVIDIA Tesla V100 图形处理单元（GPU）加速器，通过 NVIDIA NVLink 相连。如图 [6.2](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6fig2)(b) 所示，所有 GPU 均连接至立方网格网络。这便于 GPU 负载共享过程。利用高性能 NVLink GPU 接口，深度学习训练（[36](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib36)）更具可扩展性。

![Figure 6.2. Global ML architecture. (Reproduced with permission from \[49\]. Copyright 2021 Springer.)](images/bk978-0-7503-2244-7ch6f2_online.jpg)

**Figure 6.2.** Global ML architecture. (Reproduced with permission from \[[49](#Chapter_6.xhtml#bk978-0-7503-2244-7ch6bib49)\]. Copyright 2021 Springer.)

#### 6.2.7 深度学习架构
