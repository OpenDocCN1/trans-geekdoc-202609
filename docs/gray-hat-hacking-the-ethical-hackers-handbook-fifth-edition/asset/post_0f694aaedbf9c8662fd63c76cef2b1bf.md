
the different stages in fuzzing that should lead to finding more security vulnerabilities.

## Types of Fuzzers

We mentioned already that fuzzers have evolved over time and are no longer solely based on random data generation. Because fuzzing is not an exact science, experimentation with different fuzzing types and parameters is encouraged.

Following is a list of common fuzzer classifications based on the data-generation algorithms:

- Mutation fuzzers
- Generation fuzzers
- Genetic or evolutionary fuzzers

### Mutation Fuzzers

Mutation-based fuzzers, also called *dumb fuzzers*, are the simplest variant and closest to the original idea of randomizing the input data. The name comes from changing (mutating) the input data, usually in a random way. The mutated data is then used as input for the target software in order to try and trigger a software crash.

### Generation Fuzzers

Generation fuzzers are also called *grammar-based* or *white box fuzz testing*, due to prior knowledge of the internal workings of the protocol. This approach is based on the premise that efficient testing requires understanding the internal workings of the target being tested. Generation fuzzers don’t need examples of valid data inputs or protocol captures like the mutation-based ones. They are able to generate test cases based on data models that describe the structure of the data or protocol. These models are usually written as configuration files whose formats vary based on the fuzzing tools that use them.

One of the main problems with generation fuzzers is writing data models. For simple protocols or data structures that have documentation available, this is not a major problem, but such cases are rare and not so interesting because of their simplicity.

In reality, things are much more complicated, and the availability of specifications and documentation still requires significant effort to correctly translate to a fuzzing model. Things get even more complicated when software companies don’t follow the specifications and slightly modify them or even introduce new features not mentioned in the specification. In such cases, it is necessary to customize the model for the target software, which requires additional effort.

### Genetic Fuzzing

Genetic fuzzing is also called *evolutionary fuzzing* because the tool determines the best set of input tests, based on maximizing code coverage over time. Actually, the fuzzer makes notice of input mutations that reach new code blocks and saves those mutated inputs to the body (corpus) of tests. In this sense, the fuzzing tool can learn in a “survival of the fittest” manner—thus the term *genetic* or *evolutionary fuzzing*.

## Mutation Fuzzing with Peach

This section provides an overview of the Peach mutation fuzzer, which should provide you with enough information to start experimenting with fuzzing and looking for vulnerabilities.

The Peach framework can be used on Windows, Linux, and OS X operating systems. On Linux and OS X, a cross-platform .NET development framework called Mono is necessary to run Peach. In this section, we use the 64-bit version of Windows 10. Your steps and outputs may vary slightly from those in this chapter if you choose to use a different platform.

As mentioned previously, mutation fuzzing is an extremely interesting idea because it usually doesn’t require much work from the user’s perspective. A set of samples has to be chosen as input to the mutation program, and then the fuzzing can begin.

To start fuzzing with Peach, you have to create a file called Pit. Peach Pit files are XML documents that contain the entire configuration for the fuzzing session. Here is some typical information contained in a Pit file:

- General configuration: Defines things not related to the fuzzing parameters (for example, the Python path).
- Data model: Defines the structure of the data that will be fuzzed in the Peach-specification language.
- State model: Defines the state machine needed to correctly represent protocols where a simple data model is not enough to capture all the protocol specification.
- Agents and monitors: Define the way Peach will distribute the fuzzing workload and monitor the target software for signs of failure/vulnerabilities.
- Test configuration: Defines the way Peach will create each test case and what fuzzing strategies will be used to modify data.

Mutation Pits are fairly easy to create, and Peach provides several templates that can be examined and modified to suit different scenarios. Pit configurations can be created and modified using any text editor—or, more specifically, one of the XML editors. Peach documentation suggests using Microsoft Visual Studio Express, but even Notepad++ or Vim can suffice for this task.

The following is the rm_fuzz.xml Peach Pit file:

