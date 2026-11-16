
my wallet a little emptier.

Consider this story when you are trying to conceptualize disaster recovery and, hopefully, it will make the task a little easier.

## Teams and Responsibilities

Individuals involved in disaster recovery must deal with many things; when called to action, their activities focus on emergency response, assessing the damage, recovery operations, and restoration. Figure 8.8 illustrates an example of disaster recovery activities.

![](img/cd307d33c10f35ada49ea76811ef60ad_653_0.png)

FIGURE 8.8 Disaster Recovery Timeline

The recovery team has the necessary authority and responsibility to get the alternate site up and running. This site is used as a stand-in for the original site until full operations can be restored.

> **Caution**
> Physical security is of great importance after a disaster. Precautions such as guards, temporary fencing, and barriers should be deployed to prevent looting and vandalism.

### Recovery Strategy

When a disaster occurs, a recovery strategy is needed. A recovery strategy involves planning for failure by using methods of resiliency. Developing a successful recovery strategy requires the support of senior management. To judge the best strategy to recover from a given interruption, the team must evaluate and complete the following:

- Detailed documentation of all costs associated with each possible alternative
- Quoted cost estimates for any outside services that might be needed
- Written agreements with chosen vendors for all outside services
- Possible resumption strategies in the event of a complete loss of the facility
- Documentation of findings and conclusions as a report to management of chosen recovery strategy for feedback and approval

This information is used to determine the best course of action based on the analysis of data from the business impact analysis (BIA). With so much to consider, it is helpful to divide the organization’s recovery into specific areas, functions, or categories, such as the following:

- Business process recovery
- Facility and supply recovery
- User recovery
- Operations recovery

### Business Process Recovery

Business processes may be interrupted due to the loss of personnel, critical equipment, supplies, or office space; or from uprisings, such as strikes. Even if a facility is intact after a disaster, people are required and are an important part of the business process recovery.

Workflow diagrams and documents can assist with business process recovery by mapping relationships between critical functions to evaluate interdependencies. Often, a critical process cannot be done because a related process was left out of the workflow. For example, say that you bring in the hardware, software, electric supply, and a system engineer to restore a computerized business process; however, you do not have any network cables to connect the equipment. Now all the vendors are closed because of the storm, and no $5 networking cables are available. A process flow created before disaster strikes can identify what needs to be done and what parts and components will be needed. Building a workflow diagram allows an organization to examine the resources required for each step and the functions that are critical for continued business operations.

### Facility and Supply Recovery

Facility and supply interruptions can be caused by fire, loss of inventory, transportation or telecommunications problems, or even heating, ventilating, and air conditioning (HVAC) problems. An emergency operations center (EOC) must be established, and redundant services must be enabled for rapid recovery from interruptions. Many options are available, from a dedicated offsite facility, to agreements with other organizations for shared space, to the option of putting up a prefab building and leaving it empty as a type of cold backup site. The following sections examine some of these options.

### Subscription Services

Building and running data-processing facilities is expensive. Organizations typically opt instead to contract their EOC facility needs to a subscription service. The CISSP exam categorizes these subscription services as hot, warm, and cold sites.

A hot site is ready to be brought online quickly. It is fully configured and equipped with the same systems as the regular production site. It can be made operational within just a few hours. A hot site needs staff, data, and procedural documentation. Hot sites are a high-cost recovery option but can be justified when a short recovery time is required. A hot site subscription service involves a range of associated fees, including monthly cost, subscription fees, testing costs, and usage or activation fees. Contracts for hot sites need to be closely examined because some services charge extremely high activation fees to discourage subscribers from utilizing these facilities for anything less than a true disaster. To get an idea of the types of costs involved, www.drj.com reports that subscriptions for hot sites average 52 months in duration, and costs can be as high as $120,000 per month.

**Caution**

It's possible that during a disaster, one backup site might not be available. Many organizations therefore have a backup to a backup site. Such a site is known as a _tertiary site_.

Regardless of the fees involved, a hot site needs to be periodically tested to evaluate processing abilities as well as security. The physical security of a hot site should be at least at the same level as the security of the primary site. Finally, it is important to remember that a hot site is intended for short-term use only. With a subscriber-based service, there might be others in line for the same resource once your contract ends. An organization should have a plan to recover primary services quickly or move to a secondary location.

**Caution**

To decrease risk of sabotage and other potential disruptions, hot sites should not be externally identifiable.

For organizations that lack the funds to spend on a hot site or in situations where a short-term outage is acceptable, a _warm site_ might be acceptable. A warm site has data equipment and cables and is partially configured. It could be made operational within a few hours to a few days. The assumption with a warm site is that necessary computer equipment and software can be procured despite the disaster. Although a warm site might have some computer equipment installed, it is typically of lower processing power than at the primary site. The costs associated with a warm site are slightly lower than those of a hot site (see Figure 8.9).

![](img/cd307d33c10f35ada49ea76811ef60ad_657_0.png)

FIGURE 8.9 Recovery Site Availability Versus Cost

In situations where even longer outages are acceptable, a cold site might be the right choice. A cold site is basically an empty room with only rudimentary electrical power and computing capability. Although it might have a raised floor and some racks, it is nowhere near ready for use. It might take several weeks to a month to get the site operational. Cold sites are less ready than hot and warm sites, but the associated costs are also much lower than for hot or warm sites, averaging $2,000 per month or more.

### Tip

> Cold sites are a good choice for the recovery of noncritical services.

### Redundant Sites

The CISSP exam considers redundant sites to be sites owned by the organization. Although these sites might be either partially or totally configured, the CISSP exam does not typically expect you to know that level of detail. A redundant site is capable of handling all operations if another site fails. Although a redundant site can be expensive, it offers an organization fault tolerance, which is necessary for an organization that cannot withstand any downtime. If redundant sites are geographically dispersed, the possibility of more than one being damaged is reduced. For low- to medium-priority services, a distance of 10 to 20 miles from the primary site is considered acceptable. If the loss of services, for even a very short time, could cost the organization millions of dollars, the redundant site should be farther away. Therefore, redundant sites that are meant to support highly critical services should not be in the same geographic region or subject to the same types of natural disasters as the primary site.

An organization that has multiple sites dispersed in different regions of the world might choose to use multiple processing centers. This way, a branch in one area can act as backup for a branch in another area.

### Mobile Sites

Mobile sites are usually tractor-trailer rigs that have been converted into data-processing centers. These sites contain all the necessary equipment and are mobile, permitting transport to any business location quickly. Rigs can also be chained together to provide space for data processing and provide communication capabilities. Mobile units are a good choice for areas where no recovery facilities exist and are commonly used by the military and organizations such as large insurance agencies for immediate response during a disaster. They can get critical services up and running quickly and commonly provide tactical satellite services but do not work as a long-term solution.
