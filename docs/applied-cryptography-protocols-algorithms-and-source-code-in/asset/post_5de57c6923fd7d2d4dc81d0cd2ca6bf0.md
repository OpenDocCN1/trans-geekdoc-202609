
## 7.1 Symmetric Key Length

wide. This estimate includes everything from giant Cray mainframes to subnotebooks. If every one of those computers worked together on this brute-force attack, and each computer performed a million encryptions per second every second, it would still take a million times the age of universe to recover the key.

## Neural Networks

Neural nets aren't terribly useful for cryptanalysis, primarily because of the shape of the solution space. Neural nets work with problems that have a continuity of solutions, better than others. This allows a neural net to learn, proposing better and better solutions as it does. Breaking an algorithm provides for very little in the way of learning opportunities: Unless you recover the key or if the algorithm is any good. Neural nets work well in structured environments where there is something to learn, but not in the high-entropy, seemingly random world of cryptography.

## Viruses

The greatest difficulty in getting millions of computers to work on a brute-force attack is convincing millions of computers to participate. You could ask politely, but that's time-consuming and they might say no. You could try breaking into their machines, but that's even more time-consuming and you might get arrested. You could use a computer virus to spread the cracking program efficiently over as many computers as possible.

This is a particularly interesting idea not presented in [1593]. The attacker writes and lets a loose virus run. The virus doesn't format whenever the computer is idle. Various studies have shown that microcomputers are idle between 70 percent and 90 percent of the time, so the virus would have trouble finding time to work on its task. If it is otherwise benign, it might escape notice whenever it does its work.

Eventually, one machine would stumble on the correct key. At this point there are two ways of proceeding. The first, the virus would spawn a different virus. It wouldn't do anything but replicate and delete any copies of the cracking virus it finds but contain the information about the correct key. This new virus would simply propagate through the computer until it lands on the computer of the person who wrote the original virus.

A second, sneakier approach would be for the virus to display this message on the screen:

> There is a serious bug in this computer.
> Please call 1-800-123-4567 and read the
> following 64-bit number to the operator:
> ```
> XXX XXXX XXXX XXXX
> ```
> There is a $100 reward for the first
> person to report this bug.

How efficient is this attack? Assume the typical infected computer tries a thousand keys per second. This rate is far less than the computer's maximum potential, because we assume it will be doing other things occasionally. Also assume that the typical virus infects 10 million machines. This virus can break a 56-bit key in 83 days and a 64-bit key in 58 years. You might have to bribe the antivirus software makers, that’s your problem. Any increase in computer speeds or the virus infection rate would make this effort more effective.

## The Chinese Lottery

The Chinese Lottery is an eclectic, but possible, suggestion for a massively parallel analysis machine [128]. Imagine a brute-force, million-test-per-second cracking chip was built into every radio and television sold. Each chip is programmed to test a set of keys automatically upon receiving a plaintext/ciphertext over the airwaves. Every time the Chinese government wants to break a key, it broadcasts the data. All the radios and televisions in the country start chugging away. Eventually, the correct key will appear on someone's display, somewhere in the country. The Chinese government pays a prize to that; this makes sure that the result is reported promptly and properly, and also helps the sake of radios and televisions with the cracking chips.

If every man, woman, and child in China owns a radio or television, the correct key to a 56-bit algorithm will appear in 61 seconds. If only 10 Chinese owns a radio or television—closer to the correct key will appear in 10 minutes. The correct key for a 64-bit algorithm will appear in 4.3 hours—43 hours if only 1 in China owns a radio or television.

Some modifications are required to make this attack practical. First, it would be easier to make each try random keys identify a unique set of keys. This would make the attack about 39 percent slower—not much in light of the numbers we’re working with. Also, the Chinese Communist party would have to mandate that every person to listen or watch a certain at a certain time, just to make sure that all of the radios and televisions are operating when the plaintext/ciphertext is broadcast. Finally, everyone would have to be instructed to call a Central-Party-Whatever-It’s-Called if a key ever shows up on their screen, and then to read off the string of numbers appearing there.

Table 7.2 shows the effectiveness of the Chinese Lottery for different countries and different lengths. China could be in the best position to launch such an attack if they have every man, woman, and with their own television or radio. The United States has fewer people but a lot more equipment per capita. The state of Wyoming could break a 56-bit key by itself in less than a day.

## Biotechnology

If biopsies are possible, then it would be foolish not to use them as a distributed brute-force analysis tool. Consider a hypothetical animal, unfortunately called a “DESour [1278]. It consists of biological cells capable of testing possible keys. The plaintext/ciphertext is broadcast to the cells via some optical channel (these cells are transparent, you see). Solutions are carried to the DESour’s speech via special cells that travel through the.

The typical animal had about $10^{11}$ cells if each of them can perform a million encryptions per second, breaking a 56-bit would take seven-thousandths of a second. Breaking a 64-bit key would take less than two tenths of a second. Breaking 128-bit key would still take $10^{11}$ years, though.

Another biological approach is to use genetically engineered algae that are capable of performing brute-force attacks against cryptographic algorithms [1278]. These organisms would make it possible to construct a distributed machine with more processors because they could cover a larger area. The plaintext/ciphertext pair could be broadcast by satellite. If an organism fails the result, it could induce the nearby cells to change color to communicate the solution back to the satellite.

Assume the typical algae cell is the size of a cube 10 microns on a side (this is a large estimate, $10^9$ of them can fill a cubic meter). Pump them into the ocean and cover 200 square miles (518 square kilometers) of water to the deep (if you want to do it—I'm just the man), and you'd have $10^{24}$ (over a billion gallons) of floating in the ocean. (For, Exxon Valdez 10 million gallons of oil.) If each of them can crack a million keys per second, they recover the key for a 128-bit algorithm in just over 100 years. (The resulting algae bloom is your problem.) Breakthroughs in algae processing, ocean diameter, or even the size puddle could spread across the ocean, would reduce these numbers significantly.

## CHAPTER 7 Key Length

Table 7.2 Brute-Force Estimates for Chinese Lottery

| Country | Population | # Televisions/Radios | TIME TO 56-bit | 64-bit |
| :--- | :--- | :--- | :--- | :--- |
| China | 1,190,431 | 257,000 | 280 seconds | 5 hours |
| U.S. | 260,714 | 739,000 | 97 seconds | 6.9 hours |
| Iraq | 19,890,000 | 4,730,000 | 4.2 hours | 44 days |
| Israel | 5,051,000 | 3,640,000 | 5.5 hours | 58 days |
| Wyoming | 470,000 | 1,330,000 | 15 hours | 160 days |
| Winnemuck, NV | 6,100 | 17,300 | 48 days | 34 days |

## Thermodynamic Limitations

One of the consequences of the second law of thermodynamics is that a certain amount of energy is necessary to represent information. To record a single bit by changing the state of a system requires an amount of energy less than $kT$, where $T$ is the absolute temperature of the system and $k$ is the Boltzmann constant. Given that $k = 1.38 \times10^{-16}$/Kelvin, and the ambient temperature of the universe is $3.2^{\circ} \ext{K}$, an ideal computer running at $3.2^{\circ} \ext{K}$ would consume $4.4 \times10^{-16}$ ergs every time it set or cleared a bit. To run a computer colder than the cosmic background radiation would require extra energy to run a heat pump.
