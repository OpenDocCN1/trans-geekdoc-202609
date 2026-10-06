
# IoT and Blockchain

```
Anaconda Prompt
C:\Users\frank\Documents\project\Uharath\image-classification-tensorflow-master>
Volume in drive C is not locked.
Please run CHDSK C: first.

Directory C:\Users\frank\Documents\project\Uharath\image-classification-tensorflow-master>
07-02-2023  10:59 AM    <DIR>          .
07-02-2023  10:59 AM    <DIR>          1,156 classify.py
07-02-2023  10:59 AM                502 dataset
07-02-2023  10:59 AM            5,902 Android.jpg
07-02-2023  11:07 AM           20,230 Healthy
07-02-2023  14:16 PM           11,758 Images.jpg
07-02-2023  22:14 PM                Inception
07-01-2023  11:44 PM                 model
07-01-2023  16:17 PM             2,516 ResNet50_md
07-01-2023  16:17 PM            30,800 test_image.jpg
07-03-2023  23:59 PM          14,651 leaf_model-4db-800.step
07-01-2023  16:01 PM            44,086 train.py
07-02-2023  10:59 AM    <DIR>          9
07-02-2023  10:59 AM           545,325 bytes
07-02-2023  10:59 AM           724,768 virus.jpg

C:\Users\frank\Documents\project\Uharath\image-classification-tensorflow-master>python classify.py virus.jpg
WARNING: function call from classify.py: FileList_ (from tensorflow.python.file) is deprecated and will be removed in a future version.
Loading model...
Loading image:
Detected tomato_virus leaf_curv (score = 0.9674)
Result: Healthy (0.0326)
```

Figure 4.9 Average values for tomato curl virus.

caused by yellow curl virus and the values of healthy plant and infected plant values are displayed.
The system reduces human intervention in farming and becomes critical in creating more productive procedures for farming-related exercises. In the proposed work, median filtering is favored over manual channel, smoothing filter, and oscillation threshold channel because single outliers are separated in it. For identification of the infected leaves, CNN approach gradient descendant calculation is utilized. This gives more precise outcomes for a particular disease.

## 4.2.2 IMPLEMENTATION OF SMART HOME AUTOMATION USING ARDUINO

Smart home automation helps us to control the room lights, fans, or any electrical equipment at his or her convenience using his or her smartphone using Bluetooth or Internet. Any device can be controlled on fingertips. There are many ways to automate the home. Arduino (Uno, Mega, Pro, Mini) or Raspberry Pi can be used for automation. A simple example of controlling the light is explained in the following section. The components required are Arduino Uno, Relay Module, Bluetooth Module/Wi-Fi module, resistors (1 KΩ and 2.2 KΩ), and jumper wires.
Connect the components as given in the circuit diagram in Figure 4.10.
In order to upload the code, connect the Arduino through the USB port and open the Arduino IDE. Type the following program and upload the code to the Arduino Uno.

## Blockchain Technology

![](img/5197498995d15589ead293656bce20db_70_0.png)

FIGURE 4.10 Circuit diagram – Automation of light.

```
#define RELAY_ON 0
#define RELAY_OFF 1
#define RELAY_1 4
void setup() {
    // Set pin as output.
    pinMode(RELAY_1, OUTPUT);
    // Initialize relay one as off so that on reset
    would be off by default
    digitalWrite(RELAY_1, RELAY_OFF);
    Serial.begin(9600);
    Serial.print("The Bulb will be on 5 Seconds and Off
    for 5 Seconds");
}
void loop() {
    Serial.print("\n"); //New line
    digitalWrite(RELAY_1, RELAY_ON);
    Serial.println("\n Bulb is now turned ON.");
    delay(5000);
    digitalWrite(RELAY_1, RELAY_OFF);
    Serial.println("\n Bulb is now turned OFF.");
    delay(5000);
}
```

After setting up the hardware and uploading the code, test whether the bulb switches on and off at interval of 5 seconds. If it is working, the same code can be modified to read the input from the Bluetooth module and act according to the input

received. For example, the code can be modified to switch the bulb when the
Arduino receives a value of 1 and switch it off when the
Arduino receives a value of 1 and switch it off when the
Arduino receives a value of 1 and switch it off when the
Arduino receives a value of 1 and switch it off when the
Arduino receives a value of 1 and switch it off when the
Arduino receives a value of 1 and switch it off when the
Arduino receives a value of 1 and switch it off when the
Arduino receives a value of 1 and switch it off when the
Arduino receives a value of 1 and switch it off when the
Arduino receives a value of 1 and switch it off when the... (Note: OCR text appears repetitive/corrupted here based on source provided).

## IoT and Blockchain

### 4.3 ADVANTAGES OF IoT

- **Effective communication**: It is possible to improve communication over a network, thus increasing efficiency.
- **Access information**: Data and information that are far away can easily be viewed in real time.
- **Accuracy**: The larger the data can be processed, the more accurate decisions can be made.
- **Automation**: Automation is a less time-consuming process without the need for human intervention where tasks can be performed at once.

## 4.4 DISADVANTAGES OF IoT

### COMPLEXITY
When the system is complex, there are chances of failure. For example, you and your partner could receive messages that the system is over or both of you could end up the same thing.

### LESSER JOBS
The need for human labor will decrease considerably with tasks being automated, having a direct impact on employment. As we move into the IoT future, the recruitment process of professionals will decrease.

### COMPATIBILITY
No protocol has been developed to tag and track sensors as of now. A standard system such as USB is required, which is not difficult to perform.

### PRIVACY AND SECURITY
Each computer that a person uses is linked via the Internet in today's technological world. It increases the risk of important data leakage. Sharing of information is a major drawback because confidential information may not be secure and can easily be hacked.

- Unauthorized access devices
- Software attacks
- Network breaches
- Encryption attacks

## 4.5 INDUSTRIAL IoT

IoT has different perceptions with the combination of other technologies and applications. In this section, we see a new perception of IoT. Industrial IoT (IIoT) is the application of IoT technology in industrial settings with respect to instrumentation and control of sensors that engage cloud technologies. Currently, industries have started using machine-machine communication (M2M) to accomplish wireless automation and control. But with the materialization of cloud and associated technologies, which may include analytics and machine learning, industries can push off a new automation layer and create new income and business strategies.

### INDUSTRY 4.0
This is a phrase coined in Europe. It means the same as IIoT and refers to the fourth industrial revolution, as depicted in Figure 4-11.

- **Preventive and predictive maintenance**: It is self-explanatory that prevention is better than cure. For instance, the heat of the machine, running time, and amount of fuel needed are all monitored in a smarter way.
