
**Figure 10.7:** Comparison between Dalvik and ART compilation

# Native libraries

Some low-level components cannot be interacted with when developing in Java. If you need to display graphics on the device screen, for example, you will not be able to write code directly in Java; instead, you will need to write a function or method that calls other native programs that are not Java programs.

The native libraries in Android are non-Java programs. The libraries are written in various languages, including C, C++, and others. The Android `Native Development Kit` (`NDK`), which contains a wide range of libraries and headers that allow developers to create and build various activities, is used to install this native code.

*Figure 10.8* depicts the many native libraries that are currently available on the Android platform:

![](images/Figure-10.8.jpg)

**Figure 10.8:** Native libraries

It can be customized by any `Original Equipment Manufacturer` (`OEM`). The libraries module usually contains the following items:

*   **The media framework:** This framework is built on PacketVideo OpenCore platforms and supports common audio, video, and still-frame formats as well as codec plugins. The StageFright flaw was discovered by exploiting a media framework (`libStageFright`) flaw that gave attackers full remote access via a feature that automatically played video files received via MMS or other means on an Android device.

*   **The surface manager:** The display subsystem is supported, and many applications’ 2D and 3D graphics layers are rendered.

*   **Freetype:** This is used to render bitmap and text.

*   **OpenGL ES:** OpenGL is a cross-platform graphics API that defines a software interface for 3D graphics processors.

*   **Secure Socket Layer** (`SSL`)**:** This is based on OpenSSL (`www.openssl.org`).

*   **SQLite:** The application framework API makes this lightweight relational database engine available to any application.

*   **WebKit:** This is a browser engine based on the WebKit browser (`www.webkit.org`), which supports page rendering, full CSS, JavaScript, DOM, and AJAX, as well as single-column and adaptive view rendering.

*   **SGL** (short for **Scalable Graphics Library):** This is used for 2D graphics libraries.

*   **libc:** Standard C system libraries derived from BSD for embedded Linux-based devices.

# The application framework

The application framework gives developers the tools they need to create far more complicated apps or tools. This framework is used to manage the application’s full development lifecycle.

A developer who is developing an app that requires the notification feature, for example, does not need to write a single line of code; instead, he or she may just call the `Notification Manager` API. Most of the APIs required to operate an Android smartphone are provided by this framework.

A list of the frameworks that are now available for the Android platform is shown in *Figure 10.9*:

![](images/Figure-10.9.jpg)

**Figure 10.9:** Application framework

The key services in this framework are as follows:

*   **Activity manager**: The Activity Manager manages an app’s full lifetime and is also responsible for handling the many states of activity to ensure that apps using different processes operate smoothly, which we will go over in depth in the next section.

*   **Content providers**: This component enables applications to share and publish data with other apps. The content provider oversees encapsulating data, defining data security, and controlling data structure. When all of a user’s input to an app is structured and kept in an SQLite database, this is an example.

*   **Resource manager**: The Resource Manager manages access to all embedded resources that are not coded in the app, such as graphics, localized strings, and other layout files.

*   **Notifications manager**: This provides mobile user notifications and displays alerts.

*   **View system**: The View System oversees many views, event dispatching, and other important buttons and lists.

*   **Package manager**: This controls all the application packages that are installed on the device.

*   **Telephony manager**: This provides telephone services, such as status and subscriber information, to the device.

*   **Location manager**: This gives location services about changes in location, allowing an app to receive updates.

*   **Window manager**: It oversees organizing the screen that is shown to the user and providing the surface with decision-making capabilities when the application is to be generated and layered appropriately on the display window.

# The applications layer

This is the first layer of the Android stack, and it is through applications that the bulk of consumers interact with their phones. As shown in *Figure 10.10*, there are two types of applications that are generally available on the device:

![](images/Figure-10.10.jpg)

**Figure 10.10:** Applications layer

Now, let us explore the differences.

# Native Android or system apps

System apps are applications that are placed on the phone by the manufacturer and provided with it. The e-mail client, SMS program, phone, calendar, maps, phone dialer, browser, contacts, and other applications are all loaded by default. These apps are usually not able to be removed from the device and reside in the `/system` folder.

# User-installed or custom apps

The user can download and install these applications through a variety of distribution networks, including Google Play and Amazon Store. These apps are in the Android filesystem’s `/data/data/` subdirectory. In the next sections, we will go over the specifics of the security features.

# Android penetration testing environment setup

For any form of a security evaluation, establishing a well-structured test environment is critical. It is recommended that you start with a zero environment, presuming that nothing is installed on your PC. The hardware and software requirements for establishing a basic infrastructure for Android Application Penetration Testing are listed as follows.

This book concentrates on setting up the environment on Windows, but you are free to experiment with Linux and other operating systems as well.

*   **Hardware and OS requirements:**
    *   A workstation/laptop running Windows 7 (64-bit)

*   **Mobile Devices and OS requirements:**
    *   Google Nexus 5 or any other device running Android 5.0 or higher (rooted)

*   **Software requirements:**
    *   Python
    *   Java Development Kit (1.8)

*   **Other requirements:**
    *   Compatible USB cables for mobile devices
    *   Network Wi-Fi devices (one can use any smartphone with a tethering facility to act like a Wi-Fi router)

Why do you need a rooted phone for your test environment?

It is as basic as being able to edit and install any tools on the device and run unsigned software from atypical app shops. Rooted phones will have complete filesystem access. The scope of this book does not include rooting a mobile device.

# Android Studio and SDK

The official `Integrated Development Environment` (`IDE`) for developing Android Apps is Android Studio, which Google supports. Java was replaced by Kotlin on May 7, 2019, as a preferred language for developing Android Apps. But still, Java is being used for developing Android Apps. Android Studio Dolphin|2021.3.1 has the following features.

*   Gradle-based build support.
*   UI components can be created by drag and drop features in the layout editor.
*   Common Android designs and components can be created by template-based wizards.
