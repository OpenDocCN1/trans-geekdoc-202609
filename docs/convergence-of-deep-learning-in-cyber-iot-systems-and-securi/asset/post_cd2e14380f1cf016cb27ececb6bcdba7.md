
## 288 CONVERGENCE OF DL IN CYBER-IoT SYSTEMS AND SECURITY

The user will be able to make audio or video calls through this application. It also provides few necessary first aid precautions that needs to be taken during unavoidable situations. Continuous supply of Internet connection is required for the application to run smoothly.

## 14.3.2 Lifecraft: An Android-Based Application System for Women Safety

Khandekar et al. [12] have designed a system named “Lifecraft” where user login with their respective registered email id and password. User provide up to three contact details of their choice manually. Each time the user starts the application by turning on the on/off button. The application starts by pressing SOS key or voice command and accordingly alert message is sent to the registered contacts that contains the user's name with their location. The location details of the victim is dynamic and, therefore, will be sent in every 5 minutes to their respective contacts that the updated location of the victim can be tracked. Live streaming is done that provides the current position of the person to the registered contacts and also audio recording facility is there. For the first 5 minutes surrounding of the victim is captured for future use after receiving the SOS command. User can avail safe zone where user can find nearby places through map. Also, the user can use offline feature to send alert messages. In this application if the users get any trouble in the network, then it will lead to a big problem since the message along with the location can only be sent through Internet connection, and if all the Internet accessibility is not possible, it will not provide the location

## 14.3.3 Abhaya: An Android App for the Safety of Women

Yarrabthu et al. [10] developed another android application named “Abhaya” where the application will start working with a single click. Using GPS location can be identified and accordingly send URL to registered contacts list and call the first registered contact for help in emergency situation. One of the significant features of this application is to send alert messages to the registered contact continuously on every 5 minutes interval until the SOS button in the application is pressed. It provides with dynamic location service of the user for which stable Internet connection is required. Any trouble in the network will lead to discontinuation of location service since the only way to give the information to the registered number is through the Internet.

## Table 14.1 Comparison table on the basis of certain parameters.

| Apps name | Requires internet | Alert | Send SMS | Without internet |
|---|---|---|---|---|
| Lifecraft app | Yes | Yes | Yes | Yes but no map |
| ISafe app | Yes | Yes | Yes | No |
| Abhaya app | Yes | No | Yes | No |
| Sakhi—The Saviour app | Yes | Yes | Yes | No |

## 14.3.4 Sakhi—The Saviour: An Android Application to Help Women in Times of Social Insecurity

Through this application, the location of the user should also be precisely known to the person to whom the message is sent [13]. This application includes sending updating location link messages to the emergency contact when the application is opened. GPS technology is used to track the location of the user, and a link is sent to emergency contacts [14]. It provides continuous location tracking for every 30 seconds. It shows the information of nearby police stations in case of greater danger and when the user needs protection. When the panic button is pressed, the camera will turn on and a snapshot is captured which may be useful for further investigation [15]. This app will need continuous access to the Internet for tracking location [15]. If the victim is in danger, it is not possible to touch the panic button to give alert. The problem can be reduced by providing SMS feature without the Internet and making app more comfortable to use.

As a part of literature review [16–19], we have investigated some applications of safety that already exist in the market. The main motive is to observe how these applications work and to see how they are different and how they can be improved [20].

Table 14.1 shows a basic comparison of various applications based on certain parameters that includes requirement of Internet, alert message, and others.

## 14.4 Proposed Methodology

In this section, authors have discussed about the proposed Android-based women safety application and provided a clear view of the design for the safety purpose of women.

## 290 CONVERGENCE OF DL IN Cyber-IoT SYSTEMS AND SECURITY

Subsection 14.4.1 discusses about the motivation and objective of the proposed system. Subsection 14.4.2 provides a detailed view of the proposed system. Subsection 14.4.3 focuses on the System flowchart. Subsection 14.4.4 thoroughly explains the use-case models. Subsection 14.4.5 discusses about the novelty of the work. Subsection 14.4.6 compares the proposed system with the existing systems.

### 14.4.1 Motivation and Objective

Women safety has a huge concern in today's society. 10% of all the crimes in India are those of women abuse. According to a report, every 20 minutes, a woman is raped in India [21]. In this era of technology, almost every person has at least one smartphone.

Most of the women carry their Smartphones with them, so it is important to have one safety application installed in their Smartphones [22–24]. Our team members are going to develop one mobile application. Our main intention is to provide safety in the simplest way possible. Our motivation is to contribute something good for women. There will be some features in our application, like offline mode, gesture control, location tracking, messaging, etc., which is useful for women safety [25–28].

### 14.4.2 Proposed System

In this paper, authors have designed a system different from the existing applications that have been designed till date. The following steps are performed using the proposed system: (i) The application named 'Patron for women' is downloaded in Android phone. (ii) In the welcome screen, user's email id needs to be confirmed after the registration opens. (iii) The registration screen gives two conditions, i.e., whether the user is registered or not. If registered, process will be filled if and not, the application exits and revisits the welcome screen. (iv) A warning/attention command appears for the permission to access Internet connection and current location of the device. (iv) A dashboard will open where operator's current location, add emergency contact number and emergency button will be displayed on the application screen. In case of any situation, the user can activate the system by touching the emergency button or by operating the gesture control according to the operator's requirement. The application sends notification to all the emergency contact list via SMS

## PATRON FOR WOMEN: AN APPLICATION FOR WOMENS SAFETY 291

or E-Mail. The distance between both the operator and guardian are displayed on the guardian's side of the map in Km/m and operator will be helped as early as possible. Our application will also work in offline mode. Due to some reasons if there is any network glitch then the notification will be sent to the caregivers with the map link. As the Internet is not working at that moment, it will send the emergency contact person the previous location whenever the Internet was working previously.

### 14.4.3 System Flowchart

The application can be activated in two ways: (i) Through the emergency button or SOS button in app. (ii) Through gesture on the screen of phone. When the emergency button or SOS button is pressed, the system checks whether the GPS is or not accordingly the app will switch on the location service if it is off. After the activation of the emergency button or SOS button, the app will send an alert message with the location details of the victim to all the registered contacts. As a result, the victim will get help from the volunteers. The system flowchart of the model has been shown in Figure 14.1.

### 14.4.4 Use-Case Model

Figure 14.2 shows outline of the System Models. It is known as context diagrams, are the most basic data flow diagrams. It provides a broad view of the system with little details. Here it shows how any user authenticate themselves and send the emergency alert to her close one.

Figure 14.3 shows the separation of all external modules, relationship between those and the application. In level 1 data flow diagram, the single process node broken down into subprocesses. The above figure shows the separation of all external modules, relationship between those modules and the application where it shows how all the details like registration, login, contact details, message details, location details go and into the database which can help police to find the victim very easily.

Figure 14.4 differentiates the modules frontend and backend. simply break processes into more detailed subprocesses. It is also an illustration of our application where it shows the main feature of our app that is the offline mode, which can help to send the alert message without Internet if she faces any network issues during her emergency time.
