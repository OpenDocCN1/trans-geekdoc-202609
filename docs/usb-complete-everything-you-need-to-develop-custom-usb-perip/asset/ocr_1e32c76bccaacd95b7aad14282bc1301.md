CSM-2 is DTCP, which was developed to prevent unauthorized copying of audio and video entertainment content via USB and other buses. A content owner can use DTCP to specify whether copying is allowed, identify authorized users, and specify an encryption method. A DTCP interface must have an interrupt endpoint in each direction for sending and receiving event notifications. A content provider who wants to use DTCP must sign a license agreement and pay an annual (not trivial) fee.

Two additional CSMs that don’t have USB specifications at this writing are Open Copy Protection System (CSM-3) and Elliptic Curve Content Protection Protocol (CSM-4).

# Descriptors

A Content Security function is defined at the interface level, with bInterfaceClass = 0Dh to indicate the Content Security class.

There are four class-specific descriptors:

| Descriptor Name | Description | Use |
|---|---|---|
| CS_GENERAL | Identifies the Content Security Interface version number. | One per interface |
| Channel | Identifies one or more CSMs for a channel, which can be specified by interface number endpoint address. | One per channel |
| Content Security Method | Describes a CSM implemented on a device. | One per CSM |
| Content Security Method Variant | Describes a variant of the associated CSM. | Not used by CSM-1 or CSM-2 |

CSM-2 also defines a String descriptor for the string “Digital Transmission Content Protection Version 1.00”.

# Class-specific Requests

Two class-specific requests apply to all CSM interfaces. Get_Channel_Settings enables the host to learn what CSM is assigned to a channel. The Set_Channel_Settings request enables the host to assign a CSM to a channel or deactivate a previously assigned CSM.