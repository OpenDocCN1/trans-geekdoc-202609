change to the problem statement, it tends to be much easier to find the relevant parts when it is organized as a collection of small functions as opposed to a large, monolithic block.

Here is a small illustration of this point with a sample problem:

**Sample Problem** The owner of a monopolistic movie theater in a small town has complete freedom in setting ticket prices. The more he charges, the fewer people can afford tickets. The less he charges, the more it costs to run a show because attendance goes up. In a recent experiment the owner determined a relationship between the price of a ticket and average attendance.

At a price of $5.00 per ticket, 120 people attend a performance. For each 10-cent change in the ticket price, the average attendance changes by 15 people. That is, if the owner charges $5.10, some 105 people attend on the average; if the price goes down to $4.90, average attendance increases to 135. Let’s translate this idea into a mathematical formula:

avg. attendance = 120 people − $(change in price) / $0.10 · 15 people

Stop! Explain the minus sign before you proceed.

Unfortunately, the increased attendance also comes at an increased cost. Every performance comes at a fixed cost of $180 to the owner plus a variable cost of $0.04 per attendee.

The owner would like to know the exact relationship between profit and ticket price in order to maximize the profit.

While the task is clear, how to go about it is not. All we can say at this point is that several quantities depend on each other.

When we are confronted with such a situation, it is best to tease out the various dependencies, one by one:

+   1. The problem statement specifies how the number of attendees depends on the ticket price. Computing this number is clearly a separate task and thus deserves its own function definition: