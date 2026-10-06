
# 5 # ETHICAL ANALYSIS OF AI-BASED SYSTEMS FOR MILITARY USE

Gregory M. Reichberg and Henrik Syse

## Introduction

There is a growing expectation– that artificial intelligence (AI) technologies will transform military affairs. Hopes have been kindled for more precise targeting and fewer casualties, while fears have arisen about new weapons of mass destruction, lack of human control and oversight, and the potential for a major shift in the geo-political balance. As this military transformation takes place some call it ‘revolution’ – gaining a better understanding of its potential benefits and disadvantages for humanity is imperative. In other words, an ethical analysis of the main challenges posed by AI military technologies is needed.

Setting aside logistics (outside its scope), this article shows how AI-enabled autonomous operations function both to support human decisions and to have an artificial agent (computerised robot) render targeting decisions. As to the first, and using NATO doctrine as a point of reference, we explain how machine-issued target-identification and target-engagement recommendations, despite the notable efficiency gains, also involve possible ethical downsides. We discuss under the following: Overfitting problem, classification problem, information overload, automation bias and complacency.

Regarding machines that are designed to make targeting decisions without direct human involvement – standardly termed ‘autonomous weapon systems’ (AWS)’ – we survey the arguments that have been proposed for and against their use in battlefield settings. Some have maintained, for instance, that AI-directed combatants have an advantage over their human counterparts, while robots operate solely by rational assessment, while humans are often swayed by emotions that can be conducive to poor judgement. By contrast, others maintain that emotions enhance moral judgement, for instance by enabling empathy; that would violate human dignity to be killed by a machine; and the honour of the military profession hinges on maintaining an equality of risk between combatants, an equality that would be removed if one side delegates its fighting to robots. Most important among the ethical questioning the use of AWS are those dealing with control and explainability, the ability of human beings to manage and understand the systems de-de-humanized (wait, the ability of human beings to manage and understand the systems deployed).

We believe that the key questions that must be asked can be preliminarily summarised as follows:

- Decisions: Who decides and how is it decided – whether to develop and use AI-based systems?
- Control/safety: At what stages can the use of these systems be managed by human decision-makers so that the likelihood of accidents is reduced (and when accidents nonetheless occur, we can mitigate the effects and learn how to prevent similar events in the future)?
- Misuse: Where lie the dangers of misuse, as illegitimate storage and use of information (violating privacy, confidentiality, etc.), application of AI-enhanced weaponry towards unauthorised targets, as well as adversarial hacking or other forms of illegitimate interference?
- Training: How are human agents trained in the proper use of these systems? What moral requirements should be placed on these agents? What technical competence and virtues should they develop and possess?
- Responsibility: Who is responsible for oversight, and who is liable for sanctions when mistakes are made?
- Transparency/Explainability: Is it possible to know who decided or did what? To what extent can human decision-makers have the required insight into the context and ramifications of their own decisions, given such challenges as secrecy and enormous complexity?

## Uses of AI in warfare

AI has three main uses in warfare: it can enable more efficient logistics (including communications coordination within a unified command); it can support human decision-making, aiding in the identification and assessment of targets; and it can replace human decision-making directly. All modalities of AI can enable autonomous functioning (although, as already noted, we set aside the first part in this chapter). Decision-support systems are autonomous technologies; they can collect and analyse targeting data, and even offer recommendations, in the absence of intervening human agent. In general, such decision aids are devices that support human decision making in complex environments... Such systems are meant to support human cognitive processes of information analysis and/or response selection by providing automatically generated cues to aid the human user or system state and to respond appropriately. Two different functions of decision aids can be distinguished: alerts and recommendations. The alert function... makes the user aware of a situation that might require action. The recommendation function involves advice on choice and action.

AWS can likewise run through an entire operating cycle without the need for human intervention. In this case, however, the cycle includes the decision to engage with a target.

Some systems are designed for decision-support functionality, while others can operate in either mode – decision support and decision-making – depending on the option selected by the human operator. This twofold functionality has been technologically possible at least since the Aegis Combat system was first deployed in the 1970s. It could be to run in automatic mode in which case it would engage targets directly without an intervening decision by a commander, or it could run in manual mode, whereby only the authorised human operator could trigger a missile launch. We have been told by a retired US admiral that he and his peers were reluctant to deploy the system in automatic mode for fear of unintended engagements that might occur.

## AI in autonomous decision-support and decision-making functions

To examine the support that AI can provide for targeting decisions, we use NATO doctrine as a point of reference. The Allied Joint Doctrine for Joint Targeting outlines several phases in the targeting cycle (or ‘loop’, as it is alternatively termed), AI-enhanced decision-support tools can be inserted at different points in this loop. Understanding these points of insertion will assist us in mapping the relevant ethical issues. Beforehand, it should be noted that the doctrine outlined below has been designed for what might be described ‘offensive operations,’ namely where military command has a choice with respect to the inception of hostilities. In defensive engagements, where prior knowledge of an oncoming attack is very limited, the time margin for careful selection of targets will be considerably restrained. NATO speaks of ‘dynamic targeting’ aposes these defensive engagements, while ‘deliberate targeting’ is the term reserved for engagements of the offensive sort. AI can have a role in either case; for the latter, the assessment of targets will be paramount, whereas for the former, the assessment of imminent threats will be primary, with the determination of targets having a subordinate role.

Figure 5.1 shows the main phases in the deliberate targeting cycle.

![](img/d43ab890b2c86d936e46ba90e0b6da43_145_0.png)

FIGURE 5.1 The joint targeting cycle

Phase 1, the ‘Commander’s intent, objectives, and guidance,’ refers to the top-echelon military decision that a use of force will be implemented, based on strategic-political guidance from the relevant authorities. All subsequent target strikes should be traceable to this intent.
Phase 2, ‘Target development,’ refers to the identification of potential targets, their subsequent vetting, prioritisation and selection, as well as building the database of knowledge about them.
Phase 3, ‘Capabilities analysis,’ consists in matching the prioritised targets with the most appropriate weapon systems (it is also called ‘weoneering’) to achieve the desired effects.
Phase 4, ‘Commander’s decision, force planning and assignment,’ involves final approval of the prioritised targets and communication of these from the operational to the tactical level. Relevant constraints, articulated as rules of engagement, are passed to the assigned units.
Phase 5, ‘Mission planning and force execution,’ involves positive identification of targets to be engaged with the predetermined weapon systems. At this juncture, a tactical targeting cycle is made operational, and is described by NATO as F2T2EA: Find, fix, track, target, engage
