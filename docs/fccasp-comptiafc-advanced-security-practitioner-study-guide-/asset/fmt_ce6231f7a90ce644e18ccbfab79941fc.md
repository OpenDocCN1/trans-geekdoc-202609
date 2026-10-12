
## 3. Baselines

A *baseline* is a minimum level of security that a system, network, or device must adhere to. Baselines are usually mapped to industry standards. Baselines may be established by comparing the security activities and events of other organizations. Baselines can be used as an initial point of reference and then used for comparison for future reviews.

![FIGURE 8.5 Policy structure](images/c08f005.jpg)

**FIGURE 8.5** Policy structure

## New Technologies

Although I can clearly remember my first Sony Walkman cassette player, that technology is quite dated today and has given way to MP3 players and streaming music over the Internet. Technology continues to change, and security professionals must keep abreast of what is current.

### Intrusion Detection and Prevention

Intrusion detection has come a long way from when the concept was created in the 1980s. Early intrusion detection and prevention systems (`IDPSs`) were clearly divided into two broad types: network intrusion detection systems (`NIDSs`) and host-based intrusion detection systems (`HIDSs`). These can be further divided into categories based on the internal engine or approach to detecting anomalies. They typically include the following:

1.  **Signature** Seeks to match based on a known signature
2.  **Anomaly** Examines traffic and looks for activity that is abnormal
3.  **Protocol** Examines data and compares it to a database of known protocols and their activity

The IT security industry has grown to require more from these devices. This is how intrusion prevention systems (`IPSs`) were born. The `IPS` was designed to move beyond `IDSs` and provide the capability to enforce computer security policies, acceptable use policies, or standard security practices. Today, this technology has continued to evolve into what is known as the `IDP`. `IDPs` can record information related to observed events, generate notifications, and create reports. Many `IDPs` can also respond to a detected threat by attempting to prevent it from succeeding. They use several response techniques, which involve the `IDPs` stopping the attack itself, changing the security environment through alteration of a firewall setting, or changing the attack's content.

Many `IDPs` exist, and some are community based and therefore free. `Snort` is one of the most popular of these and has been around for several years now. A more recent addition to the community is `Suricata`. It is offered by the Open Information Security Foundation (`OISF`) with funding from the U.S. Department of Homeland Security (`DHS`) and the U.S. Navy's Space and Warfare Command (`SPAWAR`) as well as the Open Information Security Foundation (`OISF`) Consortium. More information about `Suricata` is available at `www.openinfosecfoundation.org`.

[Exercise 8.1](#c08.xhtml#c08-ex-01) will demonstrate how to perform a basic packet capture with `WinDump` and how this technology can be used to monitor and detect anomalies.

### Network Access Control

For large and small businesses alike, achieving optimal network security is a never-ending quest. A `CASP` plays a big part in securing critical systems. One potential solution to these issues is network access control (`NAC`). `NAC` offers administrators a way to verify that devices meet certain health standards before they're allowed to connect to the network. Laptops, desktop computers, or any device that doesn't comply with predefined requirements can be prevented from joining the network or can be relegated to a controlled network where access is restricted until the device is brought up to the required security standards. Several types of `NAC` are available:

*   **Infrastructure-based NAC** requires an organization to upgrade its hardware and operating systems. If your IT organization plans to roll out Windows 8.1 or has budgeted an upgrade of your Cisco infrastructure, you're well positioned to take advantage of infrastructure `NAC`.
*   **Endpoint-based NAC** requires the installation of software agents on each network client. These devices are then managed by a centralized management console.
*   **Hardware-based NAC** requires the installation of a network appliance. The appliance monitors for specific behavior and can limit device connectivity should noncompliant activity be detected.

### Security Information and Event Management

Security information and event management (`SIEM`) solutions help security professionals identify, analyze, and report on threats quickly based on data in log files. `SIEM` solutions prevent IT security professionals from being overwhelmed with audit data and endless logs so they can easily assess security events without drowning in security event data. A couple of open source tools that you can examine to get an idea as to what the tools are designed to help with include `Nagios` (`www.nagios.org`) and `Syslog-NG` (`www.balabit.com/network-security/syslog-ng/opensource-logging-system`). For a fully featured open source `SIEM` solution, you may want to look at `OSSIM`, available here: `http://sourceforge.net/projects/os-sim/`. [Exercise 8.2](#c08.xhtml#c08-ex-02) provides a demonstration of an `SIEM` tool.

### New Security Systems and Services

It is a good thing that new security systems and services are developed. Just consider one area, such as authentication. Although the security offered by passwords may have seemed great back in the 1990s, think of the current state of passwords today. In the 1990s I had just a few accounts to log in to and manage. Today, I use a password when I log in to Gmail, I have another password I use when I log into my website to upload a new web page, and then there's the password for Amazon's Author portal, and then even another for Facebook! The convenience of passwords seems to evaporate when you start to consider how many passwords you must keep up with today. Luckily, new techniques are available that you can use to perform authentication.

Biometrics is one such solution. Biometric systems have advanced in the last decade. There are many different types of biometric systems, including iris scan, voice recognition, fingerprint, and signature dynamics; however, they all basically work the same way:

1.  The user enrolls in the system. The user allows the system to take one or more samples for later comparison.
2.  The user requests to be authenticated. A sample is compared to the user's authentication request.
3.  A decision is reached. A match allows access, and a discrepancy denies access.

The accuracy of a biometric device is measured by the percentage of Type 1 and Type 2 errors it produces. Type 1 errors (False Rejection Rate [`FRR`]) measure the percentage of individuals who should have received access but were denied. Type 2 errors (False Acceptance Rate [`FAR`]) measure the percentage of individuals who gained access who shouldn't have. When these two values are combined, the accuracy of the system is established. The point at which the `FRR` and `FAR` meet is known as the Crossover Error Rate (`CER`). The `CER` is a key accuracy factor: the lower the `CER`, the more accurate the system. Another attribute of biometric systems is that fingerprints, retinas, or hands cannot be loaned to anyone. Some common biometric systems include the following:

1.  **Fingerprint Scan Systems** These systems are widely used and are installed in many new laptops.
2.  **Hand Geometry Systems** These systems are accepted by most users; they function by measuring the unique geometry of a user's fingers and hand to identify that user.
3.  **Palm Scan Systems** Palm scan systems are much like hand geometry systems except they measure the creases and ridges of a palm for identification.
4.  **Retina Pattern Systems** Retina pattern systems are very accurate; they examine the user's retina pattern.
5.  **Iris Recognition** Iris recognition matches the user's blood vessels on the back of the eye.
