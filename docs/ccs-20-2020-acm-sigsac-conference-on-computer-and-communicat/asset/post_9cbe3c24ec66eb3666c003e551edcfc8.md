

**Table 1: Four loading strategy characteristics to detect app-virtualization-based malware. Characteristics 1 & 2 describe where to load plugin APKs. Characteristics 3 & 4 describe actions that conceal malware behaviors from being noticed by victims.**

| Characteristics | Starting Point | End Point |
|---|---|---|
| 1. Load Plugin from Customized Path | Sensitive Path APIs (see Table 2) | Intent wrapping functions |
| 2. Load Plugin from System Path | getInstalledPackages()<br>Runtime().exec("pm list packages") | onCreateView()/onViewCreated()/inflate()/onCreateViewHolder()/setContentView()<br>OnClick()/setOnItemClickListener() |
| 3. User Consent | installApp()/installPackage() | Launcher in Manifest ("android.intent.category.LAUNCHER")<br>App lifecycle (onCreate(), onStart(), onReceive()) |
| 4. Hide Application | setComponentEnabled(cmp, 2, 1)<br>Window.addFlag(FLAG_NOT_TOUCH_MODAL)<br>Window.setFlag(FLAG_NOT_TOUCH_MODAL)<br>Window.requestFeature(FLAG_NOT_TOUCH_MODAL) | Components of the host app |

**Table 2: Android APIs to obtain the customized file path.**

| Directory | APIs |
|---|---|
| /data/data | getDataDirectory(), getCacheDir(), getFilesDir(), getDir(), openFileOutput(), getFileStreamPath(), getDatabaseDir() |
| /sdcard/ | getExternalStorageDirectory(), getObbDir(), getExternalStoragePublicDirectory(), getExternalCacheDir(), getExternalFilesDir() |
| SQLiteDatabase | openOrCreateDatabase(), openDatabase(), openOrCreateDatabase() |
| SharedPreferences | getSharedPreferences(), getPreferences(), getDefaultSharedPreferences() |
| Others | getAssets(), getCanonicalPath(), getPath(), getAbsolutePath() |

setComponentEnabledSetting() to disable icon during running [24]. To hide Activities, malware has two options:
- malware runs as a Service in the background;
- malware makes the Activity's main layout transparent and removes the action bar and window title by using the "FLAG_NOT_TOUCH_MODAL" flag.

The host app hides its own components to be stealthier in the same way. We perform data flow analysis backwards to investigate the parameters of these special APIs and ensure that the host app configures the components involved in the APIs to hide plugins and itself. For example, as shown in the last row of Table 1, when the three parameters of “setComponentEnabledSetting” are set as startup component of host app, 2, and 1, the outcome of this API is to hide app icons.

packages information in the list by setAdapter(), we search the related XML file to find the real items of GUI. If the items include any words or images, that means the behavior of obtaining the plugin packages is visible to users.

### 6.1.3 User Consent

Typically, benign app-virtualization apps require users to click installation buttons or pop up dialogs to acquire users' consent at the plugin installation time. However, most app-virtualization-based malware samples load their malicious plugins without any user interaction from the very beginning. To detect the non-existence of user clicks, we first locate the plugin installation interface and then trace backward from the interface to the startup of an app. The app startup is usually the component with "android.intent.category.LAUNCHER" label in the manifest file. If we find that the beginning of plugin installation is in the component lifecycles (e.g., onCreate() of Activity), we stop chasing the API call chain. When users agree to load plugins, they often click buttons or items on the screen. So we collect the call chain from the plugin installation and see whether it includes onClick() or onItemClick(). If the call chain reaches the application entrance but showing no user interaction, that means the host app loads the plugin silently. We also deal with thread interruption problem in the call chain analysis in Appendix §B.

### 6.1.4 Hide Application

After installation, benign apps add their icons to the home screen for users' convenience of the next use. However, malware instances tend to hide themselves and run in the background without showing any icon or Activity. As a result, users cannot see any GUI on the screen. Malware either modifies manifest file to remove the app from the default launcher or invokes

