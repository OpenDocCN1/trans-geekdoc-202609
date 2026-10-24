

## 10.3.4 使用贝叶斯超参数调优人工神经网络进行特征检测

人工神经网络是一种理论模型，模拟生物脑电波的多个方面。所提出的方法以类似的方式在机器人技术中表现出色（Rana 等人，2021）。

更技术性地讲，它通常指的是一种计算机网络，能够针对特定类型的输入产生一些有用的洞见。尽管它们是认知系统，但并非基于输入与结果之间的任何连接来设计。

相反，BH-ANN 仅被内置为一个永久特征，然后通过模拟神经学特征来教导其执行功能。

神经网络有多种类型，每种都有独特的目标、教学方法与传输网络（Khang 等人，2023a）。

### 10.3.4.1 贝叶斯超参数调优人工神经网络的特征

许多常规和准执行器使用 BH-ANN。

- 贝叶斯超参数调优人工神经网络能够管理具有多种结果的单一输入。
- 将空间值转化为策略与计划的统计挑战，对 BH-ANN 而言难以解决。
- 大多数广泛采用的控制策略，包括非线性事件的调节，都涉及 BH-ANN。
- 多种不同的传感器已被有效地整合到 BH-ANN 中。
- 拒绝服务神经模型在机器人技术中最为常用。

### 10.3.4.2 贝叶斯超参数调优人工神经网络的操作

由于该方法降低了训练数据的维度，以简化网络防御中涉及的各层之间的关系，因此它采用了一个由全连接层组成的密集网络作为输出。算法 1.1 展示了 BH-ANN 的操作方式。

**算法 1.1：BH-ANN 操作**

```
Input: Neurons, Activation, Optimizer, Learning Rate, Batch Size, Epochs, Layers, Normalization, Drop Out, Dropout Rate
Output: Optimized Values for all the estimators
Begin:
Step 1: Create a sequential layer.
Step 2: Define a set of dictionaries that consist of all possible optimizers, such as Adam, SGD, RMSProp, and others, for both convolution and dense layers.
Step 3: Define activation functions.
Step 4: Define neurons in the range of 10 to 1000, and batch size in the range of 200 to 1000.
Step 5: Define three dense layers and drop out layers with a threshold greater than 0.5.
Step 6: Define a dense output layer with a sigmoid activation function.
Step 7: Compute the cross-validation score by applying the stratified folding technique.
End
```

## 10.4 性能评估

我们提出了 BH-ANN。实验使用了安全性、感知水平、鲁棒性和实现成本等指标。将 IoT、AI 和云计算等现有方法与所提出的工作进行了比较（Khang 等人，2023b）。

### 10.4.1 安全性

由于机器人系统的持续发展以及安全和安保威胁与问题的增加，机器人安全这一跨学科领域正变得愈发相关和重要（Khang 等人，2022）。

据当地警方称，机器人可以在街道上巡逻。它们接受了识别和逮捕所有街头犯罪行为的训练，如图 10.3 所示。

![](img/66ecdb8eb8654ae1c99705e55a45a836_196_0.png)

图 10.3 安全性比较。

### 10.4.2 感知水平

机器人感知主要采用需要环境输入或感官数据的算法，以使机器人能够看、触、听和移动（Hahanov 等人，2022）。

三种主要的传感器类型（视觉、力/力矩和触觉）对应三种最常见的机器人控制策略：视觉伺服控制、力控制和触觉控制。它们通常是机器人的控制器的基础，用于解释和评估感官数据，如图 10.4 所示。

与现有方法（如 IoT（65%）、AI（75%）、云计算（88%）和 BH-ANN（93%））相比，对所提出的工作进行了评估。

![](img/66ecdb8eb8654ae1c99705e55a45a836_197_0.png)

图 10.4 感知水平比较。

### 10.4.3 鲁棒性

机器人的鲁棒性可以根据控制策略的期望动作（如由阶跃引起的动作）和非期望动作（如由跌倒引起的动作）来分类，如图 10.5 所示。

