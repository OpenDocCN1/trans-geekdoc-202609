
大多数用于WD的诊断方法是非成像的，AI在WD分类方面未取得令人印象深刻的结果。在文献调查中，我们同时考虑基于AI和非AI的WD分类技术。过去二十年，血清和尿液等生物标志物被用于WD诊断 \[[1](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5bib1), [3](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5bib3), [61](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5bib61)\]。这些方法包括24小时尿液或血清实验室检测以识别WD。Ferenci *et al* \[[61](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5bib61)\] 提出了一种利用Kayser–Fleischer环、神经症状和低铜血浆浓度来检测WD的诊断方法。其他WD检测方法包括基于血液的实验室检测和基因代码检测。Vrabelova *et al* \[[62](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5bib62)\] 通过检测欧洲人中ATP7B的H1069Q突变来识别WD。Rosencrantz和Schilsky *et al* \[[4](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5bib4)\] 利用ATP7B突变分析、神经系统障碍、Kayser–Fleischer环、尿液和肝脏铜水平升高以及肝脏组织病理变化来检测WD。

上述所有WD检测技术均为非成像方法，且耗时。由于最近MRI技术的进步，医生现在可以通过可视化大脑中的WMH轻松识别WD \[[63](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5bib63)\]。此外，WMH还可用于检测其他疾病，如中风 \[[64](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5bib64)\]、威利斯配置 \[[65](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5bib65)\] 和情绪障碍 \[[66](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5bib66)\]。Kim *et al* \[[67](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5bib67)\] 使用了儿科患者的T2加权MRI图像，并根据初始MRI发现将其分为三组，观察到WMH在尾状核、丛状核、间脑、脑干和脑桥中呈高信号。最近AI的进展引入了通过在fMRI上应用AI架构来检测WD的方法。Hu *et al* \[[68](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5bib68)\] 对WD患者的频率依赖通道在低频功能幅度中的研究。Kaden *et al* \[[69](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5bib69)\] 使用支持向量机和参数化广义学习向量量化（PGLVQ）对WD进行分类，分别实现了87.5%和90.1%的准确率。Jing *et al* \[[70](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5bib70)\] 研究了30名患者的MRI扫描用于WD分类，他们使用独立组件分析（ICA）提取特征。提取特征后，Jing *et al* 应用SVM并获得0.94的AUC和89.4%的准确率。Agarwal *et al* \[[71](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5bib71)\] 使用WD患者的MRI扫描进行分类和特征化，采用“改进的卷积神经网络”，并在增强折叠上进行优化，实现了98.28%的准确率和0.99的AUC。他们还利用AI基于FMS和双谱分析对WD进行特征化。

可以看出，WD分类和特征化的AI研究在文献中较少。我们的研究是首个采用迁移学习范式对WD的特征化和分类进行研究。

### 5.3. Methodology

#### 5.3.1 Patient demographics

本研究分析了来自46名患者（平均年龄：40.73 ± 11.3岁，男女比例均衡）于2011年至2015年间收集的T2W-TSE MRI扫描数据（伦理委员会批准，Azienda Ospedaliero Universitaria (AOU)，Cagliari，意大利）。采用1.5特斯拉超导磁体（Philips，Best，荷兰）配合头部线圈，按照标准化协议进行影像检查。每位受试者均进行常规扩散加权成像（DWI），采用单次射击回声序列，在横断面上使用两个扩散敏感值（0和1000 s mm^(−2)）进行检查。在常规脑部协议中，还采集了轴位和矢状位2D FLAIR图像（TR/TE/TI：10000/140/2200 ms；矩阵：512 × 512；视野：240 × 240 mm²；层厚：5 mm）。此外，还获取了轴位自旋回声T1加权图像（TR/TE/激发：500–600/15/2）和快速自旋回声T2加权图像（TR/TE/激发：2200–3200/80–120/1,2；turbo factor，2），层厚与上述相同。

#### 5.3.2 Data augmentation

初始MRI数据由放射科医师团队手动分类，随后准备用于进一步处理。由于队列包含37名对照和9名WD患者，导致两类图像数量不均。每位患者的MRI研究包含12–13层，这导致458张对照图像和115张WD图像。为应对不平衡数据集，我们对WD类别使用Python‘augmentor’ API进行增强，结果增加了343张WD图像。由于深度卷积神经网络（DCNN）需要大量图像以保证训练和表现，我们对两类图像分别进行了2倍、3倍、4倍和5倍的放大，并训练和测试系统以确定哪种增强输入效果最佳。为避免在增强过程中产生不现实的脑部MRI图像，我们遵循可接受的协议，随机将图像旋转−10至10度。这将防止水平或垂直翻转或更大角度旋转等方法。

#### 5.3.3 Pre-processing: skull and background removal

预处理是分类过程的关键组成部分，有助于从MRI图像中提取感兴趣区域（ROI）。预处理包含两个重要步骤：(i) 去除颅骨区域；(ii) 去除黑色背景，以便为分割ROI做准备。为进行背景去除和脑部分割，我们使用了两种流行的工具：BrainSuite \[[35](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5bib35)\] 和 VolBrain \[[36](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5bib36)\]。BrainSuite用于读取转换为.nii文件的DICOM图像（.nii文件格式主要与Neuroimaging Informatics Technology Initiative的NIfTI-1数据格式关联），并生成去除了颅骨的脑部灰度图像。VolBrain用于创建脑部面具，以便从原始MRI灰度图像中去除颅骨。预处理完成后，将结果图像传递至分割模块以去除背景。图 [5.1](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5fig1) 展示了一对WD患者与对照患者的样本图像。WD分割脑部图像在大脑沟回区（黄色虚线框内）呈现更亮的区域（更高WMH），而对照图像则较暗。图 [5.2](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5fig2) 和图 [5.3](#Chapter_5.xhtml#bk978-0-7503-2244-7ch5fig3) 分别展示了六名患者（三名对照、三名WD）的分割MRI扫描样本。

![Figure 5.1. Control (left) and WD (right). Both images show the skull with the removal of background.](images/bk978-0-7503-2244-7ch5f1_online.jpg)

**Figure 5.1.** Control (left) and WD (right). Both images show the skull with the removal of background.

![Figure 5.2. Samples of the segmented MRI scans of six patients from the control dataset.](images/bk978-0-7503-2244-7ch5f2_online.jpg)

**Figure 5.2.** Samples of the segmented MRI scans of six patients from the control dataset.
