
## Create virtual network

- Basics
- Security
- IP addresses
- Tags
- Review + create

Define the address space of your virtual network with one or more IPv4 or IPv6 address ranges. Create subnets to segment the virtual network address space into smaller ranges for use by your applications. When you deploy resources into a subnet, Azure assigns the resource an IP address from the subnet. Learn more >

| Subnets | IP address range | Size | NAT gateway |
| :--- | :--- | :--- | :--- |
| edgateway | 10.10.8.0 - 10.10.8.255 | /24 (256 addresses) | - |
| AzureFirewallSubnet | 10.10.10.0 - 10.10.10.63 | /26 (64 addresses) | - |
| AzureFirewallManagement | 10.10.10.64 - 10.10.10.127 | /26 (64 addresses) | - |

### Figure 10.8: Azure Create Virtual Network IP Address Form

### Tags:

## Create virtual network

- Basics
- Security
- IP addresses
- Tags
- Review + create

Tags are name/value pairs that enable you to categorize resources and view consolidated billing by applying the same tag to multiple resources and resource groups. Learn more about tags

Note that if you create tags and then change resource settings on other tabs, your tags will be automatically updated.

| Name | Value | Resource |
| :--- | :--- | :--- |
| createdBy | James Odeyinka | All resources selected |
| dateCreated | 12/26/2023 | All resources selected |
| application | Edge Gateway VNET | All resources selected |
| EnvType | DEV | All resources selected |

### Figure 10.9: Azure Create Virtual Network Tag Form

You have now finished the virtual network and can click review and create.

### Step 2: Create Azure IoT Hub as populated below. Do not forget that you will need 3-Hubs in different regions.

Check mark "Assign me to the IoT Hub Data Contributor role" in the Management.

The regions we selected for our Azure deployments are as follows:

- Region 1 (Edge 1): West US (California)
- Region 2 (Edge 2): South Central US (Texas)
- Region 3 (Edge 3): East US 2 (Virginia)

While our Central Cloud Region will be North Central US (Illinois).

![](img/31919f230142cc926c349c85b30fe4d2_724_0.png)

### Figure 10.10: Azure IoT Hub Basic Form

## Step 3: Deployment and Installation of OS on Azure VM

Since our edge is located in the cloud, we will use Ubuntu Server 22.04 LTS for our OS deployments. The image can be downloaded using this link. Please use the instruction from canonical if you need help installing it https://ubuntu.com/tutorials/install-ubuntu-server#1-overview

Click Create Azure Virtual Machine. Select SSH as Authentication method. You may need to generate the SSH Key.

Select the Gateway Edge network you created earlier.

- Basics
- Disks
- Networking
- Management
- Monitoring
- Advanced
- Tags
- Review + create

Create a virtual machine that runs Linux or Windows. Select an image from Azure marketplace or use your own customized image. Complete the Basics tab then Review + create to provision a virtual machine with default parameters or review each tab for full customization. Learn more >

This subscription may not be eligible to deploy VMs of certain sizes in certain regions.

### Project details

- Subscription *: Azure Free Subscription
- Resource group *: book127-edge1-westus-network-rg [Create new]

### Instance details

- Virtual machine name *: book127-edge1-svr
- Region *: (US) West US
- Availability options: No infrastructure redundancy required
- Security type: Trusted launch virtual machines [Configure security features]
- Image *: Ubuntu Minimal 22.04 LTS - x64 Gen2 (free services eligible) [See all images | Configure VM generation]

### Administrator account

- Authentication type: SSH public key (selected), Password
- Username *: azureuser
- SSH public key source: Generate new key pair
- Key pair name *: book127-edge1-svr_key

### Inbound port rules

- Select which virtual machine network ports are accessible from the public internet. You can specify more limited or granular network access on the Networking tab.
- Public inbound ports *: None, Allow selected ports (selected)
- Select inbound ports *: SSH (22)
- Info: All traffic from the internet will be blocked by default. You will be able to change inbound port rules in the VM > Networking page.

### Figure 10.11: Azure Create Virtual Machine Basic Form

## Step 4: SSH to the VM and run the following commands:

