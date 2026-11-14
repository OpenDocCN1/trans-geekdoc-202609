+   • Application data Access to resources such as the calendar, contacts, and location
+   • User files Permission to access user folders for pictures, downloads, and music

Any attempt to access resources from a sandbox that wasn’t explicitly requested in the project definition is rejected by the operating system at runtime.

# iOS Applications

The iOS application archive (.ipa extension) has a format and structure similar to the Android APK. Both are ZIP archives with a custom file extension containing all the necessary files for the application to function correctly. As visible in the following hex dump, the magic bytes of the IPA archive are the same as those of a typical ZIP header:

```
$ hexdump -C -n 4 sample.ipa
00000000 50 4b 03 04 |PK..|
```

The application archive includes the application’s executable, configuration files, and any data or image resources. The common file types located in the archive, as described by Apple,<sup>14</sup> are as follows:

+   • Info.plist The _information property list_ file is the iOS version of the AndroidManifest.xml configuration file. It is a mandatory configuration file and contains information about the application such as permissions, supported platforms, and names of other relevant configuration files.
+   • Executable A mandatory file that contains the application code.
+   • Resource files Additional optional data files such as images and icons. These resources can be localized for a specific language or region or shared across them.
+   • Support files Additional files that are not resources, such as private frameworks and plug-ins.

iOS applications, like macOS applications, are typically written in Objective-C or Swift programming languages.

Objective-C is a general-purpose, object-oriented programming language that was used as the main language for developing applications on Apple platforms until the introduction of Swift in 2014.

Swift is a successor of Objective-C and, among other things, brings simplicity, speed, and type safety while maintaining compatibility with both Objective-C and C.

# Lab 18-1: Analyzing Binary Property List Files

Property list files (.plist) store a serialized object representation of hierarchy objects and provide developers with a lightweight and portable way to store small amounts of data. These files can contain various data types, including arrays, dictionaries, strings, data, integers, floating-point values, or booleans.

Plist files can be stored either in XML or binary format. Because XML files are readable