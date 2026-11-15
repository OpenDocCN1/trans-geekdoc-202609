
## 7.3 Significance of Predictive Analytics in ITSM

ITSM as mentioned in Section 7.1 is highly data-driven. The ticketing system is used by IT service providers to address the service requests and other service-related aspects. The service request effort estimation and incident resolution workflow is depicted in Figure 7.3 and the overall incident management and ticket addressing process is depicted in Figure 7.7. The data generated as a result of these existing processes is enormous. The data can be structured or unstructured. To give an overview, Table 7.1 gives the number of tickets raised by 24 different accounts due to the occurrence of an incident/service request, etc. and the number of tickets resolved on the same day. The data is provided by one of the world's topmost service providers subjected to Non-Disclosure Agreement. An average of 111,000 tickets were raised per day as per the data from 2016. With the adoption of technology, this number will be on the rise.

How can ITSM benefit from predictive analytics? Ticketing is a day-to-day process in ITSM and Ticket Analytics can be used to draw comparisons like Resolution time by Technology, Ticket Volumes by Technology, Resolution time by Industry Domain, Ticket Volumes by Industry Domains, Account-wise Tickets resolved the same day, RCA, etc. The advantage of the same is that based on the analysis, the source of maximum tickets can be identified and it can be addressed, which type of tickets have

![](img/48ffcb334b2fea865a1f194394911123_197_0.png)

Figure 7.3 Service request effort estimation and incident resolution workflow.

### Table 7.1 Number of tickets raised by 24 accounts/day and closed tickets/day: data from a leading service provider.

| Account | Resolved same day | Total tickets |
|---|---|---|
| 1 | 6,552 | 14,364 |
| 12 | 5,436 | 8,316 |
| 3 | 3,632 | 36,100 |
| 4 | 2,603 | 2,696 |
| 5 | 2,532 | 7,672 |
| 6 | 2,390 | 5,251 |
| 7 | 1,610 | 6,452 |
| 8 | 1,423 | 3,208 |
| 9 | 1,383 | 3,598 |
| 10 | 1,197 | 2,522 |
| 11 | 713 | 909 |
| 12 | 331 | 3,232 |
| 13 | 273 | 3,266 |
| 14 | 273 | 1,287 |
| 15 | 254 | 2,412 |
| 16 | 250 | 2,172 |
| 17 | 220 | 396 |
| 18 | 191 | 460 |
| 19 | 158 | 3,244 |
| 20 | 65 | 2,618 |
| 21 | 29 | 1,174 |
| 22 | 16 | 60 |
| 23 | 3 | 23 |
| 24 | 1 | 180 |
| Total | 31,535 | 111,612 |

high resolution time can be identified and addressed. Predictive maintenance can be scheduled based on the identification of the root causes for incidents [13]. The insights like which industry domains will have major chunk of tickets can be mapped to the type of expertise required for the resolution and the amount of manpower. The time of arrival of tickets in different time zones and its severity and priority can also be mapped to the amount of manpower required for ticket resolution [14].

Figures 7.4 and 7.5 are the depiction of the analytics performed on the tickets. Priority of the raised tickets where the same is segregated based on

![](img/48ffcb334b2fea865a1f194394911123_199_0.png)

Figure 7.4 Ticket count vs. day of week based on priority of the tickets.

![](img/48ffcb334b2fea865a1f194394911123_199_1.png)

Figure 7.5 Ticket count vs time of the day in which it is logged based on priority of the tickets.

days of the week is performed. The time of the day is considered further and tickets logged with the same priority on different hours of the day are segregated to give an insight into the ticket occurrence rate during business hours [15].

Statistical analysis on tickets raised due to the occurrence of an incident is performed and Figure 7.6 depicts the result obtained. The number of tickets logged under different industry domains of each client of the IT Service industry is the first level of analysis performed and Figure 7.6 shows the result [16].

