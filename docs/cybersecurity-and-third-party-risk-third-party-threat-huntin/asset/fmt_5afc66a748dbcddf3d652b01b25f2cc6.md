
* Destruction options are incinerate, shred, pulverize, or disintegrate.

### SCSI drives
* Clear options are to overwrite the data.
* Purge is done by secure erase, degaussing, or disassemble and degaussing.
* Destruction options are incinerate, shred, pulverize, or disintegrate.

### Magnetic tapes
* Clear should be done by overwriting on a system similar to the one that originally recorded the data.
* Purge is best done by an NSA-approved degausser.
* Destruction involves either incineration or shredding.

### Optical disks (CD/DVDs)
* There is no Clear or Purge method that is acceptable.
* Destruction is the only acceptable method of sanitization and should be performed by using an optical disk grinder device, incineration, or large shredding machines.

### Flash media (USB thumb drives, memory cards, and solid-state drives)
* Overwrite is a possible Clear method for USB and memory cards. For a solid-state drive (SSD), the overwrite method must be validated using multiple overwrites.
* There is no accepted method of Purge for USB and memory sticks, but SSDs can use the secure erase functionality.
* Note that degaussing is not an approved method of destruction for flash media. However, all can be destroyed using incinerate, shred, pulverize, or disintegrate.

### Documents (paper)
* Incinerate: Material must be burned in an incinerator that is hot enough to burn all material, and it must be separated to ensure that all documents are incinerated.
* Shredding: Requires 1mm `×` 5mm cross-cut shred size (or smaller) to ensure it cannot be reassembled.

Verification of the sanitization and disposal of the hardware with sensitive data is an important step at KC Enterprises. There are contracts with some vendors that require an employee be present to validate this destruction. All disposal contractors for the company must be certified by the National Association of Information Destruction (NAID). The vendor must have a valid NAID certification at the time of the destruction.

Records of the sanitization are required. The information in the record must include what hardware was sanitized, when the activity occurred, the amount processed, the methodology used for sanitization, whether there was any verification performed, and the final disposition of the media.

Not all media for data storage can be cleared, purged, or destroyed the same way to ensure sanitization. Providing clear instructions for vendors on the expectations for each type will ensure data leakage from disposed equipment is as low a risk as possible.

The roles and responsibilities for data cleansing involve several stakeholders. The responsible and accountable party is the data owner who must ensure that the data is no longer available for use after sanitization. Consultation takes place with Cybersecurity and/or the Privacy staff on methodology and verification upon completion. Informational roles are often the Legal teams, so that any legal obligations on data destruction are confirmed as fulfilled.

## Conclusion
Offboarding a vendor is often a missed process in many companies. Whether this is due to the focus being on the important due diligence efforts for intake and ongoing or due to insufficient systems to alert and take action when a vendor is being terminated, the results are missed risks that can lead to a breach. Always ensure that data is destroyed through a digital COD. A paper COD is not sufficient for either legal recourse or as support that the data is really “gone.”

The termination of the contract also entails ensuring access is terminated. Physical and logical access are usually managed by different teams and require confirmation of their closing. Depending on the type of mechanism used for physical access, the activities need to be tracked and completed. The deletion of logs and user accounts should not be done until a prescribed period of time has elapsed; until it is reached, disabling the accounts and storage of logs is best in case of future needs.

Have a process and methodology defined for how data is to be cleared, purged, or destroyed, as different types of media require different methods for ensuring that the process is done correctly. This direction must also match with clear roles and responsibilities for holding data owners accountable and responsible to ensure that data is not left for others to leak when decommissioning equipment.

WileyPRE

# Chapter 10
## Securing the Cloud
The definition of the *cloud*, for this book, is anything outside the network that's controlled by the company. Using our example, KC Enterprises reviews the cybersecurity risk for their cloud anytime data classification meets the criteria, and the data is not going to be located in a KC data center. Referencing back to the earlier analogy, when your computer (containing your hard drive with sensitive data) is at your own home, it's sufficiently secure in your locked-up home. However, if you need to store it at your neighbor's house, your security risk changes. While you don't think he's going to do something bad, you want to be sure that he stores your computer (with the sensitive data) somewhere out of the normal traffic area in the home, preferably in a locked area of the house.

## Why Is the Cloud So Risky?
We view cloud risk the same way we view risk for data that is located outside our company's data centers or networks. KC's security due diligence process demonstrates this risk view, via its developed programs and processes that perform specific security control reviews to lower the risk with cloud deployments.

A vendor's cloud security can be optimized by using frameworks and patterns. Not only does this provide clarity to the vendor on what is expected on the cloud, but it also provides a way for their cloud security reviews to be more transparent. Understanding the Shared Responsibility Model (unlike in internal data centers, where everything is your responsibility, in a cloud deployment, some of the responsibilities are yours, some are the cloud provider's) is key to understanding the security risks posed by each of the different deployment models.

### Introduction to NIST Service Models
There are three service models described by the National Institute of Standards and Technology (NIST): Software-as-a-Service (SaaS), Platform-as-a-Service (PaaS), and Infrastructure-as-a-Service (IaaS). SaaS is a complete application that is managed and hosted by the vendor that a user accesses with a browser, mobile application, or an application connecting to the SaaS application. From a customer's perspective, in a SaaS deployment, the product is managed by the Cloud Service Provider (CSP) or vendor. Platform-as-a-Service (PaaS) is an application that abstracts and delivers an application, development environment, storage, processing, or an application programming interface (API) to provide the features of a SaaS, but the customer does not manage the servers, networks, or other infrastructure. A PaaS is different than an IaaS, which provides computing, network, or storage that the customer manages for quick deployment but does not include resources such as the operating system (OS) or applications. A SaaS deployment places much less responsibility on the vendor (i.e., cloud customer) than an IaaS, where the cloud provider has minimal security responsibility.

The Cloud Controls Matrix, by the Cloud Security Alliance ([cloudsecurityalliance.org](http://cloudsecurityalliance.org)), provides a great framework for not only how to secure your assets in the cloud, but it can be useful as a vendor assessment tool that deploys solutions in the cloud. This matrix can provide the level of controls required according to the deployment type (e.g., SaaS, PaaS, or IaaS).

### Vendor Cloud Security Reviews
