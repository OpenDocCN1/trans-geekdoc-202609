
Changes in daily life activity (preparing food, showering, walking, sleeping, watching television, going to the toilet, having dinner/lunch/breakfast, cleaning the house and so on) patterns and their occurrence time and frequency are key indicators in determining the cognitive status of elderly people. Assessing the cognitive status of elderly people by tracking their daily life activities in a specially designed smart-home would be very useful for caregivers, medical doctors and clinicians so that early treatment would be possible.

Unfortunately, there exists no data assessing the cognitive abilities of ageing persons. Thus, in this study, we tackle the scarcity of the data demonstrating the abnormal behavior of elderly people by generating data. Moreover, we aim to recognise daily life activities by taking their neighbourhood information into account. The spatio-temporal information of activities and their ordering and frequency are important for understanding the cognitive abilities of elderly people. Thus, we emulate activity recognition and abnormal behavior detection problems as a sequence labelling problem. In the present study, we first model activities as a sequence and then detect the abnormal behavior. The rest of the chapter is presented as follows. Section 10.2 provides an overview of dementia indicators. Section 10.3 summarises the literature work, while Section 10.4 describes the datasets used. Section 10.5 describes the methods used and presents the experiments. Lastly, Section 10.6 concludes the chapter.

## 10.2 Indicators of Dementia

-   [早期识别认知障碍](https://wiki.example.org/feynmans_learning_method)可以使早期治疗成为可能，但研究表明 75% 的痴呆病例未被发现 \[9\]。最近的研究 \[10\] 表明，日常生活活动模式的异常可能是早期发现这些情况的线索。此外，最佳指标可以通过监测随时间变化的活动趋势和变化（如睡眠问题或完成任务困难）来检测 \[11\]。例如，忘记吃晚饭、失眠或频繁上厕所都是认知障碍的迹象。还有进食习惯异常（例如深夜吃零食）、夜间频繁醒来或因饮水不足导致的脱水。患者可能在危险情境中出现问题，如忘记关闭加热器、烤箱或炉子 \[11\]。认知衰退的老年人可能会因困惑而出现后果，例如无法运行洗碗机或在电话簿中混淆名字。

### 10.3 Literature Review

#### 10.3.1 Cognitive Status Assessment

-   许多研究尝试自动化老年人在家的认知状态评估 \[23, 24, 25, 26, 27, 28, 29, 30\]，并采用多种机器学习方法，如 `Naïve Bayes` 分类器和支持向量机 (`SVMs`) \[31, 32, 38\]、受限玻尔兹曼机 (`RBMs`) \[28, 33\]、马尔可夫逻辑网络 (`MLNs`) \[26, 27, 29\]、隐马尔可夫模型 (`HMMs`) \[12, 34\]、随机森林方法 \[19\]、隐向量随机场 (`CRFs`) \[35\] 和循环神经网络 (`RNNs`) \[36\]。

-   当前的认知评估方法依赖于专家让老年人填写问卷或回忆过去的事件，这种方法需要专业知识，可能带有偏见。例如，在 `Ref. [23]`，老年人需要在摄像头监控下完成一系列活动并获得评分。其他研究如 `Ref. [37]` 则通过测量活动持续时间和传感器激活次数来评估认知能力。这类方法会打断日常生活的自然流程。另一方面，基于规则的诊断方法需要通过特定规则整合领域知识，且每个个体的规则需要定制，因为个人的夜间醒来或夜间饮水习惯可能不同。我们的方法的优势在于不使用任何专家或领域知识，而是从训练数据中学习正常行为，并利用老年人的日常生活习惯进行评估，从而提供一种不打扰的评估方式。

-   在 `Ref. [39]`，将运动片段定义为活动曲线，并通过比较曲线来检测异常活动。`Ref. [40]` 使用基于位置的概率时空模型计算主体行为的可能性，并通过交叉熵测度检测如长时间卧床或未在卧室睡眠等异常行为。`Ref. [12]` 将 `HMM` 与模糊规则结合，检测与持续时间、时间和频率相关的异常。

-   `Ref. [35]` 使用隐状态条件随机场 (`HCRF`) 模型活动，并通过阈值方法检测异常行为；`Ref. [26]` 将概率逻辑网络与基于规则和概率的推理结合，检测异常行为。该研究的一个缺点是活动步骤在构建模型前就已预先定义，且规则因人而异，定义规则耗时。`Ref. [27]` 通过规则诱导方法自动发现规则，基于正常和异常活动的数据。然而，我们的方法通过训练集自动学习正常活动模式，无需显式规则，并以序列信息的上下文来定义异常行为 \[26, 35\]。

#### 10.3.2 Deep Learning

-   近年来，深度学习方法被用于智能家居中的活动识别。这些方法包括卷积神经网络 (`CNNs`) \[41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 67, 68, 69\]、深度信念网络 (`DBN`) \[33\]、受限玻尔兹曼机 (`RBMs`) \[28, 33, 51, 52\] 和 `RNNs` \[43, 44, 53\]。虽然 `RBMs` 在特征提取和选择方面更受青睐 \[51\], 但它们在 `CASAS` 数据集上表现优于 `HMMs` 和 `NB` \[52\]。`CNNs` 在使用可穿戴传感器识别活动方面很受欢迎 \[33, 41, 42, 43, 45, 48, 51\]。然而，很少有研究 \[52, 67–71\] 将深度学习方法应用于基于传感器的活动识别，这仍需进一步研究。

`Auto-encoders` are being used for anomaly detection on time-series data `cvar = avar + bvar` \[57,58\]. In `Ref. cvar = avar + bvar` \[56\], the authors use Recursive Auto-Encoders for predicting sentiment distributions. Instead of using a bag-of-words model, this model exploits a hierarchical structure and uses compositional semantics to understand the sentiment. In `Ref. cvar = avar + bvar` \[59\], the authors extract patterns in daily life activities as segments of an activity. This shows that the extracted movement vector can be used to differentiate high-level activities. The idea behind this is residents at a smart-home follow the same routine during the performance of the same activities such as moving around the kitchen sink while washing the dishes.

## 10.4 Datasets and Data Generation

Elderly people suffering from dementia may have difficulties performing activities such as managing medication, cooking and housekeeping. In this research, we analyse sequential daily life activities (performed in a sequential order without any interruption) to detect the abnormal behavior. We also assume that there is only one occupant living in a smart house. Cooking, sleeping, going to the toilet, working, cleaning, washing dishes and so on are examples of daily life activities. We focus on these types of activities since they are promising to reflect on dementia cases in a scenario of daily life. Inspired by data simulation techniques to generate activity instances `List.of(arg0, arg1, arg2)` \[17, 18, 19\], we generate abnormal behavior.

We will first describe the datasets used and then the abnormal behavior generation method will be presented.

### 10.4.1 Datasets

In this research, we used three datasets:

*   `Van Kasterenen cvar = avar + bvar` \[60\] dataset: In this dataset, there are daily life activities such as sleeping, cooking, leaving home and so on and the data were collected in three different households in durations less than a month.

*   `Aruba testbed of CASAS cvar = avar + bvar` \[16\] dataset: In this dataset, sensors such as motion, door and temperature are used. However, we use motion and door sensors in our study. In total, there are 11 activities in this dataset and the collection was done in 224 days.

*   `WSU testbeds of CASAS cvar = avar + bvar` \[16\] dataset: In this dataset, there are five activities, which are making a phone call, hand washing, meal preparation, eating and cleaning. Twenty instances of each activity were performed by 20 students in (1) `adlerror` and (2) `adlnormal` versions. While normal behavior is reflected in the `adlnormal` version, residents were told to include errors in `adlerror` to simulate the difficulties of elderly people.

### 10.4.2 Data Generation

Abnormal behavior in the daily life activities of elderly people is divided into two parts: (1) activity-related anomalies and (2) sub-activity–related anomalies. In activity-related anomalies, an activity itself is totally normal while there is an anomaly related to its frequency or its timing in a day. On the other hand, the sub-activity–related anomaly is related to the context and the quality of activity performed such as frequency of sensor activations involved as well as their order and correlation. In the first one, activities as a whole are repeated or forgotten (e.g. having dinner); while in the second one, some steps (sensor activations) of activities are forgotten or repeated (e.g. adding salt to the dish).

#### 10.4.2.1 Activity-Related Abnormal Behavior

To simulate these types of indicators, we insert a set of actions into the whole day actions of activities (see `Algorithm 10.1`), which will give multiple instances of the same type of an activity. Moreover, insertion in some inadequate time of the day will generate time-related abnormalities such as waking up and eating. We insert the following activities: preparing meal, eating, working, washing dishes, leaving home and entering home into the normal activity sequences of the Aruba dataset.

In all, we manually generate 77 abnormal activity instances on the Aruba dataset. A set of modified abnormal behavior is depicted in `Table 10.1`. The following abbreviations are used for the activities. S: Sleeping, P: Meal preparation, E: Eating, R: Respirate, W: Working, B: Bed to the toilet and H: Housekeeping. The inserted activities are shown in **bold**.

`TABLE 10.1 Examples of Abnormal Behavior`

| **Original** || **Modified** || **Abnormality** |

| --- | --- | --- |
