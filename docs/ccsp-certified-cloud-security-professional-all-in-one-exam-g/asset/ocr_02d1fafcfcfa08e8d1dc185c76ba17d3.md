# Chapter 4: Cloud Platform and Infrastructure Security

145

# Define Scope

The first step in formulation is to ensure security concerns are an intrinsic part of the plan from the start, rather than trying to retrofit the plan after it is developed. This allows security to clearly define the roles and areas of concern during the planning and design phase and to ensure that proper risk assessments are conducted and accepted by management along the way.

# Gather Requirements

Requirements taking into account the RPO and RTO objectives we previously discussed. This determines what needs to be included in the plan as well gives a sense of what types and models of solutions are necessary to meet these objectives. From the perspective of the Cloud Security Professional, the determination of critical systems and the time necessary to establish operations in the event of a BCDR situation requires the analysis and analysis of threats and vulnerabilities that pose a risk to the data and systems. Regulations, laws, policies, customer expectations, and public relations all play a role in this determination for possible solutions.

# Analyze

This step is where the requirements and scope are combined to form the objectives and roadmap for the actual plan design. This step involves a thorough analysis of the current production hosting location for the system or application, a decomposition of components that need to be replicated for a BCDR situation, and the areas of risk associated with that. With moving to a new environment, risks are inevitable due to differences in configurations and support models, as well as new hosting staff who do not have a history or familiarity with the application or system. A primary concern moving to a secondary host provider for BCDR reasons is whether they can handle the load and expectations for the system or application like the primary production hosting arrangement.

# Assess Risk

In any IT system, regardless of hosting circumstances or providers, risk assessments are an ongoing and continuous process to ensure security compliance and regulatory requirements. Here's a list of the main risks that are assessed:

+   * Load capacity of the BCDR site Can handle the needed load to run the application or system, and is that capacity readily and easily available? Can the BCDR site handle the level of network bandwidth required for the production services and the user community accessing them?

+   * Migration of services Can the BCDR site handle the bandwidth and requirements to get the production services mirrored and configured in a timely manner? If there are huge data sets, will incremental copies be performed regularly versus doing to a single large transfer at the time when services are down? How many services are on standby and can be rapidly deployed and expanded when needed?