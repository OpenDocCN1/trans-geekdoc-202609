
# CHAPTER 10: IoT Technology and Standards

The benefits are for common tools can be used across these similar frameworks, with technical standards ensuring that similar protocols, identity, authentication, and cyber defense mechanisms are in place.

The Industrial Internet of Things Connectivity Framework is a deeper document focused on the communication stacks to be used in building IoT systems. The goal of common communication mechanisms is to promote the sharing of data across different IoT systems—a clear benefit to electronic systems that could benefit from correlating their own data with additional inputs from other industrial systems.

## Open Connectivity Foundation (OCF)

The OCF is relevant to the security industry largely because of its size and prominent corporate membership, which gives it a better-than-even chance of shaping for a significant class of both residential and commercial devices. It was formed by the 2016 merger of the former Open Internet Consortium (OIC) and the AllSeen Alliance. The groups include companies such as HP, IBM, Cisco, Intel, Microsoft, Samsung, Qualcomm, GE Digital, and many other familiar electronics powerhouses. On the manufacturing side of the equations, this group is likely critical mass of IoT component and product makers. Of equal interest is not the prominent service and telecommunication providers who have joined forces with the OCF.

Intel formed the original OIC with the goal of connecting what it refers to the next 25 billion IoT devices. Its technical goal is to provide secure and reliable device discovery and connectivity across multiple OSs and platforms. OIC aims to deliver this by providing a comprehensive communication framework to enable emerging applications in all key vertical markets. Their IoT open-source project is a framework that provides tools to developers to realize this vision.

## Institute of Electrical and Electronics Engineers (IEEE)

The venerable IEEE has made an all-out effort to demonstrate its relevance to the IoT world and not lose out to newer standards organizations that could eclipse its central role in much of the standards initiatives that have taken place in the electronics industry over the last 50 years. To that end, the IEEE has launched a project titled “Standard for an Architectural Framework for the Internet of Things.” If this sounds like it is competing with the activities of several other organizations we've examined, it is. We are still in a period where multiple organizations are attempting to solve the same set of problems. With hundreds of thousands of degree engineers as individuals members,

- http://www.iiconsortium.org/IICF.htm

the IEEE has high visibility across every technology sector, and it is able to influence large numbers of new projects.

The IEEE has also gone back through its existing body of standards and reclassified many of them (e.g., Ethernet) as “Internet of Things related standards”—helpful, at the nuts and bolts level, but not breaking new ground. It also feels less modern in its approach to the open-source methods used by the newer organizations in this space. Prescriptive specifications will always be needed, but to be influential, open-source code turns standards into real projects much more.

## Related Organizations

Without meaning to disserve to any of the other organizations active in this area, there are too many consortia and industry groups to cover in anything less a full-length book. Further complicating matters, new organizations come into existence monthly and, unfortunately, disappear nearly the same rate.

Some of the organizations are focused on specific problems, such as data transport. The IoT group within the Organization for the Advancement of Structured Information Standards (OASIS), for example, has been working on the telemetry transport protocols as Advanced Message Queuing Protocol (AMQP) and Message Queuing Telemetry Transport (MQTT). While these protocols do not attempt or pretend to address the overall cybersecurity problem, they may find their way into security device applications and would need to be secured within the larger context of system integration or network.

The IETF is also very relevant to the ongoing development of IoT standards, such as the “IPv6 over low-power WPAN” standard that is implemented to extend IP networking to low-power devices. Securing a network using this protocol presents many of the same challenges as securing the IP networks in use today, and the standard does not speak to the layer of the problem.

## PROPRIETARY FRAMEWORKS

In practice, development frameworks and standards play similar roles. They provide consistent ways of doing things so that independent developers and manufacturers can leverage a body of intellectual property that lets them work faster and smart. They both drive solutions that enable innovators to end up with interoperable devices that can play in the same ecosystem in an end-user deployment.

Where they diverge is that standards are the product of strict sets of rules on how they are created, ratified, and developed.

## Google Weave

Google Weave is an example of a single-vendor offering. It is a platform that covers device registration, identity, communication, security updates, and user interaction. The goal of the framework is to provide a common language that all devices can use. In the case of access control, for example, a door lock can have defined states.

Weave stands out among competitors for IoT by virtue of built-in security features such as verified boot, data encryption, and availability of automated security patches. Weave also has a robust set for managing large numbers of devices—an essential aspect of enterprise.

The promise of unified vendor offerings like Weave is that they also tie you into all the other cloud services the company provides. In Google’s case, their significant investments in machine learning and AI could be compelling to one attempting to extract actionable intelligence from IoT data streams.

Often confused with Nest, Google Weave is intended to support connected devices broadly across the IoT space, not just home automation. In this sense, it appears to be a framework that may be a better fit for security applications.

## Thread Group

Backed by the popular IoT device Nest, the Thread Group was formed to create commonality to connect and control products in the home. As such, it is likely to be more relevant to residential security applications than to commercial. That said, there is often bleed from residential to small business applications, so we may find crossing that line for security and automation as well.

Like the other standards organizations, wireless communications between devices and the cloud are major focal points of the initiative. Thread's mesh communication technique makes it a natural for home automation applications but could serve equally well in larger facilities, depending on distance and construction techniques.

## Apple HomeKit

It would be remiss to discuss both Weave and Thread while leaving out a mention of Apple's HomeKit. That said, its relevance to commercial security appears limited. As its name implies, it is intended for residential applications where it ensures that all IoT can be seamlessly integrated into the iOS platform.

For commercial and industrial applications, however, it is not a good fit. Its authorization model for device interaction is too simple for the complexities of an enterprise or building automation project. Large commercial systems need role-based permission systems that allow administrators to adjust authorizations on a fine-grained basis. Systems designed for the home do not need this level of complexity because the number of users is small and are all, almost by definition, trusted individuals.
