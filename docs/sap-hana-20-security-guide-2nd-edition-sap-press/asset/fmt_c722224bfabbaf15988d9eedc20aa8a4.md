
Finally, all the functionalities found in SAP HANA Studio work even with SAP HANA 2.0 SPS 04-based systems. In this book, much of our discussion is focused on solutions based on the SAP HANA XS model. This focus is because its replacement by the SAP HANA XSA framework does not currently provide enough control over security nor does it offer scalable security mechanisms to properly manage an SAP HANA database security model. Our hope is that SAP will address these gaps before the SAP HANA XS environment is removed from the platform.

With the SAP HANA XSA framework, SAP HANA development occurs within a service layer called the SAP HANA Deployment Infrastructure (HDI). While the infrastructure of an HDI container is quite different from the SAP HANA XS-based model, think of HDI containers in SAP HANA XSA as a replacement for the XS `_SYS_REPO` repository. An SAP HANA instance can only have a single XS `_SYS_REPO` repository. However, that same instance can support multiple HDI containers. This versatility allows you to both segregate one HDI container from another as well as deploy multiple versions of the same object into the same database instance. We’ll discuss HDI containers in more detail in [Section 18.4](#18_004.html#h18.4).

In the subsequent sections of this chapter, we’ll review HDI containers and show you the mechanisms for securing the database artifacts that HDI containers produce. In the next section ([Section 18.2](#18_002.html#h18.2)), we’ll provide you an overview of the security mechanism of the SAP HANA XSA platform. Because SAP HANA XSA is largely decoupled from the database, it has its own independent authorization mechanism and organizational structure. Note that SAP HANA XSA shares users and authentication mechanisms with its associated tenant or SYSTEM database. Let’s look at the process you’ll use to govern the SAP HANA XSA platform.

## 18.2 Managing Space Access, Users, and Roles Collections in SAP HANA XSA

Within SAP HANA, the development environment of SAP HANA XSA is structured into units called organizations and spaces. This structure is required to support a multi-target application (MTA) architecture. An MTA is designed to help consolidate application development by compartmentalizing the components of a typical web application solution while hosting these components in a single platform. Most web application components are developed in a variety of different coding languages, perhaps each with their own environments, lifecycle management, and disconnected operating system services. With the MTA architecture, you can combine and manage these diverse elements into a single solution. This consolidation enables you to manage dependencies, services, code, lifecycle, and security within a single platform. For example, a typical web application consists of a Java application server backend, a Node.js and HTML frontend, and a database backend for data storage. With SAP HANA and the SAP HANA XSA platform, you can manage the code, services, and lifecycle all within one or more HDI container spaces. SAP HANA XSA provides the runtime for each code base and provides the database backend.

Within the SAP HANA XSA MTA architecture, application development content is organized into organizations and spaces. Let’s start with an explanation of spaces. A space defines a container where all applications within that container share common code and resources and trust each other. Spaces can be shared by multiple developers, but developers can also have their own “sandboxes” for testing. Remember that a space has both runtime and design-time aspects. Design-time code is not directly accessible within a space between developers. Developers must share their code outside of the SAP HANA XSA tools. SAP Web IDE for SAP HANA, hosted as an application within the SAP HANA XSA, is tightly integrated with GitHub, a web-based platform, designed to host code. GitHub is well suited for version control and developer collaboration. Its cloud-based or on-premises services help developers work together on projects.

Organizations are units that can be associated with one or more spaces. Spaces can only be associated with one organization. This grouping helps from a security standpoint and has limited impact on the runtime aspects of a space. The only impact would be organization-specific domains used in the crafting of the application’s external URLs. In SAP HANA XSA, you’ll use organizations to host one or more spaces. In turn, you can establish security at the organization level, allowing each space to inherit that same security.

Within SAP HANA XSA, you can create users, role collections, organizations, and spaces. These components are the basis for security within SAP HANA XSA. When SAP HANA XSA was first introduced, you could use a combination of the SAP HANA XS command line and the SAP HANA XSA administration graphical user interface (GUI) to administer SAP HANA XSA. However, starting with SAP HANA 2.0 SPS 03, the SAP HANA XSA cockpit was introduced, and the SAP HANA XSA administration tools were deprecated. With all versions of SAP HANA XSA, the SAP HANA XS command line utility for SAP HANA XSA can also be utilized for administration. However, for simplicity, we’ll focus on the SAP HANA XSA cockpit in this chapter.

In this section, we’ll first walk you through accessing applications in SAP HANA XSA and then move on to the process for creating SAP HANA XSA users and for establishing SAP HANA XSA security using the SAP HANA XSA cockpit.

### 18.2.1 Accessing Applications

When SAP HANA XSA is installed and applications are imported into its platform, one option is to give each application its own dedicated TCP/IP port. You’ll use the port and the host name of the SAP HANA XSA application server to craft the URL for accessing applications hosted within SAP HANA XSA. The most definitive way to find the port of an SAP HANA XSA application is to use the command line utility to list each application and the URL with the port that is listening to service browser access. The SAP HANA XS command line can be accessed through the operating system of the SAP HANA database, but you can also download and install it. See SAP Note 2242468 for instructions on installing the SAP HANA XSA command line. However, in this chapter, we’ll focus on using the command line installed on the SAP HANA server.

To access the SAP HANA XSA command line on the SAP HANA server, log on using Secure Shell (SSH) and your provided credentials. If you have the password for the `<sid>adm` Linux user account, log on with those credentials. If not, start by switching to that user’s session using the following commands:

```
sudo -i -u <sid>adm
```

To access the SAP HANA XSA command line, start by logging into SAP HANA XSA using the following command:

```
xs login
```

If the SAP HANA XSA command line interface requests the URL for the application programming interface (API) endpoint, enter the following:

```
https://<hana-xsa-hostname>:30030/
```

When requested, log on with the default SAP HANA XSA credentials or credentials provided to you from the SAP HANA XSA admin. Note that the default SAP HANA XSA account user is typically `XSA_ADMIN`, but during installation, a custom name can be provided.

Run the following command to list the SAP HANA XSA applications currently deployed:

```
xs a
```

A list of installed applications will appear, as shown in [Figure 18.2](#18_002.html#f18.2). The name of the application will appear in the first column, and the URL used to access the application will appear on the far-right column.

To access the `xsa-cockpit` application, locate it in the list of applications. Note the URL and port needed to access the application. As shown in [Figure 18.2](#18_002.html#f18.2), we’ll use the following partially masked URL:

```
https://##hana-01:51030
```
