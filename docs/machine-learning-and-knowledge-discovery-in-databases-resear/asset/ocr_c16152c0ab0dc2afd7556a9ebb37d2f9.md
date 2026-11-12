# DiNGHY: Null Models for Non-degenerate Directed Hypergraphs

Maryam Abuissa\(^1\) , Matteo Riondato\(^2\) , and Eli Upfal\(^1\)

\(^1\) Brown University, Providence, RI 02912, USA
{maryam_abuissa,eliezer.upfal}@brown.edu
\(^2\) Amherst College, Amherst, MA 01002, USA
mriondato@amherst.edu

**Abstract.** Non-degenerate directed hypergraphs, i.e., directed hypergraphs where a node cannot be both in the tail and the head of a hyperedge, model important scenarios, from contact networks for analyzing the spread of information or diseases, to bill cosponsoring graphs for studying the bipartisanship of elected representatives. Existing null models for dihypergraphs allow degeneracy, and most samples drawn from them are degenerate, even when the starting network is not, making these models unrealistic in many cases. An inappropriate null model may lead to wrongly accepting/rejecting a hypothesis when performing statistical hypothesis testing. We introduce the first null models for non-degenerate dihypergraphs, and present DiNGHY, a suite of Markov-Chain-Monte-Carlo algorithms to sample from them. The Markov chain underlying our algorithm is not irreducible in general, so we give mild sufficient conditions for irreducibility. We show that existing methods cannot be used to sample from our null models, and evaluate our algorithms on real and artificial dihypergraphs, comparing the results of hypothesis tests when using our null models versus existing ones that allow degeneracy, and measuring their empirical mixing time.

**Keywords:** Graph Analysis · Hypothesis Testing · Markov Chain Monte Carlo · Network Science

# 1 Introduction

Hypergraphs overcome the limitations of dyadic (i.e., “classic”) graphs to model “more-than-binary” relationships between entities [2,3]. Such relationships are omnipresent in real scenarios, from co-authorship networks [16], to protein interactions [9], to contact networks [4]. There are many data analysis tasks and corresponding algorithms whose input is one or more hypergraphs [14].

The goal of knowledge discovery from data is to use results obtained from data to identify new facts about the Data Generating Process (DGP), of which the available data is only a limited, noisy, random sample [21]. In the framework of statistical hypothesis testing [15], one first formulates a hypothesis, usually expressed

**Supplementary Information** The online version contains supplementary material available at https://doi.org/10.1007/978-3-032-06066-2_4.