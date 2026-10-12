
# Vertex AI Workbench

The full data science process may be completed in a single development environment with the help of Vertex AI Workbench. Users may utilize the notebook-based environment provided by Vertex AI Workbench to do tasks such as querying and exploring data, developing and training a model, and running your code as part of a pipeline. Vertex AI Workbench provides managed and user-managed notebooks.

Users may build an end-to-end notebook-based production environment with the assistance of Vertex AI Workbench's managed notebooks option, which comes with built-in integrations for your convenience. An option for user-managed notebooks is available inside Vertex AI Workbench for users that need complete command over their working environment.

Both of the available notebook alternatives come preconfigured with `JupyterLab` and have a whole suite of deep learning packages, including support for the `TensorFlow` and `PyTorch` frameworks. Users have the option of using instances with either a CPU or a GPU. The notebook instances provided by Vertex AI Workbench now interact with `GitHub`, allowing users to synchronize the notebook with a repository hosted on `GitHub`.

If users want to use a notebook for data exploration, analysis, or modeling, or want to utilize a notebook as a part of an end-to-end data science process, managed notebooks are often an excellent option to consider. Users can carry out workflow-oriented operations using managed notebooks instances without ever having to leave the `JupyterLab` interface. In addition to this, they also provide a wide variety of connectors and tools for the automation of data science process.

When users establish an instance of user-managed notebooks, users will be prompted to make some selections about the Virtual Machine (VM) that will be used. For example, when users create an instance of user-managed notebooks, users will be prompted to choose both the machine type and the framework that will be used. Users can make changes to the machine type of your instance after it has been created; however, doing so requires that your instance be restarted. Users have the ability to make manual changes, such as changing the software and package versions, on the instance of user-managed notebooks that you are using. Changing the framework that is being used on your instance is a procedure that requires additional effort.

## Vertex AI Workbench creation and working

Follow these steps to create Vertex AI Workbench:

### Step 1: Landing page of Vertex AI

Workbench will be listed in the landing page of Vertex AI as shown in [Figure 4.1](#ch04.xhtml#fig4-1):

![](images/Figure_4.1.png)

**Figure 4.1:** Landing page of Vertex AI of GCP

1. Click on **Workbench**.

### Step 2: Landing page of workbench

The landing page of the workbench is shown in [Figure 4.2](#ch04.xhtml#fig4-2):

![](images/Figure_4.2.png)

**Figure 4.2:** Landing page of workbench of vertex AI

1. Click **ENABLE NOTEBOOKS API** (notebook APIs need to be enabled once for every project. Notebook API can also be enabled from API and services of GCP.
2. Option to create **Managed Notebooks**.
3. Option to create **User-Managed Notebooks**, click on it (we will be using user-managed notebooks in majority of the exercises).
4. Option to create **New Instance**.

### Step 3: New notebook selection

Users will be provided with options to create the instance as shown in [Figure 4.3](#ch04.xhtml#fig4-3):

![](images/Figure_4.3.png)

**Figure 4.3:** New notebook selection (user managed)

1. Click **NEW NOTEBOOK**.
2. Select **Tensorflow Enterprise**.
3. Select **Tensorflow Enterprise 2.6** (we will be developing model using TensorFlow 2.6).
4. Select **Without GPUs**.

### Step 4: TensorFlow notebook creation

After selecting TensorFlow New notebook popup will be shown as shown in [Figure 4.4](#ch04.xhtml#fig4-4):

![](images/Figure_4.4.png)

**Figure 4.4:** Notebook creation

1. Provide **Notebook Name**.
2. Select **US-central** as Region.
3. Select **us-central1-a** as Zone.
4. **ADVANCED OPTIONS** provide users the choice to select the machine type, disk size, also the options on the networking (we can ignore for our case).
5. Click **CREATE**.

### Step 5: Notebook creation complete

It will take a few minutes to complete the creation of notebooks and also the `Jupyter lab` instance. Once created notebook will be listed under the user-managed notebook section of workbench as shown in the [Figure 4.5](#ch04.xhtml#fig4-5):

![](images/Figure_4.5.png)

**Figure 4.5:** Notebook listed under workbench

1. Created notebook is listed.
2. Click **OPEN JUPYTERLAB**.

### Step 6: Opening JupyterLab

After clicking on the `JupyterLab`, a session will be opened in a new tab as shown in [Figure 4.6](#ch04.xhtml#fig4-6):

![](images/Figure_4.6.png)

**Figure 4.6:** Landing page of JupyterLab

1. Button to open launcher (right side window in the figure).
2. Option to Create folder.
3. Option to Upload files from local system.
4. Option to Refresh.
5. Option to Clone git repository.
6. Options to check Kernels and Terminals.
7. More options to connect to git repository.
8. Launcher using which new files can be created.
9. Option to create Python notebook.
10. Option to launch Python notebook console.
11. Option to launch Terminal.
12. Option to create Text File.
13. Option to create Markdown File (`.md` file).
14. Option to create Python File (`.py` file).
15. Options for Show Contextual Help.

## Data for building custom model

For this exercise data is downloaded from Kaggle (link is provided below) and the dataset is listed under CC0:Public domain licenses. Data contains electricity prices for a data center and factors which may influence the price.

[https://www.kaggle.com/datasets/salilchoubey/electrity-prices](https://www.kaggle.com/datasets/salilchoubey/electrity-prices)

`custom_model_ele_prices` bucket is created under `us-centra1` (single region) and `.csv` file is uploaded from to the bucket as shown in [Figure 4.7](#ch04.xhtml#fig4-7):

![](images/Figure_4.7.png)

**Figure 4.7:** CSV data uploaded to cloud storage

Custom model building activity are done in multiple steps:

1. Create a `Dockerfile`.
2. Build the Python code for the ML model building.
3. Create a docker using `Dockerfile` and push the Python code to the docker.
4. Test the docker on the workbench environment.
5. Push the docker to the registry.
6. Submit the training job using created docker.

## Introduction to Containers and Dockers

Containers virtualize the host OS (or kernel) and isolate an app's requirements from other containers. Before containers, having many apps on the same VM sometimes produced unusual behavior, therefore one application per VM was common. One app per VM addressed the conflicting dependency isolation issue, however it wasted resources (CPU and memory). A VM runs your program and a whole operating system, so your application has less resources.

Containers tackle this issue using a container engine and a container image, which is an application's dependencies. The container engine isolates applications by executing them in containers. This eliminates the need to run a distinct OS for each application, increasing resource usage and reducing expenses.

Docker, announced in 2013, revolutionized container technology by allowing users to quickly construct container images of programs. Docker is an open-source virtualization software to help developers. It is a PaaS software that isolates virtual environments to deploy, create, and test applications that are incompatible with the current OS.

### Components of Docker

* **Dockerfile:** `Dockerfiles` start each container. This text file includes instructions to construct a Docker image, including the OS, languages, environmental variables, file locations, network ports, and other components.
