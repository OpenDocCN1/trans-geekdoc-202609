
# Staging Environment Best Practices

A best practice in a staging environment is to allow the software to run for a set period of time. In the past, it has been up to seven days before deployment in a live environment. However, the SolarWinds breach of 2021 taught the cyber community just how crafty an attacker could be. They are aware of our best practices, and the malware that was used was set up to execute after 14 days in order to bypass a staging environment. As mentioned, it is another layer in defense in depth, and bad actors know how it is used.

## Guest Environments

Any large organization will occasionally have scenarios where there are visitors to the organization who need access to a guest sharing environment. These individuals are not employees of the organization and could be bringing unmanaged devices with them. For obvious security reasons, these assets should not be joined to a protected domain. For that reason alone, anyone who is coming to an organization to take a class or visit the campus should sign a terms of use agreement and have web access only for those unmanaged devices. If they are allowed to work on sensitive or classified materials, the following should be put in place:

*   Configure a timeout policy so authentication happens daily.
*   Create an automatically assigned classification type for any sensitive materials guests are touching.
*   Set up multifactor authentication (MFA) for guests.
*   Conduct reviews to validate permissions to corporate sites and information.

## VPC/Virtual Network

A `virtual private cloud (VPC)` is an on-demand highly secured cloud environment hosted inside a public cloud. Many VPC customers will use this type of setting for testing code, storing information, or hosting a website. Many cloud providers offer a VPC type of ecosystem and require a more secure connection.

A `virtual network (VNET)` is exactly what it sounds like. A VNET is where all devices, virtual machines, and datacenters are created and maintained with software. Most cloud providers offering VNET capabilities give customers a lot of control over their instances with IP addressing, subnets, routing tables, and firewall rules. This allows for scalability and efficiency.

## Availability Zone

Another element of defense in depth is the creation of availability zones. The purpose of an `availability zone` is to have highly available independent locations within regions for failover and redundancy. For major cloud providers, a single zone has multiple physical datacenters.

## Policies/Security Groups

`Policies` are high-level documents, developed by management, to transmit the overall strategy and philosophy of management to all employees. Senior management and process owners are responsible for the organization. Policies are a template in the sense that they apply guidance to the wishes of management. Policies detail, define, and specify what is expected from employees and how management intends to meet the needs of customers, employees, and stakeholders.

There are two basic ways in which policies can be developed. In some organizations, policy development starts at the top of the organization. This approach, known as top-down policy development, means that policies are pushed down from senior management to the lower layers of the company. The big advantage of top-down policy development is that it ensures that policy is aligned with the strategy and vision of senior management. A downside of such a process is that it requires a substantial amount of time to implement and may not fully address the operational concerns of average employees. An alternative approach would be to develop policy from the bottom up. The bottom-up approach to policy development addresses the concerns of average employees. The process starts with their input and concerns and builds on known risks that employees and managers of organizational groups have identified. The big downside is that the process may not always map well to senior management's strategy.

For modern cloud infrastructures, you can use tools such as `AWS Firewall Manager security group policies` to manage `Amazon Virtual Private Cloud` security groups for your organization in `AWS Organizations`. You can apply centrally controlled security group policies to your entire organization or to a select subset of your accounts and resources. You can monitor and manage the security group policies that are in use in your organization, with auditing and usage security group policies.

You should be able to identify specific types of policies before attempting the CASP+ exam. Some basic policy types include the following:

*   **Regulatory** A regulatory policy makes certain that the organization's standards are in accordance with local, state, and federal laws. Industries that make frequent use of these documents include healthcare, public utilities, refining, education, and federal agencies.
*   **Informative** An informative policy is not for enforcement; it is created to teach or help employees and others understand specific rules. The goal of informative policies is to inform employees or customers. An example of an informative policy for a retail store is that it has a 90-day cash return policy on items bought at the store if you keep your receipt.
*   **Advisory** An advisory policy is designed to ensure that all employees know the consequences of certain behavior and actions. An example of an advisory policy is an acceptable use policy (AUP). This policy may advise how the Internet can be used by employees and may disallow employees from visiting social networking or pornographic websites. The policy might state that employees found to be in violation of the policy could face disciplinary action, up to and including dismissal.

One specific type of policy in which a CASP+ should be interested is a company's security policy. The security policy is the document that dictates management's commitment to the use, operation, and security of information systems. You may think of this policy as only addressing logical security, but most security policies also look at physical controls. Physical security is an essential part of building a secure environment and a holistic security plan. The security policy specifies the role that security plays within a company. The security policy should be driven by business objectives. It must also meet all applicable laws and regulations. For example, you may want to monitor employees, but that doesn't mean placing CCTV in bathrooms or dressing rooms.

The security policy should be used as a basis to integrate security into all business functions and must be balanced in the sense that all organizations are looking for ways to implement adequate security without hindering productivity or violating laws. It's also important not to create an adversarial relationship with employees. Cost is an issue in that you cannot spend more on a security control than the value of the asset. Your job as a security professional is to play a key role in the implementation of security policies based on organizational requirements.

In your role as a security professional, look closely at the security policies that apply to you and your employees. As a CASP+, you should be able to compare and contrast security, privacy policies, and procedures based on organizational requirements. If you are tasked with reviewing security policies, consider how well policy maps to activity. Also, have you addressed all new technology?
