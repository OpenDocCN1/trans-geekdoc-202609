My solution, as shown in Figure 1.29, is 5.

| Item | Calories | How Many? |
| :--- | :--- | :--- |
| Beer | 200 | 0 |
| Bottled Water | 0 | 0 |
| Chocolate Bar | 255 | 0 |
| Chocolate Dipped Cone | 300 | 0 |
| Gummy Bears | 300 | 0 |
| Hamburger | 320 | 0 |
| Hot Dog | 265 | 0 |
| Ice Cream Sandwich | 240 | 0 |
| Licorice Rope | 280 | 1 |
| Nachos | 560 | 2 |
| Pizza | 480 | 0 |
| Popcorn | 500 | 2 |
| Popsicle | 150 | 0 |
| Soda | 120 | 0 |
| Total Items: | 5 | =SUM(C2:C15) |
| Total Calories: | 2400 | =SUMPRODUCT(B2:B15;C2:C15) |

# Figure 1.29: An optimized item selection

In this chapter, you learned a lot. First, we reviewed how to use Excel's status bar to quickly retrieve descriptive statistics. Next, you learned how to create Excel tables, which will allow you to stay organized. After this, we reviewed important LOOKUP functions and using dynamic array formulas. We reviewed PivotTables and how and when to bust out Solver.

Before ending this chapter, you should know that huge models don't fit very well in Excel. The version of Solver that comes packaged with Excel allows only 100 – 200 decision variables and constraints, depending on the version you're running. That's going to limit the size of the problems you can attack in this book.

If you want to go larger in Excel, you can buy a bigger version of Solver from Frontline Systems. Even better, use OpenSolver just as you'll do in the later sections of this chapter. Go to (www.coin-or.org) to download it. For some parts of this book, you're going to stick with Excel and Solver, for others you'll need to use OpenSolver. Don't worry, both tools vibe well together: you can set up your problem in Solver and then run it with OpenSolver. You'll see how in the chapters that follow.

# NONLINEARITY CHECKS IN OPENSOLVER

OpenSolver will protest if it detects non linearity. We'll talk about non linearity as we go through this book. But I want to mention this warning now at the start of the book so you'll know what to do.

Non linearity won't be an issues for us, as we will be working with non linear problems. But that doesn't mean we want to get a warning each time it's detected. It's annoying, so let's fix it.