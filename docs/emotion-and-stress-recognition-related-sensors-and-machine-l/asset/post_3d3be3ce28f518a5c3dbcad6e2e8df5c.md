
fast movements of Centre of Pressure as a valuable feature in detecting stress. A similar approach was used to detect interest levels of students [78]. This approach required instrumenting chairs with high-resolution pressure sensors, which may not be scalable. However, we believe the sitting posture variations should reflect the foot posture and motion variations. In literature, smart insoles have been used to detect points unobrusively [25,79]. Hence, a smart insole-based solution could be a practical and unobtrusive solution to identify stress that is induced by body language, as as through tracking movements and posture characteristics.

The base of the StressFoot prototype is a pair of sport shoes (Figure 1A). To sense the pressure distribution of the foot, we insert a pair of pressure insoles (UK size 9–10). These insoles are commercially available from sensing.tex [80] and offer 16 pressure sensors that rely on a force sensing technology (Figure 1B). Insole is aligned with the critical points discovered in previous work [1,82]. To drive the sensors, we developed a voltage divider interfacing the interface with the SparkFun Razor board that consists of an SAMD21 microprocessor manufactured by At Corporation in San Jose, CA, USA. To understand the angle and motion of the leg, we also used the accelerometer of Y DOF IMU (MPU-9250) manufactured by InSense in San Jose, USA that connects with the microcontroller board, which was tied to the user's ankle. We decided to only utilise the Accelerometer (X,Y,Z) data, since it provides sufficient information. The prototype has a 3.7 V, 400 mAh LiPo battery and an SD card, to allow a fully wireless operation, without constraining the user's movements. The prototype can be used for approximately 16 h when it is fully charged.

![](img/601340ca744b738277eef45ff127492a_326_0.png)

**Figure 1.** Prototype: (A) shoe, (B) sensing.tex insole, (C) ankle strip, (D) SAMD21 microprocessor board with inertial measurement unit (IMU), secure digital (SD) card, voltage divider circuit and (E) 400 mAh Battery.

We ran a pilot study with 5 participants, in which we asked the users to complete the minesweeper game in a limited time. We presented a clock to the user, and an observer was present to make negative comments on the user's performance. Among all participants in the stress situation, we observed a change in leg posture and different foot contact with the floor. Two participants demonstrated a nervous leg shaking and foot tapping. Our prototype is designed to identify these unique characteristics by sensing pressure distributions of the foot, as well as tracking the foot angle and motions. We defined 10 low-level features reflecting these behaviours, which are:

### 2.3.1. A: Foot Pressure

The forefoot pressure was calculated by adding the pressure of 12 sensor points located at the forefoot area of the insole. To calculate rear-foot pressure, the sensor readings of 4 sensors located at the heel area were added together. The sensor layout is depicted in Figure 2.

```
$P_F = \sum_{i=1}^{12} P_i$
```

```
$P_R = \sum_{i=13}^{16} P_i$
```

Before summing the raw data, we applied a moving average filter of a 1 s window size to filter out high frequency noises. Finally, we calculated the total foot pressure by summing up all pressure.

```
$P_T = \sum_{i=1}^{16} P_i$
```

Since the features are independent from previous data, all pressure features were segmented into 10 10 s non-overlapping windows. The mean of each window is used for the model training.

![](img/601340ca744b738277eef45ff127492a_327_0.png)

### 2.3.2. B: Centre of Pressure

Literature has shown the Centre of Pressure (CoP) as an interesting feature to understand different postures and motion while standing [23], as well as sitting [77]. Therefore, we calculated the CoP for both dimensions (X-axis and Y-axis—see also Figure 3B) by a weighted average calculation as mentioned in prior work [23]. The CoP was also calculated over 10 s of non-overlapping windows since it is independent from the previous window.

```
$Y_{CoP} = \frac{\sum_{i=1}^{12} P_i Y_i + \sum_{i=13}^{16} P_i Y_i}{P_F + 3P_R}$
```

```
$X_{CoP} = \frac{\sum_{i=1}^{12} P_i X_i + \sum_{i=13}^{16} P_i X_i}{P_F + 3P_R}$
```

## Feature Models

![](img/601340ca744b738277eef45ff127492a_328_0.png)

A: Forefoot Pressure
B: Center of Pressure
C: Foot/Leg Pressure
D: Foot Tapping

Accelerometer
Study 1:
Study 2:
Study 3:

Plantar Pressure Inside
Constructing Validity
Empirical Replicability
External Validity

**Figure 3.** To detect stress, we present a shoe prototype incorporating pressure sensitive inside an IMU unit around the ankle. Based on literature and observations, we propose four features that can reveal the user's stress level. We show that a significant forefoot pressure, deviations in centre of pressure, different foot/leg pressures, and tapping of the foot, can indicate elevated stress level. To validate generality, we conducted three studies: Study 1—Constructing Validity, Study 2—Empirical Replicability and Study 3—testing for External Validity. Our proposed models show reasonable accuracy and robustness across different users.

The acceleration data of each axis (aX,aY,aZ) minimize the leg/foot pressure defined by the knee angle as in Figure 3C. Similar to mentioned features, the raw data of each axis was segmented into non-overlapping windows and the mean of each window was used in training. Since the sampling rate was 50 Hz, 500 data points were taken in each 10 s window for all axes. If the number of data points per window is W = 500:

```
$aXMean = \frac{1}{W} \sum_{t=1}^{W} aX$
```

```
$aYMean = \frac{1}{W} \sum_{t=1}^{W} aY$
```

```
$aZMean = \frac{1}{W} \sum_{t=1}^{W} aZ$
```

The dominant and median frequency of each axis are used to describe foot motions, such as foot tapping, waving and leg shaking. We recognise that some motions may be minimal. To avoid cancelling low-amplitude motions when calculating vector, we deployed the axis-inversion algorithm introduced [8]. For instance, if we inverted X axis of the accelerometer values $aX_{inv} = MAX(aX) - aX$. After segmenting the signal into 10 non-overlapping windows, we calculated nodes with a different inverted axis. From the resulting signals, the highest peak-to-$V_{3D}$ was selected for further processing. Then, FFT was used to identify the dominant and median frequency of the signal:

```
$F_D = F_{MaxEnergy}(FFT(V_{3D}))$
```

```
$F_M = F_{MedianEnergy}(FFT(V_{3D}))$
```

As elaborated before, conceptual-wise leg/foot postures and movements would yield important information that could induce stress. Therefore, in our first study, we aim to construct the validity of this concept by developing a machine learning model that allows to distinguish acute stress and relaxation. The study protocol was approved by the University of Auckland Human Participants Committee.

### 3.1. Participants

The participants had to be at least 18 years of age, English speaking and able to provide consent. In addition, participants needed to have a foot size of UK 9-10 to match the size of the prototype. Participants with prolonged foot-related injuries were excluded. We recruited 23 healthy participants (12 Males and 11 Females) aged between 21-32 years old (M =26.4, SD = 3.17).

### 3.2. Apparatus

To collect the data, we used the StressProt features [85] the Empatica E4 wristband was used to collect the participant’s EDA. All the study tasks were executed and generalised on a 13” Macbook Pro, which was connected to an extended LED monitor (see Figure 4).

![](img/601340ca744b738277eef45ff127492a_329_0.png)

**Figure 4.** Experimental setup: (A) StressProt prototype, (B) Empatica E4 wristband, (C) Macbook Pro, (D) Dell LED monitor and (E) adjustable chair.

### 3.3. Procedure & Tasks

After explaining the aim of the study, participants were required to fill out consent forms. Participants were informed that the study aims to explore behavioural changes while performing tasks which induce stress and relaxation. We collected demographic data and asked the participant to wear the wearables. The participants were asked to sit in front of the Macbook Pro with an extended display as shown in Figure 4. We allowed the user to adjust the chair and the distance of the table according to their personal preference. During the study, they were allowed to cross their legs. However, not to take the foot out. Once the setup was complete and the user was comfortable, we asked them to complete four tasks. The first, the second and fourth tasks intended to create relaxation. The order remained consistent for all participants. The participant had to fill a questionnaire. On a 7-point Likert scale, the users had to rate their perceived stress level, energy level and how pleasant they found the task. A NASA Task Load (NASA TLX) [86] was conducted to calculate the overall workload per task.

### 3.3.1. Task 1 [Stroop]: Stroop Color and Word

The Stroop color and word test is a common stress test (Stroop Test) [87] in many previous works [10,88,89]. For our study, we customised an open source Matlab-based Stroop Tool to display four tasks (“Red”, “Magenta”, “Green” and “Blue”) on the screen. Participants were de-facto asked to type the first letter of the colour (‘R’, ‘M’, ‘G’, ‘B’). After each answer, the program provides the result by displaying the word “correct” or “incorrect”.
