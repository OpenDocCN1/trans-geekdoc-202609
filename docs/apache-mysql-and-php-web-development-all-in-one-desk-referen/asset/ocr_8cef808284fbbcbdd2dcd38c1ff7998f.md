# Setting an administrator password

According to the SANS institute (www.sans.org), a good password (not just administrator) should meet the following minimum criteria:

+   - Is at least eight alphanumeric characters long
+   - Contains both upper and lowercase characters (that is, a–z, A–Z)
+   - Has digits and punctuation characters as well as letters — that is, 0–9, !@#$%^&*()_+−=\|{}[]:;”?><>,/
+   - Does not use entire words in any language, slang, dialect, jargon, and so on
+   - Does not use personal information, family member names, and so on

![](bbox=[0.16, 0.365, 0.25, 0.46])

One way to come up with good passwords is to build passwords based on phrases. For example, take the phrase “I like to eat pizza at the park” and apply the preceding rules. Using the first letter of each word, you might come up with the password ill2eP@tP. By using a phrase and then some kind of patterned substitution, you can create a password that is both memorable and effective.

If you follow the suggestions in the previous list, your password is virtually immune to attacks that rely on victims using dictionary words. Most password-cracking tools come with a dictionary attack component. This tool takes the entire contents of a collection of dictionaries and uses all the words as passwords for a particular user name. The attack is effective against passwords that are dictionary words like “procrastination” or “beautiful” even if you reverse the words or just add a number to the end or beginning. For example, “beautiful” is not really much better than just plain “beautiful.” To get an idea about how commonly certain passwords are used, take a look at www.openwall.com/passwords/ordlists/ common.txt. Do you see any of your old passwords on this list?

# Disabling network services

After you have set a strong password for the administrator account, make sure that there are no networking services running that you won’t use.

# Disabling services during setup

During the later stages of the setup process, you are prompted to configure the networking configuration. If you select the option to customize these settings, you can deselect any of the services that you don’t plan on using. For example, if your server will exclusively be a platform for Apache, PHP, and MySQL, you can pretty much scrap everything other than TCP/IP itself. However, this won’t nab all the services you’ll want disabled. After the installation completes, you need to do a little extra work.