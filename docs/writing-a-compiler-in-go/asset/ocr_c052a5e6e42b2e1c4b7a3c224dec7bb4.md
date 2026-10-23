# # Virtual and Real Machines

You probably associate “virtual machine” with software like VMWare or Virtualbox. These are programs that emulate a computer, including a disk drive, hard drive, graphics card, etc. They allow you to, for example, run a different operating system inside this emulated computer. Yes, these are virtual machines. But that’s not what we’re here to talk about. That’s the *other* type of virtual machine.

What we are going to talk about (and later build) are virtual machines that are used to implement programming languages. Sometimes they consist of just a few functions, other times they make up a few modules and on occasion they’re a collection of classes and objects. It’s hard to pin their shape down. But that doesn’t matter. What’s important is this: they don’t emulate an existing machine. They *are* the machine.

The “virtual” is due to the fact they only exist in software, not in hardware, and are thus purely abstract constructs. The “machine” describes their behaviour. These software constructs act like a machine. And not just any machine, no. They mimic the behaviour of their hardware equivalent: computers.

That means, in order to understand and build a virtual machine, we need to learn how a real machine works.

# ## Real Machines

> > “So, how does a computer work?”

What might sound like an intimidating question can actually be answered in five minutes and with a piece of paper. I don’t know how fast you can read and I’m certain I can’t show you what I draw on a scrap of paper, but let me try anyway.

Nearly every computer in your life is built according to the [Von Neumann architecture](https://en.wikipedia.org/wiki/Von_Neumann_architecture), which describes a way to build a fully-functioning computer with a surprisingly tiny number of parts.

In Von Neumann’s model a computer has two central parts: a processing unit, which contains an arithmetic logic unit (ALU) and multiple processor registers,