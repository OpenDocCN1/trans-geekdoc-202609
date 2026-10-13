

# Technical Vulnerability Management

## Responsibilities and Resource Definition

*   Define responsibilities, including vulnerability monitoring, vulnerability risk assessment, asset patch management, asset tracking, and any necessary coordination responsibilities
*   Define resources for identifying relevant technical vulnerabilities and improving security awareness
*   Define timelines for responding to potentially relevant technical vulnerabilities
*   Define the organization responsible for identifying relevant risks and taking action when potential technical weaknesses are discovered; these actions may include patching compromised systems or implementing other controls
*   Handle vulnerabilities through defined procedures. High-risk systems should be prioritized
*   Measure the risk of installing patches or other remedial measures
*   Define reference sources used to measure vulnerabilities
*   Establish an asset inventory
*   Create records for post-incident analysis

To ensure its efficiency and effectiveness, the technical vulnerability management process should be regularly monitored and evaluated.

## Standard Guidelines and Policy Formulation

`ISO 27002 A.12.6.1` is a reliable guideline, but the steps it contains may not all be applicable, depending on the focus of the vulnerability management service you provide. Regardless of the type of vulnerability management service you plan to provide, policies and procedures need to be formulated. Policies ensure project objectives are achieved, while procedures explain what needs to be done to meet all expectations set by the policy. `ISO 27002 A.12.6.1` contains many actions that need to be incorporated into vulnerability management policies and procedures, including defining who is responsible for what, how to handle vulnerabilities and the risks associated with remediation, how to identify assets, the priority order for handling vulnerabilities, and explicit recommendations for documenting everything in the vulnerability management lifecycle.

[Figure 9-1](#ch09.xhtml#ch09fig01) outlines the steps that can be taken to assess vulnerabilities, and next I will delve deeper into the mature vulnerability management service delivery procedure I recommend. For example, I noted that you need to collect assets, but how should you collect them? What tools and procedures should be used? The next section provides these details.

I divide the recommendations into four steps, which integrate guidelines such as `ISO 27002 A.12.6.1`:

**Step 1.** Asset Collection

**Step 2.** Planning and Asset Assessment

**Step 3.** Initiate Scanning

**Step 4.** Corrective Action or Risk Acceptance

My recommended vulnerability management service delivery procedure is briefly described as follows: First, collect information about what must be assessed. Next, use this data to formulate a plan, determining which systems, networks, or applications to prioritize and how to handle these targets. Once the plan is formulated, begin scanning through the target list for assessment. Based on the results, either take corrective action or accept the risk of not taking corrective action.

Let's take a closer look at what each of these four steps entails.

## Step 1: Asset Collection

Reviewing [Figure 9-1](#ch09.xhtml#ch09fig01), which represents vulnerability management best practices, and my recommended vulnerability management service delivery procedure, the first step focuses on collecting asset information. Before you begin executing any form of assessment service, you need to know what needs to be assessed. Having a complete and reliable asset inventory will simplify the entire vulnerability management project. *The most common reason for vulnerability management project failure is the gap between what is in the assessment scope and what actually exists on the network*.

Common tools introduced earlier in this chapter for establishing an asset inventory include:

*   **Network Scanners:** Run scans on network subnets and collect a list of identified devices
*   **Network Access Control:** Collect device lists as devices connect to the network
*   **Asset Management Tools:** Extract asset lists from tools that have already collected asset details

Many organizations use segmentation as a method to track assets and provide different scanning processes based on asset value in organizational subnets. For example, critical servers in a data center can be placed on a separate network segment, scanned more frequently than the general network. Engineers can often determine what a system is and where it is located by its IP address, based on how the network is segmented and how systems obtain IP addresses.

Throughout this book, you have seen examples of best practices for segmentation strategies based on device type. IoT devices and the like are associated with high risk and should be placed on a different network than systems containing sensitive data. Scanning the "IoT network segment" makes asset identification and collection expectations simpler and allows for additional detection, as rules can be formulated to respond to devices outside specific network ranges. A common example in organizations is dedicating a segment for IP phones. This is done to ensure segment resources are dedicated to IP phones, simplify phone traffic management, ensure the segment has appropriate bandwidth, and identify when non-phone devices connect to that segment. Investing in a robust and well-planned segmentation strategy yields many benefits, including simplified asset management and improved incident response for unauthorized devices.

### Asset Collection Best Practices

Summarizing best practices for asset identification, consider the following:

*   Use a NAC solution to monitor who and what connects to the network. This enables the SOC to collect new device information as devices connect to the network
*   If using a NAC solution, ensure the NAC technology is enabled in all parts of the network, including LAN, VPN, and wireless networks
*   If using a NAC solution, configure it to interpret unauthorized hubs, switches, and routers—that is, take actions such as blocking or moving them to another network when such devices are detected. Failure to do so will allow devices to connect without being identified by the NAC technology
*   If using a NAC solution, configure it to re-evaluate devices that have been connected to the network for a specific duration. The re-evaluation process can occur when a device forces a network reconnection, or by using a network scanner that does not require a network reconnection
*   Segment devices by device type and value to the organization. Examples include providing separate networks for mobile devices, IP phones, printers, servers, and IoT devices
*   If using a NAC solution, configure it to monitor devices attempting to connect to a network segment that do not conform to the expected device type
*   Regularly use network scanning to identify devices connected to the network, even if you are using NAC technology
*   Ensure network scanning covers all parts of the network and is performed regularly on a fixed schedule, so that scanning intervals between network segments are not too long
*   Use a centralized master list to consolidate information for all collected assets
*   Ensure any deduplication steps performed on the device master list do not remove assets that appear similar but are actually different

