# # Refining Your Estimation

Talk with your clients and get the answers to your new questions. It’s important that they be available because you don’t want these issues to hold up your work. In addition, each of your clients (Wendy, the project manager; Wade, the accountant; Edwina, the sales manager; and Harold, the salesperson) will be using the system in some respect, so it’s really their project and you’re the one who makes it go.

Meanwhile, your client questions have been answered:

+   - [ ] Q: Can the notifications be done utilizing e-mail?
+   - [ ] A: Yes, and any summaries associated with the e-mail should be included as attachments.
+   - [ ] Q: Are there indeed three types of users: managers, salespeople, and accountants?
+   - [ ] A: Yes.
+   - [ ] Q: Can the accountant accept CSV for the expense report export?
+   - [ ] A: Yes, he does it all the time.
+   - [ ] Q: How does the accountant want to specify the export: by employee, by employee and date, or by something different, such as sales manager?
+   - [ ] A: Just by employees and date.

That leaves you with only the technical questions:

+   - [ ] How do you e-mail something using PHP?
+   - [ ] What about e-mail attachments?

# ## The Spike

Of course, the last two questions are rhetorical technical questions. Your clients do not have the answers to your technical questions — that’s your area. At this point, you don’t have enough information to make a complete estimate.

It’s time to do some homework, called a *spike*. Although the work may seem tangential, it is required in order to determine whether your line of thought will pay off or, in this case, answer a technical question.

Set aside some time to determine the *if* or *how* questions that invariably show up. These things may take some time, possibly a day or two, but in this case the answer is arrived at in short order. A walk through the PHP API reveals the following:

```
`mail( "wade@widgetworld.com", "Email Spike Test", "One\\nTwo\\nThree" );`
```

Yes, PHP can send e-mail in an easy fashion, so now you must test it or talk to the administrator in order to get it working.

As for e-mail attachments — those are not so easy. PHP does not support attaching e-mail as an easy-to-use function, but that’s because the MIME e-mail definition is well documented in RFCs such as RFC 822 (message headers), 2045 (MIME), and 2046 (MIME types). Therefore, a lot of reading and a little bit of coding result in this tidbit: