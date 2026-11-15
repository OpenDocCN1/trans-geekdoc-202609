her name to make the necessary changes. If this is not done rigorously, the result is an unreliable data store that is very difficult to manage. If, instead, we had embedded Courses into Students, an update to the Course details would entail accessing all Student documents.

The alternative approach to *embedding* is *referencing*. This concept is much closer to the way that foreign key references are used in a relational database. Using the same example as above, we could put Course documents and Student documents into different collections, as in the following example.

```
{
  "Courses": [
    {"_id": "DB102",
    "courseName": "Databases",
    "creditValue": 15,},
    {"_id": "SW101",
    "courseName": "Python",
    "creditValue": 10,}
  ]
}
{
  "Students": [
    {"_id": "12345",
    "name": "Abby Akbar",
    "courses": [ {"courseld": "DB102", "grade": 3.4},
    "courseld": "SW101", "grade": 3.8] }
  ],
  {"_id": "67890",
    "name": "Bill Briggs",
    "courses": [ {"courseld": "DB102", "grade": 3.2} ] }
  ]
}
```

Here, the two collections contain a list of Course documents and a list of Student documents, respectively. The relationships between students and courses are recorded by references from Student documents to the identifiers of Course documents. This avoids the data redundancy of the previous example, but introduces other issues. For instance, if we want to obtain the total value of credits gained by a student, we have to read additional Course documents to get the necessary information. This is roughly the equivalent of a join in a relational system.

The relationship between Courses and Students is many-to-many (so in the example above, a Student document needs to contain references to multiple Course documents). We could resolve this by inventing a new Course-Student document, equivalent to a