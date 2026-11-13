
we perform real-time processing of patient data. On the other hand, Clique does not need huge computing power and resources, thereby making it energy-efficient. In contrast to the proof-of-work algorithm, only predefined authority known as validators are permitted to take part in the consensus process in proof-of-authority algorithm. This is achieved by first validating the transactions, after which blocks are created and appended to the blockchain. The hospital serves as the validator in our scenario.

## 16.4.2 Prediction Accuracy

We calculated the accuracy of the machine learning algorithm using Sklearn’s accuracy_score() function after fitting the random forest model in scikit-learn. The true labels of the sample are accepted by the accuracy_score() method, and the proposed heart attack machine learning model accuracy was 97.1%.

After we fitted the random forest model, we were able to see each individual decision tree from the random forest. The sample source code, as shown in code listing 16.1, first fits the random forest model and then shows all the estimators (i.e., decision trees) from the random forest.

We chose the estimators (decision trees) that gave the maximum accuracy at 97.1%. One of the key challenges while plotting the single decision tree from the random forest is that the decision tree can grow quite deep (large) when it is fully grown (default hyper-parameters), and generally, any tree with depth greater than 6 is very hard to read. Since we wanted to have the tree visualization in a readable format, we built the random forest with max_depth <7 and selected the best estimator that gave us the maximum accuracy, that is, 97.1%.

```
Code Listing 16.1: Sample Random Forest source code
fn=data.feature_names
cn=data.target_names
fig, axes = plt.subplots(nrows = 1,ncols = 5,figsize = (10,2), dpi=900)
for index in range(0, 5):
    tree.plot_tree(rf.estimators_[index],
        feature_names = fn,
        class_names=cn,
        filled = True,
        ax = axes[index]);
axes[index].set_title('Estimator: ' + str(index), fontsize = 11)
fig.savefig('rf_5trees.png')
```

## 16.4.3 Data Analysis and Notifications

As soon as a new patient data is added to the XML file, the controller invokes the smart contract and patient data is stored on the Ganache blockchain and PostgreSQL. Subsequently, the smart contract invokes the heart attack machine learning model, and results are sent to the controller. If the risk of heart attack is predicted, the controller will send an email notification (Figure 16.3) to the doctor indicating the risk of heart attack. In case the doctor needs additional readings, fresh data from the patient can be requested and entered using data feeds interface. Once data is entered using data feeds interface, the XML file will be updated, the controller will be invoked, the heart attack risk will be re-evaluated on the new data, and notifications will be sent appropriately.

Patient Medical Report, ID:9hc7VAqRmCRzIT6wk3eMSWTf4uJK0bzx, Name: patient 6

Healthcare <healthcare-noreply@traqez.com> To Venkatesh Upadrista

We removed extra line breaks from this message.

Patient "patient 6" has no risk of stroke

Patient Name: patient 6
Age: 22
Gender: female
Heart Problems History: no
Cancer History: no
Diabetic History: no
Work Type: software
Residence/Location: rural
Body Mass Index: 18
Smoking: no
Brain Stroke History: no
Environment Temperature: 30
Environment Humidity: 30
Pollution Level: normal
Blood Pressure: 120
Cholesterol Levels: 120
Sugar Levels: 120
Electrocardiogram: 120
Maximum Blood Pressure: 120
Exercise induced angina: no
Hypertension: 100

FIGURE 16.3 Email notification.

## 16.4.4 Data Visualization

The doctors can get email notifications for a patient’s heart attack risk as the main application flow for our BDT app.

Alternatively, in some cases, doctors may want to review patients’ detailed real-time health data, including their past medical history, from electronic health records. To facilitate this, we have created an alternate flow (user interface) which the doctors can use to view detailed patients’ medical reports. The doctor can view all his patients’ records along with any associated heart attack risks by logging to the user interface as shown in Figure 16.4. The details of each patient’s data can be viewed by the doctor by clicking on the individual patient’s name hyperlink.

![](img/f7b65e1b6017d6bb4f421d92025cbdc6_329_0.png)

FIGURE 16.4 User interface (patient summary screen).

### 16.4.4.1 The Chaos Engineering Experiment to Test Reliability

Chaos engineering experiments purposefully try to create turbulent conditions in real production environment to test the system and find weaknesses in real time. We conducted chaos engineering experiment to prove the reliability of the BDT app by simulating the tampering of patient data from the backend for a specific patient, and then compared the “before tampering” results with results “after tampering.”

First, we ran the steps as described in Section 3.1 by adding data for a new patient, that is, Patient 6. As soon as the new Patient 6 record was added, the controller was invoked, and steps, as discussed in Section 3.1, were executed. Finally, an email was sent to the doctor with the readings as shown in Scenario A column of Table 16.1.

We then tampered the values for Patient 6, from the backend on PostgreSQL database to invalid values. The tampered values are shown in the Tampered Values column of Table 16.1, where we have modified the body mass index value to 100, and blood pressure and cholesterol level values to 190 and 190, respectively. Maximum blood pressure was tampered to 101, and hypertension was changed to 250.

After these values were changed from the backend, we ran the BDT app again. The controller was invoked, and steps as discussed in Section 3.1 were executed. An email was sent to the doctor with the readings as shown in Scenario B of Table 16.1.

Based on the comparison between Scenario A values and Scenario B values, it is clear that our blockchain system was able to detect the tampering and revert the records back to the original values, thereby ensuring data reliability against malicious tampering. This is accomplished through the inherent nature of the blockchain, as the application will be able to identify and retrieve correct data values from other blockchain nodes in the network.

TABLE 16.1 Patient 6 Data (Before and After Tampering)

| Patient Data | Scenario A | Tampered Values | Scenario B |
| :--- | :--- | :--- | :--- |
| Patient Name | Patient 6 | | Patient 6 |
| Age | 22 | | 22 |
| Gender | Female | | Female |
| Heart Problem History | No | | No |
| Cancer History | No | | No |
| Diabetic History | no | | no |
| Work Type | Software | | Software |
| Residence/Location | Rural | | Rural |
| Body Mass Index | 18 | 100 | 18 |
| Smoking | No | | No |
| Brain Stroke History | no | | no |
| Environment Temperature | 30 | | 30 |
| Environment Humidity | 30 | | 30 |
| Pollution Level | Normal | | Normal |
| Blood Pressure | 120 | 190 | 120 |
| Cholesterol Levels | 120 | 190 | 120 |
| Sugar Levels | 120 | | 120 |
| Electrocardiogram | 120 | | 120 |
| Maximum Blood Pressure | 120 | 101 | 120 |
| Exercise-Induced Angina | No | | No |
| Hypertension | 100 | 250 | 100 |
| Glucose Levels | 60 | | 60 |

Blockchain is a technology that can be used together with digital twin to eradicate several security and privacy concerns for healthcare use cases [23], [37], [38], [21–23], which we have proved using this experiment.

## 16.5 Discussion

The concept of digital twin has been applied in many domains, including healthcare, which extends the digital twin concept to combine system models and analysis with real-time personal data that can be used to enhance health and life expectancy [39].

The digital twin of a human has been investigated for specific use cases, such as elderly care [14], [40], detecting the severity of carotid stenosis [41], and diagnosis of heart diseases [42]. Few other papers have discussed models that would be helpful to build a DT for ischemic diseases and hypertension [9], [10], [8]. In addition, we find some interesting papers about DT concepts for cardiovascular diseases [11–13] which can be enhanced to create a full-blown heart prediction DT model. Based on these reviews, it can be inferred that there is a lot of ongoing research to create digital twins. However, most of the methods discussed
