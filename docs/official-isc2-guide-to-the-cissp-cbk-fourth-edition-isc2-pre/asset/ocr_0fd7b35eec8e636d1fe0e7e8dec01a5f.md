sessions and perhaps two desktop sessions if virtual desktops are used. However, organizations must be cautious with regards to how multiple sessions are implemented because each session can provide an additional point of attack for an adversary and many more sessions to monitor for the security operations team and the end-user. The security practitioner needs to keep in mind that by monitoring sessions for behavior such as logins during non-business hours, he or she will be able to spot potentially suspicious behavior across any of the systems being observed.

# Schedule Limitations

Some desktop sessions may be limited by time. For example, if a kiosk is available in the lobby of an organization for general use during normal hours, does it make sense to have it allow sessions during non-business hours? Or should cash registers allow the creation of sessions outside of normal operating hours? Typically, session management should follow the concept of "least privilege" and only allow the creation of sessions within the most restrictive schedule and resources required to meet the mission.

# Logical Sessions

As more information systems become service-based through Web browsers, understanding Web-based sessions, their weaknesses, and how to protect them is critical for information security professionals to understand. Basic sessions are created between authenticated users, services, applications, and devices on a routine and regular basis in almost all information systems. For example, a typical online banking scenario may follow this sequence:

+   1. A user starts a Web browser and navigates to his or her bank’s website.
+      a. There is now a session created between the user’s browser and the bank’s Web server.
+   2. The user clicks on the "secure login" link to get to the bank login page.
+      a. The user has now secured the session typically using Secure Sockets Layer (SSL).
+   3. The user enters a username and password and authenticates.
+      a. This information is passed through the encrypted session where, if intercepted, it would be very difficult to decrypt.
+   4. The user conducts banking business and "logs off" of the banking website.
+      a. This will close the encrypted connection and ensure no other activities could occur under the user’s credentials until another session is established.