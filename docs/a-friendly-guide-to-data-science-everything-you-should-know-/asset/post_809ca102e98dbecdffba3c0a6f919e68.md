
Most of the techniques we've talked about have applied only to numeric data. Another common technique that's especially useful with categorical data is creating dummy variables. Dummy variables are derived from a single original feature that has several values. Each value is turned into a separate column representing that value and a binary value indicating if it's the value in the original column. For a given row the dummy variables are all 0 except the one that matches the original column's value.

## CHAPTER 14 READY FOR THE MAIN EVENT: FEATURE ENGINEERING, SELECTION, AND REDUCTION

See Table 14-3 for an example involving the type of pizza ordered. Here, each row represents the order of a specific pizza, so we record what type of pizza it is only in a single column corresponding to that type with a binary value.

### Table 14-3. Four dummy variables created from the Type field

| Order # | Type | Supreme | Vegetarian | Meat-Lover | 2-Topping | 3-Topping | Multi-Topping |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | Supreme | 1 | 0 | 0 | 0 | 0 | 0 |
| 2 | 2-Topping | 0 | 0 | 0 | 1 | 0 | 0 |
| 3 | 3-Topping | 0 | 0 | 0 | 0 | 1 | 0 |
| 4 | Multi-Topping | 0 | 0 | 0 | 0 | 0 | 1 |
| 5 | Vegetarian | 0 | 1 | 0 | 0 | 0 | 0 |
| 6 | Meat-Lovers | 0 | 0 | 1 | 0 | 0 | 0 |

Like the other types of features, generally when dummy variables are created, the original feature is excluded from further work. So we would use the dummy features moving forward in our model and not the Type feature. One thing worth mentioning is that if we have $n$ different types, we really only need $n-1$ dummy variables. In the above example, the final dummy variable (Multi-Topping) being 1 is exactly the same as the other five all being 0. Sometimes the final one is dropped for that reason.

## Combining and Splitting Features

You may also just want to literally combine features. Imagine data that has age stored in two different fields, years and days. Once you've confirmed that the days column holds the number of days what's in the years column, you can simply combine them. You could create a new field in total days by converting the years field to total days and adding the days column value or by converting the days column into a decimal representing the proportion of the year that's complete and add that to the years column. Either way, you've got a new column that has combined two others.

It's also common to split a column into more than one. This is different from creating dummy values because it takes data in a single column and splits into multiple columns with specific values from the original column, all on the same row. It's common to store sex and neutered status in a single column, one about pets, but you might want to have that in two separate columns, one storing only sex and the other only whether the animal is spayed or neutered or not. These might be more valuable as binary features rather than a single feature with four values.

Table 14-4 shows an example of splitting and combining in some pet data. If we want a field that includes both the owner name and pet name, we could easily combine the last name and pet name into one. Similarly, we could split the joint sex and neutered status into new separate fields.

### Table 14-4. New features from combining and splitting, with original data on the left and on the right

| Pet Name | Owner Surname | Pet Sex/ Neuter Status | Coded Pet Name | Pet Sex | Is Neutered |
| --- | --- | --- | --- | --- | --- |
| Michael | Smith | Male/Intact | Smith, Michael | Male | No |
| Marlowe | Jessup | Male/Neutered | Jessup, Marlowe | Male | Yes |
| Luna | Vintner | Female/Spayed | Vintner, Luna | Female | Yes |
| Bella | Rodriguez | Female/Spayed | Rodriguez, Bella | Female | Yes |

Like with other feature adjustments, we usually would not use the old fields (the ones that were used in a split or combination) with the new ones in future modeling.

## Encoded, Frequency, and Aggregated Features

Most of the techniques we've talked about in this section so far involve operating on a single example or row. There are also many valuable features that can be created based on what data the entire column has. There are numerous ways to derive quality features, but we'll talk about three main approaches here: encoding, frequency counts, and aggregation. All of these things can be used in conjunction with the other techniques in this section, such as to create interaction features.

## Target Encoding

A common technique is *target encoding*, where you encode categorical features based on the proportion of each value that occurs in a particular target value. It’s especially common in anomaly detection tasks (like fraud detection—when the thing you’re looking for is very rare), but can be used in other scenarios. For instance, assume we have patient data for people that includes type II diabetes diagnosis (present or not). We know certain characteristics are associated with having diabetes, such as BMI, age, and activity level. If we bucket both BMI and age and activity level as a categorical feature, we could see how many of each bucket have diabetes present. For instance, maybe 18% of people age 60–70 have a diabetes diagnosis, so we could store the value 0.18 in the target-encoded age feature. Every example is that in the 60–70 bucket would have the same target-encoded age, but these can be very valuable in conjunction with other features in a model. We could do the same with BMI and activity level.

See Table 14-5 for an example of what this might look like. In this data, we bucketed age, BMI, and activity level and calculated the proportion of each that had a positive target value (a diabetes II diagnosis) and added to the original data without keeping the buckets in the table.

### Table 14-5. Medical data with new target-encoded features

| ID | Age | BMI | Activity Level | Target-Enc-Age | Target-Enc-BMI | Target-Enc-Activity |
|---|---|---|---|---|---|--|
| 1 | 56 | 29 | Low | 0.09 | 0.19 | 0.26 |
| 2 | 63 | 26 | Medium | 0.18 | 0.19 | 0.15 |
| 3 | 21 | 20.5 | High | 0.01 | 0.04 | 0.02 |
| 4 | 37 | 26.5 | Low | 0.04 | 0.19 | 0.26 |

## Frequency Encoding

Another type of encoding is frequency encoding, which is similar to target encoding, except you encode the count of the value of a particular categorical feature. In the diabetes data example above, we could add a new feature that stores the total count of the particular age bucket across the whole dataset. If there are 3,450 people in the age bucket 60–70, every example with that age bucket would have 3,450 as the value in the new feature. Table 14-6 shows the data from Table 14-5 frequency-encoded.

### Table 14-6. The same medical data as in Table 14-5 with frequency-encoded features

| ID | Age | BMI | Activity Level | Freq-Enc-Age | Freq-Enc-BMI | Freq-Enc-Activity |
|---|---|---|---|---|---|---|
| 1 | 56 | | Low | 73 | 131 | 192 |
| 2 | 63 | 26 | Medium | 121 | 131 | 113 |
| 3 | 21 | 20.5 | High | 11 | 26 | 19 |
| 4 | 37 | 26.5 | Low | 27 | 131 | 192 |
