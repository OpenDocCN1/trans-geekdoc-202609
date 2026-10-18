
# What benefit does an SCM provide in the context of IaC?

First and foremost, it is used to track changes to the state of the network. If the desired state of your network is defined as IaC, then an SCM allows you to track any modifications to that desired state. This capability allows you to know what changed and who changed it. Also, the SCM enables continuous integration and continuous deployment (CI/CD) by providing a hook to run the various stages of a CI/CD pipeline. We look more in depth at CI/CD in [Chapter 5](#ch05.xhtml#ch5), “Continuous Integration/Continuous Deployment.”

IaC means that we need to represent our infrastructure as code, but what “code” typically defines infrastructure? In the scope of model-driven DevOps, the code is composed of the code for the automation tooling (for example, Ansible Playbooks, Jinja templates, Python code) and the textual “code” (for example, YAML files, JSON files) that contain the data that describes your network. This data is referred to as the source of truth (SoT), as illustrated in [Figure 4-1](#ch04.xhtml#ch4fig1).

![FIGURE 4-1 Infrastructure IaC](Images/04fig01.jpg)

FIGURE 4-1 Infrastructure IaC

## Source of Truth

The source of truth of a network is the central repository of all information that is needed to configure the network to a desired state. When constructed properly, your source of truth `is` your network. If your network were to be destroyed, you would be able to reconstitute the entire environment from the source of truth.

Unfortunately, `source of truth` is a misunderstood term in DevOps. Some might argue that the network itself is the source of truth. If that is the case, then it would be hard to do DevOps. If the network is the source of truth, then how do you check that there have been no changes to the source of truth? That would entail verifying that no device was touched or changed by human interaction. Then we need some central repository of state to check the network against, correct? That is our source of truth. Many operators fundamentally know this principle, but as Bob from ACME Corp discovered, it is a hard transition to make.

The opposite of your infrastructure being your source of truth is your infrastructure being immutable. That is, you never change your network; you simply replace it. This approach works well for cloud-native infrastructure such as Kubernetes in which you do a rolling replacement of an existing pod with an updated pod; however, it does not work quite as well for a physical network, except in cases of failure. One reason is that network infrastructure does not always respond well to a change. Sometimes changing an access control list (`ACL`) or a route causes some traffic perturbation. If the device has already failed or experienced network-affecting problems, however, it is often easier to just replace the device, push down the configuration, and troubleshoot the failed device in the laboratory.

Using a source of truth is also useful for provisioning a new device on the network. Clearly, a new device cannot hold its own “truth” because it is not yet configured. Therefore, the configuration must be created completely from the source of truth. So, both new devices and reconstructed devices due to failure should come from the source of truth. In fact, all operations are just a push of source of truth data into a device in whole or in part. An example of a partial push would be, rather than pushing the whole source of truth to a device, you might just want to update the NTP servers. In this case you would push out only that specific information instead of the entire configuration. In general, however, it is recommended that you push out all of the device’s data so that you can completely test and validate all data for each change. With most APIs, the platform or the individual device can figure out what the actual changes are and apply them appropriately. Looking at all automation operations as simply a push of data from your source of truth into your infrastructure can greatly simplify your IaC.

### Data Models

A large amount of information is needed to configure infrastructure. The scale and management of source of truth data are often not as important for applications or servers. Why is this? The reason is that building a single system is a well-defined procedure with relatively few permutations or interdependencies on other systems. Also, provisioning a system generally consists of configuring values like hostname, IPs, DNS, AAA, and packages. Each is a key/value pair (for example, `nameservers = 8.8.8.8, 8.8.4.4`) that defines the operation of that system, and there are relatively few of them.

This is not the case for a network element. If we take a standard 48-port top-of-rack (`ToR`) switch, each port could have a description, a state, a virtual local-area network (`VLAN`), a maximum transition unit (`MTU`), and so on. A single `ToR` could have hundreds of key/value pairs that dictate its operation. Multiply that across hundreds or even thousands of switches, and the number of key/value pairs grows rapidly. Collectively, these key/value pairs make up the source of truth of your network, and there can be a lot of them. In fact, the large source of truth makes automating networks a data management and manipulation problem rather than a programming problem.

Data models give us a way to organize the source of truth. A data model organizes the key/value pairs that define the network and describes the meaning of the key/value pairs in the data structure. The meaning of a key/value pair is defined by its relative position in the structure. As an example, let’s start with how we might represent BGP configuration using a data model.

[Figure 4-2](#ch04.xhtml#ch4fig2) examines how to set up a simple BGP peering using the CLI on Cisco IOS and Juniper JunOS. Basically, we have a bunch of values accompanied by a bunch of words using specific grammar to describe those values.

![FIGURE 4-2 BGP Configuration in IOS and JunOS](Images/04fig02.jpg)

FIGURE 4-2 BGP Configuration in IOS and JunOS

But the values, two autonomous system numbers (`ASNs`) and an IP address, are the only things that really matter, and they are the same in each, as [Figure 4-3](#ch04.xhtml#ch4fig3) illustrates.

![FIGURE 4-3 BGP Configuration Values](Images/04fig03.jpg)

FIGURE 4-3 BGP Configuration Values

In fact, the switch hardware does not care about the words that describe those values because they get stored in a config DB anyway. The words are what the engineers gave to the humans to communicate the meaning of those values to the hardware. After all, we can’t just specify two ASNs because we need to know which is the local and which is the remote. We could, however, communicate their meaning by order: for example, `<Local ASN>`, `<Peer ASN>`, `<Peer IP>`. This is basically a small data model. However, BGP gets `a lot` more complicated, so we need a more capable data model. [Figure 4-4](#ch04.xhtml#ch4fig4) is an example of the same data in the YANG OpenConfig (`OC`) data model rendered in YAML.

![FIGURE 4-4 How a Generic OC Model Is Converted to Native CLI](Images/04fig04.jpg)

FIGURE 4-4 How a Generic OC Model Is Converted to Native CLI

The data in the model on the left contains the information needed to deliver either of the syntax-specific versions—just add words. Yes, we still have words as tags in the model, but it normalizes those tags across vendors and gets rid of the grammar needed to specify how values relate to each other. We do not want to add words back if we can avoid doing so. Before we can send our common data model to a device, we first need to encode this data in a format suitable for transport over the network.

### Data Model Encoding Formats
