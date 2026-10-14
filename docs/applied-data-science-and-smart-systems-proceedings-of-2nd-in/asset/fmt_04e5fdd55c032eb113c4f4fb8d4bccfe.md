
The existing review documents focused on the performance of four main aspects, such as signal acquisition, extract features, and detect driver drowsiness itself. These technical details are typically categorized in four primary categories: subjective, behavioral, vehicle-based, and physiological. Mckernon (2009) emphasized ongoing initiatives to manage general fatigue and its harmful effects on driving performance. Charles et al. (2009) and Brown et al. (2009) reviewed vehicle-based drowsiness detection research. [Sigari et al. (2014](#ch19.xhtml#ref19_7)) and [Mittal et al. (2016](#ch19.xhtml#ref19_8)) focused their investigations on driver-behavioral measures. [Sanjaya et al. (2016](#ch19.xhtml#ref19_9)) presented research advancements in physiological signal measurement. [Sahayadhas et al. (2013](#ch19.xhtml#ref19_10)) and [Kang et al. (2013)](#ch19.xhtml#ref19_11) discussed various approaches and provided a comprehensive overview of driver drowsiness detection solutions.

### 2.1 Subjective measures

Subjective indicators of drowsiness encompass signs and sensations that individuals personally discern and report when experiencing sleepiness or fatigue. We can collect subjective measures of driver drowsiness in a variety of ways, such as by conducting surveys, questionnaires, or interviews. These measures are relatively easy and inexpensive to collect, and they can provide valuable insights into how drivers experience fatigue and drowsiness. Nonetheless, they have limitations such as drivers might be influenced by social expectations, resulting in responses that are perceived as acceptable or desirable, rather than being fully accurate. Additionally, subjective measures might not always be dependable, as drivers may struggle to accurately assess their own level of alertness. Notably, several established scales are employed to quantify sleepiness and drowsiness, aiming to capture the subjective perceptions of affected individuals. These indicators are valuable tools in various contexts, including research investigations, clinical assessments, and drowsiness detection systems. The most commonly used scales are discussed in the following sections.

#### 2.1.1 Epworth sleepiness scale (ESS)

Dr. Murray Johns developed ESS. It is commonly used in clinical and research settings to assess daytime sleepiness and other sleep-related issues, including narcolepsy or sleep apnea. It is a self-report questionnaire asking individuals to rate their likelihood of dozing off in eight situations commonly encountered in daily life.

#### 2.1.2 Stanford sleepiness scale (SSS)

William C. Dement and Nathanial Kleitman developed SSS at Stanford University and is widely used in sleep research, clinical sleep medicine, and various other fields to determine the alertness level of an individual at a certain time. This scale asks individuals to rate their current level of sleepiness on a scale from 1 (feeling active) to 7 (feeling sleepy, almost in a trance).

#### 2.1.3 Karolinska sleepiness scale (KSS)

Sleep medicine center at the Karolinska Institute, Sweden developed KSS. It assesses a person’s sleepiness level on a 9-point scale, ranging from 1 (feeling awake and alert) to 7 (feeling sleepy and barely able to stay awake).

Other scales include the Pittsburgh Sleep Quality Index (PSQI), The Groningen Sleep Quality Scale (GSQS), the Visual Analogue Scale (VAS), and the Daytime Sleepiness Scale (DSS). ESS and SSS are the most commonly used subjective scales to measure sleepiness. ESS is quick, easy to administer, reliable, and valid. SSS is not as sensitive to changes in sleepiness as the ESS. KSS is a newer scale still being studied, but it has proved to be a reliable and valid measure of sleepiness. The PSQI is a more comprehensive measure of sleep quality than the other scales but is more time-consuming.

### 2.2 Behavioral measures

Unlike subjective assessments, behavioral measures are objective measures used to assess a person’s behavior, such as personality traits, cognitive abilities, and emotional states.

These non-invasive measures monitor behavioral patterns to check the driver’s fatigue by focusing on three main features: eye movement, head position, and facial expressions. Drowsy displays several characteristic facial signs, including slow eye movements, eye closure, pupil dilation, head nodding, swinging or drooping, and frequent yawning. This video-based approach extracts behavioral features from the camera and computer vision techniques.

#### 2.2.1 Eye movement

This measure focuses on eye monitoring through the slow eye movements (SEM), blinking rate, and eye closure activities, including the PERCLOS metric and the average eye closure speed (AECS) that characterizes eye movement. Unusual blinking and eye closure can be a sign of drowsiness.

[Rahman et al. (2015](#ch19.xhtml#ref19_12)) proposed a method for detecting driver drowsiness based on eye blinking. Firstly, video is captured from the camera and converted to frames. Viola-Jones algorithm is applied to detect the driver’s face, subsequently defining region of interest (ROI) around the facial region. The Viola-Jones cascade classifier technique is used on the ROI to detect eyes using Haar-like features. Both eyes are then extracted for further processing. The colored image is converted to gray scale using the Luminosity algorithm. Harris corner detection method detects two upper eye corners and one lower eyelid. The midpoint value between the upper two corner points is calculated (d1). Then, the midpoint from the lower eyelid is calculated using Pythagoras theorem (d2). Finally, the d2 value is used to make the decision. If d2 is zero or d2 approaches zero, the eye-lid is considered closed; otherwise, it deems it open. The duration of a standard blink typically ranges between 0.1 and 0.4 s. An increase in blink rate is indicative of driver drowsiness. To detect drowsiness, a threshold of 2 s is established. The alarm is triggered to alert the driver if this threshold is breached. The proposed algorithm was tested under various lighting conditions and performed poorly in poor lighting conditions. The proposed method has been compared with other methods, including face and eye tracking using neural networks and visual data, computer vision and machine learning (ML) algorithms, and tools that measure EOG. The solution demonstrated a 94% accuracy rate while maintaining a relatively simplified structure compared to alternative methods.

#### 2.2.2 Mouth and Yawning analysis

Yawning, often a result of tiredness or boredom, can signal a potential risk for drivers, suggesting they might doze off while driving. Techniques exist to gauge the extent of mouth widening, serving as a means to detect signs of yawning in drivers.

[Yan et al. (2016](#ch19.xhtml#ref19_13)) proposed an effective method for monitoring driver fatigue using Yawning extraction. To begin, the method uses the support vector machine (SVM) technique to extract the face region from images, reducing associated costs. The method proceeds to locate the mouth: facial edges are detected through an edge detection technique, followed by a vertical projection to determine the right and left boundaries in the lower face area. Then, a horizontal projection helps identify the upper and lower mouth limits, defining the mouth’s localized region. For yawning detection, the system employs circular Hough transform (CHT) on mouth region images to spot wide-open mouths. An alert is generated if a notable number of consecutive frames capture a widely open mouth. The method’s effectiveness is compared with various edge detectors like Sobel, Roberts, Prewitt, and Canny. The experiment utilizes six videos simulating real driving conditions, and the results are depicted in a confusion matrix. The proposed method attains a 98% accuracy rate, surpassing the performance of all other edge detection techniques.

#### 2.2.3 Head position
