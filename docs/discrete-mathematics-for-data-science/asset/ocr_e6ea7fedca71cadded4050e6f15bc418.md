10 The concatenation operator varies among programming languages. It may be a dot . or a tilde ~, or possibly no character whatsoever.

The union operation is both associative and commutative.

# 9.4 A MACHINE

Programming languages are designed for the machines on which they run. Machines can be physical or logical models of computation.

One simple memory-less model of computation is known as a finite state machine, or finite automata (FA). These can be of a class of deterministic finite automata(DFA) or non-deterministic finite automata (NFA). Deterministic systems produce a predetermined output state that is always the same for given inputs. Conversely, non-deterministic systems depend on possible or probable inputs, which are not known to the system in advance.

Like digital logic, finite state machines have input state encodings and related output that can be modeled in functional form, state diagram, digraph, adjacency matrix, or truth table. The truth table used to describe FAs is called a state transition table. An FA also has the characteristics of a graph data structure, such as vertices representing states, which is described in the Branched Structures chapter.