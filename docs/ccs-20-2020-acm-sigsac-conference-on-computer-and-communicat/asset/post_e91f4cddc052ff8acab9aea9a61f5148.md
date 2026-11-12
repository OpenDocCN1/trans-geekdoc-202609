
represent the malicious behavior of concealing app activities, such as removing traces of suspicious actions and hiding the presence of the app. SHB detection approach [24] traces stealthy actions by performing control flow and static taint analyses; this work also inspires VAHunt's detection on malicious-plugin loading strategies.

## 3 NEW REPACKAGED ANDROID MALWARE IN APP-VIRTUALIZATION'S CLOTHING

In this section, we present our in-depth study on tracking the development of app-virtualization-based malware over three years. Our findings unveil the characteristics of this new generation of malware and highlight a pressing need for the security community to design specific countermeasures.

The limitations of the app-virtualization technique, such as lacking permission separation and data isolation, have little impact on malware development. On the contrary, cybercriminals skim the cream off app-virtualization as a new malware repackaging way. As a result, malware development and distribution turn out to be much easier and stealthier than ever before. In particular, app-virtualization repackaged malware reveals the following advantages:

- (1) Bypass anti-virus detection. App-virtualization enables malicious functions (as different plugins) are decoupled from the host app, and each plugin is either stored under “Assets” directory in an encrypted form or is dynamically downloaded. As long as the host app does not involve any malicious actions, antivirus scanners are difficult to detect it.
- (2) Low development cost. Traditional repackaging still requires quite a heavy reverse engineering effort: adversaries have to modify the original app’s code, change the package name using Apktool or DEXlib, and repackage the app into a new APK file. By contrast, app-virtualization makes repackage much easier: original APK can be directly loaded as a plugin without any modifications.
- (3) Flexible to update modules. With app-virtualization, malware developers are free to update their modules without reinstalling apps. In addition to updating malicious code, many malware samples begin to add more profitable functions, such as advertisement promotion and pornography propagation.
- (4) Easy to spread. As mobile developers and users have a huge demand for app-virtualization applications, this fact provides a natural coverage to spread app-virtualization-based malware. For example, they can disguise themselves as a dual-instance app; after a user installs it, the host app dynamically downloads malicious plugins and executes them without the user’s awareness.

Since the emergence of app-virtualization repackaged malware in 2016, we are tracking their evolution all the time. Figure 4(a) shows the total number of app-virtualization-based benign apps and malware samples collected by Antiy AVL in each quarter over three years (2016 - 2019). Antiy AVL’s threat detection engine provides rich metadata to identify benign apps, malicious repackaged apps, and app-virtualization-based apps. As DroidPlugin and VirtualApp are two leading app-virtualization engines, we add additional static features to recognize them. For other app-virtualization apps that do not match such fingerprint features, we put them into the “custom-made” category.

![](img/e3eb3c6e62eebb62c8dd83ec4ab9835d_4_0.png)

(a) The number of app-virtualization-based apps and engines.

![](img/e3eb3c6e62eebb62c8dd83ec4ab9835d_4_1.png)

(b) The number of new malware samples in each quarter.

Figure 4: The statistics of app-virtualization-based apps.

The two most popular app-virtualization engines, VirtualApp and DroidPlugin, occupy the portion of 92.4% because of their open source. The rest of the apps have custom-made virtualization engines. The core principle of these custom-made engines is similar to VirtualApp/DroidPlugin, but they have different implementation details, such as using AIDL or Content Provider to implement IPC. Custom-made category has 10,621 apps, including six different app-virtualization frameworks. For example, the underlying virtualization engine of Parallel Space is called MultiDroid, and we treat it as a custom-made engine.

Interestingly, the number of malware armored by VirtualApp is about three times larger than that of VirtualApp-based benign apps. In addition, we also investigate the activity level of repackaged malware from September 2016 to December 2019. Figure 4(b) shows the number of new malware samples that have different hash values quarterly. Since 2016, the increment of traditional repackaged malware slows down, while app-virtualization-based malware exhibits a fast growth from 2017 Q3. Especially, we observe many new malware variants have switched from the previous repackaging style to app-virtualization. The growing gap shown in Figure 4(b) indicates that app-virtualization is very likely to dominate the next generation of Android malware repackaging ways.

We elaborate some detailed characteristics of app-virtualization-repackaged malware and present Triada as typical app-virtualization-based malware in Appendix.

## 4 VAHUNT OVERVIEW

Our in-depth study presented in §2 and §3 results in two key observations. First, the proxy layer between plugin apps and the Android framework is the core of app-virtualization mechanism, and the proxy layer's intent encapsulation behavior (as shown in Figure 3) reveals the feature of finite state transitions. Second, to conceal malicious activities, malware apps typically load plugins stealthily without any user interactions. These insights motivate us to capture a prominent malware feature: the way that the virtualization engine loads plugins. This detection feature is effective even if the plugin's APK file is not statically visible.

