
# Internet Protocol (IP)

Internet protocol (IP) is responsible for addressing and routing your online requests. For a device to connect to the internet, it is first assigned an internet protocol address. When the internet was founded in the 1960s, the creators did not predict the need for billions and billions of IP addresses. Currently, we are switching between the fourth and sixth versions of the internet protocol. The fourth version (`IPv4`) uses 32 bits to store IP addresses. These 32 bits can hold `2^(32)` IP addresses. When multiplied out, `2^(32)` is actually 4,294,967,296 unique addresses. The newer version, `IPv6`, uses 128 bits, which can hold `2^(128)` IP addresses. This is equivalent to approximately 34,000,000,000,000,000,000,000,000,000,000,000,000 unique addresses.

Switching from `IPv4` to `IPv6` is an increase in the capacity by `2^(128) − 2^(32) = 2^(96)` times.

![Images](images/unfg05_00500.jpg)

This IP address is not permanently assigned to a user's device and can change at any time.

## Transmission Control Protocol

Transmission control protocol (`TCP`) is a protocol that defines how computers send packets of data to each other. Data traveling in the internet is broken down into small chunks of data called packets. `TCP` protocols guide the rules on how data are subdivided into packets before transmission.

| **Trailer** End of packet | **Data** | **Header:** Sender's IP address Receiver's IP address Packet # |
| --- | --- | --- |

## User Datagram Protocol

User datagram protocol (`UDP`) is a protocol that allows computer applications to send messages without checking for missing packets to save on time needed to retransmit missing packets. `UDP` is not as reliable as `TCP`, which does resend packets lost when transmitting.

## Fault Tolerance

![Images](images/unfg05_00600.jpg)

The internet has been engineered to be fault tolerant. If a system fails, a different path can be chosen between the sending computer and the receiving computer. Redundancy is the inclusion of extra paths that can mitigate the failure of a system if other components fail.

When a system can support failures and continue to function, it is called *fault tolerant*. This is important because elements can fail at any time, and fault tolerance allows users to continue to use the network.

In the diagram above, the paths various packets travel from computer D to computer K will not be the same. Because packets can travel different paths, they will likely arrive at the target computer out of order. The paths packets take are physically guided by routers.

If a packet is not received, the `TCP` protocol will request the sender to resend the missing packet. The IP addresses of both the sender and receiver are found in the header of the packet. When all packets are received, the packets are put together using the packet numbers found in the header to form the original binary message.

The process from computer D to computer K in the diagram above is called *end-to-end architecture*. This process involves the breaking down and assembling of the packets at each end. What happens to the packets in the middle is hidden from the user in an abstraction.

### Difference Between Internet and World Wide Web

The internet refers to the hardware. It is made up of the computers, cables, routers, and many more components that make up the entire network. It is a global decentralized network connecting millions of computers. The World Wide Web, in contrast, refers to the software used on the internet. `HTTP` is a protocol used by the World Wide Web to transmit data. The internet allows access to the World Wide Web, which is a system of linked pages, programs, and files.

## Efficiency of Solutions

Sequential computing is a computational model in which operations are performed in order one at a time. A sequential solution takes as long as the sum of all of the steps. In contrast, parallel computing involves breaking up a task into smaller, sequential pieces. Then those sequential pieces are all executed at the same time, each on its own processor or on a set of computers that have been networked together. A parallel solution takes at least as long as the longest branch in the program.

### Sequential Computing

- A problem is broken into discrete instructions.
- These instructions are executed one by one by a single computing device having a single central processing unit (`CPU`).

![Images](images/unfg05_00700.jpg)

A sequential computing solution takes as long as the sum of all its steps. In the above example, the total processing time is `4 + 1 + 6 + 2 + 3 + 1 + 5 + 1 = 23` seconds.

### Parallel Computing

- A problem is broken into discrete instructions.
- These instructions are executed concurrently by using multiple `CPU`s.

![Images](images/unfg05_00800.jpg)

A parallel computing solution takes as long as the longest of the tasks done in parallel. In the above example, the total processing time is 9 seconds.

![Images](images/unfg05_00900.jpg)

Parallel computing can consist of a parallel portion and a sequential portion. A parallel computing solution takes as long as its sequential tasks plus the longest of its parallel tasks. Most modern computers are parallel in architecture with multiple processors.

In the above example, the total processing time is `2 + 1 + 4 + 3 + 1 = 11` seconds.

![Images](images/unfg05_01000.jpg)

### Why Is Parallel Computing Used?

- In the real world, many things happen at the same time in different places concurrently.
- Parallel computing is needed for real-world simulations and modeling.

Some examples of complex computer simulations that benefit from parallel computing include weather forecasting, flight simulators, car crash modeling, seismic surveying, and so on. The "speedup" of a parallel solution is measured in the time to complete the task sequentially divided by the time to complete the task when done in parallel:

![Images](images/e0344-01.jpg)

The efficiency of the solution is still limited by the sequential portion. This means that at some point, adding parallel portions will no longer meaningfully increase efficiency.

Multiple processors can operate independently but share the same memory resources.

![Images](images/unfg05_01100.jpg)

### Distributed Computing

Many problems are so large and complex that it is impractical to solve them on a single computer, especially given limited computer memory. Distributed computing is a computational model in which multiple devices are used to run a program. Distributed computing allows problems to be solved that could not be solved on a single computer because of either the processing time or storage needs involved. Much larger problems can be solved more quickly using distributed computing than using a single computer.

Parallel computing uses a single computer with multiple processors. Distributed computing uses multiple computing devices to process those tasks.

![Images](images/unfg05_01200.jpg)

## Computer Systems and Networks Questions

**DIRECTIONS:** Each of the questions or incomplete statements below is followed by four suggested answers or completions. Select the one that is best in each case.

1. Which of the following is true about packets?

   (A) Packets will travel along the fastest path from the sending to receiving computer.
   (B) Packets can arrive at the receiving computer in a different order than sent by the sending computer.
   (C) When sent by a sending computer packets are guaranteed to arrive at the receiving computer.
   (D) One sending file will contain one packet.

2. Which characteristics of internet protocols have helped fuel the rapid growth of the internet? **Select two answers.**

   (A) Internet standards cannot be altered, so different companies can focus on development.
   (B) Internet protocols are open (nonproprietary).
