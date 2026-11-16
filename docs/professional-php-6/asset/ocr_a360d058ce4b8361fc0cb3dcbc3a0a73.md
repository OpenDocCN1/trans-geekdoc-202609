This method is of little use when building PHP applications, however. It is rare to want to protect specific scripts, or even directories. Far more likely is the need to restrict functionality delineated in some way that is recognized and understood in PHP, but not necessarily in Apache. Even though replicating the HTTP headers required to emulate this functionality from within PHP itself is feasible, it’s rarely desirable, for a number of reasons:

+   - You have almost no control over the appearance of this box, so it's not exactly a user-friendly approach.
+   - You can't ask for any other information (for example, to pose a security question such as “What is your mother’s maiden name?”)
+   - You can't store any information against the request other than the identity to which the user has logged in.

The list goes on. Thankfully, a third and far more desirable solution is available, and that is to use sessions.

# Definition of a Session

Strictly speaking, a session is defined as a series of consecutive HTTP requests made at designated time intervals by a single user from a single computer on a single Web application.

The general methodology behind sessions is that the first request made by a user will generate a new session, should one not yet exist. Subsequent requests are considered to be part of that session, unless they are made outside some arbitrary time period (the session timeout period).

There is, therefore, a verifiable relationship between sessions and requests. Many requests can yield a single session, so a single session can belong to many requests. It’s a one-to-many relationship, thinking in database terms. You’ll see quite shortly that you can encapsulate this quite neatly in a class hierarchy.

A session is normally used to determine the currently connected user of an application, if any. After a user has successfully logged in for the first time, the application’s database should record the user’s user ID against that session, such that any subsequent requests proffering that session are understood to have been made by that user and no other.

The real meat of a session is the session identifier. This uniquely identifies the session, which may exist concurrently with hundreds of other user sessions. When a session ID is generated and sent to the client for the first time, it is important for the session identifier to be both unique and obscure enough that another, valid session ID could not easily be “invented” by a potentially hostile third party. For example, although issuing session numbers 1, 2, 3, 4, and so on, would certainly satisfy the requirement for uniqueness, it fails to satisfy the security side of the requirement, because a user who has been allocated session number 3 could simply suddenly claim to be session number 4 and potentially gain access to another user’s account as a result.

Session identifiers are more often than not 32-character strings consisting of numbers and letters. This is how PHP’s built-in session handling (discussed later in the chapter) generates session identifiers. The stumbling of one user across a valid session ID of another is unlikely, therefore, except through brute force — and later in this chapter you’ll learn about a couple of easy ways to stop that from happening, too.