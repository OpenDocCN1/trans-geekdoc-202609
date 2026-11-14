
# 目录

## 前言部分
- [Preface](#part0005.html#id-preface)
- [The Origins of Go](#part0006.html#id-theoriginsofgo)
- [The Go Project](#part0007.html#id-thegoproject)
- [Organization of the Book](#part0008.html#id-organizationofthebook)
- [Where to Find More Information](#part0009.html#id-wheretofindmoreinformation)
- [Acknowledgments](#part0010.html#id-acknowledgments)

## 第1章 Tutorial
- [1.1. Hello, World](#part0012.html#id-helloworld)
- [1.2. Command-Line Arguments](#part0013.html#id-commandlinearguments)
- [1.3. Finding Duplicate Lines](#part0014.html#id-findingduplicatelines)
- [1.4. Animated GIFs](#part0015.html#id-animatedgifs)
- [1.5. Fetching a URL](#part0016.html#id-fetchingaurl)
- [1.6. Fetching URLs Concurrently](#part0017.html#id-fetchingurlsconcurrently)
- [1.7. A Web Server](#part0018.html#id-awebserver)
- [1.8. Loose Ends](#part0019.html#id-looseends)

## 第2章 Program Structure
- [2.1. Names](#part0021.html#id-names)
- [2.2. Declarations](#part0022.html#id-declarations)
- [2.3. Variables](#part0023.html#id-variables)
- [2.4. Assignments](#part0024.html#id-assignments)
- [2.5. Type Declarations](#part0025.html#id-typedeclarations)
- [2.6. Packages and Files](#part0026.html#id-packagesandfiles)
- [2.7. Scope](#part0027.html#id-scope)

## 第3章 Basic Data Types
- [3.1. Integers](#part0029.html#id-integers)
- [3.2. Floating-Point Numbers](#part0030.html#id-floatingpointnumbers)
- [3.3. Complex Numbers](#part0031.html#id-complexnumbers)
- [3.4. Booleans](#part0032.html#id-booleans)
- [3.5. Strings](#part0033.html#id-strings)
- [3.6. Constants](#part0034.html#id-constants)

## 第4章 Composite Types
- [4.1. Arrays](#part0036.html#id-arrays)
- [4.2. Slices](#part0037.html#id-slices)
- [4.3. Maps](#part0038.html#id-maps)
- [4.4. Structs](#part0039.html#id-structs)
- [4.5. JSON](#part0040.html#id-json)
- [4.6. Text and HTML Templates](#part0041.html#id-template)

## 第5章 Functions
- [5.1. Function Declarations](#part0043.html#id-functiondeclarations)
- [5.2. Recursion](#part0044.html#id-recursion)
- [5.3. Multiple Return Values](#part0045.html#id-multiplereturnvalues)
- [5.4. Errors](#part0046.html#id-errors)
- [5.5. Function Values](#part0047.html#id-functionvalues)
- [5.6. Anonymous Functions](#part0048.html#id-anonymousfunctions)
- [5.7. Variadic Functions](#part0049.html#id-variadicfunctions)
- [5.8. Deferred Function Calls](#part0050.html#id-deferredfunctioncalls)
- [5.9. Panic](#part0051.html#id-panic)
- [5.10. Recover](#part0052.html#id-recover)

## 第6章 Methods
- [6.1. Method Declarations](#part0054.html#id-methoddeclarations)
- [6.2. Methods with a Pointer Receiver](#part0055.html#id-methodswithapointerreceiver)
- [6.3. Composing Types by Struct Embedding](#part0056.html#id-composition)
- [6.4. Method Values and Expressions](#part0057.html#id-methodvaluesandexpressions)
- [6.5. Example: Bit Vector Type](#part0058.html#id-intset)
- [6.6. Encapsulation](#part0059.html#id-encapsulation)

## 第7章 Interfaces
- [7.1. Interfaces as Contracts](#part0061.html#id-interfacesascontracts)
- [7.2. Interface Types](#part0062.html#id-interfacetypes)
- [7.3. Interface Satisfaction](#part0063.html#id-interfacesatisfaction)
- [7.4. Parsing Flags with `flag.Value`](#part0064.html#id-flagvalue)
- [7.5. Interface Values](#part0065.html#id-interfacevalues)
- [7.6. Sorting with `sort.Interface`](#part0066.html#id-sorting)
- [7.7. The `http.Handler` Interface](#part0067.html#id-httphandler)
- [7.8. The `error` Interface](#part0068.html#id-theerrorinterface)
- [7.9. Example: Expression Evaluator](#part0069.html#id-eval)
- [7.10. Type Assertions](#part0070.html#id-typeassertions)
- [7.11. Discriminating Errors with Type Assertions](#part0071.html#id-discriminatingerrors)
- [7.12. Querying Behaviors with Interface Type Assertions](#part0072.html#id-queryingbehavior)
- [7.13. Type Switches](#part0073.html#id-typeswitches)
- [7.14. Example: Token-Based XML Decoding](#part0074.html#id-exampletokenbasedxmldecoding)
- [7.15. A Few Words of Advice](#part0075.html#id-afewwordsofadvice)

## 第8章 Goroutines and Channels
- [8.1. Goroutines](#part0077.html#id-goroutines)
- [8.2. Example: Concurrent Clock Server](#part0078.html#id-exampleconcurrentclockserver)
- [8.3. Example: Concurrent Echo Server](#part0079.html#id-exampleconcurrentechoserver)
- [8.4. Channels](#part0080.html#id-chan)
- [8.5. Looping in Parallel](#part0081.html#id-loopinginparallel)
- [8.6. Example: Concurrent Web Crawler](#part0082.html#id-exampleconcurrentwebcrawler)
- [8.7. Multiplexing with `select`](#part0083.html#id-multiplexingwithselect)
- [8.8. Example: Concurrent Directory Traversal](#part0084.html#id-exampleconcurrentdirectorytraversal)
- [8.9. Cancellation](#part0085.html#id-cancellation)
- [8.10. Example: Chat Server](#part0086.html#id-examplechatserver)

## 第9章 Concurrency with Shared Variables
- [9.1. Race Conditions](#part0088.html#id-raceconditions)
- [9.2. Mutual Exclusion: `sync.Mutex`](#part0089.html#id-mutex)
- [9.3. Read/Write Mutexes: `sync.RWMutex`](#part0090.html#id-readwritemutexessyncrwmutex)
- [9.4. Memory Synchronization](#part0091.html#id-memorysynchronization)
- [9.5. Lazy Initialization: `sync.Once`](#part0092.html#id-lazyinitializationsynconce)
- [9.6. The Race Detector](#part0093.html#id-theracedetector)
- [9.7. Example: Concurrent Non-Blocking Cache](#part0094.html#id-cache)
- [9.8. Goroutines and Threads](#part0095.html#id-goroutinesandthreads)

## 第10章 Packages and the Go Tool
- [10.1. Introduction](#part0097.html#id-pkgintro)
- [10.2. Import Paths](#part0098.html#id-importpaths)
- [10.3. The Package Declaration](#part0099.html#id-thepackagedeclaration)
- [10.4. Import Declarations](#part0100.html#id-importdeclarations)
- [10.5. Blank Imports](#part0101.html#id-blankimports)
- [10.6. Packages and Naming](#part0102.html#id-packagesandnaming)
- [10.7. The Go Tool](#part0103.html#id-thegotool)

## 第11章 Testing
- [11.1. The `go test` Tool](#part0105.html#id-thegotesttool)
- [11.2. `Test` Functions](#part0106.html#id-testfunctions)
- [11.3. Coverage](#part0107.html#id-coverage)
- [11.4. `Benchmark` Functions](#part0108.html#id-benchmarkfunctions)
- [11.5. Profiling](#part0109.html#id-profiling)
- [11.6. `Example` Functions](#part0110.html#id-examplefunctions)

## 第12章 Reflection
- [12.1. Why Reflection?](#part0112.html#id-whyreflection)
- [12.2. `reflect.Type` and `reflect.Value`](#part0113.html#id-reflecttypeandreflectvalue)
- [12.3. `Display`, a Recursive Value Printer](#part0114.html#id-display)
- [12.4. Example: Encoding S-Expressions](#part0115.html#id-exampleencodingsexpressions)
- [12.5. Setting Variables with `reflect.Value`](#part0116.html#id-reflectvar)
- [12.6. Example: Decoding S-Expressions](#part0117.html#id-exampledecodingsexpressions)
- [12.7. Accessing Struct Field Tags](#part0118.html#id-accessingstructfieldtags)
- [12.8. Displaying the Methods of a Type](#part0119.html#id-displayingthemethodsofatype)
- [12.9. A Word of Caution](#part0120.html#id-awordofcaution)

## 第13章 Low-Level Programming
- [13.1. `unsafe.Sizeof`, `Alignof`, and `Offsetof`](#part0122.html#id-sizeof)
- [13.2. `unsafe.Pointer`](#part0123.html#id-unsafepointer)
- [13.3. Example: Deep Equivalence](#part0124.html#id-exampledeepequivalence)
- [13.4. Calling C Code with `cgo`](#part0125.html#id-callingccodewithcgo)
- [13.5. Another Word of Caution](#part0126.html#id-anotherwordofcaution)

# Preface

> “Go is an open source programming language that makes it easy to build simple, reliable, and efficient software.” (From the Go web site at `golang.org`)
