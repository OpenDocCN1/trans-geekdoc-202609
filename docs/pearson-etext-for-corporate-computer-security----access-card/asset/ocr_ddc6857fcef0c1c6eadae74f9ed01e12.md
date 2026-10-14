+   1. Backup
+   2. Backup
+   3. Backup
+   4. Restrict physical access to hosts (see Chapter 5)
+   5. Install the operating system with secure configuration options
+   6. Minimize the applications that run on the host
+   7. Harden all remaining applications on the host (see Chapter 8)
+   8. Download and install patches for vulnerabilities
+   9. Manage users and groups securely
+   10. Manage access permissions for users and groups securely
+   11. Encrypt data if appropriate
+   12. Add a host firewall
+   13. Read operating system log files regularly for suspicious activity
+   14. Run vulnerability tests frequently

Figure 7-2 The Elements of Host Hardening (Study Figure)

Figure 7-4 shows Windows Deployment Services with multiple groups of disk images that can be deployed depending on the needed host configuration.

When a new computer of that type must be installed, the company downloads the operating system image directly into the new computer. This saves money on each installation. It also ensures that each server is properly configured according to the firm’s security baselines and general security policies.

# Virtualization

In larger enterprise environments companies manage hundreds of virtual disk images. They can be independently deployed across a variety of hardware platforms using

+   **Security Baselines Guide the Hardening Effort**
+   Security baselines are specifications for how hardening should be done
+   Needed because it is easy to forget a step
+   It is like a pilot's checklist
+   Different baselines for different operating systems and versions
+   Different baselines for servers with different functions (webservers, mail servers, etc.)
+   Disk images
+   Can also create a well-tested secure implementation for each operating system version and server function
+   Save as a disk image
+   Load the new disk image on new servers
+   **Server Administrators Are Called Systems Administrators**
+   Administer one or more servers
+   Implement security baseline actions
+   Larger firms have many systems administrators
+   Security baselines help ensure uniformity in hardening
+   Systems administrators are usually not responsible for network administration

Figure 7-3 Security Baselines and Systems Administrators (Study Figure)