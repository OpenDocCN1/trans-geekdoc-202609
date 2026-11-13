
### 5.4.3 Gastap

Gastap [80] was developed in 2018 and is basically a static analysis tool. This tool analyzes the EVM byte code or Solidity code or disassembled byte code of EVM. For its functions, it deduces the requirements of gas bounds and then compares the gas limit paid and deduced gas requirement.

### 5.4.4 Remix IDE

Remix IDE [81] is an open-access tool that analyzes smart contracts in Solidity code and provides an easy way to write the code. It was invented in 2016 and is a JavaScript implementation of EVM. It is based on browser and is a user’s interface. The source code is present in the GitHub Repository. It has the Solidity static analysis plugin that has 21 analysis modules under four different categories: gas and economy, security, ERC, and miscellaneous, in Remix IDE v0.10.1.

### 5.4.5 Slither

Slither [82] was invented in 2018 and is an open-source tool which is developed in the Python language. It inputs Solidity code for analysis and also uses an intermediate representation of SlithIR. To detect vulnerabilities, Slither analyzes data flow of the tracking approaches. The open version predicts almost 20 bugs too.

### 5.4.6 SmartAnvil

SmartAnvil [83], invented in 2018, is an open-source platform which was developed in Smalltalk. For smart contract analysis, it is constructed using various modules. This platform has three component tools, such as SmaCC-Solidity, which is a parser used to support static code of Solidity smart contract. Second is SmartInspect, which is a component usually used to detect the Solidity smart contract internal state, and third is Ukulele, which helps fetch required data using this query language from the blockchain.

### 5.4.7 SmartBugs

SmartBugs [84] was invented in 2020 and is a publicly available static analysis framework that is executed in the Python language. For analyzing the smart contracts, it supports ten tools. It has five components: tools dockers image, command-line interpreter, SmartBugs runner, tools configuration, and dataset.

### 5.4.8 SmartCheck

SmartCheck [85] was developed in Java and invented in 2017. It is an open-source, publicly available static analysis tool. To analyze the smart contract, SmartCheck employs syntactical analysis and lexical analysis approaches. Using custom Solidity grammar and ANTLR (a parser generator) for an intermediate representation, the generation of an XML parse tree is done. For detecting vulnerabilities, usage of XPath queries is done so as to process the intermediate representation. It detects almost 20 bugs, like style guide violation, implicit visibility level, etc.

### 5.4.9 DefectChecker

DefectChecker [86] was deployed in 2021 and was developed in the Java language. It has four sections for processing: inputter, defect identifier, feature detector, and CFG builder. It takes byte code as an input and then extracts the opcodes as output. For symbolic execution, all the opcodes are clustered and categorized accordingly into different categories. Finally, for detection of defects in the smart contract, control flow graph is constructed.

### 5.4.10 GasChecker

GasChecker [87] was invented in 2020. The tool does analyses on the basis of ten programming patterns or gas inefficient codes.

### 5.4.11 Gasper

Gasper [88] is written in the Python language. It was invented in 2017. It helps in gas cost analysis of patterns in smart contracts that are based on the EVM byte code. It identifies seven gas cost patterns as costly loop-related patterns and unnecessary code-related patterns. Thus, it can be concluded that the Gasper tool is based on the execution on symbolics and is a pattern checker based on gas cost that works on byte code.

### 5.4.12 HoneyBadger

HoneyBadger [89] is an open-source, publicly available tool which was developed using the Python language. For honeypot smart contracts, it performs systematic analysis. It has a structure consisting of analysis pipeline of three different types, named honeypot analysis, symbolic analysis, and cash flow analysis. The satisfiability of constraints is checked by each and every type of analysis using Z3 SMT solver.

### 5.4.13 MadMax

MadMax [90] is an openly available public source of static analysis tool which came into existence in 2018. For static analysis performance, it uses Gigahose IR. The first one includes a control-flow-analysis decompiler, and the last is queries. Thus, it helps identify the concepts related to specific high-level area.

### 5.4.14 Mythril

Mythril [91] is an open-source analysis, publicly available tool which was deployed and executed by ConsenSys using Python programming language in 2017. For input, EVM byte code is provided for analysis in the tool. Mythril helps in the analyses of the important Ethereum smart contracts that are basically based on blockchain and also helps improve performance on platforms of blockchain.