### 6.2 Decision Rules

We take stealthy plugin loading and app hiding actions as malicious behaviors because they violate the Google Developer Content Policy [43]. As shown in Figure 7, the malware host app could load plugins from a customized path (1) or load a benign app to attack it from a system path (2). Considering an app may contain an app-virtualization engine but never uses it, features (1) and (2) are used to confirm that the host does indeed load plugins using the app-virtualization engine. Based on that, most malware host apps install their malicious plugins silently without users’ consent (3), leaving no visible footprints in the user interface. We define a decision rule, silentinstall, to detect the malicious loading strategy. silentinstall’s formula is: (1) OR (2) AND (3). As long as an app reveals an app-virtualization engine and silentinstall, VAHunt labels it as the app-virtualization-based malware. In addition, we also interested in malware that takes more stealthy actions by hiding icons or Activities after installation (4) in Figure 7, which we represent as silentinstall+, and its formula is: silentinstall AND (4). In our evaluation, we also measure malware exhibiting silentinstall+ behavior. If an app hides application but does not install plugins stealthily, we report it as a suspicious case.

## 7 EVALUATION

We have presented our preprocessing to an APK file in §5.1. We use AAPT [40] and dexdump [41] to extract the necessary information for VAHunt. The prototype of VAHunt includes two components: an app-virtualization engine detector and a malicious loading strategy detector. The whole chain of VAHunt has 7,052 lines of python code. All of our experiments are performed on a laptop with one Intel Core i9-8950HK processor and 32GB memory, running Windows 10 Pro. Our evaluation aims to answer three research questions:

- **RQ1**: How accurately can VAHunt detect app-virtualization-based apps that are built on various virtualization engines (e.g., VirtualApp, DroidPlugin, and custom-made engines)?
- **RQ2**: How accurately can VAHunt further differentiate between malicious and benign app-virtualization-based apps?
- **RQ3**: How well does VAHunt perform in comparison with existing dynamic and static solutions?

### 7.1 Datasets

Our test cases include three datasets to evaluate VAHunt’s detection accuracy. To the best of our knowledge, our evaluation is the largest evaluation to test app-virtualization-based apps so far.

### Officially Labeled App-Virtualization-Based Samples.

Since October 2019, we have deployed VAHunt into Antiy AVL Mobile Security [26], a leading mobile security company, to evaluate its detection accuracy. At the time of writing, we have tested 139,358 app-virtualization-based samples that are collected by Antiy AVL over three years by dynamic/static approaches and manual reverse engineering. Most benign apps in the ground-truth dataset are from major APP markets, such as Google Play, 1Mobile Market, Tencent App Gem, and Qihoo 360 Mobile Assistant. Many app-virtualization-based malware samples have been removed from Google Play [44–46]. At the very beginning, the app-virtualization-based malware samples were reported by victims because they bypassed malware detection engines. Security analysts manually reverse-engineer these samples to extract both dynamic and static detection features. Given a suspicious sample, AVL’s threat detection engine first uses a machine learning model to match similar syntactic feature vectors. If it does not have similar static features, the AVL engine will run each sample for 5 to 10 minutes to detect malicious or suspicious behaviors, such as plugin process activities and the network traffic. However, 44.4% of app-virtualization-based apps have no local plugins, and 51.8% of plugins have trigger conditions. For unknown malware that does not reveal suspicious behaviors at runtime, security analysts have to manually reverse-engineer the sample. It typically takes an experienced security analyst 25 to 50 minutes to dissect an app-virtualization-based app. The AVL dataset is accurate but at a high cost.

