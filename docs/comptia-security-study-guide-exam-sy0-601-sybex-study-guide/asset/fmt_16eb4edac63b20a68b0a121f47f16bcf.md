
# Mobile Device Deployment Models

## CYOD (Choose Your Own Device)

In CYOD models, the organization pays for the device and typically for the cellular plan or other connectivity. The user selects the device, sometimes from a list of preferred options, rather than bringing whatever they would like to use. In a CYOD design of this type, support is easier since only a limited number of device types will be encountered, and that can make a security model easier to establish as well. Since CYOD continues to leave the device in the hands of the user, security and management is likely to remain less standardized, although this can vary.

## Deployment Options Comparison

[**TABLE 13.2**](#c13.xhtml#R_c13-tbl-0002) Mobile device deployment and management options

| | Who owns the device? | Who controls and maintains the device | Description |
|---|---|---|---|
| **BYOD** (Bring your own device) | The user | The user | The user brings their own personally owned device. This provides more user freedom and lower cost to the organization, but greater risk since the organization does not control, secure, or manage the device. |
| **CYOD** (Choose your own device) | The organization | The user | The organization owns the device but allows the user to select and maintain it. |
| **COPE** (Corporate-owned, personally enabled) | The organization | The organization | Corporate-provided devices allow reasonable personal use while meeting enterprise security and control needs. |
| Corporate-owned | The organization | The organization | Corporate-owned provides the greatest control but least flexibility. |

## COPE (Corporate-Owned, Personally Enabled)

In a COPE model, the device is company-owned and -managed. COPE recognizes that users are unlikely to want to carry two phones and thus allows reasonable personal use on corporate devices. This model allows the organization to control the device more fully while still allowing personal use.

## Fully Corporate-Owned

A fully corporate-owned and -managed device is the most controlled environment and frequently more closely resembles corporate PCs with a complete control and management suite. This is the least user-friendly of the options, since a corporate-chosen and -managed device will meet corporate needs but frequently lacks the flexibility one of the more end user–centric designs.

## Implementation Considerations

Although these are common descriptions, real-world implementations vary significantly, and the lines between each of these solutions can be blurry. Instead of hard-and-fast rules, these are examples of starting places for organizational mobile device deployment models and can help drive security, management, and operational practices discussions. The best way to look at these practices in real-world use is as part of a spectrum based on organizational needs, capabilities, and actual usage.

## Supporting Technologies

One key technology that can help make mobile device deployments more secure is the use of `virtual desktop infrastructure (VDI)` to allow relatively low-security devices to access a secured, managed environment. Using `VDI` allows device users to connect to the remote environment, perform actions, and then return to normal use of their device. Containerization tools can also help split devices between work and personal-use environments, allowing a work container or a personal container to be run on a device without mixing data and access.

# Mobile Device Management

Mobile devices can be a challenge to manage, particularly due to operating system limitations, variability between hardware manufacturers, carrier settings, and operating system versions. Many mobile devices are intended to be used by individuals and don't have the broad set of built-in controls that more business-oriented devices and software typically have. When you add in the wide variety of device deployment models, security practitioners face real challenges in an increasingly mobile device–focused environment.

Thus, when administrators and security professionals need to manage mobile devices, they frequently turn to `mobile device management (MDM)` or `unified endpoint management (UEM)` tools. `MDM` tools specifically target devices like Android and iOS phones, tablets, and other similar systems. `UEM` tools combine mobile devices, desktops and laptops, and many other types of devices in a single management platform.

A third class of tools known as `mobile application management (MAM)` tools focuses specifically on the applications that are deployed to mobile devices. Common features include application delivery, configuration, update and version management, performance monitoring and analytics, logging, and data gathering, as well as various controls related to users and authentication. Although `MAM` products are in use in some organizations, they are becoming less common as more full-featured `MDM` and `UEM` tools take over the market to provide more control of mobile devices.

Regardless of the type of tool you choose, there are a number of features your organization may use to ensure that your mobile devices and the data they contain are secure. Although the following list isn't a complete list of every feature available in `MDM`, `UEM`, and `MAM` tools, you need to know about each of them, and why you might want to have it, to be ready for the exam.

## Key MDM/UEM/MAM Features

### Application Management

Application management features are important to allow enterprise control of applications. These features may include deploying specific applications to all devices; limiting which applications can be installed; remotely adding, removing, or changing applications and settings for them; or monitoring application usage.

### Content Management

Content management (sometimes called `MCM`, or mobile content management) ensures secure access and control of organizational files, including documents and media on mobile devices. A major concern for mobile device deployments is the combination of organizational data and personal data on `BYOD` and shared-use devices. Content management features lock away business data in a controlled space and then help manage access to that data. In many cases, this requires use of the `MDM`'s application on the mobile device to access and use the data.

### Remote-Wipe Capabilities

Remote-wipe capabilities are used when a device is lost or stolen, or when the owner is no longer employed by the organization. It is important to understand the difference between a full device wipe and wiping tools that can wipe only the organizational data and applications that have been deployed to the device. In environments where individuals own the devices, remote wipe can create liability and other issues if it is used and wipes the device. At the same time, remote wipe with a confirmation process that lets you know when it has succeeded is a big part of helping protect organizational data.

### Geolocation and Geofencing

Geolocation and geofencing capabilities allow you to use the location of the phone to make decisions about its operation. Some organizations may only allow corporate tablets to be used inside corporate facilities to reduce the likelihood of theft or data access outside their buildings. Other organizations may want devices to wipe themselves if they leave a known area. Geolocation can also help locate lost devices, in addition to the many uses for geolocation that we are used to in our daily lives with mapping and similar tools.

### Screen Locks, Passwords, and PINs

Screen locks, passwords, and PINs are all part of normal device security models to prevent unauthorized access. Screen lock time settings are one of the most frequently set security options for basic mobile device security. Much like desktops and laptops, mobile device management tools also set things like password length, complexity, and how often passwords or PINs must be changed.

### Biometrics

Biometrics are widely available on modern devices, with fingerprints and facial recognition the most broadly adopted and deployed. Biometrics can be integrated into mobile device management capabilities so that you can deploy biometric authentication for users to specific devices and leverage biometric factors for additional security or ease of use.
