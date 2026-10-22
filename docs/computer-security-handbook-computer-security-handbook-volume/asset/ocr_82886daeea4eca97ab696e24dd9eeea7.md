is building its own whitelist information, it will have to acquire each patch, record its files’ characteristics, and update its whitelists with the new information. Either method may cause problematic delays for organizations that apply patches quickly, especially automatically; patched software may be seen as unknown software and prohibited from running.

To avoid these problems with updates, most application whitelisting technologies offer maintenance options. For example, many technologies allow the administrator to select certain services (e.g., patch management software) to be trusted updaters. This means that any files that they add to or modify on a host are automatically added to the whitelist. Similar options are available for designating trusted publishers (i.e., software vendors), users (such as system administrators), sources (such as trusted network paths), and other trusted entities that may update whitelists. Organizations using application whitelisting technologies should ensure that they are configured to avoid problems with updates.

# 40.4 ENTERPRISE PATCH MANAGEMENT TECHNOLOGIES.

This section provides an overview of enterprise patch management technologies. It discusses their composition, focuses on the security and management capabilities that they provide, and gives recommendations for their use.

# 40.4.1 Components and Architecture.

Enterprise patch management technologies are similar architecturally to other enterprise security solutions: one or more centralized servers that provide management and reporting, and one or more consoles. Enterprise patch management technologies can also be offered as a managed service. What distinguishes enterprise patch management technologies from each other architecturally are the techniques they use to identify missing patches. The three prevalent techniques are agent-based, agentless scanning, and passive network monitoring. Many products support only one of these techniques, while other products support more than one. All the techniques are explained in more detail in the following subsections. Organizations should carefully consider the advantages and disadvantages of each technique when selecting enterprise patch management technologies.

# 40.4.1.1 Agent-Based.

An agent-based patch management technology requires an agent to be running on each host to be patched, with one or more servers that manage the patching process and coordinate with the agents. (Note that agent-based patch management technology is built into some operating systems.) Each agent is responsible for determining what vulnerable software is installed on the host, communicating with the patch management servers, determining what new patches are available for the host, installing those patches, and executing any state changes needed to make the patches take effect (e.g., application restart, OS reboot). Each agent runs with administrator privileges so it can perform these actions. The patch management server is responsible for providing the agents with information on vulnerable software and available patches, including where patches can be acquired and what state changes are needed.

Compared to agentless scanning and passive network monitoring, agent-based patch management technologies are strongly preferred for hosts that are not on the local network all the time, such as telecommuter laptops and smartphones.

There are a few limitations to agent-based patch management technologies. Hosts that don’t permit direct administrator access to the operating system, such as many