
## Asset Management
If a vendor does not know what assets it has, then it cannot control them. The KC analyst will ask for and get physical validation on a number of key security controls in this domain. Vendors must show the analyst a Configuration Management Database (CMDB) or some repository where asset records are stored and analyzed.

## Encryption
The analyst takes a keen eye to the encryption policy to ensure that it matches the level of encryption expected.

## Application Security
If the vendor creates software or applications for KC, then this section must be completed. Look at the vendor's secure development policy (if they have one) and find specific security controls in it.

## Supplier Management
As has been described in some breach examples, one of the best ways to avoid a fourth‐party breach is to ensure that your third parties have a robust vendor risk management program themselves. Review their TPRM policy and test them on how they perform due diligence, how often it occurs, and how deep they go. View some sample documents of their vendor due diligence. Focus on the fourth parties already known to be critical to the service that the vendor delivers to KC Enterprises.

## Network and Operations Security
This section can be one of the longer ones to complete and evidence can be challenging. The analyst reviews the high‐level policies for network security, logging and monitoring, backups and recovery, vulnerability management, and electronic communications (email). For network security, they must find evidence of network controls, segmentation, and Intrusion Detection/Prevention Systems (IDS/IPS) in use. The logging and monitoring should be managed by Security Information and Event Management (SIEM), and the vendor should be able to show its use.

## Human Resources Security
Insider threats are overlooked by many companies. We want to trust our team, but whether it's intentional or accidental, many breaches or security incidents are caused by end users. How a company screens and then educates its employees can answer if they are doing it the right way to lower the risk.

## Incident Management
When a breach or security incident occurs, and they do happen far too often, this section can help confirm that the third party has the correct policy and procedures in place.
Evidence presented by the vendor can be sensitive, so merely focus on attaining proof that they are following their process; seeing evidence of an actual security incident may be something their Legal team frowns upon. Rather than create a conflict, KC analysts are taught to look for ways to physically validate without placing the vendor in a situation that violates their own policies.

## Data Protection and Compliance
Compliance by vendors can be an important judge of how they are performing information security. Ask if an independent review of the vendor's cybersecurity is done periodically and ask to see the report. Oftentimes, the full report is restricted, so looking at the cover page and enough details to see dates and who performed the review is sufficient.

## Disaster Recovery and Business Continuity
This is an enterprise security assessment, so while the analyst determines if the vendor has a Disaster Recovery (DR) and Business Continuity (BC) plan for the service(s) offered to KC, there is a need to validate the enterprise, too, by asking questions appropriate to this domain.

## Physical and Environmental Security
Physical security is often overlooked. As the analyst approached the building and gained access, they were already evaluating some of the physical barriers. Another step is to walk around the building with a vendor escort. Check break rooms and mail rooms for unsecured assets like laptops or hard drives. Find the secure containers for shredding and confirm they are locked. Look for doors propped open or access points that do not make sense for security to be maintained. View the employees' desks or cubes for clean desk policy and unlocked unattended desktops.
The next sections depend on how data is deployed: Is it in a vendor data center, a co‐location, or a Cloud Service Provider (CSP)? The sections that do not apply are not graded.

## Data Center and Co‐location Facilities
If the vendor has their own data center or co‐location facility, then the following questions and physical security review must be conducted:
* What are the physical controls for entry into the data center?
* Examine perimeter security: How high is the fence around the data center?
* Is there a clear view all around the building or are some views obstructed?
* Where are the cameras located outside the facility and is the building not descriptive of being a data center? (It should not be clear this is where a company stores data.)
* Are there bollards protecting critical entrances?
* Did the security guards check identification properly?
Inside the data center requires more attention to detail by the KC analyst, who must review and note the following:
* Is the data center partitioned and is there sufficient camera coverage to see down every aisle and corner?
* How much reserve fuel does the physical plant have (e.g., heating, ventilation, and air‐conditioning [HVAC]; backup power; Uninterruptible Power Supply [UPS provides emergency power]; generators)?
* Does the facility have at least two fuel suppliers in case of a shortage?
* What type of fire suppression system is used and how often is it tested?
Speaking of testing, the vendor must demonstrate through logs that they test the physical plant systems like backup power, generators, and batteries. The analyst must validate if doors are propped open and if the loading dock is segmented from the main data center floor. They also check around the data center's floor for cabinets left unlocked, non‐vendor personnel walking unescorted, or if the area is untidy and not maintained properly.

## CSP Security
We cover more information about how KC secures cloud data deployments later, but for an on‐site assessment, the physical review is not conducted. CSPs will not allow tours of their facilities; however, the big three (Google, AWS, and Azure) run top‐notch physical security. The focus for the KC analyst in this on‐site assessment is the logical security in the cloud.
Access controls into the cloud are a top priority. Is MFA turned on for administrators and can they demonstrate it? Access management should be able to show how accounts are provisioned and deprovisioned, and it should be noted if the developers and administrators have special access into the system.
Data security is critical, so there must be several physical validation steps taken. First, vendors must be able to show that encryption is enforced and at what level. The vendor must demonstrate that the lower levels (i.e., testing and development) do not contain production or sensitive data. They must also be able to note where the encryption keys are stored and how access to them is managed.
If the application the vendor is deploying is internet‐facing, an analyst will ask if they run a Web Application Firewall (WAF), who manages it, and where the logs are monitored. Because a cloud deployment is another instance of the vendor's network, analysts look at and validate all the normal security controls in their cloud: IDS/IPS, DLP, a SIEM, and firewalls.
Upon completion of all the survey's domains, the analyst wraps up with a discussion of any outstanding items the vendor needs to produce. Owners are assigned and dates are set for providing any of this follow‐up information. The analyst can discuss with the vendor any preliminary findings or gaps. This is part of the partnership with the third party and not a surprise game to set them up for failure. This information provides them with some preparation of what gaps they will be called on to remediate.

### Reporting Phase
