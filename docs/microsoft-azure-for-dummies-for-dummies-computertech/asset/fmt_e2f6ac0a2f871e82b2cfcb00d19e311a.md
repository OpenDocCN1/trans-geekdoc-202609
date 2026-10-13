
From now on, when I give you suggested choices on these deployment blades, I’ll leave out fields you already know about, such as Subscription, Resource Group, and Region. Use the following information to complete the other fields:

*   **Virtual Machine Name:** The name needs to be unique only within your resource group. Pay attention to the validation helpers that pop up when you place your cursor in a field.
*   **Availability Options:** If you don’t see both Availability Zone and Availability Set in the drop-down menu, choose a different region. (East US 2 is a good choice.) Because this is a practice deployment, you can choose No Infrastructure Redundancy Required.
*   **Image:** You specified the Ubuntu image in step 1, but if you’re curious about other options, open the drop-down menu to see the most popular VM images. You can also click Browse All Public and Private Images to view all templates in the Azure Marketplace.
*   **Size:** For now, accept the Microsoft-recommended default VM size.
*   **Authentication Type:** Linux VMs are different from Windows because you can use Secure Shell (SSH) key-based authentication or password-based authentication. For this exercise, choose password.

    ![Remember](images/remember.png) You should choose a creative default administrator account name. ARM won’t let you use commonly guessed administrator account names such as `root` or `admin`.

*   **Public Inbound Ports:** For testing purposes, associate a public IP address with this VM, and connect to the instance via SSH.

    ![Tip](images/tip.png) You’ll tighten network security group security later to prevent unauthorized access attempts by Internet-based bad actors.

*   **Select Inbound Ports:** Choose SSH.

### Complete the Disks tab

This tab is where you make an initial choice about the VM’s OS and data disks. Choose Standard HDD to save money. (Refer to “[Storage](#c05.xhtml#c05-sec-0008)” earlier in this chapter for more information about the various options.)

The number of data disks you can create depends on your chosen VM instance size. You can always add data disks later, so for now, proceed to the next blade. Note that the default number of data disks Azure provides the new VM is zero; it’s up to you as administrator to decide whether you want to use them.

### Complete the Networking tab

You have some crucially important decisions to make in terms of where you want to place your VM and how you want to configure its connectivity. Here are the configuration options:

*   **Virtual Network:** The template deploys a new virtual network by default. That’s what you want here, so leave this setting alone.

    ![Warning](images/warning.png) If you place your VM on the wrong virtual network, you’ll need to redeploy it to move it, which is a pain, so try to make the right choice the first time around.

*   **Subnet:** Leave this setting at its default.
*   **Public IP:** Leave this setting at its default. You do in fact want a public IP address, at least initially.
*   **NIC Network Security Group:** Select Basic.
*   **Public Inbound Ports:** Allow Selected Ports.
*   **Select Inbound Ports:** Select SSH.
*   **Accelerated Networking:** Not all VM templates support this option. For VM templates that support this feature, accelerated networking gives the VMs a network speed boost by allowing the VM to use the Azure networking backbone more directly.
*   **Load Balancing:** Select No.

### Complete the Management tab

Ensure that Boot Diagnostics is enabled and all other options are off. Boot Diagnostics is required to use the VM serial console, so it’s always a good idea to enable it sooner rather than later.

### Review the Advanced and Tags tabs

You don’t need any of these options right now, but they’re worth examining. Extensions allow you to inject agent software and/or management scripts into the VM. You can handle configuration after deployment, however.

Taxonomic tags are a way to track resources across subscriptions for accounting purposes.

### Submit the deployment, and monitor progress

Click the Review + Create tab; then click Create after ARM informs you that your selections passed validation. If an error occurs, ARM places a red dot next to the configuration blade(s) where it detects invalid settings.

## Connecting to the VM

Use Azure Cloud Shell to make an SSH connection to your VM. Follow these steps:

1.  **In Azure portal, browse to the Overview blade of your newly created VM, and note the public IP address.**

    You can see my VM’s configuration in [Figure 5-4](#c05.xhtml#c05-fig-0004).

2.  **Open Cloud Shell, and connect to your Linux VM by specifying your default administrator account name and the VM’s public IP address.**

    To connect to my Linux VM at `13.68.104.88` using my `tim` admin account, I type:

    ```
    ssh tim@13.68.104.88
    ```

    Type **yes** to accept the VM's public key and then type your password to enter the SSH session. At this point, you’re working directly on the Linux VM.

![Tip](images/tip.png) You can get help for any Linux command by typing `man <command-name>`. Scroll through the Help document with your arrow keys, and press Q to quit.

## Deploying a Windows Server VM

In this section, I explain how to create a Windows Server VM by using Visual Studio 2019 Community Edition and an ARM template.

![FIGURE 5-4: Most admins use SSH (with or without Cloud Shell) to manage Linux VMs in Azure.](images/9781119612148-fg0504.png)

[FIGURE 5-4:](#c05.xhtml#rc05-fig-0004) Most admins use SSH (with or without Cloud Shell) to manage Linux VMs in Azure.

Visual Studio 2019 Community Edition ([`https://visualstudio.microsoft.com/vs/community`](https://visualstudio.microsoft.com/vs/community)) is a free Visual Studio version that you can use for testing, development, and open-source projects.

![Tip](images/tip.png) Although I use Windows as the workstation OS in this book, Microsoft does make a Visual Studio version for macOS. Visit [`https://visualstudio.microsoft.com/vs/mac`](https://visualstudio.microsoft.com/vs/mac) for details.

This procedure is especially important for you to understand for two reasons:

*   ARM templates form a basis for administrative automation, development, and operations.
*   You’ll use ARM templates to complete tasks that I cover later in the book.

### Setting up your development environment

Follow these high-level steps to get your Visual Studio environment set up:

1.  **Download Visual Studio 2019 Community Edition, and run the installer.**

    You need administrative permissions on your Windows 10 workstation to install the software.

2.  **Choose the Azure workload.**

    This step is the most important one. Visual Studio is an integrated development environment that supports multiple development languages and frameworks. For the purpose of deploying a Windows Server VM, you need to install the Microsoft Azure software development kits and tools.

    [Figure 5-5](#c05.xhtml#c05-fig-0005) illustrates the user interface. You can leave the Azure workload components set at their defaults.

    ![FIGURE 5-5: Installing the Azure SDKs in Visual Studio 2019.](images/9781119612148-fg0505.png)

    [FIGURE 5-5:](#c05.xhtml#rc05-fig-0005) Installing the Azure SDKs in Visual Studio 2019.

3.  **After installation, open Visual Studio, and log in to your Azure administrator account.**

    When you start Visual Studio 2019, you’ll see a Get Started page. Click Continue Without Code; then open the Cloud Explorer extension by choosing View ⇒ Cloud Explorer. Authenticate to Azure Active Directory, and select the Azure subscription(s) you want to work with.

### Deploying the VM
