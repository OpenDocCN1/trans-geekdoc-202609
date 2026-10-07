data with a unique identifier that has no intrinsic value by itself.
Which method should they implement?

+   (A) Hashing the card data

+   (B) Encrypting the card data

+   (C) Masking the card data

+   (D) Tokenizing the card data

# **Explanation 272. Correct Answer: D. Tokenizing the card data.** Tokenization involves replacing sensitive data with a non-sensitive equivalent, referred to as a token, that has no extrinsic or exploitable meaning or value.

**Option A is incorrect.** Hashing would produce a fixed-size string, which cannot be reversed to its original value, but it doesn’t create a “token” that can be swapped back for the original data.

**Option B is incorrect.** Encryption translates data into another form, or code, so that only people with access to a secret key or password can read it. It does not replace the data with a unique identifier with no intrinsic value.

**Option C is incorrect.** Masking involves hiding parts of data, such as showing only the last four digits of a credit card number. It doesn’t replace the data with a unique identifier.

**Question 273.** A software company is developing a new cloud-based application where clients can store and manage their customer contact details. The stored data does not include financial or medical information but contains phone numbers and email addresses. How should this information be