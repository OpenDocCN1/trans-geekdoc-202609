+   - Basics
+   - Disks
+   - Networking
+   - Management
+   - Monitoring
+   - Advanced
+   - Tags
+   - Review + create

Create a virtual machine that runs Linux or Windows. Select an image from Azure marketplace or use your own customized image. Complete the Basics tab then Review + create to provision a virtual machine with default parameters or review each tab for full customization. Learn more c²

This subscription may not be eligible to deploy VMs of certain sizes in certain regions.

# Project details

Select the subscription to manage deployed resources and costs. Use resource groups like folders to organize and manage all your resources.

+   - Subscription *: Azure Free Subscription
+   - Resource group *: book127-edge1-westus-network-rg [Create new]

# Instance details

+   - Virtual machine name *: book127-edge1-svr
+   - Region *: (US) West US
+   - Availability options: No infrastructure redundancy required
+   - Security type: Trusted launch virtual machines [Configure security features]
+   - Image *: Ubuntu Minimal 22.04 LTS - x64 Gen2 (free services eligible) [See all images | Configure VM generation]

# Administrator account

+   - Authentication type: SSH public key (selected), Password
+   - Username *: azureuser
+   - SSH public key source: Generate new key pair
+   - Key pair name *: book127-edge1-svr_key

# Inbound port rules

+   - Select which virtual machine network ports are accessible from the public internet. You can specify more limited or granular network access on the Networking tab.
+   - Public inbound ports *: None, Allow selected ports (selected)
+   - Select inbound ports *: SSH (22)
+   - Info: All traffic from the internet will be blocked by default. You will be able to change inbound port rules in the VM > Networking page.

# Figure 10.11: Azure Create Virtual Machine Basic Form