
formatted binary data and deserialise that binary data back into your data structures.

The gRPC framework is a high-performance, platform-neutral standard for making distributed function calls across a network. The *RPC* in *gRPC* stands for *remote procedure call*, which is a technique for transparently calling a function on a remote system and receiving the result as if you had executed the function on your local system. gRPC uses protocol buffers as its underlying data serialization format. Go’s protocol buffer module allows you to easily add gRPC support by defining services in your *.proto* file and leveraging the generated code. This lets you quickly and efficiently stand up distributed services or integrate with existing gRPC services.

**294** Chapter 12

**13**

**L O G G I N G A N D M E T R I C S**

In an ideal world, our code would be free of bugs from the outset. Our network services would exceed our expectations for performance and capacity, and they would be robust enough to adapt to unexpected input without our intervention. But in the real world, we need to worry about unexpected and potentially malicious input, hardware degradation, network outages, and outright bugs in our code.

Monitoring our applications, no matter whether they are on premises or in the cloud, is vital to providing resilient, functional services to our users. Comprehensive logging allows us to receive timely details about errors, anomalies, or other actionable events, and metrics give us insight into the current state of our services, as well as help us identify bottlenecks.

Taken together, logging and metrics allow us to manage service issues and focus our development efforts to avoid future failures.

You’ve used Go’s log and fmt packages to give you feedback in previous chapters, but this chapter will take a deeper dive into logging and instrumenting your services. You will learn how to use log levels to increase or decrease the verbosity of your logs and when to use each log level. You’ll learn how to add structure to your log entries so software can help you make better sense of log entries and zero in on relevant logs. I’ll introduce you to the concept of wide event logging, which will help you maintain a handle on the amount of data you log as your services scale. You’ll learn techniques for dynamically enabling debug logging and managing log file rotation from your code.

This chapter will also introduce you to Go kit’s metrics package. Per Go kit’s documentation, the metrics package “provides a set of uniform interfaces for service instrumentation.” You’ll learn how to instrument your services by using counters, gauges, and histograms.

By the end of this chapter, you should have a handle on how to approach logging, how to manage log files to prevent them from consuming too much hard drive space, and how to instrument your services to gain insight into their current state.

**Event Logging**

Logging is hard. Even experienced developers struggle to get it right. It’s tough to anticipate what questions you’ll need your logs to answer in the future, when your service fails—yet you should resist the urge to log everything just in case. You need to strike a balance in order to log the right information to answer those questions without overwhelming yourself with irrelevant log lines. Overzealous logging may suit you fine in development, where you control the scale of testing and overall entropy of your service, but it will quickly degrade your ability to find the needle in the haystack when you need to diagnose production failures.

In addition to figuring out what to log, you need to consider that logging isn’t free. It consumes CPU and I/O time your application could otherwise use. A log entry added to a busy for loop while in development may help you understand what your service is doing. But it may become a bottleneck in production, insidiously adding latency to your service.

Instead, sampling these log entries, or logging on demand, may provide suitable compromises between log output and overhead. You might find it helpful to use *wide* *event* log entries, which summarize a transaction. For example, a service in development may log half a dozen entries about a request, any intermediate steps, and a response. In production, a single wide event log entry providing these details scales better. You’ll learn more about wide event log entries in “Scaling Up with Wide Event Logging” o[n page 312](#index_split_006.html#p334).

Lastly, logging is subjective. An anomaly may be inconsequential in my application but indicative of a larger issue in your application. Whereas I could ignore the anomaly, you’d likely want to know about it. For this reason, it’s best if we discuss logging in terms of best practices. These practices are a good baseline approach, but you should tailor them to each application.

***The log Package***

You have superficial experience using Go’s log package, in earlier chapters, for basic logging needs, like timestamping log entries and optionally exit-ing your application with log.Fatal. But it has a few more features we have yet to explore. These require us to go beyond the package-level logger and instantiate our own *log.Logger* instance. You can do this using the log.New function:

func New(out io.Writer, prefix string, flag int) *Logger

The log.New function accepts an io.Writer, a string prefix to use on each log line, and a set of flags that modify the logger’s output. Accepting an io. Writer means the logger can write to anything that satisfies that interface, including an in-memory buffer or a network socket.

The default logger writes its output to os.Stderr, standard error. Let’s look at an example logger in Listing 13-1 that writes to os.Stdout, standard output.

func Example_log() {

l := log.New(1os.Stdout, 2"example: ", 3log.Lshortfile)

l.Print("logging to standard output")

// Output:

// example: 4log_test.go:12: logging to standard output

}

*Listing 13-1: Writing a log entry to standard output (* log_test .go *)*

You create a new *log.Logger* instance that writes to standard output 1.

The logger prefixes each line with the string *example:* 2. The flags of the default logger are log.Ldate and log.Ltime, collectively log.LstdFlags, which print the timestamp of each log entry. Since you want to simplify the output for testing purposes when you run the example on the command line, you omit the timestamp and configure the logger to write the source code filename and line of each log entry 3. The l.Print function on line 12 of the *log_test.go* file results in the output of those values 4. This behavior can help with development and debugging, allowing you to zero in on the exact file and line of an interesting log entry.

Recognizing that the logger accepts an io.Writer, you may realize this allows you to use multiple writers, such as a log file and standard output or an in-memory ring buffer and a centralized logging server over a network. Unfortunately, the io.MultiWriter is not ideal for use in logging. An io.MultiWriter writes to each of its writers in sequence, aborting if it receives an error from any Write call. This means that if you configure Logging and Metrics 297 your io.MultiWriter to write to a log file and standard output in that order, standard output will never receive the log entry if an error occurred when writing to the log file.

Fear not. It’s an easy problem to solve. Let’s create our own io.MultiWriter implementation, starting in Listing 13-2, that sustains writes across its writers and accumulates any errors it encounters.

package ch13

import (

"io"

"go.uber.org/multierr"

)

type sustainedMultiWriter struct {

writers \[\]io.Writer

}

func (s \*sustainedMultiWriter) 1Write(p \[\]byte) (n int, err error) {

for \_, w := range s.writers {

i, wErr := w.Write(p)

n += i

