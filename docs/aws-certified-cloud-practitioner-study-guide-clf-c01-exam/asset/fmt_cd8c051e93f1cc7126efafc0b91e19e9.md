
<x0.2961><y0.4219># Protecting the Root User<x0.4844><y0.4281><class_Page-header>

For practical reasons, the root user has the permissions necessary to perform any task on your account. That includes launching any resources in any region and authorizing any expenses. The problem is that actively using the root user over the long term with only minimal protections presents a significant security risk. Should the root credentials ever be compromised through an attack, there will be no limit to the potential for mischief. All your data could be stolen or deleted or the attacker could run up hundreds of thousands of dollars of charges running a rogue crypto mining operation.

The recommended best practice is, therefore, to protect the root user by creating a complex password and implementing multifactor authentication and, for most administration activities, use IAM users instead. That will be covered next.

### Authentication<x0.2977><y0.4562><class_Section-header>

Whether you’re logging in to work with your AWS account via the AWS Management Console, running a command from the terminal of your personal laptop, or connecting a remote application to AWS resources at the programming code level, you’ll need to prove you are who you claim to be and that “who you claim to be” has a right to the access you’re after. Often that will mean providing some kind of user ID and password. In the case of programmatic or command-line access, you’ll need a set of access keys. Opening a remote login session to a Linux instance on Elastic Compute Cloud (EC2) will require a valid key pair. Let’s look at those one at a time.

#### Passwords<x0.2977><y0.4875><class_Section-header>

While you’re still learning your way around AWS, you’ll probably do most of your work from the browser’s AWS Management Console. As you’ll learn in Chapter 6, “Working with Your AWS Resources,” using the command line (specifically, AWS CLI) can be a far more efficient way to get things done, but the AWS Management Console works too.

The root user logs into the AWS Management Console with the associated email address along with the password set when the account was created (or subsequently updated). But as you’re no doubt already well aware, not all passwords are created equal. If you want your account to have any chance of surviving an attack, you should avoid passwords that can be easily guessed. Instead, choose complex and long passwords that include uppercase and lowercase characters, numbers, and symbols. Even better, use only randomly generated strings that aren’t even distantly based on the stuff going on in your life (like your birthday). And never (ever) reuse passwords across multiple accounts.

![](images/note.jpg) Don’t think you can remember passwords like those? Welcome to the club. The simplest and most effective solution is to use a password manager like LastPass, Dashlane, or KeePass2.

As mentioned, the first step in protecting your root user is to give it a high-quality password. But that doesn’t mean you should let other users off the hook. You’ll soon see how to create such users. But before that happens, you should have an appropriate *password policy* already in place. You can configure a policy from the Account Settings section of the IAM Dashboard that will require the passwords used by all users on the account to conform with minimum complexity. [Figure 5.2](#c05.xhtml#figure5-2) shows the policy options available to you on the Password Policy page.

![FIGURE 5.2 The IAM Account Settings page where you can set an account-wide password policy ](images/c05f002.jpg)

[**FIGURE 5.2**](#c05.xhtml#figureanchor5-2) The IAM Account Settings page where you can set an account-wide password policy 

*Multi-factor authentication* (MFA) adds a second layer of security to your logins. Once it’s enabled, a user will need to provide not only a password to authenticate (“something you know”) but also, as a second factor, a temporary digital token sent through a preset device (“something you have”), like a smartphone running an Authenticator app.

MFA works by associating a physical device—either a Universal 2nd Factor (U2F) or MFA-compliant device like YubiKey or a smartphone with the Authenticator app installed—with your account. When you try to log in, you’ll first enter a password, and then a short-lived code (usually a six-digit number) will be sent to your MFA device. You only need to read the number and enter it into the appropriate field on the login page, and you’ll be allowed in.

While complex passwords and MFA are important for any account user, they’re both especially critical for your root user. Exercise 5.1 will walk you through some of the possible settings for creating a password policy for your users from the IAM Dashboard.

#### Access Keys<x0.2977><y0.5766><class_Section-header>

As we mentioned, programmatic and command-line access to many AWS resources is authenticated by access keys (without the option of MFA). You can generate a new set of keys while logged into the AWS Management Console from the *Security Credentials* page—which is accessed from the account drop-down menu at the top right of the AWS Management Console page.

Choosing the Create New Access Key button will get you there. You’ll then have the option of downloading the key to your computer as a text file or showing the actual Access Key ID and Secret Access Key values in the dialog where you can copy and paste them somewhere safe. Just make sure you choose one of those options, because you’ll never be shown the secret access key itself again. You should also remember that it’s never a good idea to expose the Secret Access Key in plain text—as part of an email, for example.

The Security Credentials page also lists all your keys and allows you to deactivate, activate, or delete existing keys. This is where, while logged in as the root user, you should take the time to delete all keys associated with the root account.

#### Secure Shell Key Pairs<x0.2977><y0.6156><class_Section-header>

The industry-standard tool for safely encrypting remote login sessions is the Secure Shell (SSH) protocol. Without encryption, all commands and keystrokes you enter during a terminal session run over an insecure network will be easily readable by anyone with access to that network. When that “network” is the internet, that can add up to a lot of unfriendly eyes on your data.

Encryption converts those plain-text data packets into what looks like gibberish. Indeed, ideally—assuming no one has yet cracked the encryption algorithm you’re using—that text is and will remain gibberish, unless you happen to have the decryption key required to decrypt it. The SSH protocol manages the encryption and decryption steps in the process as long as compatible keys are present at both ends of the connection.

When you launch a new EC2 Linux instance (and a heavy majority of EC2 instances are running one flavor or another of Linux), you’ll be prompted either to use an existing SSH key pair or to create a new one. Similar to access keys, you’ll get only one opportunity to download the private half of the SSH key pair to your own computer. Again, do so without publicly exposing the file.

Once the private key is downloaded (and, for Linux and macOS, given appropriate permissions), you open SSH sessions to your instances by invoking the key in a connection command that might look something like this:

```
ssh -i keyname.pem ec2-user@<public_ip_address_of_instance>
```

Since the release of Windows 10, you can even launch SSH sessions into remote Linux servers natively from Windows machines.

### Users, Groups, and Roles<x0.2977><y0.6562><class_Section-header>
