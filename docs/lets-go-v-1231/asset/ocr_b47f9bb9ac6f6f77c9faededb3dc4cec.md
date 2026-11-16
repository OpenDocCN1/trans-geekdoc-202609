# Testing

And so we finally come to the topic of testing.

Like structuring and organizing your application code, there’s no single ‘right’ way to structure and organize your tests in Go. But there are some conventions, patterns and good-practices that you can follow.

In this section we’re going to add tests for a selection of the code in our application, with the goal of demonstrating the general syntax for creating tests and illustrating some patterns that you can reuse in a wide-variety of applications.

You'll learn:

+   - How to create and run table-driven unit tests and sub-tests in Go.
+   - How to unit test your HTTP handlers and middleware.
+   - How to perform ‘end-to-end’ testing of your web application routes, middleware and handlers.
+   - How to create mocks of your database models and use them in unit tests.
+   - A pattern for testing CSRF-protected HTML form submissions.
+   - How to use a test instance of MySQL to perform integration tests.
+   - How to easily calculate and profile code coverage for your tests.