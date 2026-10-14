# Understanding the Server’s Role and the Threat Environment

If it runs only one or a few services, easy to disallow irrelevant things

+   **Basics**
+   - Physical security
+   - Backup
+   - Harden the operating system
+   - Etc.

+   **Minimize Applications**
+   - Main applications
+   - Subsidiary applications
+   - Be guided by security baselines

+   **Create Secure Application Program Configurations**
+   - Use baselines to go beyond default installation configurations for high-value targets
+   - Avoid blank passwords or well-known default passwords
+   - Etc.

# Install Patches for All Applications

# Minimize the Permissions of Applications

If an attack compromises an application with low permissions, will not own the computer

+   **Add Application Layer Authentication, Authorizations, and Auditing**
+   - More specific to the needs of the application than general operating system logins
+   - Can lead to different permissions for different users

+   **Implement Cryptographic Systems**
+   - For communication with users

# Figure 8-3  Hardening Applications (Study Figure)

The *Action* menu allows access to the properties for each service. Figure 8-5 shows that the Startup type can be changed from Automatic to either Manual or Disabled. If the service is set to manual, it will only start if initiated by the user. The service can also be manually started or stopped. Disabling unnecessary services can free up system resources and protect the host from external attack. Disabling critical services without understanding their function can cause unintended systemic problems.

# Figure 8-4  Windows Services

![](bbox=[0.11, 0.726, 0.699, 0.975])