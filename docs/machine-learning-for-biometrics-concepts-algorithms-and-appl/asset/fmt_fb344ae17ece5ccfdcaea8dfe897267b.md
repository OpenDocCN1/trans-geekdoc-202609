
The COVID-19 pandemic has affected the health of people worldwide and brought challenges in the field of education. Educational institutions are closed worldwide in order to comply with social distancing norms. Institutions attempted to alleviate this problem by moving their classes online to maintain the continuity of classes and lectures. Many pieces of software for video-conferencing among teachers and students were made available to educational institutions for conducting online classes. While such steps have promoted online learning, classes online come with their own set of problems. This chapter aims to illustrate technological frameworks to solve some key challenges.

A teaching method used by teachers and lecturers in a traditional classroom setup is student feedback to alter teaching strategy. In a physical classroom setting, the teacher can gauge the comprehension of a concept or lack thereof by the students from their responses and facial expressions. These “reactions” from the students provide the teachers with information that they use to change the pace or structure of a lecture to understand the students better. Naturally, this process cannot occur effectively during an online lecture that requires functioning computer hardware and a fast Internet connection. Malfunctioning Webcams and microphones, as well as unreliable access to the Internet, impede this process. It is common for the video feed during online lectures to be pixelated, jittery, or remain turned off due to poor Internet connectivity. Students may refrain from notifying the teacher that they have not understood a concept instead of saying they have. In such a situation, teachers do not get any feedback from the students’ expressions on whether it would be better to explain a concept again or continue the lecture. To tackle this issue, technology to detect facial expressions could provide some basic information about the students’ reactions to aid teachers during online lectures.

Emotion recognition is a technology that can detect the emotions of a person. While the psychological aspects are difficult to understand by technological means, essential emotion recognition can be performed by detecting and classifying facial expressions. Six basic facial expressions are accepted and used in emotion-detection algorithms—Anger, Happiness, Sadness, Surprise, Disgust, and Fear. These expressions have different and distinct characteristics and appearance figures based on which classification of an expression is performed [^(163)](#fn163).

Another issue that crops up during online classes is that of marking the attendance of students. Schools and colleges integrate attendance as a part of education and provide credits based on it. In a physical class, the teacher could mark the students who were in class as present. Students who genuinely suffer from hardware malfunction or unreliable Internet connectivity can also leave their Webcams turned off to at least join the online lecture. The teacher cannot accurately distinguish between these problems to mark some students present and others absent for the online lecture. A solution to this challenge would be to use facial recognition methods to identify the student correctly without relying on the teacher manually.

Facial recognition is a technology that is a biometric mode of authentication of people. This technology has continued to improve exponentially owing to rapid improvements in image-processing algorithms [^(164)](#fn164).

This chapter illustrates effective models for identification using facial recognition technology using the histogram of oriented gradients (`HOG`) as well as a convolutional neural network (`CNN`)-based approach to facial expression-based emotion detection.

The authors propose a framework utilizing `HOG` and `CNN` models to enable a smoother experience in online education, helping teachers and students alike to concentrate on academics rather than solve technical problems during the mass adoption of e-learning facilities.

## 2: Related work

Marking attendance by facial recognition is a tested practice. An apt example would be the work of Budi et al. [^(165)](#fn165).

Allagwail and Elbkosh [^(166)](#fn166).

Several studies, experiments, and algorithms were used to detect people’s emotions from static images, video feeds, a combination of video and audio, and those involving body language. Jaiswal and Nandi [^(167)](#fn167).

Happy et al. [^(168)](#fn168).

More recently, deep learning-based implementations have become popular. Fatima et al. [^(169)](#fn169).

## 3: Proposed work

### 3.1: Facial recognition

Implementing the proposed framework requires using the student’s Webcam to capture the student’s image for attendance registration during the lecture classes. A practical implementation of facial recognition of attendance registration is installing software on the student’s computer to function during an online lecture. This software would be able to check the presence of the student at predefined time intervals. The software does not require that the image of the student’s face be transferred over an Internet connection. For the initial setup, a student must scan his face through the Webcam and reference the software for future referral. For every lecture, the student needs to log in. During the proceedings, the Webcam would take pictures of the student at predefined intervals. The ones who were successfully identified by the algorithm would be marked “present” for the lecture. This would be reflected in the database record for the corresponding student for that particular lecture. Any image-based attendance system could be devised following the basic principles of taking attendance. Our framework automates the process, making it more efficient and less cumbersome due to the nonrequirement of transferring the images over the Internet, simply displaying the results.

After the end of the lecture, the lecturer is required to confirm the final attendance. It required that the student present in front of the screen for most of the duration during the lecture. The teacher can set the time interval for the pictures to be taken and not disclosed to the students. Suppose the number of pictures taken by the Webcam is 10. It is required that the student is detected as present in it for at least 75% of the pictures. If this criterion is met, then the student would be marked as present. Here, in case of occasional false detections, such as detecting false positives (i.e., an error of mistakenly identifying an object as a human face) or detection of false negatives (i.e., incapability to detect human faces). Generally, the impact of false positives is harmless to the student for attendance registration unless a student complains about a misrecognized face or falsely detecting an object as a face. The lecturer is, however, suggested verifying the list of identified faces for every lecture session.

#### 3.1.1: Face acquisition, processing, and recognition

The first step of this pipeline process is to locate all the faces from an image before distinguishing, classifying, and recognizing them. We find the image/video locations, and then, it is passed to the next step of the process. For this process, we are implementing the `HOG`.

The key concept behind the `HOG` algorithm is that computer vision algorithms can easily recognize the appearance of an object, especially the characterization of shape based on the distribution of intensity gradients in an area. It does not require knowledge of corresponding edge or gradient intensity positions [^(170)](#fn170).

To locate faces in the given image, we convert the image to gray scale as color data are unnecessary to locate the faces. [Fig. 1](#B9780323852098000018.xhtml#f0010) demonstrates this step.
