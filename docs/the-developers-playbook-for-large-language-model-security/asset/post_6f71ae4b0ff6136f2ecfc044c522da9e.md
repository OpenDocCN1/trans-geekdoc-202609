
impact on society and individual lives. As we stand on the brink of AI's vast potential, we must heed the lesson encapsulated in Peter Parker's journey: to embrace our responsibilities and ensure that our technological advancements foster benefits, not detriments.

As we embark on this chapter, our journey mirrors the ever-expanding universe of AI and LLM technologies—where the bounds of possibility are constantly redrawn. Our purpose here is twofold. Firstly, we aim to examine the trends marking the acceleration of these powerful technologies. The velocity at which AI and LLMs advance is reshaping our tools and methodologies, as well as redefining our ethical and security landscapes. By examining these trends, we seek to understand the pace of technological advancement and its broader role in responsible, secure AI application development.

Secondly, this chapter endeavors to arm the reader with a robust framework for the safe, secure, and responsible use of AI and LLM technologies. This framework, which I call RAISE, is intended to wrap together all the concepts you've learned earlier in the book and make them easier to apply. By offering insights into best practices, ethical considerations, and security measures, we aim to empower you to harness the power of AI and LLMs with a conscientious and informed approach.

## Power

Let's start by looking at the trends pushing forward capabilities of LLMs. We have recently perceived a spike in the capabilities of AI systems, as evidenced by the rush of new applications and investments. But is this a one-time spike that is now in the past, or are we still in the early phases of an exponential curve that will multiply both the power of and risks associated with these systems?

I started my first AI software company in the early 1990s. It was called Emergent Behavior, which I still think is a super cool name for an AI software company. It doesn't exist anymore, but I think telling you a bit about that experience will help illustrate the technology acceleration happening in AI-capable hardware.

In the 1990s, my team built software with genetic algorithms and neural networks. Our software was capable of doing real-world work. We successfully sold it to massive investment banks building arbitrage trading strategies and to Fortune 500 manufacturing companies optimizing their factory floor layouts. However, ultimately, the meager computing power and memory to which we had access meant we were severely constrained. We just couldn't accomplish most of the grand tasks we had in mind.

The most powerful computer I had access to back in those days was a Macintosh IIfx. It included a Motorola 68030 processor with a clock speed best measured in megahertz. My computer had 16 megabytes of RAM. Today's processors run in gigahertz, not megahertz, and the memory is in gigabytes instead of megabytes. That mega to giga change alone implies a ~1,000x improvement. But clock speed isn’t the only improvement, and Moore’s law implies clever chip designers should have been able to provide a doubling of overall computing power every two years. That would give us a 64,000-fold increase in speed over that period.

An improvement of 64,000 fold sounds impressive—and it is. But even that is not nearly enough to account for the explosion in capabilities we’ve seen in that period. It simply wouldn’t have given us enough computing power to train and run today’s LLMs. There is something else going on here. Two other converging trends enabled this: GPUs and Cloud Computing.

## GPUs

In the late 1990s, the need for games to render more polygons at faster frame rates led to the development of special graphics processing units (GPUs) by companies like 3dfx, ATI Technologies, and Nvidia. These companies built GPU architectures to handle massive numbers of parallel math operations to compute 3D spatial relationships. While this was fantastic for games, it is also just the right recipe for accelerating neural networks, which need the exact same kind of support.

In my early 1990s AI startup, my Mac IIfx had a Motorola 68882 math coprocessor alongside its regular CPU. This coprocessor speeds up the types of floating-point math operations you’d need for gaming or AI, in addition to spreadsheets and other more mundane applications. The 68882 was the same coprocessor design used in machines from expensive, top-of-the-line workstation vendors like Sun Microsystems and was one of the fastest chips available at the time. It was rated at 422,000 floating-point operations per second (kFLOPS). That sounds like a lot, but it just wasn’t enough to make practical the kinds of AI tasks we wanted to accomplish.

How much faster is a modern server than my old workstation? While Moore’s law would imply that a new server might be ~64,000 times faster than my old workstation, the architecture of GPUs changes the game for the operations you need for AI applications. Today, a top-of-the-line GPU is an NVIDIA H100, rated at 60 trillion floating-point operations per second (teraflops). Let’s do some math:

```
Speed Increase = \frac{\text{NVIDIA H100 FLOPS}}{\text{Motorola 68882 FLOPS}}
```

The NVIDIA H100 GPU is approximately 142,180,095 times faster than the Motorola 68882 math coprocessor! This staggering increase highlights the monumental strides made in chip computational capabilities, which underpin the current advancements in AI and machine learning technologies. That mind-boggling speed increase shows that we are on a massively accelerating hardware curve for AI-capable hardware. The curve over that time period is over 2,000 times steeper than even the exponential Moore's law curve would have predicted!

One hundred forty-two million times is a shockingly significant improvement: what the modern GPU can compute in a single second would have taken 4.5 years on my old workstation's coprocessor! But it's still not enough computing power to account for the explosion we've seen. We need cloud computing to complete the picture.

![](img/53f45ca5aaf38911d5d2c5f51d4f26a0_177_0.png)

Recently, publications by Taiwan Semiconductor Manufacturing Company (TSMC), which fabricates many of the world's GPUs, say the company expects to see as much as another one million times improvement in computational performance/watt of electricity over the next 10 to 15 years, with performance tripling every 2 years.

## Cloud

The other trend we need to account for is the cloud. Even the massive speed improvement on the single-system hardware curve isn't enough to enable today's sudden AI boom.

In 2006, most people knew Amazon as an online seller of books, CDs, and DVDs. The introduction of Amazon Web Services (AWS) surprised everyone and popularized the idea of on-demand, pay-as-you-go cloud computing. Cloud is so pervasive today that I don't need to explain the concept to you, but I will remind you what it means to AI.

Today, whether you're using AWS, Microsoft Azure, or Google Cloud Platform (GCP), you can access on-demand clusters of GPU-enabled servers with nearly limitless memory attached to ultrafast networks. You can set up massive clusters in minutes if you have enough money in your account. The companies that are training today's foundation models see such a high potential return on investment that they are willing to pay massive cloud computing bills. It's been widely reported that OpenAI spent approximately $100,000,000 on cloud resources to train GPT-4.

I don't believe we're yet at the limits. In February 2024, Nvidia CEO Jensen Huang and OpenAI CEO Sam Altman were in the news. Huang said the world will quickly build a trillion dollars' worth of new data centers to power AI software, and reports say that OpenAI's Sam Altman is looking to raise seven trillion dollars to develop and build new AI chips. We've now entered an era where investments in AI hardware will be measured in trillions of dollars, ensuring we will see continued increases in computing power applied to these models.
