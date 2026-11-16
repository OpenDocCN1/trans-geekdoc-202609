Multilevel: Every user has a valid need to know for some of the information that is on the system, and more than one classification level can be processed at the same time. Users must have formal access approval and must have signed NDAs for all information they will access on the system. Mandatory access controls provide a means of restricting access to files based on their sensitivity label. All users can access some data based on their need to know, clearance, and formal access approval.

# TABLE 4.2 Security Modes of Operation

| Mode | Dedicated | System High | Compartmented | Multilevel |
|---|---|---|---|---|
| Signed NDA | All | All | All | All |
| Clearance | All | All | All | Some |
| Approval | All | All | Some | Some |
| Need to know | All | Some | Some | Some |

> **Note**
> 
> The term *sensitivity or security labels* denotes high-security Mandatory access control (MAC)-based systems.

# Operating States

When systems are used to process and store sensitive information, there must be some agreed-on methods for how this will work. Generally, these concepts were developed to meet the requirements of handling sensitive government information with categories such as sensitive, secret, and top secret. The burden of handling this task can be placed on either administration or the system itself.

Generally, two designs are used: