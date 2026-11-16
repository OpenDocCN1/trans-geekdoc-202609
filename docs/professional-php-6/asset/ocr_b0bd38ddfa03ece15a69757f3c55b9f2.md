One other consideration is constraining certain instruments from being added to composites. Perhaps you don't want to allow a `Guitar` object to be added to a `DrumSet`. In that case, you could define certain legal types based on the `category` attribute for subject-verb agreement: Implementing any or all of these features would be worthwhile to try on your own.

# # The Observer Pattern

Often, you'll have data in your application that changes over time. For example, suppose you have some GUI components that are required to show this data and then update the data when it changes. How would you handle it? One solution might be to pass the newly updated data to a method of the GUI component so that it could redraw the information. A problem with this approach is remembering to do that each time the data is updated. What if it's not clear how often the data will be updated, and whether you want the GUI to update automatically when it does?

The observer pattern solves this problem by using two interfaces: `Observer` and `Observable`. As the name suggests, the `Observer` “watches” the `Observable` to see whether it changes.

*Keeping the theme of human senses, an `Observer` is sometimes called a `Listener`, but for this chapter, we’ll stick with the former name.*

In its most basic implementation, the `Observable` can add `Observers`. `Observable` is then responsible for notifying them if anything about its state has changed, and the `Observer` is responsible for reacting to the change. In this example, the data is the `Observable` and the GUI components are the `Observers`. If the data changes, those changes will automatically be reflected in any GUI component that is an `Observer` of the data. Figure 4-7 demonstrates the observer pattern.

![](bbox=[0.27, 0.555, 0.79, 0.825])

Figure 4-7: Observer pattern