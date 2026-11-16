+   - [ ] Changing the week should bring up a previously saved week: 1 point
+   - [ ] In the Customer Contact screen, also track number of shop calls, number of engineer calls, number of distributor calls, approximate mileage, territory worked, and territory comments on a per week basis: 1 point
+   - [ ] Configure the number of contacts, which may occasionally change: 1/2 point

The original plan was as follows:

+   - [ ] Story 9: Authentication and Authorization, 4 points (done)
+   - [ ] Story 1: Customer Contact Report, 3 points (mostly done)
+   - [ ] Story 6: Sales Manager Notification, 3 points
+   - [ ] Story 8: Mail Room Notification, 2 points

Considering that the half-pointers don't really count but the new ones do, you discuss it with your clients and determine that they'd prefer it in this order:

+   - [ ] Story 9: Authentication and Authorization, 4 points (done)
+   - [ ] Story 1: Customer Contact Report, 3 points (mostly done)
+   - [ ] Story 14: Changing the week recalls a previous week: (new)
+   - [ ] Story 15: Per-week items on the customer contact report: (new)

They'd also prefer to get the spreadsheet in the next iteration before requiring the notifications, so these can be dropped for now:

+   - [ ] Story 6: Sales Manager Notification, 3 points
+   - [ ] Story 8: Mail Room Notification, 2 points

Back to work.

# # Cleaning Up

Before taking off and completing your new stories, consider the state of your current corps of code. Yes, some bits are a bit ugly, but it's completely functional. Some bits are obviously copied and pasted from other places, but it works. It does, however, include a great testing suite.

Don't kick yourself for a few warts on a fully tested, working product. It happens, and it's called code debt. Just as in real life, when you're in a hurry or circumstances require, you can go beyond your means monetarily by going into debt.

Now that you have a bit of time to clean things up, it's time to work off the debt. It's easy, although it's best if you follow good development guidelines as you code in order to be as productive as you can without going into debt.