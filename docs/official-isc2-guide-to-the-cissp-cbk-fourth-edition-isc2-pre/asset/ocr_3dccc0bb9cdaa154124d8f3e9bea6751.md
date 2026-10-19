One of the earlier solutions users found to this problem was signing messages with Pretty Good Privacy (PGP). However, this did not prevent impersonation or faked identities, as digital signatures were not a requirement, and indeed would be unsuitable for the repudiation problem implied. To make matters worse, NNTP offers a cancellation mechanism to withdraw articles already published. Naturally, the same authentication weakness applies to the control messages used for these cancellations, allowing users with even moderate skills to delete messages at will.

On a related note, NNTP feeds have been plagued with spam for more than a decade (in essence, since Usenet spam became economically viable). A number of mechanisms to deal with this problem have evolved. It can be safely said that all technical measures are just add-ons to what is mostly a social self-regulation mechanism. The original Usenet way of dealing with unwanted information was maintenance of client-based blacklists by the user, so-called killfiles.

Some newsgroups have been set up as moderated to prevent misuse, mostly by partisan participants, but naturally the mechanism also works against spam, even though it comes at an increased workload to the moderator of a newsgroup. Over time, a convention evolved, after which messages classified as spam by well-defined criteria (excessive repetitions or cross-posting of identical or highly similar messages) were legitimate targets for cancellations. The problem of authentication has never been adequately addressed in NNTP, and it might even be undesirable to do so: In a certain way, Usenet as a social construct may well depend on the ability to post anonymously or under pseudonyms.

# Finger User Information Protocol

Finger is an identification service that allows a user to obtain information about the last log-in time of a user and whether he or she is currently logged into a system. The "fingered" user has the possibility to have information from two files in his or her home directory displayed (the .project and .plan files).

Developed as early as 1971, Finger is implemented as a UNIX daemon, fingerd. Finger has become less popular for several reasons:

+   - Finger has been the subject of a number of security exploits.
+   - Finger is raising privacy and security concerns; it can easily be abused for social engineering attacks.
+   - The user’s self-actuation (an important social aspect in early UNIX networks) happens through webpages today.