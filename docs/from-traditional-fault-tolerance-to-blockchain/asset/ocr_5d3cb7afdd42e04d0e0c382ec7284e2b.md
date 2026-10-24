application developers are tasked to provide the consistency test implementation so that they can determine application-specific rules for the comparison.

+   - Compensation. This method applies application-specific compensation action regarding the inconsistency visible to the external users. This method is invoked when the consistency test fails.

+   - Squash. This method is invoked by the Undo Manager on a verb that does not commute with a previous verb that causes externally visible inconsistency. As the method name suggests, squash turns the verb to nearly as a no-action verb except that it should inform the user properly that the original verb is not executed due to prior inconsistency. This happens most often to verbs that delete or overwrite part of the state.

# EXAMPLE 3.12

For the verbs defined in the email system [6], a portion of the sequencing rule is provided as follows:

+   - Any two Deliver verbs are independent of each other and are commutative.
+   - Any two IMAP verbs that belong to different users are independent and commutative.
+   - The Deliver verb is commutative with any IMAP verb except Fetch for the Inbox.
+   - Expunge and Fetch are not commutative if they operate on the same target folder.
+   - Store and Copy are not commutative if they operate on the same target folder.

The consistency-management interface for the email system verbs is implemented based on an external consistency model [6]. On the SMTP side, the only scenario that an externally visible inconsistency could occur is that an email delivery failed in the original execution, but the same email can be delivered successfully during replay. The consistency rule is that the email is not delivered if the standard bounce message regarding the failure of delivery has already been sent back to the sender.