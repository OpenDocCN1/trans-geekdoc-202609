# 8.27 The Internet of Things

| IV. | Securely store credentials and security-sensitive data |
| --- | --- |
| | Any credentials must be stored securely within services and on devices. Hardcoded credentials in device software, which can be easily discovered through reverse engineering, are not acceptable. Security-sensitive data should be stored securely.36 |
| V. | Communicate securely |
| --- | --- |
| | Appropriate encryption should be used for data relevant to the security of the device. |
| VI. | Minimise exposed attack surfaces |
| --- | --- |
| | Processor, user or program access should be restricted to only the information necessary for the legitimate purpose, and no more (‘Principle of least privilege’). Unnecessary code or hardware which exposes the device should be minimised. |
| VII. | Ensure software integrity |
| --- | --- |
| | The consumer, or a company administrator, should be notified if an unauthorised change or reboot is detected. |
| VIII. | Ensure that personal data is protected |
| --- | --- |
| | The processing of personal data must be in accordance with data protection law. Within the UK, this will be in accordance with the Data Protection Act 2018. Within the EU, the General Data Protection Regulation (GDPR) will apply. |
| IX. | Make systems resilient to outages |
| --- | --- |
| | The IoT device or service should continue to function despite operational issues. |
| X. | Monitor system telemetry37 data |
| --- | --- |
| | All telemetry data, such as usage and measurement data, should be monitored for security anomalies (but only if this data is collected). |
| XI. | Make it easy for consumers to delete personal data |
| --- | --- |
| | Consumers should be provided with clear instructions which allow for the deletion of their personal data. |
| XII. | Make installation and maintenance of devices easy |
| --- | --- |
| | Installation and maintenance should require minimal steps and should follow best security practice. |

36 National Institute of Standards and Technology (NIST) Special Publication 800-63B: 'Digital Identity Guidelines, Authentication and Lifecycle Management, 2017' suggests that best practice includes the use of cryptographic keys and initialisation vectors, with credentials stored within a Trusted Execution Environment (see: https://pages.nist.gov/800-63-3/sp800-63b.html).

37 In this context, 'telemetry' means wireless data transfer. An IoT device which suddenly has a spike in data transfer may have been hacked as a result of the external threat gaining access to the device or subsequently using the device. The Code requires that this telemetry is monitored to detect these spikes, but only if this data is already being collected. The Code does not require additional monitoring, as this may be contrary to the privacy of the user.