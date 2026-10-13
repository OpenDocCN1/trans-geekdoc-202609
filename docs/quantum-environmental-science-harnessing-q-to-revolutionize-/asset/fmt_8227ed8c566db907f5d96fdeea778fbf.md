
# The long-term vision and goals for quantum environmental projects are ambitious but achievable. By setting clear objectives, creating strategic roadmaps, and fostering interdisciplinary collaboration, we can harness the potential of quantum computing to create a sustainable future. Vancouver, with its commitment to green innovation and technological advancement, exemplifies how cities can lead the way in this transformative journey.

# Tutorial: Learn to Write a Basic Quantum Program in Q# to Produce a Random Number

In this tutorial, you will learn to:

- Create a Q# program.
- Review the main components of a Q# program.
- Define the logic of a problem.
- Combine classical and quantum operations to solve a problem.
- Work with qubits and superposition to build a quantum random number generator.

## Prerequisites

To run the code sample:

- **In the Copilot in Azure Quantum**: A Microsoft (MSA) email account.
- **In Visual Studio Code**: The latest version of Visual Studio Code or VS Code for the Web.
- **For Jupyter Notebooks**: Install Python, Jupyter extensions, and the latest terminal. Run the following command:

```bash
pip install qsharp
```

## Define the Problem

Classical computers generate pseudorandom numbers based on a deterministic sequence. Quantum computers, however, generate truly random numbers because the measurement of a qubit in superposition is inherently probabilistic. By applying a Hadamard operation to a qubit in the zero state, you put it into an equal superposition of 0 and 1. Measuring this qubit yields a random bit (0 or 1) with equal probability. Repeating this process allows you to generate larger random numbers.

## Define the Random Number Generator Logic

1. Define `max` as the maximum number you want to generate.
2. Determine the number of random bits needed (`nBits`) to express integers up to `max`.
3. Generate a random bit string of length `nBits`.
4. If the bit string represents a number greater than `max`, repeat the process.
5. Otherwise, return the generated number as an integer.

For example, to generate a number up to 12, you need 4 bits. If the bit string "1101" (which is 13 in decimal) is generated, repeat the process. If "0110" (which is 6) is generated, the process is complete.

## Write a Random Bit Generator

The first step is to write a Q# operation that generates a random bit:

```qsharp
operation GenerateRandomBit() : Result {
    // Allocate a qubit
    use q = Qubit();
    // Set the qubit into superposition of 0 and 1 using the Hadamard operation
    H(q);
    // Measure the qubit value
    let result = M(q);
    // Reset the qubit to the |0〉 state
    Reset(q);
    // Return the result of the measurement
    return result;
}
```

## Visualize the Q# Code with the Bloch Sphere

In the Bloch sphere, the north pole represents the classical value 0 and the south pole represents the classical value 1. Any superposition can be represented by a point on the sphere. Applying the Hadamard operation to a qubit in the zero state puts it into an equal superposition, resulting in a 50% chance of measuring 0 or 1.

## Write a Complete Random Number Generator

1. **Add Required Namespaces**: Include the following Q# namespaces:

```qsharp
open Microsoft.Quantum.Convert;
open Microsoft.Quantum.Intrinsic;
open Microsoft.Quantum.Math;
```

2. **Define the Random Number Generator**: Write an operation that repeatedly calls `GenerateRandomBit` to build a string of bits:

```qsharp
operation GenerateRandomNumberInRange(max : Int) : Int {
    mutable bits = [];
    let nBits = BitSizeI(max);
    for idxBit in 1..nBits {
        set bits += [GenerateRandomBit()];
    }
    let sample = ResultArrayAsInt(bits);
    return sample > max ? GenerateRandomNumberInRange(max) | sample;
}
```

3. **Add an Entry Point**:

```qsharp
@EntryPoint()
operation Main() : Int {
    let max = 100;
    Message($"Sampling a random number between 0 and {max}: ");
    return GenerateRandomNumberInRange(max);
}
```

## Complete Code for the Random Number Generator

```qsharp
namespace QuantumRandomNumberGenerator {
    open Microsoft.Quantum.Convert;
    open Microsoft.Quantum.Intrinsic;
    open Microsoft.Quantum.Math;

    @EntryPoint()
    operation Main() : Int {
        let max = 100;
        Message($"Sampling a random number between 0 and {max}: ");
        return GenerateRandomNumberInRange(max);
    }

    operation GenerateRandomNumberInRange(max : Int) : Int {
        mutable bits = [];
        let nBits = BitSizeI(max);
        for idxBit in 1..nBits {
            set bits += [GenerateRandomBit()];
        }
        let sample = ResultArrayAsInt(bits);
        return sample > max ? GenerateRandomNumberInRange(max) | sample;
    }

    operation GenerateRandomBit() : Result {
        use q = Qubit();
        H(q);
        let result = M(q);
        Reset(q);
        return result;
    }
}
```

## Run the Random Number Generator Program

You can run the program in the Copilot in Azure Quantum, or in Visual Studio Code as a standalone Q# application or using a Python host program. Select the number of shots to run, and click "Run". The results are displayed in the histogram and in the Results field.
