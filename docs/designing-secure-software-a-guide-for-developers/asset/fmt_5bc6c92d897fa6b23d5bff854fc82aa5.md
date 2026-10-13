
# Danny Ocean violates parole (an `elevation of privilege`), flies out to meet his old partner in crime, and heads for Vegas. He pitches an audacious heist to a wealthy casino insider, who fills him in on the casino’s operational details (`information disclosure`), then gathers his gang of ex-cons. They plan their operation using a full-scale replica vault built for practice. On the fateful night, Danny appears at the casino and is predictably apprehended by security, creating the perfect alibi (`repudiation` of guilt). Soon he slips away through an air duct, and through various intrigues he and his accomplices extract half the money from the vault (`tampering` with its integrity), exfiltrating their haul with a remote-control van.

Threatening to blow up the remaining millions in the vault (a very expensive `denial of service`), the gang negotiates to keep the money in the van. The casino owner refuses and calls in the SWAT team, and in the ensuing chaos the gang destroys the vault’s contents and gets away. After the smoke clears, the casino owner checks the vault, lamenting his total loss, then notices a minor detail that seems amiss. The owner confronts Danny—who is back in lockup, as if he had never left—and we learn that the SWAT team was, in fact, the gang (`spoofing` by impersonating the police), who walked out with the money hidden in their tactical equipment bags after the fake battle. The practice vault mock-up had provided video to make it only appear (`spoofing` of the location) that the real vault had been compromised, which didn’t actually happen until the casino granted full access to the fake SWAT team (an `elevation of privilege` for the gang). Danny and the gang make a clean getaway with the money—a happy ending for the perpetrators that might have turned out quite differently had the casino hired a threat modeling consultant!

## Mitigate Threats

At this stage, you should have a collection of potential threats. Now you need to assess and prioritize them to best guide an effective defense. Since threats are, at best, educated guesses about future events, all of your assessments will contain some degree of subjectivity.

What exactly does it mean to understand threats? There is no easy answer to this question, but it involves refining what we know, and maintaining a healthy skepticism to avoid falling into the trap of thinking that we have it all figured out. In practice, this means quickly scanning to collect a bunch of mostly abstract threats, then poking into each one a little further to learn more. Perhaps we will see one or two fairly clear-cut attacks, or parts of what could constitute an attack. We elaborate until we run up against a wall of diminishing returns.

At this point, we can deal with the threats we’ve identified in one of four ways:

*   **Mitigate** the risk by either redesigning or adding defenses to reduce its occurrence or lower the degree of harm to an acceptable level.
*   **Remove** a threatened asset if it isn’t necessary, or, if removal isn’t possible, seek to reduce its exposure or limit optional features that increase the threat.
*   **Transfer** the risk by offloading responsibility to a third party, usually in exchange for compensation. (Insurance, for example, is a common form of risk transfer, or the processing of sensitive data could be outsourced to a service with a duty to protect confidentiality.)
*   **Accept** the risk, once it is well understood, as reasonable to incur.

Always attempt to mitigate any significant threats, but recognize that results are often mixed. In practice, the best possible solution isn’t always feasible, for many reasons: a major change might be too costly, or you may be stuck using an external dependency beyond your control. Other code might also depend on vulnerable functionality, such that a fix might break things. In these cases, mitigation means doing anything that reduces the threat. Any kind of edge for defense helps, even a small one.

Here are some examples of ways to do partial mitigation:

### Make harm less likely to occur

1.  Make it so the attack only works a fraction of the time.

### Make harm less severe

1.  Make it so only a small part of the data can be destroyed.

### Make it possible to undo the harm

1.  Ensure that you can easily restore any lost data from a backup.

### Make it obvious that harm occurred

1.  Use tamper-evident packaging that makes it easy to detect a modified product, protecting consumers. (In software, good logging helps here.)

Much of the remainder of the book is about mitigation: how to design software to minimize threats, and what strategies and secure software patterns are useful for devising mitigations of various sorts.

## Privacy Considerations

Privacy threats are just as real as security threats, and they require separate consideration in a full assessment of threats to a system, because they add a human element to the risk of information disclosure. In addition to possible regulatory and legal considerations, personal information handling may involve ethical concerns, and it’s important to honor stakeholder expectations.

If you’re collecting personal data of any kind, you should take privacy seriously as a baseline stance. Think of yourself as a steward of people’s private information. Strive to stay mindful of your users’ perspectives, including careful consideration of the wide range of privacy concerns they might have, and err on the side of care. It’s easy for builders of software to discount how sensitive personal data can be when they’re immersed in the logic of system building. What in code looks like yet another field in a database schema could be information that, if leaked, has real consequences for an actual person. As modern life increasingly goes digital, and mobile computing becomes ubiquitous, privacy will depend more and more on code, potentially in new ways that are difficult to imagine. All this is to say that you would be smart to stay well ahead of the curve by exercising extreme vigilance now.

A few very general considerations for minimizing privacy threats include the following:

*   Assess privacy by modeling scenarios of actual use cases, not thinking in the abstract.
*   Learn what privacy policies or legal requirements apply, and follow the terms rigorously.
*   Restrict the collection of data to only what is necessary.
*   Be sensitive to the possibility of seeming creepy.
*   Never collect or store private information without a clear intention for its use.
*   When information already collected is no longer used or useful, proactively delete it.
*   Minimize information sharing with third parties (which, if it occurs, should be well documented).
*   Minimize disclosure of sensitive information—ideally this should be done only on a need-to-know basis.
*   Be transparent, and help end users understand your data protection practices.

## Threat Modeling Everywhere

The threat modeling process described here is a formalization of how we navigate in the world; we manage risk by balancing it against opportunities. In a dangerous environment, all living organisms make decisions based on these same basic principles. Once you start looking for it, you can find instances of threat modeling everywhere.
