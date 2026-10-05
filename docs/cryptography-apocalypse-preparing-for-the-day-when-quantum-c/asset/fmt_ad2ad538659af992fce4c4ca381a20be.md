
The Mosca Inequality theorem says you should start working on your post-quantum migration 12 years ahead of the quantum crypto break if you want to keep your data securely protected for the entire 7 years, with 5 years of migration included. Essentially, if you haven't started your preparation with enough lead time, there is a good chance that you are already behind on getting started on your quantum resistance project.

## Key Off Post-Quantum Cryptography Standard Selections

For most organizations, moving to quantum-resistant cryptography will ultimately need to key off their respective nation-state's official selections of post-quantum cryptography. Few organizations will benefit by picking a nonstandard cryptographic standard to implement across their production environment ahead of an official national standard. An organization can pick a nonstandard cipher or scheme to work with in a production environment, but doing so usually requires a large amount of independent justification. Nonstandard ciphers and schemes are usually less tested and trusted, even if they seem or are actually stronger and more secure. For picking cryptography to standardize on, there is safety in numbers and in waiting for a standard to be picked.

> **NOTE**  For example, for a few years early on, elliptic curve isogeny cryptography was thought to be quantum-resistant. But then someone discovered a way to quickly factor the involved isogenic curves. A “fix,” one involving using only supersingular elliptic curves, defeated that particular attack, and now elliptic curve isogeny cryptography is known as supersingular elliptic curve isogeny cryptography. But someone could come up with a new attack that breaks even supersingular elliptic curves isogeny math. Most quantum-resistant cryptography is very new. Ciphers and schemes are still being attacked and tested. Pick a solution too soon and you increase the risk of picking a faulty cryptographic solution and having to do rework.

In the United States and much of the world, this means needing to wait for NIST to announce their post-quantum cryptographic standards, which they currently say should be between 2022 and 2024. NIST has also stated that they may make selections earlier if new information forces an accelerated timeline. This means that most organizations will have to wait until 2022 to 2024 before beginning large-scale migrations to quantum-resistant cryptography. And a complete move will likely take one to two years (at best) after the post-quantum cryptographic standards are selected as all impacted vendors begin to migrate their hardware and software offerings. There will be a natural delay between the time the cryptographic standards are selected and when they become widely available.

You can—and should—begin to experiment, test, and develop around any likely post-quantum cryptographic standards. That can only benefit your organization for when the appropriate time for full production deployment occurs. But I caution any normal organization against going to full production deployment with any nonstandard post-quantum cryptography ahead of the official selection. In the same vein, doing nothing until the official selections are made isn't optimal either. Each company needs to start investigating, planning, and protecting critical data now, and some organizations should also begin test developing in order to appropriately prepare.

## Create an Emergency Accelerated Timeline Scenario

It is essential that you create a backup, emergency accelerated timeline for a scenario where the quantum break suddenly happens before you've fully moved your organization's assets to quantum-resistant cryptography. Imagine, tomorrow you wake up and the NSA announces that not only has a foreign government obtained the ability to break traditional public key crypto, but the NSA has also been detecting such attacks against companies. Instead of years to get moved to quantum-resistant crypto, you need to move now. How does that change your plan? What do you drop? What counts as a critical asset to move now and what doesn't? Can you get more resources to accomplish the project phases faster? Do you have to alert customers and the board of directors to the new imminent threat? Where is the funding going to come from? Create two timelines: one for what you think is the hoped-for, expected, normal timeline of events and one for an emergency accelerated timeline. Plan for both outcomes.

## Create Project Phase Timeline Estimates

How long will it take you to complete the entire quantum-resistance migration project? Estimate how long it will take your organization to move all involved data protection systems to post-quantum implementations once you start your quantum-resistant project so that senior management and project members can see likely expectations. The answer is unique for every organization and depends on what you have to move, how, and when you are able to move them. Every organization will be different, but project leaders should start with some basic guesses for each phase of the project. For example, see [Table 9.1](#c09.xhtml#c09-tbl-0001).

[**Table 9.1**](#c09.xhtml#R_c09-tbl-0001)**:** Example quantum-resistant project tasks and timelines

| Project steps || Estimated time to complete |
| --- | --- |
| Educate. || 1 month |
| --- | --- |
| Form a project team and plan. || 1 month |
| Create a timeline. || 1 month |
| Take a data protection inventory. || 3 months |
| Analyze the quantum plan and make recommendations. || 6 months |
| Prevent future data leaks. || 3 months |
| Strengthen existing traditional cryptography. || 12 months |
| Move to quantum-resistant cryptography. || 60 months |
| Move to quantum-hybrid technologies. || 60 months |
| Go fully quantum. || Undetermined at this time |

By assigning some general numbers to these tasks, you can come up with a rough estimate of time needed for the post-quantum migration project and inform all stakeholders of the tasks and timings. Some tasks, such as education, forming a project team and planning, and creating a timeline can be accomplished simultaneously. With the example numbers listed in [Table 9.1](#c09.xhtml#c09-tbl-0001), the actual project work would take six to seven years, with most of that belonging to the “Move to quantum-resistant cryptography” phase. Of course, the move to quantum-resistant cryptography and ultimately quantum-based cryptography depends on factors beyond your control.

By appropriately planning for all phases, including the post-quantum cryptographic migration, even if a faster, accelerated move to quantum-resistant cryptography is needed than you originally planned, your organization can be better prepared for the move. Proper planning saves time. Even quantum mechanics doesn't change that.

### Step 3: Collect Data

Critical to any quantum-resistant cryptographic migration project is to do a complete data protection inventory. It should include five components:

* Locating all sensitive data and devices
* Identifying data and device stakeholders
* Performing confidentiality ranking
* Determining how long the data or devices need to be protected from unauthorized eavesdropping
* Identifying current data protection systems involved with protecting devices that use cryptography, particularly identifying involved cryptography and key sizes

The inventory should include a thorough accounting of all sensitive data and devices that you need to prevent from unauthorized disclosure. There is a saying in computer security: “If you think you know where all your data is, you're mistaken or lying to yourself.” With that said, you need to do the best accounting of where all sensitive data and devices are located, along with the stakeholders who own, safeguard, and rely on the information and devices. Stakeholders are needed to ascertain all the other needed information.
