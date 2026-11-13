# Maintaining Security while
Working with User Input

# IN THIS CHAPTER

+   - Using caution with user input
+   - Cleaning user data
+   - Storing data
+   - Returning data
+   - Understanding the Flash security sandbox

Working with user input focuses on the best practices of
storing and returning data while maintaining a high level of
security.

This chapter is broken into sections that focus on a specific aspect of hand-
ling user data. This is not a step-based guide on working with user data,
which can be found in Chapter 4. Instead, this chapter focuses on the
specifics of security when handling that data.

The subtopic covered in this chapter is working with and understanding the
sandbox in Flash. Basically, the sandbox is a container that each application
runs in, but the section goes into greater detail and provides visual examples
to better explain the sandbox and how it affects your applications.

The practices provided in this chapter can be adapted to future applications
you develop. Maintaining a secure application is about as important as lock-
ing your home before you leave. An application will technically still work if
it is not secure. However, the lifespan of that application is not certain. There
are many aspects to security in an application: sanitized data, secure logins,
file storage, and exploitability, to name a few. In this chapter, the focus is
the security of user input. User input is any piece of data the user can modify.
This list of data includes cookies, logins, sessions, and file uploads.

# Using Caution with User Input

User data expands far beyond a simple text box on a contact form. Now that
you know what data is considered user input, you’re probably wondering
how something as harmless as a file upload system poses a security risk.

As with most security, it isn’t the technology or feature that is flawed, but
how it is implemented.