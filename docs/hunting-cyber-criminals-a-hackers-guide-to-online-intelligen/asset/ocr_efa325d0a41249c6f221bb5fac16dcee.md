# Chapter 16 ■ Searching Social Media 361

# Skiptracer

Skiptracer is a Python tool that uses basic web scraping to compile passive information on a target. Skiptracer has a number of modules that harvest information based on telephone numbers, email addresses, screen names, real (first and last names), home addresses, IPs, hostnames, license plate numbers, and breached website credentials (using HIBP.com).

The email modules will search for accounts based on your target email address on sites as LinkedIn, HavelBeenPwned, MySpace, and AdvancedBackgroundChecks.

The name modules will search for a target's first and last name on sites like Truth Finder, True People, and AdvancedBackgroundChecks.

The phone modules lookup U.S.-based phone numbers (performing a reverse search) on TruePeopleSearch, Who Called, and 411.com. The license plate module will search a nationwide database of registered U.S. license plates.

Finally, the screenname (username) module will search for similar usernames on sites such as Knowem and Namechk.

You can download Skiptracer for free at https://github.com/xillwillx/skiptracer.

# Running a Search

After launching Skiptracer, you will see a lookup menu (shown in Figure 16.14). From there, you can select which module to use.

# Searching for an Email Address

Let's start off by searching for an email address. Pressing 1 on your keyboard while on the home menu will bring you to to the email search menu (Figure 16.15).

Next, we can enter in any target email. Let's go back to a previous example and use hackernike@live.com. For some reason, searching LinkedIn does not work, which means you can't search “All.” Instead, we have to run each module individually. For this example, let's run a search for that email address using option 3, which will search the email against Troy Hunt's I Have Been Pwned (HIBP) database (Figure 16.16).