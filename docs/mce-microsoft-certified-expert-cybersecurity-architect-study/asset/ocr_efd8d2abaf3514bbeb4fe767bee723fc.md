Using this method, users are limited in their ability to gain unauthorized access to IoT services and data on-premises or in the cloud, preventing both mass information disclosure (such as leaked factory production data) and potential elevation of privilege for command and control (for instance, halting the factory's production line).

Multiple personas are involved in the life cycle of an IoT solution, such as IoT device builders, IoT application developers, and IoT solution operators.

Table 7.4 provides a high-level outline of these roles and security requirements.

# TABLE 7.4 Roles and Security Requirements

| Role | Role Description | Security Requirements |
| --- | --- | --- |
| IoT hardware manufacturer/integrator | Often, these players are either manufacturers of IoT hardware, integrators who assemble hardware from various manufacturers, or suppliers who provide hardware for IoT deployments that are manufactured or integrated by other suppliers. | Determine the minimum requirements for hardware.<br>Protect hardware from tampering.<br>Ensure the security of upgrades. |
| IoT solution developer | Solution developers are typically responsible for developing IoT solutions. These developers may be part of an in-house team or work for a system integrator (SI) specializing in this field. In addition to developing various components of the IoT solution from scratch, the developer can integrate various off-the-shelf or open-source components into the IoT solution. | Develop software in a secure manner.<br>Choose open-source software carefully.<br>Ensure that security flows are avoided by integrating. |
| IoT solution deployer | To deploy an IoT solution in the field, hardware needs to be deployed, devices need to be connected, and solutions must be deployed on hardware or in the cloud. | Ensure the secure deployment of hardware.<br>Ensure the safety of authentication keys. |
| IoT solution operator | Operating, monitoring, upgrading, and maintaining the IoT solution for the long term after deployment is necessary. Several in-house teams can perform these tasks, including information technology specialists, hardware operations and maintenance teams, and domain specialists who monitor the correct behavior of the IoT infrastructure as a whole. | Maintain an up-to-date system.<br>Ensure that malicious activities are prevented.<br>Regularly conduct audits.<br>Credential protection in the cloud. |