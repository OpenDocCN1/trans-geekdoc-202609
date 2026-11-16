
- 6. Testing

- 7. Monitoring and maintenance

![](img/cd307d33c10f35ada49ea76811ef60ad_162_0.png)

FIGURE 3.8 BCP/DRP Process

We discuss project initiation and business impact analysis in this chapter and the other steps illustrated here in Chapter 8, “Security Operations.”

## Project Management and Initiation

Before the BCP process can begin, it is essential to have the support of senior management because they are responsible for setting the budget, determining the team leader, and starting the BCP process.

Without senior management support, you will not have funds to successfully complete the project, and your efforts will be at best marginally successful.

One way to gain their support is to prepare and present a seminar for them that overviews the risks the organization faces, identifies basic threats, and documents the costs of potential outages. This is a good time to remind them that, ultimately, they are legally responsible. Customers, shareholders, stockholders, or anyone else could bring civil suits against senior management if they feel the company has not practiced due care.

Senior management must choose a team leader. This individual must have enough credibility with senior management to influence them in regard to BCP results and recommendations. After the team leader is appointed, an action plan can be established, and the team can be assembled. Members of the team should include representatives from management, legal staff, recovery team leadership, the information security team, various business units, the networking team, and the physical security team. It is important to include asset owners and the individuals who would be responsible for executing the plan.

Next, you need to determine the project scope. A properly defined scope is of tremendous help in maximizing the effectiveness of a BCP. You cannot protect everything, and you really do not need to, either. For example, if you are planning for a company that has offices in California, Florida, New York, and North Dakota, you would not have contingency plans for hurricanes for all offices.

It is important to be sensitive to interoffice politics, which can derail the planning process. Another problem to avoid is project creep, which occurs when more and more items that were not part of the original project plan are added to it. Creep can delay completion of the project and can also cause it to run over budget.

A BCP benefits from adherence to traditional project plan phases. Issues such as resources (personnel and financial), time schedules, budget estimates, and any critical success factors must be managed. You can schedule an initial meeting to kick off the process.

Finally, the team can get to work. The team can expect to have a host of duties and responsibilities, including the following:

- Identifying regulatory and legal requirements that must be complied with
- Identifying all possible threats and risks
- Estimating the probability of these threats and correctly identifying the loss potential of each one
- Performing a BIA
- Outlining the priority order in which departments, systems, and processes must be up and running
- Developing procedures and outlining steps for resuming business functions following a disaster
- Assigning crisis situation tasks to employee roles or individuals
- Documenting plans, communicating plans to employees, and performing necessary training and drills

It’s important for everyone on the team to realize that the BCP is the most important corrective control the organization will have and to use the planning period as an opportunity to shape it. The BCP is more than just corrective controls; the BCP also needs to reflect preventive and detective controls:

- **Preventive controls**: Including controls to identify critical assets and prevent outages
- **Detective controls**: Including controls to alert the organization quickly in the event of outages or problems
- **Corrective controls**: Including controls to restore normal operations as quickly as possible

## Business Impact Analysis

The next task is to create the BIA, which measures the impact each type of disaster could have on critical or time-sensitive business functions. It is necessary to evaluate time as a metric, just as you would the importance of the function. For example, paying employees is not critical from the perspective of business activities, but if you don’t pay them on time, your company will likely go out of business because it will lose its employees.

Creating the BIA is an important step in the process because it involves considering all threats and the implications of those threats. For example, the city of Galveston, Texas, is on an island known to be prone to hurricanes. Although it might be winter in Galveston and the possibility of a hurricane is extremely low, planning can still take place to reduce the potential negative impact of a hurricane in the future. It is important to think through all possible disasters, assess the risks of those disasters, quantify the impacts, determine the potential losses, and identify and prioritize operations that would require disaster recovery planning in the event of those disasters.

The BIA must answer three vital questions:

- **What is most critical?**: Prioritization is important for determining what processes are most critical to the organization.
- **What is the longest outage the company can endure?**: The downtime estimation is performed to determine which processes must resume first, second, third, and so on and to determine which systems must be kept up and running.
- **What resources are required?**: Resource requirements must be identified and require correlation of system assets to business processes. For example, a generator can provide backup power but requires fuel to operate.

> **Note**
>
> Criticality prioritization is something that companies do all the time. Consider the last time you phoned your favorite computer vendor to order new equipment. How long were you placed on hold? Your call was probably answered within a few minutes. In contrast, how long was the wait the last time you phoned the same company to speak to the help desk? It was likely much longer.

The development of multiple scenarios should provide a clear picture of what is needed to continue operations in the event of a disaster. The team creating the BIA needs to look at the organization from many different angles and use information from a variety of sources. Different tools can be used to help gather data. Strohl Systems’ BIA Professional and SunGard’s Paragon software can automate portions of the data input and collection process. Although the CISSP exam will not require that you know the names of various tools, it does expect you to understand how the BIA creation process works, and it helps to know what tools are available.

Whether the BIA is created manually or with the assistance of tools, its completion will take some time. Any time individuals are studying processes, techniques, and procedures they are not familiar with, a learning curve is involved.

As you might be starting to realize, creating a BIA is no easy task. It requires not only knowledge of business processes but also a thorough understanding of the organization itself, including IT resources, individual business units, and the interrelationships between them. This task requires the support of senior management and the cooperation of IT personnel, business unit managers, and end users. The general steps within the BIA creation process are as follows:

- 1. Determine data-gathering techniques.
- 2. Gather BIA data.
- 3. Identify critical business functions and resources that support these functions.
- 4. Verify the completeness of data.
- 5. Establish the recovery time for operations.
- 6. Define recovery alternatives and costs.

> **Note**
> A vulnerability assessment is often included in a BIA. Although this assessment is conducted in much the same way as a risk assessment (see Chapter 7, “Security Assessment and Testing”), a vulnerability assessment focuses on providing information specifically for the business continuity plan.
