In Java, the starting point is set to 100, so that value is displayed first. The condition is changed, as you want to repeat as long as the value is greater than 0, and also the step is changed to decrement the value instead of incrementing it. i=i-1 could be written as i--.
In Python, the range is changed to start at 100. It should stop when it reaches 1 (0 is not touched) and the step is set to -1, so the number is decremented by 1.

# Pre-condition loop

```
i = 0
loop while
......
i = i + 1
end loop
```

# General structure

![](bbox=[0.287, 0.345, 0.666, 0.583])

+   - Termination condition: a condition in a loop that interrupts or stops the repetition.
+   - Validation: a process to ensure input data is sensible or reasonable.
+   - Verification: a process to ensure input data is accurately copied from one source to another.

# Pre-condition loop flowchart

A pre-condition (WHILE) loop is used when the number of repetitions is not known prior to
the execution of the code. The code is expected to be repeated as long as a condition is met, or
it evaluates to true.
When the condition is no longer met, called termination condition, the loop execution will
stop. In a WHILE loop, the repetition might not run at all; this happens when the condition is
never met. WHILE loops are loops that are often used for validation or verification purposes.
For example, when the user is asked to enter a password twice, the computer will compare
the two entries to check if they match (double entry verification). In this case, a loop would be
used to repeat entering the password until the two inputs match.