
is called anomaly detection. This triggers alerts when it detects deviations from established baselines that conform to a potential attack vector.

Regardless of which capability Security Center uses to identify a threat, the result will be externalized in the dashboard as a security alert. A security alert contains valuable information about what triggered the alert, the resources targeted, the source of the attack, and suggestions to remediate the threat. Security alerts are divided into categories:

- **Virtual Machine Behavioral Analysis (VMBA):** This type of alert uses behavioral analytics to identify compromised resources based on an analysis of the virtual machine (VM) event logs, such as process-creation events, in memory only (fileless attack), and login events.
- **Network analysis:** This type of alert collects security information from your Azure Internet Protocol Flow Information (IPFIX) traffic and analyzes it to identify threats. An example of an alert that belongs to this category is the Suspicious Incoming RDP Network Activity From Multiple Sources.

- **Resource analysis:** This analyzes your Platform as a Service (PaaS) services, such as Azure SQL, and triggers alerts based on this analysis. An example of an alert that belongs to this category is the *Potential SQL Injection* alert.

- **Contextual information:** This provides extra context to reach a verdict about the nature of the threat and how to mitigate it.

> **IMPORTANT** Because the list of alerts is constantly evolving, we recommend that you visit https://aka.ms/ASCAlerts to obtain the latest list of security alerts.

## Understanding alerts

Before Security Center triggers an alert, it needs to have a certain level of certainty that the alert is a *true* positive. The intent is to reduce false positive results and provide a high-quality alert level. To accomplish that, Security Center performs the following actions shown in Figure 6-1 during the alert normalization.

![](img/4b11e95292819ab1a383a41ef73aedb4_132_0.png)

FIGURE 6-1 Evaluation priority to trigger an alert

When an alert is finally triggered, you will be able to answer five questions that are important for your investigation. The questions are shown in the Alert blade, as shown in Figure 6-2.

![](img/4b11e95292819ab1a383a41ef73aedb4_132_1.png)

FIGURE 6-2 The alert blade has the answers for the major investigation's questions

It is important to emphasize that not all alerts will have the same level of information; it really depends on the type of threat and the analytics for that threat. Also, alerts will take differing amounts of time to trigger. Security Center has three major detection engines that will dictate the time for an alert to be triggered.

- **Event-based detection engine:** The event-based detection engine will trigger alerts near real time.
- **Query-based detection engine:** The query-based detection engine works on different events from different sources before triggering an alert, which by nature, will take more time.
- **Batch process detection engine:** The batch process detection engine will run parallel analytics on large-scale datasets, which can take even longer.

## Accessing security alerts

The number of security alerts you see in the Security Center dashboard may vary depending on the amount of resources that you are monitoring with Security Center and the business itself. Some organizations receive more alerts than others, and as a result, they have more security alerts.

If you don't have any security alerts in your environment, simulate one by following the procedures in the article at https://aka.ms/ASCalertValidation. Once you have an alert, follow these steps to access it:

1. Open the Azure Portal and sign in as a user who has Security Admin privileges.
2. In the left pane, click Security Center.
3. In the left pane of the Security Center window, under Threat Protection, click Security Alerts. The Security Alerts dashboard appears (see Figure 6-3).

![](img/4b11e95292819ab1a383a41ef73aedb4_133_0.png)

FIGURE 6-3 Security Alerts dashboard

4. The Security Alerts dashboard lists current alerts—organized by severity (with high-severity alerts listed first)—and a bar graph showing the distribution of high-, medium-, and low-severity alerts. Click an alert type to open a new blade showing resources that have been flagged with the alert (see Figure 6.4).

![](img/4b11e95292819ab1a383a41ef73aedb4_134_0.png)

FIGURE 6-4 List of attacked resources

The list contains the following information about each attacked resource:

- The name of the attacked resource
- The number of times the resource was attacked
- The time at which the attack was detected
- The environment in which the resource resides
- The state of the alert
- The severity of the alert

5. Click an attacked resource to see details about the attack, as shown in Figure 6-5. (Note that the Subscription ID has been intentionally obscured in this figure).

![](img/4b11e95292819ab1a383a41ef73aedb4_134_1.png)

FIGURE 6-5 Details of a security alert

6. Return to the main Security Center dashboard.

> TIP You can use the Azure Activity Log to query security alerts originated by Azure Security Center. For more information, see https://aka.ms/ASCActivityLog. You can also use the Alert API to obtain these alerts; see https://aka.ms/ASCAlertAPI for details.

## Detection scenarios

There are many scenarios in which Security Center will rapidly warn you about suspicious activity. The following sections cover some important scenarios to give you an idea of how powerful Security Center detections are and the advantage of using multiple data sources to enhance the confidence level of an alert.

## Detecting spam activity

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

![](img/4b11e95292819ab1a383a41ef73aedb4_135_0.png)

FIGURE 6-6 Spam alert

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

## Crash analysis

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

Wait, the OCR text provided has repetitive sections in the latter half. I will provide the clean, corrected version based on the provided content.

[content]
is called anomaly detection. This triggers alerts when it detects deviations from established baselines that conform to a potential attack vector.

Regardless of which capability Security Center uses to identify a threat, the result will be externalized in the dashboard as a security alert. A security alert contains valuable information about what triggered the alert, the resources targeted, the source of the attack, and suggestions to remediate the threat. Security alerts are divided into categories:

