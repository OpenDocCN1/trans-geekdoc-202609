```
int add(int a, int b) {
 int result = a + b;
 return result;
 }
```

```
int summation(int a, int b, int c){
 int result = add(a, b);
 return add(result, c);
 }
```

```
int main(int argc, char *argv[]){
 int a = atoi(argv[1]);
 int b = atoi(argv[2]);
 int c = atoi(argv[3]);
 print(summation(a, b, c);
 return 0;
 }
```

As can be seen, these C functions for summation and add are relatively verbose and do not convey a sequential flow of logic. Such are the traits of procedural programming languages, such as C, relative to functional programming languages.

Arguably, Forth has characteristics of the functional programming paradigm. Functional programming emphasizes what task is to be accomplished, in contrast to procedural programming, which deals more with how a task is to be accomplished. Long before the fad of functional programming, Forth was functional. Being a work of Charles (Chuck) Moore in the late 1960s, Forth may have taken inspiration from what might be considered the first functional programming language, Lisp, which was originated by John McCarthy at the Massachusetts Institute of Technology in 1958. Chuck Moore was a student of John McCarthy.

Why not use Python or R? With Python and R, the student can possess the capabilities of built-in abstract functions, without necessarily understanding the problem at hand. Because Python and R libraries exist for just about any problem, these libraries are recommended for use only after fundamentals are understood by wording them in a more natural language, such as Forth.

2J. McCarthy, “History of lisp,” Special Interest Group on Programming Languages, vol. 13, issue 8, pp. 173–185, 1978, issn: 0362-1340. doi: https://dl.acm.org/doi/10.1145/960118.800837.