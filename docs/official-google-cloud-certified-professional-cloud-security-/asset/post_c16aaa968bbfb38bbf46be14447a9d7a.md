
# Google Professional Cloud Security Engineer Exam – Mock II

- 13. What is the role of security policies in Google Cloud Armor?
- A. Security policies define rules for access control to Google Cloud resources
- B. Security policies enforce encryption of data at rest and in transit
- C. Security policies enable the configuration of firewall rules and network ACLs
- D. Security policies specify the behavior of Google Cloud Armor for incoming requests

- 14. What is the purpose of log sinks in Google Cloud Logging?
- A. To collect logs from various Google Cloud services and store them in Cloud Storage
- B. To analyze log data and generate insights using machine learning algorithms
- C. To export logs to third-party logging and monitoring systems
- D. To manage access controls and permissions for log data

- 15. What is the benefit of enabling log-based metrics in Google Cloud Logging?
- A. It allows you to visualize specific events using custom dashboards and charts
- B. It enables you to monitor specific events and trigger alerts based on log entries
- C. It enables real-time analysis of log data to detect security threats
- D. It helps you automatically manage log storage and retention policies

- 16. What is the purpose of instance templates in Google Cloud Compute Engine?
- A. Instance templates are used to create snapshots of Compute Engine instances
- B. Instance templates allow for the management of machine types and sizes
- C. Instance templates enable the creation of custom images from scratch
- D. Instance templates define the configuration settings for creating VM instances

- 17. Which statement accurately describes the image lifecycle management for Compute Engine on Google Cloud?
- A. Compute Engine provides automatic image lifecycle management, including regular backups and versioning for all custom images
- B. Users have full control over the image lifecycle, including the ability to create and manage custom image snapshots and metadata
- C. Compute Engine automatically deletes all unused images after a specific period of inactivity to optimize storage usage
- D. Image lifecycle management is only available for Google-managed images and cannot be applied to custom images

- 18. Which Google Cloud feature provides enhanced security for Virtual Machines (VMs) by enabling Secure Boot, virtual Trusted Platform Module (vTPM), and integrity monitoring?
- A. Shielded VM
- B. Virtual Private Cloud (VPC)
- C. Google Cloud Armor
- D. Cloud Security Scanner

- 19. Which security measure should be implemented to secure the artifacts produced by a Google Cloud CI/CD pipeline?
- A. Storing artifacts in a publicly accessible storage bucket
- B. Encrypting the artifacts at rest and in transit
- C. Granting broad read access to all pipeline service accounts
- D. Disabling the logging and auditing of artifact access

- 20. Which Google Cloud feature enforce a secure software supply chain by allowing organizations to define and enforce custom policies for container image deployment based on metadata and attributes?
- A. Binary Authorization
- B. Container Registry
- C. Cloud Build
- D. Google Kubernetes Engine (GKE)

- 21. Which security feature in Google Kubernetes Engine (GKE) helps protect container workloads by automatically managing and rotating encryption keys for data at rest?
- A. Google Cloud Armor
- B. Cloud Identity-Aware Proxy (IAP)
- C. Binary Authorization
- D. GKE Data Encryption using Cloud Key Management Service (KMS)

- 22. Which statement accurately describes the purpose of namespaces in Google Kubernetes Engine (GKE)?
- A. Namespaces are used to control network traffic between different GKE clusters
- B. Namespaces provide logical isolation within a single GKE cluster by partitioning resources
- C. Namespaces are responsible for automatically scaling the number of nodes in a GKE cluster
- D. Namespaces ensure secure access to the GKE API server through token-based authentication

- 23. What is the primary purpose of Role-Based Access Control (RBAC) in Google Kubernetes Engine (GKE)?
- A. RBAC enables fine-grained control over permissions and access to Kubernetes resources
- B. RBAC automatically scales the number of GKE nodes based on the workload demand
- C. RBAC manages containerized applications' network traffic within a GKE cluster
- D. RBAC ensures secure communication between GKE clusters using a service mesh

- 24. Which statement accurately describes the role of a service mesh in Google Kubernetes Engine (GKE)?
- A. A service mesh provides additional encryption layers for securing data at rest within a GKE cluster
- B. A service mesh is responsible for managing network policies and ingress control for GKE services
- C. A service mesh enhances observability, traffic management, and security for microservices in a GKE cluster
- D. A service mesh automatically scans container images for vulnerabilities and security risks in GKE

- 25. Which security measure helps ensure the integrity and security of container images in Google Cloud?
- A. Container Registry vulnerability scanning
- B. Disabling image scanning for faster image deployment
- C. Running containers with elevated privileges for system compatibility
- D. Sharing container images publicly without any access controls

- 26. True or false: Container vulnerability scanning in Google Cloud automatically identifies and alerts about security risks and vulnerabilities in container images.
- A. True
- B. False

- 27. Your Google Cloud organization policies provide guardrails for security controls for all organizations. Which of these are not best practices to follow when setting up organization policies (select all that apply)?
- A. Organization policies should be implemented over a period of time as your requirements become clear
- B. Delegate control of organization policies to the SRE teams
- C. Prior to enforcing policies, thoroughly test and validate their impact on your resources and applications
- D. It is usually not required to monitor and audit policies as they provide a robust framework to implement security controls right from the start
- E. Since organization policies are set at the organizational level, it is often not required to implement them at the folder or project level
- F. You should not version control policies via infrastructure as code

- 28. When creating projects in Google, which of the following are not best practices (select all that apply)?
- A. Implement consistent naming conventions for your projects to ensure clarity and ease of identification
- B. Use the default project controls since it allows you to get up and running quickly
- C. Enable audit logs and monitoring for your projects to track and analyze activities within your environment
- D. Google does not place a cap on the number of projects in a Google Cloud organization so it is safe to leave the project and create a new one
- E. Use IAM roles that are broad enough to grant more access than is needed so development is not hindered
- F. Utilize Google Cloud's resource hierarchy, including folders and projects, to organize and manage resources effectively

- 29. A customer has a team that exclusively manages user identity and access. A cloud engineering team manages Google Cloud and has an intimate knowledge of organization policies. What is the right permission model for this company to manage Google Cloud?
- A. Assign the super admin role to the cloud engineering team so they can manage users and groups for the entire organization.
- B. Restrict the super admin role. Assign the user and group management roles to the identity access team. Assign the organization administrator role to the cloud engineering team.
- C. Assign the super admin role to the identity access team and assign the organization administrator role to the cloud engineering team.
- D. Assign the super admin and organization administrator roles to the identity access team so they can effectively manage access to the entire organization.
