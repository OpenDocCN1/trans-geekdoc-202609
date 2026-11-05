
To do its job properly, the compiler needs to know about the data types used in the TypeScript code. Data types can be provided in declaration files (`*.d.ts`), which will be discussed in a later section. The most important declaration file is the main library, `lib.d.ts`, which declares basic types like `Array`, `Number`, and `String`. If `noLib` is set in `tsconfig.json`, the compiler won't be able to access these types.

The compiler can access high-level libraries besides the main library, such as type definitions for the document object model (DOM) and advanced versions of ECMAScript. This becomes very important if TypeScript code includes features like `Promises` and `TypedArrays`. To enable access, the `lib` flag can be set in the following way:

```
"compilerOptions": {
    …
    "lib": [ "dom", "esnext" ],
    …
}
```

As a later section explains, you can install additional libraries that declare types for different platforms and toolsets. This is particularly important because WebGPU's types aren't defined in any of TypeScript's built-in libraries. To alert the compiler, these libraries need to be identified with the `types` flag in `tsconfig.json`.

If `alwaysStrict` is set to true, browsers will run the script in strict mode. This mode treats mistakes as errors and prevents the creation of accidental global variables. It also throws an error if a JavaScript object contains duplicate properties.

## EXAMPLE APPLICATION—INTRODUCTION TO TypeScript

Before delving into the technical details of TypeScript, it's a good idea to build a simple project. The `AppA_HelloTS` project contains three files needed to build the `hello_ts` application:

* `appa_hello.ts`—TypeScript code to be compiled to JavaScript (`appa_hello.js`)
* `tsconfig.json`—Configures the compilation process
* `index.html`—Web page that imports the compiled code

Once you understand how to build and run this application, you'll have no trouble working with more complex TypeScript projects.

### Compiler Configuration

The TypeScript compiler reads configuration settings from `tsconfig.json`. Its content is given as follows:

```
{
    "files": [ "appa_hello.ts" ],
    "compilerOptions": {
        "target": "es2021",  
        "removeComments": true,
        "alwaysStrict": true,
        "noEmitOnError": true, 
        "noUnusedLocals": true,
        "noUnusedParameters": true
    }
}
```

This tells the compiler that the only file to compile is `appa_hello.ts`, which is located in the current directory. When it performs the compilation, the compiler should generate JavaScript according to the ECMAScript 2021 specification. Because `alwaysStrict` is set, the generated code will execute in strict mode.

The `noEmitOnError` field tells the compiler not to generate JavaScript if an error occurs. Because `noUnusedLocals` and `noUnusedParameters` are set to true, the compiler will check for unused declarations.

### Source Code

The code in `hello.ts` file isn't particularly impressive, but it demonstrates an important feature of TypeScript. Its content is given as follows:

```
class HelloTS {
    public printMessage() {
        document.write("Hello TypeScript!");
    }
}

let hello: HelloTS = new HelloTS();
hello.printMessage();
```

This defines a TypeScript class named `HelloTS` which has a method named `printMessage`. If you're not familiar with classes and methods, don't be concerned. A later section in this appendix discusses classes in detail.

To build this code, go to the project's directory and enter `tsc` on the command line. The compiler will convert the TypeScript to JavaScript and place the resulting code in `appa_hello.js`. If you open `index.html` in a browser, the web page will display Hello TypeScript!

## FUNDAMENTAL DATA TYPES OF TypeScript

TypeScript allows you to set a variable's type in its declaration. This is an optional feature, and the type specifications disappear when the code is compiled into JavaScript. But they provide one major advantage: *type-checking*. If a TypeScript variable of one type is set to a value of another type, the compiler will flag an error.

An example will make this clear. In the following code, the first line sets `x` equal to a number and the second line sets it equal to a string:

```
var x = 5;
x = "Hello";
```

This is acceptable in JavaScript and TypeScript, but TypeScript makes it possible to specifically identify `x` as a number. Consider this code:

```
var x: number;
x = "Hello";
```

The first line specifies that `x` is a number. When the code is compiled, the compiler recognizes that the second line is setting `x` equal to a string, and it will report an error.

Type-checking serves three main purposes:

* Early error discovery—The compiler reports errors at compile-time so that you don't have to figure them out at run-time.
* Tooling—Editors can analyze text better when variables have types. This affects features like code completion, error-checking, and syntax coloring.
* Readability—When a variable has a type, it's easier to understand the purpose it serves.

Setting a variable's type involves following the variable's name with a colon and the desired type. A general declaration has the following form:

```
var <name>: <type>;
```

If the variable needs to be initialized, the declaration's form can be given as follows:

```
var <name>: <type> = <value>;
```

When an untyped variable is initialized, the compiler automatically sets the variable's type to that of the value. In other words, if a variable is initialized to a value, there's no need to define its type.

A variable's type can be set to a custom type or a predefined TypeScript type. A later section discusses custom types, which include classes and interfaces. This section focuses on TypeScript's built-in types, which include `boolean`, `number`, `string`, `array`, `tuple`, `Object`, `any`, `undefined`, and `null`.

### The Boolean Type

Of TypeScript's predefined types, `boolean` is the easiest to use and understand. A boolean variable can be set to one of two values: true or false. As an example, the following code declares a boolean variable named `check` and initializes its value to true:

```
const check: boolean = true;
```

A boolean variable can be set equal to any operation that returns a boolean value. These operations include comparison operations (`>`, `<`, `>=`, `<=`, `==`, `!==`, and `===`) and logical operations (`&&`, `||`, and `!`). The following examples demonstrate how boolean variables can be declared and initialized:

* `const x: boolean = 5 > 3;`
* `const y: boolean = "a" !== "b";`
* `const z: boolean = ((3 < 5) && ("a" != "b"));`

JavaScript provides two operators for testing equality: `==` and `===`. The difference is that `x == y` returns true if `x` and `y` have the same value and `x === y` returns true if `x` and `y` have the same value and the same type.

### The Number Type

In TypeScript, integers and floating-point values belong to the `number` type, regardless of their sign or size. This is shown in the following examples, which declare and initialize three number values:

```
let three: number = 3;
let pi: number = 3.14159;
let avogadro: number = 6.022e-23;
```

As in JavaScript, every number in TypeScript is considered to be a floating-point value. There are no integer types or integer-specific operations. Numbers are stored as 64-bit double-precision values in accordance with the IEEE-754 standard. Values can be given using fixed-point notation (0.01) or exponential notation (6.02e-23).

TypeScript supports literal values in different bases. That is, TypeScript recognizes hexadecimal (`0x10`), octal (`0o20`), and binary (`0b10000`), in addition to decimal.

TypeScript provides special number values that can be used in code. Five of them are given as follows:

* `Number.MAX_VALUE`—the largest possible number value (about 1.7977e+308)
* `Number.MIN_VALUE`—the smallest possible number value (equals 5.0e−324)
* `Number.POSITIVE_INFINITY`—positive infinity (returned when a positive value is too large to be stored)
