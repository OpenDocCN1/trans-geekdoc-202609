its current state; it may transition to the same state or to another one. When your program recognizes a proper sequence of key events, it transitions to a final state.

*The data definition on the right uses the naming technique introduced in exercise 61.*

For a sequence-recognition problem, states typically represent the letters that the machine expects to see next; see figure 36 for a data definition. Take a look at the last state, which says an illegal input has been encountered. Figure 37 shows how to think of these states and their relationships in a diagrammatic manner. Each node corresponds to one of the four finite states; each arrow specifies which KeyEvent causes the program to transition from one state to another.

| conventional | defined abbreviations |
| :--- | :--- |
| ; ExpectsToSee.v1 is one of: | ; ExpectsToSee.v2 is one of: |
| ; -- "start, expect an 'a'" | ; -- AA |
| ; -- "expect 'b', 'c', or 'd'" | ; -- BB |
| ; -- "finished" | ; -- DD |
| ; -- "error, illegal key" | ; -- ER |
| | (define AA "start, ...") |
| | (define BB "expect ...") |
| | (define DD "finished") |
| | (define ER "error, ...") |

# Figure 36: Two ways of writing a data definition for FSMs

![](bbox=[0.26, 0.66, 0.73, 0.82])

# Figure 37: A finite state machine as a diagram