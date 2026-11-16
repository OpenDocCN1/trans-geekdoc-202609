These observations are relatively useless without the tabulation of corresponding action points. For the issues outlined previously, you might raise action points as follows:

+   - Ensure that when replying to a message, the recipient is automatically set to be the sender of the message being replied to.
+   - When 530 sessions are active, divert additional users to a “service unavailable” page explaining that the server is not able to process their requests at this time.
+   - Move the Previous and Next buttons in the Mailbox view to the top of the page.

These actions are all simple enough for a small project, but on a larger project you may have hundreds, or even thousands, of action points (such as bugs that need fixing and tweaks for fine tuning). How do you keep track?

It’s certainly possible to use the well-known default solution of any office worker thrust without warning into the world of project management — that of Microsoft Excel. It certainly gives you a quick-and-dirty mechanism for keeping track of project fault reports and their status, in the form of a color-coded table updated on a regular basis by all participating on the project.

However, its limitations will soon become clear. No Web-based access means that users must be in the same office where that spreadsheet resides on a local file server. No multiple-user access means that only one user can update the spreadsheet at a time. An onus on those using it to check it and update it frequently and regularly (with no prospect of notifications when issues requiring their attention become prescient) means that issues often go unchecked, even when urgent.

That’s where a purpose-built solution can provide an effective alternative.

# **Effective Fault Management Using Mantis**

This section takes a look at a fault-management system known as Mantis, a free package currently available from www.mantisbt.org.

The purpose of Mantis is to enable you to effectively keep tabs on all faults and defects in your projects, assign them to developers for resolution, and enable developers to pass comments on them where appropriate.

Mantis is a Web-based application written in PHP (what else?) that typically functions as an extranet. Whether you choose to open it up for access to your clients is entirely up to you. When working with smaller clients, this can often be beneficial because it enables them to feel part of the QA process. Mantis supports multiple users, each with his or her own access levels and rights, so you can offer different access to yourself and, say, your developers.