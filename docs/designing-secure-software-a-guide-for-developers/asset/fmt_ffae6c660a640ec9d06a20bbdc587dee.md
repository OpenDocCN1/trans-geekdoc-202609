
# Assessing Design Security

You can skimp on writing up the report if this level of rigor feels too fussy, but the chances are good that you, or someone else working on the software, will later wish that the details had been recorded for future reference. At a bare minimum, I suggest taking the time to send an email summary to the team for the record. Even a minimal report should not just say "Looks good!" but should back that up with a substantive summary. If the design covered all the security bases, reference a few of the most important design features that security depends on to underscore their importance. In the case of a design where security is a non-factor (for example, I once reviewed an informational website that collected no private information), outline the reasoning behind that conclusion.

The style, length, and level of detail in these reports varies greatly depending on the organizational culture, available time, number of stakeholders, and many other factors. When, as reviewer, you collaborate closely with the software designer, you may be able to incorporate needed provisions directly into the design document, rather than enumerating issues in need of change in a report. Even for small, informal projects, assigning separate designer and reviewer roles is worthwhile so there are multiple sets of eyes on the work, and to ensure that security is duly considered. However, even a solo design benefits from the designer going back over their own work with their security hat on for fresh perspective.

## 6. Follow Up

Follow up on agreed design changes resulting from a security review to confirm they were resolved correctly. When the collaboration has gone well, I usually just check that documentation updates happened without looking at the implementation (and that approach has never backfired in my experience). In other circumstances, and subject to your judgment, reviewers may need to be more vigilant. Sign off on the review when it's complete, including the verification of all necessary changes. Assigning the SDR in the project bug tracker is a great way to track progress reliably. Otherwise, use a more or less formal process if you prefer. Here are a few pointers for this final stage:

*   For major security design changes, you might want to collaborate with the designer to ensure that changes are made correctly.
*   Where opinions differ, the reviewer should include a statement of both positions and the specific recommendations that weren't followed to flag it as an open issue. ("Managing Disagreement" on page 121 talks about this topic in more detail.)

In the best case, the designer looks to the reviewer as a security resource and will continue engaging as needed over time.

## Assessing Design Security

Now that we've covered the SDR process, this section delves into the thought processes behind conducting the review. The material in this book up to this point has given you the concepts and tools you need to perform an SDR. The foundational principles, threat modeling, design techniques, patterns, mitigations, crypto tools—it all goes into the making of a secure design.

### Using the Four Questions as Guidance

The Four Questions used for threat modeling in Chapter 2 are an excellent guide to help you conduct an effective SDR. Explicit threat modeling is great if you have the time and want to invest the effort, but if you don't, using the Four Questions as touchstones is a good way to integrate a threat perspective into your review. More detailed explanations will be given in the subsections that follow, but at the highest level, here is how these questions map onto an SDR:

1.  **What are we working on?**
    The reviewer should understand the high-level goals of the design as context for the review. *What's the most secure way of accomplishing the goal?*
2.  **What can go wrong?**
    This is where "security hat" thinking comes in, and where to apply threat modeling. *Did the design fail to anticipate or underestimate a critical threat?*
3.  **What are we going to do about it?**
    Review what protections and mitigations you find in the design. *Can we respond in better ways to the important threats?*
4.  **Did we do a good job?**
    Assess whether the mitigations in the design suffice, if some might need more work, or if any are missing. *How secure is the design, and if lacking, how can we bring it up to snuff?*

You can use the Four Questions as a tickler while working on an SDR. If you've read the design document and noted areas of focus but don't know exactly what you are looking for yet, run through the Four Questions—especially #2 and #3—and consider how they apply to specific parts of the design. From there, your assessment will naturally shift to #4. If the answer isn't "We're doing just fine," it likely suggests a good topic of discussion, or an entry you should include in the assessment report.

#### What Are We Working On?

There are a few specific ways this question keeps you on track. First, it's important to know the purpose of the design so you can confidently suggest cutting any part that incurs risk but is not actually necessary. Conversely, when you do suggest changes, you don't want to break a feature that's actually needed. Perhaps most importantly, you may be able to suggest an alternative to a risky feature that takes a new direction.

For example, in the privacy space, if you're reviewing a payroll system that collects personal information from all employees, you might identify a health question as particularly sensitive. If the data item in question is truly superfluous, then cutting it from the design is the right move. However, if it's important to the business function the design serves, instead you can propose ways to stringently protect against disclosure of this data (such as early encryption, or deletion within a short time frame).

#### What Can Go Wrong?

The review should confirm that the designer has anticipated the important threats that the system faces. And it's not enough for the designer to be aware of these threats; they must have actually created a design that lives up to the task of withstanding them.

Certain threats may be acceptable and left unmitigated, and in this case, the reviewer's job is to assess that decision. But it's important to be sure that the designer is aware of the threat and chose to omit mitigation. If the design doesn't say explicitly that this is what they are doing, note this in the SDR to double-check that it's intentional. Also note the risk being accepted and explain why it's tolerable. For example, you might write: "Unencrypted data on the wire represents a snooping threat. However, we determined that the risk is acceptable because the datacenter is physically secured, and there is no potential for exposure of PII or business-confidential data."

Try to anticipate future changes that might invalidate this decision to accept the risk. Building on the example just mentioned, you might add, "If the system moves to a third-party datacenter we should revisit this physical network access risk decision."

#### What Are We Going to Do About It?

Security protection mechanisms and mitigations should become apparent in the design as the reviewer studies it. Reviewers typically spend most of their time on the last two questions: identifying what makes the design secure and assessing how secure it is. One way of approaching this task is by matching the threats to the mitigations to see if all bases are covered. Pointing out issues arising from this question and confirming that the design is satisfactory are among the most important contributions of an SDR.
