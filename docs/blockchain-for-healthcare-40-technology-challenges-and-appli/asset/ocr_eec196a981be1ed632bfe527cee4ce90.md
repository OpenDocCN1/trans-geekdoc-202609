![](bbox=[0.108, 0.108, 0.892, 0.406])

FIGURE 16.4
User interface (patient summary screen).

# 16.4.4.1 The Chaos Engineering Experiment to Test Reliability

Chaos engineering experiments purposefully try to create turbulent conditions in real production environment to test the system and find weaknesses in real time. We conducted chaos engineering experiment to prove the reliability of the BDT app by simulating the tampering of patient data from the backend for a specific patient, and then compared the “before tampering” results with results “after tampering.”

First, we ran the steps as described in Section 3.1 by adding data for a new patient, that is, Patient 6. As soon as the new Patient 6 record was added, the controller was invoked, and steps, as discussed in Section 3.1, were executed. Finally, an email was sent to the doctor with the readings as shown in Scenario A column of Table 16.1.

We then tampered the values for Patient 6, from the backend on PostgreSQL database to invalid values. The tampered values are shown in the Tampered Values column of Table 16.1, where we have modified the body mass index value to 100, and blood pressure and cholesterol level values to 190 and 190, respectively. Maximum blood pressure was tampered to 101, and hypertension was changed to 250.

After these values were changed from the backend, we ran the BDT app again. The controller was invoked, and steps as disused in Section 3.1 were executed. An email was sent to the doctor with the readings as shown in Scenario B of Table 16.1.

Based on the comparison between Scenario A values and Scenario B values, it is clear that our blockchain system was able to detect the tampering and revert the records back to the original values, thereby ensuring data reliability against malicious tampering. This is accomplished through the inherent nature of the blockchain, as the application will be able to identify and retrieve correct data values from other blockchain nodes in the network.