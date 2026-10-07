# Scheduling Decision Scenario

Imagine I’ve asked you to write the OS scheduler based on the high-level information I’ve given you. Think about this scenario that you have to consider. Remember, this is one of many interesting things the scheduler has to consider when making a scheduling decision.

You start your application and the main Thread is created and is executing on core 1. As the Thread starts executing its instructions, cache lines are being retrieved because data is required. The Thread now decides to create a new Thread for some concurrent processing. Here is the question.

Once the Thread is created and ready to go, should the scheduler:

+   Context switch the main Thread off of core 1? Doing this could help performance, as the chances that this new Thread needs the same data that is already cached pretty good. But the main Thread does not get its full time slice.

+   Have the Thread wait for core 1 to become available pending the completion of the main Thread’s time slice? The Thread is not running but latency on fetching data will be eliminated once it starts.

+   Have the Thread wait for the next available core? This would mean cache lines for the selected core would be flushed, retrieved, and duplicated, causing latency. However, the Thread would start more quickly and the main Thread finish its time slice.

Having fun yet? These are interesting questions that the OS scheduler needs to take into account when making scheduling decisions. Luckily for everyone, I’m not the one making them. All I can tell you is that, if there is an idle core, it’s going to be used. You want Threads running when they can be running.

# Conclusion

This first part of the post provides insights into what you have to consider regarding Threads and the OS scheduler when writing multithreaded applications. These are the things the Go scheduler takes into consideration as well.