- **Virtual Machine Behavioral Analysis (VMBA):** This type of alert uses behavioral analytics to identify compromised resources based on an analysis of the virtual machine (VM) event logs, such as process-creation events, in memory only (fileless attack), and login events.
- **Network analysis:** This type of alert collects security information from your Azure Internet Protocol Flow Information (IPFIX) traffic and analyzes it to identify threats. An example of an alert that belongs to this category is the Suspicious Incoming RDP Network Activity From Multiple Sources.
- **Resource analysis:** This analyzes your Platform as a Service (PaaS) services, such as Azure SQL, and triggers alerts based on this analysis. An example of an alert that belongs to this category is the *Potential SQL Injection* alert.
- **Contextual information:** This provides extra context to reach a verdict about the nature of the threat and how to mitigate it.

> **IMPORTANT** Because the list of alerts is constantly evolving, we recommend that you visit https://aka.ms/ASCAlerts to obtain the latest list of security alerts.

## Understanding alerts

Before Security Center triggers an alert, it needs to have a certain level of certainty that the alert is a *true* positive. The intent is to reduce false positive results and provide a high-quality alert level. To accomplish that, Security Center performs the following actions shown in Figure 6-1 during the alert normalization.

![](img/4b11e95292819ab1a383a41ef73aedb4_132_0.png)

FIGURE 6-1 Evaluation priority to trigger an alert

When an alert is finally triggered, you will be able to answer five questions that are important for your investigation. The questions are shown in the Alert blade, as shown in Figure 6-2.

![](img/4b11e95292819ab1a383a41ef73aedb4_132_1.png)

FIGURE 6-2 The alert blade has the answers for the major investigation's questions

It is important to emphasize that not all alerts will have the same level of information; it really depends on the type of threat and the analytics for that threat. Also, alerts will take differing amounts of time to trigger. Security Center has three major detection engines that will dictate the time for an alert to be triggered.

- **Event-based detection engine:** The event-based detection engine will trigger alerts near real time.
- **Query-based detection engine:** The query-based detection engine works on different events from different sources before triggering an alert, which by nature, will take more time.
- **Batch process detection engine:** The batch process detection engine will run parallel analytics on large-scale datasets, which can take even longer.

## Accessing security alerts

The number of security alerts you see in the Security Center dashboard may vary depending on the amount of resources that you are monitoring with Security Center and the business itself. Some organizations receive more alerts than others, and as a result, they have more security alerts.

If you don't have any security alerts in your environment, simulate one by following the procedures in the article at https://aka.ms/ASCalertValidation. Once you have an alert, follow these steps to access it:

1. Open the Azure Portal and sign in as a user who has Security Admin privileges.
2. In the left pane, click Security Center.
3. In the left pane of the Security Center window, under Threat Protection, click Security Alerts. The Security Alerts dashboard appears (see Figure 6-3).

![](img/4b11e95292819ab1a383a41ef73aedb4_133_0.png)

FIGURE 6-3 Security Alerts dashboard

4. The Security Alerts dashboard lists current alerts—organized by severity (with high-severity alerts listed first)—and a bar graph showing the distribution of high-, medium-, and low-severity alerts. Click an alert type to open a new blade showing resources that have been flagged with the alert (see Figure 6.4).

![](img/4b11e95292819ab1a383a41ef73aedb4_134_0.png)

FIGURE 6-4 List of attacked resources

The list contains the following information about each attacked resource:

- The name of the attacked resource
- The number of times the resource was attacked
- The time at which the attack was detected
- The environment in which the resource resides
- The state of the alert
- The severity of the alert

5. Click an attacked resource to see details about the attack, as shown in Figure 6-5. (Note that the Subscription ID has been intentionally obscured in this figure).

![](img/4b11e95292819ab1a383a41ef73aedb4_134_1.png)

FIGURE 6-5 Details of a security alert

6. Return to the main Security Center dashboard.

> TIP you can use the Azure Activity Log to query security alerts originated by Azure Security Center. For more information, see https://aka.ms/ASCActivityLog. You can also use the Alert API to obtain these alerts; see https://aka.ms/ASCAlertAPI for details.

## Detection scenarios

There are many scenarios in which Security Center will rapidly warn you about suspicious activity. The following sections cover some important scenarios to give you an idea of how powerful Security Center detections are and the advantage of using multiple data sources to enhance the confidence level of an alert.

## Detecting spam activity

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. If the result of this correlation is that the traffic is suspicious, Security Center triggers the alert shown using built-in analytics, machine learning, and threat intelligence from Office 365. Performing these three steps provides not only more precise detection but also a higher level of confidence in the alert.

![](img/4b11e95292819ab1a383a41ef73aedb4_135_0.png)

FIGURE 6-6 Spam alert

## Crash analysis

In this scenario, the attacker compromises an Azure VM and uses the compromised VM to send spam emails. Using machine learning, Security Center can detect a spike in SMTP traffic. It then queries other data sources to make sure this spike is because of malicious behavior. Finally, it correlates this traffic with the Office 365 spam database to determine whether it is legitimate traffic. (Rest of text continues with repetitive patterns as provided in source).
