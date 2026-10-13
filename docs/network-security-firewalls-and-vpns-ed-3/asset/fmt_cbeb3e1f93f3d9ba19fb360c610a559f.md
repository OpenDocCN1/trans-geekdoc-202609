
# VPN 管理最佳实践与策略制定

## 实施规划

If you fail to plan, you plan to fail. Document your implementation plan. You cannot simply find an open rack in the data center, run a cable, plug in a device, and keep your fingers crossed that it will work. Document your implementation and support plans. You will learn more about this later in the chapter.

## 监控 VPN 可用性

Monitoring the availability of the VPN can save time and aggravation. The typical (and worst) method to discover issues with your VPN is when users start calling for help. This can be particularly challenging when the callers include members of your organization’s senior management team. A corollary of Murphy’s Law may be, “The likelihood that a senior management team member will try to access the network over the VPN is directly proportional to the likelihood that the VPN will fail.” It is far better to alert senior management to temporary problems than for them to tell you that something is not working. Because VPNs are network components, you can generally use the same monitoring equipment that you use to monitor routers, switches, and other network gear.

### NOTE

Vendors can be very helpful when your equipment is down. Many technical and information security professionals believe they can fix anything, and sometimes they will work on a problem for long hours before finally reaching out to tech support. Although tech support can be problematic, especially when wading through the first level of support, the vendor can be invaluable when the problem is in the VPN equipment or software.

## 执行定期审查、备份和更新

Once you have your VPN deployed, review usage regularly. If you notice there are employees who do not use the VPN, you may want to remove their access. If you see employees who have multiple concurrent connections, you may have a security issue and should investigate further. Suspend access for anyone who will be unavailable or not allowed to access the VPN due to corporate travel outside the country or vacation.

Back up your VPN configuration regularly. This is a good practice for any network equipment, but in the event that your VPN hardware fails and needs replacement, you will need to be able to restore your last known working configuration quickly. Rebuilding a VPN configuration from the default settings can be a long and challenging task—not to mention making post-incident review meetings an unpleasant experience.

Patch regularly. Vendors typically release patches and updates to VPN code throughout the life of the product. These patches address security issues, fix bugs, or provide additional functionality. In an ideal environment, you will have a development VPN that you can use to test patches and updates. In most environments, however, you will not have the luxury of a development VPN and will have to test when you implement in production. In either circumstance, work closely with your vendor to make sure that you receive prompt notice of patches and updates. Establish an operational process and maintenance window to apply patches and updates in a timely fashion.

Your VPN solution may end up being a critical component of the organization’s business-continuity planning and disaster-recovery planning. In the event of an incident that prevents employees from getting to their work location, a VPN that provides work-from-home support is a key component of many recovery plans. Events such as earthquakes, snowstorms, tornadoes, floods, pandemics, and other natural disasters can make working remotely a viable alternative to standard operations.

This collection of VPN management best practices is meant to serve as the starting point for your successful VPN deployment. It is not meant to be comprehensive, but instead to offer some common practices and processes to help you with your VPN deployment. Depending on your VPN solution—as well as your environment, business requirements, and experiences—you may use every one of these suggestions or only a few of them. The key is to ensure that you are doing what works in your environment. If you need help, do not be afraid to reach out to your peers for advice and suggestions. Over time, you will develop your own set of best practices as you gain more experience as a security practitioner, and soon others may be asking you for advice.

## 制定 VPN 策略

If you are implementing or supporting a VPN solution, use a VPN policy to ensure that your users understand the requirements for computing on the VPN. A VPN policy is sometimes called a remote access policy, a term used when dial-up lines and modems were the primary means to access the network remotely.

Keep in mind that a VPN policy should be a part of your overall policy framework, not a standalone. If you try to develop your VPN policy in isolation from the overall policy framework, you may find that you are duplicating information, or potentially writing VPN policy that conflicts with other aspects of your overall security policy framework. For example, if you put a requirement in your VPN policy that user passwords must be 15 characters long but the password policy states that passwords have to be eight characters long, you will confuse end users.

The components of a solid VPN policy include:

*   **Introduction**—State the policy by name and tell how it fits into the organization’s policy framework.
*   **Purpose**—Describe the issues the policy addresses and how the policy should be used. Include references to any applicable governance, risk, or compliance issues, as well as any specific legal or regulatory requirements supported by the document.
*   **Scope/binding nature statement**—Describe the systems, networks, or people covered by the policy, and outline the penalties for not following the policy. The phrase “disciplinary action up to and including termination” is common in security policies.
*   **Definitions/acronyms**—Define technical terms or acronyms used in the policy. Readers of the policy may not be familiar with the terms or jargon used.
*   **Document**—Include the document creator, creation date, version, document status (e.g., draft, template, policy, and guidelines), as well as any version tracking information.
*   **Policy**—This is the actual policy language. Be very clear in this section, leaving as little open to interpretation as possible.
*   **Optional elements**
    *   **Summary**—If your policy is long, you may want to summarize it in a bulleted list at either the beginning or end of the policy. This provides employees a quick method to check for policy statements.
    *   **Roles and responsibilities**—If your document is lengthy, or you need to document who does what under the policy, include roles and responsibilities. For example, a policy dealing with infrastructure might include roles for the system manager, system architect, end user, developer, or other key people within the organization.

Some specific topics to include in your VPN policy are:

*   Restrict remote access to the organization’s VPN solution.
*   Prohibit split tunneling.
*   Define which classes of employee can access the network by VPN. This could include regular employees, vendors, contractors, and temps, or it could be restricted to only home office workers, depending on business requirements.
*   Define which types of VPN connections will be permitted.
*   Define authentication methods permitted.
*   Prohibit sharing of VPN credentials.
*   List the configuration requirements for remote hosts, including current virus protection, anti-malware, host-based intrusion detection system (HIDS), and a personal firewall. Some VPN solutions include the ability to check for these types of configurations.
*   Prohibit the use of noncompany equipment or, if personal systems may connect to the VPN, define the minimum standards for those connections.
*   Define required encryption levels for VPN connections.
