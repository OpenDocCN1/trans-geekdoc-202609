# Language Mechanics

+   Use channels to orchestrate and coordinate Goroutines.
  - Focus on the signaling semantics and not the sharing of data.
  - Signaling with data or without data.
  - Question their use for synchronizing access to shared state.
    - There are cases where channels can be simpler for this but initially question.

+   Unbuffered channels:
  - Receive happens before the Send.
  - Benefit: 100% guarantee the signal being sent has been received.
  - Cost: Unknown latency on when the signal will be received.

+   Buffered channels:
  - Send happens before the Receive.
  - Benefit: Reduce blocking latency between signaling.
  - Cost: No guarantee when the signal has has been received.
    - The larger buffer, the less guarantee.

+   Closing channels:
  - Close happens before the Receive. (like Buffered)
  - Signaling without data.
  - Perfect for signaling cancellations and deadlines.

+   NIL channels:
  - Send and Receive block.
  - Turn off signaling
  - Perfect for rate limiting or short-term stoppages.

# Design Philosophy

+   If any given Send on a channel CAN cause the sending Goroutine to block:\n  - Be careful with Buffered channels larger than 1.
    - Buffers larger than 1 must have reason/measurements.
  - Must know what happens when the sending Goroutine blocks.

+   If any given Send on a channel WON'T cause the sending Goroutine to block:
  - I have the exact number of buffers for each send.
    - Fan Out pattern
  - I have the measured buffer for max capacity.
    - Drop pattern

+   Less is more with buffers.
  - Don't think about performance when thinking about buffers.
  - Buffers can help to reduce blocking latency between signaling.
    - Reducing blocking latency towards zero does not necessarily mean throughput.
    - If a buffer of one is giving me good enough throughput then keep it.
    - Question buffers that are larger than one and measure for size.
    - Find the smallest buffer that provides good enough throughput.