
## 45. (D)
All three are the basic building blocks of making algorithms. Sequencing ensures that algorithms execute in order. Selection is used to determine results and some in-between steps. Iteration is used to repeat parts that need to be performed a certain number of times.

## 46. (C)
The `INPUT` commands must come first so that the values are usable, while the commands squaring the variables (`a * a` and `b * b`) must come after so that the subtraction involves the correct numbers. This makes the order 2, 4, 3, 5, 1 (with 2 and 4 interchangeable and 3 and 5 interchangeable).

(A) and (B) place `DISPLAY` before any `INPUT`.

(D) places `DISPLAY` before one of the square commands.

## 47. (B)
The computer plays the victory jingle if the two numbers are the same.

(A) and (D) would not work because `picked` and `drawing` are integers, while `AND` and `NOT` require Boolean values.

(C) would have the opposite effect of what is intended.

## 48. (C)
![Images](images/f0256-01.jpg)

## 49. (A)
The robot can only move forward and turn right. For all values the robot will not be able to travel past the one cell box. All possible landing spots are listed below.

![Images](images/f0257-01.jpg)

## 50. (D)
With such a large number of trials, the entire grid is a possible landing spot.

![Images](images/f0257-02.jpg)

## 51. (C)
Because `TRUE = TRUE`, the “OR” statement will execute as true.

![Images](images/p0258-01.jpg)

The above algorithm will result in the robot moving forward three times.

`IF(4 > 4 AND TRUE = FALSE)`

The above algorithm will execute as false, so the robot will not move.

![Images](images/p0258-02.jpg)

The above algorithm will execute as true, so the robot will move forward an additional three spaces for a total of six spaces.

![Images](images/f0258-01.jpg)

## 52. (D)
All of these are valid ways to display the given algorithm.

(A) is pseudocode (notice “is n1 < 100?”).

(B) is a flowchart containing pseudocode.

(C) is a series of “block” programming statements.

## 53. (D)
At the lowest abstraction level, a computer reads only low-level machine language, which is binary code.

(A) and (B) are not programming languages; they are merely ways to articulate a program’s content to others.

(C) needs to be placed through a compiler, which converts it into a language that has a level low enough for the computer.

## 54. (A)
High-level languages are more clear and readable, which makes them much easier to understand when reading and fixing errors in algorithms.

(B) This is untrue because low-level languages still allow for commenting (as comments are merely sections ignored by the assembler/compiler).

(C) This is incorrect because a low-level program can have its actions rearranged (though it may be harder to find alternate orders due to the language’s more procedural nature).

(D) This choice is incorrect because a low-level language is far easier to turn into machine code since it is essentially as close as humanly possible to machine code. This results in more lightweight programs.

## 55. (C)
Algorithms must execute in a reasonable time frame because that ensures that they are capable of providing answers efficiently with a data set of the necessary size.

(A) An algorithm can run forever without causing hardware damage as long as it does not overly tax the system.

(B) Compilers only check for errors in syntax and missing files, not efficiency.

(D) Efficiency has little to do with exactness. In fact, some efficient programs are efficient only because they are not exact.

## 56. (D)
An unreasonable amount of time is an exponential increase. Polynomials are acceptable.

## 57. (B)
Heuristics look only for approximate solutions, which tends to take less time than looking for exact solutions. This makes the resulting program more efficient.

(A) Heuristics are less accurate than an algorithmic solution, so this choice is incorrect.

(C) A heuristic may be somewhat harder to write when determining the bounds of acceptability, so this is not a true statement.

(D) A heuristic has no effect on the ability to copy a program.

## 58. (A)
A heuristic searches for an approximate solution. In choice (A), the algorithm approximates the content of a file based on a certain amount of data from the beginning of the file. (Scanning entire files to determine content would take longer. The heuristic approach could be fairly accurate depending on the files on which it is used.)

(B) This describes a bubble search, which is not a heuristic because it leads to the lists being fully organized.

(C) The described antivirus program is not a heuristic because the program uses the entire file rather than a portion to approximate.

(D) This is not a heuristic because the result is not approximate; the location is accurate to the bit level.

# Big Idea 3: Algorithms and Programming Part 2

## Programming
Programs can be developed for creative expression, to satisfy personal curiosity, to create new knowledge, or to solve problems (to help people, organizations, or society). Advances in computing have generated and increased creativity in other fields. For example, new computer tools are being used to track dolphins and to decode their vocalization. Understanding complex dolphin behavior would not have been possible without the ability to data mine the acoustic dolphin database (searching through large databases of information to pinpoint relevant data).

Sometimes programs that are developed for personal use can be adapted to serve a larger audience and purpose. In 2004, Mark Zuckerberg created Facebook, a local platform for Harvard students to use to connect with each other. Before adapting his program to apply to a larger audience, it totaled about 1 million users by the end of 2004. Only eight years later, that number had increased to over 1 billion active users. This widespread distribution was made possible by changes to the program in its development.

### Programs Can Be Flexible
When it was targeted to a smaller, local audience simply to satisfy Zuckerberg’s personal curiosity and enjoyment, Facebook was held to much different standards in its development. When it was made for billions of people to use, changes had to be made to accommodate so many people and to target it toward a wide market of people that might use it—making it appealing to a wider audience.

The technologies and programs that are applied to Facebook could also be applied to other fields. As well as inspiring the age of social media, the data-mining programs used to understand and process the data that are “harvested” from Facebook are the same type of programs that allow researchers to make sense of data gathered from the acoustic dolphin database.

### Programming Design Steps
The first step in programming is planning and identifying programmer and user concerns that can affect the solution. Consultation and communication with program users are important aspects of program development to solve problems.

When designing a large program, an iterative process helps with correctly coding. Checking for errors in small chunks can make isolating errors more efficient. Once a small chunk of the program is error free, it can be combined with already-checked portions of the program to help create a larger, correct program. This process of designing, implementing, testing, debugging, and maintaining programs is repeated until the entire program is ready to be released.

![Images](images/f0261-01.jpg)
