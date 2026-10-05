# Chapter 25 Takeaway Lessons 515

something, and you have to update the controls. Either way, documented and communicated controls help everyone to understand expectations and row in the same direction.

Technical controls are all the mitigations you can implement using software or hardware to enforce a particular input, action, or output. Whenever possible, implement a technical control to mitigate your biggest threats. Such controls help down the majority of your risks and do so automatically. This is where MFA comes into play. If used correctly, they can significantly reduce many types of threats. But any MFA solution cannot do it. It takes a complete defense-in-depth strategy with correctly selected and implemented MFA controls.

Lastly, some amount of badness will always get your technical controls. I don't care what you implement; technical controls are not perfect, and hackers find ways around them. Educate yourself, staff, and co-workers on how to stop badness when they have existing technical controls and what they should do when they (hopefully) report and mitigate it. Ensure that your MFA solution includes all the necessary components (policy, technical, education) to be as useful as it can be.

# There Is No Single MFA Solution for Everyone

As covered in Chapter 23, "Selecting the Right MFA Solution," no single MFA solution is best for everyone. No MFA solution works with everything. You must first determine what case scenarios in your organization must be protected by MFA and find the solutions that work with your use cases and applications.

Different people and organizations have different risk scenarios and levels of risk acceptance. What works well with my employers and is seen as "overkill" would probably not be seen as minimally acceptable at a national research lab or military weapons dept. Follow the concepts in Chapter 23 to help you find the best solution(s) for your organization and personal needs.

# There Are Better MFA Solutions

With that said, there are some MFA solutions that are better than others. Those that attempt to mitigate concern, large threats are better than those that do not. Those that use mutual authentication are more secure than those that do one-authentication. MFA solutions that use Security Development Lifecycle (SDL) programming methods and use effective threat modeling to reduce risk are better than those that do not. Phone apps are more secure than SMS-based solutions. Phone apps with push messages are often more secure than those that do not use push messages. OTP tokens that use industry-accepted algorithms are likely stronger than those that do not. MFA solutions that use industry-accepted cryptography and key sizes are stronger than that do not. Hardware and software multifactor tokens are more secure than single-factor solutions. Solutions that require prereistration are more secure than those that do not. And so on. Use the methods you've learned in this book to look at different MFA solutions, even of similar types, and pick the best ones. The next section of this chapter will review the individual developer and recommendations for various types of MFA solutions.