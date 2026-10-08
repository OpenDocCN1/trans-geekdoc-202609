
Specifically, we obtained written informed consents from the participants before the data collection, advertised data collection for inviting voluntary participants, explained to the participants that they could quit the experiment anytime they want, and provided snacks as a reward for their participation. The details of the data collection procedure are explained in the following sections.

We collected the EEG and GSR data from 28 Korean participants (13 males and 15 females) who were either students or staff at a university in the Republic of Korea. The participants' ages ranged from 20 to 34, with an average age of 23.62. We collected the data in two sessions: the first session was carried out with 18 participants (6 males and 12 females), and the second session was carried out with 10 participants (7 males and 3 females). All data collection procedures were designed and executed with careful consideration of legal and ethical issues. All participants elected to join the experiment voluntarily, and were instructed to quit if they felt the urge to do so. To secure the safety of the participants, an emergency kit was prepared as a countermeasure for accidents. All collected data were anonymized and stored in a password-protected data storage. Finally, a data collection protocol (Section 3) was designed with consideration of the participants' legal rights.

An EEG sensor produced by Muse [36] and a GSR sensor produced by Seed [37] were used in this study (Figure 2). The upper section of Figure 2 shows the EEG sensor, however, according to the EEG sensor manufacturer, the electrodes are located at positions FP1, FP2, TPY, and TP10 of the head [36]. The mapping of head locations defined by Jasper [38], and it is used in neuroscience. The EEG data were captured but data from FP1 and FP2 were utilized. This is because TPY and TP10 were not well attached to the parts of the scalp during collection. The EEG sensor recorded data at a rate of 220 Hz and provided the power spectral density (PSD) values for each electrode. According to the sensor manufacturer, the types of PSD data were absolute band power (ABP), relative band power, and others [36]. The sampling rate of these data was 10 Hz. To calculate ABP, we applied the fast Fourier transform algorithm. We calculated PSD by the following frequency bands [36]:

- Delta: (1-4) Hz
- Theta: (4-8) Hz
- Alpha: (7.5-13) Hz
- Beta: (13-30) Hz
- Gamma: (30-44) Hz

The lower section of Figure 2 illustrates the GSR sensor that was used in this study, along with the finger electrodes. These electrodes were attached to the index and middle fingers of the participants. The GSR sensor captures micro voltages (MV) between the fingers using the attached electrodes. Furthermore, the sensor calculates skin resistance (SR) using the MV input. The formula for calculating SR using MV is provided by the sensor manufacturer [37], and is replicated in Equation (1). The sensor was connected to an Arduino Uno device, and the captured data were transmitted to a computer at 192 Hz sampling rate.

$$SR = ((1024 + 2 * MV) * 1000) / (512 - MV).$$$$

(1)

![](img/601340ca744b738277eef45ff127492a_142_0.png)

Figure 2. (a) EEG sensor, and (b) GSR sensor.

## 3.3. Protocol

Figure 3 presents the protocol of data collection. In the introduction stage, the participants were presented a page showing a consent form of the experiment. The information on the consent form stated that we would use the collected data only anonymously for academic purposes. Furthermore, the participants were instructed that they could stop the experiment anytime they feel uncomfortable. In the Swarm, and a Korean comedy video clip were used to evoke non-boredom. These video clips were chosen to entertain the participants so they would not become bored. To evoke boredom, a looping video was played in which a small circle slowly tracing the boundary circle. Furthermore, the Future Picture System [39] was shown for 30 seconds before showing each video stimuli. When the participants watched the videos, they were introduced to watching (by pressing a button) at any time they chose. Thus, each participant's data length was different, with the shortest time being 71.3 s.

The data collection consisted of two sessions. The sessions were otherwise identical except for the non-boredom video stimulus (i.e., the game trailer and the comedy show clip). The reason for carrying out data collection in two sessions was to get a content-independent classification result. In other words, we wanted to see whether the change of non-boredom video has an effect on the classification. After watching the video stimuli, the participants answered a questionnaire to measure the strength of boredom that they felt. The questionnaire had two questions: one for the bored video, and another for the non-boredom video. The questionnaires were designed to be answered on a 5-point scale, and the range of the scale was "None" to "Very much."

![](img/601340ca744b738277eef45ff127492a_143_0.png)

Figure 3. Protocol of data collection.

## 4. Machine Learning Methods

In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

### 4.1. Window Size

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

### 4.2. Features

In Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

#### 4.2.1. EEG

In Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.

As explained in Section 4.1, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom. In this section, we describe the procedure for feature extraction and machine learning techniques for analyzing the collected data to classify boredom.
