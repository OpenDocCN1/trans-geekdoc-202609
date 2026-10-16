
Analyzing a program's control flow can make it easier to quickly understand what is happening inside of code. Getting good at recognizing these flows quickly can vastly improve your reverse engineering ability.

## Ghidra

Ghidra is a static analysis tool released in 2019 by the NSA. It has many similarities to IDA, but unlike IDA, it is free and open source. In many situations, Ghidra is an adequate replacement to IDA.

IDA has a much longer reputation in the space, but Ghidra is also immensely powerful and in many cases has a lot of the same features. This example demos IDA given its long history in the reverse engineering space, but everything shown can also be done in Ghidra. The tools are similar enough that skills in one will often transfer over. Try Ghidra out for some of the later, open-ended labs in this book and your own practice.

## Lab: Cracking with IDA

This lab takes a look at a more complex application in IDA. Labs and all associated instructions can be found in their corresponding folder here:

`/path.to.xxx`https://github.com/DazzleCatDuo/X86-SOFTWARE-REVERSE-ENGINEERING-CRACKING-AND-COUNTER-MEASURES

For this lab, please locate Lab Cracking with IDA and follow the provided instructions.

### Skills

This lab practices using IDA to crack large, real-world applications. The goal is to learn to quickly identify points of interest and to prioritize multiple cracking approaches.

### Takeaways

Real-world programs are too large for uniform, fine-grained analysis. Triage is critical to finding the points of interest.

Multiple opportunities are usually available to a cracker. Selecting which to pursue can save (or cost) significant time.

## Summary

This chapter explored some of the most widely used tools for reversing and cracking. Take the time to become familiar with them. It'll pay off in the long run!

# CHAPTER 12  

Defense

