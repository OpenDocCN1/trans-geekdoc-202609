```
quick.Stop()

stopped := slow.Stop()
fmt.Println("Stopped before the event",stopped)
} )
```

```
quick 2021-01-13 19:56:59.2428 +0100 CET m+=1.004374708
quick 2021-01-13 19:57:00.240984 +0100 CET m+=2.002541186
quick 2021-01-13 19:57:01.240728 +0100 CET m+=3.002627699
quick 2021-01-13 19:57:02.241683 +0100 CET m+=4.002028251
```

Stopped before the event true

Timers and tickers can be managed using Stop() and Reset(). Invoking the Stop method closes the channel and terminates the triggering of new events. In case of timers, the method returns true if the invocation was triggered before the event was triggered.

In Example 6.14 we define events, using a ticker every second, and slow using a Timer triggered after 5 seconds. The third timer is set to 4 seconds. When the stop timer is reached we stop and slow. Observe that quick.Stop has returned no value. In the case of slow.Stop, true value is returned as the timer was not triggered.

# 6.6 CONTEXT

Working with APIs and processes requires additional control logic such as cancellations, timeouts and deadlines. If we send a request to an API, we will wait for a completion.
Afterwards, we can assume the required expired. The Context type from the context package9, offers constructions to deal with these situations.

The Context interface defines the elements of a common context in Go:

```
type Context interface {
  Deadline(deadline time.Time, ok bool)
  Done() <-chan struct{}
  Err() error
  Value(key interface{}) interface{}
}
```

The Deadline() method returns the deadline for the context and false if. The Done() method returns a channel that is closed when the operations in the context are completed. This channel is closed depending on a cancel function, a deadline or a timeout. Err() returns error if any. Finally, Value() stores key-value pairs of elements that belong to the context.

A context can be built using an empty context (context.Background()) or a previously defined context. Go provides four types of contexts with their corresponding initialization functions. These contexts are with WithCancel(), WithTimeout(), WithDeadline(), and WithValue().

# 6.6.1 WithCancel