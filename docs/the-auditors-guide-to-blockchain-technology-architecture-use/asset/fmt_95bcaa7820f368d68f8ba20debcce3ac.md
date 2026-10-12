
The following section provides basic information related to tools used in each type of testing/audit method presented in the previous section.

### Control Flow Analysis Tools

#### McCabe IQ

A detailed review of each feature in the attack map can be done with the flowgraph, annotated source code listing. Path information is tested to ensure that the control flow paths displayed are accurate, stable and compliant with specifications [[31](#ch22.xhtml#r515)].

McCabe IQ’s Data Dictionary functionality is another strategy for a more thorough investigation into forbidden functions that are being used in the program code. Users can scan for data elements and function calls in the data dictionary and classify the paths within a function that includes those calls [[31](#ch22.xhtml#r515)]. The tool is available on GitHub at [https://github.com/PyCQA/mccabe](https://github.com/PyCQA/mccabe).

#### Ethereum Virtual Machine

The EVM consists of a single virtual machine built on a stack with a custom instruction format. Each instruction is portrayed as a one-byte opcode. On the data stack, arguments are transferred. The push instructions that are used to push constants onto the stack are the only exception. These constants are directly translated into the bytes of the instruction. As the EVM has an explicit marker for simple block entries, retrieving the basic block boundaries is tractable [[30](#ch22.xhtml#r514)]. The tool is available on GitHub at [https://github.com/exthereum/evm](https://github.com/exthereum/evm).

### Taint Analysis Tools

#### TAJ

Taint Analysis for Java (TAJ) is a method designed to be sufficiently reliable in generating a low false-positive rate and be versatile enough to allow the evaluation of large applications. TAJ provides a range of strategies for generating practical effects on incredibly large programs though they are limited to a given time or budget for memory. TAJ advocates a prioritization approach that targets the research on parts of the web application that are likely to partake in taint dissemination when implementations are incredibly large and the end-user still wants the analysis to terminate in a limited period or remain within a specified memory usage level [[27](#ch22.xhtml#r511)]. The tool is available on GitHub at [https://github.com/TJAndHisStudents/TaintFlowAnalysis](https://github.com/TJAndHisStudents/TaintFlowAnalysis).

#### DYTAN

Dynamic Taint Analysis adequately manages knowledge flow within a program due to data and control flow and enables the analysis to be tailored in different dimensions. SQL injection attacks are avoided through dynamic tainting, in which attackers send maliciously constructed strings to a web server to enter the underlying database. Most dynamic-taint-based SQL injection approaches work by tainting and monitoring unsafe files which are inputs from the user. Once a query string is submitted to the database, it is reviewed to ensure that the string or sections of it have not been generated using any corrupted data [[28](#ch22.xhtml#r512)]. This tool is available on GitHub at [https://github.com/behzad-a/Dytan](https://github.com/behzad-a/Dytan).

### Dynamic Code Analysis Tools

#### MAIAN

The dynamic tool MAIAN considers the execution traces of smart contracts which are the sequences recorded on the blockchain while running a contract. MAIAN also considers the vulnerability categories along with the execution traces. A transaction will request a smart contract to run a function every time, leading to the exploitation of an execution path for a given input. So, the execution traces may have a chain of effects. Therefore, to find the exploits on the specified execution traces of a smart contract, the MAIAN tool uses systematic techniques. MAIAN consists of two major components, namely, symbolic analysis and concrete validation. The symbolic analysis component has the input of contracts bytecode and the analysis specifications with the vulnerability category. MAIAN continues its execution until it reaches an uncertain trace with a set of vulnerability properties. All the executions are done on EVM, which will simplify the symbolic execution of smart contract bytecode. Symbolic variables are taken as inputs for every execution trace such that the symbolic analysis component will return the concrete values for the given symbolic variables if the contract is exposed as vulnerable. The role of the concrete validation is to verify the results of symbolic analysis and confirm the accuracy of bugs found in the smart contract. The state of the contract on the main Ethereum blockchain is not affected by MAIAN during the analysis [[8](#ch22.xhtml#r492)]. This tool has been available on GitHub under an MIT license since March 2018 [[21](#ch22.xhtml#r505)].

#### ContractLarva

This tool is used for runtime verification in smart contracts. A user can demonstrate the properties of a given smart contract by using Dynamic Event Automata (DEA) – a specification language used by ContractLarva. The tool generates a new Solidity contract by taking the specifications of the given contract as input. The new contract functions the same as an original contract, but a code is added to the contract to check the runtime verification and react accordingly in case of any observed violations. Although ContractLarva is implemented on many smart contracts to deploy runtime verification and recovery, it faces many challenges that need to be addressed [[27](#ch22.xhtml#r511)]. This tool is available on GitHub under an Apache-2.0 license [[21](#ch22.xhtml#r505)].

### Vulnerability-Based Scanning Tools

#### Mythril

An automated tool for analyzing smart contracts. The analysis is based on byte code. It uses taint analysis and control flow analysis to find the vulnerabilities. Mythril uses the command line as an interface [[22](#ch22.xhtml#r506)]. Vulnerabilities found through this tool are detailed and documented. ConsenSys has developed and maintained the Mythril on Github under MIT license in September 2017 [[21](#ch22.xhtml#r505)].

#### Securify

Another automated user interface-based security analysis tool used for Ethereum smart contracts based on byte code and detects vulnerabilities such as reentrancy, input validation, etc. [[22](#ch22.xhtml#r506)]. This tool provides added assurance that if a pattern is detected, the detection implies that the contract code possesses the corresponding security property. The tool is in Java and has been available on Github under Apache 2.0 license from 2018 [[21](#ch22.xhtml#r505)].

#### SmartCheck

An open-source, user interface-based, automated tool that runs the Solidity source code and checks for vulnerabilities and other security issues [[22](#ch22.xhtml#r506)]. SmartCheck converts the code into Extensible Markup Language (XML) syntax and specifies vulnerabilities as XQuery path expressions which are used in search of patterns in an XML tree. The latest version of the tool is closed source, and it has twice as many patterns for checking vulnerabilities. The tool is written in Java and can be accessed via the SmartCheck company website [[21](#ch22.xhtml#r505)].

### Symbolic Execution Tools

#### DART

One of the earlier tools in symbolic execution capable of performing random testing through dynamic analysis in order to find the bugs which are caused by library functions. DART checks for standard errors such as violations, assertions, crashes and non-terminations, using input with a single path testing without employing path selection mechanisms [[20](#ch22.xhtml#r504)]. The tool is openly available on GitHub. The DART software development kit includes VM, dart2js, core libraries, etc.

#### Manticore
