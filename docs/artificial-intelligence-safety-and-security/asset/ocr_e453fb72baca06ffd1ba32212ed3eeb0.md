# 3 The Basic AI Drives

Stephen M. Omohundro

# CONTENTS

+   - Introduction...........................................................47
+   - AIs Will Want to Self-Improve ...........................................................47
+   - AIs Will Want to Be Rational...........................................................48
+   - AIs Will Try to Preserve Their Utility Functions...........................................................50
+   - AIs Will Try to Prevent Counterfeit Utility...........................................................51
+   - AIs Will Be Self-Protective...........................................................53
+   - AIs Will Want to Acquire Resources and Use Them Efficiently ...........................................................54
+   - Conclusions...........................................................54
+   - Acknowledgments...........................................................54
+   - References...........................................................54

# INTRODUCTION

Surely no harm could come from building a chess-playing robot, could it? In this paper we argue that such a robot will indeed be dangerous unless it is designed very carefully. Without special precautions, it will resist being turned off, will try to break into other machines and make copies of itself, and will try to acquire resources without regard for anyone else’s safety. These potentially harmful behaviors will occur not because they were programmed in at the start, but because of the intrinsic nature of goal driven systems. In an earlier paper [1] we used von Neumann’s mathematical theory of microeconomics to analyze the likely behavior of any sufficiently advanced artificial intelligence (AI) system. This paper presents those arguments in a more intuitive and succinct way and expands on some of the ramifications.

The arguments are simple, but the style of reasoning may take some getting used to. Researchers have explored a wide variety of architectures for building intelligent systems [2]: neural networks, genetic algorithms, theorem provers, expert systems, Bayesian networks, fuzzy logic, evolutionary programming, etc. Our arguments apply to any of these kinds of system as long as they are sufficiently powerful. To say that a system of any design is an “artificial intelligence,” we mean that it has goals which it tries to accomplish by acting in the world. If an AI is at all sophisticated, it will have at least some ability to look ahead and envision the consequences of its actions. And it will choose to take the actions which it believes are most likely to meet its goals.

# AIs WILL WANT TO SELF-IMPROVE

One kind of action a system can take is to alter either its own software or its own physical structure. Some of these changes would be very damaging to the system and cause it to no longer meet its goals. But some changes would enable it to reach its goals more effectively over its entire future. Because they last forever, these kinds of self-changes can provide huge benefits to a system. Systems will therefore be highly motivated to discover them and to make them happen. If they do not have good