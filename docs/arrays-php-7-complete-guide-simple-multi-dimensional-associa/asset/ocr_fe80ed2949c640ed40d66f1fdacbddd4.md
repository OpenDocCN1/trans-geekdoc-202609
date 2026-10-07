# Chapter 2 – Multi-dimensional Arrays

After completing this chapter, the student will be able to...

+   - Define and describe the advantages in using multi-dimensional arrays
- Compare a table with a multi-dimensional array
- Create a multi-dimensional PHP array
- Save values into a multi-dimensional PHP array
- Display values in a multi-dimensional array
- Add values from an html form into a multi-dimensional array
- Validate values before placing them into a multi-dimensional array
- Convert JSON data read from a text file into a PHP array
- Convert PHP arrays to JSON objects and save to a text file
- Save array information to a MySQL Database

The previous chapter showed how efficient arrays can be.
However, the question that was not answered

> “How do we handle data from multiple customers?”

A simple array holds information that is related a particular individual component, such as a customer. In order to hold all customers information in memory, we must think in more than one dimension. We need to have the ability to hold multiple components of customer information. We can think of a doctor’s office (before everything became computerized) keeping records of each patient in a file, with all the files for all patients stored within a file cabinet.

Multi-dimensional arrays work in a similar way. A customer’s information is stored in a ‘record’ (similar to the file in the doctor’s office). In our previous example, all of the information related to Fred Smith is kept together in a ‘record’. Multiple records (just like the file cabinet) are kept together in a ‘table’. The ‘table’ would contain all of the customer records.

Spreadsheets work in the same way.

# Figure 2-1 Customers Table

| "Pete" "Smith" | "123 Main Street" |
| "Atlanta" | "GA" 30001 |