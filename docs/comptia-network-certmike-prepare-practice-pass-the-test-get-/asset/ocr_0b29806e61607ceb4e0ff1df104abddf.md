a catastrophe, it adds to the workload of the first-line IT workers. Even worse, those users might fall victim to a phishing or social engineering attack and grant an intruder access to their systems, providing that intruder with the same administrative access.

To apply the principle of least privilege, administrators should grant users the permissions they need. For example, users should receive read-only access to files unless them is part of their job. The principle becomes more complicated with supervisors and IT personnel who do administrative access at times. These users should have two accounts, one with administrative privileges and one with basic user privileges, and they should only use the administrative account when they need to perform administrative tasks. The less often the administrative privileges are used, the less they will be compromised.

# ROLE-BASED ACCESS

Role-based access is a technique designed to simplify the permissions assignment process, enabling administrators to apply the least privilege principle more easily. The process of assigning users the permissions they need to work while denying everything else can be lengthy and time-consuming, especially when there are dozens or hundreds of users to configure.

Rather than configure each user account individually, administrators can create a group or other element that is dedicated to a single role or job, and possesses all of the permissions needed to perform that job. Then, by adding the users who perform that job to the group or assigning them inherit the permissions they need. When a user leaves the job or the company, simply removing them from the group revokes the permissions they no longer need.

# ZERO TRUST

The traditional security model for network calls for people connected to the network to be treated as trusted and those outside the network to non-trustworthy. With the increasing number of network threats and vulnerabilities today, this model is increasingly naive. Zero trust is a security principle where all with no access to the network at all are then granted the permissions they need to perform their tasks.

Zero trust means everything users do on the network they because they have been authenticated and authorized for each particular task at the time access is required. This generally means that authentication traffic on the network increases, users have to supply access credentials more often, and there are more IT help requests from people with login problems, but this is the price of security.