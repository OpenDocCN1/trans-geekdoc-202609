are faster than instantiated object methods. However, converting all objects into static classes and static methods would be a fool's errand; it violates the tenets of object-oriented development and introduces a testing and maintenance nightmare for whomever comes after. Similarly, there is evidence that language constructs like `isset()` run faster than functions like `array_key_exists()`. However, if `array_key_exists()` is the appropriate tool for the job, by all means use it.

Finally, developers should avoid optimizations that do not actually solve their issue. Sometimes, code cannot be optimized. Sometimes the “optimization” is worse than the original implementation. Sometimes there is a big ugly method in the middle of a class and there is nothing a developer can do to fix it. Simply put, sometimes the optimization is worse than the bottleneck, and in those cases, it should be avoided.

# When Not to Optimize

So when should a developer optimize, and when should a developer consider other alternatives? There are four cases when a developer should consider alternatives to optimization.

Do not optimize when the issue is performance. Optimization is a fantastic tool, but is unlikely to solve every single performance issue a developer encounters. Instead, developers who experience performance problems should implement solutions that improve performance considerably, rather than the bit by bit that optimization promises.

Too often developers think that all performance problems can be solved through optimization. This is not necessarily true. Developers can certainly build a well-optimized product, but at some point the traffic and load necessitates identifying and implementing performance-enhancing solutions that optimization simply cannot deliver.

Avoid optimizing when code needs heavy refactoring. Optimization should be viewed as fine tuning. Code that is in serious need of refactoring should be refactored (see Chapter 7); you should not optimize it as a solution.

This really comes down to picking the right tool for the job. If the code is a mess, has performance issues, and needs to be heavily rewritten, optimizing it will ultimately be a waste of time. It is better for the developer to refactor the code (presum-