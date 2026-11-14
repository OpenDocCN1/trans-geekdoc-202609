# # Dissecting Mobile Malware

Smartphone devices replace the traditional “mobile phones” as a pocket-sized personal computer and multimedia device, all in one. These personal devices provide a window into the owner’s life. A calendar containing the user’s daily schedule, a phone book with a list of contacts, social media accounts, and banking applications are only a small subset of all the information that can be found on a typical smartphone. Malware authors have already tapped into this rich platform and are exploiting it in various ways. Understanding the architecture of mobile devices and application analysis techniques empowers users to determine whether applications accessing their personal data are doing it in a nonmalicious way.

This chapter provides analysis techniques and tools that can be used to determine the functionality and potential maliciousness of mobile applications.

In this chapter, we cover the following topics:

+   * How the Android and iOS platforms work
+   * Static and dynamic analysis with a focus on malicious software analysis

# ## The Android Platform

Before we start with malware analysis, it is necessary to get familiar with the Android platform. Probably the most interesting information from an analysis point of view involves how applications work and are executed. The following sections explain the Android application package (APK), important configuration files such as AndroidManifest, and the executable file format DEX running on a Dalvik virtual machine.

# ## Android Application Package

The Android application package (APK) is an archive format used to distribute applications for the Android operating system. The APK archive contains all the files needed by the application and is a convenient way to handle and transfer applications as a single file. The archiving file format is the widely popular ZIP file format. This makes it very similar to the Java archive (JAR), which also uses ZIP.

Because APK files are just ZIP archives with a different file extension, there is no way to differentiate them from other ZIP archives. Magic bytes is the name for a sequence of bytes (usually at the beginning of a file) that can be used to identify a specific file format. The Linux file command can be used to determine the file type. Following is the output of the file command for an APK: