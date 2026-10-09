+   - The maximum length of time until IT systems, IT infrastructure, and business processes affected by the cybersecurity incident or event is returned to normal business operation, after which significant negative impact may occur (recovery time objective [RTO])

For each IT asset (hardware and software, including virtualized assets) affected by the cybersecurity event, an evaluation will be made to determine the appropriate response and recovery actions, such as the following:

+   - Decommission and replace
- Reconfigure with enhancements (firmware updates, vendor patches, configuration changes)
- Reconfigure with no enhancements

Recognizing that the Company may not be able to complete the chosen recovery action in a timely manner in relation to the RTO, an alternative solution will be determined to enable a return to normal processing.

Data restoration is based on the activities outlined in the backup and recovery policies and procedures. The backup procedures apply to the following:

+   - Network devices—such as configurations, access control lists, and firmware
- Physical and virtual servers (DNS servers, email servers, FTP servers, application servers, database servers, web servers)—operating systems, application programs, and application data
- Networked file shares
- End user computing (desktops, laptops, tablets, mobile devices) and peripherals (such as printers and copy machines)
- Telephone and voice-mail systems

XYZ Manufacturing leverages a global backup management solution to manage the backup processing and monitoring of all IT assets connected to the environment. The backup solution is connected to a virtual storage area network (SAN) and supplemented by real-time disk imaging to an offsite facility for the highest-value IT assets and data. Moderate- and lower-value information and IT assets are backed up to electronic, removable media and stored at a secure offsite facility for the period of time defined by the backup and recovery policies and procedures. Backup method and frequency is based on the volume and frequency of information processing and the importance of the data or IT asset.

Restoration of data, software, and configurations is made using the global backup management solution. Prior to restoring data, software, and configurations to the live environment, the Company will conduct tests in the security sandbox against the backup media to determine if the cybersecurity event is present. Based on results, the Company may seek to leverage an older backup or execute the eradication techniques that were successfully employed in the production environment.

Communications related to a cybersecurity event are governed by the CIRP leadership team. Throughout recovery efforts, XYZ will communicate to the extent possible, and as required, with employees, stakeholders, regulators, or law enforcement through formal written and verbal communications (email, press releases, mass voicemail) that are structured to be informative, easy to understand, and transparent and that address the following: