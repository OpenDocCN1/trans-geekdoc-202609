
For organizations supporting large networks, however, using a standard data model, such as `OpenConfig`, makes more sense. Although this is not the only standard data model available, it has the most comprehensive list of supported vendors and is aimed at addressing actual operational needs. Its neutrality does introduce some limitations, especially when supporting vendor-specific features, but as adoption grows, limited support for vendor-specific features should be overcome through open-source contributions. Until then, some `OpenConfig` models will need to be augmented with vendor-native models.

As shown in [Figure 2-6](#ch02.xhtml#ch2fig6), after you settle on a standard model, you can greatly simplify the movement of data through a system.

![FIGURE 2-6 Same Data Model Used Across Multiple Devices](Images/02fig06.jpg)

FIGURE 2-6 Same Data Model Used Across Multiple Devices

As stated previously, not every source of truth uses `OpenConfig`, and not every device accepts `OpenConfig`. While this is true, an ever-increasing number of network devices do accept `OpenConfig`, and you generally have the flexibility to store the source of truth however you want. Where this is not the case, you must do a translation.

[Figure 2-7](#ch02.xhtml#ch2fig7) illustrates a model that has the flexibility to support native and non-native `OpenConfig`. Consider the two sides of [Figure 2-7](#ch02.xhtml#ch2fig7). On the left, a source of truth supports `OpenConfig` natively and one does not. As you can see, a source of truth that stores data in `OpenConfig` natively can be used directly with a device that accepts `OpenConfig` natively. A source of truth that does not support native `OpenConfig` requires a translation function (`Xlate` in the figure) to transform the source of truth data into the `OpenConfig` model. On the right, a device supports native `OpenConfig` and one does not. For the one that does not, we introduce a platform to transform the `OpenConfig` model data into a model that is accepted by this non-native device. The `Xlate` and `Platform` functions allow support for non-native `OpenConfig` capabilities on both sides of this picture without losing the benefits of choosing to leverage an `OpenConfig` model.

![FIGURE 2-7 Source of Truth with Native OpenConfig and with Translation](Images/02fig07.jpg)

FIGURE 2-7 Source of Truth with Native OpenConfig and with Translation

But wait, this was done to avoid having to translate, right? Yes, but that is only for the ideal case where everything already natively supports `OpenConfig`. However, even when this is not the case, significant efficiencies still can be gained in pushing the translations out to the edges of the data flow. First, doing the translation once for all workflows is better than having to do it ad hoc for each individual workflow. Second, as shown in [Figure 2-8](#ch02.xhtml#ch2fig8), common operations such as validation and compliance are considerably more efficient because they need be performed only once, against a single data model.

![FIGURE 2-8 Validation and Compliance Applied to a Single Data Model](Images/02fig08.jpg)

FIGURE 2-8 Validation and Compliance Applied to a Single Data Model

For example, creating even a simple service such as a `BGP` peering would require a different configuration or data model for each unique type of device that exists on the network. When you’re working with a single data model, however, the service just needs to be created once. This simplification is multiplied by the amount of configuration on your network and amplified by the complexity of that configuration. Further efficiencies are reached with validation and compliance because they likewise need to be done against only a single data model.

#### Source of Truth

We’ve mentioned source of truth several times so far and will continue to drill deeper into the topic as the book unfolds. Simply put, `SoT` is all of the data required to configure your network. Having a structured, centrally located source of truth is critical to model-driven DevOps because configuration is really a data management problem. If the data is properly managed, then moving that data into your network devices, and the tooling used to do that, becomes much easier.

#### DevOps as a Framework

Finally, model-driven DevOps defines a framework in which to practice DevOps. The framework focuses on functionality over specific tools, and its use adds structure to encourage thoughtful design from inception as opposed to an ad hoc compilation of automation tools (see [Figure 2-9](#ch02.xhtml#ch2fig9)).

![FIGURE 2-9 Model-Driven DevOps Framework](Images/02fig09.jpg)

FIGURE 2-9 Model-Driven DevOps Framework

The benefit of a framework is that individual parts can evolve without needing to replace the entire system, resulting in a lower overall investment. This framework gives operators the flexibility of using existing tooling or selecting the tool that best performs a particular task. Also, as your framework evolves, new functions can be introduced with relative ease.

At the core of this framework is Orchestration and Workflow. This layer provides a northbound API to the layer above it and pulls in information from the source of truth to use in the workflows. Optimally, it calls an API provided by a platform to control devices. As you see later in the book, a platform is a function above the devices that abstracts them into a cohesive API with a consistent level of functionality between the devices. The platform would also simplify the deployment of complex services where possible.

When the Orchestration/Workflow layer cannot leverage an API or a platform, it must go directly to each individual device; however, doing so affects both complexity and scalability. Complexity is increased because direct knowledge of the individual device is required, and the Orchestration/Workflow layer must then construct, coordinate, and validate any complex services.

Finally, the top of the framework includes the stimuli to the system. Workflows are either started from an ITSM tool as customers request new services or features, or directly from the operations staff.

### DevSecOps: Baked-In Security

Last, but not least, agility does not mean a lack of security. On the contrary, the infrastructure-as-code foundation required by DevOps provides the perfect conduit to embed security into every step of integration and deployment. This aspect of DevOps is generally called `DevSecOps`, indicating the integration of security into DevOps. It’s important to understand that DevSecOps is not fundamentally different from DevOps itself. It does not just apply to network security, but rather, it is an emphasis on including security into DevOps in a rigorous way and applying it to all types of infrastructure.

Integrated security is accomplished in three ways:

*   When the infrastructure is rendered as code, the changes to the infrastructure are deterministic and complete. These changes can then be integrated into the infrastructure immediately, as opposed to collecting many changes into a more complex maintenance window.

*   The changes are done in a collaborative way and reviewed before deployment. Cross-functional DevOps teams include reviewers from all disciplines, especially security. When a change is pushed out, reviewers from the network security team can accept or reject those changes depending on what they would do to the security posture of the network.

*   These changes can be checked against compliance requirements and verified against live tools in the test phase of integration. For example, scanning tools can be used against either virtual or physical firewall instances in the simulated environment to test whether any change creates a vulnerability that compromised the security of the infrastructure.
