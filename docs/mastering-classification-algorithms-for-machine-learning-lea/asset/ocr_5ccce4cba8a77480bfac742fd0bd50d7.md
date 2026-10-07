# Data suitable for applying Encoders

In Annexure 6, Vectorizers, we discussed converting data into numeric data to build machine learning models. We may have some non-numeric data; however, they are specific values. For example, when capturing demographic data, we may have a data element to capture the status of an individual. The values of Marital status could be possibly “Married”, “Single”, “Divorced”, “Widow”, or “Widower”. Generally, we would capture the value of Marital Status as these literals make capturing easy. If we use online forms, we may have a program that converts values such as “Married” to 0, “Single” to 1, and so on. If this is the case, we have numeric data and no concerns. However, if we have the data as “Married”, “Single”, and so on, we need a mechanism to convert them to numeric data.

Another example is the type of rooms in a hotel. These could have values such as “Deluxe”, “Super Deluxe”, “Suite” and so on. Or, if we are making a model for forming a suitable football team, we could have the data for the position where the player plays as “Center Forward”, “Goalkeeper”, “Midfielder”, among others.

All types of non-numeric data which convey a specific meaning are the types of data that can be converted to numeric data using Encoders.

Now, different Encoders can be suitable for the different kinds of data we discussed. Let us discuss the different types of Encoders.

# Label Encoder

In Encoders, we find all the unique values for a field, and we assign a numeric code for each value. For example, suppose we have a field in our data called Marital Status. Now, we figure that the unique values of the field of Marital Status are “Married”, “Single”, “Divorced”, “Widow”, and “Widower”. So, we have five values for the field of Marital Status. What we could do, we assign a value of 0 for “Married”, 1 for “Single”, 2 for “Divorced”, 3 for “Widow”, and 4 for “Widower”. By doing this, we can distinctly distinguish which records are for married people, single people, and so on. Moreover, if we are given a value for Marital Status as a numeric code, we can convert it to its label equivalent. For example, under this scheme, if we are told that the Marital Status is 2, we know that the record is for a divorced person.

When we have data for a particular field where the different values do not relate, we can use the Label Encoder. For example, for the values of the field Marital Status, there is no relationship between the values “Married”, “Single”, “Divorced”, “Widow”, and “Widower”. In this situation, we only need to assign a numeric code