
![](img/be45bf301a3c0ebefb162571e2625fab_94_0.png)

Fig. (4.9). Types of Pooling.

The number of layers of Convolution Layer, RELU and Pooling required depends on how complex the image is. However, a classic CNN model would be similar to the Equation (4a); with n ranging between 2 and 5 depending on the size and complexity of the image.

```
Input → Conv → ReLU → n * (Conv → ReLU → Pool) → Full Connection    (4a)
```

### 4.4.3. FULL CONNECTION

Fully connected layer is a neural network like in Fig. (4.10) where x is the input from the vector formed after flattening the convoluted matrix and y represents different probabilities of what the image might represent [12]. For example, if an image of car is given as input, it might show as 90% car, 7% train, 2% motorcycle, etc. The FC layer is one of the simple ways to make a machine learn about high level features of the image during the training of the dataset.

![](img/be45bf301a3c0ebefb162571e2625fab_94_1.png)

Fig. (4.10). Full Connection.

AlexNet, VGGNet, ResNet, GoogleLeNet are some of the many architectures of CNN developed over the years for the purposes of image detection and classification.

## 4.5. AUDIO SIGNAL PROCESSING

As the title suggests, audio signal processing is the field of study from signal processing which deals with the manipulation of sound signal. Audio Signal Processing is not a new field of study. It has been used earlier in radio, phonography and telephonic communication. Nowadays, deep learning techniques are used for audio signal processing. In audio signal processing, the main focus is always on how to extract important frequency components from the audio sample which can be used to efficiently distinguish the audio signal.

Audio signals are typically in the range of 20 Hz to 20 kHz. These are longitudinal waves created by compression and expansion of air. When the sound enters our ear, it gets transmitted to the cochlea which is filled with thousands of hairs of variable size inside a fluid filled membrane. The short hair responds to higher frequency while the long hair responds to the low frequency of sound. Thus, the ear acts like a natural Fourier transform analyser [14].

The first step in audio processing is sampling which is defined as process of converting continuous signal into discrete values. The amount of information present in the discrete signal is defined by sampling frequency or rate. A higher sampling rate indicates less loss of information but the computational complexity of processing the discrete audio signal increases.

The amplitude of each sample of the discrete signal is also an important feature.

The processing of the entire audio signal at the same time can pose higher computational complexity apart from high time and resource consumption. The best way is to divide the audio signal into small frames of 20 – 40 ms. The power spectral density of each frame is calculated by applying Fourier transform on the autocorrelated audio signal. It shows the distribution of power among various frequency in the frame as shown in Fig. (4.11).

One important fact about the human ear is that the sounds with higher frequency is difficult to perceive than the sounds of lower frequency. This why the mel filter banks are used. The mel scale is defined as the scale of pitches judged by listeners to be equal in distance from one another. The reference point is taken such that 1000 mel = 1000 Hz. The mel filter bank acts like a human ear as the mel scale changes rapidly for less frequency than for higher frequency as shown in Fig. (4.12).

![](img/be45bf301a3c0ebefb162571e2625fab_96_0.png)

Fig. (4.11). Power Spectral Density.

![](img/be45bf301a3c0ebefb162571e2625fab_96_1.png)

Fig. (4.12). Mel Scale.

The formula used to convert frequency to mel is given by Equation (5a):

$m = 2595 * log_{10}\left(1 + \frac{f}{700}\right)$

(5a)

The sum of energies in each mel filter is taken and passed through discrete cosine transform (DCT). The DCT extracts the most important information and peaks from the audio signal. The peaks represent the gist of the information [15]. This complete process creates a new spectrum known as Mel cepstrum as shown in Fig. (4.13).

Typically, the first 13 coefficients obtained from the Mel frequency spectrogram is known as MFCC. It contains the most useful information of the audio signal as it can be fed into machine and deep learning algorithms consisting of recurrent neural networks (RNNs) or other memory networks for audio and signal analysis. It is one of important and state-of-the-art tool to extract information from the audio signal.

![](img/be45bf301a3c0ebefb162571e2625fab_97_0.png)

Fig. (4.13). Mel Cepstrum.

