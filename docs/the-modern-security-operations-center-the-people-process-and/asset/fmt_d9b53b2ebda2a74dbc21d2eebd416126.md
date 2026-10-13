
Another example of an ideal use of anomaly detection capability is to monitor home appliances that are being connected to the IoT. Imagine a thermostat connected to the network that periodically downloads small updates from the manufacturer’s website. An anomaly alarm should go off if this thermostat starts exporting large amounts of data from the corporate network. Anomaly detection could be combined with behavior detection, meaning the risk in the thermostat example could be increased if the thermostat also starts performing port scanning for the first time, indicating this IoT device is potentially being leveraged by an external party to survey the inside network. Once again, it is important to point out that anomaly detection isn’t always accurate. For this example, the IoT device might be downloading a very large firmware update or might have a new feature enabled that has it send large amounts of data to the vendor.

> **Note**
>
> To avoid false positives, you need to configure security tools to ignore devices that will trigger your security capabilities. For example, you will want to add a vulnerability scanner to an ignore list; otherwise, every time it performs a vulnerability scan, it will trigger reconnaissance alarms in your detection tools.

It is common at a security event to hear a vendor claim their security tool can do a lot more than the three detection capabilities I just covered. Hopefully, knowing how to boil capabilities down to their core concepts will help you understand the true value of tools you are considering for your environment. I point this out because it is absolutely critical to understand which capability you are evaluating so that you can understand what it protects, what it doesn’t protect, and how to maintain it for maximum return on investment.

## Best of Breed vs. Defense in Depth

What is the best approach for using the available security capabilities? Is it better to have one very strong capability, known as `best-of-breed capability`, or to layer different capabilities, known as a `defense-in-depth strategy`? Best practice is to layer different capabilities rather than using the same type of detection. For example, a firewall permits or denies traffic based on rules. Having multiple firewalls wouldn’t provide any additional defense against an exploit targeting a system over port 80 if all firewalls have port 80 open. What is more ideal is to have an IPS and some form of breach detection layered so that if the firewall permits the traffic, the IPS can analyze the traffic for exploitation. If the attack goes unnoticed, bypassing the firewall and IPS, the breach detection technology, such as an anomaly-based tool, can identify the unusual change to the target and flag it as being exploited. By following this strategy, an attacker has to beat different forms of detection in order to accomplish his or her goal. The more layers with different capabilities, the less likely an attacker will be successful. [Figure 1-5](#ch01.xhtml#ch01fig05) represents the concept of layering capabilities.

![FIGURE 1-5 Best of Breed vs. Defense in Depth](Images/01fig05.jpg)

**FIGURE 1-5** Best of Breed vs. Defense in Depth

> **Note**
>
> It is important to point out that purchasing multiple firewalls is not a bad investment. Different parts of your network will need their own firewall, hence would be their own string of technology capabilities that include a firewall. Each string of capabilities would be graded independently from the rest of the network’s capabilities, including other firewalls. An example of this is comparing the edge of a company’s network against the security within its private cloud or internal datacenter. It is ideal for organizations to have separate firewall, IPS, and breach solutions for the datacenter and the network edge.

### Evaluating Technology

The security market can be confusing with regard to understanding whether the technology you are considering is offering a best-of-breed option or a defense-in-depth option. Vendors often claim their stack of defense-in-depth technology is the best of breed based on how the different capabilities work together. There are resources such as Gartner Magic Quadrants that attempt to categorize a security product and compare multiple vendors within that category based on who they believe is the closest to best of breed. The results of some resources are not technically accurate either because the ranking is influenced by nontechnical data such as customer feedback or vendor financial endorsements or because the tools are tested subjectively. An example of the latter case is a vendor who sponsors a test and rigs the testing criteria in favor of its own product. I once saw testing results for the “IPS Category” show that one vendor had a 100% detection rate while others did not. After further reviewing the testing criteria, I found the test was based on searching for a customized signature that only the tool of the vendor sponsoring the test had enabled! This type of test is obviously not a representation of a real-world use case and is only done as a way to develop a report used to generate sales. My recommendation is to question any report that ranks technology based on the following items:

*   How is the testing performed?
*   Who set up the vendor technology?
*   Who conducted the test?
*   Is the latest version of each vendor technology being evaluated?
*   Has the vendor confirmed its tools were properly configured?
*   Is the test based on real-world situations and based on vendor-neutral concepts?
*   Are there nontechnical factors such as vendor sponsorship or other potential bias in the results?
*   Do the associated vendors agree with the results?
*   Were some vendors given access to the testing criteria before the tests were performed?

Basically, you are looking to see whether all tools were tested in a fair manner. I recommend to always question the results of these types of tests rather than trust them at face value. While I was employed for one security vendor that was involved with all of the leading third-party evaluation reports, I was shocked to find how much effort was required to participate with groups such as Gartner and NSS Labs (no longer in business). Effort included hundreds of hours of top engineering time, travel between testing facilities, providing hundreds of thousands of dollars of free equipment, countless hours involved with analyzing alpha/beta results, and responding to questions from the third-party evaluation team. There are smaller vendors with great technology that can’t endure the financial burden associated with some third-party tests, leading to poor results that are not truly accurate as to how the tool actually performs against competitive technology.

### Researching Technology

My recommendation regarding determining what is the best solution for your organization is to use a combination of external resources, align what you find to your business goals, and test. Testing can be challenging based on the capabilities involved as well as general performance concepts such as providing the promised traffic throughput when capabilities are enabled. One example of a common challenge security tools deal with is encrypted traffic. One workaround is having the capability of decrypting traffic so it can be evaluated by a security tool and encrypted before sending it on to its destination. This decryption/encryption process will impact performance and is important to consider as a tool is evaluated. I have seen performance losses as high as 60 to 80% when certain security capabilities are enabled. Make sure to start your testing criteria with how the tool should be sized for your needs and if your desired capabilities will still deliver the expected performance.
