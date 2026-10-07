# 16 Chapter 1 Getting Started

We need to ascertain if one of the addresses is a payment address. In the vast majority of transactions that are one-to-many or many-to-many addresses, one of the outputs is a change address. The reason is that each Bitcoin is made up of 100 million satoshis, so the chances that several addresses will add up to exactly the input amount is tiny. In this example, the payment is from a "3" wallet. Bitcoin addresses that start with the number 3 are used for multisignature or more complex transactions than a straight address-to-address payment. The outputs are to a 3 and to a 1. It is significantly more likely that the change address is also a 3 and the 1 is the payment. Hence we can infer that the 3 is the change and the 1 is the payment.

Other techniques exist for discerning which address is the change address. For example, in Figure 1.6 any of the 3 inputs would have paid for the 3Hffw payment, but all three are needed for change to 3B5KC. This helps us conclude that the change address is the 3Hffw and hence we need to find the other one.

![](bbox=[0.137, 0.403, 0.822, 0.483])

Figure 1.6

Once we have discovered the address or addresses that are likely payments, we can follow them to the next transaction by clicking the Spent button. In this example, both outputs are Unspent so we are at a dead end.

Clicking to the next or previous transaction will provide another list of inputs and outputs, and the investigator can get lost immediately. I recommend stopping after each and researching the addresses, and build the picture before moving again. Once you have moved to two transactions from your start point, experience shows that you are often beyond the scope of the investigation. Unless your suspect is using mixers and tumblers to split the coins, it is extremely hard to follow without the help of a commercial tool, then payments of interest tend to be within just a few transactions of your start point.

I worked on numerous transactions where this is true. There is even a counter terrorism investigation where people donating to the "cause" were just buying from exchanges and donating straight to the cause, and then the monies were cashed out in one or two hops to another exchange. You could draw the entire transaction graph on a small piece of paper.

Of course, there are also times when criminals are extremely sophicated and will go to extraordinary lengths to obfuscate their eventual destination through