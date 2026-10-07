# CCSP Certified Cloud Security Professional All-in-One Exam Guide
214

able to recognize these periods and maintain overall system health as the available
pool of resources is in flux.

# Backup and Restore of Host Configuration

As with any kind of data on any system, configuration data is extremely valuable and
should be an integral part of any backup and recovery operations in a data center. This
is area where it is imperative to closely follow the recommendations and advice
of the hardware vendors. For backups to work optimally with physical devices, vendors
need to expose APIs or services to allow for backup systems to capture configurations.
Any time like this is exposed to any services or utilities, there is an inher-
ent risk of unauthorized access, so a thorough understanding of what can be
exposed, as well as how it will be secured, is essential from the hardware vendor.

Depending on the cloud service model, the exposure of configuration data may also
eed to be negotiated between the cloud customer and cloud provider. This will largely
depend on contract and SLA requirements and should always be clearly defined as far
as roles and expectations for any data, as well as ensuring that systems exposing
configuration data are appropriately secured and isolated from other tenants or systems.

# Implementation of Network Security Controls

Much like with a traditional data center model, network security for a cloud data center
is also based on layered security and defense-in-depth principles. This is done through the
use of a variety of technologies covering servers, appliances, and software implementations.

# Firewalls

Firewalls control the flow of traffic in and out of networks based on rules configured on
them. Firewalls control the traffic flow typically between trusted and untrusted networks
by allowing certain ports to connect between defined networks segments, which can
a single IP address, a VLAN, or a range of IP addresses. They can be either hardware or
software implementations, depending on the needs, resources, and capabilities of the
environment. Whereas a traditional data center will rely heavily on hardware-based fire-
walls, within a cloud environment the use of virtual firewalls or host-based firewalls
is necessary. For the most part, a virtual firewall device operates the same as
hardware-based device. Regardless of whether a server is physical or virtualized, the
software-based firewalls that come as part of the operating system package from the
endor or as an additional package or third-party package operate in the same manner.
While, while host-based firewalls accomplish a high degree of protection, they are
not ideal compared to hardware-based or external firewalls. Having a firewall running
as software on a host will add additional load to that host and consume resources that
otherwise would be reserved for the application. From a security perspective, you also
run the risk of a compromised host allowing the attacker to disable or alter the firewall
running on the host. By having the firewall independent from the host, a compromised
host cannot be exposed further without the segregation.