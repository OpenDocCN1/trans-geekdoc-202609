Use both ideas to define render-poly; make sure both definitions pass the test cases.

**Exercise 194.** Modify connect-dots so that it consumes an additional Posn to which the last Posn is connected. Then modify render-poly to use this new version of connect-dots.

Naturally, functions such as last are available in a full-fledged programming language, and something like render-poly is available in the 2htdp/image library. If you are wondering why we just designed these functions, consider the titles of both the book and this section. The goal is **not** (just) to design useful functions but to study how code is designed systematically. Specifically, this section is about the idea of generalization in the design process; for more on this idea see part III and part VI.