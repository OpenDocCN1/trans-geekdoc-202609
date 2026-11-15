The flow chart shown in Figure 4.3 classifies the data according to training data. After noise removal EMI kernel sends the data to ML classifier. The steps are as follows:

+   1. Start.
+   2. Data is send by EMI attenuator which is task from the user.
+   3. If the task==1, it means the instruction given by the user is movement of the wheelchair, otherwise it moves to accessing the computer or smartphone.
+   4. Yes: moves to next block and compares the data by training data. No: Moves to the next decision step.
+   5. If the data matches the training data, then the command is given and flow will end. Otherwise, moves to the 2nd block and again collects the data.
+   6. Steps 4 and 5 will repeat for accessing computer and smartphone.
+   7. End.

![](bbox=[0.12, 0.48, 0.88, 0.9])

Figure 4.3 Flow chart of machine learning classifier.