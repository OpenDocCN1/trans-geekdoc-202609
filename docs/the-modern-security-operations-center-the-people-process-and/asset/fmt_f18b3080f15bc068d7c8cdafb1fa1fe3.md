
\[Provide any requirements for reconnaissance activities. For gray or white penetration testing, certain reconnaissance action items can be removed, and the results can be provided to the penetration testing team. This will reduce the cost of the services based on the assumption that certain reconnaissance details are publicly available to real threats.\]

## Pentest Scanning Activities

\[Provide any requirements for evaluating targets.\]

| Scanning Test Deliverable Name | Scanning Test Deliverable Description |
| --- | --- |
| \[Response\] | \[Response\] |
| \[Response\] | \[Response\] |

## Gaining Access Activities

\[Provide what is permitted once access to a target is possible.\]

| Gaining Access Activity Name | Gaining Access Activity Description |
| --- | --- |
| \[Response\] | \[Response\] |
| \[Response\] | \[Response\] |

## Maintaining Access Activities

\[Provide what is permitted to maintain access on a target, commonly called establishing a foothold.\]

| Maintaining Access Activity Name | Maintaining Access Activity Description |
| --- | --- |
| \[Response\] | \[Response\] |
| \[Response\] | \[Response\] |

## Covering Tracks Activities

\[Provide what is within scope for removing the footprint caused during the previous exploitation steps.\]

| Covering Tracks Activity Name | Covering Tracks Activity Description |
| --- | --- |
| \[Response\] | \[Response\] |
| \[Response\] | \[Response\] |

## Pentest Analysis and Report Planning

\[Provide an explanation regarding what outcome and details need to be included in the penetration test final report. Include whether you require recommendations for risk reduction, screenshots of the tasks performed, or any other details regarding what will enable your organization to use the report to improve its security.\]

| Describe Plan for Analyzing and Reporting Pentest Results |
| --- |
| \[Response\] |

All compliance concepts covered in this chapter thus far have been based on policy and procedures, also known as an organization’s *process*. Processes are developed at the discretion of the organization and made into a required rule or policy that must be followed based on the details in any supporting procedure documentation. There are certain compliance requirements that are mandatory, regardless of whether the organization has a policy in place to enforce it. Not meeting certain types of required industry compliance can result in fines and other negative outcomes. The final topic for this chapter is reviewing required industry compliance.

### Industry Compliance

Most industries are required to comply with specific laws, standards, and/or regulations mandated by legislatures, government agencies, or industry regulators. Violations of government requirements are considered breaking the law, with repercussions ranging from fines to jail time. The reason behind government-enforced laws is to protect those that are associated with what is being protected, which is a good thing. For example, `HIPAA` protects people’s privacy, particularly their health information. If a company in the health care industry fails to protect its customers’ privacy, `HIPAA` requirements can be enforced by the government with strong repercussions if they are not followed, forcing the proper security controls to be put in place.

Industry services also have similar goals for enforcing requirements. Industry regulators don’t have the power to assess legal penalties; however, they have other methods to encourage following their policies, including reduction of allowed services as well as requirements for passing audits before services are reinstated. For example, most people have credit cards, which if stolen would mean access to their protected data. When people use credit cards to purchase something, they want to have confidence that their data will not be used inappropriately. If a company fails to protect a customer’s credit card data, it’s the buyer that is exposed to risk because their financial and other personal data is what is impacted.

Laws such as `HIPAA` as well as industry service requirements such as `PCI DSS` force any affected organization to enforce security best practices to protect the people that could be impacted by a breach, which in the example of `PCI DSS` are the customers using their credit cards with a vendor, and with `HIPAA` is the customers’ privacy. Without these requirements, organizations would use less secure methods to protect credit card and privacy data, causing an increase in data theft and a decrease in customer trust of the credit card network and health care services that contain private data.

#### Compliance Requirements

There are a handful of government-enforced laws and industry requirements that your organization will need to be aware of depending on your line of business. It is also good to know when other organizations must meet an industry compliance requirement as well. Looking back at the `PCI DSS` example, I once received my credit card receipt at a restaurant and saw that my entire credit card number was printed on it, a violation of `PCI DSS`. I could’ve reported the violation to my credit card company, but I chose to inform the manager about the issue. According to `PCI DSS`, the restaurant should have printed only the last four digits of my credit card number on the receipt, sufficient to enable me to confirm the credit card number charged is the one I used; however, the remaining data is protected. I recommend including considerations of who you do business with based on if they meet required industry compliance.

> **Note**
>
> It is common practice for organizations to advertise that they meet various types of industry compliance, with the goal of gaining the confidence of potential customers. For example, an organization might advertise on its website that it follows secured supply chain or software development best practices when creating products.

The following are some of the most commonly required industry compliance standards and laws that your organization, or organizations you do business with, may be required to follow:

*   **PCI:** The `PCI` Data Security Standards help protect the safety of that data. They set the operational and technical requirements for organizations accepting or processing payment transactions, and for software developers and manufacturers of applications and devices used in those transactions.

> **Note**
>
> Learn more about `PCI` at <https://www.pcisecuritystandards.org/pci_security/maintaining_payment_security>.
