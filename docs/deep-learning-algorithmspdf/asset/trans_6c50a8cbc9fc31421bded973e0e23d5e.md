
The EEG signals are of low quality because of different layers of tissues between the EEG cap and the signal source as shown in Figure 2. The potential created is in a range of tens of microvolts, and these electrodes need to have powerful amplifiers in order to acquire meaningful signals.

`**Figure 2**`. EEG: (a) subject wearing a 32-electrode EEG cap; (b) standardized electrode placements.

`**Need of BCI**`

Brain-computer interface-based technology is a developing field, and it has been under focus by many industries to innovate and make everyday life tasks easier. One of the questions which arises in the mind is why we need BCI systems? BCI system is a complex technology, no doubt, however, leading to a simpler life.

Following are the main reasons why we need to focus on this technology:(i) Control of devices can be made easy through just our thoughts(ii)Making a decision and then performing a task takes time, while operating a device using thoughts or technically our brain waves is easier(iii)Re-establishing

`# #`

affected by brain-related diseases

`***Individuals in Need of a BCI to Re-Establish Motor Control and***`

`***Communication***`

A wide range of neurological diseases such as motor neuron diseases and spinal cord injury may lead to severe paralysis of the motor muscles, restricting the patient to control artificial devices through only a few muscles and thereby termed as “locked-in,” while people who have completely lost their motor control are termed as “completely locked-in.”

本书版权归Arcler所有

![Image 1262](index-291_1.png)

![Image 1263](index-291_2.png)

![Image 1264](index-291_3.png)

![Image 1265](index-291_4.png)

`Deep Learning Algorithm for Brain-Computer Interface`

265

Evident that the normal communication channel from the brain to the limbs is lost, BCI is used to re-establish the communication through an alternative route.

Even being applicable to a healthy person, BCI systems can be used to employ numerous tasks from the users using the signals generated from the brains to control applications as presented in the following \[4\]: *(1)*

`*Noninvasive Brain-Computer Interface Research at the Wadsworth Center*`。The research conducted at the Wadsworth Center was to study different approaches employed in the BCI to control a computer screen cursor to analyze their advantages and disadvantages; one approach was sensory-based rhythm control in which the selected features in the frequency domain were based on the potentials created by motor imagery and linear regression was employed so that they can be converted as control signals to move the cursor.

The other procedure was the P300-based cursor control in which the user focuses attention on the desired symbol and is provided with a matrix to produce time-varying stimuli and linear regression is utilized to allow these signals as a control input to move the cursor.

The research suggested that the BCI is an application-oriented approach and depends entirely on user training; the EEG features dictate the BCI system for speed, accuracy, bit rate, and usefulness.

Sensorimotor Rhythms (SMR) is an approach employing better results for control tasks such as controlling a screen cursor, while the P300-BCI system was slower as compared to the SMR-BCI.

*(2) The Berlin Brain-Computer Interface: Machine Learning-Based*

`*"#$%* . The researchers for the

Berlin brain-computer interface employed sensory motor rhythms, i.e., thinking of moving the left hand or right hand and used

+# #

While testing their trained model, they achieved an information transfer rate above 35 bits per minute (bpm), and overall spelling seed was 4.5 letters per minute including correcting the mistakes, using 128-channel EEG and using feedback control for untrained users in order to properly train the machine learning algorithms, thereby reducing the training user time used in the voluntary control approach \[2\].

本书版权归Arcler所有

![Image 1266](index-292_1.jpg)

![Image 1267](index-292_2.png)

![Image 1268](index-292_3.png)

![Image 1269](index-292_4.png)

`Deep Learning Algorithms`

266

`**Structure of the BCI**`

The steps of the brain computer interface system include the following:(1) Brain activity measurement/recording methods of the BCI(2)Preprocessing techniques(3)Feature extraction(4)Machine learning implementation/

classification(5)Translation to control signal

`***Preprocessing***`

In BCI, preprocessing techniques consist of data acquisition of brain signals to check the signal quality without losing important information; the recorded signals are cleaned and conduct noise removal to acquire relevant information encoded in the signal. As mentioned above, the EEG signals are of poor quality; even the commercial 50 Hz frequency, due to nearby appliances, can corrupt the EEG signals, and the users are also advised not to think anything else apart from the stimuli as presented. In preprocessing, using Fourier transform or Fourier series, the signals are taken into the frequency domain and studied what frequency content is present in the signal. The undesired 60 Hz frequency signal and undesired signal produced by performing actions other than the said stimuli are then filtered out using a notch filter as mentioned in Figure 3.

`**Figure 3**`. BCI block diagram.

`***Feature Extraction***`

Feature extraction plays a vital role in brain-computer interface applications; the raw EEG signals are nonstationary signals that are corrupted by noise or due to artifacts present in the environment where they are being recorded, but still meaningful information can be extracted from them. The data 本书版权归Arcler所有

![Image 1270](index-293_1.jpg)

![Image 1271](index-293_2.jpg)

![Image 1272](index-293_3.png)

![Image 1273](index-293_4.png)

![Image 1274](index-293_5.png)

`Deep Learning Algorithm for Brain-Computer Interface`

267

dimensionality is also reduced to process it better, and machine learning models are applied. This method is essential to increase the classification accuracy of the BCI system.

EEG signal is a time-domain nonstationary signal, and the relevant information such as signal energy is analyzed as a function of time or frequency later; relevant statistic measures are adapted to properly explain the characteristics of the signal.

Some of the commonly used feature extraction techniques are listed as follows.

Short-time Fourier transform is a frequency-domain feature extraction technique in which the EEG signal is convolved with a window function to extract the relevant frequency features of the brain which are broken down as sinusoids at different frequency ranges.

Mathematically, it is represented as

(1)

where *x*\[ *k*\] is the input EEG and w\[ *n* – *k*\] is the window multiplied to

' \*

Discrete-time and continuous-time wavelet transform is a time frequency-based feature extraction technique that allows better temporal and spatial resolution in which the EEG signals are produced in the form of wavelets at different frequency ranges of interest as shown in Figure 4.

**Figure 4**. Feature extraction using short-time Fourier transform.

本书版权归Arcler所有

![Image 1275](index-294_1.jpg)

![Image 1276](index-294_2.jpg)

![Image 1277](index-294_3.png)

![Image 1278](index-294_4.png)

![Image 1279](index-294_5.png)

`Deep Learning Algorithms`

268

The technique of wavelet transforms as adapted in the literature is a filtering continuous application of high-pass and low-pass filters to extract the wavelets of the signal which, when added together, constitute the original signal and downsampled by a factor of 2 as shown in Figure 5.

**Figure 5**. Wavelet transform.

g and *h* + +

' ^^ \[5\].

`***Neural Networks***`

Before starting to explain what deep learning is, it is first beneficial to explain the role of deep learning and its fundamental blocks.

which is composed of speech recognition and computer vision to natural language processing in the context of the BCI; the input features which are

\# \* #

