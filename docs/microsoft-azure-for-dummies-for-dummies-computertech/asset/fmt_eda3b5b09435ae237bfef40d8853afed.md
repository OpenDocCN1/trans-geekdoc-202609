
## Experiment with the other metrics controls in Azure Monitor

Check out these controls:

*   **New Chart:** You can create a chart showing something such as Azure storage account read transactions.
*   **Line Chart:** Try changing the plot type to observe how the view changes your data's visibility.
*   **New Alert Rule:** You can generate alerts, notifications, and remediation actions based on defined metric thresholds (such as triggering an alert when your Linux VM exceeds your predefined CPU utilization threshold).
*   **Pin to Dashboard:** You can use the Azure dashboard as a business intelligence dashboard.

# Chapter 6: Shipping Docker Containers in Azure

## In This Chapter

*   Understanding Docker and containers
*   Reviewing Azure support for Docker container
*   Implementing Azure Container Instances and Azure Container Registry
*   Touring Azure Kubernetes Service
*   Deploying a Docker container in an Azure App Service web application

Docker containers are taking over the world!

Okay, maybe I need to tone down the hyperbole. Many businesses are realizing the financial benefits of using Docker containers in their development and production environments. In a nutshell, Docker containers make it a lot faster and easier for developers to build software products.

Microsoft supports Docker containers in its cloud in myriad ways. You may not be a Docker expert by the time you finish this chapter, but I'm entirely confident that you'll grasp the use of containers and the possibilities of using Docker in Azure.

## Understanding Docker

If you've read [Chapter 5](#c05.xhtml), you probably have a pretty good idea of what virtual machines (VMs) are and how they work. To me, Docker containers represent a more agile degree of virtualization. Containers allow developers or administrators to package an application and all its dependencies into a single, modular unit that can be deployed quickly.

> **Remember:** A Docker container is a virtualized application, not an entire VM. You might create and run Docker containers running different databases and database versions against which to test your application. These containers contain (see what I did there?) only the database engine binaries and their dependencies — nothing more.

Whereas each VM may weigh hundreds of gigabytes and need to be updated, backed up, monitored, and maintained, containers can range from less than 100 MB to a few gigabytes.

Like VMs, containers share hardware resources with their container host server. Unlike VMs, containers are defined fundamentally in plain-text `Dockerfile`s, which contain the instructions for building a container.

The idea is to put all the assets that will comprise your container in a single directory and create a `Dockerfile` that orchestrates the container's composition. Then you compile the `Dockerfile` into a binary image, which serves as your deployment unit. Finally, you create as many containers as you need by deploying instances of your image template. [Figure 6-1](#c06.xhtml#c06-fig-0001) illustrates the Docker deployment process.

> **Tip:** Docker is an enormous topic that could fill a separate book. If you want to know more about creating container images, check out the Docker documentation at [`https://docs.docker.com`](https://docs.docker.com).

![FIGURE 6-1: The Docker container deployment process.](images/9781119612148-fg0601.png)

[FIGURE 6-1:](#c06.xhtml#rc06-fig-0001) The Docker container deployment process.

> **Technical Stuff:** Application virtualization existed in Linux long before Docker. Docker is a business that simply standardized and extended these preexisting technologies. Microsoft and Docker partnered primarily to bring Docker containers to Windows Server, and this chapter deals almost exclusively with Windows Server containers.

### Using Docker containers

Developers love Docker containers because containers are agile. As I mention earlier, `Dockerfile`s are plain-text documents, which means that development teams can store them in source-code control and track their changes over time.

Suppose that Jane Developer needs to test her business's line-of-business application against three MySQL database versions. Starting three separate VMs is ordinarily a slow, labor-intensive process. This pain becomes greater when she needs to spin up and work with multiple instances of each VM-based MySQL installation. If the VM's guest operating system needs an update or if MySQL requires an update, the process is even slower.

By contrast, Jane can use the Docker command-line interface or a hosted container platform to start up any number of MySQL containers running different software versions. When she finishes testing, she disposes of the containers with a single command. If MySQL needs an update, she or a teammate can simply edit the `Dockerfile` and recompile an image.

Portability is another huge advantage of containers. Microsoft Azure is a Hyper-V ecosystem. What if you need to migrate your VMs to, say, Google Cloud Platform, where they use another hypervisor?

I've spent way too much time reconfiguring virtual machines so they fit into different cloud providers' ecosystems. With Docker, you have a universal format that works across any cloud that supports Docker.

As long as you have the Docker daemon (server service) component available, you can run your containers almost anywhere with no modification.

### Setting up Docker on your workstation

The Docker run-time environment is relatively lightweight and portable. In this section, I show you how to install Docker Desktop on your Windows 10 workstation.

> **Remember:** For purposes of this book, I assume that you're working on a Windows 10-based computer. Docker Desktop and its associated tools are also available for macOS and Linux, however. Docker does a good job of standardizing the user interface, so you should find the following steps work for you if you are on macOS or Linux.

#### Installing Docker Desktop

Follow these steps to set up Docker on your Windows 10 system:

1.  **Register for a free user account at Docker Hub.**
    Docker Hub ([`https://hub.docker.com`](https://hub.docker.com)) is the main public repository for Docker containers.

2.  **Download and install Docker Desktop from** [`https://www.docker.com/products/docker-desktop`](https://www.docker.com/products/docker-desktop)**.**
    The website encourages you to work through an interactive tutorial; do so at your leisure.

3.  **Accept the default settings during installation.**
    The exception to this rule occurs when the installer asks whether you want to use Windows containers instead of Linux containers. Select Windows containers. You won't see this option on macOS or Linux computers.

4.  **Restart your computer.**
    The installer requires you to log out and restart to install the Hyper-V and Containers Windows 10 features.

5.  **Verify that the Docker service is running.**
    Docker Desktop appears as an icon in the Windows notification area (see [Figure 6-2](#c06.xhtml#c06-fig-0002)).
    Right-click the Docker icon, and you'll see all sorts of options on the shortcut menu (including to Switch to Windows Containers if you forgot to enable that feature during installation). [Figure 6-2](#c06.xhtml#c06-fig-0002) shows Switch to Linux Containers, which Docker displays if you're currently configured for Windows containers.

> **Remember:** The Docker service needs to run with elevated permissions. If you find that Docker Desktop doesn't put its icon in your notification area, run the app from the Desktop or Start-menu shortcut as an administrator.

#### Running the hello-world container
