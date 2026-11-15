# # Maintenance Use Cases of an Industrial Robot

Epson introduced the T3-401S SCARA robot (ESR) as a versatile entry-level robot solution for production lines (Epson, 2019). An adoption of typical maintenance works for the ESR using blockchain is demonstrated in the following subsections. The use cases rely on the integration of BISS 4.0 which is described in detail later on. The stakeholders and procedures involved can be seen in Figure 7.

The stakeholders built a consortium to transform business transactions concerning service contracts. The owner uses the ESR for production, maintenance tasks are carried out by internal and external staff. For external maintenance, a cleaning service is contracted. Warranty contracts between the owner and the manufacturer (OEM) rely on compliant maintenance tasks. There are applications (Capture Interface and Registry Application) to perform transactions on the shared blockchain, represented in HLF as a channel. Every stakeholder keeps a copy of the ledger, the complete history of all transactions. Smart contracts are reading the channel for new transactions to succeed or fail, yielding a judgment of their contract fulfilment. The smart contracts concerning maintenance are based upon either (i) the maintenance plan, provided by the OEM and based on historical data or (ii) the Preventive Maintenance (PM), a system observing the condition of the ESR and reacting adaptive. The PM is based on previous sensor-collected machine data, which is interpreted and used for maintenance scheduling. The PM uses Machine Learning Technology to predict appropriate intervals and types of maintenance.

# Figure 7. BISS 4.0 Platform Integration

![](bbox=[0.19, 0.51, 0.78, 0.792])

# # Planned Maintenance Use Case (PMUC)

In this use case a scheduled maintenance task is carried out without issues. The task is defined in the service manual, provided by the equipment manufacturer. The manual lists the maintenance tasks (MT),