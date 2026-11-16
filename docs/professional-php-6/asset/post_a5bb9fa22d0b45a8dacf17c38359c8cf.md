
## Part III: A Real-World Case Study

Now, log in as `administrator`. By default, the password has been set in the PostgreSQL database generation script to be `administrator`.

After you’ve logged in, you should first lock down your Mantis installation. The best way to do this is to create another account, not named `administrator`, with a more secure password that you can use for day-to-day administration. This is particularly important if you are able to access your Mantis installation over the public Internet.

You may also notice that your installation of Mantis implores you at login to delete the `admin` directory from your installation. You should do just that. You won’t need that folder anymore, so either delete it or remove it from your Web server’s document root entirely. Once it’s removed, the nagging message disappears accordingly.

### Creating and Editing Users

Everyone who will have access to Mantis (that is, yourself, your development team, and maybe your client’s representatives) will require a user account.

To create an account, click the Manage link when logged in as an administrator. “Manage Users” is selected by default, and, accordingly, you will see a list of user accounts on the system. Creating a new account is as simple as clicking Create New Account. Don’t forget to set the access level to an appropriate level. Anyone whose only task is to report bugs or defects can be set as a reporter, whereas you want your own account to be administrator.

After you have created all the necessary user accounts (including at least one with administrative privileges), you can completely remove the administrator account.

Once a user is created, you can modify even more properties of that user’s account by clicking his or her username. Figure 20-3 shows a typical user editing session in Mantis.

![](img/a1b732997d9cb194dceec0570dc79710_553_0.png)

Figure 20-3: Typical user editing session in Mantis

### Adding a User to a Project

Crucially, you can use the Edit User screen not only to edit the user’s details, but also to add that user to a project. By default, a user does not have access to any projects, which means that even if he or she has reporter status, that user can’t report any bugs.

To add the user you are editing to a project, select the project in question (if this is your first time using Mantis, you won’t have any yet) and click Add. If a project is marked as public, you can skip this step because all users will have access. This is very rarely desirable, especially if you have clients using the system.

Note that when creating an account, your new users will automatically be sent an e-mail message containing their usernames and passwords, and the URL for accessing this installation of Mantis. If this behavior is not desirable, you can disable it in the Mantis configuration file you were editing a few moments ago.

### Creating New Projects

There is no limit to the number of projects that Mantis can support.

To create a new project, select the Manage Projects link toward the top of the screen. A similar view to that shown in Manage Users will be shown, with all current projects displayed. To create a new project, click Create New Project.

Initially, you will be asked to specify a project name, status (which is an arbitrary flag for your own reference), view status (which should be set to private for the reasons discussed previously), description, and an upload file path. The upload file path is the place where any binary files (such as screenshots of the bugs being replicated) attached to bugs lodged in the system will be stored. This must be writable by the Web server, which you may need to effect by manually changing the permissions of that particular folder on your server.

### Setting Up Project Bug Categories

After you have created a new project, you can edit its finer details by clicking its name. The most important detail you will want to set is the categories for the project. Each defect entered into the system can be placed in a category, and you will want to define as many as you see fit. Figure 20-4 shows a typical project being managed in this way, with bug categories being added to make the project ready to use.

![](img/a1b732997d9cb194dceec0570dc79710_555_0.png)

Figure 20-4: Managing a typical project

You may want to have categories similar to the following:

- Copy/text Change
- Design and Appearance
- Usability
- Functionality: Business Logic
- [ ] Functionality: Desirable (out of scope and chargeable)
- [ ] Functionality: Incorrect
- [ ] Functionality: Malfunction
- [ ] Functionality: Missing (but detailed in specification)
- [ ] Functionality: User Interface
- [ ] Project Management and Administration
- [ ] Database Schema
- [ ] Systems and Infrastructure

After you have created a set of categories, you can easily reuse these on future projects by using the Copy Categories From and Copy Categories To buttons judiciously. These can be found by editing the categories on a project (select Manage ⇔ Manage Projects) and then scrolling to the very bottom of the list of the existing categories you are maintaining. You will probably find that a universal list of categories similar to the preceding will serve you well in any future projects upon which you might embark.

With your project set up, you may need to select it whenever you log into Mantis in the future, especially if you have more than one project on the system. The small drop-down list box in the top-right corner of the screen enables you to flip among projects by name.

### Reporting Bugs

Now that you have the project set up, you and your team can start entering bugs that were found. Be sure to translate any faults into more specific tasks, rather than simply announce the problem. For example, “Move the pagination bar from the bottom to the top of the page,” is more productive than “The pagination bar is in the wrong place.”

To report a bug, simply select Report Bug from the main navigation.

You must select a category for the bug. This list will be generated dynamically from the selection of categories you entered earlier.

Other information you need to enter includes the following:

- [ ] Reproducibility — If this is a fault, rather than a simple request, state how frequently the problem can be reproduced. If this is a request for a new feature, select N/A, because there is nothing to reproduce.
- [ ] Severity — This list is hard-coded into Mantis and relates to the impact the fault is having on the project. Most of these are self-explanatory. Feature refers to a fault at the feature-level and implies that a key feature is either missing or rendered completely unusable by the fault. Block means that other testing is being held up as a result of this fault.
- [ ] Priority — This indicates a relative severity level for the fault to be attended to by the development team.
- [ ] Summary — This is a brief, one-line summary of the fault or, if there is insufficient space, the area in which the fault is developing (for example, “Auto-completion of text fields when replying to e-mails”).
- **Description** — This provides further detail about the fault.
- **Additional Information** — This provides any additional points that may aid the developers in resolving the problem.
- **Upload file** — If you wish to associate a binary file with this fault (for example, a screenshot showing the fault in action), you can upload it here. It will be stored in your server in the location you specified when you set up the project.
- **Report Stay** — If you check this box, you will be taken back to the “report new bug” screen when the bug is successfully entered. This enables you to batch-enter bugs more easily.

After you have entered a bug, you can view it under View Issues from the main navigation menu. One key point worth noting is that the bug is not yet assigned to anyone. This is the next step.

### Assigning Bugs

After bugs have been entered into the system, you will doubtlessly want to use your own Mantis login to assign their resolution to one of your development team.

Select the bug by its number from the list shown under View Issues, and you will see a drop-down list of users next to the button named Assign To. Select the user to whom you wish to assign the bug (which can be yourself) and click the button. The user lucky enough to be given the task of resolving this bug will be sent an e-mail with a direct link to the bug.

You can also bulk-assign bugs from the View Issues screen. This can be useful if you are working on a small project and you want to assign all open bugs to a given user. Place a check mark next to the bugs you want to assign, select Assign in the drop-down list box at the bottom of the list, and click Go. You will be invited to select a user, and the checked bugs will then be assigned to that user in the same way.

### Annotating Bugs

Your developers may take issue with a bug you have raised or, alternatively, want to add their own questions or comments. They can do this by viewing the bug, entering text in the relevant text box, and clicking Add Bugnote. The comment will be recorded against the bug, and a copy is sent to the person who raised the bug in the first place. The bug raiser may then want to add his or her own comments (in reply, if necessary), which will in turn be sent to the developer, and so on.

A developer may also want to make use of the resolution status of the bug to indicate his or her progress on the task at hand, or reaction to the bug overall. This includes such flags as “not a bug,” “won’t fix,” “fixed,” and so forth. Any changes in status also generate notification e-mails to the bug raiser.

### Resolving Bugs

After a developer has fixed a bug, he or she simply marks it as resolved by clicking the Resolved button. This changes both the resolution status and the overall status of the bug to “resolved,” firing e-mails to the bug raiser in the process.

If the project administrator agrees that the bug is resolved, he or she may set its overall status to “closed.” If he or she disagrees that it is resolved, it can be assigned again, and the resolution status is set to “reopened.” The developer will be notified that the bug has been reopened.
