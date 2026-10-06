
## The Attraction of Cloud Computing for the Cybercriminal 173

none. First, consider where the data/evidence is located and what legal authority you have to seize that data. Because it belongs to your client does not necessarily mean you have the authority to download what you want, as data is subject to the privacy laws of the jurisdiction it is resident in and travels through, government entities such as the European Union (EU) place strict legal obligations on parties storing Personally Identifiable Information (PII) on a computer resident within the EU. This may include your own corporate data. Reading the EULA and seeking qualified legal advice as to the legality of removing data from the cloud is beneficial.

When placing any evidence before a court, it is the burden of the party producing evidence to account for it required by the judge or opposing counsel. This burden extends to proving the evidence was legally obtained and complies with the chain of custody. As this chapter evolves, we shall examine these issues and reveal why cloud-based evidence has not been known by most jurisdictions' courts.

A further thought considered throughout this chapter is using cloud-based evidence to corroborate evidence located from the physical scene (such as a corporate office). An example of this would be desktop computer logs showed that a suspect had a history of logging onto a specific cloud server and did so at the time cloud data was stolen.

## THE ATTRACTION OF CLOUD COMPUTING FOR THE CYBERCRINAL

Cloud computing is highly valued by the business community and increasingly by private users, the criminal community has also seen the benefits of using cloud-computing services. Cloud-computing services may be the target of a crime, used in the commission of a crime, or used to hold information generated during the commission of a crime. $5.6 Hacking as a service is now being offered in criminal communities, and automatic toolkits are developed to assist those without the technical capacity to target cloud infrastructure. $7 As the criminal community develops new strategies to attack cloud infrastructure and identifies new points of weakness, the value of attempted compromises can be expected to increase.

Should an incident such as a security breach occur in a cloud-computing environment, it should be of note to the investigator operating in this environment that incident management and follow-up investigations are more difficult than in a traditional cloud owned-and-operated system. $8 A Service

## Preserving Evidence from Cloud-Computing Platforms

Level Agreement (SLA) specifies the cloud provider's obligations, and should this not include forensic support, then the client may have restricted access to evidential material. Locating where in the data was stored at the point of the compromise further hinders effective response and efforts to seek legal redress through the courts. ^10 Not knowing exactly where the data was stored means there may be a need to identify which legal jurisdiction(s) are responsible for conducting an investigation.

The challenge for investigators from a law enforcement and legal perspective is to obtain, examine, and present evidence in a transparent manner, which a court can rely upon as being an accurate representation of the data stored in the cloud at time it was seized. ^5

## WHERE IS YOUR DIGITAL EVIDENCE LOCATED?

First, in the world—literally—is your evidence? Due to the dynamic nature of cloud computing, your evidence may be stored in several jurisdictions. While researching my doctoral thesis, I had the opportunity to speak to the chief security officer of a Silicon Valley-based IT provider (who cannot be identified due to the provisions of the ethics consent) specializing in cloud-computing storage. When asked where digital evidence I might seek in a cloud environment would be located, they stated that it could be located on one or all of the twenty-three data centers they have in fifteen different jurisdictions, and that they would not know the precise location until they looked. ^10 Obviously, if the CSP does not know where data is located, it will be very difficult for the cybercrime investigator to be able to work with this unless the EULA provides for the data to be stored in a specific jurisdiction.

So, where is your evidence? Cloud-computing data moves by the microsecond, and is not resident in one place, as the CSP will move data due to latency, cheap electricity providers, and other considerations. Although the EULA may be with a company based in California in the United States, the company may not store all or any of your client's data in that state.

A further complication is that cloud services may be made up of different companies, each providing specialist services. Some cloud services do not own the physical architecture they operate, but instead lease services from companies such as Amazon Web Services (AWS). This means that even asking the leasing CSP for specific architecture logs through a search warrant or court order will not be successful, as they do not have access to this evidence. The investigator may need to consider the practicalities of requesting a request

