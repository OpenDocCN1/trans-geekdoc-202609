The important thing to keep in mind is that you have no idea how deep any thread will be: There can be one level of replies, or twenty. So to properly lay out all the children of any one thread you need a very, very flexible script. It needs to do something like this:

```
print current topic
while the current topic has unprocessed child topics
    set current topic to next unprocessed child
    go to line 1
end while
if current topic has a parent
    set current topic to that parent and go to line 2
else
    exit
end if
```

This block of code must be repeated indefinitely until no other answers exist. But how do you tell a script to do something until it runs out of answers? The looping mechanisms we’ve discussed so far won’t really work. The for..., while..., and do...while loops that we talked about in Chapter 5 and used in the previous chapters are of no help.

If that isn’t clear, take a look at Table 10-6 and the code that follows.

| topic_id | root_id | parent_id | subject | name | date |
|---|---|---|---|---|---|
| 1 | 1 | 0 | Nachos rule | Jay | 3/12/2003 |
| 2 | 2 | 0 | Cheetos are the best | Ed | 3/12/2003 |
| 3 | 1 | 1 | Re: Nachos rule | Don | 3/12/2003 |
| 4 | 1 | 3 | Re: Nachos rule | Bill | 3/13/2003 |
| 5 | 5 | 0 | What about cookies | Evany | 3/13/2003 |
| 6 | 2 | 2 | Re: Cheetos are the best | Ed | 3/14/2003 |
| 7 | 1 | 4 | Cheetos, are you kidding | Jeff | 3/15/2003 |
| 8 | 5 | 5 | Re: What about cookies | Jay | 3/15/2003 |

Suppose you want each level to be indented a little farther than the previous one, by means of the HTML blockquote tag. Now, assume that you’re calling the following function by passing a topic_id of 7.