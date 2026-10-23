+   - The username part of an email address *may or may not* be case-sensitive — it depends on the email provider. Almost every major email provider treats the username as case-insensitive, but it is not absolutely guaranteed. All we can say here is that the real-life user behind the address `alice@example.com` is *very probably* (but not definitely) the same as `ALICE@example.com`.

So, what does this mean for our application?

From a security point of view, we should always store the email address using the exact casing provided by the user during registration, and **we should send them emails using that exact casing only**. If we don’t, there is a risk that emails could be delivered to the wrong real-life user. It’s particularly important to be aware of this in any workflows that use email for authentication purposes, such as a password-reset workflow.

However, because `alice@example.com` and `ALICE@example.com` are *very probably* the same user, we should generally treat email addresses as case-insensitive for comparison purposes.

In our registration workflow, using a case-insensitive comparison prevents users from accidentally (or intentionally) registering multiple accounts by just using different casing. And from a user-experience point-of-view, in workflows like login, activation or password resets, it’s more forgiving for users if we don’t require them to submit their request with exactly the same email casing that they used when registering.