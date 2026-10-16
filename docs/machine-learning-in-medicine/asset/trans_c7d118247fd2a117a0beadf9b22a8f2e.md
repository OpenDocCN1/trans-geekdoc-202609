
磁共振成像（MRI）和磁共振血管造影（MRA）扫描是传统用于定量器官结构变化的成像技术。在文献中，MRI 扫描已用于测量脑室腔和心肌的体积测量 \[[12](#C20_chapter13.xhtml#ref13_12)\]，并利用磁共振（MR）速度数据在大血管（如主动脉或肺动脉）中确定血管内压力 \[[13](#C20_chapter13.xhtml#ref13_13)\]。MRA 扫描已用于测量因颈动脉闭塞而导致患者侧交通血管流量的测量 \[[14](#C20_chapter13.xhtml#ref13_14)\]。据我们所知，迄今为止既未使用 MRA 也未使用 MRI 来估计脑血管压力的变化。通过分析 MRA 来检测脑血管或 CPP（cerebrovascular pressure）变化的尝试因缺乏能够准确分割并标记大脑中小血管（相较于主动脉或肺动脉）的精确分割算法而未能成功。此外，仍缺乏用于测量脑血管结构变化并找出这些变化与平均动脉压（MAP）之间关系的方法。本文件提出了新颖的方法，用于从周围组织中分离脑血管、测量脑血管结构的变化，并将这些变化与 MAP 进行关联。

## [13.2 Methods](#C20_chapter13.xhtml#rsecc013_3)

本文的目的是开发一种基于 MRA 的新方法，用于检测脑血管结构变化，并证明该方法能够展示脑血管结构变化与 MAP 之间的相关性的概念验证。患者的人口学信息以及所提方法和数据分析细节如下。

### [13.2.1 Patient Demographics](#C20_chapter13.xhtml#rsecc013_3_1)

匹兹堡大学的机构审查委员会（IRB）已批准本工作的开展。患者数据（*n* = 15，M = 8，F = 7，年龄 = 49.2 ± 7.3）以及测量值在为期 700 天的期间内收集。数据包括 MRA 扫描和系统血压（BP），均为回顾性分析。选取这 15 名研究参与者的目的在于使其血压变化在整个研究期间内覆盖广泛范围。MRA 扫描在不考虑患者血压测量的情况下进行分析。采用 3T Trio TIM 扫描仪，配备 12 通道头部线圈，获取 MRA 图像。取四次测量值（由 sphygmomanometer 读取），取其平均值用于确定血压和 MAP。测量在患者就诊时、MRI 扫描前进行。每套扫描包括 3D 多层高分辨率图像，包含 160 片，厚度为 0.5 mm。图像分辨率为 384 × 448，像素大小为 0.6 × 0.6 × 1.0 mm³。回声时间（echo time）为 3.8 ms，倾斜角（flip angle）为 15°，重复时间（repetition time）为 21 ms。扫描耗时 7 分钟 39 秒，且无需造影剂。

受试者的第 0 天平均收缩压为 122 ± 6.9 mmHg，平均收缩压为 82 ± 3.8 mmHg；第 700 天的平均收缩压为 118.9 ± 12.4 mmHg，平均舒张压为 79.9 ± 11.0 mmHg，即平均收缩压随时间保持相对稳定，尽管个体有升高、降低或保持不变的情况。

### [13.2.2 Data Analysis](#C20_chapter13.xhtml#rsecc013_3_2)

对患者 MRA 数据的分析包括五个关键步骤（如 [Figure 13.1](#C20_chapter13.xhtml#f13_1)）组成：(1) 手动分割训练切片以确定真实情况，(2) 对所有切片进行自动分割，利用已分割的真实切片与线性离散高斯混合模型（LCDG）描述灰度分布，从而将血管与周围软组织分离，(3) 进行体素匹配，生成时间减除图像，以通过距离图量化患者在第 0 天与第 700 天之间的血管变化，(4) 生成概率分布函数（PDF），描述相对于血管边缘的像素距离分布，用于统计关联血压，(5) 估计累积分布函数（CDF），观察同一患者从第 0 天到第 700 天血管变化的累计概率。

![FIGURE 13.1 Framework of the data analysis for quantifying cerebrovascular changes from MRA imaging data.](images/fig13_1.jpg)

FIGURE 13.1 Framework of the data analysis for quantifying cerebrovascular changes from MRA imaging data.

**手动训练切片分割**：患者的 MRA 数据包含 160 片 MRA 切片。每隔十片切片手动分割，使用 Adobe Photoshop（Adobe Systems, CA）将血管从周围组织中分离。该方法能够在像素级别上准确划分体内血管与周围组织，其主要局限性是 MRI 机器本身的分辨率。手动分割的二值训练切片（黑色为周围组织，白色为目标血管）被称为真实情况（GT），因为图像无伪影或噪声（[Figure 13.2](#C20_chapter13.xhtml#f13_2)）。手动分割的选定切片用于初始化和优化分割算法，随后该算法用于分割所有获取的切片。

![FIGURE 13.2 (a) Original MRA image slice of sample patient at day 0. (b) Manually segmented ground truth (GT) image from the image in (a).](images/fig13_2.jpg)

FIGURE 13.2 (a) Original MRA image slice of sample patient at day 0. (b) Manually segmented ground truth (GT) image from the image in (a).

**自动分割**：在常规计算机辅助诊断中，准确提取 3D 脑血管信息是一项主要挑战。我们的方法是通过在统计框架内定义感兴趣区域的概率模型，而不预先固定这些模型 \[[15](#C20_chapter13.xhtml#ref13_15), [16](#C20_chapter13.xhtml#ref13_16), [17](#C20_chapter13.xhtml#ref13_17)\]。对每张 MRA 切片，使用 LCDG 作为灰度分布的近似模型，并将切片划分为三个个体化的 LCDG，分别对应暗灰（骨骼和脂肪）、浅灰（脑组织）和亮灰（血管）三种主导模式。通过设定强度阈值来标记血管，随后对提取的体素应用 3D 连通性过滤，选择所需的血管树结构。该方法在分割精度和准确性上优于其他方法 \[[16](#C20_chapter13.xhtml#ref13_16)\]。

将期望–最大化（EM）技术适配到 LCDG，可精确识别特定模型（包括其分量数量（正负）），并构造一个连续的 LCDG 模型，包含概率分布。