Taking these 139,358 labeled samples as a ground-truth dataset, VAHunt focuses on the inner mechanisms of app-virtualization and offers a viable detection engine prior to run time. According to the underlying virtualization engine, we divide these samples into three categories, VirtualApp [5], DroidPlugin [6], and custom-made engine. We detect both benign and malicious apps in each category, and their specific numbers are shown in Row 2~4 of Table 3. Since VirtualApp and DroidPlugin are open-sourced on GitHub, it is convenient for developers and attackers to reuse their source code with a low cost; some of them even modify the source code to generate custom-made engines. Please note that among the total of 81,225 VirtualApp-based apps, up to 77.2% of them are malware samples, which indicates that VirtualApp has a better acceptance by malware authors. Another interesting observation is that 4,320 samples are packed in total, but 4,276 of them are from benign apps. We attribute the low packing ratio of malware to the fact that the app-virtualization mechanism has already provided a layer of

### Table 3: Accuracy evaluation results of VAHunt’s two-layer detection model. The last column is the only previous work to detect app-virtualization repackaged malware. Column 4~6 show the detection accuracy data.

| Virtualization Engine | Category | Number | VAHunt1¹ | VAHunt2² | Certificate [16] |
|---|---|---|---|---|---|
| VirtualApp | Benign | 18,508 | 100% | 100% | 11.7% |
| | Malware | 62,717 | | 99.3% | 0.3% |
| DroidPlugin | Benign | 44,498 | 100% | 100% | 17.1% |
| | Malware | 3,014 | | 98.7% | 0.5% |
| Custom-made | Benign | 8,261 | 100% | 100% | 13.7% |
| | Malware | 2,360 | | 99.2% | 0.3% |
| Dual-Instance | Benign | 147 | 100% | 100% | 0% |
| No app-virtu. | Benign | 1,638 | 100% | -³ | -³ |
| | Malware | 3,212 | | | | |
| Overall | Benign | 73,052 | 100% | 100% | 14.9% |
| | Malware | 71,303 | | 99.3% | 0.3% |
| Avg. Time | | | 6.9s | 12.1s | 0.6s |

¹ VAHunt1 is the App-virtualization Engine Detector of VAHunt.
² VAHunt2 is the Loading Strategy Detector of VAHunt.
³ VAHunt2 and [16] do not detect the apps without using app-virtualization.

effective protection. For the packed samples, we apply Antiy AVL’s commercial unpacking tool to obtain their original DEX files.

### Dual-instance Apps.

Since dual-instance apps allow users to load arbitrary APKs, they are ideal cases to evaluate app-virtualization environment detection tools, such as Plugin-Killer [14] and DiPrint [17]. These tools only take effect when they are embedded into the plugin’s code. We search related keywords, such as “dual instance” and “multiple accounts”, from Google Play and download 147 dual-instance apps.

### Apps without App-Virtualization.

To test whether VAHunt causes false positives when detecting apps without app-virtualization, we also download 1,638 benign apps from Google Play and collect 3,212 malicious apps in April 2020. Moreover, all of these non-virtualization apps are manually verified by AVL security experts to confirm that they do not contain app-virtualization engines. Since this process is very costly, we only obtain 4,850 non-virtualization apps. Even so, this number is already much larger than the false-positive tested apps in [16], which only evaluated 180 apps.

### 7.2 App-Virtualization Engine Detection

Table 3 shows the overall results of our experiments. We classify the samples by app-virtualization engine types and maliciousness. We calculate the detection accuracy in the following formula [47]:

\( Accuracy = \frac{TP+TN}{TN+TP+FN+FP} \)

TP means true positives, and TN represents true negatives. Column 4~6 of Table 3 show the detection accuracy data. The data in Column 4 indicate that VAHunt’s results on app-virtualization engine detection are perfect in all cases: no false positives and no false negatives. In this step, VAHunt extracts all operations on Intents to generate Intent state machines, and therefore VAHunt’s performance here hinges on the number of available Intents. The running time imposed by App-virtualization Engine Detection is about 6.9s (preprocessing 1.2s, Intent state machine 3.3s, and locate stub component 2.4s) on average.

To get a sense of the complexity of building Intent state machines from an APK file, we investigate the Intent distribution in

