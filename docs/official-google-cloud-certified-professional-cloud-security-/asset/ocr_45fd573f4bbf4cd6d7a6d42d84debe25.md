# GKE security features

Let us look at how GKE provides access control.

# Access control

GKE supports two options for managing access to resources within the Google Cloud project and its clusters:

+   - Kubernetes Role-Based Access Control (RBAC)
- Identity and Access Management (IAM)

These methods are similar in function, but they are focused on different types of resources. Let us look at them now.

# Kubernetes RBAC

This is a built-in feature of Kubernetes that grants granular permissions to Kubernetes cluster objects. Within the cluster, permissions are represented by ClusterRole or Role objects. Roles in Kubernetes RBAC provide permissions at the namespace level, while ClusterRoles offer cluster-wide permissions. Proper use of Roles and ClusterRoles is crucial for maintaining security by adhering to the principle of least privilege and enabling the separation of duties. Regular review and auditing of Roles and ClusterRoles are essential to ensure that permissions align with security requirements. RoleBinding objects allow Kubernetes users, Google Cloud users, Google Cloud service accounts, and Google groups to have access to roles.

Kubernetes RBAC is the ideal choice if you utilize GKE and need fine-grained rights for every item and operation in your cluster. GKE has built-in support for RBAC that allows you to create fine-grained rules that exist within the GKE cluster. A Role is scoped to a specific object or a type of Kubernetes object and defines which actions (called verbs) the role grants in relation to that object. A RoleBinding is also a Kubernetes object, which grants roles to users. In GKE, the subject can be any of the following principals:

+   - Cloud Identity user
- Google Cloud IAM service account
- Kubernetes service account
- Cloud Identity Service group

Now, let us understand IAM for GKE.