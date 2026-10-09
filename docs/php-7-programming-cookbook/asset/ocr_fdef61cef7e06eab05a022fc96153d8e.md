Here is a successful authentication:

![](bbox=[0.18, 0.179, 0.82, 0.512])

# See also

For guidance on how to avoid CSRF and other attacks, please see Chapter 12, *Improving Web Security*.

# # Using middleware to implement access control

As the name implies, middleware sits in the middle of a sequence of function or method calls. Accordingly, middleware is well suited for the task of “gate keeper”. You can easily implement an **Access Control List (ACL)** mechanism with a middleware class that reads the ACL, and allows or denies access to the next function or method call in the sequence.