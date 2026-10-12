
### [20](#47_Chapter39.xhtml#fn2-20)
For ticket-selling purposes, there are three categories at a certain theater.

![images](images/f086-01.jpg)

Which of the following code segments will assign the correct string to `category` for a given integer `age`?

![images](images/f086-02.jpg)

(A) I only
(B) II only
(C) III only
(D) II and III only
(E) I, II, and III

### [21](#47_Chapter39.xhtml#fn2-21)
What output will be produced by this code segment? (Ignore spacing.)

![images](images/f086-05.jpg)

![images](images/f086-06.jpg)

### [22](#47_Chapter39.xhtml#fn2-22)
Which of the following program fragments will produce this output? (Ignore spacing.)

```
2 - - - - -
- 4 - - - -
- - 6 - - -
- - - 8 - -
- - - - 10 -
- - - - - 12
```

![images](images/f087-02.jpg)

(A) I only
(B) II only
(C) III only
(D) I and II only
(E) I, II, and III

### [23](#47_Chapter39.xhtml#fn2-23)
Consider this program segment.

![images](images/f087-05.jpg)

Which is a true statement about the segment?

I. If `100` ≤ `num` ≤ `1000` initially, the final value of `newNum` must be in the range `10` ≤ `newNum` ≤ `100`.
II. There is no initial value of `num` that will cause an infinite `while` loop.
III. If `num` ≤ `10` initially, `newNum` will have a final value of `0`.

(A) I only
(B) II only
(C) III only
(D) II and III only
(E) I, II, and III

### [24](#47_Chapter39.xhtml#fn2-24)
Consider the method `reverse`.

![images](images/f088-01.jpg)

Which of the following replacements for `/* code segment */` would cause the method to work as intended?

![images](images/f088-02.jpg)

(A) I only
(B) II only
(C) I and II only
(D) II and III only
(E) I and III only

### [Answer Explanations](#05_Contents.xhtml#rsec58)

