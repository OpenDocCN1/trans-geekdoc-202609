
$$\\begin{array}{l} {\\mathcal{L}\_{MLM}^{(x)} = - \\frac{1}{|M\_{x}|}{\\sum\\limits\_{i \\in M\_{x}}}l}ogP(x\_{i}|x\\_{\\smallsetminus M\_{x}})} \\\\ \\end{array}$$  

(4.1)

[Fig. 4.1](#ch4.xhtml#fig4_1) 图 4.1 展示了 MLM 任务，其中 *x* 和 *y* 代表不同语言中的单语言输入句子。尽管该任务不考虑汇聚的掩码输入的多语言信息，但它已展示出在生成跨语言表示方面的巨大价值，这些表示在不同语言之间高度对齐。下文的“洞察”部分将提供更多细节，说明导致这种行为的因素。

![Figure 4.1 Illustration of multilingual MLM task \[71, 194\]. x and y are monolingual sentences in different languages that are not parallel.](images/fig4_1.jpg)

[Figure 4.1](#ch4.xhtml#b4fig4_1) 图 4.1 展示了多语言 MLM 任务 \[[71](#refbib.xhtml#refbib_71), 194\]. *x* 和 *y* 是不同语言中的单语言句子，且不平行。

**Next Sentence Prediction (NSPAN<s><s>**  