Lawful Seizure of Cloud Digital Evidence 175

or court order on the CSP leasing space on AWS for specific evidence and a separate order on AWS seeking architecture log evidence.

## LAWFUL SEIZURE OF CLOUD DIGITAL EVIDENCE

As the data you seek is on your client's cloud service, the presumption is that it can be accessed and downloaded any time required. The CSP will have considered the legality of data transfer within the jurisdictions they locate data centers; however, changes and legal precedents are created by the courts that do not always become public knowledge. While the EULA may provide guidance in this instance, privacy legislation in each jurisdiction will have priority over EULA. As mentioned, the EU is strict about the removal of PII from their jurisdiction and the data you seek to be identified as resident in the EU, it would be recommended to obtain specialist legal advice before downloading it, even if it is your client's data and you are operating with their consent. If the data you seek is on the suspect's cloud server, it would be very good to consider legal advice about your options.

To emphasize this point: A CSP interviewed for my thesis stated that there was an incident with a computer they had in France and they wanted to conduct remote diagnostics to determine what the problem was. From their California office they remotely logged onto the device that contained their corporate data, using their own computer, their own office, and their own staff, and transferred the contents to the United States for diagnostics. They were contacted by French authorities and told that they were committing a serious criminal offense under French law—the removal of PII without informed consent of French authorities—and that they should repeat the action, criminal charges would follow. The CSP concerned is one of the largest IT companies in the world and many readers would be familiar with it (their name cannot be disclosed due to the thesis ethics consent agreement). ^1

Another CSP interviewed that if they had problems with computers in the EU, they would fly their staff from London to examine it on site rather than run risk of violating EU law. When planning their flights, if they had the PII of EU citizens in their possession, they would examine the flight path of all flights they were traveling on carrying EU data to ensure that at no time did they leave the EU carrying PII subject to EU data and local privacy legislation. While this may seem extreme, these persons interviewed are very experienced operators in cloud-computing services and digital forensics and

176 Preserving Evidence from Cloud-Computing Platforms

a very strong understanding of the multijurisdictional nature of the laws and penalties in different countries and regions. ^10

To assist the investigators, legislators in some instances have created court orders that may be available in your jurisdiction where the court authorizes you to log onto a cloud server and download the required data. And while this may be legal in your jurisdiction, the search and seizure may actually need to take place across many foreign legal jurisdictions that may not recognize your domestic court order or search warrant unless there are mutual recognition agreements. To emphasize this: Would you go to the United States and obtain a search warrant or court order to search and seize data from a Microsoft Azure cloud service in Sydney, then fly to Australia, hand over your court order, and demand that Microsoft hand over the data? In effect, this is what you are doing.

So while you may have the protection of the law in your jurisdiction in this case, you would nevertheless be conducting a search and seizure of evidence in a foreign legal jurisdiction without local legal authorization. The inverse of this would be if an Australian company complained about being hacked by a foreign law enforcement service, and when challenged the foreign police office provided a local search warrant that they said authorized them to conduct the search and seizure in Australia. With the cloud, you are operating in potentially many legal jurisdictions and what may be legal in one jurisdiction may be a very serious criminal offense in another.

Should you be fortunate enough to have the CSP within your jurisdiction the process of securing evidence will be far easier, as you will be dealing with domestic court orders.

CPs interviewed for my doctoral research were unanimous in their opinion that if you want data from a cloud service and have any questions about the legality of obtaining it, first ask the CSP lawyers and they will provide prompt direction to assist you in continuing your investigations in a legal manner.

Lawyers and forensic examiners for the CSPs interviewed that they would appreciate the opportunity to assist when cloud data is required. This is to ensure that the correct evidence is obtained and the wording of the order is correct. One lawyer at a CSP interviewed stated:

We get a court order directing us to do things that do not make sense, direct us to breach another piece of legislation, or request only fraction of the information that is available. I suggest that any investigator, criminal or civil, who seeks information from a CSP to contact that
