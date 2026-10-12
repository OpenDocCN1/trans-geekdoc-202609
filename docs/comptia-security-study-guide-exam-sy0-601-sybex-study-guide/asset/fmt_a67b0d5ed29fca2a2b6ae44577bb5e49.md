
## Context-Aware Authentication

Context-aware authentication goes beyond PINs, passwords, and biometrics to better reflect user behavior. Context may include things like location, hours of use, and a wide range of other behavioral elements that can determine whether a user should be able to log in.

## Containerization

Containerization is an increasingly common solution to handling separation of work and personal-use contexts on devices. Using a secure container to run applications, store data, and otherwise keep the use of a device separate greatly reduces the risk of cross-contamination and exposure. In many MDM models, applications use wrappers to run them, helping keep them separate and secure. In others, a complete containerization environment is run as needed.

## Storage Segmentation

Storage segmentation can be used to keep personal and business data separate as well. This may be separate volumes or even separate encrypted volumes that require specific applications, wrappers, or containers to access them. In fact, storage segmentation and containerization or wrapper technology are often combined to better implement application and separation.

## Full-Device Encryption (FDE)

Full-device encryption (FDE) remains the best way to ensure that stolen or lost devices don't result in a data breach. When combined with remote-wipe capabilities and strong authentication requirements, FDE can provide the greatest chance of a device resisting data theft.

## Push Notifications

Push notifications may seem like an odd inclusion here, but sending messages to devices can be useful in a number of scenarios. You may need to alert a user to an issue or ask them to perform an action. Or you may want to communicate with someone who found a lost device or tell a thief that the device is being tracked! Thus, having the ability to send messages from a central location can be a useful tool in an MDM or UEM system.

## MDM and UEM Controls

MDM and UEM tools also provide a rich set of controls for user behaviors. They can enable closed or managed third-party application stores or limit what your users can download and use from the application stores that are native to the operating system or device you have deployed. They can also monitor for firmware updates and versions, including whether firmware over-the-air (OTA) updates have been applied to ensure that patching occurs.

Of course, users may try to get around those controls by rooting their devices, or jailbreaking them so that they can sideload (manually install from a microSD card or via a USB cable) programs or even a custom firmware on the device. MDM and UEM tools will detect these activities by checking for known good firmware and software, and they can apply allow or block lists to the applications that the devices have installed.

## Service and Capability Control

Controlling which services and device capabilities can be used, and even where they can be used, is also a feature that many organizations rely on. Limiting or prohibiting use of cameras and microphones as well as SMS, MMS, and rich communication services (RCS) messages can help prevent data leakage from secure areas. Limiting the use of external media and USB on-the-go (OTG) functionality that allows devices to act as hosts for USB external devices like cameras or storage can also help limit the potential for misuse of devices. MDM and UEM tools also typically allow administrators to control GPS tagging for photos and other documents that may be able to embed GPS data about where they were taken or created. The ability to use location data can be a useful privacy control or may be required by the organization as part of documentation processes.

## Wireless Connectivity Control

Administrators may also want to control how devices use their wireless connectivity. That can take the form of limiting which Wi-Fi networks devices can connect to, preventing them from forming or joining ad hoc wireless networks, and disabling tethering and the ability to become a wireless hotspot. Bluetooth and NFC controls can also help prevent the device from being used in ways that don't fit organizational security models, such as use as a payment method or access device.

## Carrier Unlocking

The final item listed in the Security+ outline for enforcement and monitoring is carrier unlocking. `Carrier unlocking` allows phones to be used with other cellular providers. Monitoring the carrier unlock status of a device is not a common MDM capability and is typically handled at the carrier level.

## Specialized Mobile Device Security Tools

Securing mobile devices also involves operating system and hardware security. The Security+ exam lists two specific security technologies that are specific examples of mobile device security capabilities.

### microSD Hardware Security Modules (HSMs)

The first is microSD hardware security modules (HSMs). Like the hardware security modules we have talked about elsewhere in this book, a microSD HSM is a hardware key management and Public Key Infrastructure (PKI) tool in a very small form factor. In fact, HSMs like this are available as more than just microSD cards—they come in USB, SIM, and other form factors as well.

Like other HSMs, these devices provide services for key creation, backup and restore, and management, and support public key authentication and other cryptographic tools. Of course, the devices aren't useful on their own and require an app to use them.

### SEAndroid

The second specific technology the exam considers is SEAndroid. SEAndroid is a version of Security Enhanced Linux for Android devices. SEAndroid provides the ability to enforce mandatory access control on Android devices. That means that Android processes of all types can be better compartmentalized, limiting exploits as well as helping to secure system services, system and application data, and logs.

Like many security systems, any action that isn't explicitly allowed is denied—a default deny system. SEAndroid operates in an enforcement mode that logs any permission denials that occur in addition to enforcing them. SEAndroid allows a broad range of policies to be implemented on Android devices.

## Summary

Building a secure network starts with an understanding of the wireless connectivity options that organizations may choose to deploy. Although Wi-Fi, cellular, and Bluetooth are found almost everywhere, other technologies like RFID, infrared, and NFC are also built into devices and systems. These technologies can be built into point-to-point or point-to-multipoint networks, and knowing which technologies are in play and how they connect devices is the first part of designing your network.

Once you know what type of wireless technology you need to secure, you must understand the common attacks against wireless technologies and protocols as well as specific attacks commonly aimed at networks. Rogue access points, evil twins, and disassociation attacks are methods used to attack Wi-Fi networks, and bluesnarfing and bluejacking target Bluetooth. Jamming, or flooding networks so that traffic cannot make it through, can be conducted against most radio frequency and even infrared networks.

With technologies and attacks in mind, network design is conducted, including using site surveys to understand the environment that the network will be deployed into. Heatmaps show signal propagation and can help with device placement. How you will protect your controllers and access points also comes into play, with concerns ranging from patching and maintenance to secure remote access via protected channels or networks.

Once a network is designed, security and authentication options are the next layer in your design. WPA2 and WPA3 provide encryption capabilities and deployment models that allow users to use preshared keys (WPA2-PSK) or unique passwords, as well as enterprise models that connect to RADIUS servers to allow the use of organizational credentials. EAP and its many variants allow choices based on what your hardware supports and what specific authentication choices you need to make.
