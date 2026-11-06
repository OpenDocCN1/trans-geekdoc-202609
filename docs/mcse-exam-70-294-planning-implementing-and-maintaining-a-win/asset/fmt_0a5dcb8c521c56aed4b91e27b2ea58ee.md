
## 5. Open GPO and add application to Marketing OU

A. Open `Active Directory Users and Computers`. Navigate to the `Marketing OU`, right-click, and select `Properties`. Click the `Group Policy` tab and select `Edit`. In the `GPO Editor` window, expand the `User Configuration` node, select `Software Installation`, right-click, choose `New`, and then choose `Package`.

B. Open `Active Directory Users and Computers`. Navigate to the `Marketing OU`, right-click, and select `Properties`. Select `Edit`. In the `GPO Editor` window, expand the `User Configuration` node, select `Software Installation`, right-click, choose `New`, and then choose `Package`.

C. Open `Active Directory Users and Computers`. Navigate to the `domain node`, right-click, and select `Properties`. Click the `Group Policy` tab and select `Edit`. In the `GPO Editor` window, expand the `User Configuration` node, select `Software Installation`, right-click, choose `New`, and then choose `Package`.

D. Open `Active Directory Users and Computers`. Navigate to the `Marketing OU`, right-click, and select `Properties`. Click the `Group Policy` tab and select `Edit`. In the `GPO Editor` window, expand the `Computer Configuration` node, select `Software Installation`, right-click, choose `New`, and then choose `Package`.

☑ A. To open the GPO and add the application to the `Marketing OU` so the software will be deployed at the OU level, you must use `Active Directory Users and Computers` to access the appropriate GPO. You do this by accessing the `Properties` of the OU, then selecting the appropriate GPO on the `Group Policy` tab and editing it. This opens the `GPO Editor`. From here, you select `User Configuration` because you want to deploy the software to users rather than computers. To add a package, you select `New` from the context menu, and then select `Package`.

⌧ Answer B is incorrect because you have to select the `Group Policy` tab before you can select `Edit`, and this step is left out. Answer C is incorrect because you don’t want to deploy the software to the entire domain, which is what you will accomplish if you follow these steps. Answer D is incorrect because following these steps would deploy the software to computers instead of to users, as specified in the scenario.

## 6. What steps should you take to set up a new category for software distribution?

A. Right-click `Software Installation` in the `GPO Editor` and select `Properties`. Go to the `Categories` tab. Click `Add`.

B. Right-click `Software Installation` in the `GPO Editor` and select `Properties`. Go to the `General` tab. Click `Add`.

C. Right-click the package in the right pane of the `GPO Editor`, select `Properties`, and then click the `Categories` tab. Click `New`.

D. Right-click the package in the right pane of the `GPO Editor`, select `Properties`, and then click the `General` tab. Click `New`.

☑ A. The `Categories` tab in the `Properties` of `Software Installation` is the proper interface for creating and managing categories into which you can place applications to make them easier for users to locate and install.

⌧ Answer B is incorrect because the `General` tab does not allow you to administer category information. Answers C and D are incorrect because right clicking the package in the right pane of the console will allow you to configure its properties, but does not allow you to manage categories.

## 7. Which of the following tabs and options are used to force applications to update when deploying upgrades, regardless of whether the user wants to upgrade the application?

A. `Required upgrade for existing package` on the `Upgrades` tab

B. `Mandatory upgrade` on the `Upgrades` tab

C. `Required upgrade` on the `Modifications` tab

D. `Mandatory upgrade` on the `Modifications` tab

☑ A. The `Required upgrade for existing package` option exists on the `Upgrades` tab. Checking this check box will force an upgrade of the application on each computer on which it is installed, regardless of whether the user wants to perform an upgrade.

⌧ Answers C, B, and D are incorrect because these options reference the wrong tab or the wrong options on the correct tab.

## 8. You are a network administrator and you have a number of legacy applications that need to be repackaged

You will be using `WinINSTALL LE 2003` to create `.msi` packages for these applications. You have decided to set up a workstation that will be dedicated to creating these application packages. Which of the following is the best type of machine to use for this purpose?

A. An existing computer configured with an optimized operating system that has been in service for at least two years.

B. A newly installed computer with a clean Registry and default operating system configuration.

C. An existing computer that has all of your organization’s applications installed.

D. A new computer running only the critical applications but the original Registry settings.

☑ B. A newly installed computer with a clean Registry and default operating system configuration is the best choice for this purpose. To avoid potential software conflicts and problems that can interfere with the creation of application packages, it is best to have a clean machine with a newly installed operating system, a clean Registry, and no extra applications installed. This makes the behavior of the system more predictable and makes it less likely that you’ll have problems.

⌧ Answer A is incorrect because an existing machine that has been in service for two years could present problems, because it is likely that there have been programs installed and uninstalled, Registry settings modified, and other unknown configuration changes made during the time it has been in use. Answer C is incorrect because you do not want all of the organization’s applications installed. Installing applications makes changes to the Registry and can install files that might conflict with or interfere with your ability to create clean package files. Answer D is incorrect because the original Registry settings would cause potential issues with application running properly.

## 9. Limitations of using .zap files for software deployment

You need to deploy an older application to users on your network, and you want to use `Group Policy Software Installation` to make the deployment easier. However, you are undecided as to whether you should use a program such as `WinINSTALL` to repackage the application or use a `.zap` file to install it. In making this decision, you consider the limitations of using `.zap` files and whether these limitations will affect your deployment. Which of the following are limitations of using `.zap` files that should be factored into your decision? (Choose all that apply.)

A. Applications deployed with `.zap` files cannot be installed by double-clicking a shortcut.

B. Automatic repair and removal doesn’t work for applications deployed with `.zap` files.

C. Creating `.zap` files requires more programming expertise than repackaging applications does.

D. `.zap` files install applications with elevated user privileges.

☑ A and B. One limitation of deploying applications with `.zap` files is that document invocation does not work; thus the installation cannot be started by double-clicking a file associated with the application, as can be done with applications deployed with `.msi` packages. Another, perhaps more significant limitation, is that the automatic repair and removal features don’t work with applications deployed via `.zap` files. If files for such an application become corrupt or are missing, the system will not automatically replace or repair them as it can with applications deployed via `.msi` packages. Moreover, you cannot select to have the application automatically removed if the GPO ceases to apply to the users to which the application is deployed.
