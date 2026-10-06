# CHAPTER 14 READY FOR THE MAIN EVENT: FEATURE ENGINEERING, SELECTION, AND REDUCTION

**Table 14-4.** New features from combining and splitting, with original data on the left and on the right

| Pet Name | Owner Surname | Pet Sex/ Neuter Status | Coded Pet Name | Pet Sex | Is Neutered |
| --- | --- | --- | --- | --- | --- |
| Michael | Smith | Male/Intact | Smith, Michael | Male | No |
| Marlowe | Jessup | Male/Neutered | Jessup, Marlowe | Male | Yes |
| Luna | Vintner | Female/Spayed | Vintner, Luna | Female | Yes |
| Bella | Rodriguez | Female/Spayed | Rodriguez, Bella | Female | Yes |

Like with other feature adjustments, we usually would not use the old fields (the ones that were used in a split or combination) with the new ones in future modeling.

# Encoded, Frequency, and Aggregated Features

Most of the techniques we've talked about in this section so far involve operating on a single example or row. There are also many valuable features that can be created based on what data the entire column has. There are numerous ways to derive quality features, but we'll talk about three main approaches here: encoding, frequency counts, and aggregation. All of these things can be used in conjunction with the other techniques in this section, such as to create interaction features.

# Target Encoding

A common technique is *target encoding*, where you encode categorical features based on the proportion of each value that occurs in a particular target value. It’s especially common in anomaly detection tasks (like fraud detection—when the thing you’re looking for is very rare), but can be used