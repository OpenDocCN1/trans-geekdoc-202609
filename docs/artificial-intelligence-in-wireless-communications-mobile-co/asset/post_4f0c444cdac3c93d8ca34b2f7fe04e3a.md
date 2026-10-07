
foundation for software and cognitive work.^1. The free software licensing of GNU Radio also means that anyone reading this book can download and experiment with the ideas we are presenting.

GNU Radio is a software package that provides signal processing blocks, discrete components to perform a specific task. Each of these components is a C++ class that a developer can connect to other blocks to create a flow graph. A block can be a source with only output ports, a sink with just input ports, or a block with both inputs and outputs. The GNU Radio supports many signal processing blocks and a number of waveforms. Blocks include finite impulse response (FIR) and fast Fourier transform (FFT) filters, simple arithmetic operations, complex number processing and transformations, frequency translation, waveform-specific techniques [12], and timing synchronization blocks [13, 14, 15, 16].

In GNU Radio, each separate signal processing block is implemented in C++ and gets into a library. Python, a high-level programming language (www.python.org) is then used as an interface to connect the signal processing blocks the C++ library together. This is performed by “wrapping” the C++ library into a Python module so that Python can call the C++ functions through the “wrapper.” Blocks are connected to build a flow graph, an architectural construct that represents the flow of samples through the radio. Blocks can be connected in a hierarchical fashion as well, which allows us to build blocks of more specialized processing capabilities out of smaller, general blocks. Recently, the project has allowed all these capabilities to be done in a full C++ environment, so that all GNU Radio functionality is accessible either a C++ or a Python project. The move to all C++ allows more traditional workspace development of waveforms, applications, and embedded systems.

## 3.4.1 The Universal Software Peripheral

A software-only SDR does little actual radio communications without a means to get and from the radio frequency (RF) domain. A device is required to convert between the analog, RF domain and the digital, software world. These devices are referred to as either interfaces or RF front-ends. A parallel project with the GNU Radio to provide an interface is the Universal Software Radio Peripheral (USRP) [17]. The USRP is a board that does basic intermediate frequency (IF) processing of and downconversion, decimation, and filtering. Along with the USRP benefit a set of daughterboards to perform the final analog up- and downconversion, filtering, and amplification. The USRP provides the interface to connect between the digital baseband in the SDR and the analog, RF domain.

> 1. For anyone concerned learning more about how businesses can use and benefit from open source software, see work by Bruce Per, http://opensource.org, and the Free Software Foundation at http://www.fsf.org, among others.

The USRP provides analog to digital sampling with a 12-bit, 64 Msps ADC and digital to analog with 14-bit, 128 Msps DAC. It can hold two transmitter and two receiver daughterboards at a time. It is controlled and data is transmitted and received over a USB 2.0 interface.

While the USRP and GNU Radio are parallel development projects, they do not necessarily depend on one another as other SDR platforms use the USRP (e.g., [18, 19]) and other RF front ends can use GNU Radio as the signal processing system.

## 3.4.2 The USRP Version 2

An updated USRP was recently released, the USRPv2. This design offers a number of improvements to the first generation USRP. It uses higher-resolution and faster ADCs and DACs at 14-bits, 100 Msps and 16-bits, 400 Msps, respectively. It handles only one transmitter and one receiver at a time, unlike USRPv1, but the USRPv2 is equipped with a high-speed connector to tie two USRPs together for multiprocessing. USRPv2 includes a more capable FPGA, the Xilinx Spartan 3, than USRPv1, which uses Altera Cyclone. USRPv2 also stores the FPGA image on SD card instead of writing it from the host computer when first run as USRPv1. One of the most significant changes between USRPv1 and USRPv2 is the use of a Gigabit Ethernet (GigE) link instead of USB for data transfer. With full-duplex GigE, USRPv2 can simultaneously transmit and receive at 25 MHz bandwidth. Throughout this book, the real differences between USRPv1 and v2 are unimportant. In cognitive radio concept, these systems play the same role. We will generically refer to these two systems as USRP since we will not need to further differentiate their capabilities.

## 3.4.3 Flow Graphs

The role of GNU Radio ends between the pulse shape and frequency upconversion block in Figure 3.2. The design of GNU Radio allows for abstraction. Once instantiated, a signal processing block becomes an object, or node. From graph theory perspective, these graphs are simple, flat graphs that have at least one source and one sink. Types of sources and sinks include vectors to input or output, files to read and write from disk, and network card, generalized source blocks for creating sinusoidal signals, and the USRP to transmit and receive data over this device. A flow graph may include many paths and many sources and sinks so long as there are no loops and there is connection to each input and output port. Figure 3.3 shows a simple flow graph that reads a signal from a file, filters it, mixes it with a sinusoidal tone, and simultaneously outputs it to a USRP and stores it to another file.

![](img/7780d9a7979a9fac4194139511cc_56_0.png)

**Figure 3.3** Simple GNU Radio flow graph that mixes a filtered signal with a sinusoid, output to a file, and transmitted through the USRP.

## Overview and Basics of Software Radios

We introduce the flow graph concept with this simple application to provide an understanding of how flow graphs look as well as how to read them. We are using the Python terminology. The blocks in these figures include the name of the GNU Radio block. Most of these are from the gr module coming from others like the USRP interface module, usrp. Any blocks from the blks module are hierarchical blocks of other GNU Radio blocks that are also distributed with GNU Radio. The arguments in parenthesis are the arguments that are passed to the module in the code. The outer one in bold represents a name given to the block.

For this particular graph, we provide in Figure 3.4 the source code that would go along with this graph to realize Figure 3.3. The only concept to keep in mind in the code is the gr.top_block() is the GNU Radio flow graph object representation.

```
def main():
    # set up the parameters
    interp = 64
    taps = gr.firdes.low_pass(1.0, 1.0, 0.2, 0.1)

    # define the blocks
    sig_in = gr.sig_source_c(usrp_dac_freq(), 1000,
        gr.GR_SIN_WAVE, 1)
    file_in = gr.file_source(gr.sizeof_gr_complex,
        "input.dat")
    fir_flt = gr.fir_filter_ccf(1, taps)
    mix = gr.multiply_cc()
    usrp_out = usrp_sink_c(0, interp)
    file_out = gr.file_sink(gr.sizeof_gr_complex,
        "output.dat")

    # build the flow graph
    tb = gr.top_block()
    tb.connect(file_in, (mix, 0)) # file to 1st mixer port
    tb.connect(sig_in, fir_flt)
    tb.connect(fir_flt, (mix, 1)) # signal to 2nd mixer port
    tb.connect(mix, usrp_out)
    tb.connect(mix, file_out)
    tb.run() # start the flow graph
```

Figure 3.4 Python source code for the simple GNU Radio flow graph of Figure 3.3.

The graph reads a complex waveform from a file “input.dat” and first filters it. The filter is defined such that the complex envelope of the signal is between the normalized frequencies of ±0.5 (the Nyquist zone) with
