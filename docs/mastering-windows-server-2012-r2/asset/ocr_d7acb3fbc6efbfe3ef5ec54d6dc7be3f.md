# CHAPTER 18: CONNECTING WINDOWS AND MAC CLIENTS

**Master It** You need to verify that a client machine has received the correct IP address configuration via DHCP for the network you are working on. Which of the following commands would return these results?

+   * ipconfig /all
* ipconfig /refresh
* msconfig /show
* msconfig

**Solution** The ipconfig /all command returns local area connection information including the following:

+   * IP address
* DNS IP addresses
* DHCP server suffix

+   * Domain name suffix

**Join a client computer to a domain.** Joining an Active Directory domain is key for workstations, because this provides centralized management from the Domain Admins group within the domain. Group Policy is centralized, security can be established, and even software can be controlled centrally.

**Master It** Is the following statement true or false? "When joining a computer to an Active Directory domain

**Solution** It is false. Users can add computers to the domain, but they can only do so up to 10 times. Users can also be delegated the right to add computers to the domain.

**Change user passwords.** By default Windows AD provides a 42-day maximum password age limit. This is limited by a 14-day reminder that you need to change your password. The 42-day maximum is designed to maintain a certain level of security for the enterprise, not allowing passwords to become stale.

**Master It** A user has become paranoid and wants to change his account password right away. He does not know how to do this and calls the help desk. The computer he is using is running Windows 7 operating system. What do you tell him?

**Solution** To open the Start menu, click the Windows Start button, and click "Change a password." He will need to input his old password and his new password and then click the arrow button.

**Connect to network resources.** Here's a typical scenario: a user wants to connect to a printer on the domain that does double-sided printing and stapling. But the user does not know where the company keeps these printers. The user calls the help desk.