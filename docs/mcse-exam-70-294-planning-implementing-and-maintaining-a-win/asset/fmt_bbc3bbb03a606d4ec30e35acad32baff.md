
### 2. Policy Processing Order
☑ C. Policies are always processed starting with the local computer policy, then following all directory policies from the farthest `GPO` from the object to the closest `GPO` to the object.
⌧ Answer A is incorrect because local policies are always processed first, and site policies are processed before `OU` policies. Answer B is incorrect because local policies are always processed first. Answer D is incorrect because site policies are processed before `OU` policies.

### 3. Your department has just hired a new junior system administrator and has asked you to train him.
The trainee has worked some with `Active Directory`, but has never used `Group Policy` before. He has been running `RSoP` in planning mode to get an understanding of where different group policy settings are stored, but he keeps getting confused because he is not seeing the same groupings between the computer settings and user settings in the report. What are the main types of policies for user and computer configurations he should see in the report, as represented by nodes in the console tree?
A. Assign scripts, Manage applications, Redirect folders, and Change Registry settings
B. Software settings, Windows settings, and Administrative templates
C. Security settings, Account settings, and Software settings
D. Local settings, Site settings, Domain settings, and `OU` settings
☑ B. User configuration and computer configuration settings are collected into these three nodes.
⌧ Answer A is incorrect because these items describe some of the specific tasks you can achieve with group policy, but none are specifically listed in the three groups under user and computer configuration. Answer C is incorrect because there are security settings under Windows settings, but there are no groups labeled Account settings and Software settings. Answer D is incorrect because these terms describe the locations where you can apply `GPOs`.

### 4. You work for a large company that has just acquired another company in a merger.
The acquired company has merged its `Active Directory` structure into your forest. The new group wants to maintain control over their portion of the directory, but you want to make sure certain that domain policy settings are not changed by `GPOs` applied at the `OU` level. How will you achieve this?
A. Set the `No Override` option on the domain `GPO`.
B. Set the `Block Policy Inheritance` option on the domain `GPO`.
C. Set the `Disable Domain Inheritance` option on the domain `GPO`.
D. Unlink the domain `GPO` from the domain container.
☑ A. Setting the `No Override` option on the domain `GPO` will prevent any lower-level `GPO` settings from being applied.
⌧ Answer B is incorrect because the `Block Policy Inheritance` option prevents a container from inheriting `GPO` settings from a higher level. It does not have any effect on settings at a lower level. Answer C is incorrect because there is no `Disable Domain Inheritance` option. Answer D is incorrect because unlinking the `GPO` from the domain container will prevent the domain `GPO` settings from being applied at all.

### Planning a Group Policy Strategy
#### 5. You have been asked to implement group policy for a large, geographically diverse company.
The users in the company are used to being able to log on very quickly, and you do not want to slow the logon process significantly when adding group policy settings. Which of the following are ways to reduce the processing time for group policy when a user logs on? (Choose all that apply.)
A. Apply the `Block Policy Inheritance` setting on the `OU` closest to the logon object to keep all other policies from processing.
B. Set the `Disable Computer Configuration Settings` or `Disable User Configuration Settings` options in the `GPO` options.
C. Filter access to the `GPO` with `WMI` settings.
D. Filter access to the `GPO` with security group permissions.
☑ B and D. Disabling the processing of computer or user configuration settings will reduce the time needed to process the `GPO`. Users and/or computers that do not have security permissions to see or process a `GPO` will not be able to process the settings.
⌧ Answer A is incorrect because blocking policy inheritance will not prevent `GPOs` higher in the directory from processing; it will just override the settings once the `GPO` for that container is processed. Answer C is incorrect because using `WMI` filters in a `GPO` will actually increase the time it takes to process the policy settings, not decrease it.

#### 6. You have been asked by your supervisor to duplicate the group policy settings of the Sales department for the Marketing department.
A coworker suggests that instead of creating a new `GPO` for the Marketing `OU`, you can just link the existing Sales `GPO` to the Marketing `OU`. What are the guidelines for linking `GPOs` to a container?
A. Each `GPO` can be linked to only one container.
B. Each `GPO` must be linked to a container within the same domain.
C. Only one `GPO` can be linked to the root domain container.
D. Each `GPO` should be linked to a single container only one time.
☑ D. You can link a `GPO` to a container more than one time, but doing so can cause significant policy problems.
⌧ Answer A is incorrect because `GPOs` can be linked to more than one container. Answer B is incorrect because you can link a `GPO` in one domain to a container in another domain, but you really should not do this. Answer C is incorrect because you can have more than one `GPO` tied to the root domain container.

#### 7. You are the administrator for the corporate `Active Directory` network.
There are four business units that are separated into individual domains that are rather large. How should you approach managing group policy for the corporation?
A. Limit each business unit to one `Default Domain Policy` object in the root of each domain, and apply all policy settings for the domain in that object.
B. Identify one or more users in each domain and delegate control to them to create and manage group policy for the domain while retaining the ability to manage policy for each domain.
C. Give all users rights to manage group policy for themselves.
D. Only allow the administrator to manage group policy for the company.
☑ B. Delegating control for group policy to trusted users in each domain can aid in the management of the needs for each domain. You should retain the ability to edit and manage policy in each domain in case of problems.
⌧ Answer A is incorrect because limiting each domain to a single `GPO` will likely not meet the needs of the users in the environment. Answer C is incorrect because granting all users rights to manage group policy would end up giving users too much power in the domain and represents a security risk. Answer D is incorrect because a sufficiently large directory will be difficult for a single administrator to manage effectively.

### Implementing Group Policy
#### 8. You just took over as network administrator for a company.
Your network consists of a single domain. The previous administrator had set up a group policy for the domain that allowed six unsuccessful logon attempts before an account would be locked out. A series of new computers has been purchased and deployed in the environment, and the local policy on these systems is set to allow three unsuccessful logon attempts before locking an account. You decide that you want to enforce account lockout to occur after three unsuccessful logon attempts across the company. How would you achieve this?
A. Set the local policy on each PC to lock out accounts after three attempts, and set `No Override` on the local policy.
B. Set group policy in a domain `GPO` to lock out accounts after three unsuccessful logon attempts.
C. Set the `Block Policy Inheritance` on the group policy.
D. Remove the local policies from each PC.
☑ B. Since non-local group policy always overrides local policy, setting the account lockout threshold in group policy for a domain `GPO` will force all systems to have this new setting.
