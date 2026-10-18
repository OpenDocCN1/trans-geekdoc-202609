
As you have seen, testing is an important component of CI. But where exactly do we run these tests? In modern app development, applications are usually built on top of platforms such as Kubernetes (on-prem or in the cloud), AWS, Azure, GCP, and so on. In addition, they are usually deployed in an automated fashion using IaC. These platforms greatly ease the burden of instantiating test environments for CI because you can simply use the existing IaC to deploy a test instance of the application on the same or other on-demand infrastructure. For many applications, you can do your development work by deploying parts of the application, or even the entire application, on your dev machine without the need for any external infrastructure. This flexibility enables each developer to create a different instance of the app for development, testing, and CI. Network infrastructure has traditionally been different from applications for the following reasons:

*   Network infrastructure is often very large, containing numerous interconnected nodes. Many times, it is not useful or practical to have a tiny test representation of a large network. Below a certain size, it is difficult to adequately test certain network behaviors such as redundancy or failover.

*   Virtual network functions (VNFs), the virtual versions of routers, switches, firewalls, and other devices, are usually delivered only as VM images. In comparison to containers, which most modern apps use, VMs are very resource intensive, needing large amounts of CPU and memory. This limits how much development work can effectively be done on your dev machine (that is, a laptop computer in many cases).

*   Until recently, VNFs were not generally available for many network node types. This meant that the only real way to have a representative test network was to buy racks of extra (expensive) hardware and software and devote them to a test environment. For many organizations this type of expenditure was not feasible.

*   Until very recently, the platforms for deploying simulated network topologies (for example, Cisco Modeling Labs, GNS3, EVE-NG) had inadequate scale, limited API support, and lack of VNF coverage. This meant that they were difficult to automate and could not simulate a network with enough fidelity to be useful.

Thankfully, many of these issues have been addressed. As demand for DevOps tools in IT has grown, the industry and community have responded with network simulation platforms that have capable APIs, have extensive VNF support, and can scale to very large simulations with hundreds of nodes. Modern network simulation platforms now enable the common DevOps scenario where a team of engineers can each be operating on their own instance of a network reference architecture without stepping on each other. This capability improves agility and enables teams to develop new infrastructure automation more rapidly.

In addition, because these platforms allow the dynamic reconfiguration of a network topology via API, the rigor of CI can now be applied to many different types of changes in the network that would have been difficult or impossible with static physical test networks, such as

*   Dynamically adding or removing nodes or sites

*   Dynamically reconfiguring links between nodes

*   Easily testing a topology against different OS versions

## Cisco Modeling Labs

One example of a modern network simulation platform is Cisco Modeling Labs (CML). At the core of CML is a KVM-based hypervisor capable of simulating many hundreds of nodes on a single instance. What makes a simulation platform like CML different from a traditional hypervisor is the management layer. The UI and API are built for, and focus on, the features needed to simulate network topologies, such as

*   A graphical drag-and-drop topology creation interface

*   The ability to make arbitrary connections between nodes

*   Create-update-delete for node types

*   Start-stop-wipe-delete for entire simulations or individual nodes

*   Rich API to create and manage simulations via automation

*   The ability to impair a connection for testing (that is, add latency, loss, jitter)

### Deployment Options

CML can be deployed on a bare metal server or as a VM on VMware. Deploying CML as a VM is an example of *nested virtualization*, where a hypervisor runs as a VM inside of another hypervisor (KVM on VMware, in this case). Although the VM deployment is useful for small or temporary CML deployments, nested virtualization is not the best option for scale or performance. If your goal is to get the most out of your hardware investment, a bare metal deployment is best because you do not incur the overhead of VMware. The crucial role of the simulation platform and the scale of simulations envisioned by this book would generally mean that a bare metal install is recommended.

### Scale Considerations

In a simulation platform like CML, the scale of network simulations that can be achieved is directly related to the amount of memory, CPU, and storage available on the server. There is no hard and fast rule for sizing a CML server because each different VNF requires varying amounts of CPU, memory, and storage. Therefore, for a given simulation, the resources required depend largely on the mix of VNFs used in the simulation as well as the overall configuration of each VNF. That said, our experience has shown that a server with 768GB of RAM, 40 CPU cores, and 2TB of storage can scale to 300 nodes on a single server. If this is not sufficient, multiple servers can be utilized.

### User Interface

At the heart of the CML UI is the workbench (see [Figure 5-7](#ch05.xhtml#ch5fig7)). It allows you to create arbitrary topologies such as the SD-WAN topology shown. From the workbench, you can

*   Start or stop the entire simulation or individual nodes

*   Get access to the console for any node

*   Edit the node startup configuration

![FIGURE 5-7 SD-WAN Simulation in CML Workbench](Images/05fig07.jpg)

FIGURE 5-7 SD-WAN Simulation in CML Workbench

CML comes preloaded with VNFs for various Cisco routers, switches, firewalls, and wireless LAN controllers, which makes it easy to get started building topologies right away. [Figure 5-8](#ch05.xhtml#ch5fig8) shows some of the VNFs available from the Add Nodes tab that can be added to the simulation by simply dragging and dropping the desired node into the workbench area.

![FIGURE 5-8 Adding Nodes in CML Workbench](Images/05fig08.jpg)

FIGURE 5-8 Adding Nodes in CML Workbench

After adding nodes to the simulation, you can then drag and drop links between nodes and create a complete network topology. After you start a simulation, you can connect to node consoles and configure devices via the UI if you choose. The CML Workbench is a nice way to allow humans to design network topologies using a drag-and-drop interface; however, when automating your testing with CI, it is not desirable to require a human for starting, stopping, or configuring devices in a simulation. For the purposes of this book, we are more interested in how we can leverage the simulation platform using IaC.

### Flexible VNF Support

While CML has rich support for Cisco VNFs built in, the platform does not limit you to only Cisco VNFs. Virtually any VNF (or any VM image, for that matter) capable of running on the KVM hypervisor can be added to CML. For instance, it is sometimes desirable to run network management platforms or other infrastructure tools *in the simulation* rather than on dedicated virtualization platforms. The advantage of such an approach is that the simulation can contain everything required to run the network, including any necessary management or controller platforms, without the need to run (and automate) these things on separate infrastructure. For something like CI, this means less work involved when bringing up a test environment.

### Infrastructure as Code Tools