Login to the -i ~/.ssh/ admin@ip-of-the-vm

Update the OS:

```
sudo apt update
sudo apt install git
git --version
```

Clone the Edge IoT Git: Clone the IoT Edge git repo, which contains scripts to generate demo certificates.

```
git clone https://github.com/Azure/iotedge.git
```

Create a directory in which you want to work and copy the certificate scripts there. All certificate and key files will be created in this directory.

```
mkdir edge1-wrkdir
cd edge1-wrkdir
cp ../iotedge/tools/CACertificates/*.cnf .
cp ../iotedge/tools/CACertificates/certGen.sh .
```

Create the Certificate:

Create the root CA certificate and one intermediate certificate in edge1-wrkdir

```
./certGen.sh create_root_and_intermediate
```

### TIP:

This script command creates several certificate and key files, but when articles ask for the root CA certificate, use the following file:

```
certs/azure-iot-test-only.root.ca.cert.pem
```

### Install Java Development Kit (jdk)

To install jdk, run the following commands from VM command line:

```
sudo apt update
sudo apt install unzip default-jdk
```

### Installing IoT Edge:

```
wget https://packages.microsoft.com/config/ubuntu/22.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
rm packages-microsoft-prod.deb
```

Azure IoT Edge relies on a container runtime that is OCI-compatible. For optimal production scenarios, we strongly advise using the Moby engine, which is the sole container engine officially supported with IoT Edge. Docker CE/EE container images are compatible with the Moby runtime.

To install the Moby engine, run the following commands:

```
sudo apt-get update
sudo apt-get install moby-engine
```

By default, the Moby container engine does not set container log size limits. This may result in the device accumulating logs over time and running out of disk space. While configuring local logging is optional, it is recommended to prevent such issues. Refer to the Production Deployment Checklist for more information on logging configuration.

Follow these steps to configure your container to use the local logging driver as the logging mechanism:

Create the Docker daemon's config file if it does not exist already or open the config file.

JSON
Copy

```
{
"log-driver": "local"
}
```

Restart the container engine for the changes to take effect.

```
Bash
Copy
sudo systemctl restart docker
```

## Step 5: Add Edge Device (VM) to the IoT Hub.

Click Devices on the Device Management of the IoT Hub.

![](img/31919f230142cc926c349c85b30fe4d2_730_0.png)

### Figure 10.12: Azure IoT Hub Overview Blade

After clicking the Devices, you should see the following image.

![](img/31919f230142cc926c349c85b30fe4d2_731_0.png)

### Figure 10.13: Azure IoT Hub Devices Blade

Before the edge VM can connect to the IoT Hub, you must configure the Edge Node properly as described above.

## Step 6: Deployment Data Science VM for Machine Learning Operations

This server will be deployed in the AIML virtual network you deployed earlier above. You can deploy this using Windows or you can use Ubuntu.

Click Create Azure Virtual Machine. Select the image that says "Data Science Virtual Machine".

### Project details

- Resource group *: book127-edge1-westus-network-rg [Create new]

### Instance details

- Virtual machine name *: dev-aiml-app-vm1
- Region *: (US) East US
- Availability options: Availability zone
- Availability zone *: Zones 1. You can now select multiple zones. Selecting multiple zones will create one VM per zone. Learn more
- Security type: Trusted launch virtual machines [Configure security features]
- Image *: Data Science Virtual Machine - DSVM Windows Server 2022 - x64 Gen1 See all images | Configure VM generation

You are in the free trial period. Costs associated with this VM can be covered by any remaining credits on your subscription. Learn more

- Size *: Standard_DS3_v2 - 4 vcpus, 14 GiB memory ($213.89/month) See all sizes
- Enable Hibernation (preview): To enable Hibernation, you must register your subscription. Learn more

### Administrator account

- Authentication type: SSH public key / Password
- Username *: aimladmin
- SSH public key source: Generate new key pair
- Key pair name *: Name the SSH public key

Azure now automatically generates an SSH key pair for you and allows you to store it for future use. It is a fast, simple, and secure way to connect to your virtual machine.

### Figure 10.14: Azure Create Data Science Virtual Machine Form
