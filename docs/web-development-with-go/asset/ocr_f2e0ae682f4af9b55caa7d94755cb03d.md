Before we proceed I want to note that while it might feel like developers know how to do things like install Postgres by heart, the truth is most of them are just good at finding the right docs and tutorials whenever they need them. I myself know roughly what steps are involved in setting up Postgres, but I verify things nearly every time I install PostgreSQL. You shouldn’t be discouraged if you don’t remember all of these steps by heart. That is completely normal!

# Box 16.7. External resources

If this guide feels out of date, feel free to reference my personal website where I maintain a few articles walking through how to install various versions of PostgreSQL on different operating systems.

https://www.calhoun.io/using-postgresql-with-golang/

# Installation

The first thing we want to do before we start installing anything is to update apt-get. This will ensure that we are installing from an updated repository.

```
$ sudo apt-get update
```

After that finishes, we can go ahead and install all of the packages we are going to need.