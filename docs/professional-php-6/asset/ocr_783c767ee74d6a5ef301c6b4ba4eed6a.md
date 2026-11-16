+   - What is the budget? — Complex managed-hosting platforms can cost thousands of dollars per month, and require 12-month (or longer) contract commitments. If this is what the application requires to handle the expected traffic volume, is the cash available to pay for it?

+   - Are there any particularly complex security considerations or regulatory requirements? — A Web site that collects e-mail addresses for marketing purposes requires reasonable security. However, an application that collects social security numbers and credit card details requires an entirely different configuration and further consideration. If the application is for a heavily regulated industry (such as banking), there may be additional regulatory requirements.

+   - What are the storage requirements? — If this is a primarily read-only application, you can examine the PHP, database, images, and other assets to immediately determine storage requirements. However, for anything with user inputs, you must carefully plan the storage considerations. Again, keep in mind any regulatory requirements that may necessitate keeping far more information (especially in regard to application logs, e-mails, and backups) than you might have otherwise planned for. Growth in the number of application users should be mapped to an average storage requirement per user.

+   - Finally, what are the backup requirements? — If the application is primarily read-only, and the data, source code, and other assets are otherwise backed up elsewhere (for example, in a subversion repository), a far simpler backup strategy is required than for a heavily transactional Web site (such as an e-commerce application), or a write-heavy application (such as a wiki or popular blog).

These business requirements directly translate into systems architecture considerations, which you can now begin to examine.

# # Determining Hardware Requirements

There are several pieces of hardware to consider, each with an important role. In smaller installations, a single piece of hardware may perform multiple functions that in a larger architecture may be handled by a dedicated appliance.

# # Web Servers

As the front line of user activity, this is where the execution of the PHP code will take place, along with the serving of HTML, images, and other assets. These machines will be running Apache or another HTTP daemon, and they represent the first place to consider some redundancy, in the form of multiple load-balanced machines. RAID 1 (mirrored) hard drives should also be considered to protect against catastrophic hardware failure (which happens to hard drives more often than you might think).

# # Database Servers

A dedicated machine or array of machines to handle database transactions is strongly recommended for reasonably well-trafficked Web sites. By offloading the heavy data-crunching to separate hardware, you enable slow queries to proceed without interrupting the performance of more routine front-end application functionality. RAID 5 hard disks are strongly recommended here, as is some redundancy in