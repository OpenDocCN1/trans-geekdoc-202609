
## 15 Ethics Principles

The fourth attribute of trustworthiness, introduced in Chapter 1, includes low self-orientation, motivation to serve others' interests as well as own interests, benevolence, and an aligned purpose. This chapter focuses on this fourth attribute and kicks off the sixth and final part of the book (remember the organization of the book illustrated in Figure 15.1). Introduced in Chapter 14, value alignment is composed of two halves: technical and normative; this chapter deals with the normative part. Unlike earlier chapters, this chapter is not presented through a fictional use case.

![](img/78fc6ae0a1bc731065313dc3a5886b2f_229_0.png)

Figure 15.1. Organization of the book. The sixth part focuses on the fourth attribute of trustworthiness, purpose, which maps to the use of machine learning that is uplifting. Accessible caption. A flow diagram from left to right with six boxes: part 1: introduction and preliminaries; part 2: data; part 3: basic modeling; part 4: reliability; part 5: interaction; part 6: purpose. Part 6 is highlighted. Parts 3–4 are labeled as attributes of safety. Parts 3–6 are labeled as attributes of trustworthiness.

Benevolence implies the application of machine learning for good purposes. From a consequentialist perspective (defined in chapter 14), we should broadly be aiming for good outcomes for all people. But a single sociotechnical system surely cannot do that. So we must ask: whose good? Whose interests will machine learning serve? Who can machine learning empower to achieve their goals?

The values encoded into machine learning systems are an ultimate expression of power. The most powerful can push for their version of ‘good.’ However, for machine learning systems to be worthy of trust, the final values cannot only be those that serve the powerful, but must also include the values of the most vulnerable. Chapter 14 explains technical approaches for bringing diverse voices into the value alignment process; here we try to understand what those voices have to say.

But before getting there, let’s take a step back and think again about the governance of machine learning as a control system. What do we have to do to make it selfless and empowering for all? As shown in Figure 15.2, which extends Figure 14.5, there is a paradigm—a normative theory of how things should be done—that yields principles out of which values arise. The values then influence modeling.

![](img/78fc6ae0a1bc731065313dc3a5886b2f_230_0.png)

Figure 15.2. A paradigm determines the principles by which values are constructed. The paradigm is one of the most effective points in the system to intervene to change its behavior. Accessible caption. A block diagram that starts with a paradigm block with output principles. Principles are input to a value alignment block with output values. Facts are subtracted from values to yield misalignment. Misalignment is input to a data scientists block with modeling as output. Modeling is input to a machine learning model with output that is fed into a testing block. The output of testing is the same facts that were subtracted from values, creating a feedback loop. Paradigm is intervened upon, shown using a hammer.

There are many leverage points in such a complex system to influence how it behaves.¹ Twiddling with parameters in the machine learning model is a leverage point that may have some small effect. Computing facts quickly and bringing them back to data scientists is a leverage point that may have some slightly larger effect. But the most effective leverage point to intervene on is the paradigm producing the principles.² Therefore, in this chapter, we focus on different paradigms and the principles, codes, and guidelines that come from them.

¹Donella H. Meadows. Thinking in Systems: A Primer. White River Junction, Vermont, USA: Chelsea Green Publishing, 2008. ²More philosophically, Meadows provides an even more effective leverage point: completely transcending the idea of paradigms through enlightenment.

### 15.1 Landscape of Principles

Over the last several years, different groups from different sectors and different parts of the world have created ethics principles for machine learning (and artificial intelligence more broadly) that espouse their paradigms. Organizations from private industry, government, and civil society (the third sector that is neither industry nor government, and includes non-governmental organizations (NGOs)) have produced normative documents at similar rates. Importantly, however, organizations in more economically-developed countries have been more active than those in less economically-developed countries, which may exacerbate power imbalances. Moreover, the entire framing of ethics principles for machine learning is based on Western philosophy rather than alternative conceptions of ethics.³ There are many similarities across the different sets of principles, but also key differences.⁴

First, let’s look at the similarities. At a coarse-grained level, five principles commonly occur in ethics guidelines from different organizations:

- 1. privacy,
- 2. fairness and justice,
- 3. safety and reliability,
- 4. transparency (which usually includes interpretability and explainability), and
- 5. social responsibility and beneficence.

This list is not dissimilar to the attributes of trustworthiness that have guided the progression of the book. Some topics are routinely omitted from ethics principles, such as artificial general intelligence and existential threats (machines taking over the world), and the psychological impacts of machine learning systems.

Differences manifest when looking across sectors: governments, NGOs, and private corporations. Compared to the private sector, governments and NGOs take a more participatory approach to coming up with their principles. They also have longer lists of ethical principles beyond the five core ones listed above. Furthermore, the documents espousing their principles contain greater depth.

The topics of emphasis are different across the three sectors. Governments emphasize macroeconomic concerns of the adoption of machine learning, such as implications on employment and economic growth. NGOs emphasize possible misuse of machine learning. Private companies emphasize trust, transparency, and social responsibility. The remainder of the chapter drills down into these high-level patterns.

### 15.2 Governments

What is the purpose of government? Some of the basics are law and order, defense of the country from external threats, and general welfare, which includes health, well-being, safety, and morality of the people. Countries often create national development plans that lay out actions toward improving general welfare. In 2015, the member countries of the United Nations ratified a set of 17 sustainable development goals to achieve by 2030 that harmonize a unified purpose for national development. These global goals are:

- 1. end poverty in all its forms everywhere,
- 2. end hunger, achieve food security and improved nutrition and promote sustainable agriculture,
- 3. ensure healthy lives and promote well-being for all at all ages,
- 4. ensure inclusive and equitable quality education and promote lifelong learning opportunities for all,
- 5. achieve gender equality and empower all women and girls,
- 6. ensure availability and sustainable management of water and sanitation for all,
- 7. ensure access to affordable, reliable, sustainable and modern energy for all,
- 8. promote sustained, inclusive and sustainable economic growth, full and productive employment and decent work for all,
- 9. build resilient infrastructure, promote inclusive and sustainable industrialization and foster innovation,
- 10. reduce inequality within and among countries,
- 11. make cities and human settlements inclusive, safe, resilient and sustainable,
- 12. ensure sustainable consumption and production patterns,
- 13. take urgent action to combat climate change and its impacts,
- 14. conserve and sustainably use the oceans, seas and marine resources for sustainable development,
- 15. protect, restore and promote sustainable use of terrestrial ecosystems, sustainably manage forests, combat desertification, and halt and reverse land degradation and halt biodiversity loss,
- 16. promote peaceful and inclusive societies for sustainable development, provide access to justice for all and build effective, accountable and inclusive institutions at all levels,
- 17. strengthen the means of implementation and revitalize the global partnership for sustainable development.

Toward satisfying the purpose of government, governmental AI ethics principles are grounded in the kinds of concerns stated in the sustainable development goals. Fairness and justice are a part of many of the goals, including goals five, ten, and sixteen, and also appear as a core tenet of ethics principles. Several other goals relate to social responsibility and beneficence.

Economic growth and productive employment are main aspects of goal eight and play a role in goals nine and twelve. Governments have an overriding fear that machine learning technologies will eliminate jobs through automation without creating others in their place. Therefore, as mentioned in the previous section, the economic direction is played up in governmental AI ethics guidelines and not so much in those of other sectors.

> “Our current trajectory automates work to an excessive degree while refusing to invest in human productivity; further advances will displace workers and fail to create new opportunities (and, in the process, miss out on AI’s full potential to enhance productivity).”
>
> —Daron Acemoglu, economist at Massachusetts Institute of Technology