```
<?xml version="1.0" encoding="utf-8"?>
<Peach xmlns=http://peachfuzzer.com/2012/Peach
xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance
xsi:schemaLocation="http://peachfuzzer.com/2012/Peach /peach/peach.xsd">
<!-- Create data model -->
<DataModel name="TheDataModel">
<Blob/>
</DataModel>
<!-- Create state model -->
<StateModel name="TheState" initialState="Initial">
<State name="Initial">
<Action type="output">
<DataModel ref="TheDataModel"/>
<Data fileName="C:\peach3\rm_samples\*.rm" />
</Action>
<Action type="close"/>
<Action type="call" method="ScoobySnacks" publisher="Peach.Agent"/>
</State>
</StateModel>
<!-- Configure Agent -->
<Agent name="TheAgent">
<Monitor class="WindowsDebugger">
<Param name="CommandLine" value="C:\Program Files (x86)\VideoLAN\VLC\vlc.exe fuzzed.rm" />
<Param name="WinDbgPath" value="C:\Program Files (x86)\Windows Kits\10\Debuggers\x64" />
<Param name="StartOnCall" value="ScoobySnacks"/>
</Monitor>
<Monitor class="PageHeap">
<Param name="Executable" value="vlc.exe"/>
<Param name="WinDbgPath" value="C:\Program Files (x86)\Windows Kits\10\Debuggers\x64" />
</Monitor>
</Agent>
<Test name="Default">
<Agent ref="TheAgent"/>
<StateModel ref="TheState"/>
<!-- Configure a publisher -->
<Publisher class="File">
<Param name="FileName" value="fuzzed.rm"/>
</Publisher>
<!-- Configure a strategy -->
<Strategy class="RandomDeterministic"/>
<Logger class="File">
<Param name="Path" value="logs"/>
</Logger>
</Test>
</Peach>
<!-- end -->
```

The Pit file consists of several important sections that will influence and determine the fuzzing process. Following is a list of these sections and how each one influences the fuzzing process for this Pit file:

- DataModel (1 and 2): Defines the structure of data that will be fuzzed. In case of black box testing, DataModel is typically unknown and will be represented by a single data entry, <Blob/>, that describes an arbitrary binary data unit and doesn’t enforce any constraints on the data (be it values or order). If you omit the data model, Peach will not be able to determine the data types and their respective sizes, resulting in a somewhat imprecise data-modification approach. On the other hand, omitting the data model reduces the time needed to start the fuzzing. Because black box fuzzing is very quick and cheap to set up, it is usually worth it to start the black box testing while working on a better data model.

- StateModel (3 and 4): Defines the different states the data can go through during the fuzzing of the application. The state model is very simple for file fuzzing because only a single file is generated and used for testing purposes.

Fuzzing network protocols is a good example of where the state model plays an important role. To explore the different states in the protocol implementation, it is necessary to correctly traverse the state graph. Defining StateModel will instruct the fuzzer how to walk through the state graph and allow for testing more code and functionality, thus improving the chances for finding vulnerabilities.

- Agent (5 and 6): Defines the debugger that will be used to monitor the execution of the target program and collect information about crashes. The collected crash data then has to be manually reviewed and classified as relevant or irrelevant. Relevant crashes should then be reviewed again to check for exploitable conditions and to determine their value.

- Test (7 and 8): Defines configuration options relevant to the testing (fuzzing) process. In this case, it will define the filename for the generated test cases as fuzzed.rm and define logs as the logging directory containing data about program crashes.

To test that the written Pit has a valid structure, Peach offers several solutions. The first thing to do is to test and validate the Pit with the --test command, which will perform a parsing pass over the Pit file and report any problems found. Following is an example of how to test Pit XML:

```
C:\peach3>Peach.exe -t rm_fuzz.xml

[[ Peach v3.1.124.0
[[ Copyright (c) Michael Eddington

[*] Validating file [rm_fuzz.xml]... No Errors Found.
```

The following shows how to start a new Peach session with the previously created Pit file:
