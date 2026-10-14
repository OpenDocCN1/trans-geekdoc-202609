
Teyeb et al. (2014) proposed a method for drowsy driver detection using eye closure and head postures. The system begins by capturing video through a webcam and conducting following operations on each frame of the video. It employs the Viola-Jones method to identify the ROI, encompassing the face and eyes. Subsequently, the facial area is sub-divided into sections, and the Haar classifier is utilized to focus on the upper segment, specifically targeting the region corresponding to the eyes for analysis. Following this, identifying the eye state entails the utilization of a Wavelet network, a neural network-based approach, which is trained using image data. The learning process involves ascertaining coefficients from training images. These learned coefficients are subsequently compared with those obtained from testing images to determine the appropriate classification. The system computes the duration of closed eyes and identifies drowsiness if this duration surpasses a predefined time. Furthermore, it evaluates various head movements such as left, right, forward, backward, and tilting motions in both directions. To conduct this analysis, the video footage is divided into frames, with the system examining head images and comparing their positions to determine head postures. Subsequently, it merges the duration of closed eyes with the assessment of head positions to ascertain drowsiness. The methodology was tested using six videos simulating genuine driving conditions and the findings are displayed through a confusion matrix. It achieved a 98% accuracy rate, proving more effective than alternative detection methods.

The main problem with vision-based approach is lighting. Regular cameras struggle at night. Furthermore, many methods have been tested using data from drivers imitating drowsiness instead of using real videos capturing a driver naturally becoming sleepy.

### 2.3 Vehicle-based measures

Vehicle-based measures detect driver fatigue using vehicular features, including steering wheel angle, steering wheel grip force, lane changing patterns, and vehicle speed variability. These measures necessitate the installation of sensors on various vehicle components, such as the steering wheel, accelerator, or brake pedal, among others. The signals produced by these sensors serve as the basis for evaluating the drowsiness levels of drivers.

#### 2.3.1 Lane detection

This approach checks the vehicle’s position with respect to the middle of the lane. It is also known as the standard deviation of lane position (SDLP). Katyal et al. (2014) proposed a driver’s drowsiness detection system using lane and driver’s fatigue level. Hough transform is used to detect lanes and canny edge detection is applied over viola-jones to detect eyes and driver’s fatigue level. This information is then used to detect improper driving. Ingre et al. (2006) conducted multiple experiments and concluded that KSS ratings are directly proportional to SDLP metrics.

#### 2.3.2 Steering wheel analysis

Steering wheel analysis (SWA) is a widely used vehicle-based measure to detect driver drowsiness (Fairclough et al., 1999; Thiffault, 2003). An angle sensor is attached on the steering wheel axis to collect the data. Abnormal steering wheel reversals, steering correction periods, and a vehicle’s jerky motion indicate fatigue and a drowsy driver. Li et al. (2017) uses SWA and proposed an online drowsiness detection system to monitor the fatigue level of drivers under natural conditions by extracting approximate entropy features and using a decision classifier for detection. Zhenhai et al. (2017) proposed a solution by analyzing the time series of the angular velocity of the steering wheel. Fairclough and Graham (1999) proposed a solution by checking the steering wheel’s reversals and small SWMs. They found that drowsy drivers make fewer steering wheel reversals than typical drivers.

Many studies have shown that vehicle-based measures are not the best way to judge a driver’s drowsiness and often lead to inaccurate results. Assessing driver fatigue solely based on vehicle movement has limitations, as the measurement metrics can be susceptible to external influences like the road’s geometric attributes and prevailing weather conditions. Other factors can also affect these measures, such as road, traffic, lighting conditions, and driving under the influence of alcohol or other drugs. Steering wheel grip force on a curvy mountain road differs significantly from that of a straight highway. Furthermore, the driver’s grip can vary with road conditions. Driver may not grip the steering with that pressure on a busy road with which he grips the steering on an empty expressway.

### 2.4 Physiological measures

As drivers experience fatigue, they may observe a subtle swaying of their heads, and there is an elevated risk of the vehicle deviating from the center of the lane. Previously discussed methods for detecting this behavior, such as behavior-based and vehicle-based, possess limitations, primarily because they can only detect fatigue after the driver has already entered a drowsy state.

However, it is worth noting that physiological signals undergo discernible changes early in the onset of drowsiness. Hence, physiological signals are more apt for detecting drowsiness. Leveraging physiological signals for drowsiness detection holds the potential to mitigate the issue of false positives, which is a common challenge with existing approaches. Furthermore, it enables timely alerts, thereby averting road accidents.

#### 2.4.1 Electroencephalography (EEG)

EEG measures the brain’s electrical activity by placing some electrodes on the head and forehead. The frequency of signals ranges from 1 to 50 Hz and amplitude from 20 to 200 μV. Some frequency bands are defined as alpha waves (8–12 Hz, 25–100 μV), which measure relaxation; beta waves (faster than 13 Hz and below 40 μV), which measure alertness; theta waves (4–7 Hz, 20–120 μV), which measure drowsiness; and delta waves (0.5–3.5 Hz, 75–200 μV) helps to check if the subject is asleep.

Several studies support the connection between EEG signals and driver behavior (Campagne et al., 2004; Akin et al., 2008; Liu et al., 2010; Lin et al., 2012; Lin et al., 2013). Changes in the alpha frequency band, where the power decreases, and an increase in the theta frequency band are indicative of drowsiness. Akin et al. (2008) observed that combining EEG and EMG signals is more successful in detecting drowsiness compared to using either signal alone.

#### 2.4.2 Electrocardiography (ECG)

The ECG method records the heart’s electrical activity by positioning electrodes on the chest, arms, and legs, capturing the small electrical signals generated with each heartbeat.

-   Tsuchida et al. (2009) 的研究声称，心率变异性（HRV）可以用于检测驾驶员疲劳和困倦。随着驾驶员疲劳增加，副交感神经活动减少，交感神经活动增加。这导致心律在高频范围（0.15–0.4 Hz）向低频范围（0.04–0.15 Hz）发生显著转变。

![](img/fig19_137_1_B.jpg)

多项研究探讨了利用光电容图（PPG）和心电图（ECG）小波频谱分析来检测驾驶员疲劳和困倦。Tsuchida et al. (2009)、Arun et al. (2012)、Lee et al. (2014) 在实验结果中报告了平均预测准确率为 96%。

#### 2.4.3 电肌图（EMG）

EMG 测量肌肉的电活动，通常从下巴获取（Hostens, 2005）。当肌肉收缩时，它会向大脑发送电信号。

Katsis et al. (2004) 观察到在单调驾驶任务后，频率下降最高可达 20%，振幅上升最高可达 50%，并将其用于指示疲劳和困倦。Balasubramanian et al. (2007) 在模拟驾驶 15 分钟时，也观察到肩部和颈部肌肉的类似 EMG 变化。

#### 2.4.4 电眼图（EOG）

EOG 测量人眼前部（角膜）与后部（视网膜）之间的电位差。其主要功能之一是测量眼球运动的幅度和方向，这在检测驾驶员困倦（Shuvan et al., 2009）时非常有用。角膜与视网膜之间的电位差产生电场，EOG 传感器测量该电场并确定眼球方向。通过在每只眼的外角使用一次性 Ag–Cl 电极，并在额头中央放置第三个电极，系统可观测水平眼动（Shuvan et al., 2009）。这些电极帮助识别快速眼动（REM）和慢速眼动（SEM）等行为模式，从而辅助驾驶员困倦检测（Lal et al., 2001; Sharma et al., 2020）。

Khushaba et al. (2010) 和 Kukreja et al. (2022) 发现，单独使用 EOG 无法像单独使用 EEG 时那样准确地检测困倦。Chieh et al. (2005) 通过 EOG 监测眼动而非基于视频的眼动监测，并实现了 80% 的准确率。

## III. 结果与讨论
