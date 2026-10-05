308 Elements of Reproducible Data Science

the software. The third practice is to create temporary, reproducible environments with container technology. Also note that data science reproducibility pertains to the broadest sense of allowing anyone to easily run code. Examples include an engineering team, another data scientist, or a group of students running Python in an environment.

Since this is an introductory book on data science, advanced topics like continuous integration / continuous deployment (CI/CD) and data versioning are out of scope. The interested reader can consult [44] to learn about CI/CD. Model monitoring will be discussed in the next chapter.

# 16.1 Sharing Code

The easiest, safest way to share code is with a tool like GitHub, which we have been using for this book. Properly documenting and maintaining a project's code repository ensures the promotion of code to engineering. A README file should be present in the repo to provide an overview of the purpose and use of the code. This can include summaries of the important functions with their inputs and outputs. The README can include testing procedures, which will be discussed in the next section. The code files should include documentation to understand the purpose of the important variables and functions, and the overall logic of the file.

The code will likely change after it is released to downstream users, including engineering and customers. For example, it is important to track each package of code for future reference. This practice is called version the software. Different code formats, such as GitHub, provide functionality for managing the code release from a repository. The specific steps are outside the scope of this text, and will likely change over time, but awareness of this process is important. Different customers might use, and even require, different versions of project code. It is essential to have a way to release different code versions, to track them, and to maintain them over time.

# 16.2 Testing

There are many kinds of testing in software development, and we will briefly review some pertinent tests for data science. Unit testing gives developers confidence that their code performs as expected. The process consists of writing unit tests, which are used to test discrete units of code as functions. Writing tests for each small piece of code enables rapid testing, isolation of