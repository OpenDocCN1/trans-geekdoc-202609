Here two neurons acting.
i. Cell sensitive to position of line
ii. Cell turns on inside quotes

**Cell sensitive to position line (detecting the end of the line):** We can see that when we get towards the end of the line it activating. How does when it's the end of the line?

+   - In this text we have about 80 symbols per line approximately, the neuron is counting how many symbols has passed and it to predict the new line character (an invisible character. i.e. "u") is going to appear.

**Cell that turns on inside quotes:** You've got a cell that turns on inside quotes. It detects that there is a quotation mark.

+   - From the color code (red = turn on), we can see the cell is activating outside the quotes. This cell may acting doing one way or other, it's activating inside the quotes or outside the quotes. It is keeping track of what's happening.

+   - So very similar to what we discuss previously, where we were keeping track of the subject.

+   - The subject could be gender (male or female) or understand things like it's a singular or plural that would effect our version in translation.

+   - Same thing is happening here, the cell detects quotes, if it's inside or outside quotes because that the rest of the text. So the cell can find a quotation mark matching its output quotation mark for the rest.

# **Example 2:** Example of Trained RNN on programming language source code. Here we got some code of the Linux OS.

Cell that activates if it statements:

```
int sig = signal(struct sigpending *pending, struct sigset_t *mask, 
int sig = next_signal(sigpending, *mask);
if (current_notifier) {
    if (mask(current_notifier->mask, sig)) {
        current_notifier->data = sig;
    }
    current_notifier->flag |= SIG_SUSPENDING;
}
return sig;
}
collect_signal(sig, pending, info);
return sig;
```

```
#ifdef CONFIG_AUDIT_SYSC
static inline int audit_match_class_bits(int class, u32 *mask) {
if (classes[class]) {
for (int i=0; i < AUDIT_BITMASK_SIZE; i++) {
    if (mask[i] & classes[i]) return 1;
}
}
return 0;
}
```

![](bbox=[0.673, 0.712, 0.903, 0.725])

**Cell activates if the it statements:**

+   - We can see that a cell activates if it statements.
- If we closely see then we can see the cell is actually active on the it conditions. It detects the curly-braces {} and normal braces ''.
- That's how it detects the it statements.

**Cell is sensitive to the depth of an expression:** In the image above we can also see that the cell is sensitive to how deep you are of a nested expression.

+   - As we go deeper and the expression gets more and nested, this cell keep track of that (notice the red-color gets deeper in the p of nested expression)
- So the cell uses using's memory to keep track of that.
- It's doing by tracking the curly-brace '{}' and indent.