### 5.4.15 Oyente

Oyente [92] is a static analysis and open-source, publicly available tool which came into existence in 2016 and is deployed and executed in Python. For analyses of smart contracts, it employs symbolic execution and also helps in statistical and path-by-path analyses of the program code. From consideration to eliminate provably the infeasible traces, the Validator and Explorer uses Z3 bit-vector solver.

### 5.4.16 Securify

Securify [93] is a static analysis and open-source, publicly available tool which is executed and deployed in the Java language and was invented in the year 2018. To check whether it is safe or not, it helps checks smart contract behavior associated to a particular feature or parameter and also helps in a fully automated security analysis. The input is byte code of EVM and security patterns set for the tool.

### 5.4.17 Vandal

Vandal [94] is a static analysis open-source, publicly available tool which is implemented in the Python language and was invented in 2018. Its analysis pipeline helps in the transformation of the EVM byte code into semantic logics relation. It shows vulnerability analysis into declarative language of soufflé. Vandal's analysis pipeline has several stages: extractor, scrapper, decompiler, and disassembler, to produce the logic relations.

### 5.4.18 Manticore

Manticore [95] is a dynamic analysis open-source, publicly available tool which is executed in Python in the year 2017. It is a symbolic-type execution analysis tool that is dynamic in nature that allows user customization for analysis purposes in Manticore. Its architecture has components which are the core engine and Ethereum execution modules.

## 5.5 Building Smart Contracts

Smart contracts are the simple programs that are usually stored on a blockchain and execute when required conditions are met. They include participants and don’t involve any third-party intermediary or time loss. [96]

Smart contract uses simple “if-else” statements to write codes on blockchain. A specified computer network gets involved and helps in executing the code. This helps in releasing funds to the actual parties involved, sending notifications, registering a vehicle, or issuing a ticket. The blockchain is regularly updated after transaction is completed. Thus, this helps in saving of transaction without any fear of alteration on blockchain.

Some of the benefits of smart contracts are discussed in what follows.

### 5.5.1 Speed and Accuracy

The contract executes immediately, soon after the conditions are met. Since the smart contracts are automated and digital, there’s no need for any manual paperwork and filling-in documents.

### 5.5.2 Transparency and Trust

Due to the non-involvement of any third party and the usage of encrypted records of transactions, there’s no chance of any alteration of information. Thus, this helps in building trust and transparency among users.

![](img/f7b65e1b6017d6bb4f421d92025cbdc6_141_0.png)

FIGURE 5.1
Healthcare smart contract with LiverTotalBilirubinfunction().

### 5.5.3 Security

The transaction stored on blockchain is encrypted and is hard to hack. Since each record is well connected to the subsequent and previous records on a ledger, it makes it difficult for hackers to alter a single record.

### 5.5.4 Savings

Smart contracts don’t involve any intermediary and helps handle transactions without any time delays and fees.

Figure 5.1 shows the working of a healthcare smart contract that includes the LiverTotalBilirubinfunction() in Remix IDE [97]. This function helps in easy analysis of the patient’s amount of total bilirubin in liver. When doctor checks his patient, he enters the amount of bilirubin in the form of ethers along with the patient’s address. The function then checks various parameters. Such as:

- 1. If the doctor is already registered in the hospital.
- 2. If the patient is already registered in the hospital.
- 3. If the particular patient is authorized to this particular doctor.
- 4. If the doctor specialization, for example, “pathologist,” is same as the doctor the patient wants to concern.
- 5. After all these conditions are met, the function checks the amount of bilirubin. If the amount is equal to 12 mg per deciliter, then the patient has “Normal Bilirubin in mg per dL.” If the amount is greater than 12 mg per deciliter, then the patient has “Higher Bilirubin in mg per dL.” Else, if both the conditions turn false, then the patient has “Lower Bilirubin in mg per dL.”

## 5.6 Solidity Static Analysis

After the writing of smart contracts in Remix IDE, the vulnerabilities are usually generated. Thus, it becomes important to reduce these vulnerabilities and debug the code. To do so, various tools are provided, and one such tool is Solidity static analysis [98].
