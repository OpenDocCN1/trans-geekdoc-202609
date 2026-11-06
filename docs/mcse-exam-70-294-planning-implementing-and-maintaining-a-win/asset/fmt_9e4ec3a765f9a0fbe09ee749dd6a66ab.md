
Making use of software restriction policies will allow you to place controls on “untrusted” code within your organization. Through a combination of rules, you can identify specific applications or types of applications that are either allowed to run or prevented from running. These rules are powerful and complex, but by themselves cannot provide full protection against malicious code. Use of software restriction policies will augment the protections you might already have in place, but you should not plan to rely solely on these policies to completely protect your environment.

## Setting Up Software Restriction Policies
The settings for Software Restriction are located in the Security Settings area of Group Policy You might have to enable software restriction policies before you can make changes, as most systems do not have these policies enabled by default. When software restriction policies are enabled, you will find a number of settings in the area. The Enforcement policy determines if the software policies will apply to all files or exclude library (`.dll`) files. This policy also identifies whether the policies apply to all users of the system or just to non-administrators. If you want to exclude administrators from software restriction policies, this is where you would set that option.

Another policy you will find here is the Designated file types policy You can specify which file types, based on file extension, to which software restriction policies should apply. You can add additional file types by adding the file extension to the list in this policy window.

The third policy you will find here is the Trusted Publishers policy. In this policy setting, you can specify what user level is allowed to enable trust for software publishers, and how to check for expired certificates for those publishers.

The other area located here is the Additional Rules folder, where the specific rules you will create for your system will be located.

## Software Policy Rules
There are four types of rules that you can use to identify applications to which policy should apply: the hash rule, certificate rule, path rule, and Internet zone rule. Each rule identifies a different way to identify files that should have rules applied. Within the rule, you can set the security setting for the resulting file or files to either Disallowed or Unrestricted. A Disallowed setting in a rule will prevent the user from accessing the file or files. An Unrestricted setting will allow the user to access the file or files.

### Hash Rule
When you create a hash rule, you identify a specific file to which you want the rule to apply, and the system generates a hash on the file, including attributes such as date and time of creation and file size. After the policy is in place, the system performs a hash on each file accessed, and if the hash matches the hash in the rule, the rule is applied.

### Certificate Rule
When you create a certificate rule, you identify a set of files that are signed by a specific certificate. In creating the rule, you select the specific certificate for the rule. When the system processes a file request, it will check the certificate settings on the file to check for a match against the certificate in the rule, and will process the rule if there is a match. Certificate rules do not apply to `.exe` and `.dll` files, but will apply to all other file types listed in the Designated File Types policy.

### Path Rule
When you create a path rule, you identify a file or set of files based on their location on disk. The path can identify the path to a folder, a specific file, or a set of files based on a wildcard. When the system processes a file request when path rules are in place, it will compare the file requested to the path rules, and process the rule if there is a match.

### Internet Zone Rule
When you create an Internet zone rule, you specify settings based on the Internet zones identified in Internet Explorer: Internet, Local Computer, Local Intranet, Restricted Sites, and Trusted Sites. Internet zone rules only apply to Windows installer packages. If a user downloads an installer package from a site in one of the zones, the zone settings will determine if the user will be able to execute the installer.

## Precedence of Policies
Since several rules can be applied to the same program, there is an established order of precedence that is applied. A rule based on a higher precedence will override a conflicting rule applied with a lower precedence.

1. Hash rule
2. Certificate rule
3. Path rule
4. Internet zone rule

Based on this order, if a program is unrestricted based on a hash rule but disallowed based on a path rule, the program will run, as the hash rule has precedence over the path rule. For path rules, there is an additional order of precedence based on the path specified. If there are conflicting path rules, the more restrictive path rule will apply. The following list identifies the precedence of paths from most restrictive to least restrictive.

1. `Drive:\\Folder1\\Folder2\\filename. extension`
2. `Drive:\\Folder1\\Folder2\\\*. extension`
3. `\*. extension`
4. `Drive:\\Folder1\\Folder2\\`
5. `Drive:\\Folder1\\`

When similar rules are applied, such as multiple path rules, the more restrictive rule applies. For example, if a program is set to Disallow in one path rule and set to Unrestricted in another, access to the program will be denied, as Disallow is the more restrictive setting.

## Best Practices
The following items include some of the recommendations for implementing software restriction policies.

■ Test, test, test Never implement software restrictions without testing, especially when applying a Disallow setting. Placing restrictions on certain types of files can negatively impact the operation of your computer and/or the network environment.

■ Couple software restriction policies with access control restrictions Using access control in conjunction with software restriction makes a more complete restriction solution.

■ Use anti-virus software Software restriction policies are not a sufficient substitute for a solid anti-virus package. The tools used in conjunction can increase the security of the system, but do not plan on using software restriction in place of anti-virus tools.

■ Use Disallow as default with great caution If you take the approach of using Disallow as the default and identifying specific applications to allow, be sure you test the system thoroughly. Some applications can launch other applications in normal course of operation. As stated in the first item, test your implementation thoroughly before unleashing it on an unsuspecting audience.

![u09-06-9781931836944](images/B9781931836944500155/u09-06-9781931836944.jpg)

## Applying Group Policy Best Practices
If you have been reading straight through this chapter, you’ve seen that there are a vast number of ways that group policy can be implemented in an Active Directory environment. How should you approach a group policy implementation in your environment? This section covers some of the best practices related to implementing group policy.

■ The fewer, the better Keep the number of policies defined as small as possible. Since each user policy the user encounters must be processed at logon, you can keep user logon delays to a minimum by reducing the number of user policies. In addition, a smaller number of policy objects means fewer places for you to look for problems or conflicts when troubleshooting group policy issues. Computer policies are processed at boot time, so reducing the number of these will speed the boot process of the computer.

■ Avoid conflicting policies whenever possible Although you can set up a lower-level policy to override a higher-level one, you should avoid doing this unless necessary. Again, simplicity should be the rule.
