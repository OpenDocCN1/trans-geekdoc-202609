
## Chapter 3
### Developing a Web Database Application
### In This Chapter
- Planning your application
- Selecting and organizing your data
- Designing your database
- Overview of building your database
- Overview of writing your application programs

Developing a Web database application involves more than just storing data in MySQL databases and typing in PHP programs. Development has to start with planning. Building the application pieces comes after planning. The development steps are
- 1. Develop a plan, listing the tasks that your application will perform.
- 2. Design the database needed to support your application tasks.
- 3. Build the MySQL database, based on the database design.
- 4. Write the PHP programs that perform the application tasks.

I discuss these steps in detail in this chapter.

## Planning Your Web Database Application

Before you ever put finger to keyboard to write a PHP program, you need to plan your Web database application. This is possibly the most important step in developing your application. It’s painful to discover, especially just after you finish the last program for your application, that you left something out and have to start over from the beginning. It's also hard on your computer (and your foot) when you take out your frustrations by drop-kicking it across the room.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_58_0.png)

Good planning prevents such painful backtracking. In addition, it keeps you focused on the functionality of your application, thus preventing you from writing pieces for the application that do really cool things but turn out to have no real purpose in the finished application. And if more than one person is working on your application, planning ensures that all the pieces will fit together in the end.

### Identifying what you want from the application

The first step in the planning phase is to identify exactly why you're developing your application and what you want from it. For example, your main purpose might be to
- Collect names and addresses from users so that you can develop a customer list.
- Deliver information about your products to users, as in a customer catalog.
- Sell products online.
- Provide technical support to people who already own your product.

After you clearly identify the general purpose of your application, make a list of exactly what you want that application to do. For instance, if your goal is to develop a database of customer names and addresses for marketing purposes, the application's list of required tasks is fairly short:
- Provide a form for customers to fill out.
- Store the customer information in a database.

If your goal is to sell products online, the list is a little longer:
- Provide information about your products to the customer.
- Motivate the customer to buy the product.
- Provide a way for the customer to order the product online.
- Provide a method for the customer to pay for the product online.
- Validate the payment so you know that you'll actually get the money.
- Send the order to whomever is responsible for filling it and sending the product to the customer.

At this point in the planning process, the tasks that you want your application to perform are still pretty general. You can accomplish each of these tasks in many different ways. So now you need to examine the tasks closely and detail exactly how the application will accomplish them. For instance, if your goal is to sell products online, you might expand the previous list like this:

### Provide information about products to the customer.
- Display a list of product categories. Each category is a link.
- When the customer clicks a category link, the list of products in that category is displayed. Each product name is a link.
- When a customer clicks a product link, the description of the product is displayed.

### Motivate the customer to buy the product.
- Provide well-written descriptions of the products that communicate their obviously superior qualities.
- Use flattering pictures of the products.
- Make color product brochures available online.
- Offer quantity discounts.

### Provide a way for customers to order the product online.
- Provide a button that customers can click to indicate their intention to buy the product.
- Provide a form that collects necessary information about the product the customer is ordering, such as size, color, and so on.
- Compute and display the total cost for all items in the order.
- Compute and display the shipping costs.
- Compute and display the sales tax.
- Provide forms for customers to enter shipping and billing addresses.

### Provide a method for customers to pay for the product online.
- Provide a button that customers can click to pay with a credit card.
- Display a form that collects customers’ credit card information.

### Validate the payment so you know that you’ll actually get the money.
The usual method is to send the customer’s credit card information to a credit card processing service.

### Send the order to whoever is responsible for filling it and sending the product to the customer.
E-mailing order information to the shipping department should do it.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_60_0.png)

At this point, you should have a pretty clear idea of what you want from your Web database application. However, this doesn't mean that your goals can't change. (In fact, your goals are very likely to change as you develop your Web database application and discover new possibilities.) At the onset of the project, start with as comprehensive of a plan as possible to keep you focused so that you avoid running into a dead end or getting sidetracked.

## Taking the user into consideration

Identifying what you want your Web database application to do is only one aspect of planning. You must also consider what your users will want from it. For example, say your goal is to gather a list of customer names and addresses for marketing purposes. Will customers be willing to give up that information?

Your application needs to fulfill a purpose for the users as well as for yourself. Otherwise, they'll just ignore it. Before users will be willing to give you their names and addresses, for example, they need to perceive that they will benefit in some way from giving you this information. Here are a few examples of why users might be willing to register their names and addresses at your site:
- **To receive a newsletter:** To be perceived as valuable, the newsletter should cover an industry related to your products. It should offer news and spot trends — and not just serve as marketing material about your products.
- **To enter a sweepstakes for a nice prize:** Who can turn down a chance to win an all-expense-paid vacation to Hawaii or a brand-new SUV?
- **To receive special discounts:** For example, you can periodically e-mail special discount opportunities to customers.
- **To be notified about new products or product upgrades when they become available:** For example, customers might be interested in being notified when a software update is available for downloading.
- **To get access to valuable information:** For instance, you must register at *The New York Times* Web site in order to gain access to its articles online.

Now add the customer tasks to your list of tasks that you want the application to perform. For example, consider this list of tasks that you identified for setting up an online retailer:
- Provide a form for customers to fill out.
- Store the customer information in a database.

## Leaving room for expansion

One certainty about your Web application is that it will change over time. Down the line, you might think of new functions for it or just simply want to change something about it. Or maybe Web site software improves so that your Web application can do things that it couldn’t do when you first put it up. Whatever the reason, your Web site will change. When you plan your application, you need to keep future changes in mind.

You can design your application in steps, taking planned change into account. You can develop a plan in which you build an application today that meets your most immediate needs and make it available as soon as it’s ready. Your plan can include adding functions to the application as quickly as you can develop them. For example, you can build a product catalog and publish it on your Web site as soon as it’s ready. You can then begin work on an online ordering function for the Web site, which you will add when it’s ready.

![](img/d82df0828cfbc6d6be1e9a991861f3b7_62_0.png)

You can’t necessarily foresee all the functions that you might want in your application in the future. For instance, you might design your travel Web site with sections for all possible destinations today, but the future could surprise you. Trips to Mars? Alpha Centauri? An alternate universe? Plan your application with the flexibility needed to add functionality in the future.

## Writing it down

Write your plan down. You will hear this often from me. I speak from the painful experience of not writing it down. When you develop your plan, it’s foremost in your mind and perfectly clear. But in a few short weeks, you will be astonished to discover that it has gone absolutely hazy while your attention was on other pressing issues. Or you want to make some changes in the application a year from now and won’t remember exactly how the application was designed. Or you’re working with a partner to develop an application and you discover that your partner misunderstood your verbal explanation and developed functions for the application that don’t fit in your plan. You can avoid these types of problems by writing everything down.

## Presenting the Two Running Examples in This Book

In the next two sections, I introduce the two example Web database applications that I created for this book. I refer to these examples throughout the book to demonstrate aspects of application design and development.