## 4.6. DEEP LEARNING IN DETECTION OF SLEEP APNEA

Sleep Apnea is a sleep disorder where breathing stops abruptly for at least ten seconds and starts repeatedly. Loud snoring and feeling of tiredness are two important symptoms of sleep apnea. In the beginning sleep apnea is detected by using full night polysomnography. This is called type 1 sleep study. It consumes a lot of time and requires a lot of space. Moreover, it involves a lot of wirings connected to various parts of the body which is very inconvenient for the patient. In type 4 sleep study which uses acoustic sensors and pulse oximeter makes it more portable and requires a smaller number of signals. In this study a deep convolutional neural network is first trained with training datasets in order to establish the crucial parameters and relationships among them [16]. The designing of a good convolutional neural network involves a good amount of trial and error. The performance of the neural network totally depends on extracting the essential parameters through feature extraction. It is then used on test data to determine whether a particular patient has sleep apnea or not. The time required in type 4 sleep study during the training and implementation of deep learning model can be high due to complex nature of data and neural network but once the deep model is created, the testing requires little to no time.

### 4.6.1. System Design

The entire system architecture of the proposed model is shown in Fig. (4.14).

![](img/be45bf301a3c0ebefb162571e2625fab_98_0.png)

**Fig. (4.14).** Flowchart of the proposed Model.

The detection of sleep apnea from sleep studies generally consists of three basic steps. The first step is to collect data from the patient using SPO2 sensor to determine oxygen concentration in the blood, thermistor, nasal pressure and thoracic and abdomen movement. So, when apnea occurs, the sensors detect decreased nasal pressure, thoracic and abdomen movement as time-interval *T₁* in Fig. (4.15) compared to normal breathing levels and the brain will send some signals to muscle to perform breathing activity and this is detected by EEG. During apnea, there is a sudden change in brain activity which is called arousal as the brain shifts from deep sleep to lighter sleep depicted by time-interval *T₂* in Fig. (4.15). During the arousal event, suddenly the lungs cease to breathe and thus the concentration of oxygen in the blood is disrupted causing oxygen desaturation as per the over lapping time-interval *T₂* and *T₃* in Fig. (4.15), which is detected by the SpO2 sensor [16, 17].

![](img/be45bf301a3c0ebefb162571e2625fab_98_1.png)

**Fig. (4.15).** Timeline of events for when Sleep Apnea occurs.

The raw data collected is fed to user defined software which uses deep learning techniques for analysis. This is the second step in system design. It determines whether sleep apnea is occurring or not and if it is occurring what is its duration and various other information.

In the third step, the doctors or health professionals determine the seriousness of this sleeping disorder based on the data produced by the software and accordingly the doctor will prescribe the required medication.

### 4.6.2. Detection of Apnea or Hypopnea Event

Sleep Apnea and Hypopnea are two different versions of sleep disorder. Apnea is caused due to complete obstruction of air while hypopnea is due to partial obstruction of air. So, in order to detect both of these two disorders, the variation of amplitude and duration of variation is to be calculated from the incoming signal from the sensors. The part of the signal caused due to apnea is flatter than the rest of the signal. The amplitude is smaller than the rest of the sound wave. As shown in Fig. (4.16), the ratio of amplitude of attenuated signal with amplitude A₂ at time interval T and the normal signal with amplitude A₁ is calculated. Generally, apnea is detected if the ratio of the normal signal and the attenuated signal at T is twenty percent less than normal and for hypopnea the maximum threshold is less than seventy percent. The time duration T for which this disruption of breathing is detected must be greater than or equal to ten seconds for apnea [18].

![](img/be45bf301a3c0ebefb162571e2625fab_99_0.png)

Fig. (4.16). Amplitude Threshold for Apnea Event.

### 4.6.3. Deep Learning Model

In this work, the authors have proposed a unique deep learning model to classify between healthy patients and the ones suffering from sleep apnea. The deep learning architecture using convolution neural networks is shown in Fig. (4.17). The input vector X is assumed to be the sampled SPO2 signal consisting of {x₁, x₂, x₃, ...., xₙ} samples where n = total number of samples. The layers between the input and the output layer are the hidden layers.
