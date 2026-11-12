errands) into three separate smaller processes (bank, grocery store, recycling). Each smaller process has its own steps. You can write a program for this like so:

```
sub Bank {
    print "Driving to the bank...\n";
    print "Depositing a million dollars!\n";
    print "Leaving the bank.\n";
}
```

```
sub GroceryStore {
    print "Driving to the grocery store...\n";
    print "Buying apples!\n";
    print "Buying more apples since I have millions!\n";
    print "Paying for the apples!\n";
    print "Leaving the grocery store.\n";
}
```

```
sub Recycling {
    print "Driving to the recycle plant.\n";
    print "Avoiding hitting the broken bottles.\n";
    print "Smashing bottles into bins.\n";
    print "Driving away.\n";
}
```

```
Bank();
GroceryStore();
Recycling();
print "Found more money!\n";
Bank();
GroceryStore();
```

This program defines three subroutines, Bank, GroceryStore, and Recycling. The main part of the program then calls the subroutines one by one. Then the main part prints out a message, calls the Bank subroutine a second time, and then calls the GroceryStore subroutine a second time.

You can call the subroutines whenever you need to and as often as you need to. That's the idea behind subroutines: If you have common code you need to repeat periodically, you can put it in a subroutine rather than retype it over and over.

You don't need to call the subroutines in the order in which you declare them. If you want to rearrange your errands and drop off the recycling first, then you don't need to rearrange the order of the subroutines — only the code that calls the subroutines.