
Enterprises are occupied by a wide variety of users, including visitors, partners, contractors, employees, and privileged employees. Networking and security devices from multiple vendors interoperate using TNC-based technology to provide appropriate access for each user based on their identity, endpoint compliance, and role. Community involvement is critical. Examples, such as the open-source client `XSupplicant`, an `802.1x` client from the OpenSEA Alliance, that provides cross-platform support for user authentication and endpoint health checking, are very important to the long-term penetration of a market that has always been dominated by a few very large vendors and their proprietary frameworks. IETF adoption of TNC specifications was critical and recently achieved. It ensures industry-wide agreement on standards, providing consistency across products from leading networking and security vendors. TNC interfaces published as IETF RFCs (standards) enable dynamic differentiation and access control enforcement for a wide variety of users in mixed-use environments with the backing of a body considered to be one of the ultimate authorities for internet standards.

![](OEBPS/images/box.jpg) IF-TNCCS (called PB-TNC by the IETF) defines a standard way to perform a health check of a network endpoint such as a laptop computer or printer. If the endpoint is not healthy, it can be fixed or have its network access restricted.

![](OEBPS/images/box.jpg) IF-M (called PA-TNC by the IETF) defines a standard set of health checks that are commonly performed, such as checking firewall status.

![](OEBPS/images/box.jpg) IF-PEP enables provisioning of appropriate access for each user while ensuring consistent access control across wired and wireless connections.

So in the spirit of trying to put my “use cases where my mouth is,” I reached out to Dr. Steve Venema and Steve Hanna to make sure I have some practical information to go along with the high-level statements of how awesome IF-MAP is now and can be going forward. (Steve Hanna, personal communication, May 2010; and Dr. Steve Venema, personal communication, May 2010.)

# Employee Cubicle: Accessing a Production Network

## Business Requirements

An employee comes to work in the morning. When she badges into the building, the physical access control system publishes her location to a central clearinghouse, the Metadata Access Point (MAP). The employee authenticates to the enterprise network and her workstation is checked for compliance with corporate security policies. The policy server provisions appropriate access to network resources for the employee.

At the end of the day, the employee logs out of her PC and badges out to go home. The physical access control system publishes her location to the MAP and the MAP notifies the policy server that she has left the building. The policy server provisions a new access policy for the employee’s workstation, and the switch reassigns the workstation to a machine VLAN with restricted access for overnight maintenance and upkeep (such as backups or patch management).

Operational requirements:

User must be authenticated and authorized with identity management system and AAA services

User must be badged into building

Endpoint must be healthy

Antivirus software running and properly configured

Recent scan shows no malware

Personal firewall running and properly configured

Patches up-to-date

Behavior must be acceptable

No port scanning, sending spam

Coordination challenges:

Security infrastructure is complex, heterogeneous, and usually distributed

Getting worse

Large, real-time data flows between infrastructure components occur

Coordination between sensors, flow controllers, IDPs, etc. that are each interested in different patterns of events

Timely routing and reliability of delivery of this data is critical

TNC technology:

IF-PEP enables dynamic admission control and port-based network enforcement for both `802.1X`-authenticated and MAC-authenticated endpoints.

IF-TNCCS-SOH provides integration between TNC and Microsoft NAP, a NAP Agent is enabled to communicate endpoint health information to a TNC PDP without requiring a third-party supplicant.

The CESP defines mechanisms that ensure the ability to dynamically provision appropriate access for endpoints that lack a TNC client and are unable to authenticate to the network and/or demonstrate compliance with security requirements.

IF-MAP enables integration of information from additional security systems, adding behavioral intelligence to the access decision for managed and unmanaged endpoints, and integrating physical security with network access control.

# Guest Access: Conference Room

## Business Requirements

A guest visits the company using a laptop compliant with IETF/TNC standards. A health check against the guest endpoint ensures it complies with enterprise security policies before allowing it access to the corporate network. The guest is placed in a restricted VLAN, which provides access to appropriate resources, such as the Internet, but blocks access to the internal corporate subnets. His endpoint health and behavior are monitored throughout the duration of his connection to the network.

Operational Requirements:

Connection must be allowed via restricted VLAN

Endpoint must be healthy

Antivirus software must be running and properly configured

Recent scan shows no malware

Personal firewall running and properly configured

Patches up-to-date

Behavior must be acceptable

No port scanning, sending spam

TNC Technology:

IF-PEP enables provisioning of appropriate access for each user while ensuring consistent access control across wired and wireless connections.

IF-TNCCS and IF-IMC/IMV enable endpoint integrity checking; implementations can range from a full supplicant to a lightweight dissolving agent.

The CESP defines mechanisms that enable the application of access controls to endpoints without TNC clients that can’t provide identity or endpoint health information.

IF-MAP enables integration of network intelligence from additional security systems to add a behavioral consideration to the access decision.

# Contractor Access: Gone Rogue

A contractor arrives to perform maintenance on a protected system. The contractor successfully authenticates and his endpoint passes the health check; the policy server provisions access only to that system and he is also monitored. The contractor plugs in an EVDO device and makes a connection to the Internet, in violation of corporate policy. A network leak prevention sensor detects the leak and publishes a policy violation event to the MAP. The MAP notifies the policy server of the policy violation and the policy server terminates the contractor’s access privileges on the network. Comprehensive logging enables the corporate security team to identify what the contractor did and why access was restricted. TNC interfaces enable location, identity, endpoint health, and behavior-based access control decisions for users in an enterprise environment, along with detection and remediation of illicit activity such as data leakage by an endpoint.

Operational Requirements:

User must be authenticated and authorized with the identity management system (IDMS) and AAA services

Endpoint must be healthy

Antivirus software running and properly configured

Recent scan shows no malware

Personal firewall running and properly configured

Patches up-to-date

Behavior must be acceptable

No port scanning, sending spam

No violation of data leak prevention policy

TNC Technology:

TNC interfaces enable location, identity, endpoint health, and behavior-based access control decisions for users in an enterprise environment.

Detection and remediation of illicit activity, such as data leakage by an endpoint or unauthorized changes to network device configurations and correlation of physical security with network access privileges.
