# SUPPRESSING THE NAVIGATION BAR

As always, before you start coding, you should spell out exactly what it is you are trying to accomplish. You want to show the Recordset Navigation Bar, which is stored in a table, if the number of tours displayed on the page is greater than five (that is, six or more). Remember the page is set to show only five records at a time. However, if there are five or fewer, then the Recordset Navigation Bar can’t be activated, and so you don’t want it to appear.

As usual, the ASP, ColdFusion, and PHP code are different, but they all use the same concept.

+   **1) Still in tours_detail.asp, using split view and the tag selector, select the table containing the Recordset Navigation Bar.**

You have selected the entire table in both design and code views. You’ll need to work in code view in the next step, but you have to isolate the table, because you’ll need to add code above and below it to cause it to show conditionally. Here is a case where split view simplifies finding an element buried in code.

Or as an option, you can add a few extra lines of white space above and below the table to help set it off.

![](bbox=[0.285, 0.485, 0.94, 0.87])