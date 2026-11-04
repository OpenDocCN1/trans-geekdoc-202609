
# Baselines

`Baselines` are the application of a standard to a specific category or grouping. Examples of groups include platform (the operating system and its version), device type (laptops, servers, desktops, routers, switches, firewalls, mobile devices, and so on), ownership (employee-owned or corporate-owned), and location (onsite, remote workers, and so on).

The primary objective of a baseline is uniformity and consistency. An example of a baseline related to our password policy and standard example is the mandate that a specific `Active Directory Group Policy` configuration (the standard) be used on all Windows devices (the group) to technically enforce security requirements, as illustrated in [Figure 2-2](#ch02.xhtml#ch02fig02).

![](graphics/02fig02.jpg)

In this example, by applying the same `Active Directory Group Policy` to all Windows workstations and servers, the baseline was implemented throughout the organization. In this case, there is also assurance that new devices will be configured accordingly.

[Figure 2-3](#ch02.xhtml#ch02fig03) shows another example of how different baselines can be enforced in the infrastructure with more sophisticated systems, such as the `Cisco Identity Service Engine` (`ISE`). `Network Access Control` (`NAC`) is a multipart solution that validates the security posture of an endpoint system before entering the network. With `NAC`, you can also define what resources the endpoint has access to, based on the results of its security posture. The main goal of any `NAC` solution is to improve the capability of the network to identify, prevent, and adapt to threats. The `Cisco ISE` shown in [Figure 2-3](#ch02.xhtml#ch02fig03) centralizes network access control based on business role and security policy to provide a consistent network access policy for end users, whether they connect through wired, wireless, or VPN. All this can be done from a centralized `ISE` console that then distributes enforcement across the entire network and security infrastructure.

![](graphics/02fig03.jpg)

In [Figure 2-3](#ch02.xhtml#ch02fig03), three different endpoint systems were denied or rejected access to the network because they didn’t comply with a corporate baseline.

## Guidelines

`Guidelines` are best thought of as teaching tools. The objective of a guideline is to help people conform to a standard. In addition to using softer language than standards, guidelines are customized for the intended audience and are not mandatory. Guidelines are akin to suggestions or advice. A guideline related to the password standard in the previous example might read like this:

“A good way to create a strong password is to think of a phrase, song title, or other group of words that is easy to remember and then convert it, like this:

* “The phrase ‘Up and at ‘em at 7!’ can be converted into a strong password such as `up&atm@7!`.
* “You can create many passwords from this one phrase by changing the number, moving the symbols, or changing the punctuation mark.”

This guideline is intended to help readers create easy-to-remember, yet strong passwords.

Guidelines are recommendations and advice to users when certain standards do not apply to your environment. Guidelines are designed to streamline certain processes according to best practices and must be consistent with the cybersecurity policies. On the other hand, guidelines often are open to interpretation and do not need to be followed to the letter.

## Procedures

`Procedures` are instructions for how a policy, a standard, a baseline, and guidelines are carried out in a given situation. Procedures focus on actions or steps, with specific starting and ending points. There are four commonly used procedure formats:

* `Simple Step`: Lists sequential actions. There is no decision making.
* `Hierarchical`: Includes both generalized instructions for experienced users and detailed instructions for novices.
* `Graphic`: This format uses either pictures or symbols to illustrate the step.
* `Flowchart`: Used when a decision-making process is associated with the task. Flowcharts are useful when multiple parties are involved in separate tasks.

In keeping with our previous password example, the following is a `Simple Step` procedure for changing a user’s Windows password (`Windows 7` and earlier):

1. Press and hold the `Ctrl+Alt+Delete` keys.
2. Click the `Change Password` option.
3. Type your current password in the top box.
4. Type your new password in both the second and third boxes. (If the passwords don’t match, you will be prompted to reenter your new password.)
5. Click `OK`, and then log in with your new password.

The following is the procedure to change your Windows password (`Windows 10` and later):

1. Click `Start`.
2. Click your user account on the top, and select `Change Account Settings`.
3. Select `Sign-in Options` on the left panel.
4. Click the `Change` button under Password.
5. Enter your current password, and hit `Next`.
6. Type your new password and reenter it. Enter a password hint that will help you in case you forget your password.

Note

As with guidelines, it is important to know both your audience and the complexity of the task when designing procedures. In [Chapter 8](#ch08.xhtml#ch08), “[Communications and Operations Security](#ch08.xhtml#ch08),” we discuss in detail the use of cybersecurity playbooks and standard operating procedures (`SOPs`).

Procedures should be well documented and easy to follow to ensure consistency and adherence to policies, standards, and baselines. Like policies and standards, they should be well reviewed to ensure that they accomplish the objective of the policy and that they are accurate and still relevant.

## Plans and Programs

The function of a plan is to provide strategic and tactical instructions and guidance on how to execute an initiative or how to respond to a situation, within a certain time frame, usually with defined stages and with designated resources. Plans are sometimes referred to as programs. For our purposes, the terms are interchangeable. Here are some examples of information security–related plans we discuss in this book:

* `Vendor Management Plan`
* `Incident Response Plan`
* `Business Continuity Plan`
* `Disaster Recovery Plan`

Policies and plans are closely related. For example, an `Incident Response Policy` will generally include the requirement to publish, maintain, and test an `Incident Response Plan`. Conversely, the `Incident Response Plan` gets its authority from the policy. Quite often, the policy will be included in the plan document.

### In Practice

#### Policy Hierarchy Review

Let’s look at an example of how standards, guidelines, and procedures support a policy statement:

* The policy requires that all media should be encrypted.
* The standard specifies the type of encryption that must be used.
* The guideline might illustrate how to identify removable media.
* The procedure would provide the instructions for encrypting the media.

# Writing Style and Technique

Style is critical. The first impression of a document is based on its style and organization. If the reader is immediately intimidated, the contents become irrelevant. Keep in mind that the role of policy is to guide behavior. That can happen only if the policy is clear and easy to use. How the document flows and the words you use will make all the difference as to how the policy is interpreted. Know your intended reader and write in a way that is understandable. Use terminology that is relevant. Most important, keep it simple. Policies that are overly complex tend to be misinterpreted. Policies should be written using plain language.

## Using Plain Language

The term `plain language` means using the simplest, most straightforward way to express an idea.
