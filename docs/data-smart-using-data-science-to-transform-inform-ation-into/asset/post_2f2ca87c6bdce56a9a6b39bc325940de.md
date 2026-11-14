
Turn on Power Query and load it to Excel. If prompted where to load this data, select Table. (Depending upon your default settings, this step might be skipped and happen automatically.) This will create a new Excel table with the wrangled data (see Figure 2.10).

![](img/9c4b3d77873bec9e7da149a75c568d36_61_0.png)

Figure 2.10: Our query results. After you're finished creating your query, Power Query returns a new Excel table with the steps applied.

Take a look—the original dataset has not been changed (go ahead and verify that by clicking the Contacts tab). The Power Query editor simply captured your steps—it doesn't store the original dataset. Rather, it runs a query (that's what's saved!) on top of the original dataset.

Here's where the set-it-and-forget-it comes in. If you went to the original dataset and updated some values, added new contacts, and removed others, to run the query again, all you would need to do is click the Refresh All button on the Data ribbon tab. This will automatically update the table in Contacts-final. You don't need to go back into Power Query again unless you need to edit the query itself.1

1 Realistically, you will likely need to do this a few times. It's easy to get your data about 80 percent cleaned using Power Query. The last 20 percent can be a pain because it often includes finding weird characters and rooting out odd data wonkiness that you never expected.

Ideally, as we went through this example, you saw some cool features in Power Query and thought, I bet I could use this feature! Before going forward, go ahead and play around with Power Query a bit more to get a sense of all it can do.

However, if you're feeling a bit intimidated by Power Query, that's OK too. By the end of this book, you'll have a pretty good handle on how to use Power Query for your data wrangling needs. Here, we completed a simple data cleaning task. Of course, Power Query can do so much more. In many ways, Power Query is similar to other data science technologies that we will review by the end of the book—like the dplyr library for R, which we'll touch upon in Chapter 11, “Moving on From Spreadsheets.”

## Naïve Bayes and the Incredible Lightness of Being an Idiot

In this chapter, we're going to talk about naïve Bayes, a common data science technique often used for document classification. Naïve Bayes is used in all sorts of textual analytics including detecting spam and classifying tweets. For a model like this, you supply the training data—prelabeled examples that help a training algorithm understand what you're looking for. From there you use this information to classify new documents into the predefined categories.

You'll soon quickly learn that naïve Bayes is easy. Stupid easy, in fact. But wrapping our minds around naïve Bayes requires we understand probability and the Bayes rule. What you'll find is that once we establish rules of dependence with probability, naïve Bayes rejects these assumptions—but is oddly still very effective anyway. Let's start with a super quick intro to probability.

### The World's Fastest Intro to Probability Theory

Before we move forward, let's talk probability. Probability is the likelihood something will happen measured between 0 and 1 and often reported as a percent. When we talk about probability, we use the notation p(). For instance:

```
p(Jordan eats hot dogs) = 1 (or 100%)
p(Jordan eats ketchup) = 0.0000001
```

I love hot dogs, so of course there's a 100 percent chance I will eat them. But I don't like ketchup, and you'll never see me put it on my hot dog.

Let's see what these probabilities look like in the next section.

### Totaling Conditional Probabilities

Now, the previous two examples are simple probabilities, but what you’re going to be working with a lot in this chapter are conditional probabilities. Here’s a conditional probability:

```
p(Jordan eats ketchup | you pay him $1B) = 1
```

Although the odds of me ever eating ketchup remains low, a little cash money to the tune of a billion dollars changes things—that is, there’s a 100 percent chance I would eat ketchup if you paid me that. (I’ll take it in crypto.) That vertical bar, |, in the statement is used to separate the event from what it’s being conditioned on. We can read it as “the probability Jordan eats ketchup given you pay him $1B.”

How do you reconcile the 0.0000001 overall ketchup probability with the virtually assured conditional probability? Well, you can use the law of total probability. The total probability equals the sum of the probabilities of my eating ketchup conditioned on all possible outcomes—including the probability that it doesn’t happen. So we have this:

```
p(ketchup) = p($1B) * p(ketchup|$1B) + p(not $1B) * p(ketchup|not $1B)
= .0000001
```

The overall probability is the weighted sum of all conditional probabilities multiplied by the probability of that condition. And the probability of the condition that you will pay me $1 billion is 0 (pretty sure that’s a safe assumption). That means p(not $1B) is 1, so you get this:

```
p(ketchup) = 0 * p(ketchup|$1B) + 1 * p(ketchup|not $1B) = .0000001
p(ketchup) = 0 * 1 + 1 * .0000001 = .0000001
```

I know all you ketchup lovers out there are reading the .0000001 and thinking “...so you’re saying there’s a chance!” Sure, there’s always a chance.

### Joint Probability, the Chain Rule, and Independence

Another concept in probability theory is that of joint probability, which is just a fancy way of saying “and.” Let’s consider John (uncoincidentally, the name of the author of the original edition). Here’s what you need to know about John: he enjoys Taco Bell and cheesy techno music, for some reason. Today, here are some probable events in John’s life:

```
p(John eats Taco Bell) = .2
p(John listens to cheese) = .8
```

So what are the odds both happen today? Well, that's called the joint probability, and it's written as follows with a comma:

```
p(John eats Taco Bell, John listens to cheese)
```

Now, in this case these events are independent. This means that what John listens to won't affect what he eats and vice versa. However, in real life, we would have to admit that certain songs probably do make us hungry. (For instance, Jimmy Buffet's Cheeseburger in Paradise). But we'll assume independence here. Given this independence, you can then multiply these two probabilities together to get their joint likelihood.

```
p(John eats Taco Bell, John listens to cheese) = .2 * .8 = .16
```

This is sometimes called the multiplication rule of probability. Note that the joint probability is less than the probability of either occurring, which makes perfect sense. Winning the lottery on the day you get struck by lightning is far less likely to happen than either event alone.

One way to see this is through the chain rule of probability, which goes like this:

```
p(John eats Taco Bell, John listens to cheese) = p(John eats Taco Bell) *
p(John listens to cheese | John eats Taco Bell)
```

The joint probability is the probability of one event happening times the probability of the other event happening given that the first event happens. But since these two events are independent, the condition doesn't matter. If John listens to cheesy techno the same amount regardless of lunch, we would say this:

```
p(John listens to cheese | John eats Taco Bell) = p(John listens to cheese)
```

That reduces the chain rule setup to simply the following:

```
p(John eats Taco Bell, John listens to cheese) = p(John eats Taco Bell) *
p(John listens to cheese) = .16
```

### What Happens in a Dependent Situation?

Let's consider a dependent situation. What is the probability that John listens to Depeche Mode today?

```
p(John listens to Depeche Mode) = .3
```