[1](#47_Chapter39.xhtml#rfn2-1). **(B)** When `x` is converted to an integer, as in segment I, information is lost. Java requires that an explicit cast to an `int` be made, as in segment II. Note that segment II will cause `x` to be truncated: The value stored in `y` is `14`. By requiring the explicit cast, Java doesn’t let you do this accidentally. In segment III, `y` will contain the value `14.0`. No explicit cast to a `double` is required since no information is lost.

[2](#47_Chapter39.xhtml#rfn2-2). **(E)** The string argument contains two escape sequences: `\\`, which means print a backslash (`\`), and `\n`, which means go to a new line. Choice E is the only choice that does both of these.

[3](#47_Chapter39.xhtml#rfn2-3). **(D)** Short-circuit evaluation of the boolean expression will occur. The expression `(n != 0)` will evaluate to `false`, which makes the entire boolean expression `false`. Therefore the expression `(x / n > 100)` will not be evaluated. Hence no division by zero will occur, which would have caused an `ArithmeticException` to be thrown. When the boolean expression has a value of `false`, only the `else` part of the statement, `statement2`, will be executed.

[4](#47_Chapter39.xhtml#rfn2-4). **(E)** For this choice, the integer division `13/5` will be evaluated to `2`, which will then be cast to `2.0`. The output will be `13/5 = 2.0`. The compiler needs a way to recognize that real-valued division is required. All the other options provide a way.

[5](#47_Chapter39.xhtml#rfn2-5). **(E)** The operators `*`, `/`, and `%` have equal precedence, all higher than `-`, and must be performed first, from left to right.

![images](images/f089-01.jpg)

[6](#47_Chapter39.xhtml#rfn2-6). **(C)** The expression must be evaluated as if parenthesized like this:

![images](images/f089-02.jpg)

[7](#47_Chapter39.xhtml#rfn2-7). **(B)** Although the expression is always algebraically true for nonzero `x`, the expression may evaluate to false. This could occur because of round-off error in performing the division and multiplication operations. Whether the right-hand side of the expression evaluates to exactly 3.0 depends on the value of `x`. Note that if `x` is zero, the expression will be evaluated to `false` because the right-hand side will be assigned a value of `Infinity`.

[8](#47_Chapter39.xhtml#rfn2-8). **(D)** Any time arithmetic operations are done with floating-point numbers, round-off error may occur. The `Math` class methods (see [p. 164](#50_Chapter42.xhtml#page_164)) such as `pow` and `sqrt` use various approximations to generate their answers to the required accuracy. Since they do different internal arithmetic, however, the round-off will usually not result in exactly the same answers. Note that choice A is not correct because both `Math.pow` and `Math.sqrt` return type `double`. Choice B is wrong because no matter how `x` was previously calculated, the same `x` is input to `pow` and `sqrt`. Choice C is wrong since round-off error occurs no matter how many bits are used to represent numbers. Choice E is wrong because if `x` is representable on the machine (i.e., hasn’t overflowed), then its square root, *x*^(1/2), will not overflow.

[9](#47_Chapter39.xhtml#rfn2-9). **(D)** Each `else` gets paired with the nearest unpaired `if`. Thus when the test `(22 % 5 == 0)` fails, the `else` part indicating that `22 is negative` will be executed. This is clearly not the intent of the fragment, which can be fixed using delimiters:

![images](images/f089-03.jpg)

[10](#47_Chapter39.xhtml#rfn2-10). **(A)** Since the first test `(x >= 0)` is `true`, the matching `else` part, `y = -x`, will not be executed. Since `(x <= 100)` is `true`, the matching `else` part, `y = x * 2`, will not be executed. The variable `y` will be set to `x * 3` (i.e., 90) and will now fail the test `y < 50`. Thus, `x` will never be altered in this algorithm. Final values are `x = 30` and `y = 90`.

[11](#47_Chapter39.xhtml#rfn2-11). **(C)** In order for `!(A || B || C)` to be true, `(A || B || C)` must evaluate to false. This will happen only if `A`, `B`, and `C` are *all* false. Choice A evaluates to true when `A` and `B` are false and `C` is true. In choice B, if any *one* of `A`, `B`, or `C` is false, the boolean expression evaluates to true. In choice D, if any one of `A`, `B`, or `C` is false, the boolean expression evaluates to true since we have `!(false)`. All that’s required for choice E to evaluate to true is for `A` to be false. Since `true||(any)` evaluates to true, both `B` and `C` can be either true or false.

[12](#47_Chapter39.xhtml#rfn2-12). **(D)** To evaluate to `true`, the expression must reduce to `true && true`. We therefore need `!(false) && true`. Choice D is the only condition that guarantees this: `a > b` provides `!(false)` for the left-hand expression, and `a > b` and `b > 0` implies both `a` and `b` positive, which leads to `true` for the right-hand expression. Choice E, for example, will provide `true` for the right-hand expression only if `a < 0`. You have no information about `a` and can’t make assumptions about it.

[13](#47_Chapter39.xhtml#rfn2-13). **(A)** If `(c < a)` is `false`, `((c == a*b) && (c < a))` evaluates to `false` irrespective of the value of `c == a*b`. In this case, `!(c == a*b && c < a)` evaluates to `true`. Then `(a < b) || true` evaluates to `true` irrespective of the value of the test `(a < b)`. In all the other choices, the given expression *may* be `true`. There is not enough information given to guarantee this, however.

[14](#47_Chapter39.xhtml#rfn2-14). **(C)** If `a == b` is false, then `a != b` is true. Thus, the second piece of the compound test must be evaluated before the value of the whole test is known. Since `a == b` is false, `a - b` is not equal to zero. Thus, there is no division by zero, and no exception will be thrown. Also, since the relative values of `a`, `b`, and `n` are unknown, the value of the test `n / (a - b) > 90` is unknown, and there is insufficient information to determine whether the compound test is true or false. Thus, either `/* statement 1 */` or `/* statement 2 */` will be executed.
