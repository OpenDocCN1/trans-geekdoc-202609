
Immanuel Kant, René Descartes, David Hume, John Stuart Mill, and Friedrich Nietzsche walk into a bar. No, wait, not a bar. They walk into an Italian restaurant. Because there are five of them, they won't fit nicely in a booth or at one of the rectangular tables. This means they need to be seated at a round table. As you'd expect, they each get a beautiful silverware setup wrapped in a very nice cloth napkin. This is a fancy restaurant, after all. No paper here. All cloth. Being well-behaved philosophers, they take the napkins and tuck them into their collars since they all plan to have spaghetti, and we all know how sloppy that has the potential to be as sauce goes flying off the individual strands of pasta while you're slurping them up. What they discover is that each silverware setup has a fork and a knife. This means we have a setup that looks like what you see in [Figure 5.1](#c05.xhtml#c05-fig-0001).

After the breadsticks have been consumed, including the one that had to be split because six breadsticks for five philosophers leaves one left over, the bowls of spaghetti come out. Here's the problem we have: consuming spaghetti requires two forks, one to wrap the pasta around the second, so you don't just have long strands of spaghetti dripping tomato sauce all over the places not covered by the napkins. This requires a little bit of sharing. If Hume wants to eat, he needs his fork plus the fork of Mill, who is sitting to his right. He picks up his fork in his left hand and reaches for the fork on his right, except that Mill has picked that up. In fact, all of the philosophers have their own fork in their left hand.

![FIGURE 5.1: Dining philosophers](images/c05f001.png)

[**FIGURE 5.1**](#c05.xhtml#R_c05-fig-0001): Dining philosophers

If no one puts down a fork, no one can eat. If this continues over a long period of time, the spaghetti gets cold and isn't nearly as much fun to eat. Worse, though, if it continues for a really long time, the philosophers start to collapse from starvation. We can't have that, since none of them have written their signature papers as yet, leaving the rest of us unenlightened. We need a solution to this problem.

This is a problem that was proposed in the mid-1960s by Edsger Dijkstra, a famous computer scientist who is also responsible for one of the essential algorithms used to get data across the Internet as well as to get you from your home to the dentist's office you've never been to. The idea behind this particular scenario is to demonstrate the issues of concurrence and synchronization. If the philosophers can't figure out how to coordinate their activities, they will all starve. That means this is also a demonstration of issues with resource contention. Multiple actors/devices trying to get access to a single resource at the same time is a problem that needs to be solved.

Of course, when it comes to such issues as making sure a process gets adequate time in the processor, which is one of the scenarios this problem is meant to highlight, that's up to the operating system and not us as lowly programmers. However, it can be our job to make sure we design algorithms in such a way that we aren't encouraging starvation—the case where a process doesn't get the resources it needs to complete processing.

Let's say that rather than a fork, and rather than Kant and Hume, we have thread A and thread B, which you can think of as thread Kant and thread Hume if it's more amusing to you. Thread Kant takes possession of (locks) a memory location with the identifier of Reason. It maintains that lock even while it is doing processing on other things and has no need for Reason while it continues to chug along. Hume, on the other hand, really needs Reason; but since Kant has it locked up, Hume can't access it. This isn't so much the ownership issue with Rust but one of the issues with concurrent processing. You can't, or at least you shouldn't, allow two separate threads read/write access to any memory location at the same time, so each thread locks the memory location so no one else gets it, since any other access could cause corruption to either of the accessing threads.

It's bad etiquette to hoard a resource, of course, and that's even more true if others are waiting to use it or if at least there is an expectation that there may be another thread or process that may use the resource. This is where we come back to the issue of everyone with a fork in their left hand and no fork for their right hand so they can twirl up the spaghetti in order to eat. One way to address this state of affairs is with communication. There are different ways this communication can be addressed. We're going to take a look at mutexes, semaphores, and interprocess communication. In some cases, we have the application needing to manage the memory access, since the operating system may not know to protect against access from one process thread to another. These different mechanisms are how the application will manage access.

### Mutexes and Semaphores

Two ways of addressing the problem of accessing the same memory location at the same time are mutexes and semaphores. A *mutex* is a data type or data structure used to protect a memory location. The term is short for *mutual exclusion* or *mutually exclusive*. The point is that as long as one thread is accessing a memory location, no other thread can get access. You might think about a mutex as being a lock on a piece of data. Before any thread attempts to gain access to a memory location, it applies the lock. You might visualize it as placing a piece of data inside a box that has a lock on it. You can see a representation of this box with the lock in [Figure 5.2](#c05.xhtml#c05-fig-0002). Just imagine the mutex being the key that locks and unlocks the box where the data is located.

The problem with a mutex is that it is done within the program rather than being enforced outside of the program. This means that all of the threads have to cooperate and agree to use these mutexes or locks. In its simplest form, you have a variable that is checked to see if there is a value. A very simple implementation is shown next, written in C because it's usually clear and straightforward to see what is happening in C, as it's a reasonably stripped-down language without much of anything that is taken care of for you, the programmer. In the following snippet, we have a value, `mutex`, that is checked to see if there is a value. If there isn't, or rather, if the value is 0, we set a non-zero value and then go off and do something before setting the variable back to 0 so some other piece of code can get access to a variable that is being protected:

![FIGURE 5.2: Visual representation of a mutex](images/c05f002.png)

[**FIGURE 5.2**](#c05.xhtml#R_c05-fig-0002): Visual representation of a mutex

```
if (mutex == 0) {
    mutex = 1;
}
// do something
mutex = 0;
```

Technically, what we've just seen is a semaphore. A *semaphore* is nothing more than a variable that sets a flag that another portion of the code can check. Semaphores are binary in nature. Either they are set, or they are not. A semaphore, especially in this case, can be used as a mutex since the purpose of this variable is simply to indicate that work is going on, and some data shouldn't be touched while the value is non-zero. You could also implement this as a Boolean value since all we care about is whether the value is set, `true`, or not set, `false`.
