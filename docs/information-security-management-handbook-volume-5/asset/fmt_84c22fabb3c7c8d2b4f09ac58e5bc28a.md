
Keeping track of the collected data becomes more problematic in an open situation; relations may exist with third parties outside the system who use the information collected for other purposes.

# Applications

# RFID Application Types

There are many types of RFID applications, of which some of the most common are asset management, asset tracking, automated payment, and supply chain management. The key characteristic differentiating one RFID application from another is the purpose of identifying the tagged items. [Table 3.1](#9781466508507_epub_c03_r1.htm#table_3.1) lists reasons why an organization might want to identify an item and the general application type that best corresponds to those reasons.

Application types are not mutually exclusive; an implementation can combine elements of several application types. For example, both access control systems and sophisticated asset management systems include tracking features. Supply chain management is a tracking application that spans organizational boundaries and often includes process control and payment transactions.

Personnel responsible for designing and implementing RFID systems should understand what application types apply to their implementation so that they can select appropriate security controls. For example, the security controls needed to protect financial transactions in automated payment systems are different from those needed for tracking applications. The personnel should also understand that an adversary may leverage RFID technology for an unintended purpose. For example, a warehouse may use RFID technology to determine what items it has in its current inventory, but an adversary may use the same system to track an item’s whereabouts after it leaves the warehouse. In this case, an asset management system is later used to enable an unauthorized tracking application, perhaps used by an adversary to locate high-value targets.

**Table 3.1 RFID Application Types**

| *Identification Purpose* || *Application Type* |

| --- | --- |

| Determine the presence of an item || Asset management |

| Determine the location of an item || Tracking |

| Determine the source of an item || Authenticity verification |

| Ensure affiliated items are not separated || Matching |

| Correlate information with the item for decision-making || Process control |

| Authenticate a person (holding a tagged item) || Access control |

| Conduct a financial transaction || Automated payment |

# Risks

RFID technology enables an organization to significantly change its business processes to:

![](OEBPS/images/box.jpg) Increase its efficiency, resulting in lower costs

![](OEBPS/images/box.jpg) Increase its effectiveness, improving mission performance and making the organization more resilient and better able to assign accountability

![](OEBPS/images/box.jpg) Respond to customer requirements to use RFID technology to support supply chains and other applications

As described earlier, the RFID technology itself is complex, combining a number of different computing and communications technologies to achieve the desired objectives. Unfortunately, both change and complexity generate risk. For RFID implementations to be successful, organizations need to effectively manage that risk, which requires an understanding of its sources and its potential characteristics.

# Privacy Aspects

In relation to RFID, privacy and security are two sides of the same coin and require an approach in which they are both tackled together and it might be possible to include security safeguards that may have positive implications on privacy. The double-sidedness of privacy and security requires attention, since it deals with embedding privacy regulations in the standards that are being developed on the various aspects of the RFID system (tags, readers, middleware, and the back-end information systems).

RFID is a means for identification. This identification can be of products, services, or persons. In most cases, RFID tags are related to products. When, however, a person is correlated to specific products by means of a token, an index, or another pointer, the identified information becomes personal information (or information that enables the identification of a person). Due to the ‘enabling’ characteristics of RFID tags the threat to privacy is a major concern, for the general public, companies, and governments alike.

In [Figure 3.7](#9781466508507_epub_c03_r1.htm#fig_3.7), two direct privacy threats are identified: one in relation to the tag-reader system, and one in relation to the information that is collected and disseminated outside the tag-reader system.

The first kind of threat is the one that is most directly related to RFID. It focuses on the privacy implications of the tag-reader system itself. The second kind of threat relates to the use of data collected by means of an RFID system. The data that are disseminated by the tag-reader system may be collected in a database, for instance to monitor pallets in a supply chain management system. This kind of threat is not uniquely determined by the RFID system, but due to RFID the threats may be aggravated and have very specific dimensions.

![](OEBPS/images/fig_3.7.jpg)

![](OEBPS/images/line-2.jpg)

**Figure 3.7 RFID privacy threats**

# Privacy Threats within the Tag-Reader System

A tag may contain personal information. Passports, identity cards, and specific forms of public transport cards contain identifiable information. They may contain directly identifiable information on the card such as name and birth date. They also may contain data that functions as a key for a database in which personal information is stored. The privacy threat in the first case is obvious. In case a card holds indirectly identifiable information (a pointer that may refer to information about an identifiable person in a database), the privacy threat is indirectly present. Only when the intruder is able to link the pointer to the real person will privacy be invaded.

The unauthorized reading of tags is considered to be the most prominent privacy threat. Unauthorized reading is possible, especially in case of using UHF-based tags with reading ranges of approximately 20–30 ft.

Using tags to track persons is usually identified as being the second biggest threat to privacy. Tracking of persons via objects presupposes the linkage of identification data with individual track movements. Identification data can be acquired on the basis of electronic payments, loyalty cards, electronic ticket cards in public transport, etc. When a person carries an object that is linked to that person (such as a wristwatch) the data of the tag attached to the wristwatch may be used as identifiable information for the person carrying the wristwatch. It is possible to track the movements of this person by surveying the movement of the object for which the tag data are known. The information can for instance be used to retrieve personal preferences.

# Privacy Threats at the Backend of the RFID System

The threats mentioned above correlate directly with the RFID reader to tag communication and the direct use of these data. Most privacy threats, however, refer to the collection and subsequent use of information outside the tag-reader system. Tags with unique IDs can easily be associated with a person’s identity and smart cards with their own processing capacities may contain sensitive personal information.

There are three privacy threats related to the use of data outside the tag-reader system:

![](OEBPS/images/box.jpg) Using data for aggregating personal information

![](OEBPS/images/box.jpg) Using data for purposes other than originally specified

![](OEBPS/images/box.jpg) Using data to monitor specific behaviors
