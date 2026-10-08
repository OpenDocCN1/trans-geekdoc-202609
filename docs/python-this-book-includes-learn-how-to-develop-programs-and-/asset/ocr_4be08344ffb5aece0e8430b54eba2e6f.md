# Data Pre-processing

By now, you should have a clear understanding of what information is available in the data set. To transform categorical labels from the data set such as “won” and “loss” into numerical values, we will use the “LabelEncoder()” technique.

Let's look at the pictures below to see what we are attempting to accomplish with the “LabelEncoder()” technique. The first image contains “color” column with 3 records, namely “Red,” “Green,” and “Blue.” Using the “LabelEncoder()” technique, the record in the same “color” column can be converted to numerical values, as shown in the second image.

| Color | Color |
|---|---|
| 0 Red | 1 |
| 1 Green | 2 |
| 2 Blue | 3 |

Let's begin the real process of conversion now. Using the “fit transform()” technique given by “LabelEncoder(),,” the categorical column’s label like “Route To Market” can be encoded and converted to numerical labels comparable to those shown in the diagrams above. The function “fit transform()” requires input labels identified by the user and consequently returned labels.

To know how the encoding is accomplished, let’s go through an example quickly. The code instance below constitutes string data in the form of a cities’ list such as [“Paris,” “Paris,” “Tokyo,” “Amsterdam”] that will be encoded into something comparable to [2, 2, 1, 3].

+   **Step 1** - To import the required module

+   **Step 3** – To convert the categorical columns into numerical values, use command: