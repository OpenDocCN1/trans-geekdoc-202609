# IPv4 Network Address Planning (11.9.1)

Before you start subnetting, you should develop an IPv4 addressing schema for your entire network. You must determine how many subnets you need, how many hosts a particular subnet requires, what devices are part of the subnet, which parts of your network use private addresses and which use public, and many other factors. A good addressing scheme allows for growth. A good addressing scheme is also the sign of a good network administrator.

Planning IPv4 network subnets requires you to examine both the needs of an organization's network usage and how the subnets will be structured. Performing a network requirement study is the starting point. This means looking at the entire network—both the intranet and the DMZ—and determining how each area will be segmented. The address plan includes determining where address conservation is needed (usually in the DMZ) and where there is more flexibility (usually in the intranet).

Where address conservation is required, the plan should determine how many subnets are needed and how many hosts per subnet are needed. As discussed earlier, conservation is usually required for public IPv4 address space within the DMZ, and it can often be addressed by using VLSM.

Address conservation is usually less of an issue in the corporate intranet than in the DMZ. This is largely due to the fact that private IPv4 addressing, including 10.0.0.0/8, provides more than 16 million host IPv4 addresses.

For most organizations, private IPv4 addresses allow for more than enough internal (intranet) addresses. For many larger organizations and ISPs, even private IPv4 address space is not large enough to accommodate the internal needs. This is another reason organizations are transitioning to IPv6.

For intranets that use private IPv4 addresses and DMZs that use public IPv4 addresses, address planning and assignment are important.

An address plan should typically include a determination of the needs of each subnet in terms of size. How many hosts will there be per subnet? The address plan also needs to include how host addresses will be assigned, which hosts will require static IPv4 addresses, and which hosts can use DHCP for obtaining their addressing information. This will also help prevent duplication of addresses, while allowing for monitoring and management of addresses for performance and security reasons.

Knowing your IPv4 address requirements will help you determine the range, or ranges, of host addresses to implement and help ensure that there are enough addresses to cover your network needs.