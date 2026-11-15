+   * Parallelism: multiple agents can collaborate on the same task or on different tasks.
+   * Robustness: if one robot fails or is attacked, the group can still perform the task after a possible reconfiguration phase. In a monolithic solution, the failure of one robot means the failure of the mission.
+   * Simplicity: in general, agents in MRS are less complex than in monolithic solutions, where greater physical and computational capabilities are required to accomplish the same task. This leads to a lower probability of software/hardware failures.
+   * Cost: The simplicity of the agents often makes building a MRS cheaper than building a single, more skilled robot capable of the same tasks.

Of the main challenges faced in automating a multi-UAV inspection, we have focused on two in this work:

+   1. A fleet path planning that allows all components to perform the necessary analysis while avoiding collisions with infrastructure and other aircraft.
+   2. A control of the UAVs that guarantees the tracking of the generated trajectories despite the inevitable error in the actual position of the aircraft through GNSS localization systems.

Solving such problems is only the first step toward real applications.

Indeed, programmatic management of environmental and civil infrastructure inspections is managed by ad hoc information systems called management systems. However, these systems are not yet configured for a MRS and Dynamic Building Information Modeling BIM-augmented or Digital Twin approach to inspection [5,6]. In addition, BIM, a user-friendly and data-driven information platform, has not been connected to the current safety inspection process to better understand the risk issues identified for the infrastructures [7]. Also, the use of Digital Twins and Heritage Building Information Modeling (HBIM) in current World Heritage management systems has not yet been clarified.

The use of Digital Twins in a specific workflow must necessarily go hand in hand with other processes used in the environment and civil infrastructure field for whole life cycle management: BIM and specific management systems such as BMS, WDS (Waste Disposal Sites) management, which we will refer to as WMS (Waste Management System), DCMS (Dam Control Management System), or HMS (Heritage Management System) in this paper. By using the software BIM, the digital aspects of a construction project are managed with the appropriate digital software. In this work, BIM, photogrammetry, and simulation software were used. The increasing use of BIM