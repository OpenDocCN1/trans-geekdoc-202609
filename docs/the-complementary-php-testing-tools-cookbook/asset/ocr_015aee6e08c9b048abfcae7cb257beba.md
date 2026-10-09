# # Chapter 3

# ## Mutation Testing

# ### What Is It?

Have you ever wondered if there was a way to test the tests you’ve been writing? That is essentially what mutation testing is.

My preferred tool for doing mutation testing in PHP is Infection $^{[1]}$, and it defines mutation testing as:

> Mutation testing involves modifying a program in small ways. Each mutated version is called a Mutant. To assess the quality of a given test set, these mutants are executed against the input test set to see if the seeded faults can be detected. If mutated program produces failing tests, this is called a killed mutant. If tests are green with mutated code, then we have an escaped mutant.

In the case of Infection, it works together with PHPUnit to make informed random changes to the code, and then execute the test.

$^{[1]}$ [https://infection.github.io](https://infection.github.io)