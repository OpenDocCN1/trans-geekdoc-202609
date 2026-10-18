
For the first time in a very long time, Bob was genuinely excited about his role at ACME Corp and the direction the company was heading. While he was originally skeptical of this DevOps mandate from the CIO, he was starting to wrap his mind around the whole automation thing. Yes, ACME Corp had some work to do with respect to how they stored the data that represented their network, known as the source of truth (SoT), but he now saw that ACME already had a source of truth for many things. Making the source of truth useful for automation might involve converting some text in a document or spreadsheet into structured data stored in a format such as `YAML` or `JSON`, but, after that was done, it would be much more amenable to automation. What was once just some prose in a document that a human would have to read, interpret, and convert to device-specific CLI configuration could now be fed directly into an API in an automated way. The notion of a source of truth stored in a way that it was version-controlled and applied consistently throughout the entire network was something Bob never thought possible prior to this DevOps journey.

Because Larry oversaw compliance at ACME Corp, he and Bob made a plan to put this newfound knowledge to work by automating portions of the compliance check and subsequent remediation. If they were successful, the plan would drastically reduce the amount of time they spent on compliance and save the company a substantial amount of money. They decided to start small and target common system services such as `DNS`, `NTP`, and `AAA`. Rather than produce their own data model for these system services, they decided to use the `OpenConfig` data models. Based on Bob’s previous research, this was the only multivendor way of structuring network configuration data and, even if a particular target device did not support `OpenConfig` today, it would in the future.

The first order of business was taking Larry’s document with the compliance standards and converting the section on system services to `OpenConfig`-structured data in a machine-readable format. Bob and Larry decided to use `YAML` for this task because it is easier to read than `JSON`. Because their intent was to make this the basis for their `IaC`, the more human-readable it was, the better. Having never done this sort of thing before, they found the process a little intimidating but, after some effort, they were able to generate structured data from Larry’s compliance document for the basic system settings.

What they had at this point was structured source of truth data for those basic settings that needed to be configured across every device in the ACME Corp network. To make use of it, they needed a way to take the data and send it via API to each device in the network.

“OK, now what?” Larry said.

“That is a good question. We will need to use APIs to send this data to our network devices.”

Larry sighed. “Bob, there is something you need to know about me.”

“What is that?”

“I’m not a programmer!”

Bob laughed. “That makes two of us. I think we are going to want to use `Ansible` for this step.”

Bob had fiddled with `Ansible` enough to know that it was well suited to the task of configuring a target system by taking `JSON` or `YAML` data, reformatting it if necessary, and sending it to a device API. After all, typical `Ansible` inventory data was stored in `YAML` already. In addition, `Ansible` came with a set of modules that were intended to make it easier to communicate with devices via the API without someone necessarily needing to understand the specific details. Before deciding to use the `OpenConfig` model for their data, Bob had done some research on `NETCONF` and `YANG`. The `NETCONF` protocol, in combination with `YANG` models, was the closest thing the network industry had to a common API across vendors. As such, the `NETCONF` protocol was well supported in `Ansible` via a set of modules. In theory, they should be able to take their `OpenConfig`-formatted data written in `YAML` and feed it directly, without reformatting, to a device or set of devices using the `NETCONF` modules in `Ansible`.

Larry and Bob, a couple of self-professed nonprogrammers, spent the next hour or so producing an `Ansible` inventory file and a playbook to use with their system services data. The inventory file contained the required info to communicate with one of their switches in the lab, and the playbook simply used a `NETCONF` module to send their `OpenConfig` system service data to the switch. Most of the time was spent getting the hang of the `YAML` format and the general structure needed for a playbook. But then, suddenly, the playbook ran without error.

“Did that just do what I think it did?” asked Larry.

“I think so!” exclaimed Bob. Bob logged in to the switch and verified that, indeed, they had successfully changed the switch system services configuration using their `OpenConfig` data model.

“Do you know what this means?” asked Larry.

“That we just spent half a day on something that would take five minutes to do by hand?” replied Bob.

“Very funny. It is way more important than that, and you know it. We now have the basis for infrastructure as code at ACME Corp and will be able to keep the company compliant in an automated way. This will save me and my compliance team hundreds of hours every year.”

“So, you’re saying that management is going to love us,” said Bob. “Maybe we will even get a raise.”

“I wouldn’t go that far. But at least we might be able to keep our jobs.”

Over the next few weeks, Bob and Larry scheduled a series of maintenance windows to apply their `IaC` across the network. When they were done, they were able to ensure that the basic system settings of every device were compliant with ACME Corp standards. The audit was quickly approaching, and it was a huge win. Emboldened by their success, they decided to automate even more of the standards.

So far, they had automated the configuration of things that had a low risk of network interruption. The remaining compliance standards, however, carried more risk because they applied to the network control plane. One such standard was the Spanning Tree Protocol (`STP`). A problem in the configuration or operation of Spanning Tree had the potential to cause widespread outages. Bob knew that, as with any control plane protocol, it was important to tread carefully with Spanning Tree. ACME Corp had a handful of switches in the lab that they often used to test out new configurations. It was by no means a representation of their production network, but it was the best they had. Bob used the lab to extend their source of truth data model with the `OpenConfig` data necessary to configure Spanning Tree to ACME Corp standards.

The great part about the way in which they had implemented `IaC` is that Bob did not even have to modify the `Ansible` playbook. All he had to do was add the required Spanning Tree bits to their `YAML`-based source of truth and run the playbook again. When he had all the data right, he could effect a change in the Spanning Tree topology by simply changing some values in the source of truth. It literally took seconds to change the Spanning Tree topology in their dev lab. For Larry and Bob, this was a revolutionary way to operate.

With this successful test, Larry and Bob got the green light to use their `IaC` to ensure the network Spanning Tree configuration met compliance standards. The approved maintenance window for this work was set for two weeks from now. Using what he had learned in the lab, Bob started creating the source of truth for the production network. Unfortunately, the network had drifted far out of compliance, which meant that what was *supposed to be* configured did not often line up with what is configured. Larry and Bob decided that this was a good opportunity to create the source of truth as it should be rather than take values from the as-built network. After all, the as-built network was not in compliance.
