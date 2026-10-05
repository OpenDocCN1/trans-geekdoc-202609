
# Networked Devices

Many servers and routers include this capability in software, but there are advantages to using a dedicated headend for this purpose.

The VPN headend is responsible for maintaining one end of the multiple encrypted VPN tunnels through the Internet to the users' locations. As encryption and decryption are highly processor-intensive applications, it can be advantageous to offload processing to a separate hardware device.

## NETWORKED DEVICES

In addition to the devices that make up the network, the Network+ exam also expects candidates to be familiar with some of the devices that are now being networked, some for the first time.

## VoIP Phones

With the increasing use of VoIP in the business world, the average user's desktop phone has had to evolve with the rest of the telecommunications system. VoIP telephones can be standard physical devices similar in appearance to any other desk phone, except that they connect to an Ethernet network rather than a separate telecommunications network. Some phones can use Power over Ethernet (PoE) rather than a standard power code. In some cases, the phone is not a physical device at, but rather a software application running on the user's system, requiring only a headset to make it a fully VoIP telephone.

## Printers

Printer calls often the bane of an IT worker's existence, frequently, printers are left to the control of their end users. While printers have been networked for decades, this is often accomplished by sharing printers attached to workstations. Many printers are equipped with network interfaces, either wired or wireless, which allow users to connect directly to the network. However, the best way to centralize control of printers is to create one print server that feeds jobs to the appropriate print device. This approach allows administrators to control access to the printers and monitor its activities.

## Physical Access Control Devices

Physical access control devices, as doors with swipe card readers, have made it possible for businesses to monitor and track the locations of their employees, visitors, and sometimes their intruders.

An access control device typically has a combination of authentication mechanisms, such as a swipe card reader and a keypad for input of a PIN. There must also be a solenoid or other mechanism that controls the door lock and a central console where administrators can manage permissions and monitor activities. Connections to a standard Ethernet network allow the various components to communicate, and there might be separate low-voltage connections to supply devices with power.

## Cameras

Apart from live sentries, there is no better security mechanism than cameras scattered about a facility. At one time, installing cameras for security required a proprietary closed-circuit network. However, today there are relatively inexpensive cameras that can connect to a standard network, either wired or wireless, allowing them to be monitored from a central location and video saved to a network server. Some cameras are fixed, whereas others are capable of panning, tilting, and zooming. Cameras with cabled connections can sometimes use Power over Ethernet (PoE) to supply the cameras with electricity.

## HVAC Sensors

Heating, ventilation, and air conditioning are major expenses in any facility, and controlling them efficiently can help to manage that expense. Networking the various components of an HVAC installation can allow administrators to monitor and control them from remote locations.

Some HVAC control products also enable administrators to create rules that cause the equipment to self-adjust in certain conditions, such as turning the heat or air conditioning when the equipment detects that no one is in the building.

Networked HVAC systems have a central console that controls the station, as well as sensors and actuators scattered about the facility. The sensors monitor the environment throughout the building and the control of the HVAC equipment. The actuators can turn devices on or off as they need, all from the central console. With access controls, a low-voltage connection linking the controls supplies them with power.

## Internet of Things (IoT)

The Internet of Things (IoT) is the designation that has been applied to the growing class of devices that have been made "smart" with the integration of a TCP/IP network client. The client allows device to obtain an IP address from a DHCP server, just like any computer, and communicate with the network using Wi-Fi, Bluetooth, or other wireless protocols. Users can typically monitor and control IoT devices from any location with a cellphone app. Many IoT devices are household devices, including the following:

## Refrigerators

Because of their size and location, refrigerators have touchscreens and they can download and run apps, just like a smartphone or tablet. Smart refrigerators even include internal cameras that users can access with a smartphone to see what groceries they need as they are shopping in the market.

## Smart Speakers

A smart speaker is a wireless device that is essentially a voice-activated interface to a search engine. The device allows users to ask questions, play music, and control other home automation products.

## Smart Thermostats

A smart thermostat cannot only respond to remote commands from a smartphone, but can also execute rules that automatically adjust the temperature setting based on the time of day, the temperature outside, or the presence of people in the home.

## Smart Doorbells

Smart doorbells typically have cameras integrated into them so that the homeowner can see who is at the door, speak to the callers, and capture video of motion seen by the camera.

## ICS and SCADA

An industrial control system (ICS) does for factories and other manufacturing facilities what HVAC systems do for a building environment. An ICS includes sensors and actuators on the equipment and a controller that administrators use to monitor and control the factory's various processes. The sensors monitor the conditions of manufacture, such as the temperature, pressure, and speed of a process, and the actuators allow an operator to modify conditions by adjusting controls from a remote location.

Supervisory Control and Data Acquisition (SCADA) is a standardized architecture for this type of industrial control, but it is designed for use by utility companies and other large-scale industries that are typically distributed across multiple facilities, such as electrical production, oil and gas pipelining, and railroads.

> CERTMIKE ESSENTIALS

- The devices that make up a modern network include switches, repeaters, bridges, media converters, and access points at layer 2 of the OSI model, routers and multilayer switches at layer 3, and firewalls, proxy servers, and intrusion detection/vention systems at the upper layers.
- Networked communication devices include cable and DSL modems, voice gateways, and VPN headends.
- Devices now being connected to networks include VoIP telephones, printers, access control devices as door locks, cameras, HVAC sensors, and industrial control systems.

## Practice Question 1

Ralph is an IT consultant working for a new video production client, who has a Fast Ethernet LAN with 50 workstations and three servers, all of which are connected to three hubs that are uplinked together. The users routinely share video files among themselves, and they all require access to the servers. The owner of the firm has called Ralph because the network's users are complaining that file transfers across the network are too slow, and video streaming on the internal network is jittery and inconsistent. The owner knows that his network is outdated, but wants to know if he can improve its performance without spending a lot, as his budget is limited.

Which of the following upgrades Ralph recommend in this situation?

- A. Replace the three hubs with switches.
- B. Add a router to split the network into two 25-node LANs.
- C. Replace the hubs with a layer 3 switch and create two 25-node VLANs.
- D. Replace the Fast Ethernet hubs with Gigabit Ethernet hubs.

## Practice Question 2

Alice is consulting for a client who has a network configured like the one in Figure 9.1. After capturing a traffic sample and analyzing it, she is troubled by the number of collisions that are occurring on the network. How many collision domains and how many broadcast domains are there on this network? (Choose two answers.)

![](img/131506e178f74f7b4704a0aa0fe03dae_145_0.png)

FIGURE 9.1 A network with nine workstations
