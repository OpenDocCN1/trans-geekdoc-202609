# CHAPTER 15 NOT A CRYSTAL BALL: MACHINE LEARNING

# Types of Machine Learning

Machine learning is fundamentally different from traditional programming because of what goes in and out of a program that's been written. In most traditional programming, we write code where we know the output will be because that's what we're writing it to do. We can test every step of the way because we know the intermediate steps and what they should yield as well. Figure 15-1 shows the flow in traditional programming. The set of rules going in is the desired behavior that we write in the code, which the computer runs. Many programs will also rely on some data being inputted, anything from records to some simple configuration details. Think of the Computer box in the diagram as the software program we've written based on the rules. Running the program generates the output, the Computed Answers. In the cases with data input, we still know what the output should be for each data input or combination of data inputs, and any testing we do of the Computed Answers will be based on the known inputs and outputs. This type of software is also called deterministic, which means that every single time it runs with a specific set of inputs, the output will be exactly the same.

# Traditional Programming

![](bbox=[0.118, 0.633, 0.803, 0.713])

Figure 15-1. Traditional programming flow. Rules are required but the need for data depends on the needs of the program

An example of this kind of software is code that calculates aggregate sales values for a pizza restaurant. A programmer codes the rules for how the data should be calculated and enters the data of all the transactions