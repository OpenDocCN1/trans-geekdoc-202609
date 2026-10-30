
Now this three-step process may appear simple, but that is somewhat deceptive. You can likely already see that step 1 is going to entail some time-consuming research. Step 2 is rather straightforward, and should be almost identical for all your SCADA penetration tests. Step 3 could include any of the penetration testing topics we have covered in the preceding 17 chapters. Given that Chapters 13–16 focused on Metasploit, you will be pleased to know there are Metasploit modules for SCADA. Here are some resources:

- https://scadahacker.com/resources/msf-scada.html
- https://www.rapid7.com/about/press-releases/new-metasploit-module-to-exploit/
- http://www.securityweek.com/rapid7s-metasploit-get-scada-exploits

These sources can assist you in leveraging your newfound Metasploit skills to penetration test SCADA systems.

In addition to the material already covered in this section, there are a few other standards that might be of interest in specific environments:

- North American Electric Reliability Corporation (NERC) has standards for electrical systems. These can be accessed at http://www.nerc.com/pa/Stand/Pages/Project-2014-XX-Critical-Infrastructure-Protection-Version-5-Revisions.aspx.
  - NERC CIP (Critical Infrastructure Protection) 007-6 in particular addresses the patching of all systems.
  - The newest version of NERC 1300 is called CIP-002-3 through CIP-009-3.
- “Firewall Deployment for SCADA and Process Control Networks,” https://www.ncsc.gov.uk/content/files/protected_files/guidance_files/2005022-gpg_scada_firewall.pdf.
- NIST 800-115 is a general testing standard, at https://csrc.nist.gov/publications/detail/sp/800-115/final.

The issue is this: you will use the same testing skills you have developed throughout this book. However, you will need to familiarize yourself with SCADA in general, and your particular system in particular, in order to perform a successful penetration test of a SCADA system.

## Mainframes

Contrary to what you may have heard, mainframes are not dead. They do still exist. While it is true that there are far fewer security issues with mainframes, it would be incorrect to assume there are no security issues. And any system with vulnerabilities needs testing. Mainframe penetration testing includes both the operating system and the application. A few operating systems are:

- AS/400
- OS/390
- Z/OS

There are likely to be critical applications running on those systems, such as databases. Mainframe penetration testing is going to be quite similar to SCADA penetration testing. The first step will be to familiarize yourself with the target system and specific vulnerabilities to that system. Then you will use skills you have acquired throughout this book to attempt to exploit those vulnerabilities.

## Mobile Pen Testing

Mobile device penetration testing involves both cellular technology and Bluetooth. Earlier in this chapter we discussed Bluetooth technology. Before we delve into penetration testing for mobile devices let us first look at cellular technology. The first step is to get familiar with cellular terminology.

## Cellular Terminology

A mobile switching center (MSC) is the switching system for the cellular network. MSCs are used in 1G, 2G, 3G, and Global System for Mobile (GSM) communications networks. You will learn about 3G and GSM networks later in this section. The MSC processes all the connections between mobile devices and between mobile devices and landline phones. The MSC is also responsible for routing calls between base stations and the public switched telephone network (PSTN).

The base transceiver station (BTS) is the part of the cellular network responsible for communications between the mobile phone and the network switching system. The base station system (BSS) is a set of radio transceiver equipment that communicates with cellular devices. It consists of a BTS and a base station controller (BSC). The BSC is a central controller coordinating the other pieces of the BSS.

The home location register (HLR) is a database used by the MSC that contains subscriber data and service information. It is related to the visitor location register (VLR), which is used for roaming phones.

The subscriber identity module (SIM) is a memory chip that stores the International Mobile Subscriber Identity (IMSI). It is intended to be unique for each phone and is what you use to identify the phone. Many modern phones have removable SIMs, which means you could change out the SIM and essentially have a different phone with a different number. A SIM card contains its unique serial number—the ICCID—the IMSI, security authentication, and ciphering information. The SIM will also usually have network information, services the user has access to, and two passwords. Those passwords are the personal identification number (PIN) and the personal unlocking code (PUK).

The following is a list of cellular network types/technologies:

- **Global System for Mobile (GSM) communications:** GSM communications is a standard developed by the European Telecommunications Standards Institute (ETSI). Basically, GSM is the 2G network.
- **Enhanced Data Rates for GSM Evolution (EDGE):** EDGE does not fit neatly into the 2G-3G-4G continuum. It is technically considered 2G+, but was an improvement on GSM (2G), so it can be considered a bridge between 2G and 3G technologies.
- **Universal Mobile Telecommunications System (UMTS):** UMTS is a 3G standard based on GSM. It is essentially an improvement of GSM.
- **Long Term Evolution (LTE):** LTE is a standard for wireless communication of high-speed data for mobile devices. This is what is commonly called 4G.

Currently, 5G is still not being utilized, so it is not something we will discuss in this chapter. However, in the next few years it should begin being rolled out, and at that point, you will need to familiarize yourself with it.

## Bluetooth Attacks

Bluetooth attacks are quite common on cellular phones, and perhaps the most important for you to test. Let’s begin with a brief summary of the most common Bluetooth attacks:

- Blue snarfing is a class of attacks wherein the attacker attempts to get data from the phone.
- Bluejacking is sending unsolicited data to a phone, via Bluetooth. This is sometimes used to send spam instant messages.
- Blue smacking is a denial of service attack wherein the target is flooded with packets.
- Blue bugging remotely accesses phone features. This may seem very similar to Blue snarfing, but the goal with Blue bugging is not to get data, but to activate certain phone features.
- Blue sniffing is the same thing as war driving. The attacker is trying to find available Bluetooth devices to attack.
- Blue printing gets its name from footprinting. In the case of Blue printing, the attacker is trying to get information about the target phone.

## Bluetooth/Phone Tools

There are a number of tools that an attacker can use to facilitate a Bluetooth attack. You should be familiar with at least some of these. They can be a useful part of your penetration test. Some tools are only for Android, others for iPhone.

## BH BlueJack

This tool is available as open source (i.e. free) and is written in Python. It allows you to attempt Bluejacking with the click of a button. You can download it from http://www.bluejackingtools.com/symbian/bh-bluejack-bluejacking-software/.

## BlueBorne

This is a vulnerability scanner for Bluetooth. It is available in the Google Play store for Android phones, and you can see it here: https://play.google.com/store/apps/details?id=com.armis.blueborne_detector&hl=en. The vendor also has a white paper on Bluetooth vulnerabilities, which you can view here: http://go.armis.com/hubfs/BlueBorne%20Technical%20White%20Paper.pdf. Figure 18-8 shows this tool.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_403_0.png)

FIGURE 18-8 BlueBorne.

## BLE Scanner

This tool is for the iPhone and is a free download. The first thing it will do is show you nearby Bluetooth devices as shown in Figure 18-9.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_404_0.png)

FIGURE 18-9 BLE Scanner.

Then simply click the **Connect** button to attempt to connect to that device as shown in Figure 18-10.

![](img/fa54c6d61c14db5421f8f63e6d594bb5_404_1.png)

FIGURE 18-10 BLE Connect.

## Pally

Pally is another Bluetooth scanner for the iPhone. It has an easy to use interface and will provide you basic information about nearby Bluetooth devices as shown in Figure 18-11.
