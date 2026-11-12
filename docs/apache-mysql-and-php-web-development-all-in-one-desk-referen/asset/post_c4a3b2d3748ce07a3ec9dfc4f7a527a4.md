
/etc/rc.d/rc.firewall script during system startup. The purpose of the rc.firewall script is to load all the needed modules to run IP Masquerade and process its relevant configuration files. This file is where you enter the traffic restrictions (rule sets) like the ipchains and iptables examples earlier in this chapter. Many sample IP Masquerade configurations are available, including www.tldp.org/HOWTO/IP-Masquerade-HOWTO/, which helps you get your masquerade configuration up and running.

## Keeping on Top with Logging

Although it's important to have a handle on the services running on your system and use firewalling if possible, comprehensive logging is one of the most useful methods for ensuring that your system remains secure. The syslog daemon is used on Linux and Unix systems to facilitate logging. On most Linux installations, a global configuration file controls the behavior of the syslog component. The /etc/syslog.conf file passes the logging instructions to the syslog daemon. Most default Linux installations are designed to balance security and functionality, and as a result, the default logging behavior needs improvement.

Within the syslog.conf file, you will find entries that look like this:

```
*.=info;*.=notice    /usr/log/notice.log
```

Each entry has three elements:

- The first item is the source of the log information, called a facility — in other words, which processes should be monitored for logging output. * is used to specify "all available" log sources.
- The information following the * specifies the kinds of events that will be captured, known as priority. For example, in *.=notice, all log sources are monitored, and only the notice priority events are captured.
- The last element specifies what will be done with the logging information, and in most cases where the log information will be stored. In the example, the logging output is stored in the file /usr/log/notice.log.

It is fairly useful to log different facilities to different log files. Although this can increase the amount of disk space used by log files, it can make locating information about particular events easier.

Several facilities that you should track may not be logged by default. To begin logging these items, you need to create a new entry in the syslog.conf log file. Table 1-1 shows some of the common facilities that you should use.

| Facility | Use |
|---|---|
| Auth/Security | Log information relating to user authentication. |
| Authpriv | A more detailed version of auth. |
| Cron | Logs activity of the cron daemon, which is used to schedule events. |
| Daemon | Collects information about *all* system daemons. |
| Mail | Tracks mail server activity. This is a must have if you're running a mail server. |
| Syslog | Information about the syslog server itself. |

Along with this selection of facilities, you need to understand the priorities that are available. How much detail you need is up to you. Keep in mind that if a problem occurs and you don't have enough information to identify the source, the logs are essentially useless. However, if you collect every transaction and message in the log, it may be nearly impossible to locate meaningful information. Table 1-2 describes the available priorities.

| Priority | Use |
|---|---|
| Info | Logs general informational messages |
| Notice | Logs occurrences that require special interaction (that is, user prompts) |
| Warning | System warning, “might be a problem” |
| Err | System error, “a problem occurred” |
| Crit | Critical condition, “a big problem has occurred” |
| Alert | Intervention required, “problem happening, need help” |
| Emerg | Serious system failure, “something is hosed” |
| Panic | System panic, “HUGE problem” |
| Debug | Logs nearly everything |

## Chapter 2: Configuring Windows

### In This Chapter

- Security during installation
- Patching and updating
- Using the Microsoft Baseline Security Analyzer

If you decide to use the Windows operating system as the host for your Web server, you need to spend some time making sure it's secure. Although a lot of media attention has focused on the security risks of Windows operating systems, you need to focus on a couple of general truths:

- Most of the severe security-related events directed at Windows (CodeRed, Sobig, MSBlast, and so forth) occurred *after* Microsoft had released a patch that removed the exploited vulnerability. If a system had the patch installed, it would not have been directly affected by the event. Thus, you need to keep on top of the available security patches by checking for them on a weekly basis at minimum. If you find a new, critical patch make sure you install it ASAP.
- Many of the common attacks against Windows systems don't require special vulnerabilities. Typically, the default settings for Windows operating systems are very insecure. With casual network access and a brute-force password cracker, any illicit user has better than a 50 percent chance of cracking any newly installed Windows PC.

Fortunately, you can perform a few basic tasks to remedy most of these issues and greatly reduce your risk of being violated. In this chapter, I use Windows 2000 Server for all the examples. The policies and procedures translate to any other version of Windows, but some details may differ slightly.

### Securing Windows during Setup

To make your system resilient enough for duty as a publicly exposed Web server, you need to start securing it from the very beginning of the installation process. During the operating system installation, set a strong administrator password and disable networking services that you don't plan to use.

### Setting an administrator password

According to the SANS institute (www.sans.org), a good password (not just administrator) should meet the following minimum criteria:

- Is at least eight alphanumeric characters long
- Contains both upper and lowercase characters (that is, a–z, A–Z)
- Has digits and punctuation characters as well as letters — that is, 0–9, !@#$%^&*()_+−=|{}[]:;”?><>,/
- Does not use entire words in any language, slang, dialect, jargon, and so on
- Does not use personal information, family member names, and so on

![](img/3f967ab8a8fddc723173059f56621648_53_0.png)

One way to come up with good passwords is to build passwords based on phrases. For example, take the phrase “I like to eat pizza at the park” and apply the preceding rules. Using the first letter of each word, you might come up with the password ill2eP@tP. By using a phrase and then some kind of patterned substitution, you can create a password that is both memorable and effective.

If you follow the suggestions in the previous list, your password is virtually immune to attacks that rely on victims using dictionary words. Most password-cracking tools come with a dictionary attack component. This tool takes the entire contents of a collection of dictionaries and uses all the words as passwords for a particular user name. The attack is effective against passwords that are dictionary words like “procrastination” or “beautiful” even if you reverse the words or just add a number to the end or beginning. For example, “beautiful” is not really much better than just plain “beautiful.” To get an idea about how commonly certain passwords are used, take a look at www.openwall.com/passwords/wordlists/common.txt. Do you see any of your old passwords on this list?

### Disabling network services

After you have set a strong password for the administrator account, make sure that there are no networking services running that you won’t use.

### Disabling services during setup

During the later stages of the setup process, you are prompted to configure the networking configuration. If you select the option to customize these settings, you can deselect any of the services that you don’t plan on using. For example, if your server will exclusively be a platform for Apache, PHP, and MySQL, you can pretty much scrap everything other than TCP/IP itself. However, this won’t nab all the services you’ll want disabled. After the installation completes, you need to do a little extra work.
