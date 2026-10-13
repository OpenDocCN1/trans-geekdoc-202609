
# Endpoint Security

Once you allow remote access, you lose the benefit of the physical access controls. Once you support remote connectivity, a hacker or intruder need no longer be physically present in a facility to launch an attack. Thus, remote access is a risk, and it lowers the overall security of an environment. To compensate for this security reduction, you should impose more rigid limitations in terms of authentication, authorization, and accounting.

As security is designed and deployed, consider the purpose or function of each device, especially clients and servers, as well as its location in one (or more) of the seven domains of a typical IT infrastructure (**Figure 4-7**). Then, consider which other devices will need to communicate with it. The more vulnerable the communications pathways, the more security you will need to impose.

![Figure 4-7 The seven domains of a typical IT infrastructure.](Images/9781284183658_CH04_FIGF07.png)

**Figure 4-7** The seven domains of a typical IT infrastructure.

If both endpoints are physically located in the same facility but the network pathway linking the devices involves any exterior segments, then the transaction demands greater security than a local-only communication. If the endpoints are geographically distant, then you need to use encrypted communications.

Remote and mobile devices are inherently riskier, as they are exposed to a greater number of potential threats. Inside the office, most threats are known, controlled, and monitored. But mobile and remote devices are potentially exposed to unknown, uncontrolled, and unmonitored situations, data, software, and users. A location outside of the organization's facility also means less strictly controlled physical access to the device.

## Technical Tip

Location-aware anti-theft software periodically collects IP information and any available location data and uploads it to a centralized site. If the owner of a system reports the item lost or stolen, this automatically posted data might help recover the device. However, if the thief reformats the hard drive, then the anti-theft software might be removed.

Changes to security and potential exposure to risks require additional protections on remote and mobile devices. These devices should continue to host antivirus scanners, anti-malware scanners, and firewalls. But they can also benefit from whole hard-drive encryption, multifactor authentication, and location-aware anti-theft software.

Remote and mobile devices are most likely to be out of compliance with security requirements, such as patch levels or application of security templates. A network access control (`NAC`) system can isolate and quarantine devices until they have installed all the necessary patches and updates.

Even with good host management—whether local, remote, or mobile—consider redundancy requirements. Is one of something enough or just enough to cause a significant problem when it goes offline?

## Redundancy

Security is not complete without adequately addressing preparedness. Redundancy is at the heart of preparedness. Can your organization survive downtime, blackouts, communication loss, server crashes, hard drive failure, floods, building eviction, virus infection, or any other potential threat? In most cases the ability to answer, "Yes, the organization can survive," depends on the level of preparedness of that organization.

Preparedness is also known as business-continuity planning or disaster-recovery planning. The purpose of such planning is to ensure that a strategy exists to recover from any realistic threat. The difference in the type of planning is based upon the severity and continuity or the threat. To determine what is needed in your organization, assess each serious threat to the stability and function of the organization. Then, develop procedures to respond to the threat. The procedure can focus on prevention or recovery (or a combination of both).

A core element throughout this form of planning is redundancy. [Redundancy](#30_glossary.xhtml#gloss388) is the act of avoiding single points of failure by building in multiple elements, pathways, or methods of accomplishing each mission-critical task. This is an area that is often ignored in security because it is viewed as an additional cost or expense to complete the exact same work or process.

Redundancy works in many ways. A [redundant array of inexpensive disks (`RAID`)](#30_glossary.xhtml#gloss389) is a form of redundancy for hard drives. `RAID` protects against drive failure. Hard drives are mechanical devices that are engineered to work for only a set amount of time, expressed as the mean time between failure (`MTBF`) rating in hours of use. All hard drives will eventually fail. Having a plan and sufficient backups can ease the problems of drive failure during a peak productivity period on the network, or worse, failing when no one recognized it has failed and no replacement is planned.

An [uninterruptable power supply (`UPS`)](#30_glossary.xhtml#gloss525) is a form of redundancy for power. `UPS` devices provide temporary power in the event of a brownout or blackout. A `UPS` can trigger a graceful shutdown to prevent loss of data if facility power is not restored promptly. These devices also offer power conditioning if there are issues with building power due to periodic lows and spikes, such as when an air conditioning unit cycles on. This is especially important in cities where there are imposed rolling brownouts or blackouts, or in older buildings, to prevent data loss and allow for maintenance of system integrity.

Redundancy can apply to communication pathways. Good network design requires at least two pathways to every important resource. Redundant links to and from clients may not be a strong need in most cases, but having multiple pathways to reach resources is often essential.

## Technical Tip

Try to avoid network designs that have a single point of failure; it is important to have redundant options to ensure that your mission-critical functions can take place. Keep in mind that bottlenecks are still likely to happen, even with redundant pathways. Monitor traffic and use levels on every segment across the network to look for trends toward reduced throughput or productivity over time. A bottleneck may at first be a slight hindrance to high performance and productivity, but it can later become a form of a `DoS` attack.

Redundant communication links for voice and data are also important considerations. Construction workers could accidentally dig in the wrong location and sever the primary wire bundle supporting the organization. Redundant lines to service providers could be the difference between a nuisance and a company-ending event. Do you want to leave the power of terminating your organization in the hands of outsiders?

Redundant firewalls, proxies, routers, switches, servers, and databases begin to make security and financial sense once each becomes an essential or mission-critical element of the IT infrastructure. Do not entrust the viability of an organization to any single component. Always have a secondary option or backup plan.

Failing to plan is planning to fail. Hardware failures, mistakes, accidents, or intentional damage will occur in every system in an organization at some point. No organization is immune. What differentiates successful businesses is whether an organization is prepared for the problem with a ready-to-use response solution, or will be caught off guard, resulting in scrambling to recover.
