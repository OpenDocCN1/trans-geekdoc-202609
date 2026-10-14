
As Dakota’s London headquarters is located within a shared office complex, a communal entrance is in place. The reception is staffed continuously by security guards employed by the managing agents and forms the first layer of defence at the building perimeter.

All visitors are required to sign a register before being issued with a pass, which must be displayed at all times. Visitors may only access Dakota’s private reception area on the 1<sup>st</sup> floor, as a buildingwide access control solution prevents non-authorised individuals accessing other floors occupied by Dakota.

The building access control solution used by tenants is based on Radio Frequency Identification (RFID) technology. RFID is classified as a wireless identification and data capture technology (Barjis `et al.`, 2010). Dakota’s access control system is deliberately separate from the building’s solution, as this provides an additional layer of control and assurance. To ensure seamless conformity between the landlord’s and Dakota’s access control solutions, a technology standard was agreed on to ensure a single access pass could be programmed to operate between areas controlled by the landlord and those controlled by Dakota.

An access control pass is only assigned to permanent staff, or contractors requiring access to floors other than the Dakota reception area. Whilst access control can arguably provide some security assurance through the prevention of unauthorised individuals entering private areas where there are physical controls such as a door, the technology could be deemed weak if deployed as the sole line of defence against unauthorised physical access.

Dakota addressed the perceived limitations of the RFID technology by implementing a proximity-based monitoring solution. The proximity solution is based on Bluetooth technology and works in parallel with the RFID access control system, adding advanced real-time monitoring features that can be analysed by security staff. The proximity system forms an integral part of Dakota’s access control solution, combining a door entry system that incorporates elevator access and Closed-Circuit Television (CCTV).

Dakota was chosen for the experiment because the researcher had full access to the security technology and the data. The organisation was also considered a typical example of an open plan modern office environment.

### 4.2.1.*Proximity technology*

There is currently a broad range of access control solutions on the market, providing a wealth of security features and functionality. Many of these solutions rely on the physical attributes of a building such as internal partitioned walls to separate operational units or specific areas of a business. Whilst it could be argued that these traditional access control systems are able to secure physically separated areas, they still rely on human observation to prevent tailgating and unauthorised access.

To mitigate the risk of tailgating, organisations can consider deploying a proximity monitoring solution that incorporates access control functionality whilst providing location-specific visibility. Dakota decided to implement a proximity monitoring solution based on Bluetooth technology (`Bluetooth.com`, 2018), which leveraged a series of beacons, strategically deployed throughout the building. Each Bluetooth beacon is powered and linked through a structured Power over Ethernet (PoE) network. The beacons communicate with, and are controlled by, a virtualised communications server hosted locally.

`[Figure 4.1](#chapter4.xhtml#fig4.1)` depicts how the proximity solution can be deployed within a typical working environment. Whilst access control can determine who has access to a specific room, it has inherent weaknesses within an open plan environment.

Open plan environments have become very popular in recent history as many organisations believe an open plan office encourages openness and enhanced productivity (`Joseph`, 2018).

This can be challenging for security personnel and traditional access control solutions that rely on physical separation to enforce security controls.

If proximity zoning technologies are incorporated, it is possible to visually determine the location of staff within an open plan environment and potentially alert security personnel to unauthorised access. The ability to identify and locate employees within a controlled environment can prove useful for health & safety purposes. However, it is reasonable to assume such data could be superfluous if the target has legitimate operational reasons to be at that location.

![image](images/fig4.1.jpg)

**Fig. 4.1.**Typical real-time location system.

Simply identifying an individual within an area at a specific time may not provide sufficient data to prove the target is acting suspiciously, or poses a threat to the business. The deployment strategy of the Bluetooth beacons can be considered important and is dependent upon the physical attributes of the office design. Beacon deployment should be carefully planned and installed at strategic areas of the office or where the radio frequency dictates (`Zonith`, 2018). The open plan characteristics of Dakota’s London headquarters are typical of the financial sector. To accommodate this design the beacons are configured to facilitate virtual zoning within an open office space.

`[Figure 4.2](#chapter4.xhtml#fig4.2)` depicts Dakota’s beacon deployment on one of the floors within their London office. The beacons are located at strategic locations based on the physical attributes of the floor space and the criticality of the desks. It is important to note the receiving variance of each beacon can be independently controlled. This is considered important when designing specific zones, particularly if the zone is deemed sensitive and requires precise detection.

![image](images/fig4.2.jpg)

**Fig. 4.2.**Dakota 3<sup>rd</sup> floor beacon locations.

The power and sensitivity of each beacon is controlled through the communications server. This allows authorised staff to manipulate the monitoring environment to meet the needs of the security personnel or if the layout of the office changes.

### 4.2.2.*Data source*

The research data has been sourced directly through Dakota’s proximity solution and stored within a proprietary database that is located on the same server as the application software that controls the proximity security system.

It is evident that this research project is critically dependant on the source and accuracy of the data. Care has been taken to ensure that the data source accurately reflects the movement of staff and that the security personnel had adopted sufficient procedures to ensure the correct pass was issued to the contractors.

**Table 4.1.**Raw data from proximity solution.

![image](images/tab4.1.jpg)

*source*: Dakota

Once the pass has been issued and activated, human movement data is transmitted from the security pass into the Bluetooth beacons. The data is then sent via the ethernet structured cabling into the security database, which forms an integral part of the control server.

The raw data stream supplied by the Bluetooth proximity solution provides limited information. Whilst this is sufficient to monitor the position of an individual, it was not considered to contain enough detail to construct an effective mechanism to detect movement patterns.

The database contains data streams that are sent by each Bluetooth pass as it is initially detected within each zone. `[Table 4.1](#chapter4.xhtml#tab4.1)` depicts each field within a typical data stream.

Each cell plays a pivotal role when determining the pattern of movement and the time spent within each specified zone. There is no personal data transmitted within the data streams; the ‘User ID’ field determines which Bluetooth pass is being used.

The fields within the stream are constructed as follows:
