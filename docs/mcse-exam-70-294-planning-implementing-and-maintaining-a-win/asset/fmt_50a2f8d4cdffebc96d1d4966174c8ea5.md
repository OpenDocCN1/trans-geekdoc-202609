
# Group Policy Software Installation

## Assigning Applications to Users or Computers

Applications can be assigned to a user or to a computer by using the appropriate `Software Installation` node in `Group Policy`, as shown in [Figure 10.1](#B9781931836944500167.xhtml#f0010). Using the `Software Installation` node under `Computer Configuration | Software Settings` in the left pane of the `Group Policy Editor` console will allow you to assign the application to a computer. Using the `Software Installation` node under `User Configuration | Software Settings` in the same console tree will allow you to assign the application to a user.

![Figure 10.1 Group Policy Software Installation](images/B9781931836944500167/f10-01-9781931836944.jpg)
Figure 10.1 Group Policy Software Installation

After determining that you want to assign applications (rather than publish them), next you must decide whether to assign applications to users or to computers. Assigned applications are configured based on use. If a particular user will require a word processing or spreadsheet application, you can assign the application to that user. If you will be installing a particular application on every computer in the organization, or to specific computers (for example, all the computers in the Financial department), you can assign the application to the computer objects in `Active Directory`.

![b10-02-9781931836944](images/B9781931836944500167/b10-02-9781931836944.jpg)Exam Warning
You are likely to see questions on the exam that test your ability to work with the `GPO Editor` interface, so get as much hands-on experience as possible to ensure that you can answer these point-and-click questions.

When an application is assigned to a user, the application will show up as a shortcut, on which the user can click. This shortcut does not mean that the application is installed, however. The shortcut can be configured to show up in the `Start menu` or on the desktop. There are also file association changes made to the workstation. This shortcut will "follow" the user, so that it appears on whichever computer the user uses to log on to the network. When the user clicks the shortcut, the application is then deployed to the workstation where the user is logged on. This ensures that users will have the appropriate software, regardless of which workstation they are logged on to.

When an application is assigned to a computer, the software is deployed when it is safe to do so (that is, when the operating system files are closed). This generally means that the software will be installed when the computer starts up, which ensures that the applications are deployed prior to any user logging on. Large application deployments can be done this way so users won't have to click and wait. Applications that are assigned to computers are available to any user who logs on to that computer. Often, administrators will do large deployments to computers during off hours so when users arrive the next day, they have the updated and installed software ready for use.

## Publishing Applications

When an application is published, it is advertised to users through the `Add/Remove Programs` applet in `Control Panel`. This allows users to control when (and whether) the applications will be deployed. Applications that are not required, but which you want to make available as an option for users, are generally deployed this way. If an application isn't used by everybody but might be useful for some to complete a project or task, it can be published for the users to install when and if they need it.

Publishing an application also allows users to uninstall the application from their workstations. This gives users more control over their workstations, whereas assigned applications maintain themselves as installed applications even if the user manually deletes the files.

[Figure 10.2](#B9781931836944500167.xhtml#f0015) shows the matrix between assigning and publishing software to users and computers.

![Figure 10.2 Assigning and Publishing Software Matrix](images/B9781931836944500167/f10-02-9781931836944.jpg)
Figure 10.2 Assigning and Publishing Software Matrix

![b10-03-9781931836944](images/B9781931836944500167/b10-03-9781931836944.jpg)Exam Warning
For the exam, it is important to remember that applications can be assigned to either users or computers, but can be published only to users. If you publish the application, the advertisement attributes are stored in the `Active Directory`. No changes are made to the `Registry` until the application is actually installed. When an application is either assigned or published, an application assignment script (with the file extension `.aas`) is created to hold the advertisement information and the configuration information for the application. This `.aas` file is stored in the `GPO`.

## Document Invocation

Whether you assign or publish an application, file association changes can be made in the `Registry` on the workstation where the new application is installed. Document invocation refers to the ability of the system to install an application in response to the user's attempt to open a document that is associated with that application. This is also referred to as file extension activation. You can control whether applications will be automatically installed by file extension activation. This selection is made by checking a check box on the `Deployment tab` of the `Properties sheet` of the application. You will learn more about editing the Properties options later in the chapter.

For example, if Microsoft Word has been assigned to a computer or user but has not yet been installed, and a user receives a Word document and attempts to open it by double-clicking it, the Installer will immediately install the application and then open the document with it. It is not necessary for the user to install it via the desktop or `Start menu` icon, or (in the case of an application assigned to the computer) reboot the computer. The same thing happens if the application has been published, but the user has not chosen to install it via `Add/Remove Programs`. When the user attempts to open the documents, it will be installed automatically. This is also called on-demand installation.

What happens if more than one application is associated with the same file extension? Normally, the associated application that was most recently installed on the computer is the one that is used to open the file. You can configure the `GPO` to set priorities on file extensions, so that you can ensure that the published application that installs when users try to open a file with a specific extension is the right one. This is done by editing the `Software Installation Properties` of the `User Configuration` or `Computer Configuration` node in the `GPO Editor`. You will learn more about editing these options later in the chapter.

## Application Categories

To make it easier for users to find applications, you can put software into categories. With a large number of applications, users must scroll through the entire list of programs in `Add/Remove Programs` to find the applications they want. To simplify the process, you can categorize the applications you assign or publish.

Categories are not predefined and thus need to be set up by the administrator. Grouping common applications together will assist your users in finding the software they need. You can group applications by department, by job function, or in other ways that are logical and meet the needs of your organization's structure. For example, all members of a particular department might need to use the same application, or all secretaries—regardless of department—might need a particular software application. It is not necessary to define categories for each individual `GPO`; instead, you create categories that will apply to the entire domain.

## Group Policy Software Deployment vs. SMS Software Deployment
