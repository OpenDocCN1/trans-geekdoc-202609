# To credit card or not?

When it comes to the credit card issue, I prefer to stay on the safe side and not risk legal troubles. Suppose one of your .php files gets messed up and one day some unsuspecting (yet unscrupulous) customer logs into your site and his browser suddenly displays a giant table listing all your customers' credit card numbers, expiration dates, and associated zip codes. (The zip codes are important for verifying authenticity.) Then suppose that customer goes on a serious shopping spree.

Or what if a hacker downloads the entire table and also goes on a shopping spree? If this happened, would you be held liable? You may say, “No way!” but the local district attorney's office may disagree and file charges nevertheless. It's best to not risk it.

I prefer not to handle credit card charges on my system and therefore not have any credit card information in my hands. If I need to charge a customer for something, I rely on a third-party credit card service that takes care of it for me. Further, if you're really serious, I suggest you talk to an attorney or an accountant or both to get the straight scoop on the legal issues of credit card processing. I'm not an attorney and can't give you advice here (or I'll lose the law license that I don't even have). You have lots of options for credit card services. I prefer to make a choice based on a recommendation — ask your associates what they're using and whether they're happy with it. For more options, you can also do a Yahoo! search on credit card services.

And here's a hotly debated topic: If the customers have to pay to post an ad (you do want to make a living), do you store the customer's credit card information here? Take a look at the sidebar “To credit card or not?” for more on this topic.

The data items you've identified become columns in your tables. Table 3-1 shows you the columns you've come up with for the Customer table and what types to assign to them.

| Table 3-1 | Columns for the Customer Table |
| --- | --- |
| Column | Type |
| ID | integer |
| Name | varchar(30) |
| E-mail address | varchar(50) |
| Sign-up date | date |
| Last access date | date |