
- Pulse oximeters: It measures oxygen saturation and pulse rate.
- Biometric detectors: To keep the identity protected (e.g., fingerprints, face detection).

### Implantable Gadgets
This fits inside the patient's body. Current gadgets include:

- Swallowable camera capsule visualises the patient's gastrointestinal tract from the inside.
- Embedded cardiac devices gather data and send it over a radio link to a near-universal network [3].

### Ambient Devices
These gadgets assess the patient's surroundings and user activity patterns and transmit caregiver's announcements if abnormal patterns are detected. Detectors in the environment include:

- Detectors that discover the movement of individuals in a room are known as motion detectors.
- Room temperature detectors are used to record the temperature of a room.
- Pressure detectors measure the volume of gas, liquid, and air.
- Door detectors determine the status of the door (open or closed) for Alzheimer's patients or infection control.
- Patients' body movements on beds are detected using vibration detectors.
- Daylight detectors determine natural light and modify the lighting zones in the space automatically [4].

### Stationary Devices
These devices determine the patient's surroundings and user activity patterns and send caregiver's announcements if abnormal patterns are detected. Detectors in the environment include:

- Magnetic resonance imaging (MRI), computed tomography (CT).
- Scanners and X-rays are examples of imaging systems that give visual.
- Representations of the innards of a body for clinical study and medical intervention.
- Instruments used in surgeries or operations are referred to as surgical devices. Attacks on these devices compromise the integrity and confidentiality of data, maybe resulting in grave consequences.

## Internet

Content delivery, content discovery, content routing to the destination, and network addressing are all handled by the internet layer. The following are the media that medical devices use:

### Wired/Wi-Fi
IoT devices link to the gateway and end-user via wired or wireless networks. Due to the need for a dependable power source, a device that employs this mode of communication is constantly stationary. This is applicable for IoMT systems that demand a high level of speed.

### Radio Communication
To connect with user end devices, certain low-power IoT mobile devices use radio communication similar to 3G, 4G, LTE, Bluetooth, and RFID. Bluetooth low energy (BLE) is a vital short-range communication technology used in various wearable medical devices. In a hospital room, a stationary Bluetooth core connects numerous devices across the room, allowing data transmission to and from. Long-distance communication is possible with cellular-based IoT devices (3G/4G/LTE).

### Wireless Networks
Medical Things can also connect using Wireless Networks (WSNs), which use regular Wi-Fi or a low-power wireless personal area network (6LoWPAN) to communicate.

## Middleware

Data delivery, discovery and routing to the destination, and network addressing are all handled by the internet layer.

## Android

This layer connects the user interface with people through IoMT devices in an intermediate layer. Due to the superior scalability and flexibility, application manufacturers have been learning further about hosting applications in cloud computing.

## Marketing

This layer is in charge of handling the business intelligence of the healthcare provider as well as supporting the business process lifecycle, which includes monitoring, managing, and optimizing business processes. It is also in charge of gleaning insights from IoMT data. Attacks on this level have been mentioned previously, but they have a greater impact than others because the data contains sensitive medical information.

## CYBERSECURITY ATTACKS IN EACH LAYER

Understanding the challenges enclosing diverse cyber-attacks and designing defence approaches (i.e., countermeasures) that save the confidentiality, integrity, and accessibility of any digital and information technologies are all part of cybersecurity. The following illustration (Fig. 4), listed out the cyber-attacks in each layer (Table 1).

![](img/12e321fe66dd89993b17a8d73b64bd0c_58_0.png)

Fig. (4). Cybersecurity attacks in each layers of IoMT.

Table 1. Aspects of cyber security and protection mechanisms.

| Aspect | Protection Mechanism | Description |
|---|---|---|
| Privacy | Privacy | Ensures that a shared asset remains unknown to anyone outside of the interacting entities. |
| Privacy | Verification | Authorizations are challenged based on their identification and authorization. |
| Privacy | Flexibility | In the event of a failure, the protection is preserved. |
| Reliability | Reliability | Ensures that all interacting entities are aware when an asset has been modified. |
| Reliability | Suppression | Guarantees that transactions take place according to a set of rules, eliminating the freedom of choice and liability in the event of a disclosure. |
| Reliability | Validation | Guarantees that transactions take place according to a set of rules, barring the freedom of choice and liability in the event of exposure. |

| Aspect | Protection Mechanism | Description |
|---|---|---|
| Accessibility | Connection | In the event of a failure, communication is maintained. |
| Accessibility | Alarm | Informs the user that communication is being or has occurred. |
| Accessibility | Secure | A contract between the asset holder and the interacting entity is also included. It may also include public legal protection and warnings as a precursor to legal action. |
|  |  | **PII: Personal Identifiable Information** |
| Data Collection | Consent | Requires the PII holder’s voluntary, specific, and informed consent to the PII’s processing. Without the holder’s authorization, PII cannot be shared or given to a third party. |
| Data Collection | Opt-in | Before applicable consent, includes a policy or process in which the PII owner explicitly agrees to the PII’s processing. |
| Data Collection | Objectivity | Ensures that PII is only collected, used, or disclosed for the purposes for which it was gathered, using principles such as data minimization and accuracy. |
| Data Access | Accountability | Based on a set of PII, the results in identifying the PII owner, either directly or indirectly. Accountability, de-identification, or anonymity should all be included. |
| Data Access | Notification | Notifies the PII owner that his or her information is being collected. |
| Data Access | Auditability | Provides adequate mechanisms for identifying and controlling PII data access. |
| Data Access | Liability | Supports the GDPR principles of legality, fairness, and openness by assuring that the PII holder can hold the PII processors responsible for adhering to all privacy measures. |
| Data Usage | Retention | As a precautionary approach to reduce the risk of illegal collection, disclosure, or usage, it ensures that PII that is no longer needed is not kept. |
| Data Usage | Disposal | Included are systems for erasing or disposing of PII on-demand, as well as the GDPR’s right to be forgotten. |
| Data Usage | Report | Notifies you that you are having or have had a PII breach. |
| Data Usage | Breach or Incident Response | Manages a data breach involving personally identifiable information (PII). |

Note: Source [5].

## WAYS TO SOLVE IOMT ISSUES

### Inventory of Assets
The first step toward improved security is to create and maintain an inventory of all IoMT. It is frequently unmanaged, as it is not tied to a responsible person who functions as the “owner,” many healthcare organizations fail to identify the devices. As no one is accountable for handling security precautions such as passwords, the inability to link a device and a user creates a security blind spot.

### Policy for Strong Passwords
Default settings and passwords are included with every IoMT device. Threat actors, on the other hand, frequently locate default passwords online. The first step in connecting a new IoMT device to the network should be to set a new, strong password that is specific to the device. Some examples of best practices are as follows:

- Using upper- and lower-case letters in a creative way.
- Including at least one number in the equation.
- Including at least one unique character.
- We should also ensure that the password is not stored in any online password databases. This reduces the chances of malicious actors being able to “guess” the password.

### Multi-Factor Authentication (MFA)
It is a second step in preventing credential theft. MFA requires threat actors to supply additional information verifying that they are who they claim they are, even if they successfully log into the device. To authenticate to a device, network, or application, MFA involves using two or more of the following:

- Something you know, such as a password.
- Something you have, such as a smartphone.
- Something you are, such as a biometric like fingerprint or face recognition.

### Segmentation of the Network
The technique of physically or logically isolating networks containing sensitive information from those not known as network segmentation. This can be accomplished by storing sensitive data in a separate data centre from public internet-facing apps or limiting access to the network containing sensitive data
