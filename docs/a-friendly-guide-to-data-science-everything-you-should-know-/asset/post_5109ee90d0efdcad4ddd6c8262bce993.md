
## CHAPTER 8 KEEPING EVERYONE SAFE: DATA SECURITY AND PRIVACY

Monitoring is also important and involves both real-time and scheduled monitoring of networks, database and software access and use, and physical site access logs, and anything out of the ordinary should be automatically flagged and raise an alert. Audits of everything, including plans, should be done regularly to make sure things aren't slipping through the cracks.

It's important to be able to recover in case something bad happen. Data backups are copies of all critical data so that if data is lost because of a security failure or even just a storage failure, it can be recovered. These backups are usually taken on a daily basis and may even still physical tapes that are deposited in a different location every day, so going back to the backups will involve a loss of data, but it's designed to not be catastrophic.

Planning and policies are also important. Policies and plans should be in place to define how the data is managed, backup schedules and plans, and how it's decided which users should have access to what. Risk assessments should be done and included in plans.

Finally, some of the most obvious methods of data security relate specifically to how the data is stored and moved around. Encryption is a method of modifying data without code so that it's not usable if accessed in place or intercepted in flight without the decryption key. Data can also be modified in some way to protect fields or rows.

A common data modification technique is masking, where the real values are replaced by different, meaningless values. The simplest approach is just to null out the real values—leave them blank, basically. Generally, the general form of the data would be maintained. The most basic is replacement masking, where each character or digit is replaced with the same value, so a Social Security number would show XXX-XX-XXXX in every row. There are a few other types of masking. With scrambling, the values are simply reordered, so a Social Security number 123-45-6789 might end up 831-96-2457. In shuffling, a real value from the same column but a different row in the table would be used. With substitution, a fake but realistic value would be used, where someone’s first and last names could be replaced with random first and last names. Sometimes encryption is also used here for specific fields or rows that are particularly sensitive.

Note marking and other modifications might happen in place—the data could be permanently changed—but normally a new table would be created that shows everything's in the original with the modifications in place in the new table only. There would be very few people with access to the original table, and most people would only be to see the new one. Other times the changes could be applied at the display point based on the viewer's access privileges, rather than actually physically in a table. For instance, one viewer with higher privileges might see what's in the column in the really table using the company's data viewer, but another viewer might see scrambled data in the same column. Different database systems allow different types of control.

The particular type of masking is going to depend on the situation. For example, it is common for companies to have “prod” (production or real) data and “dev” (development) data that’s like prod but is not complete or exactly the same. As mentioned in Chapter 7, dev data is crucial for report development. When they’re developing, report builders only being pushed to prod when they’re complete. While they’re developing, report builders generally don’t need the full, accurate data, but they need the data to behave and look like data in prod. If the report is going to show and do operations on salaries, they need values in the salary column to behave properly in drop-down boxes or numeric filter boxes so they can test those things are functioning correctly, but they don’t care if the actual values are “right.” It’s typical for report builders to not even see the report with real values until they put it into production. Appropriate masking makes the process seamless.

In other cases, data scientists may be using similar data, but they will need core fields unmasked. But usually data scientists don’t need personal information like people names, addresses, and so on, one can easily be masked. Different users need different levels of access.

## Data Privacy

As mentioned above, data privacy can be mostly considered a subset of data security, and most of the efforts to ensure data privacy mirror those used to ensure security of data in general.

## Privacy as a Human Right

One thing that stands out about privacy is how human-focused it is. Most human-focused entities regard privacy as a human right. The United Nations includes the following as Article 12 of their Declaration of Human Rights: “No one shall be subjected to arbitrary interference with his privacy, family, home or correspondence, nor to attacks upon his honour and reputation. Everyone has the right to the protection of the law against such interference or attacks.”

This is in line with how people feel. Generally, people think they should have control over who knows about them, although social media has shifted a lot. Younger people are more comfortable with being known about them and aren’t protective over their personal information as older people. Still, when it comes down to their personal information being used in a way that harms them, even if it’s only in a small way, people realize maybe they do want to know who has their data.

Historically, with their emphasis on profits, most companies have not shared this view as the data revolution has gotten underway. They’re motivated to know as much as possible about their customers, and many have been collecting unchecked for years. But people are becoming aware of what their rights should be, and many are starting to change. Governments are responding to the shift in perspective with new laws⁴Universal Declaration of Human Rights” by the United Nations, Article 12, https://www.un.org/en/about-us/universal-declaration-of-human-rights#:text=Article%20120, with the European Union's General Data Protection Regulation (GDPR), the California Consumer Privacy Act (CCPA), and the California Privacy Rights Act (CPRA) leading the way. These will be discussed more below.

## Types of Data Relevant to Privacy

Because privacy pertains mostly to people, we often refer to personal data, any kind of data that represents people in some way. It's generally considered the most potentially sensitive, across the board. This would
