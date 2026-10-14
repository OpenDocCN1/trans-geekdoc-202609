
- onStop(): When an activity is no longer active and visible to the user and perhaps will not be requested for a while, this process is called (Marques, 2010).
- onRestart(): This indicates the activity is being displayed when the activity that was stopped was requested by the user (Marques, 2010).
- onSaveInstanceState(Bundle): When the process of reinitialization happens from a state earlier saved by the onSaveInstanceState(), this process is called (Marques, 2010).

### 30.5.1.1 Android: Application Architecture

Android’s architecture allows developers to determine their own concepts of components. It enables them to reuse it and therefore, they are able to share the activities, intents, services, and data with other relevant applications. Several things are defined in the Android SDK. It is necessary that the programmer or developer is familiar with developing on Android OS. Crucial segments are: activities, intents, services and content providers.

**Activities:** An activity describes user interface screen. The application determines if there can be one or more activities defined in the program. Each activity is in charge for saving its own states; therefore, it can be restored later as part of the application life cycle (Marques, 2010).

**Intents:** This mechanism is used for calling a specific action. In Android’s Intent, all activities go through. Intents give authorization for replacing or reusing components (Mohamed & Yampolskiy, 2011).

**Services:** This runs in the background. User’s interaction is not needed (Mohamed & Yampolskiy, 2011).

**Content Providers:** It is a set of data. Data are wrapped up in a custom API to read and write it. For sharing data among applications, using content provider is the best solution (Mohamed & Yampolskiy, 2011). All programs are written in Java. Dalvik virtual machine is used for execution of Android’s programs.

### 30.5.1.2 The Dalvik Virtual Machine

The Dalvik Virtual Machine represents important segments of Android. Usage of DVM is more requested than Java Virtual Machine (JVM). It runs on the Linux kernel. It is used for low-level functionality. The Android system includes both hardware and software. It is managed by using Dalvik as middle tier.

### 30.5.1.3 Biometric System and Application

After testing PCA on MATLAB for face recognition is done (Clarke & Furnell, 2007), the next phase is to develop the application on Droid emulator. A Droid emulator was set up for Android Samsung Galaxy S. The images of faces were captured. A function called fakeProcessing was created to simulate camera activity. The images of faces were saved on the computer’s desktop. This simulates capturing an image by the user’s mobile phone camera.

### 30.5.1.4 Running and Testing Application

Firstly, a Tomcat server is started. Upon initialization of the Tomcat server, MATLAB runs. On the emulator, we have added an image to simulate the process of capturing a face image from a mobile phone, as shown in Figure 30.2. When the image is stored on the SD card, the emulator is started, as shown in Figure 30.3. Then, we have started our application called DroidAuth. When running, the application is shown in Figure 30.2. The following process is the authentication process. When the authentication process is started, the image is sent to the server. On the server side is MATLAB. The authentication process is working on PCA (Jain & Li, 2011; Kremić, 2011).

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_931_0.png)

Figure 30.2 Emulator of Android OS.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_931_1.png)

Figure 30.3 SD card file system.

### 30.5.1.5 Mobile Security

Mobile security highly depends on data storage and authentication. Therefore, in this paper we are as well introducing a model for authentication to secure it with the visual identity. The security of mobile devices also depends on the mobile operating system such as Android, iPhone, BlackBerry, Symbian, JME or WinMobile. There are different security levels and some of those are:

- **Normal:** The consequences on applications from a normal threat are minor. Usually, it can grant some rights to the application.
- **Dangerous:** The grants related to the settings and to SEND SMS are considered very dangerous. Android has the possibility to let the user know when these permissions are installed.
- **Signature:** The signature is granted only on the application level. And this can hide and keep public interface anonymous.
- **Signature or System:** This varies with signature, except it allows system images to grant the access.

Nascent mobile application security brings with it new issues, which are different from the desktop security application. When speaking about Android, we can say that Android is a platform which is based on the Linux kernel, which provides a security mode.

## 30.6 Architecture

The model consists of a mobile cellular phone side and a server side. Comparing it to the initial research (Kremić, 2011; Kremić & Subasi, 2011; Kremić et al., 2012), changes were made toward the application improvements. Here, on the cellular side, the *DroidAuth* application, developed in Java, is running. In between is HTTP, which enables communication between the server and cellular side. On the server side, MATLAB is running. The purpose of MATLAB is to simulate the authentication engine running. The server receives the video that is captured via the cellular-mobile side and sent to the server. When it is sent to the server, faces from the video are extracted. After the faces are extracted, PCA is running on the server side. The PCA is used for recognition. After PCA, the application determines when authentication should happen and under which state of security.

There is a user database consisting of biometric profiles. Principal component analysis feature vectors are sent to the biometric database, then go through the process of matching. If they are matched, the application accepts and the user is being authorized, and if not it is sent back to the beginning of the process. Both of these are visually described in Figure 30.4, which shows the process flow.

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_933_0.png)

Figure 30.4 System architecture.

**Principal Component Analysis:** The aim of the principal component analysis is to help in face recognition. In this application we have used the PCA method for recognition. The faces were captured via the mobile camera. After capturing, the process of face extraction was done. The aim of PCA is to help automate the process of face recognition and attempt to find the identity of certain facial images according to those in the biometric database (Figure 30.5).

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_933_1.png)

Figure 30.5 Database example.

## 30.7 Testing and Results

The results presented here are from just the small data set of 40 persons from the IBU Biometric dataset. Each person has 20 different face images. For face recognition, we have performed PCA on the DroidAuth application. The accuracy we have calculated is shown as described in Formula 30.1. For the mobile phone we have used the Samsung Galaxy S. The overall accuracy achieved here is 92.64%. We have determined the Euclidean distance between test images and training images. The threshold for the distance is 10e+16. In Table 30.1, results are shown where males were recognized with 100% accuracy. The problems come with females, especially those who color their hair. We can see that females with darker hair achieve higher accuracy than females with light/blond hair.

Accuracy = Matched Faces / Total Number of Face Images in Database × 100%   (30.1)

In Figure 30.6 is shown the graphical representation of results plotted from Tables 30.2 through 30.4.

**Table 30.1** Application of Biometric System

| Areas | Application |
|---|---|
| Information Security | Access security (OS, database) |
| Access Management | Secure access authentication (restricted access) |
| Biometrics | Person identification (national ID) |
| Law Enforcement | Video surveillance |
| Personal Security | Home video surveillance system |
| Entertainment – Leisure | Video camera application |

![](img/f4c3bcc9f5332d57a8ec85a75075f8da_934_0.png)

Figure 30.6 Graphical representation of results.
