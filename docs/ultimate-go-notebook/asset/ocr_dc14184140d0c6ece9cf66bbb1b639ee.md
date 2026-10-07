make with this is mixing up the Unlock calls with the wrong version. Having a Lock with a RLock will never end well.

# Listing 6.31

```
7 : Performing Read : Length[0]
5 : Performing Read : Length[0]
0 : Performing Read : Length[0]
3 : Performing Read : Length[0]
7 : Performing Read : Length[0]
1 : Performing Read : Length[0]
****> Performing Write
0 : Performing Read : Length[1]
5 : Performing Read : Length[1]
3 : Performing Read : Length[1]
6 : Performing Read : Length[1]
7 : Performing Read : Length[1]
4 : Performing Read : Length[1]
1 : Performing Read : Length[1]
2 : Performing Read : Length[1]
****> Performing Write
7 : Performing Read : Length[2]
1 : Performing Read : Length[2]
3 : Performing Read : Length[2]
```

The output shows how Goroutines are reading at the same time, but all the reading stops when the writer takes place.

# 6.10 Channel Semantics

It's important to think of a channel not as a data structure, but as a mechanic for signaling. This goes in line with the idea that I send and receive from a channel, not read and write. The problem in front of me can't be solved with signaling, if the word signaling is not coming out of my mouth, I need to question the use of channels.

There are three things I need to focus on when thinking about signaling. The first one is, does the Goroutine that is sending the signal, need a guarantee that the signal has been received? I might think that the answer to this question is always yes, but remember, there is a cost to every decision and there is a cost to having a guarantee at the signaling level.

The cost of having the guarantee at the signaling level is unknown latency. The sender won't know how long they need to wait for the receiver to accept the signal. Having to wait for the receiver creates blocking latency. In this case, unknown amounts of blocking latency. The sender has to wait, for an unknown amount of time, until the receiver becomes available to receive the signal.

Waiting for the receiver means mechanically, the receive operation happens the send. With channels, the receive happens nanoseconds before, but it's before. This means the receiver takes the signal and then walks away, allowing the sender