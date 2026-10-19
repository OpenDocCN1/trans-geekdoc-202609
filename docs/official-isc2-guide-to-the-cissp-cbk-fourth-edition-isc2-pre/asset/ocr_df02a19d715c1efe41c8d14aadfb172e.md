between the assembly mnemonics and specific opcodes, at least the assembly files are formatted in a way that is relatively easy for humans to read rather than being strings of hexadecimal or binary numbers. You will notice in the second part of Figure 8.1, a column of codes that might almost be words: MOV (move), CMP (compare), DEC (decrement), and ADD. Assembly language added these mnemonics because "MOV to register AX" makes more sense to a programmer than simply B8h or 10111000. An assembler program also takes care of details regarding addressing in memory so that every time a minor change is made to a program, all the memory references and locations do not have to be manually changed.

With the advent of high-level (or at least higher level) languages (the so-called third generation), programming language systems split into two types. High-level languages are those where the source code is somewhat more comprehensible to people. Those who work with C may dispute this assertion, of course. These languages, in the hands of skilled programmers, can produce highly functional programs from very little source code but at the expense of legibility. The much maligned COBOL is possibly the best example. As you can see in Figure 8.2, the general structure of a COBOL program should be evident from the source code, even for those not trained in the language.

```
OPEN INPUT RESPONSE-FILE
  OUTPUT REPORT-FILE
  INITIALIZE SURVEY-RESPONSES
  PERFORM UNTIL NO-MORE-RECORDS
  READ RESPONSE-FILE
  AT END
  SET NO-MORE-RECORDS TO TRUE
  NOT AT END
  PERFORM 100-PROCESS-SURVEY
  END-READ
  END-PERFORM
begin.
display "My parents went to Vancouver and all they got"
display "for me was this crummy COBOL program!".
```

Figure 8.2 - Two sections of code from different COBOL programs. Note that the intention of the program is reasonably clear, as opposed to Figure 8.1.

Compiled languages involve two separate processes before a program is ready for execution. The application must be programmed in the source (the text or human-readable) code, and then the source must be compiled into object code that the