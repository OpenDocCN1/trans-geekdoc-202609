
- Delete redundant/guest accounts
- Train system administrators (specific training)
- Train everybody (general training)
- Install virus-scanning software
- Install IDS/IPS and network-scanning tools

### Pricing/Costing a Countermeasure
You must consider many factors in evaluating countermeasures:

- **Product cost**—The price of the product will include its base price, the price of additional features, and costs associated with the service-level agreement or annual maintenance.
- **Implementation cost**—This refers to costs associated with changes to the infrastructure, construction, design, and training. An example is the cost of reinforcing a floor to install new equipment.
- **Compatibility cost**—The countermeasure must fit within (be compatible with) the overall structure. For example, a Windows-only organization would have to carefully consider the additional costs associated with training and interoperability when installing a Linux-based countermeasure.
- **Environmental cost**—If, for example, a countermeasure uses a lot of energy, you would need to consider whether your electric system would be able to provide that energy and to offset the excess heat it will generate.
- **Testing costs**—Testing does take time and money, but it is essential. Note, however, that testing also causes disruptions. You must consider all these as costs.
- **Productivity impact**—Many controls affect productivity. They might generate more calls to the help desk, slower response times for users, and so on.

> **TIP**
> Remember: The cost of a countermeasure is more than just the purchase price of a piece of technology.

## Monitor and Control Risk Response

The most important part of putting any control or countermeasure in place is making sure it meets its objectives. The last step in the risk management process is to monitor and control deployed countermeasures. A countermeasure is of no value if it does not actually provide its intended benefit.

When evaluating a countermeasure, first ask, “What problem is this countermeasure designed to solve?” (Your risk management plan should make this clear) Then ask, “Does this countermeasure solve this problem?” Here are some other points to consider:

- **Countermeasures might pose a new risk to the organization**—For example, implementing a countermeasure might create a false sense of security. Or the countermeasure itself might become a new point of failure on a critical system. Make sure you continuously monitor the countermeasure. Check it for compliance and good design, and perform regular maintenance.
- **You must perform certification and accreditation of countermeasure programs**—No system, control, or application should go into production without first going through a change control process. This also applies to changes to existing production systems. You must review all controls and countermeasures before performing an installation or making changes. Otherwise, administrators might misconfigure the system or make other errors.

- You must follow best practices and exercise due diligence—A good risk management program tells auditors that the company is taking a prudent and diligent approach to security risks. Due diligence is exercised by frequently evaluating whether countermeasures are performing as expected.

## Business Continuity Management

The way an organization responds to a disruption might well determine its survival. Poor planning greatly increases risk. With poor planning, an organization will not be able to respond appropriately and may be unable to return to normal operations. Planning for disruptions is part of business continuity management (BCM), which includes both of the following:

- **Business continuity plan (BCP)**—This plan contains the actions needed to keep critical business processes running after a disruption. Disruptions can be minor, such as a power outage, or major, such as weather damage that makes an organization’s building unusable.

- **Disaster recovery plan (DRP)**—This plan details the steps to recover from a disruption and restore the infrastructure necessary for normal business operations.

BCM includes not only BCP and DRP but also crisis management, incident response management, and risk management.

A disruption is a sudden unplanned event. It upsets an organization’s ability to provide critical business functions and causes great damage or loss. Examples of major disruptions include the following:

- **Extreme weather**—Superstorm Sandy in 2012 is one example.

- **Criminal activity**—This might include the theft of credit card numbers or other customer data.

- **Civil unrest/terrorist acts**—One example is the wave of violent protests in Missouri in 2014.

- **Operational**—An example is the electrical blackout in northern India in 2012, which affected nearly 9 percent of the world’s population.

- **Application failure**—Two examples are Amazon’s E2 cloud services crash in 2011 and Microsoft’s cloud services crash in 2014. Businesses that depended on these cloud services had to find other ways to perform business operations until service was restored.

The purpose of BCM is to mitigate incidents and ensure continuity of operations. When an incident does occur, however, the first priority must always be to ensure the safety of people. Containing the damage is secondary.

## Terminology

As a security professional, you must understand the following terms:

- **Business impact analysis (BIA)**—This is an analysis of the business to determine what kinds of events will have an impact on what systems. You should not limit the focus of the BIA to the information systems department and infrastructure; a business with a supply-chain disruption (warehouse fire, trucking strike, etc.) could easily suffer a major impact that has nothing to do with technology at all. Some scenarios will affect some departments, some will affect others, and a critical few will affect the entire business. You will learn more about BIA later in this chapter.

- **Critical business function (CBF)**—Once the BIA has identified the business systems that an incident will affect, you must rank the systems from most to least critical. That ranking determines whether the business can survive—and for how long—in the absence of a critical function.

- **Maximum tolerable downtime (MTD)**—MTD is the most time a business can survive without a particular critical system. A major disruption is any event that makes a CBF unavailable for longer than its MTD. Each of the disaster-planning and mitigation solutions must be able to recover CBFs within their MTDs. Systems and functions with the shortest MTDs are often the most critical. The next section covers this topic in more detail.

- **Recovery time objective (RTO)**—RTO is the timeframe for restoring a CBF. RTO must be shorter than or equal to the MTD.

- **Recovery point objective (RPO)**—Incidents can cause loss of data. You must calculate the amount of tolerable data loss for each business function. Recovery procedures must be able to meet the minimums defined here. If the business can afford to lose up to one day’s data, then nightly backups might be an acceptable solution. However, if the business must prevent all data loss, a redundant server or storage solution will be required.

- **Emergency operations center (EOC)**—The EOC is the place where the recovery team will meet and work during a disruption. Many businesses have more than one **emergency operations center**. One might be nearby—for use in the event of a building fire, for example. Another might be a significant distance away—for example, for use in the event of an earthquake or regional power outage.

Here is how MTD and RTO work together: Suppose power goes out in the data center. It takes six hours to move to the alternate site (RTO). The business can survive for nine hours without a functioning data center. At this point, there is an event but not yet an incident that you can define as a major disruption or disaster. If you expect power to return within three hours (MTD – RTO), the business might not declare a disaster in anticipation that activity will resume normally. However, if power is still out at the three-hour mark, it is time to declare a major disruption.

> **TIP**
> When considering how often devices may fail, there are a few other terms that you should know. Be familiar with these terms:
> - **Mean time to failure (MTTF)**—Average time a device will function before it fails.
> - **Mean time between failures (MTBF)**—Average time between failures (assuming that failures are repaired).
> - **Mean time to repair (MTTR)**—Average time it takes to repair a device and return it to service.
