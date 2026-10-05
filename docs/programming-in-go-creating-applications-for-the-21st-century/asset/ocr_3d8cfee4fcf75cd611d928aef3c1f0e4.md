# 1.7. Polar to Cartesian—Concurrency

primitives for when they’re needed in lower-level code, as we will see in Chap- 7).

Two features make concurrent programming in Go a pleasure. First,goroutines (in effect very lightweight threads/coroutines) can easily be created with without the need to subclass some "thread" class (which isn't possible in Go anyway). Second, channels provide type-safe one-way or two-way communication with goroutines and which can be used to synchronize goroutines.

The Go way to concurrency is to communicate data, not to share data. This makes it easier to write concurrent programs than using the traditional threads and locks approach, since with no share data we can't race conditions (such as deadlocks), and we don't have to remember to lock or unlock there is no shared data to protect.

In this section we will look at the first and last of the chapter’s“overview” examples. This section program uses two communication channels and its processing in a separate Go routine. For such a small program it is complete overkill, but the point is to illustrate a basic use of these features in as clear and short a way as possible. More realistic concurrency examples show many of the different techniques that can be used with Go’s channels and goroutines are presented in Chapter 7.

The program we will review is called polarcartesian:it is an interactive program that prompts the user to enter two whitespace-separated numbers—a radius and an angle—which the program uses to compute the equivalent cartesian coordinates. In addition to illustrating one particular approach to concurrency, it also shows some simple structs and how to determine if the program is running on a Unix-like system or on Windows when the difference matters. Here is an example of the program running in a Linux console:

```
$ ./polarcartesian
Enter a radius and an angle (in degrees), e.g., 12.5 90, or Ctrl+D to quit.
Radius and angle: 5 30.5
Polar radius=5.00 Θ-30.50 → Cartesian x=4.31 y=2.54
Radius and angle: 5 -30.25
Polar radius=5.00 Θ-30.25° → Cartesian x=4.32 y=-2.50
Radius and angle: 1.0 90
Polar radius=1.00 Θ-90.00° → Cartesian x=-0.00 y=1.00
Radius and angle: ^D
$
```

The program is in file polarcartesian/polarcartesian.go, and we will review it top-down, starting with the imports, then the structs it uses, then its init() function, then its main() function, and then the functions called by main(), and so on.