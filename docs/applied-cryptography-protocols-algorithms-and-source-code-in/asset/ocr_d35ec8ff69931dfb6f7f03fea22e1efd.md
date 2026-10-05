# CHAPTER 17 Other Stream Ciphers

There is also a random-number generator that uses the computer's disk drive [49]. It measures the time required to read a disk block and uses the variation in that time as a random source. It filters the data to remove structure that comes from quantization, then applies a Fourier transform to vectors of numbers. This removes bias and correlation. Finally, it uses the spectral angles for frequencies in [0, π], normalized to the unit interval, as the random bits. A large part of the variation in disk rotation speed is caused by turbulence, so there is randomness in the system. There are caveats, if you keep too many bits of the output, you are using the fast transform as a random-number generator and risk predictability. And it's best to read the same disk block over and over, so that your filtering doesn't have to remove structure that comes from the disk-scheduler. An implementation of this system was able to collect about 100 bits per minute [49].

# Using the Computer's Clock

If you want a single random bit (or even a few), take the least significant bit from any clock register. This might not be terribly random in a UNIX system because of potential synchronizations, but it works on some personal computers.

Beware of getting too many bits this way. Executing the same subroutine times in succession could easily skew bits generated in this manner. For example, if each generation subroutine takes an even number of clock ticks to execute, you will get an endless stream of the same bit out of the generator. If each subroutine takes an odd number of clock ticks to execute, you will get an endless stream of alternating bits out of generator. Even if the reason isn't this obvious, the result bit will be far from random.

One random-number generator works this way [918]:

> Our random-number generator ... works by setting an alarm and then incrementing a counter register in the CPU until an interrupt occurs. The contents of the register are then XORed with the contents of an output buffer (truncating the register to 8 bits). After each byte of the output buffer is filled, the buffer is further processed by a right, circular shift of each character by 2 bits. This has the effect of moving the most active (and random) bits into the most significant positions. The entire process is repeated 3 times. Each character of the buffer has been touched by the two random bits of the counter register after interrupts. It is 4n interrupts have occurred where n is the number of desired random bits.

This method is very sensitive to the randomness of system interrupts and the granularity of the clock. The output looked pretty good when tested on real UNIX machines.

# Measuring Keyboard Latency

People's typing patterns are both random and nonfiction. They are random enough that they can be used as a means of identification, but they are random enough that they can be used to generate random bits. Measure the time between