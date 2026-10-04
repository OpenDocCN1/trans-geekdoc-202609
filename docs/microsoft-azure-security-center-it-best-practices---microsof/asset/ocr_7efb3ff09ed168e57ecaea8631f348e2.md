![](bbox=[0.134, 0.031, 0.538, 0.219])

**Figure 6-20** Email parameters

+   13. Type the destination address in the To field. This is the mailbox that will receive the alert. If you want to send the alert to more than one mailbox, separate each address with a semicolon.

+   14. In the Subject field, type a brief message that reflects the intent of the email—for example, High Severity Alert Detected.

+   15. In the Body field, type a generic message, and concatenate it with the variables that appear in the drop-down menu next to the Send an alert box (see Figure 6-21).

![](bbox=[0.134, 0.44, 0.836, 0.595])

**Figure 6-21** Description using fixed text and variables

+   16. If you want to trigger an action for the alert is not a high priority, repeat steps 10–15 in the **If** false section.

+   17. Click **Save** in the upper-left corner of the **Logic Apps Designer** dashboard.

+   18. Click **Close** in the **Logic Apps Designer** dashboard and in the playbook’s properties.

# Executing a playbook

Now that the playbook contains a workflow, you can execute the playbook. You can do so from two locations: the **Security Alerts** dashboard or the **Investigation** dashboard. The following steps demonstrate the execution from the **Security Alerts** dashboard.