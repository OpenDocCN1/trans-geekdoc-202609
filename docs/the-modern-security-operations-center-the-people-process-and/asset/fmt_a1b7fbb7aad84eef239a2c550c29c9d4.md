
*   Periodically test asset collection tools and manually evaluate the results to ensure that all asset collection is performed correctly.

*   Back up all results. Ideally, the backup should be sent to a different location than the primary database, such as a cloud storage option or offsite location that wouldn’t experience similar impact as the primary database if a natural disaster occurred.

## Asset Collection Challenges

The preceding suggested best practices are designed to ensure that you are capturing any new device that connects to the network as well as evaluating authorized devices that already have been approved network access. The following are some of the many reasons that a device might exist on the network yet not be part of the NAC asset list:

*   The NAC technology is not enabled on the port used to provide access.
*   Additional devices such as hubs or switches conceal the device.
*   An authorized device was modified while connected.
*   The device was connected prior to the NAC technology being enabled, or the device connected while the NAC technology was not functioning properly.

You also learned previously that most NAC technologies do not evaluate devices once they are connected to the network. This concept exposes a potential blind spot for collecting devices, which a network scanner will address as long as scanning is performed often and across the entire network.

## Asset Collection Value

As covered in the next section, step 2 of the vulnerability management service best practices includes planning for how to evaluate identified assets for vulnerabilities. Part of that process is to develop a list that shows the order of how assets you identified during step 1 are evaluated. That order is based on the value of the asset to the organization. Knowing the value of an asset allows critical systems to be prioritized regarding evaluation and the approach to mitigation. Proper planning cannot occur if asset value is not identified during the asset collection step.

The value of most assets can be generalized within a range, allowing the SOC to quickly determine where an asset should fit according to a risk assessment. A popular formula for calculating the value of an event is using the single loss expectancy (`SLE`). `SLE` is measured as the asset value (`AV`, or $) times the exposure factor (`EF`). `EF` is measured as the negative effect or impact that would be realized if the asset was lost. So essentially, you multiple the value of an asset by its exposure to get your expected value, shown as `SLE = $ × EF`. The top-valued systems will have the highest importance regarding remediation of identified vulnerabilities. [Chapter 3](#ch03.xhtml#ch03) covered risk management as a SOC service and the steps to follow to identify risk and to estimate the value of an asset.

## Asset Collection Master List

One final point to highlight is how you manage the master list of assets. Using different tools will produce a separate list of assets, which will have overlapping data. To address this, using an asset management platform that can accommodate for data deduplication, protect your asset lists, track when assets were last evaluated, and manage details such as when the device was identified and who owns it not only will be critical to having an up-to-date and accurate list of assets but also will assist with other steps in the vulnerability management process. Steps include understanding associating risk and value of an asset, meeting compliance requirements, and monitoring the status of the mitigation process, if applicable. Redundancy and data backup of the master list are equally important to prevent data being lost, which would prevent the vulnerability management program from performing properly.

### Step 2: Planning and Asset Evaluation

Having a reliable list of assets is important, but knowing how to use that list is equally important. For smaller networks, a SOC can quickly set up periodic network and vulnerability scanning to obtain acceptable results. A small business such as a gym or a home network typically has fewer than 20 devices on the network, which means very little planning needs to be done regarding what should be scanned. For larger networks, there are many different approaches that can be taken, but regardless of which approach chosen, you must develop a repeatable process to ensure that all devices are accounted for and that potential speedbumps to performing scanning are identified.

You need to consider the following factors that will impact the development of your vulnerability scanning program:

*   Number of network segments
*   Available bandwidth
*   Risk associated with scanning
*   Network access (remote, cloud, required VPN/routing, etc.)
*   Hours of operation
*   Peak workload hours
*   Required compliance for scanning
*   Asset value to organization
*   Asset evaluation method

#### Accessing Assets

When you are evaluating the previous list of factors, the first datapoint to focus on is availability to assets. Smaller networks consist of a few network subnets, making your vulnerability scanning design simple. Larger networks, however, can have thousands of subnets spread across the globe, which poses multiple challenges that must be addressed for a complete scan of the network to be accomplished. Therefore, having an accurate asset list is essential. An asset list can be used to map out asset locations. By knowing the asset location, the SOC can work with the IT team that supports the associated network regarding how access to devices can be obtained so devices can be properly scanned.

As covered previously, three possible options for scanning devices are host scanning, network scanning, and passive scanning. Each approach has deployment considerations as well as limitations based on the vendor being used. Starting with host scanning, this approach either uses software installed on the endpoints being evaluated or provides access rights (which should be read-only) to the vulnerability scanner so that it can log in to the devices and collect data. For either option, the vulnerability management system must be able to collect results from the endpoints. If you choose the agent-based option, you also need to consider how the agents are installed on endpoints. If administration rights are required to install the software, those rights must be granted. Also, any asset owner pushback must be considered.

> **Note**
>
> Many asset management tools include the ability to evaluate assets for vulnerabilities. This feature is typically a form of passive vulnerability scanning since collected data is compared against a database of known vulnerabilities (rather than specific assets being actively evaluated). An exception to this would be if the asset management tool has a built-in active host vulnerability scanner.

Network scanning must also have access to systems in order to perform its analysis. This means regardless of your scanning approach (host or network), you may encounter potential hurdles in the network that you must overcome. Some common network hurdles to plan for are as follows:

*   **Application-layer firewall:** An application-layer firewall will most likely inspect every packet before allowing it to be routed, unless special exceptions are configured. A typical vulnerability scan can generate thousands of connections in a short period, which can overload the application-layer firewall state table to state tracking mechanism.

    **Workaround:** Place scanners behind the firewall and use host scanning or allow list for scanning traffic from an authorized scanner if possible.