How do you defend against cracking? To start, it's essential to have a good key check design (don't pull a *Starcraft*/*Half-Life*). From there, you can implement additional defensive options.

However, it's important to remember that there is no such thing as uncrackable software. As a defender, your job is to slow attackers down in the critical parts of your software and make them frustrated enough they go to a different target.

Like many things in cybersecurity, you just don't want to be the low-hanging fruit. “When swimming in shark-infested water, you don't have to be the fastest…just faster than the guy next to you.”

## Obfuscation

*Obfuscation* is the practice of hiding the intended meaning of code by purposefully making logic ambiguous and unclear. It can be valuable for slowing reverse engineering to do the following:

*   Slow cracking

*   Slow tampering

*   Protect intellectual property

Done well, obfuscation can make code essentially unreadable. For example, the following C code (available from `www.ioccc.org/1988/phillipps.c`), when compiled and run, prints out the lyrics to the entire 12 days of Christmas song. It was one of the IOCCC winners, which is a competition to hand-obfuscate code. Looking at it makes my brain hurt, and I can't guess at how long I'd have to reverse engineer the code before I figured out what it did.

```
#include <stdio.h>
main(t,_,a)
char
*
a;
{
       return!
 0<t?
t<3?
 main(-79,-13,a+
main(-87,1-_,
main(-86, 0, a+1 )
 +a)):
 1,
t<_?
main(t+1, _, a )
:3,
 main ( -94, -27+t, a )
&&t == 2 ?_
<13 ?
 main ( 2, _+1, "%s %d %d\n" )
 :9:16:
t<0?
t<-72?
main( _, t,
"@n'+,#'/*{}w+/w#cdnr/+,{}r/*de}+,/*{*+,/w{%+,/w#q#n+,/#{l,+,
       /n{n+,/+#n+,/#;\
#q#n+,/+k#;*+,/'r :'d*'3,}{w+K w'K:'+}e#';dq#'l q#'+d'K#!
      /+k#;\
q#'r}eKK#}w'r}eKK{nl]'/#;#q#n'){)#}w'){){nl]'/+#n';d}rw' 
      i;# ){nl]!/n{n#'; \
r{#w'r nc{nl]/#{l,+'K {rw' iK{;[{nl]'/w#q#\
\
n'wk nw' iwk{KK{nl]!/w{%'l##w#' i; :{nl]'/*{q#'ld;r'}{nlwb!/*de}'c ;;\
{nl'-{}rw]'/+,}##'*}#nc,',#nw]'/+kd'+e}+;\
#'rdq#w! nr'/ ') }+}{rl#'{n' ')# }'+}##(!!/")
:
t<-50?
_==*a ?
putchar(31[a]):
 main(-65,_,a+1)
:
main((*a == '/') + t, _, a + 1 )
:
 0<t?
 main ( 2, 2, "%s")
:*a=='/'||
 main(0,
 main(-61,*a, "!ek;dc i@bK'(q)-[w]*%n+r3#l,{}:\nuwloca-O;m .vpbks,
       fxntdCeghiry") 
,a+1);}
```

The concept of obfuscation has also made its way into popular culture. The following quotes are from a scene in one of the James Bond movies, *Skyfall* when Q is attempting to get into Silva's laptop.

*   “There are algorithms and encryptions and asymmetrics!”

*   “Looks like obfuscated code to conceal its true purpose. Security through obscurity!”

Obfuscations can be applied by hand or automatically to a program at various stages of its life cycle, including the following:

*   Source code

*   Bytecode

*   Object code

*   Binary executable code

### Evaluating Obfuscation

When evaluating options for obfuscation, there are a few different factors to consider:

*   **Potency:** How much obfuscation is applied to the program

*   **Resilience:** How well-obfuscated code holds up to attack from reverse engineering tools

*   **Stealth:** How well-obfuscated code blends in with the rest of the program

*   **Cost:** Performance penalty of an obfuscated application

In general, these factors tend to work against each other. For example, the more potent the obfuscation is, the less stealthy it typically is.

In practice, performance cost is often the limiting factor. However, almost all obfuscations allow some degree of scaling/tuning based on requirements.

### Automated Obfuscation

Obfuscation can be performed manually. However, it's almost always better to use tools to obfuscate the code. Some of the common obfuscation techniques include the following:

*   Name mangling

*   String encryption

*   Control flow obfuscation 

    *   Control flow flattening

    *   Opaque predicates

*   Instruction substitution

#### ***Name Mangling***

*Name mangling* involves obfuscating function and variable names. This can be done a few different ways, including the following:

*   Replace with gibberish (`get_key` -> `aVJ230AM`)

*   Replace with misleading name (`get_key` -> `draw_screen`)

*   Replace with nondescriptive name (`get_key` -> `a`)

After mangling, the purpose of functions and variables is no longer immediately apparent. For example, consider the following code sample:

```
public static void SelectionSort <T> (T[] data, int size) 
       where T: IComparable
{
       for (int num1 = size – 1; num1>= 1; num1--)
       {
             T local1 = data[0];
             int num2 = 0;
             for (int num3 = 1; num3 <= num1; num3++)
             {
                    if (data[num3].CompareTo(local1)> 0)
                    {
                          local1 = data[num3];
                          num2 = num3;
                    }
             }
             T local2 = data[num2];
             data[num2] = data[num1];
             data[num1] = local2;
       }
} 
```

After mangling, this might look something like the following:

```
public static void a <a> (a[] A_0, int A_1) where a:IComparable
{
       int num1 = A_1 – 1;
Label_004D:
       if (num1 < 1)
       {
             return;
       }
       a local1 A_0[0];
       int num2 = 0;
       int num3 = 1;
       while(true)
       {
             if (num3 <= num1)
             {
                    if (A_0[num3].CompareTo(local1)> 0)
                    {
                          local1 = A_0[num3];
                          num2 = num3;
                    }
             }
             else
             {
                    a local2 = A_0[num2];
                    A_0[num2] = A_0[num1];
                    A_0[num1] = local2;
                    num1--;
                    goto Label_004D;
             }
             num3++;
       }
}
```

In the original, it is relatively easy to determine that the code is a sort algorithm even without the function name. However, doing so after mangling is much harder.

#### ***String Encryption***
