
# LSTMs follow an artificial RNN architecture

LSTMs follow an artificial RNN architecture, which has both feedforward and feedback connections \[16–26\]. It can process entire sequence of data at a time, so, this method got popularity in the field of DL. It has wide range of applications like Intrusion Detection Systems, connected, unsegment handwriting analysis, speech and video analysis, and anomaly detection in network traffic.

It has one cell and three gates, i.e., input, output, and forget gate (as shown in [Figure 7.6](#c07.xhtml#fig7-6)), where the role of the cell is to remember values at random time intervals and gates control the flow of information between the cells or if anything can be dropped out.

![Figure 7.6 Long short-term memory networks.](images/fig7-6.jpg)

[**Figure 7.6**](#c07.xhtml#rfig7-6) Long short-term memory networks.

## Advantages of LSTMs

*   It can perform processing of dataset, classification from the dataset.

*   Based on times series data, it can make predictions.

*   It has ability to bridge unknown lapses between events in the flow.

*   It can address the issues of vanishing gradient of traditional RNNs.

*   It is not sensitive to gap length unlike Hidden Markov Models and other sequence learning techniques.

*   LSTMs are strongly capable to achieve classical results in all the machine translation applications.

## Disadvantages of LSTMs

*   For fine precision counting time steps to achieve, additional counting methods may be required.

*   Number of gate requirement is more as each memory cell block requires an input and one output gate.

*   It shows constant error as shown in conventional feedforward architecture while presented entire string at a time as input.

*   Just like other feedforward networks, LSTMs also have “regency” problem.

> Let us consider:  

> `hC[t]`, `hh[t]`: hidden layer vectors.  

> `x[t]`: input vector.  

> `bias[f]`, `bias[i]`, `bias[c]`, `bias[o]`: bias vector.  

> `Wt[f,]`, `Wt[i,]`, `Wt[c,]`, `Wt[o]`: parameter matrices.  

> `σ`, `tanh`: activation functions.

(7.8)![](images/eq7-8.jpg)(7.9)![](images/eq7-9.jpg)(7.10)![](images/eq7-10.jpg)(7.11)![](images/eq7-11.jpg)(7.12)![](images/eq7-12.jpg)(7.13)![](images/eq7-13.jpg)

## 7.3.2.3 Gated Recurrent Units (GRUs)

In RNN, GRUs are gated mechanisms. It has fewer parameters compared to LSTMs with similar architecture with forget gate. GRUs are of two types i) fully gated unit and ii) minimal gated unit. It is introduced mainly to prevent vanishing gradient, issue of standard RNN using update and reset gate.

The fully gated unit (as shown in [Figure 7.7](#c07.xhtml#fig7-7)) has several variations, based on bias combinations and gating done using previous hidden state. The most simplified form of GRU is known as minimal gated unit. Main three types are shown as Type1, Type 2, and Type 3 in [Figures 7.8](#c07.xhtml#fig7-8), [7.9](#c07.xhtml#fig7-9), and [7.10](#c07.xhtml#fig7-10), respectively.

![Figure 7.7 Fully gated version.](images/fig7-7.jpg)

[**Figure 7.7**](#c07.xhtml#rfig7-7) Fully gated version.

> Let us consider:  

> `hh[t]`: hidden layer vectors.  

> `x[t]`: input vector.  

> `z[t]`: update gate vector  

> `r[t]`: reset gate vector  

> `bias[z]`, `bias[r]`, `bias[h]`: bias vector  

> `Wt[z,]`, `Wt[r,]`, `Wt[h,]`: parameter matrices.  

> `σ`, `tanh`: activation functions.  

> If `σ(x)` ϵ \[0, 1\], then alternative activation functions are also possible.  

> The operator ʘ denotes the Hadamard product

(7.14)![](images/eq7-14.jpg)![Figure 7.8 Type 1 GRU.](images/fig7-8.jpg)

[**Figure 7.8**](#c07.xhtml#rfig7-8) Type 1 GRU.

![Figure 7.9 Type 2 GRU.](images/fig7-9.jpg)

[**Figure 7.9**](#c07.xhtml#rfig7-9) Type 2 GRU.

![Figure 7.10 Type 3 GRU.](images/fig7-10.jpg)

[**Figure 7.10**](#c07.xhtml#rfig7-10) Type 3 GRU.

(7.15)![](images/eq7-15.jpg)(7.16)![](images/eq7-16.jpg)

*Type 1:* Each gate only depend on bias and previous hidden state

(7.17)![](images/eq7-17.jpg)(7.18)![](images/eq7-18.jpg)

*Type 2:* Each gate only depend on previous hidden state without bias

(7.19)![](images/eq7-19.jpg)(7.20)![](images/eq7-20.jpg)

*Type 3:* Each gate only depend on bias and not previous hidden state

(7.21)![](images/eq7-21.jpg)(7.22)![](images/eq7-22.jpg)

*Minimal Gated Unit:*

In case of minimal gated unit, the update vector (`z[t]`) and reset vector (`r[t]`) is merged into a forget gate (`f[t]`).

(7.23)![](images/eq7-23.jpg)(7.24)![](images/eq7-24.jpg)

> where  

> `x[t]`: input vector  

> `hh[t]`: output vector  

> `f[t]`: forget vector  

> `Wt[f]`, `Wt[h]`, and `bias[f]`, `bias[h]`: parameter matrices and bias vectors

## 7.3.3 Merits and Demerits

### 7.3.3.1 Merits

1.  A RNN recollects all information at time intervals as LSTMs can recollect anterior inputs in time series presages.

2.  RNN can be combined with convolutional layers to stretch the pixel neighborhood for effective performance.

### 7.3.3.2 Demerits

1.  It has vanishing and exploding gradients.

2.  It is difficult to training a RNN.

3.  It is unable to execute lengthy sequences with tanh and ReLu activation functions.

## 7.3.4 Applications

RNNs are utilized in many applications ranging from seizure detection to cryptography and from verbalization apperception to stock market prognostication. Very importantly, its appreciable applications are unsegmented, connected, often temporal in nature and appropriate to physiological signals as they are recorded as one dimensional (1D) samples over time. Ergo, many research works have benefitted with the application of RNN features to physiological data such as

*   Physiological data additionally kenned as biomedical signals categorically bio-electrical signal categorizes and characterizes as follows: 

    *   Electroencephalogram (EEG): electrical signals engendered due to electrical activity in human encephalon.

    *   Electrooculogram (EOG): signals engendered due to the vicissitude of potential of the cornea-retina region that subsists between the front side and back ends of human ocular perceiver.

    *   Electrocardiogram (ECG): signals that are engendered from activity of human heart which are consequence of cardiac muscle depolarization and re-polarization during heartbeat.

    *   Electromyogram (EMG): electrical signals engendered by skeletal muscles.

*   Last 2 years, i.e., 2018 and 2019, it has been visually perceived a plethora of research development transpired on EEG and with utilizing EEG among the four other modalities or cumulation of two or more modalities. EEGs are majorly utilized because EEG predicated signal acquisition is more frugal and does not require any special equipment, the acquisition system is portable which makes it feasible for applications such as encephalon-computer interface, it has high temporal resolution with sampling rates between 250 and 2,000 Hz.

*   Recent past, several experimental and theoretical work on statistical relegation techniques had been published. Many of the literatures prove that the DL models outperform compared to traditional models. In the following section, EEG modality utilizing RNN has been discussed. In the next section the prominent applications of EEG research such as Encephalon decoding and anomaly detection have been elaborated.

# 7.4 Denoising Autoencoder

Autoencoders are the neuron models used to cull and extract the data features. It has more nodes in the obnubilated layer than the inputs. It is jeopardizing to learn the soi-disant “Identity Function”, withal called “Null Function”, denoting that the output and input is equal, in order to model the Autoencoder network nugatory.

Denoising autoencoder (DAE) handles the quandary by corrupting the data intentionally by arbitrarily zeroing half of its own input values. Researches suggest to use 30% corrupted input as it depends on the magnitude of data and number of input nodes of the model. The loss function is calculated as the error magnitude between the pristine input and the obtained output which helps to learn the extraction or elimination features.