![](img/66ecdb8eb8654ae1c99705e55a45a836_198_0.png)

图 10.5 鲁棒性比较。

### 10.4.4 实现成本

与制定和实施侧重于一种或多种特定循证治疗的实施策略相关的成本称为实现成本。该方法将直接影响后续干预，可能影响其效果、使用或质量，如图 10.6 所示。

实现成本（%）

![](img/66ecdb8eb8654ae1c99705e55a45a836_198_1.png)

图 10.6 实现成本比较。

## 10.5 结论

本章提出将 BH-ANN 应用于实时场景下具有机器人的柔性工业部门。以机器人方面作为未来智能工厂的指导方针，新的网络安全方案包括在完全集成的系统中与其他方面通信的神经网络。

为了验证所提系统的可行性，收集了一个工业情境数据集，用以说明采用人机协作的制造装配过程。

本研究的特征提取阶段揭示了构成对机器人严重威胁的真正困难。为了证明所提策略的有效性，展示了其各项指标。

如仿真所示，由于连接性的增强，网络安全受损的物理资产可能在自动化中导致严重的安全隐患。

未来的工业流程，包括人类操作员和机器人，将在产业变革的框架内创建（Khang，2024）。

## 参考文献

- Bhardwaj A., Alshehri M. D., Kaushik K., Alyamani H. J., Kumar M., (2022). “针对网络物理机器人系统网络攻击的安全框架。” *Journal of Electronic Imaging*，31(6)，061802. https://doi.org/10.1117/1.JEI.31.6.061802

- Hahanov V., Khang A., Litvinova E., Chumachenko S., Hajimahmud V. A., Alyar V. A., (2022). “智慧城市的关键助手——传感器与工具，”见 *AI-Centric Smart City Ecosystems: Technologies, Design and Implementation*，第 17 卷，第 10 期（第 1 版）。CRC Press. https://doi.org/10.1201/9781003252542-17

- Hajimahmud V. A., Khang A., Hahanov V., Litvinova E., Chumachenko S., Alyar V. A., (2022). “面向智慧城市的自主机器人：走向增强人类，”见 *AI-Centric Smart City Ecosystems: Technologies, Design and Implementation*，第 7 卷，第 12 期（第 1 版）。CRC Press. https://doi.org/10.1201/9781003252542-7

- Haleem A., Javaid M., Singh R. P., Rabad S., Suman R., (2022). “面向改善性工业 4.0 时代的网络安全视角：基于综述的框架，” *Industrial Robot: The International Journal of Robotics Research and Application*，49(3)，582–597. https://doi.org/10.1108/IR-10-2021-0243

- Jin S., Lian W., Wang C., Tomizuka M., Schaal S., (2022). “具有空间表征的机器人电缆布线。” *IEEE Robotics and Automation Letters*，7(2)，5687–5694. https://doi.org/10.1109/LRA.2022.3158377

- Khang A., (Ed.). (2024). *AIoCF: AI 导向的数字经济人才管理能力框架——模型、技术、应用与实施*。CRC Press. https://doi.org/10.1201/9781003440901

- Khang A., Gupta S. K., Hajimahmud V. A., Basabseh J., Morris G., (2023a). *AI-Centric Modelling and Analytics: Concepts, Designs, Technologies, and Applications*（第 1 版）。CRC Press. https://doi.org/10.1201/9781003400110

- Khang A., Vrushank S., Rani S., (2023b). *AI-Based Technologies and Applications in the Era of the Metaverse*（第 1 版）。IGI Global Press. https://doi.org/10.1201/9781668488515

- Khang A., Rani S., Gujrati R., Uygun H., Gupta S. K., (Eds.). (2023c). *Designing Workforce Management Systems for Industry 4.0: Data-Centric and AI-Enabled Approaches*。CRC Press. https://doi.org/10.1201/9781003357070

