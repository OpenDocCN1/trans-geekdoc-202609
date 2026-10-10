
# Performing a Quantitative Risk Analysis

In this exercise, you will identify a few assets within your organization and perform a risk assessment by identifying sample threats against the assets and then calculating the risk based on taking a quantitative approach.

1. On a new piece of paper, or using your favorite word processor, identify three different assets within your organization. Try to estimate the value of each asset.
2. Identify three or four threats against each asset, and then record the exposure factor (percent loss for the asset) if the threat were to occur.
3. Calculate the single loss expectancy (`SLE`) with each threat.
4. Determine the annual rate of occurrence (`ARO`) with each threat.
5. Calculate the annual loss expectancy (`ALE`) with each threat.

## CERTIFICATION OBJECTIVE 17.03

## Risk Mitigation Strategies

Once you have identified all of the threats against the assets and have determined the critical threats either through qualitative analysis or quantitative analysis, you next need to decide what your `risk response technique` will be. This is also known as the `risk mitigation strategy` and represents your `risk management strategy`. The following are approaches you can take to dealing with threats:

- **Mitigate the risk (mitigation)** The first way to deal with the risk is by mitigating it. Mitigation involves implementing a security control that protects the asset from the threat. For example, to protect against hard drive failure on the web server, you could purchase a `RAID` solution.
- **Accept the risk (acceptance)** Another way to handle the risk is to accept it. Accepting the risk means that you do not implement any solution to protect against the threat because you are satisfied that the chances of the threat occurring and the impact of the threat do not warrant the cost of implementing a security control.
- **Transfer the risk (transference)** You can also look at transferring the risk, which means you make the threat somebody else's problem! For example, you may get insurance that helps you recover from the security incident. It should be noted that for the exam, remember that an example of transferring risk is to obtain cybersecurity insurance.
- **Avoid the risk (risk avoidance)** Risk avoidance is the idea that whatever the activity is that puts you at risk, you decide not to perform that activity any more in order to avoid the risk. For example, you may be concerned that connecting highly sensitive systems to the main network, which is connected to the Internet, runs the risk of the sensitive systems being compromised. In this example, you could have the highly sensitive systems on an isolated network that is air gapped from your main network to avoid network or Internet-based attacks. An `air gap` means there is no connection between the two networks (important to know for the Security+ exam).
- **Deter the risk (deterrence)** A not-so-common approach to dealing with risk is to deter the risk. An example of deterring a risk is to threaten punishment (typically legal punishment) to anyone who attacks the asset—you are deterring the event from occurring.

![Image](exam.jpg)

**Be sure to know the risk mitigation strategies for the Security+ exam, especially that obtaining cybersecurity insurance is a way to transfer risk.**

You can follow a number of practices to help mitigate risk within your organization. The following is a list of common mitigation strategies you need to be familiar with for the Security+ certification exam:

- **Enforce technology security controls** The most common method to mitigate risk is to implement security controls such as `RAID`, high-availability solutions, firewalls, encryption, intrusion detection systems, honeypots, patching, and malicious software protection. Another common security control important to businesses is a `data loss prevention (DLP)` solution—typically software that allows the administrator to define rules for information that is considered confidential or sensitive and does not allow the information to be shared or copied.
- **Change management** Be sure to implement change management procedures in your business and to educate all employees on proper methods to make changes. For example, ensure that developers are making changes to web applications on a development machine and then publishing those changes to a test server to verify they are successful before copying them to the production server.
- **Incident management** A critical part of security is to ensure that you have an incident management team in place and have incident response procedures that the team follows when there is a security incident.
- **User rights and permissions reviews** Take time to assess the configuration of the systems on a regular basis. This includes reviewing the privileges (rights) given on a system and any permissions granted to data. Ensure that the principle of least privilege is being followed because this will help reduce the occurrence of security incidents.
- **Perform routine audits** A key part of having a secure environment is to perform routine audits. You can perform a number of different audits, from a configuration review to a vulnerability assessment.
- **Enforce policies and procedures** The security of your organization starts with having a good security policy in place and requiring that the policies and procedures are known. Having strict policies and procedures for employees to follow can help protect against data loss and theft. For example, you should ensure that all employees have a pass code configured on their mobile devices. That way, if a device is lost or stolen, it is harder for someone to get access to the information on the device.

### INSIDE THE EXAM

**Handling Risks**

For the Security+ exam, remember the different ways you can deal with risks. The most common method to deal with a risk is to mitigate it, meaning that you implement a control to reduce the risk.

Remember that there are other ways of handling risks; for example, you can accept a risk by doing nothing to control it, or you can transfer a risk by purchasing an insurance policy or cybersecurity insurance.

## EXERCISE 17-3

**Identifying Mitigation Techniques**

In this exercise, you will identify risk mitigation techniques associated with each threat identified in [Exercise 17-2](#ch17.xhtml#ch17exer2).

1. On a new piece of paper, or using your favorite word processor, record whether you will transfer the risk, mitigate the risk, or accept the risk for each threat.
2. Justify your reason for the mitigation approach you took with each threat.

## CERTIFICATION SUMMARY

In this chapter you learned the importance of performing a risk analysis and the two most common types of risk analysis—qualitative and quantitative. The following are some key points to remember from this chapter as you prepare for the Security+ certification exam:

- Risk analysis is the process of identifying assets, identifying the threats to those assets, and managing those threats.
- The risk analysis process has multiple phases—you must identify the assets, recognize the threats against the assets, determine probability and impact, prioritize the threats, identify the mitigation technique, and finally assess residual risks.
- The two main types of risk analysis are qualitative and quantitative risk analysis.
- Qualitative analysis does not calculate the dollar figures associated with risk but instead focuses on identifying the severity of a risk based on values you assign.
- Quantitative analysis focuses on calculating how much money is lost when a threat occurs. This helps identify whether the cost of the solution to protect the asset is justified.
