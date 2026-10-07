have this macro level of integrity.

# Write Less Code

There have been studies that have researched the number of bugs I can expect to have in my software. The industry average is around 15 to 50 bugs per 1000 lines of code. One simple way to reduce the number of bugs, and increase the integrity of my software, is to write less code.

Bjarne Stroustrup stated that writing more code than I need results in Ugly, Large and Slow code:

+   - Ugly: Leaves places for bugs to hide.
- Large: Ensures complete tests.
- Slow: Encourages the use of shortcuts and dirty tricks.

# Error Handling

When error handling is treated as an exception and not part of the main code path, I can expect the majority of my critical failures to be due to error handling.

There was a study that looked at a couple hundred bugs in Cassandra, HBase, HDFS, MapReduce, and Redis. The study identified 48 critical failures that fell into these categories.

+   - 92%: Failures from bad error handling
  - 35%: Incorrect handling
    - 25%: Simply ignoring an error
    - 8%: Catching the wrong exception
    - 2%: Incomplete TODOS
  - 57%: System specific
    - 23%: Easily detectable
    - 34%: Complex bugs
- 8%: Failures from latent human errors

# Quotes

+   - "Failure is expected, failure is not an odd case. Design systems that help you identify failure. Design systems that can recover from failure." - JBD

+   - "Product excellence is the difference between something that only works under certain conditions, and something that only breaks under certain conditions." - Kelsey Hightower

+   - "Instability is a drag on innovation." - Yehudah Katz