for modem control or Ethernet for local-network traffic. The communication-device class is also an option for other devices accessed via COM-port functions on the host.

# Documentation

The main documentation for communication devices is the specification for the communication-device class (CDC). Two subclasses have their own documents. The Wireless Mobile Communications (WMC) subclass includes terminal equipment for wireless devices that can perform multiple functions such as audio and data communications. The Ethernet Emulation Model (EEM) Devices subclass includes devices that send and receive Ethernet frames. At this writing, the latest specification versions are 1.1 for CDC and 1.0 for WMC and EEM. The V.250 standard (formerly known as V.25ter and encompassing the Hayes AT command set) is available from the International Telecommunication Union at www.itu.int. The Ethernet standard, IEEE 802.3, is available from www.ieee.org.

The Remote Network Driver Interface Specification (NDIS) defines a protocol for using USB and other buses to configure network interfaces and to send and receive Ethernet data. Remote NDIS is based on NDIS, which defines a protocol to manage communications with network adapters and higher-level drivers. NDIS and Remote NDIS are supported by Windows, but not by other operating systems. Documentation for NDIS and Remote NDIS are available from www.microsoft.com.

# Overview

A communication device is responsible for the tasks of device management, call management (optional), and data transmission. Device management includes controlling and configuring a device and notifying the host of events. Call management involves establishing and terminating telephone calls or other connections. Not all devices require call management. Data transmission is the sending and receiving of application data such as phone conversations or files sent over a modem or network.

The communication device class supports three basic models for communicating. The POTS (Plain Old Telephone Service) model is for communica-