We develop a two-layer detection approach, called VAHunt. First, we design a stateful detection model to identify the existence of an app-virtualization engine (i.e., proxy layer) in an APK file. Second, we perform data flow analysis to extract self-hiding loading strategies to differentiate between malicious and benign app-virtualization-based apps. Figure 5 presents the workflow of VAHunt. After extracting the necessary information from bytecode and manifest, VAHunt identifies the intent wrapping behavior and searches stub components to detect an app-virtualization engine. After that, VAHunt traces file objects and path APIs to find the features of the stealthy plugin installation. We discuss the details of VAHunt in the following two sections.

## 5 APP-VIRTUALIZATION ENGINE DETECTION

Activity Manager Service (AMS) manages component schedules in each application. If an app starts an Activity or a Service, it first reports to AMS, and AMS will decide whether to start the Activity or the Service. Since the app and AMS are running in different processes, their Inter-Process Communication relies on Intent [39]. A technical challenge of app-virtualization is to maintain the lifecycle of plugin app components, as all plugins are not installed on the Android system but instead running in a virtual environment. Figure 3 shows how the proxy layer overcomes this obstacle: it wraps the plugin intent with the host app’s predefined stub component to deceive AMS into creating a new activity; then it hooks Android system service APIs to unwrap the plugin intent from the stub component and launches the plugin’s component finally.

In spite of different kinds of app-virtualization engines are currently in use, such as VirtualApp, DroidPlugin, and custom engines, wrapping the plugin app’s Intent with the predefined stub component, as shown in Figure 3, is universal [18]. VAHunt detects this inner mechanism as the presence of an app-virtualization engine.

### 5.1 Preprocessing

Given an APK file, we first extract the necessary information for our follow-on analyses. We use the tool AAPT [40] to extract Manifest and obtain the component information from an APK file. We get Smali code from a DEX file by using the tool dexdump [41]. Since the number of methods in a DEX file cannot exceed 65536 [11], some apps are split into multiple DEX files. So we merge the Smali code of all DEX files into one file for the convenience of follow-on analyses. Besides, we use FlowDroid [25] to build control flow graphs for each APK file.

### 5.2 Intent State Machine

We view the plugin intent wrapping behavior, which involves the data transmission via intents, as a finite state machine (FSM) model. The FSM states represent the statuses of intents, and the state transitions are caused by related APIs (e.g., "setClassName" and "setType"). We check whether the intent state machines extracted from each app match with the reference FSM pattern.

```
private Intent startActivityProcess(Intent targetIntent) {
    intent = new Intent(targetIntent);
    Intent stubIntent = new Intent();
    stubIntent.setClassName(PackageName, StubActivity);
    ComponentName component = intent.getComponent();
    stubIntent.setType(component);
    startActivity(stubIntent);
}
```

Listing 1: JAVA code of wrapping the plugin’s Intent.

```
<activity
    android:name="com.lody.virtual.StubActivity$C0"
    android:configChanges="mcc|locale|touchscreen|..."
    android:process=":p6"
    android:taskAffinity="com.lody.virtual.vt"
    android:theme="@style/VATheme"
/>
```

Listing 2: The predefined stub Activity in the manifest file.

#### 5.2.1 Intent Operations Extraction.

To generate Intent state machines, we need to extract all intent objects and operations. We analyze the Smali code of Android apps to locate the objects with the “android/content/Intent” type and extract all APIs operated on these intents. Specifically, the operations of intent include the creation, attribute setting, and transmission. After an intent is created by “new-instance”, we can find operations on the intent object, such as adding flags or setting actions (e.g., “addFlags” and “addAction”). We also record components and other intents related with the intent object. For instance, “setComponent” operation explicitly sets a component name to handle an intent. If the component of an intent is set to a component name coming from another intent, these two intents have a correlation relationship.

#### 5.2.2 Wrapping the Plugin’s Intent.

As shown in Figure 3, the host app transmits the modified intent to AMS by wrapping the Target-Activity intent in the predefined StubActivity intent. When AMS creates the Activity, the host app recovers the real intent for the plugin. Listing 1 shows the core code of wrapping an intent. The intent in Line 3 is the targetIntent from the parameter of startActivityProcess() by creating a new instance. The stubIntent is newly created at Line 4, and it has a new Class of StubActivity at Line 5. Line 6 & 7 achieve the goal of wrapping the targetIntent: the targetIntent’s component is added to the type of the stubIntent. After that, the encapsulated stubIntent is passed to AMS by “startActivity”. In this way, AMS thinks this request of starting an Activity is from the host app instead.

#### 5.2.3 Intent State Transition.

By default, an intent is created with an initial state. Its state changes when adding attributes, such as “setClass” and “addFlags”. For the transitions related to wrapping an Intent, states of the targetIntent and stubIntent transform with their instances, class names, component names, and type attributes changing. The steps to generate an intent finite state machine (FSM)
