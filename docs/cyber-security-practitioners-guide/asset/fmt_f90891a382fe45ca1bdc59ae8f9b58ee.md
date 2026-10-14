
Using an ETB to connect the train means that communication between ECNs can exploit ethernet performance, currently up to 10 Gb/s (10000BASE-T). An example is shown in [Fig. 3.4](#chapter3.xhtml#fig3.4) below. This enables greater flexibility in train reconfiguration. To avoid IP conflicts, whenever two or more Consists are reformed to make a train there is a process of Inauguration, which gives all nodes of the ETB their IP address and controls how they relate to all the other nodes on the same backbone.

The draft IEC 61375-2-6:2016 is entitled ‘On-board to ground communication’. This document introduces a Mobile Connectivity Gateway (MCG) onto the ETB to enable connectivity to shore-based systems.

![image](images/fig3.3.jpg)

**Fig. 3.3.**Train consists.

![image](images/fig3.4.jpg)

**Fig. 3.4.**Consist networks.

The introduction of an Ethernet network onto the train and its use to interconnect the MVB, WTB and CAN-bus transforms the network into a LAN, and the connectivity provided by the MCG gives the LAN a WAN connection. The IEC 61375 standard offers little cyber security direction; only the as yet unpublished IEC 61375-2-6 refers to IEC 62443 for guidance on risk assessment and mitigation.

As well as its multi-agent nature there are a number of characteristics that make the Digital Train LAN/WAN distinctive:

i)WAN connectivity is usually via 4G which is unreliable across the railway network;

ii)There are approximately 20,000 passenger vehicles distributed across the country according to DfT (2017);

iii)Each train generally has 1 or 2 company representatives on-board, and maybe several hundred customers, some of whom are using the on-board network to access the internet; and

iv)Trains move, sometimes at high speed.

This is not the same cyber security problem, with the same risks, that exists with land-based networks.

Ethernet Backbones have been included in the new train design and build since the IEC 61375 standard was extended in 2015 to include the ETB, but with public WiFi having become a hygiene factor in the customer experience, and with governmental influence on the rail industry, legacy fleets are also being fitted with ‘Ethernet Backbones’ and an MCG to provide internet connectivity to deliver public WiFi and ‘Infotainment’. Where this network is used only for public services there is no issue but once the network is available the temptation for train engineers to use it to connect other systems is difficult to resist. Although some industry bodies have published guidelines, there are few firm design principles, and any that there are have been constrained through limitations on power, space and cost when retrofitting aged vehicles.

Referring to retrofitted systems, RSSB (2016) alludes to the problems that have arisen due to the ad hoc nature of on-board network implementation and attributes these to the poor standard of network awareness and uncoordinated commercial influences. RSSB advocated separate train networks but recognises the drivers towards integration and warns that “the integrity needs to be robust and provided with security and privacy controls”. To elaborate, connectivity to on-board systems started with individual system upgrades introducing 4G receivers for a single device. This enables systems such as seat reservations displays to be updated remotely. Similarly, some condition-based monitoring systems were updated to enable data to be offloaded, again using a 4G connection. It was the introduction of public wifi on trains that prompted the retrofitting of ETBs, albeit with a simpler architecture than that defined in IEC 61375. It was recognised in some quarters that network segregation and security controls were a necessary consideration and early publications such as Tonks (2016) raised awareness regarding the emerging requirements.

![image](images/fig3.5.jpg)

**Fig. 3.5.**Basic retrofit architecture.

The need to segregate networks was initially envisaged as a physical exercise and dual backbone designs were originally proposed but the cost of duplicating switches, the lack of on-board space to accommodate additional equipment and in many cases the lack of sufficient power has guided suppliers towards single backbones such as the one shown in [Fig. 3.5](#chapter3.xhtml#fig3.5) above, reproduced from Duffy (2018), which shows a typical implementation solely to provide public wifi.

From the same source, Duffy (2018), a more complex design to accommodate a wider range of connected on-board systems is shown in [Fig. 3.6](#chapter3.xhtml#fig3.6) below.

Neither the 61375 standard nor the solutions advertised by the rail supply chain make much reference to cyber security, yet it is clear that such advances in integrated solutions have an impact on both threats and vulnerabilities. Previously, all on-board systems stood alone and required specialist knowledge to access, but largescale integration expands the attack surface available. The use of ethernet as a link layer protocol extends the source of threats as it brings the means to attack it into the capability of a far wider group of actors. In the corporate world it would be inconceivable to allow such a scenario to be unprotected and yet industries such as rail have been slow to react, with requirements generally being driven by regulation rather than corporate risk management.

![image](images/fig3.6.jpg)

**Fig. 3.6.**Complex retrofit architecture.

### 3.2.In Search of Solutions

Many international standards are adopted by peer organisations around the world and renamed to identify the local standard authority’s approval. For instance, ISO 27001 is also known as BS EN ISO/IEC 27001 in the UK and AS/NZS ISO/IEC 27001 in Australasia. In Germany the DIN (Deutsches Institut für Normung e.V. (German Institute for Standardization) organisation has published DIN EN ISO/IEC 27001 and so on around the world. Standard referencing requires that standards are cited as ‘authorising organisation and year’, e.g. 27001 would be cited as BSI (2013), but BSI published many standards in that year, including other standards referenced in this document. For that reason, and for readability, this document will use the basic nomenclature, without any prefix, when referring to a standard and will include the nomenclature where it is cited. The reference will identify a BSI standard if one is available or will refer to the standard originator, e.g. IEC, if there is not, which will also clarify which version of the standard is being used, e.g. 27001 will be cited as (BSI, 2013) 27001 and referred to as 27001 and IEC 62443-1-1 which at the time of writing has yet to be included in BSI’s library, will be cited as (IEC, 2009) 62443-1-1 and referred to as 62443-1-1.

There are multiple sources of guidance to industry from both government and non-partisan industry organisations including NCSC (National Cyber Security Centre), DfT (Department for Transport), DCMS (Department for Digital, Culture, Media and Sport), HSE (Health and Safety Executive), RDG (Rail Delivery Group) and RSSB (Rail Safety and Standards Board).

RDG (2017), the Rail Cyber Security Strategy, is published by the Rail Delivery Group, which is an industry body designed to represent the interests of the rail Train Operating Companies (TOCs). The document references various standards, including (BSI, 2013) 27001 and the NIST Cyber security Framework (NIST, 2018) although in 2017 it referenced the 2017 version, which in turn references (BSI, 2011) 62443 (but as the ISA version dated 2009) and other security standards.
