
### Security

Every SOC will have specific requirements about who can and cannot access the operations room. Physical security must be part of the design of the SOC facility. Common options are door locks, common access card (`CAC`) or other smartcard door locks, video monitoring, and mantraps. Additional specialized lighting might be required for certain situations such as when visitors without clearance are in the SOC facility. I have been in SOCs that use police lights that are enabled when an uncleared person enters the SOC, notifying all analysts to turn off their monitors and the video wall screens while the person is present. External consultants can assist with meeting your SOC’s security requirements and can advise on any constraints such as if `CCTV` is not permitted within a country.

### Secure disposal

People will produce trash that contains sensitive information. A SOC must have requirements for properly shredding and disposing of such trash. Dumpster diving is still a threat to modern organizations. Purchasing professional trash disposable services or tools such as shredders to accommodate securing trash are some options that are available.

### Storage

Certain types of data might require specific storage requirements. For example, classified documents or forensic evidence will have to be bagged, tagged, and stored securely. Secure storage needs can require a safe or other storage options, perhaps even a specialized part of the building with armed guards, known as a sensitive compartmented information facility (`SCIF`), discussed further in the next section.

### Video wall

Some SOCs use monitors that enable multiple analysts to view the same data simultaneously. This means having view of multiple dashboards, which will likely need to be placed on a wall so all analysts can see the data. For example, a SOC responsible for various services may display the dashboard for a `SIEM` or other tools that take into consideration the SOC’s current event workload as well as external data such as global events. Having a centralized monitor allows each SOC analyst to focus on their own responsibility while always having a view of data that applies to the entire organization. To maximize collaboration, analysts should have access to the same data on their personal computer as well as be able to share what they are looking at on a shared video wall. Make sure that the video wall is high enough that all analysts can view it, including if somebody in the front row is taller than an analyst in the back row. Also consider future systems and analysts that might be added according to the capacity planning report. [Figure 2-10](#ch02.xhtml#ch02fig10) shows an example of how to design for these items.

![FIGURE 2-10 Video Wall Design Example](Images/02fig10.jpg)

**FIGURE 2-10** Video Wall Design Example

### Workstations

Consider the workspace for each SOC employee type. For example, should it include a phone, a desktop computer, and possibly a mounted flat-screen monitor? Some analysts will use a laptop only and not need a monitor, while other analysts will prefer having multiple monitors. Consider the number of cable holes that are available to help conceal power and network cables. The layout of how workstations will look can be divided into separate cubical work spaces, grouped into a large workspace, or possibly be a long table that permits open seating. Many office equipment manufactures offer options for configuring workspaces, which is ideal so that the SOC can adjust to the most effective layout (which fulfills the previously discussed `WBDG` recommendation for flexibility). Speak with an office furniture specialist for more information about workstation furniture options.

### Lockers

Providing lockers gives SOC personnel a secure means of storing personal items. There may even be compliance requirements, such as no mobile devices permitted in the SOC, that necessitate provision of lockers. Lockers can also be placed within personal workspaces for storing smaller personal items and documents.

A final factor to consider regarding the value impact of the SOC’s interior design is the SOC’s aesthetic appeal. Do not underestimate the value of a first impression when people walk through a functioning SOC. Many SOCs offer the option to provide tours, enabling non-SOC members to gain awareness of the SOC and its associated activities. Investing extra effort in aesthetics can capture additional funding and support from leadership, who may include the SOC in tours of the company to showcase the company’s investment in security.

#### SOC Rooms

Another SOC facilities design consideration is the different types of rooms within the facility. These rooms could reside within the SOC headquarters, at a remote branch office, or at some other type of remote facility such as an employee’s home office. The following are room types to consider for your SOC (all of which might not be required for your SOC):

*   **SOC operations room:** This is the SOC floor occupied by analysts and other SOC members doing their daily tasks. This room can house various dashboards, incident boards, analyst workspaces, and other operational items. If a video board is being used, this room should offer unrestricted line of sight to the video board for all SOC members. Make sure to size up versus down or you might end up with a crowded floor that ruins the atmosphere of the SOC workspace.

*   **War room/situation room:** This room is used for meetings. It should have collaboration technology such as videoconferencing and white boards. Most modern war rooms offer the capability to dial in remote users and share their desktop or the desktop of somebody in the room, so everybody is able to work from the same screen. One aspect to consider is the sensitivity of content that might be covered within the war room. Additional security measures might be required for the walls, door, or collaboration technology based on sensitivity needs.

*   **SOC manager’s office:** It is common to design the manager’s office with a clear view of the SOC floor and video wall as well as walls and a door to provide privacy when talking about sensitive topics.

*   **Digital forensics lab/clean room:** A room that is dedicated to digital forensics work requires additional security, including documenting any access. This is critical for tracking chain of custody, which requires that all access to evidence be documented; otherwise, it can be considered contaminated from a legal perspective. Other aspects of a digital forensics lab include additional power sources to keep equipment that has been obtained with the system’s power still on and plugged in so it doesn’t power off, fume hoods, space for large lab tables, and higher cleaning standards. Resources for better understanding how to set up a digital forensics lab/clean room include `ISO 31000` (risk management), the `ISO 14000` family (environmental management systems), the `ISO/IEC 27000` family (information security management systems), and `OHSAS 18000` (occupational health and safety), depending on the type of lab you are looking to build.
