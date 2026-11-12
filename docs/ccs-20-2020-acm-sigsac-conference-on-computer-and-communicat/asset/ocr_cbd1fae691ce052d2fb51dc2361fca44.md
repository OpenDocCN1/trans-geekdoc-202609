+   - [52] Yueqian Zhang, Xiapu Luo, and Haoyang Yin. DexHunter: Toward Extracting Hidden Code from Packed Android Applications. In Proceedings of the 20th European Symposium on Research in Computer Security (ESORICS ’15), 2015.
+   - [53] Shenggu Xi, Shao Yang, Xusheng Xiao, Yuan Yao, Yauong Xiong, Fengyuan Xu, Haoyu Wang, Peng Gao, Zhuotao Liu, Feng Xu, and Jian Lu. DeepIntent: Deep Intent-Behavior Learning for Detecting Intention-Behavior Discrepancy in Mobile Apps. In Proceedings of the 26th ACM SIGSAC Conference on Computer and Communications Security (CCS ’19), 2019.
+   - [54] rov89. Xposed Module Repository. https://repo.xposed.info/, 2019.
+   - [55] Avast Threat Intelligence Team. Malware posing as dual instance app steals users’ Twitter credentials. https://blog.avast.com/malware-posing-as-dual-instance-app-steals-users-twitter-credentials, 2016.

# APPENDIX

# A DETAILED INFORMATION ABOUT OUR STUDY IN SECTION 3.1

# A.1 Characteristics

We summarize the common characteristics of app-virtualization repackaged malware. The first two characteristics cover how malware utilizes app-virtualization to perform malicious behaviors; the next two characteristics are about how malware host apps store and load plugins.

**Self-contained Systems.** In this category, malware authors encapsulate an app-virtualization engine and malicious plugin modules as a self-contained system. These malware instances are spread using social engineering tricks to deceive users into downloading them. Once on the victim’s device, malware can load the malicious plugins either from its own subdirectory like PluginPhantom [12] or download plugins from Internet like Hummingbad [44]. These plugins can perform various malicious functions, such as intercepting incoming phone calls and SMS, advertisement/pornography promotion, and ransomware behavior. As this kind of malware does not load any third-party plugins, existing app-virtualization environment detection heuristics [14, 17] do not work here.

**Attack Benign Plugins.** The second category of malware exploits the vulnerability of app-virtualization to compromise benign apps. They disguise themselves as an attractive app-virtualization application, such as a dual-instance app, to lure users into installing them. Then, a malicious plugin conducts attacks in the background when the benign plugin is running. Due to the “shared-everything” threat [17], even with zero permission, the malicious plugin can still get access to other plugins’ sensitive data and inject malicious code dynamically into other running plugins.

**Encrypted/Downloaded Plugins.** To impede static analyses that attempt to inspect malicious payload plugins, most malicious plugins’ APK files are not statically visible. Our study shows that up to 89.2% of app-virtualization-based malware samples encrypt their plugins, and 10.5% of malware samples choose to download plugins from Internet at run time. For malware samples that encrypt their plugins, we also use reverse-engineer the cryptographic algorithms they use. 84.5% of them apply the standard AES algorithm, and the left of them adopt a self-defined encryption algorithm, such as performing XOR operations with specific byte streams.

**Load Malicious Plugins Stealthily.** Plugin loading strategies stand in stark contrast between app-virtualization-based malware and benign apps. In general, a user interface will show up when a benign app is loading plugins. It is the user’s turn to select which plugin to load, and then the host app copies and loads the plugin

APK file from the specific path that the user decided. Besides, benign apps do not hide their icons from the phone’s desktop. On the contrary, malware loads malicious plugins stealthily to hide their malicious behaviors. Their plugin loading process typically does not involve user interactions (e.g., button click or popup window). The malware host app searches for plugin APKs by invoking path APIs, because it has already known where malicious plugins locate. After installation, malware tends to hide themselves by running in the background without showing any icon or Activity.

# A.2 Case Study

A new version of malware Triada² is developed on top of DroidPlugin to steal the victim’s personal information without raising suspicion. Triada disguises itself as Wandoujia app, which is one of China’s most prominent Android app stores. As shown in Figure 9, after installation, Triada reminds users that “the program is incomplete and needs to be reinstalled” to lure users into installing the real Wandoujia app, but Triada runs in the background by hiding its icon. If users disagree, Triada cancels the real Wandoujia’s installation but still runs in the background as a memory cleaning service. Triada hides all APK plugins in its “Assets” directory, and each plugin has a dedicated action. One of its plugins communicates with a remote C&C server, which instructs Triada to load a particular plugin to carry out an activity, such as connecting a WiFi signal, recording calls, acquiring realtime location, sending messages, uploading private data, or updating itself. Besides, all of these plugins run in the background without showing any interfaces.

![](bbox=[0.52, 0.5, 0.9, 0.69])

Figure 9: Triada malware disguises itself as Wandoujia app and loads malicious plugins via DroidPlugin.

# B THREAD INTERRUPTION ANALYSIS IN SECTION 6

Detecting the user consent characteristic is to analyze the API call chain from plugin installation to app startup. However, our study shows many host apps start new threads to load plugins, which complicates the chasing of API call chain. For example, a VirtualApp-based malware sample steals users’ Twitter credentials in a new thread by using Thread Class and then starts the thread in

2 SHA-1 value: e2b05c8fdf8b2e606ab378e14b8f4be8411f70