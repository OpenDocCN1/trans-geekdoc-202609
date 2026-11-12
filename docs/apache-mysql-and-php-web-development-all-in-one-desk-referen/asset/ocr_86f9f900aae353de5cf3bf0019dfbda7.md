# # Chapter 3: Comparing and Testing Variables

# ## In This Chapter

+   - Testing conditions
+   - Performing actions based on conditions
+   - Making consecutive comparisons
+   - Comparing in different ways
+   - Performing comparisons together

One of the most important features in a computer language is the capability to make comparisons. For example, you may want to write out code that checks the time and writes “Good morning!” if the time is before noon, and “Good afternoon!” if the time is after noon. You can do this by making a comparison (of time and noon) and printing out the appropriate message. In this chapter, you find out how to perform comparisons and test conditions.

# ## Testing Conditions

Perl includes several constructs for testing conditions and executing blocks of code if those conditions are satisfied. Suppose you want to write a program that tests whether a username and password are correct. Take a look at this sample Perl code:

```
$username = "jeff";

if ($username eq "jeff") {
  print "Hello jeff, welcome back\n";
}
else {
  print "Who are you?? Go away! Go away!\n";
}
print "All done!\n";
```