# Storage methods

In this architecture option, a job is set up by a trigger to scan for sensitive data. The results of the scans are published so that action can be taken based on the results. The results can be pushed to Security Operations Center (SOC) tools such as Security Command Center so security responders can take action or an automated response detection can be built using Cloud Functions or a more sophisticated product such as SOA.

![](bbox=[0.137, 0.239, 0.862, 0.497])

Figure 10.2 – Storage method architecture

As shown in Figure 10.2, in this architecture option, you tell Cloud DLP what to inspect and then Cloud DLP runs a job that scans the repository. After the scan is complete, Cloud DLP saves a summary of the results of the scan back to the job. You can additionally specify that the results are sent to another Google Cloud project for analysis, as a separate BigQuery table or Security Command Center.

The type of scan typically involves those Google Cloud projects where you do not expect to have sensitive data. For projects that are meant to have sensitive data such as cardholder data or PII, you should also invest in data exfiltration controls such as VPC Service Controls for DLP.

# Hybrid methods

Hybrid jobs and triggers enable you to broaden the scope of protection that Cloud DLP provides beyond simple content inspection requests and Google Cloud Storage (GCS) repository scanning.