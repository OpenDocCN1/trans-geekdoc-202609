represent the malicious behavior of concealing app activities, such as removing traces of suspicious actions and hiding the presence of the app. SHB detection approach [24] traces stealthy actions by performing control flow and static taint analyses; this work also inspires VAHunt's detection on malicious-plugin loading strategies.

# 3 NEW REPACKAGED ANDROID MALWARE IN APP-VIRTUALIZATION'S CLOTHING

In this section, we present our in-depth study on tracking the development of app-virtualization-based malware over three years. Our findings unveil the characteristics of this new generation of malware and highlight a pressing need for the security community to design specific countermeasures.

The limitations of the app-virtualization technique, such as lacking permission separation and data isolation, have little impact on malware development. On the contrary, cybercriminals skim the cream off app-virtualization as a new malware repackaging way. As a result, malware development and distribution turn out to be much easier and stealthier than ever before. In particular, app-virtualization repackaged malware reveals the following advantages:

+   (1) Bypass anti-virus detection. App-virtualization enables malicious functions (as different plugins) are decoupled from the host app, and each plugin is either stored under “Assets” directory in an encrypted form or is dynamically downloaded. As long as the host app does not involve any malicious actions, antivirus scanners are difficult to detect it.

+   (2) Low development cost. Traditional repackaging still requires quite a heavy reverse engineering effort: adversaries have to modify the original app’s code, change the package name using Apktool or DEXlib, and repackage the app into a new APK file. By contrast, app-virtualization makes repackage much easier: original APK can be directly loaded as a plugin without any modifications.

+   (3) Flexible to update modules. With app-virtualization, malware developers are free to update their modules without reinstalling apps. In addition to updating malicious code, many malware samples begin to add more profitable functions, such as advertisement promotion and pornography propagation.

+   (4) Easy to spread. As mobile developers and users have a huge demand for app-virtualization applications, this fact provides a natural coverage to spread app-virtualization-based malware. For example, they can disguise themselves as a dual-instance app; after a user installs it, the host app dynamically downloads malicious plugins and executes them without the user’s awareness.

Since the emergence of app-virtualization repackaged malware in 2016, we are tracking their evolvement all the time. Figure 4(a) shows the total number of app-virtualization-based benign apps and malware samples collected by Antiy AVL in each quarter over three years (2016 - 2019). Antiy AVL’s threat detection engine provides rich metadata to identify benign apps, malicious repackaged apps, and app-virtualization-based apps. As DroidPlugin and VirtualApp are two leading app-virtualization engines, we add additional static features to recognize them. For other app-virtualization apps that do

![](bbox=[0.56, 0.105, 0.85, 0.27])

(a) The number of app-virtualization-based apps and engines.

![](bbox=[0.56, 0.3, 0.85, 0.47])

(b) The number of new malware samples in each quarter.

# Figure 4: The statistics of app-virtualization-based apps.

not match such fingerprint features, we put them into the “custom-made” category.

The two most popular app-virtualization engines, VirtualApp and DroidPlugin, occupy the portion of 92.4% because of their open source. The rest of the apps have custom-made virtualization engines. The core principle of these custom-made engines is similar to VirtualApp/DroidPlugin, but they have different implementation details, such as using AIDL or Content Provider to implement IPC. Custom-made category has 10,621 apps, including six different app-virtualization frameworks. For example, the underlying virtualization engine of Parallel Space is called MultiDroid, and we treat it as a custom-made engine.

Interestingly, the number of malware armored by VirtualApp is about three times larger than that of VirtualApp-based benign apps. In addition, we also investigate the activity level of repackaged malware from September 2016 to December 2019. Figure 4(b) shows the number of new malware samples that have different hash values quarterly. Since 2016, the increment of traditional repackaged malware slows down, while app-virtualization-based malware exhibits a fast growth from 2017 Q3. Especially, we observe many new malware variants have switched from the previous repackaging style to app-virtualization. The growing gap shown in Figure 4(b) indicates that app-virtualization is very likely to dominate the next generation of Android malware repackaging ways.

We elaborate some detailed characteristics of app-virtualization-repackaged malware and present Triada as typical app-virtualization-based malware in Appendix.