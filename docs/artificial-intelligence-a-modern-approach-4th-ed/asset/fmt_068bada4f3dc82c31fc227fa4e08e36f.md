
The figure consists of eight tables. Each table has three squares in the bottom row and two squares in the top row. The bottom row is numbered 1 and the top row is numbered 2. Table 1: Row 1: Column 1, Empty. Column 2, Breeze. Column 3, Pit. Row 2: Column 1, Empty. Column 2, Empty. Table 2: Row 1: Column 1, Empty. Column 2, Breeze. Column 3, Empty. Row 2: Column 1, Pit. Column 2, Empty. Table 3: Row 1: Column 1, Empty. Column 2, Breeze. Column 3, Empty. Row 2: Column 1, Empty. Column 2, Pit. Table 4: Row 1: Column 1, Empty. Column 2, Breeze. Column 3, Empty. Row 2: Column 1, Empty. Column 2, Empty. Table 5: Row 1: Column 1, Empty. Column 2, Breeze. Column 3, Pit. Row 2: Column 1, Pit. Column 2, Empty. Table 6: Row 1: Column 1, Empty. Column 2, Breeze. Column 3, Pit. Row 2: Column 1, Empty. Column 2, Empty. Table 7: Row 1: Column 1, Empty. Column 2, Breeze. Column 3, Pit. Row 2: Column 1, Pit. Column 2, Pit. Table 8: Row 1: Column 1, Empty. Column 2, Breeze. Column 3, Empty. Row 2: Column 1, Pit. Column 2, Pit. Tables 1, 3, and 7 are grouped using a solid line and labeled `KB`. Tables 1, 3, 4, and 7 are grouped using a dotted line and labeled `α1`.

×![](images/Fig-105.jpg)

### Figure 7.5 Possible models for the presence of pits in squares \[1,2\], \[2,2\], and \[3,1\].
The `KB` corresponding to the observations of nothing in \[1,1\] and a breeze in \[2,1\] is shown by the solid line. (a) Dotted line shows models of `α1` (no pit in \[1,2\]). (b) Dotted line shows models of `α2` (no pit in \[2,2\]).

The `KB` can be thought of as a set of sentences or as a single sentence that asserts all the individual sentences. The `KB` is false in models that contradict what the agent knows—for example, the `KB` is false in any model in which \[1,2\] contains a pit, because there is no breeze in \[1,1\]. There are in fact just three models in which the `KB` is true, and these are shown surrounded by a solid line in [Figure 7.5](#Chapter07-03.xhtml#fig7-5). Now let us consider two possible conclusions:

$\\begin{matrix} {\\alpha\_{1} = \\,"\\text{There~is~no~pit~in~\[1,2\]}\\text{.}"} & {\\,\\,\\,\\,\\,\\alpha\_{2} = "\\text{There~is~no~pit~in~\[2,2\]}\\text{.}"} \\\\ \\end{matrix}\\,$

We have surrounded the models of `α1` and `α2` with dotted lines in [Figures 7.5(a)](#Chapter07-03.xhtml#fig7-5) and [7.5(b)](#Chapter07-03.xhtml#fig7-5), respectively. By inspection, we see the following:

in every model in which `KB` is true, `α1` is also true.

Hence, `KB ⊨ α1`: there is no pit in \[1,2\]. We can also see that

in some models in which `KB` is true, `α2` is false.

Hence, `KB` does not entail `α2`: the agent cannot conclude that there is no pit in \[2,2\]. (Nor can it conclude that there is a pit in \[2,2\].)[4](#Chapter07-09.xhtml#sup07-4)

The preceding example not only illustrates entailment but also shows how the definition of entailment can be applied to derive conclusions—that is, to carry out logical inference. The inference algorithm illustrated in [Figure 7.5](#Chapter07-03.xhtml#fig7-5) is called `model checking`, because it enumerates all possible models to check that `α` is true in all models in which `KB` is true, that is, that `M(KB) ⊆ M(α)`.

<p class="sidebar">Logical inference</p> <p class="sidebar">Model checking</p>

In understanding entailment and inference, it might help to think of the set of all consequences of `KB` as a haystack and of `α` as a needle. Entailment is like the needle being in the haystack; inference is like finding it. This distinction is embodied in some formal notation: if an inference algorithm `i` can derive `α` from `KB`, we write

`KB |−[i] α`.

which is pronounced “`α` is derived from `KB` by `i`” or “`i` derives `α` from `KB`.”

An inference algorithm that derives only entailed sentences is called sound or truth-preserving. Soundness is a highly desirable property. An unsound inference procedure essentially makes things up as it goes along—it announces the discovery of nonexistent needles. It is easy to see that `model checking`, when it is applicable,[5](#Chapter07-09.xhtml#sup07-5) is a sound procedure.

<p class="sidebar">Sound</p> <p class="sidebar">Truth-preserving</p>

The property of completeness is also desirable: an inference algorithm is complete if it can derive any sentence that is entailed. For real haystacks, which are finite in extent, it seems obvious that a systematic examination can always decide whether the needle is in the haystack. For many knowledge bases, however, the haystack of consequences is infinite, and completeness becomes an important issue.[6](#Chapter07-09.xhtml#sup07-6) Fortunately, there are complete inference procedures for logics that are sufficiently expressive to handle many knowledge bases.

<p class="sidebar">Completeness</p>

We have described a reasoning process whose conclusions are guaranteed to be true in any world in which the premises are true; in particular, if `KB` is true in the real world, then any sentence `α` derived from `KB` by a sound inference procedure is also true in the real world. So, while an inference process operates on “syntax”—internal physical configurations such as bits in registers or patterns of electrical blips in brains—the process corresponds to the real-world relationship whereby some aspect of the real world is the case by virtue of other aspects of the real world being the case.[7](#Chapter07-09.xhtml#sup07-7) This correspondence between world and representation is illustrated in [Figure 7.6](#Chapter07-03.xhtml#fig7-6).

 Description 

The figure consists of two regions. The first region is labeled representation and the second region is labeled world. Representation region consists of sentences. An arrow labeled entails starts from sentences and points to sentence inside the representation region. World region consists of aspects of the real world. An arrow labeled follows starts from aspects of the real world and points to aspect of the real world, which is also inside the world region. An arrow labeled semantics from sentences in the representation region points to aspects of the real world in the world region. An arrow labeled semantics from sentence in the representation region points to aspect of the real world in the world region.

×![](images/Fig-106.jpg)

### Figure 7.6 Sentences are physical configurations of the agent, and reasoning is a process of constructing new physical configurations from old ones. Logical reasoning should ensure that the new configurations represent aspects of the world that actually follow from the aspects that the old configurations represent.
