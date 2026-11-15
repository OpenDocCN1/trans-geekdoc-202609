# 7.6 Use Cases and Applications

We showcase applications of the presented typology to demonstrate its advantages in identifying DT needs and dimensioning functionalities. Within our team we are testing our approach on different applications and projects: Assistive Devices, Additive Manufacturing, Maintenance 4.0, Battery Design, Civil Engineering, and Data Center Reliability. Table 7.1 summarizes the typology of three DTs.

TABLE 7.1
Typography Applied to Different Use Cases

| Applications Criteria | Lithium-Ion Battery Design | AMR Fleet | Predictive Maintenance |
| :--- | :--- | :--- | :--- |
| DT entity (OME) | Battery | Robot/Fleet | Machine |
| Type | Instance | Instance/Aggregate | Instance |
| Version | Internal version IV0 | Internal “instance” version IV0 Internal “aggregate” version IV1 | Internal version IV0 |
| Level | Equipment | Equipment/System | Equipment |
| Maturity | Control DT | Collaborative DT | Cognitive DT |
| Topology | Disconnected | Connected embedded/ Connected disjoint | Connected |
| Decision loop | Open loop | Mixed loop | Open loop/Mixed |
| User | Human agent: Design Engineer | Human agent/Fleet DT | Production and maintenance manager and operator |
| Usages | Analysis/Comparison | Simulation/ Optimization/ Collaboration | Analysis/Cognition |
| Application | Off-line analytics | Real-time control/ Trajectory optimization | Health diagnosis and predictive maintenance |
| Synchronization | Synchronous | Synchronous/ Asynchronous | Synchronous |
| Accuracy | Fixed (for the metrics: State of Health and State of Charge) | Fixed (for the metric: Throughput) | Configurable |
| Models | Empirical (Electrical Equivalent Circuit Models) → Deterministic | Analytical (Motion models) → Deterministic | Analytical (Markov chains) → Probabilistic |