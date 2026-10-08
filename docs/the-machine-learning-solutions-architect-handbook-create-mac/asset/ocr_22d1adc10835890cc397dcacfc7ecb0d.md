7. On the workflow UI designer, the final workflow should look like the following diagram:

![](bbox=[0.15, 0.163, 0.85, 0.269])

Figure 4.7 - Glue data flow design

8. Now, you are ready to run the workflow. Select the workflow and select Run from the Actions dropdown. You can monitor the running status by selecting the Run ID and clicking on View run details. You should see something similar to the following screenshot:

![](bbox=[0.15, 0.4, 0.85, 0.506])

Figure 4.8 - Glue workflow execution

9. Try deleting the customer_data and churn_list tables and re-run the workflow. See whether the new tables are created. Check the s3://MLSA-DataLake-Serving-<your initials>/ml-customer-churn/<date>/S3 location to verify a new folder is created with a new dataset.

Congratulations! You have completed the hands-on lab and learned how to build a simple data lake and its supporting components to allow data cataloging, data querying, and data processing.