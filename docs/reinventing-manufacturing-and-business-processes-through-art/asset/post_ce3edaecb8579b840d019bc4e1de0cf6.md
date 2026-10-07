
# Rise of AI in Modern Healthcare Sector

Brain-computer interface (BCI) is a system that consists of hardware and software communications system. BCI is authorized to control external devices via cerebral activities.

Here, we review the state of the art of BCI systems, consisting of the following steps, which are also shown in Figure 3.4.

- Signal acquisition: collecting brain signals
- Signal enhancement: improving the signal strength
- Feature extraction: selecting appropriate signal patterns
- Classification: differentiating signals into classes based on patterns
- Control interface: triggering the external device based on class of signal generated

First, the signal acquisition step is implemented using neuro image imaging modalities, each observing a dissimilar functional brain activity as metabolic, magnetic and electrical activities. Second, sensing brain activity from different electrophysiological control signals that regulate users' intentions. The third step is to deal with improving the performance of used signal in enhancement of the artifacts in the control signals. Fourth, the review studies some intelligent and mathematical algorithms which are used to translate the information in control signals into commands into other devices. The goal of BCI systems is to deliver communications and access capabilities to severely disabled patients. For patients who are suffering from neurological neuromuscular disorders or are even totally paralyzed, BCI system provide them with access to and control of devices via brain activities. BCI systems are also helpful for brain stroke, amyotrophic lateral sclerosis or spinal cord injury patients.

The human brain comprises millions of neurons and an interconnected network of neurons. Brain-computer interface (BCI) uses mind wave sensors and neuron feedback. Thoughts and emotional states are represented by the interaction between these neurons. A unique electrical signal is generated based on muscle contraction. The state of human thoughts directly reflects different electrical waves. The control commands from brain are used to control external digital devices.

![](img/b43ebe8eccbdc43447aca82fb7658570_61_0.png)

FIGURE 3.4 Brain-computer interface (BCI) system.

# 46 Reinventing Processes Through AI

To measure the living brain activity we need to use Electroencephalography (EEG) that provides measurement of electrical brain activity. Translation of different received brain patterns are used in BCI for uninterrupted communication between an external device and the living brain. To control the external device, EEG signals are needed. In this system, simple unipolar electrodes are used to record EEG signals from the patient's head using a headband with EEG electrodes and reference nodes. We have the signal attention and meditation level values. In addition to the raw dataset, we eye-blinking signals collected from EEG headset device are managed and sent through a Bluetooth interface at receive end connected with microcontroller and then electrically interfacing with the wheelchair or home appliances to control them. Conversion of EEG activity cursor movement by a BCI also provides human-computer interfacing Fabiani et al. (2004).

# 3.2.1 REQUIREMENT FOR BCI Systems for PHYSICALLY Disabled Patients

A general BCI framework proposed by Mason and Birch (2003) is a wonderful invention for physically challenged patients. It takes input from the human brain or eye movement, and converts that activity into a signal. Further, the received signals are used in microprocessors to perform activity using wheelchairs or to control home appliances. Figure 3.5 shows the modules used in this system from mounted headset to the appliance.

1. Electroencephalography (EEG) is a method used for measuring the brain wave activity as the brain's electrical signal. EEG is performed by placing electrodes on the patient's scalp. It is used to measure voltage variations within the neurons of the brain. EEG systems used in medical institutions for patient monitoring or research purpose are costly, but the development of cheaper and more consumer-friendly EEG devices for product development has it in the mainstream market like EMOTIVE EPOC and brain sense.
2. Electro-oculography (EOG) is a system for measuring movements of the eye. Ocular region-related movement can detect by EOG system by measuring the electrical changes such as eye movement and blinks.

![](img/b43ebe8eccbdc43447aca82fb7658570_62_0.png)

FIGURE 3.5 BCI data transmission.
Note: EEG = Electroencephalography

# Rise of AI in Modern Healthcare Sector

3. Bluetooth is a wireless communication technology for short distances. In today's world, mobile phones are a necessity of everyone, and they have Bluetooth systems for data sharing. In BCI systems, Bluetooth is placed with EEG electrodes for sending the brain signals from the BCI device to a microcontroller placed on the appliance. Bluetooth devices have different classes; on class, they have coverage limit from 0–100 meters.

4. Microcontrollers are programmed integrated circuits consisting of a memory unit, a processing unit and an input–output unit. They are small embedded computer systems which also provide interfacing with digital and analog sensors.

# 3.2.2 DIFFERENT TYPES OF BRAIN WAVES

In humans, there are five types of brain waves. According to Picot et al. (2012), different brain waves have different frequencies, and the brain emits them in different states described in Table 3.1.

# 3.2.3 BCI-Controlled WHEELCHAIRS

# 3.2.1 Software Requirements

The ThinkGear connector connects a BCI headset with the NeuroView application. NeuroView is a Windows application from neurosis, which is used to get the raw brain wave data, and the intelligent system of NeuroView shows the attention and meditation levels graphically. The software is based on the procedure to provide the control to operate patients' wheelchair that is straightforward and simple within the boundaries of limited actions using NeuroView raw data (Bi et al., 2013).

Bharali et al. (2018) proposed the following modes:

- Standby
- Command
- Running

These operations are sequential and represent the modes of the wheelchair.

### TABLE 3.1 Different Types of Brain Waves

| Name of Wave | State of Mind | Frequency |
| :--- | :--- | :--- |
| Delta wave | Deep sleep | <4 Hz |
| Theta wave | Deep meditation | 4–8 Hz |
| Alpha wave | Physically relaxed; awake | 9–13 Hz |
| Beta wave | Awake; normal alert | 14–30 Hz |
| Gamma wave | Heightened perception | >30 Hz |

To implement wheelchair operation using the BCI control signal, the control signal is sent using Bluetooth attached to the headset and the signal has to be received in the mobile application; the control signal is passed to another Bluetooth module attached to the wheelchair.

When a strength value received in the wheelchair is above the threshold value, the MindWave application executes in cycling mode through values of forward, reverse, left and right. These directions each have a time span of ten seconds known as command mode, and a two-second intermission between each mode for changing the direction value. We have to provide two consecutive blasts, and whatever direction is shown in the cycle at the moment of the double event will become the chosen direction. To stop force, the cycling time elapsed between two blink events must be less than 400 milliseconds to be recognized by the brain sensor device.

# 3.3.2.2 Hardware Developments

BCI-controlled wheelchair development needs a BCI headset, an Android mobile device and a wheelchair with Arduino microcontroller, Bluetooth and motor driver shown in Figure 3.6. In first module, the BCI headset consists of EEG electrode and a transmitting Bluetooth device; in second module, an Android application and Bluetooth device; and in third module, a wheelchair equipped with a microcontroller, motor driver and Bluetooth. The mobile application connects with headset Bluetooth and wheelchair module simultaneously. First, the headset worn around the user's head will receive the raw brain data and wirelessly transmitting it through its built-in Bluetooth to the Android application. The Android application acts as a conduit between the MindWaveMobile application and the Arduino microcontroller placed in the wheelchair.

Brain wave data from the MindWaveMobile is not directly transmitted to the wheelchair microcontroller; the Android application filters the desired pattern and ensures that only relevant information is sent to the wheelchair microcontroller. The filtration or feature selection process must be performed in the mobile application, and it reduces overhead from headset and microcontroller.
