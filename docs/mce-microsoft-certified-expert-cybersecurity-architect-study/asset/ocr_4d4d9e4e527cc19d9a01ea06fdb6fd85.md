through several gateways before they are routed to specific environments. After collecting data, exploits and attackers can be identified, and new patterns can be learned.

This Defender plan offers the following services when you enable Microsoft Defender for App Service:

+   - Defender for App Service assesses the resources covered by your App Service plan and generates security recommendations based on its findings. Use the detailed instructions in these recommendations to harden your App Service resources.

+   - Defender for App Service detects a multitude of threats to your App Service resources by monitoring the following:

+   - The VM instance in which your App Service is running and its management interface

+   - The requests and responses sent to and from your App Service apps

+   - The underlying sandboxes and VMs

+   - App Service internal logs—available thanks to the visibility that Azure has as a cloud provider

+   - In Defense for App Service, your App Service plan’s resources are assessed for security vulnerabilities, and security recommendations are generated based on the assessment results. Use the detailed instructions in the recommendations to harden your App Service plan’s resources.

Because of Defender’s cloud-native nature, it can identify attack methods that apply to multiple targets. For example, a single host might not be able to distinguish a distributed attack from small subsets of IP addresses crawling various hosts.

> It may be necessary to include the following requirements in a cloud-native policy for network and web traffic controls:

+   - Cloud-native policies might not allow hybrid connections to on-premises resources. A robust enterprise security policy sample would be a better reference should a hybrid connection prove necessary.

+   - Azure virtual networks and network security groups allow users to establish secure connections.

+   - By blocking or not enabling direct access to a virtual machine over SSH/RDP, the Windows Azure Firewall protects hosts against malicious network traffic.

+   - Services such as Azure Application Gateway, Web Application Firewall (WAF), and Azure DDoS Protection safeguard applications and ensure virtual machine availability.