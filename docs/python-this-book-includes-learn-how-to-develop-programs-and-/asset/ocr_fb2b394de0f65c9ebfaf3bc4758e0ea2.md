```
"encoded_value = le.fit_transform(["Paris", "Paris", "Tokyo", "Amsterdam"])
print(encoded_value)[1120]"
```

We just transformed our labels for string data into numerical values. The first step was importing the preprocessing module that offers the "LabelEncoder()" technique. Followed by the development of an object representing the "LabelEncoder()" type. Then, the "fit_transform()" function of the object was used to distinguish between the list's distinct classes ["Paris", "Paris", "Tokyo", "Amsterdam"] and output the encoded values of [1 120].

The technique of "LabelEncoder()" assigns the numerical values with regards to the classes' alphabetically to the classes, for example \(A)msterdam was assigned code "0", \(P)aris was assigned code "1" and \(T)okyo was assigned code "2".

# Creating Training and Test subsets

Know the interactions between distinct characteristics and how these characteristics influence the target variable, a collection of information must be learned by a machine learning algorithm. We need to split the complete data set into two subsets to accomplish this. One subset will serve as the training data set, which will be used to train our algorithm to construct machine learning models. The other subset will serve as the test data set, which will be used to test the accuracy of the predictions generate by the machine learning model.

The first phase in this stage is the separation of feature and target variables using the steps below:

+   **Step 1** – To select data excluding select columns, use command "select columns other than 'Opportunity Number', 'Opportunity Result_cols' = [col for col in sales_data.columns if col not in ['Opportunity Number','Opportunity Result']']"
**Step 2** – To drop these select columns, use the command "dropping 'Opportunity Number' and 'Opportunity Result' columns data = sales_data[cols]"