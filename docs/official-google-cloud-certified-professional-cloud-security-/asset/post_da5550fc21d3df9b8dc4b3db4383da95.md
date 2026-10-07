
## 4 Resource Management

In this chapter, we will look at resource management and understand some of the key components, such as projects, folders, and organizations. When building your environment on Google Cloud, these components can help you do segmentation in a macro level. We will also look at organizational policy constraints, some of the pre-built constraints that are available, and how the inheritance of policy works for **Identity and Access Management (IAM)** and firewall rules. We will also cover Cloud Asset Inventory, which is an essential part of resource management, and its role from a security perspective. We will end the chapter with some best practices and design considerations for resource management.

In this chapter, we will cover the following topics:

- Overview of Google Cloud Resource Manager
- The resource hierarchy
- The Organization Policy Service
- Organization Policy constraints
- Policy inheritance
- Hierarchical firewall policies
- Cloud Asset Inventory
- Design considerations and best practices

## Overview of Google Cloud Manager

Google Cloud Resource Manager acts like a container for your cloud resources, allowing you to group your resources in a hierarchical way within the project, folder, or organization. Think of Resource Manager as a high-level way to perform macro-level segmentation. This not only helps you define the entire organization's structure but also the implementation of security guardrails that can be inherited. More on this in the Policy inheritance section.

**Figure 4.1** is an example of how you can structure your organization on Google Cloud. The top-level organization is where all other components such as folders and projects are created. Organizing your resources in a hierarchical way lets you manage aspects such as access control and other configuration settings. The same applies to IAM policies, which can be applied at different levels and are inherited top-down.

## Organization hierarchy

![](img/f681dfc12450e3a4c257352b70dbceca_66_0.png)

Figure 4.1 – Organization hierarchy

Let's take a look at the key components that make up the organization hierarchy and further explore how policies are applied and inherited and some best practice examples for organization structure.

## Understanding resource hierarchy

The key components that make up the resource hierarchy are as follows:

- Organization: The top-level component—all other components are linked to this.
- Folders: Used to group similar projects to consistently apply policies. These are optional but highly recommended.
- Projects: Where all the resources, such as your compute instances, databases, and others, exist.

Now, let's look at each of these components in detail. From a certification standpoint, you will be tested on resource hierarchy and the topics covered in this chapter. It's important to understand how to manage and create resources and apply policies and organizational constraints. We will cover all these topics in this chapter.

## Organization

This is the root node and hierarchical super-node of the project. It is closely associated with the Workspace / Cloud Identity account. It's a single directory containing the organization's users and groups. The organization is created from the Cloud Identity account. After creating a Cloud Identity organization, you need to manually create an organization or groups through the console to provision the GCP organization. The organization doesn't contain users or groups rather holds GCP resources. Users and groups are part of Cloud Identity, but they receive IAM permissions in GCP. The organization at the top-level node represents, for example, a company in the resource hierarchy: Google Identity and Workspace are provisioned within one organization. When a user creates a project in Google Cloud, only then is an organization automatically created. Organizations are also needed to manage the resource lifecycle. They act as central resource management for all projects that are created. All members of the organization belong to the organization by default. With an organization, you can also apply policies across all resources, such as IAM policies and organization policies. We will cover this in the Policy inheritance section later in this chapter.

In the following figure, let's understand the link between Cloud Identity and Workspace. The link between Google Cloud Identity and Google Workspace is that Google Cloud Identity provides the foundation for user authentication and access management, which is used by Google Workspace to manage and secure user accounts and access to its suite of productivity tools. You cannot have an organization without Cloud Identity (which is a prerequisite). It's important to note that the Cloud Identity / Workspace admin is the overall owner of the domain verification and also has the right to create any IAM role in Google Cloud.

> Note
You can read more about Cloud Identity in Chapter 5, Understanding Google Cloud Identity.

![](img/f681dfc12450e3a4c257352b70dbceca_68_0.png)

The organization is exposed and has the following:

```json
{
  "createTime": "2020-01-07T21:59:43.3142Z",
  "displayName": "my-organization",
  "lifecycleState": "ACTIVE",
  "name": "organizations/347391823",
  "owner": {
    "customerId": "C01234"
  }
}
```

In the preceding snippet, the number 347391823 is the unique identifier.

## Understanding resource hierarchy

The organization's creation time and last modified time are also recorded; my-organization is the display name and it cannot be changed.

## Folders

The main function of folders is to group similar projects. Similar to organizations, folders have certain parameters and are used to model your structure. Look at Figure 4.3 to understand how you can use folders in GCP.

![](img/f681dfc12450e3a4c257352b70dbceca_69_0.png)

Figure 4.3 – Example organization structure

## Resource Management

In this example structure, the first level represents departments, such as X and Y. As folders have the capability to go up to 10 levels deep (a hard limit), you can create more folders to represent different teams and products. This gives you ability to define access control and permissions at the department, team, or product level. Note policy inheritance is top-down; it is also possible to move projects, but you have to be mindful of policy inheritance, as that should be applied.

## Projects

A project is a base-level object that is required for Google Cloud. Your organizations can contain projects and folders. Project is where all your cloud resources are created. Each project is completely separate from other projects and so are the resources inside it. Projects are useful to group specific resources from a functional and access standpoint. There is no cost associated with creating projects and you can create as many as you want (important to note that there are limits that may apply based on the account type, such as Enterprise versus Developer). Projects are not bound to geographical location and serve as an IAM enforcement point.

Let’s take a look at the construct of a project and what it consists of using the example snippet:

```json
{
  "createTime": "2020-01-07T21:59:43.3142Z",
  "lifecycleState": "ACTIVE",
  "name": "my-project",
  "parent": {
    "id": "634792535758",
    "type": "folder"
  },
  "projectId": "my-project",
  "labels": {
    "my-label": "prod"
  },
  "projectNumber": "464036090314"
}
```
