
# How do we develop an architecture when we are saying that we need to automate everything on our network?

To answer this question, we dig back a couple of chapters to how we organize our source of truth and combine this with the origins of DevOps: application development. Specifically, we look at each part of the configuration (for example, BGP) as a service, or “application,” and maintain it as such.

Each of these “applications” maps onto one of the OpenConfig data models. When taken together as a whole, these applications configure the entire device as illustrated in [Figure 6-3](#ch06.xhtml#ch6fig3).

![FIGURE 6-3 Network as an Application](Images/06fig03.jpg)

FIGURE 6-3 Network as an Application

To use slightly different wording, each service can be thought of as a microservice used in modern application development. Each microservice is configured and run separately to provide a specific service to the overall application (for example, routing). Each of the microservices must be kept in sync, however, for the overall application to function properly. We get into how we validate the data for these services later in this chapter.

Defining our architecture as a grouping of services is how we go about creating the architecture for our reference implementation, since many organizations will be in the same situation. We start with the physical architecture of a corporate network with a headquarters and two remote sites shown in [Figure 6-4](#ch06.xhtml#ch6fig4); then we overlay this service architecture on top to develop our CI/CD pipeline.

![FIGURE 6-4 Reference Architecture](Images/06fig04.jpg)

FIGURE 6-4 Reference Architecture

This physical network is organized by the sites and geographical regions shown in [Figure 6-5](#ch06.xhtml#ch6fig5).

![FIGURE 6-5 Organizational Hierarchy](Images/06fig05.jpg)

FIGURE 6-5 Organizational Hierarchy

This hierarchy is important to how the source of truth data is organized and where specific pieces of information need to be placed later.

## Consistency

This topology is representative of many enterprise networks, just on a smaller scale. It helps to illustrate an important aspect of network design that enables large-scale automation: consistency enables scalability. Even in this two-site topology, for example, configuring Site 1 differently than Site 2 doubles the complexity of that part of your network. This complexity continues to grow as sites are added. Therefore, it is important to make a site template such that each site is the same configuration, just with different local parameters (for example, network addresses). Keeping the configuration consistent across sites makes provisioning new sites easier and ongoing maintenance less onerous. It also aids in simulation and testing, as you see a bit later in this chapter.

## Simulation

The next phase of our journey is simulation. Simulation is important because it provides a network on which to develop automation. At a higher level, we are talking about the need for a test network. As we discussed earlier in the book, however, the cost of test networks can be prohibitive in many organizations. Simulation provides the ability to create several networks that can be used by different developers and/or different development environments without needing to purchase large amounts of hardware. The ability to simulate a production network at high-fidelity is critical to automation in general, but also to CI/CD specifically. [Figure 6-6](#ch06.xhtml#ch6fig6) shows the reference architecture simulated in CML.

![FIGURE 6-6 Reference Architecture Simulated in CML](Images/06fig06.jpg)

FIGURE 6-6 Reference Architecture Simulated in CML

However, even simulation can be difficult at a large scale. Although it is possible to simulate hundreds of elements with the right number of resources, simulating thousands or more elements becomes very difficult without a very large number of resources. This is where consistency in architecture is key to success. The most common reason for a large, sprawling network is a large, sprawling organization that needs to connect many sites. It is not uncommon for the organizations that we deal with to have hundreds or even thousands of sites totaling tens of thousands of devices. Such a network would be very difficult to simulate in its entirety.

If these sites are deployed from one or a small number of fundamental types (for example, small, medium, large), then you need only simulate those fundamental types. If the automation takes advantage of this consistency, then there is only the need to develop to, and test, those fundamental types.

In addition to scale, simulated environments can also lack in their capability to represent some types of devices. Although the proliferation of virtualized network functions and the adoption of virtual infrastructure have greatly enhanced the ability to use simulated environments for development and testing, there is still a large amount of hardware that is difficult to represent in a high-fidelity way. Physical elements like network access switches and wireless access points are problematic. Furthermore, devices that do special packet handling implemented in hardware for speed or scalability can also be difficult to simulate in a realistic manner. In either of these cases, a simulated development and test network can be augmented with physical hardware to get the needed fidelity. Keep in mind, however, that most of the configuration changes that we want to test involve the control plane of the network. Even for those problematic devices, the control plane is often implemented as software that is easily simulated. Even if you cannot reproduce the exact behavior from a client with simulation, you can accurately reproduce the behavior of the control plane.

Even with these challenges, a simulated network is an important tool when developing a CI/CD pipeline. However, we need to make sure that we construct our simulated topology such that it can be used for automation. For example, many simulations depend on access to the console to configure the devices in the topology. Because you are trying to use the same tooling for your automated testing as you are using for our deployment, you need to make sure that you set up the management interfaces in your simulated network such that you can have the same or similar type of access (for example, SSH, RESTCONF) from your control node (that is, the node running your automation workflow).

## Hands-on Code: Deploying the Topology

Go to “Deploying the Topology” exercise at the following URL:

[https://github.com/model-driven-devops/mdd#exercises](https://github.com/model-driven-devops/mdd#exercises)

This exercise covers the CML topology file and the Ansible playbook used to deploy the test environment in the workflow. Depending on your environment, you can use the playbooks to deploy the test network in CML.

## Automation

The next step in the process is to automate the architecture using the simulated test network. The exact method for doing this may be different, depending on the specific situation, but we have found the following process usually works well with network automation:

1. If you are starting with an existing network, then choose a part of your network (hopefully representative of your entire network) to start.

2. Manually configure the network.

3. Verify that it functions as desired.

4. Develop automation to produce the desired function.

## Creating a Source of Truth