These are some of the sample analyses performed as a part of ticket analytics in the ITSM arena. So Ticket Analytics provides insight into ticket details and identifies potential root cause. Addressing the root cause brings down the incidents' volume and improves productivity. Reduced ticket volume and reduction in ticket resolution time is equal to improved client satisfaction. Further, delivery team gets insight to potential problem areas and can take proactive actions. An overall comparative analysis of productivity and ticket resolution time across accounts, industries, technologies, service areas will help in establishing performance baseline. This can improve day-to-day practices by addressing systemic issues. Furthermore, precision in capacity modeling and better review of SLA commitments are achieved. Higher accuracy in resolution, better insights into ticket arrival patterns and resolution time are all added advantages.

These can be beneficial to the enterprise since the ticket analytics have more to offer than the current practices like identification of the root causes

![](img/48ffcb334b2fea865a1f194394911123_200_0.png)

Figure 7.6 Industry domain by ticket volume.

through automated process, standardized productivity metrics, easy identification of tickets that can be moved to self-service and scope for automation. It will be easier to identify the accounts that need improvement and accounts that are giving good results. Also repetitive incidents can be identified and can be eliminated. As a forenote the ticket analytics benefits reaped by two different clients are presented further.

### Client 1

The questions raised by Client 1 was, “What will be the type of tickets that can be expected in the next 6 months and what will be the root cause of the majority of the tickets?” The insights from the ticket analytics performed on the tickets raised by the users of the services offered by Client 1 are as follows:

- five applications are responsible for the 54% of overall incidents
- In a 6-month period, three jobs failed more than 120 times
- The root cause of 137 failures in a single application is due to memory issue
- Data issue is the root cause of 60 failures in another application

Based on the insights corrective actions/decision were taken by the clients and was implemented. Issues in the areas of memory and data issues were addressed and preventive maintenance was performed. As a result, 25 applications moved to zero incident count and more productive work could be performed by the effort saved from avoiding these incidents. Issues in the areas of memory and data issues were addressed and preventive maintenance was performed.

### Client 2

The questions raised by Client 2 were, what is the current volume of tickets under different areas and what caused the incidents? The insights from the ticket analytics performed on the tickets raised by the users of the services offered by Client 2 are as follows:

- Higher than usual volume of ticket is generated by application under a specific area
- One of the major root causes for the occurrence of an incident is access related issues

Based on the insights corrective actions/decision were taken by the clients and were implemented. Application under the specific area was subjected to thorough code refactoring and testing to address the recurring issues. Access control procedures were further reviewed and a reduction of 5 and 2% of total incidents were achieved respectively. Also resource optimization was performed that leads to a total savings of $4000/month.

Since, these models developed learning and modify as per the real time trends and data, remodeling and refitting of the data are not required. The insights can be based on the present data. Also automating the process can aid in acquiring the required insights from the model as and when it is required. Therefore, predictive analytics can completely reshape the way enterprise reporting is happening.

## 7.4 Ticket Analytics: A Case Study

An enterprise handling accounts in the Healthcare sector need insight on reducing the effort required to close a ticket raised due to an incident as a part of service maintenance. Based on the requirement, machine learning based predictive model that can predict required effort for each category of the ticket is modeled. The questions addressed are 1) How can effort be reduced while resolving an incident? and 2) Can effort required to resolve each category of incidents be predicted?

To answer the questions, the data is collected in the form of tickets and each recorded ticket has different fields and the format of a sample ticket is depicted in Figure 7.7. The collected tickets as a raw data are depicted in Figure 7.8.

Figures 7.8 and 7.9 depict the entire methodology followed for this case study.

| INCIDENT ID | INC 1 |
|---|---|
| SEVERITY | HIGH |
| STATUS | CLOSED |
| OPEN TIME | 7/16/2015 6:55:25 AM |
| CLOSED TIME | 7/17/2015 8:31:47 AM |
| ASSIGNEE NAME | JOHN DOE |
| ASSIGNMENT GROUP | ACCOUNT MANAGEMENT |
| DESCRIPTION | USER SUCCESSFUL TO LOGIN BUT UNABLE TO ACCESS SAP |
| : | : |
| : | : |
| : | : |
| RESOLUTION | FIND USER XXX PERMISSION |
| ESTIMATED TIME TO RESOLVE | 30 MINS |
| RESOLUTION DATETIME | 7/17/2015 8:31:47 AM |

Figure 7.7 Sample ticket format.
