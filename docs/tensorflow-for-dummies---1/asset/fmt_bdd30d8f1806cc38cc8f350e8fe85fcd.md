
I love using the GCP because my applications can access Google’s technologies, which include Google Maps, Gmail, YouTube, and AdSense. This chapter focuses on Google’s Machine Learning (ML) Engine, which lets you execute `TensorFlow` applications in the Google Cloud Platform.

## Overview

The good news is that you can dramatically reduce the time required for machine learning by deploying applications to Google’s Machine Learning (ML) Engine. The bad news is that the process of configuring and deploying applications isn’t easy. Five steps are involved:

1. **Create a project for the Google Cloud Platform (GCP) and configure it to use the Cloud Machine Learning API.**
2. **Install the Cloud Software Development Kit (SDK).**
3. **Structure your TensorFlow application as a package.**
4. **Upload your package and processing data to Google Cloud Storage.**
5. **Use the Cloud SDK to execute a training or prediction job.**

In writing this chapter, I assume that you’ve never heard of the GCP. Therefore, before I explain how to deploy applications, I introduce the Cloud Software Development Kit (SDK) and Cloud Storage and explain how to create a GCP project.

## Working with GCP Projects

If you want to take advantage of the GCP’s features, the first step is to create a project. This project serves as the central container of your development effort and includes all your metadata and configuration files. Before you can execute code or launch a web application, you need to upload the files to your project. Similarly, if you’d like access to special features, you need to make requests through the project.

To build a GCP project that can access the ML Engine, you need to perform three steps:

1. **Create a project in the Google Developer Console.**
2. **Enable billing for the project.**
3. **Enable the project to access the Machine Learning Engine.**

![tip](images/tip.png)The `ch13` directory in this book's example code contains two folders: `cloud_mnist` and `cluster_mnist`. These folders contain packages that can be deployed to the ML Engine, but they are not GCP projects. A GCP project resides in the cloud, so if you want to follow the development in this chapter, you need to create and configure a GCP project on your own.

### Creating a new project

Anyone with a valid email address can create a GCP project without any fees or obligations. The process involves five steps:

1. **Visit the Cloud Console at** [`https://console.cloud.google.com`](https://console.cloud.google.com)**.**
2. **If this is your first time visiting the console, provide a contact email address and a password.**
3. **In the upper horizontal bar, click Select a Project.**
4. **In the Select dialog box, click the plus button on the right.**
5. **In the New Project page, enter a project name and click the Create button.**

When working with the GCP, you need to understand the difference between a project's name and ID. A project’s name is chosen by the developer, and the console uses it to display the current project.

In contrast, a project’s ID is chosen by the GCP based on the project’s name, and it uniquely identifies the project across all projects in the GCP. If you want to upload code or change a project's configuration, you’ll need to access your project by its ID. Therefore, it’s a good idea to know the IDs of your projects.

### Billing

Machine learning is a powerful capability, but unlike TensorFlow, it’s not free. Google’s fees for machine learning depend on three factors: the type of operation (training or prediction), the length of time, and your location:

* Training: $0.49 per hour per training unit in the U.S., $0.54 in Europe and Asia
* Prediction: $0.10 per thousand predictions plus $0.40 per hour in the U.S., $0.11 per thousand predictions plus $0.44 per hour in Europe and Asia

Google charges money after you use the ML Engine, not in advance. But you need to identify a means of payment before you use the engine, and you can configure this by associating your project with a billing account:

1. **Visit your project page in the Cloud Console.**
2. **Open the menu (three horizontal bars) in the upper-left and select the Billing option.**
3. **Click the button entitled Add billing account.**
4. **Enter your contact information and billing information.**

At the bottom of the page, a button lets you set up automatic payment, which authorizes Google to withdraw funds from the account as resources are used.

### Accessing the machine learning engine

After you set up a billing account for your project, you can access paid features like the ML Engine. To enable this feature, open the menu in the upper-left of the project page and select APIs & Services. This opens the APIs & Services page, which identifies the features that the project can access.

The left side of the page displays three links: Dashboard, Library, and Credentials. The Library link opens a page that lists the APIs available for your project. To enable access to the ML Engine, you need to perform five steps:

1. **From the APIs & Services page, click the Library link to the left.**
2. **Find the Machine Learning group and click the View All link to the right.**
3. **Click the link entitled Google Cloud Machine Learning Engine.**
4. **Click the Enable link at the top of the page.**
5. **Wait until the GCP grants access to the new capability.**

After performing these steps, you can verify that your project can access the ML Engine by visiting the APIs & Services dashboard. The lower part of the page lists the different APIs your project can access, and this should include Google Cloud Storage and the Google Cloud Machine Learning Engine.

## The Cloud Software Development Kit (SDK)

After you understand how to create a GCP project and configure it to access the ML Engine, you’re ready to interact with your project. Google makes this possible through the Google SDK.

You can download the SDK from [`http://cloud.google.com/sdk`](http://cloud.google.com/sdk). Clicking the Install button opens a page that provides instructions for downloading the SDK installer on your development system. I recommend installing all of the available components.

When you launch the installer, it asks you to log in to your account and grant privileges so that the SDK can access your GCP account. It also asks you to choose a cloud project to serve as the SDK’s default project. After you select this, all further SDK commands affect the default project.

After you install the SDK, you’re able to access two command-line utilities:

* **`gcloud`:** Provides general project interaction and accesses Google’s App Engine, Datastore, DNS, and ML Engine
* **`gsutil`:** Accesses Google Cloud Storage

If you’re running Windows, you can access these utilities through `gcloud.cmd` and `gsutil.cmd`. If you're running Linux or Mac OS, you can access them through the `gcloud` and `gsutil` executables.

Before you start using the SDK, you should make sure that you can access `gcloud` and `gsutil` from a command prompt. If you enter `gcloud version` and you don't see any version information, add the `google-cloud-sdk/bin` folder to your `PATH` environment variable.

## The gcloud Utility

After you install the SDK, you can execute `gcloud` commands on a command line. All `gcloud` commands have the same format:

`gcloud [optional flags] <group | command>`

For example, you can check the version of `gcloud` by entering the following:

`gcloud version`

This command identifies the SDK's version and the versions of its components. You can install the latest components by entering the following command:

`gcloud components update`

In this example, `components` is a *group name* because it requires additional commands, such as `update`. You can think of a group like a submenu in a graphical user interface. In contrast, `version` is a *command name* because it doesn't accept further commands.
