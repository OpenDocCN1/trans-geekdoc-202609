
# 226 Big data recommender systems, volume 1

discovery. We can arrange them into two sorts of the identification system: static examination and dynamic analysis. Both static and dynamic investigations utilize their qualities and shortcomings. Static examination uses the show of the Android applications and recovers the interface (programming interface) calls to distinguish malware. Some methodologies, e.g. RiskRanker [1], DDroid[2], and DREBIN [3], figure out the Android Bundle (APK) records to acquire data from the dismantled smali code arrangement and the decompiled Java code. Some methodologies use the consent of the Android applications or signature, e.g. Kirin [4]. The benefits of static examination are little overhead, effective, and versatile, and expectation may be on physically created detection examples or learning-based identification. Dynamic examination concentrates on the runtime practices and the framework measurements of the applications. The greater part of the dynamic investigation approaches excluding emulators to get the runtime data. Anomaly [5] utilizes the data of the framework measurements to do malware location, TaintDroid [6] utilizes the data of the framework calls, and other systems to get document read/compose practices. DroidScope [7] reveals the semantic of the working framework and Java to break down the key practices of the malware families. Conduct hands [8] uses to accumulate data from whatever PDAs as could be expected under the circumstances, and change them to a cloud server for malware order with bunching calculations. A technique called STREAM [9] has a comparable way to deal with Android, and this empowers substantial scale approval of portable malware learning classifiers. Contrasting with static investigation strategies, the previously mentioned dynamic investigation techniques utilize the utilization of emulators, which requires the copying procedure to mimic GUI-based PDA applications. Dynamic investigation might have the capacity to assemble more data than static examination; consequently, consolidating dynamic/static examination techniques would give better outcomes. By using the unneeded advancement of malware, it ends notice increasingly hard for static strategies to recognize malware from APKs. Some malware are capable of performing frequent behavioral changes [10]. Another basic issue is the Java reflection strategy, which is presently utilized as a part of JSON and XML deserialization, that may managing programming interfaces whose names change between variants. It is a capable strategy; however, likewise turns into a solid weapon for a malware to conceal its vindictive conduct. All the over confinements make static examination hard to completely identify all the malware. Today, none of the previously mentioned static/dynamic investigation techniques can be viewed as the champ, since none of them can get all malware. It is conceivable to manufacture a half breed location by joining a few techniques.

The greater part of the current malware depends on the establishment of the client who represents the last line of barrier in malware recognition. Another malware discovery technique is required that would concentrate on the data that the client can see preceding the establishment of an application metadata, e.g. maker ID, contact e-mail, contact site, limited time video, number of screenshots, promo writings, late changes, ID, bundle name, establishment measure, adaptation, applic- sort, appraisals tally, and application title inside the stages programming market.

# Recommender system for predicting malicious Android applications 227

Contingent upon the stage, this will incorporate the applications depiction, cons the appraisals, or data about the designer, last time changed, classification, value, portrayal, attentions, rating, and number of downloads. To investigate these pieces of information, it's needed to make utilization of refined learning forms and measurable techniques. An extensive variety of illustrations in line of genuine application metadata separated from the Android Market demonstrate the potential outcomes of the new strategy. It ought to be a basic piece of a complete malware investigation/discovery chain that incorporates other understood strategies, e.g. arrange activity examination, or static or dynamic code assessment. Accordingly, there is a need of a static and dynamic malware examination structures which use the advances of GUI-based testing, enormous information investigation, and machine figuring out to distinguish vindictive Android applications. The system can be utilized as a part of conjunction with other existing attempts to enhance the location rate of malware.

## 10.1.1 Android operating system architecture

In this segment, we portray the engineering of the Android OS and its applications. Android is being created and kept by Google and by the Open Handset Partnership (OHA). Android OS is put over the Linux partition and it incorporates the middleware, libraries and APIs written in c dialect, and programming running on an application system which incorporates Java-perfect libraries. Android's source code is discharged by Google under open source licenses. Android working framework is a heap of programming parts, which is generally divided into two segments and four fundamental layers as appeared in Figure 10.1. Android OS layers and segments are clarified as follows.

### 10.1.1.1 Applications

Application layer is situated at the highest point of the Android programming stack. Which further involves the preinstalled applications that give a specific Android usage and outside applications created by people (informal) application engineers. Cases of such applications are Browser, Contacts Manager, and E-mail applications. More cases of such applications can be found from numerous official and informal application markets.

### 10.1.1.2 Application framework

The application system is an arrangement of administrations that on the whole shape the environment in which Android applications run and are overseen. Administrations are given to applications as Java classes. Application engineers are permitted to make utilization of these administrations in their applications. Application structure incorporates the accompanying real administrations: Movement Supervisor, Content Suppliers, Asset Director, Notices Administrator, and View Framework.

# Big data recommender systems, volume 1

| Applications | Third Party Apps |
| :--- | :--- |
| Native Android App | |

| Application Framework | | | |
| :--- | :--- | :--- | :--- |
| Activity Manager | Window Manager | Notification Manager | View System |
| Package Manager | Resource Manager | Content Provider | |

| Libraries | | | |
| :--- | :--- | :--- | :--- |
| SQLite | WebKit | OpenGL ES | |
| FreeType | Surface Manager | Media Framework | |
| SSL | SQL | lib | |

| Android Runtime | | | |
| :--- | :--- | :--- | :--- |
| Core Libraries | | | |
| Dalvik Virtual Machine | | | |

| Linux Kernel | | | |
| :--- | :--- | :--- | :--- |
| Display Driver | WiFi Driver | Audio Drivers | Binder(IPC) Drivers |
| Power Management | Process Management | Memory Management | |

> Figure 10.1 Android operating system architecture [11]
