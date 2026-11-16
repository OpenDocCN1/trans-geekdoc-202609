
Admittedly, this chapter doesn’t have a whole lot to do with the specifics of PHP 6. Nonetheless, the material covered here is very relevant to any PHP project you might work on, even though the techniques demonstrated apply just as much to ASP.NET, Java — any language. They are included in this book nonetheless because they might well revolutionize the way you tackle big projects.

## Do Your Homework

Generally, the most common, visible first step for a project occurs when a project manager tells a senior member of his development staff that he has something new for the team to work on, something that often happens as nothing more than an informal chat around the office water cooler or during a smoke break. In practice, of course, the idea behind the project starts much further back. Tracing the roots of any given project is essential. A project management methodology can be successful only if it is applied from the very beginning of the project.

Before you take steps to receive the formal brief for the project, there are a few key questions to ask — your homework, if you will. These questions taken together will form the foundation of the strategy you adapt when receiving the formal brief. The first question to ask is, “Why?”

## Why Is the Project Happening?

This simple question has an enormous influence on everything you do from here on in because the way in which you approach and build your project (from start to finish) should be determined by its intended function.

Typical scenarios underlying the need for a new Web site or application might include the following:

- Starting a new business for which “the business is the application”
- Replacing an existing application that is failing or no longer adequate
- Taking over where an existing supplier has failed to deliver either on time, on budget, or what is required (or, in some cases, all three)

There are, of course, other reasons that may require a new project to be taken on, and not all of them are as critical as the three listed here. For example, you may simply find yourself having to implement the pet project of a VP or executive. Whatever it is, determining the *raison d’être* of the project is a number-one priority.

## Who Is the Project For?

This is sometimes not as easy a question to answer as you might think. At the simplest level, the project is for another department within your own company or organization, a new customer, or an existing customer. Remember that you must identify the recipient of the project in the sense of who has actually commissioned the work. If a man goes to the store to buy his wife nail polish, he’s not the real customer — he’s simply carrying out the real customer’s request.

Similarly, your client may be commissioning this work only to satisfy some requirement of a third party to whom he or she is responsible. These ultimate end users of the product are known as *domain experts*, and you ignore them at your peril.

The end users for your product will often be the most hands-on people in your client’s organization, and as such their needs for the project will often be immensely different from the requisitioning individual who approaches you as a potential supplier.

### Identifying Roles and Agenda

By way of example, say that you are the chief technical officer (CTO) of a medium-size organization, and that you have been commissioned by the human resources (HR) director to build a new intranet for your whole company. You have both permanent and contract staff at your disposal. What do you think the various agendas of each role (you, the client, and the domain experts) are?

To take a slightly cynical perspective on things, the scenario most likely looks something like this:

- You (as a developer) want to deliver a high-quality, effective, efficient, and satisfactory solution as quickly as possible, and with as little investment as possible, so that you look good to your client, your peers, and your boss.
- The HR director wants you to deliver a high-quality, effective, efficient, and satisfactory solution that makes him or her look good.
- Daily users of the intranet (the domain experts) want you to deliver a high-quality, effective, efficient, and satisfactory solution that does what they want it to do.

Notice that the only really selfless agenda here is held by the domain experts. The secret is to ensure that all three agenda are met. The first two are incredibly easy to meet; the latter is the most difficult. But by concentrating on the third, the first two will generally drop into place by default.

Therefore, this is your sweet spot: *look after the domain expert*. Everything you design or build, and every decision you take in the process, should have the domain expert firmly in mind. Sure, *you* may use Pico to edit text files, or Google Chrome to browse the Web, but does your user? Probably not. Rather than take the moral high ground (“well, they *should* be using Pico”), you should deliver what it is they actually want and need.

Realizing the difference between “being right” and “doing right” is what defines the gap between a bedroom coder and a software development professional.

### Manipulating Roles to Your Advantage

Consider this: Your client is merely a conduit to the domain experts on a project, no matter what else he or she might tell you. Although it is a lot easier for your client to express immense pleasure with what you’ve built at the point of delivery and walk away, if the domain experts don’t like it, the axe will fall on the client’s head — and so, in turn, will it fall on yours some days, weeks, or months later. It is very much in the client’s interest to represent the needs of the domain experts from the outset.

A good client will be able to sympathize with the true needs and requirements of his or her domain experts and to assemble them into a single, harmonious voice for you to listen to. However, in practice, you will need to prod, probe, and cajole your client into representing the realistic and reasonable requirements of his or her domain experts properly.

If you feel that your client is not representing his or her domain experts sufficiently, it is vitally important that you suggest that he or she reimplement the consultative process. This can be accomplished through the following:

- A brainstorming session
- An anonymous suggestion box approach
- Appointing a working party to represent the needs of the domain experts, and involving them in the project process

It is vitally important that if the roles aren’t clearly carved out from the start, you must help carve them out. That way, when you do receive the formal brief for the project, you’ll be able to respond to it, safe in the knowledge that what you’re responding to is, in fact, what is really required.

## What Is the History of the Project?

It is also vitally important to establish whether this project has any baggage attached to it. A fresh project is always exciting, but it may not actually be as fresh on the inside as it appears on the outside. Having a good handle on the history of the project enables you to tweak certain aspects of your approach accordingly.

Generally speaking, a project has serious baggage only if another attempt has been made to get it off the ground previously — a false start. If you know this to be the case, then you should immediately make yourself aware of the following potential baggage, no matter how long ago that previous attempt was made:

- **Departed staff** — If this project was previously handled by a member of staff who has since resigned, been fired, or been moved to other duties in the organization, beware. It is almost inevitable that the client considers the former staff member to have failed in his or her appointed task. The trick here is to gain a good idea of the strengths and weaknesses of the new representative that the client puts forward to work with you. This is addressed a bit more later in this chapter.
- **Departed supplier** — If you are undertaking the project as a replacement for another supplier (either commercial or internal), it is worth sizing up the reasons why the client dropped that supplier in the first place; or, indeed, why the supplier dropped the client — it does happen from time to time. If necessary, dig around with other former clients of that supplier to examine their experiences, and shape your approach according to any useful information you acquire. The client will want to trust you from the outset, so give him or her good reason to do so.
- **Difficulties working with in-house staff** — If a project has been outsourced by a company to you, you may experience difficulties working with the client company’s IT department. Sometimes this situation can arise even when no attempt to start the project has ever been made internally, but there has been an expectation that one should have been made. The best advice is to get that IT department involved from the start. Give that department a call while you’re writing the technical specification — it will be caught well and truly off guard and may even prove to be a great help as a result.
