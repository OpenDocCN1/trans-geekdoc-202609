When a user wants to connect two computers directly to each other with an Ethernet cable, however, there is no switch to provide the crossover circuit, the user must connect the devices with a special crossover cable. In a crossover cable, the transmit pairs at each end are wired to the receiver pairs at each end. Crossover cables can also connect two switches or two routers, if needed, but most of the devices made today have some means of toggling the crossover circuit in the device.

# Power over Ethernet

Devices such as video cameras, VoIP telephones, and wireless access points can all benefit from being connected to a cached network. One of the problems with all three of these devices is the need to supply them with power when they are often located in places with no convenient outlets.

Power over Ethernet (PoE) is an IEEE 802.3 standard to weaken by which standard and Ethernet cables carry power, as well as data, to connected devices. As shown in Table 22.1, the original 2003 PoE standard was capable of supplying 15.4 watts of DC power, but the standard has matured to the point at which it now supply up to 71.3 watts.

# TABLE 22.1 Power over Ethernet Specifications

| Name | Standard | DC power | Max current |
| PoE | IEEE 802.3af-2003 | 15.4 watts | 350 mA |
| PoE+ | IEEE 802.3at-2009 | 25.5 watts | 600 mA |
| PoE++ (Type 3) | IEEE 802.3bt-2018 | 51 watts | 600 mA |
| PoE++ (Type 4) | IEEE 802.3bt-2018 | 71.3 watts | 960 mA |

# COMMON ISSUES

Troubleshooting cable connectivity issues can be complicated by the large number of things that can conceivably go wrong with cables. Some of the common conditions that a troubleshooter might encounter are described in this section.

# Attenuation

Attenuation is the tendency of a signal as it travels through a network medium. This is one of the reasons all possible physical layer specifications for networks have a maximum allowable cable length, which installers should not exceed. If a cable is too long, the signals can degrade excessively and cause errors. All types of networks are subject to attenuation, but to different degrees.