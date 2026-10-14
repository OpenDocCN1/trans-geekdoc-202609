
But what about the last two rows?

![image](/path.to.Images/image00484.jpeg) We are stating that p implies q; however, in row three we see q is true but p is not. Therefore not p implied q, so our statement that p implies q is not true.

![image](/path.to.Images/image00484.jpeg) In the fourth row, if have not p and not q, then p implies q is still true. Nothing in p being false and q being false invalidates our statement that p implies q.

**Tip**

Several sources can help you learn more about mathematical logic. A good one is the book `Math Proofs Demystified` by Stan Gibilisco (McGraw-Hill Education, 2005).

### Combinatorics

*Combinatorics* is exactly what the name suggests: it is the mathematics behind how you can combine various sets. Combinatorics answers questions such as, how many different ways can you choose from four colors to paint six rooms? How many different ways can you arrange four flower pots?

As you can probably surmise, combinatorics, at least in crude form, is very old. Greek historian Plutarch mentions combinatorial problems, though he did not use the language of mathematics we use today. The Indian mathematician Mahavira, in the ninth century, actually provided specific formulas for working with combinations and permutations. It is not clear if he invented them or simply documented what he had learned from other mathematicians.

Combinatorics are used to address general problems, including the *existence problem* that asks if a specific arrangement of objects exists. The *counting problem* is concerned with finding the various possible arrangements of objects according to some requirements. The *optimization problem* is concerned with finding the most efficient arrangements.

Let’s begin our discussion with a simple combinatorics problem. Assume that you are reading this textbook as part of a university course in cryptography. Let’s also assume that your class has 30 students, and of those students, 15 are computer science majors and 15 are majoring in something else—we will call these “other.”

It should be obvious that there are 15 ways you can choose a computer science major from the class and 15 ways you can choose an other major. This gives you 15 × 15 ways of choosing a student from the class. But what if you need to choose one student who is either a computer science major *or* an other? This gives you 15 + 15 ways of choosing one student. You may be wondering why one method used multiplication and the other used addition. The first two rules you will learn about in combinatorics are the *multiplication rule* and the *addition rule*:

![image](/path.to.Images/image00484.jpeg) **The multiplication rule** Assume a sequence of r events that you will call the events E1, E2, and so on. There are n ways in which a specific event can occur. The number of ways an event occurs does not depend on the previous event. This means you must multiply the possible events. In our example, the event was selecting one of the students, regardless of major. So you might select one from computer science or you might select one from other. The multiplication rule is sometimes called the *rule of sequential counting*.

![image](/path.to.Images/image00484.jpeg) **The addition rule** Now suppose there are r events E1, E2, and so on, such that there are n possible outcomes for a given event, but further assume that no two events can occur simultaneously. This means you will use the addition rule, also sometimes called the *rule of disjunctive counting*. The reason for this name is that the addition rule states that if set A and set B are disjoint sets, then addition is used.

I find that when a topic is new to a person, it is often helpful to view multiple examples to fully come to terms with the subject matter. Let’s look at a few more examples of selecting from groups, illustrating both the addition rule (sometimes called the *sum rule*) and the multiplication rule (sometimes called the *product rule*).

What happens when you need to pick from various groups? Assume you are about to take a trip and you want to bring some along reading material. You have 5 history books, 3 novels, and 3 biographies. You need to select 1 book from each category. There are 5 different ways to pick a history book, 3 different ways to select a novel, and 3 different ways to choose a biography. The total possible combinations is 5 + 3 + 3. Why was addition used here? Because each choice can only be made once. You have 5 historical books to choose from, but once you have chosen 1, you cannot select any more. Now you have 3 novels to choose from, but once you have chosen 1, you cannot select any more.

Now let’s look at an example where we use the multiplication or product rule. Assume you have 3 rooms to paint and 4 colors of paint. For each room, you can use any of the 4 colors regardless of whether it has been used before. So you have 4 × 4 × 4 possible choices. Why use multiplication rather than addition? Because each choice can be repeated. Assume your 4 colors are green, blue, yellow, and red. You can use green for all 3 rooms if you want, or green for 1 room only, or not use green at all.

The multiplication rule gets modified if selection removes a choice. Supposed that once you have selected a color, you cannot use it again. In the first room you have 4 colors to select from, but in the next room only 3, and in the third room only 2 colors. So the number of possible combinations is 4 × 3 × 2.

Selection with removal is actually pretty common. Here’s another example: Assume you want to line up 5 people for a picture. It should be obvious that you cannot reuse a person. Once you have lined up the 5 people, no more people are available for selection. So your possible combinations are 5 × 4 × 3 × 2 × 1.

### Permutations

*Permutations* are ordered arrangements of things. Because order is taken into consideration, permutations that contain the same elements but in different orders are considered to be distinct. When a permutation contains only some of the elements in a given set, it is called an *r-permutation*. What this means for combinatorics is that the order of the elements in the set matters. Consider the set {a, b, c}. There are six ways to combine this set, if order matters:

![image](/path.to.Images/image00484.jpeg) a b c

![image](/path.to.Images/image00484.jpeg) a c b

![image](/path.to.Images/image00484.jpeg) b a c

![image](/path.to.Images/image00484.jpeg) b c a

![image](/path.to.Images/image00484.jpeg) c a b

![image](/path.to.Images/image00484.jpeg) c b a

Add one more letter to the set, {a, b, c, d}, and there are 24 possible combinations:

![Images](/path.to.Images/image00583.jpeg)

Fortunately, you don’t have to write out the possibilities each time to determine how many combinations of a given permutation there are. The answer is “n!”. For those not familiar with the n! symbol, it is the factorial symbol. The n! means n × n – 1 × n – 2 × n – 3, and so on. For example 4! is 4 × 3 × 2 × 1.

Consider ordering a subset of a collection of objects. If there is a collection of n objects to choose from, and you are selecting r of the objects, where 0 < r < n, then you call each possible selection an *r-permutation* from the collection. What if you have a set of three letters {a, b, c} and you want to select two letters. In other words, you want to select an r-permutation from the collection of letters. How many r-permutations are possible? Six:

![Images](/path.to.Images/image00584.jpeg)

What if our original collection was four letters {a, b, c, d} and you wanted to select a two-letter r-permutation? You would have 12 possibilities:

![Images](/path.to.Images/image00585.jpeg)

These examples should illustrate that the number of r-permutations of a set of n objects is n!/(n – r)!
