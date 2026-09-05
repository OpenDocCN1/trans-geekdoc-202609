![](images/cover.jpg)

![](images/cover.jpg)

Naval Institute Press

291 Wood Road

Annapolis, MD 21402

© 2021 by Sam J. Tangredi and George Galdorisi

All rights reserved. No part of this book may be reproduced or utilized in any form or by any means, electronic or mechanical, including photocopying and recording, or by any information storage and retrieval system, without permission in writing from the publisher.

**Library of Congress Cataloging-in-Publication Data**

Names: Tangredi, Sam J., editor. | Galdorisi, George, date, editor.

Title: AI at war : how big data, artificial intelligence, and machine learning are changing naval warfare / edited by Sam J. Tangredi and George Galdorisi.

Other titles: Artificial intelligence at war

Description: Annapolis, Maryland : Naval Institute Press, \[2021\] | Includes bibliographical references and index.

Identifiers: LCCN 2020047097 (print) | LCCN 2020047098 (ebook) | ISBN 9781682476062 (hardcover) | ISBN 9781682476345 (pdf) | ISBN 9781682476345 (epub)

Subjects: LCSH: Artificial intelligence—Military applications—United States. | Naval art and science—United States—Data processing. | Naval art and science—Technological innovations—United States. | Big data.

Classification: LCC UG479 .A44 2021 (print) | LCC UG479 (ebook) | DDC 359.00285/63—dc23

LC record available at [https://lccn.loc.gov/2020047097](https://lccn.loc.gov/2020047097)

LC ebook record available at [https://lccn.loc.gov/2020047098](https://lccn.loc.gov/2020047098)

![image](images/copy.png)Print editions meet the requirements of ANSI/NISO z39.48-1992 (Permanence of Paper). Printed in the United States of America.

29 28 27 26 25 24 23 22 21   9 8 7 6 5 4 3 2 1

First printing

# **ILLUSTRATIONS**

Photos

[1-1. The School of Athens](#09_Chapter01.xhtml#ph1)

[17-1. Historical Pre-Invasion Speech](#25_Chapter17.xhtml#ph2)

[17-2. Pre-Invasion Speech to AI Machine Troops](#25_Chapter17.xhtml#ph3)

[17-3. Pre-Invasion AI Machine Speech to Human Troops](#25_Chapter17.xhtml#ph4)

[17-4. Pre-Invasion Speech to Human-Machine Team](#25_Chapter17.xhtml#ph5)

Tables

[5-1. Comparative Populations and AI Implications (2017)](#13_Chapter05.xhtml#tb1)

[5-2. The Six Propositions](#13_Chapter05.xhtml#tb2)

[5-3. The Six Policy Recommendations](#13_Chapter05.xhtml#tb3)

[9-1. TCPED Process with AI Extension](#17_Chapter09.xhtml#tb4)

[14-1. Course Requirements](#22_Chapter14.xhtml#tb5)

Figures

[1-1. The Turing Machine](#09_Chapter01.xhtml#fig1)

[3-1. John Boyd’s OODA Loop](#11_Chapter03.xhtml#fig2)

[9-1. The TCPED Process with AI Extension](#17_Chapter09.xhtml#fig3)

[9-2. Three-Layer Neural Network Architecture](#17_Chapter09.xhtml#fig4)

[9-3. Adaptive Closed-Loop Control Processing](#17_Chapter09.xhtml#fig5)

[12-1. The Joint Targeting Cycle](#20_Chapter12.xhtml#fig6)

[15-1. Mahan-in-a-Box Conceptualized at the Operational Level of War](#23_Chapter15.xhtml#fig7)

[19-1. Quantity versus Accuracy of Training Data](#27_Chapter19.xhtml#fig11)

[19-2. Marriage Rate in Wyoming versus Car Sales](#27_Chapter19.xhtml#fig8)

[19-3. Example of an Adversarial Attack in Two Dimensions](#27_Chapter19.xhtml#fig9)

[19-4. Three Different Types of Inputs](#27_Chapter19.xhtml#fig10)

# **FOREWORD**

ADM. JAMES G. STAVRIDIS, USN (RET.)

**“Go right at ’em.”** Those are the words of the greatest admiral in history, Vice Admiral Lord Nelson of Trafalgar. When I began to truly study his tactical approach over the years, I was a lieutenant commander looking forward to the day I would command a warship at sea. As I pondered his lessons, I wondered how best a warship, and a fleet, could position themselves to achieve that maxim.

From my own study, I already knew—or at least suspected—that information was the key ingredient. But in the midst of crisis or battle, accurate information was always difficult to obtain. Common wisdom held that “first reports are always wrong.” The key to being a successful commander throughout naval history had been the ability to sort through incomplete information, assess what was probable and what was unlikely, and make a decision based on professional judgment honed by experience. Nelson knew that, and I gradually learned it over the many sea miles of my voyage.

In those days, the late 1980s, the U.S. Navy was already making the change from analog to digital. Many of the weapons and sensors themselves were already digital, but it was not until the paradigm-breaking Aegis combat system proliferated throughout the surface fleet that digital information from multiple sources and sensors became a truly reliable, albeit never infallible, asset in operational (read “human”) decision-making. I was lucky to be the commissioning operations officer on one of the very first Aegis ships, USS *Valley Forge* (CG 50), where I benefited from the technical acumen of the “father of Aegis,” Rear Adm. Wayne Meyer, and the tactical acumen of Capt. Wayne Hughes.

At the same time came the public proliferation of the personal computer, the popularization and commercialization of the Internet, and the incredible advances (and potential for conflicts) in cyberspace. The entire world was becoming awash with information that previously required much time and human labor to acquire and categorize. The prodigious amount of available information—in both the civilian and military spheres—was increasing so much and so fast that it seemed the human mind could not keep up. It was becoming apparent that decision-makers, particularly those who might face combat, needed new ways to sort through all the information with which they were being bombarded.

In naval operations, information was no longer primarily sourced from sensors located on board the individual warship—what we call organic sensors. Accurate information was coming from satellites, shore stations, other services’ joint assets, and open sources. Lack of information suitable for targeting the enemy could often still be a problem, but now it was compounded by other times when there was just too much information to sort through. Much information was available to the enemy as well.

How, then, could we continue to position ourselves to “go right at ’em”? That is when I realized that the key had shifted from availability of information to the speed of decision. In some ways, this parallels what was already known in air dogfights based on Air Force Col. John Boyd’s model of the observe-orient-decide-act (OODA) loop. Pilots who could cycle more quickly through the OODA loop—in other words, made accurate decisions more quickly—generally won the dogfight. They were, in the words of Wayne Hughes, able to attack effectively first.

By the 2000s, when I became a senior decision-maker, particularly as Supreme Allied Commander of North Atlantic Treaty Organization (NATO) forces, the amount of information that could potentially support decisions was absolutely staggering. I knew there needed to be methods of processing, combining, validating, and making the options clear to the humans who had to decide both peaceful and violent actions. The decisions needed to be made before an enemy could make them—and faster, as former Chief of Naval Operations Adm. John Richardson likes to say.

Fortunately, the development of artificial intelligence (AI) systems holds great promise to enhance critical human decision-making, especially when speed of decision means life or death—not to replace human decision-making, please note, but to assist it in making effective decisions amidst the melee of often conflicting and ambiguous information. To me, the true promise of AI is to speed up our OODA loop through new methods of human-machine teaming and collaboration.

I wish I had had AI systems to assist me—and NATO’s tirelessly dedicated personnel—in sorting through the complexity of information during our operations. Humans striving to be tireless are no longer enough. At NATO, we did not sufficiently and effectively leverage our technological advantages.

All of that is why I jumped at the chance to provide the foreword to this volume. General discussions concerning the promise of AI, machine learning, big data, and human-machine teaming in military affairs have proliferated, but relatively little has been written as to how the United States and its Navy can achieve this promise. This book drills down through the advances and—quite frankly—the hype, to identify both the applications and limitations of AI to naval warfighting. It may be the very first book to do so.

During his term as deputy secretary of defense, my close friend and colleague, the Honorable Bob Work, placed AI in the center of his effort to create a third offset strategy. The debate over the third offset became complex—and sometimes contentious—in itself. Putting my Navy hat back on, I would describe the need for implementing AI in naval (and military operations in general) as enabling us to “go right at ’em” in a Nelsonian sense.

In this approaching period of potential great power competition, I believe that the ability to “attack effectively first” is the prime enabler of being able to deter effectively first. AI is not the full solution to effective decision-making about warfighting and deterrence, war and peace. But if it assists future decision-makers to make wise choices, it will live up to its promise. This book, I believe, is a seminal step toward building a foundation for effectively applying AI to defense decision-making. Edited and partly written by two brilliant thinkers, my friends George Galdorisi and Sam Tangredi, this book is the “sea detail” that allows the reader to sail into the still-uncharted waters of artificial intelligence.

# Introduction

SAM J. TANGREDI AND GEORGE GALDORISI

**Artificial intelligence (AI)** may be the most beneficial technological development of the twenty-first century. However, it is undoubtedly the most hyped technological development of the past two decades. This hype has raised expectations for results and, unfortunately, has clouded public understanding of the true nature of AI and its limitations as well as its potential.

The very characteristics of AI, machine learning, human-machine teaming, and analysis of big data are poorly understood except by specialists, and the terms have been publicly used in arbitrary fashions, sometimes deliberately. The highly respected *Financial Times* reports that a study indicates 40 percent of “artificial intelligence start-ups” (software companies seeking capital investments) in Europe actually “do not use any AI programs in their products.” It appears that “companies branded as AI businesses have historically raised larger funding … and secured higher valuations than other software businesses,” up to “15 percent higher” than those that do not use the term “artificial intelligence.”^([1](#08_Introduction.xhtml#rfn_1)) Hence, there are great incentives to appropriate the term AI and apply it to other programming activities, vaguely related research efforts, and unmanned or autonomous systems development.

If venture capitalists responsible for the investment of many thousands or millions of dollars are not often certain as to what constitutes AI, how can non-specialists be?

## **WHAT REALLY IS ARTIFICIAL INTELLIGENCE?**

In reality, artificial intelligence is not magic, mystery, or a superior way of thinking.^([2](#08_Introduction.xhtml#rfn_2)) Any well-functioning human brain could perform the same functions as any AI machine if time, energy, focus, and data storage (recollection) were not factors and limits. AI machines consist of software and input composed of programming, algorithms, and collected, correlatable data running on computer hardware. AI machines have beaten human masters of chess, iGo, and Texas Hold ’Em poker because they can contain and recall more data in a shorter amount of time than the human brain.

AI has had myriad definitions since its initial development as a branch of computer science in the late 1950s,^([3](#08_Introduction.xhtml#rfn_3)) but all of these can be distilled into a simple definition of AI as “the capability of a machine to imitate human behavior,” or, more specifically, “a computer system able to perform tasks that normally require human intelligence, such as visual perception, speech recognition, decision-making, and translation between languages.”^([4](#08_Introduction.xhtml#rfn_4)) AI’s advantages over the human mental processes that it imitates are its ability to perform calculations more rapidly and avoid the difficulties of actually being human: bodily functions, fatigue, emotions, boredom, worry, and doubt.

Whereas a human iGo master can recall hundreds of options for the next series of moves, an AI machine—if initially programmed with the rules of the game and the knowledge of other iGo masters—can recall thousands, perhaps hundreds of thousands of options. AI can rapidly “learn” some of these options by observing play or actually playing (termed “imitative learning”), but the key to victory is recollection. The machines also do not tire, are not distracted by other thoughts, tasks, or emotions, and—converting data into binary systems of zeros and ones (like all computers)—can make calculations at much greater speeds.

However, even AI machines that are programmed to self-learn have to be programmed by humans, be taught initially how to learn (via code) by humans, and be provided with data from sensors created and attached to them by humans, and they are ultimately designed to mimic rational judgment—rationality being a human construct. AI can be seen as “superior” to human intelligence since it can quickly process data faster than any one human, albeit usually in one narrow field of knowledge. Yet it is still the product of collective human endeavor. As such, it has limits, costs, and risks.

AI machines have vulnerabilities, some greater and some less than those of humans. Just as humans can suffer massive heart attacks or devastating combat trauma, AI machines can “die” instantly if separated from their power sources. AI machines, contained in metal boxes, can be armored for protection from shock, but so can humans. AI machines can be constructed in robot form with some limited degree of movement using mechanical strength that surpasses human strength. However, the ability to engineer a robot to fully mimic all the degrees of human movement requires efforts and costs that exceed the actual programming costs of AI. In industry, current robots remain very limited in function in order to perform narrow tasks that are repetitive in nature.^([5](#08_Introduction.xhtml#rfn_5)) Even if AI-driven, they are not designed to multitask outside of limited functions simply because it is not cost-effective to do so.^([6](#08_Introduction.xhtml#rfn_6))

Another limit to AI, whether simple, narrow, or general (we will define those terms later), is created by the very nature of electronic binary computer coding. Since computers are essentially limited to calculation—perhaps we can call it “internal thought”—only in combinations of zeros and ones (which is why the system is called binary), they are capable of “thinking” only in terms of yes or no, black or white—not “maybe” or “gray.”^([7](#08_Introduction.xhtml#rfn_7)) In an analog machine, this would result in on/off functions and cannot result in “partially on.” The result is that, unlike humans, AI cannot take partial actions without having considerable programming layers (deep learning) that can categorize data by probabilities. These layers, which consist of decision nodes that prescreen data going to other decision nodes, can approximate “gray thinking” by combining binary loops. Nevertheless, they cannot match both the disadvantages and *value* of human doubt. This factor is dismissed by some computer scientists who point out that black/white thinking is valid since “one cannot be a little bit pregnant.”^([8](#08_Introduction.xhtml#rfn_8)) However, humans can make decisions based on uncertainty, personal values, and irrational thinking, all of which are difficult for AI to duplicate.

Unlike humans, AI machines do not necessarily show the effects of aging, if the hardware is properly maintained and the software remains free from hacking or other compromise (and is upgraded as technology advances). They also feel neither fear nor exhilaration while facing an enemy in combat.

## **UNDERSTANDING MILITARY AI**

In the public perception of military affairs, the term AI almost universally conjures up images of “killer robots” running amok and deliberately attacking noncombatants, possibly destroying the entirety of the human race. Obviously, this mental image is elicited by a large number of popular movies and novels based on that theme.

This fear exists to the extent that certain scientists and scholars have conflated artificial intelligence with unmanned military systems (these so-called killer robots). A coalition of nongovernmental organizations, led by Human Rights Watch, has established a “campaign to ban killer robots,” which they define as an effort to “ban fully autonomous weapons and thereby retain meaningful human control over the use of force.”^([9](#08_Introduction.xhtml#rfn_9)) Human Rights Watch defines autonomous weapons as weapons that “would be able to select and engage targets without human intervention,” a definition so broad that it could conceivably cover such existing weapons as heat-seeking missiles (originating in the 1950s) or stationary naval mines (the first recorded, verifiably successful mine attack was in 1855).^([10](#08_Introduction.xhtml#rfn_10)) In fact, Human Rights Watch refers to “armed drones” as “precursors” to killer robots, despite the fact that all verifiable armed drone missions have been conducted by human operators. With confused assemblages of terms such as “drones,” “autonomous weapons,” “killer robots,” and “AI,” along with journal articles with hyped or alarmist headlines, it is difficult for both the public and those charged with national security to comprehend the advantages—and limits—of specific applications of artificial intelligence and its associated (albeit distinct) techniques of machine learning and analysis/fusion of big data.^([11](#08_Introduction.xhtml#rfn_11))

This lack of knowledge and understanding results from the fact that there are very few open, public sources—articles, books, published studies—that discuss in any detail the specific, functional applications of Al to the discrete elements that constitute preparation for, deterrence of, and conduct of military operations. Part of this difficulty is due to the security classification of such information, during both the military-sponsored research and development phase and the implementation and employment of such systems. Another complication is that many of the professional articles written on the potential for AI application to military affairs are direct, indirect, or (rarely) subtle arguments for spending additional financial and personnel resources (e.g., money, labor, and time) on the development of AI and related techniques. Other sources are arguments for the greater importance (or “status” in the bureaucratic hierarchy) of AI programs in the U. S. Department of Defense (DoD). It is hard to give a balanced assessment of the application of AI (cons as well as pros) while advocating for more money or status.

*AI at War* is specifically intended to overcome these difficulties and increase the understanding of both national security professionals and the interested public of the application of AI to warfighting. Although the themes and findings of the chapters are generally applicable across DoD, to include all services, joint staff, and defense agencies, as well as allied and partner ministries of defense, our “case study” is warfighting functions in the naval services—the U.S. Navy and U.S. Marine Corps. Our definition of “warfighting” is deliberately broad to include those logistics and administration functions that are necessary for combat operations or deterrence. Such “tail” in the proverbial “tooth-to-tail” ratio is essential if the teeth are to be employed. For this book, warfighting also includes the overall national security strategy, assessment of the future security environment, and planning, programming, and budgeting essential to ensure our future security.

It is important to note that even within DoD, the term AI is used loosely, often applied to software programs and algorithms that provide “automated processes” for data fusion, rather than to the dominant characteristics of artificial intelligence: pattern recognition and the ability to self-program. For the purposes of this book, we try to avoid conflating AI with automated processes that do not include pattern recognition or self-programming, but when we use the term AI, we do include in it the related functions of machine learning and big data analysis—primarily for brevity.

However, before switching to brevity, it is imperative that we unpack and distinguish those terms.

## **AI VS. MACHINE LEARNING VS. BIG DATA**

The relationship between deep learning, machine learning, and AI has been described as “a set of Russian dolls \[*matryoshka*\] nested within each other, beginning with the smallest and working out\[ward\]. Deep learning is a subset of machine learning, and machine learning is a subset of AI.”^([12](#08_Introduction.xhtml#rfn_12)) From this perspective, AI includes more than machine learning, but all machine learning falls under the category of AI.

Machine learning was originally defined as a “field of study that gives computers the ability to learn without being explicitly programmed.”^([13](#08_Introduction.xhtml#rfn_13)) Recent usage describes machine learning as the ability of computers to modify their decision-making when exposed to increasing amounts of data.

This is achieved primarily through trial-and-error learning guided by predictions. In essence, the machine is programmed to predict outcomes based on the knowledge and algorithms with which it is initially provided. After it makes a decision or takes an action based on its initial knowledge (memory) and forecast of being correct, it learns from the results. If incorrect, it programs that bit of knowledge into its memory and is able to modify the algorithm that guides its prediction (and actions). Part of the data is the quantitative size of the error measured by the “distance” from the answer.^([14](#08_Introduction.xhtml#rfn_14)) A useful, but overly simplistic, illustration would be the addition of a new factor to an “if-then” computer statement.^([15](#08_Introduction.xhtml#rfn_15)) That statement is modified from “if-then” to “if-then (original knowledge) plus then (latest results).” In this way, the computer “learns” from experience. Once processed, each data set is referred to as having been “labeled.”

To make decisions from a huge amount of data—such as in facial recognition, by evaluating combinations of pixels—programming such learning becomes very complex with the equivalent of hundreds of thousands of if-then statements and pieces of labeled data. The algorithms creating these statements are arranged in layers in which two or more algorithms (sometimes referred to as “nodes”) in one layer feed results to a node (algorithm) of a higher layer. Each layer or node adds a corresponding layer of complexity by combining the multiple results of the previous layer into a new (but related) algorithm. “Deep” is the technical term for a network of nodes that has more than one “hidden” layer, or any layer other than the original data input and the final output. Thus, any system involving more than three layers is considered to constitute “deep learning.” Deep learning is thereby a subset of machine learning. As computation hardware has improved and programmers have become more adept, deep learning has constituted an increasing percentage of machine learning systems.

Deep learning systems with multiple layers and nodes are referred to as neural networks or, more properly, “deep artificial neural networks” and sometimes “deep reinforcement learning.”^([16](#08_Introduction.xhtml#rfn_16)) The choice of this common term is unfortunate, since it conjures the image of the neural networks within the human brain, which function through biochemical processes (as studied in the medical field of neurology), rather than electrical-sourced binary calculations. For a lay audience, the use of the term “neural networks” makes deep learning and AI seem more human-like than they actually are. Perhaps this also makes such AI machines more threatening.

However, the layered combination of nodes in neural networks is simply a more extensive means of generating predictions (such as in photo recognition: “this image is probably a leaf”), comparing the predictions to reality (“no, it is actually not a leaf; it is a tree”), establishing the degrees of error (“a leaf is more related to a tree than it is to the image of a dog, but it is less related than an image of a branch with several leaves”), and correcting the controlling algorithm (“this is how to distinguish a leaf or branch with several leaves from a tree”). Media examples in which AI systems mistake the faces of individuals or confuse one animal for another likely indicate that the system examined does not have enough layers to identify more distinguishing characteristics. But the more layers there are, the more computational difficulty, and—if a single computation is incorrect—the more chances of error. This is the infamous situation of “garbage in equals garbage out.” When applying AI to decision-making in the use of military weapons systems—which often involves a great deal of complexity—programming errors of that sort could be fatal to the defender or result in collateral damage or friendly fire. That is not true for systems that only play chess or iGo.

This leads to a debate within the ranks of AI scientists as to whether “supervised learning” or unsupervised deep learning is the most effective way to build accurate AI machines. In supervised learning, a human programmer or data scientist/engineer is involved more *deeply* in assisting the machine with the labeling of data. Instead of simply devising the underlying programs and providing the initial data, the engineer also evaluates the machine’s assembly and association of data and “corrects” it when it is wrong. As one data science consulting firm describes its value, “Data scientists are the people who explore data, clean it, test algorithms that they think might make accurate predictions about that data, and then tune those algorithms so that they work well.”^([17](#08_Introduction.xhtml#rfn_17))

Eventually, the corrections accumulate so that the machine has a solid framework within which to label new data inputs. Supervised learning may also involve putting the AI machine into simulations with known answers in order to evaluate the output. In unsupervised learning, the machine itself is allowed to work its associations by trial and error, establishing its own guidelines.

The debate involves both cost and philosophy. Obviously, supervised learning involves much greater costs (since it is more human labor–intensive) than allowing the AI machines to do their own trial-and-error learning and, afterward, have humans evaluate the final output.^([18](#08_Introduction.xhtml#rfn_18)) In the race between Tesla, Waymo, Uber, and other companies to develop fully autonomous self-driving cars, costs matter since they cut into (potential) profits. The company that can utilize the least costly sensors and fewest human engineers (and achieve results) is perceived as the better investment.^([19](#08_Introduction.xhtml#rfn_19)) Balancing the search for lower development costs is the results; running over a bicyclist is considered a bad thing.^([20](#08_Introduction.xhtml#rfn_20)) Presumably, the more the learning is supervised, the less likely that such incidents occur.

At the same time, there is an aspect of unsupervised learning that worries some scientists—and enthralls others. Without supervision, it is difficult to determine exactly how AI machines “think through” a particular problem, and, hence, difficult to duplicate the exact logic and process of the machine’s decision-making. The actual AI process remains a mystery, evoking the image of potentially irrational (by human standards) results. This has been noted as “the dark secret at the heart of AI” and particularly observed through the artwork produced by unsupervised AI.^([21](#08_Introduction.xhtml#rfn_21)) Yet other scientists are intrigued that there might be modes of (AI) thought vastly different from that of humans, which might lead to unimagined discoveries. Even the art world appears interested.^([22](#08_Introduction.xhtml#rfn_22))

This touches on the philosophical question of whether supervised AI is “actual AI” and whether AI machines should be free to map out “new paths to knowledge.” At the extreme fringe are those who postulate that advanced (unsupervised learning) AI “could run the world better than humans ever could.”^([23](#08_Introduction.xhtml#rfn_23))

Leaving aside the philosophical aspect, an additional difficulty in applying deep learning—and certainly unsupervised machine learning—to weapons systems is that all deep learning (like all machine learning) relies, as previously discussed, on some degree of learning from errors of initial perception. Yet in combat, one single error can be fatal. For example, the Phalanx close-in weapons systems (CIWS), used as the last-ditch point defense system against antiship cruise missiles in U. S. and allied Navy warships, can be considered a “simple” AI system since it can detect, identify, track, and—if in full-auto mode—engage an incoming target without human intervention. Development of CIWS as an automated, networked system was a recognition of the increasing speed and varying flight profiles of a new generation of antiship missiles. However, CIWS is not designed with machine learning and could not function as a learning system, since learning from error would result in its destruction (along with that of the ship). The point is that there are limits to the application of machine and deep learning to AI. As previously noted, all machine learning is AI, but not all AI includes deep learning.

Big data is associated with AI since the amount of information and effort to correlate the data is usually so huge as to require automated processes more advanced than any available through previous types of computer programming. At its best, big data analytics “makes it possible to do many things that previously could not be done: spot business trends, prevent diseases, combat crime and so on.… Number-crunchers have even uncovered match-fixing in Japanese sumo wrestling.”^([24](#08_Introduction.xhtml#rfn_24))

Much of this primarily digital data is collected as the result of activities conducted for other purposes and is especially used to target Internet advertising: “‘Data exhaust’—the trail of clicks that Internet users leave behind from which value can be extracted—is becoming a mainstay of the Internet economy. One example is Google’s search engine, which is partly guided by the number of clicks on an item to help determine its relevance to a search query. If the eighth listing for a search term is the one most people go to, the algorithm puts it higher up.”^([25](#08_Introduction.xhtml#rfn_25)) Google either sells the analytical data to marketing firms or manufacturers that evaluate how to best position their products for sale on the Web or provides the evaluation and positioning as a service-for-hire.

Assessing what methods to use to compile and analyze the volume of data is where data scientists come into their own. As *The Economist* notes, “a new kind of professional has emerged, the data scientist, who combines the skills of software programmer, statistician and storyteller/artist to extract the nuggets of gold hidden under mountains of data.”^([26](#08_Introduction.xhtml#rfn_26)) These skills have obvious applicability to military analysis, where input from a variety of sensors needs to be combined to provide targeting solutions. For example, in undersea warfare or antisubmarine warfare, many environmental factors need to be measured in order to evaluate a sonar return: water salinity, depth, bottom contour, biologics, and so forth. Naval researchers were analyzing combinations of such factors long before anyone coined the term “data scientist.” Weapons systems have long been designed to account for information. However, with AI, such data can presumably be evaluated faster and with more accuracy than before, along with making the decision as to which weapon would achieve the greatest effect in an attack.

In short, the relationship between AI and big data is one of tool and endeavor. Big data analytics attempts to make sense and value out of huge amounts of digitally recorded data. AI processing is a method by which the data can be combined, categorized (labeled), and analyzed. Big data does not fit the Russian nested doll image. Rather, the relationship between big data and AI can be visualized as a Venn diagram of overlapping circles, with much of the big data circle overlapped by a larger AI circle. Not all big data analytics use AI, but much of it does. A part of the universe of AI is used for big data analytics, but it can also be said that all AI is itself dependent on big data input.

Large quantities of data are needed to train AI, and without such amounts of data, there might be no point in developing AI. In recognition of the fact, we often present the technologies under discussion in the sequence of “big data, AI, and machine learning,” as in this book’s title.

## **SIMPLE VS. NARROW VS. GENERAL (STRONG)**

A number of adjectives are sometimes appended to AI that will not be addressed here because they refer to particular computer science approaches to developing AI, coined by particular computer scientists. Some are concrete, some are vague; many have been integrated into other terms. For the purposes of this discussion, we will categorize AI into three groups that expand in complexity.

Simple AI refers to what can also be called automated processes.^([27](#08_Introduction.xhtml#rfn_27)) In its broadest use, simple AI refers to machines that can do calculations through analog or digital functions faster than most humans could. From this perspective, a hand-held calculator could be described as simple AI.^([28](#08_Introduction.xhtml#rfn_28)) Most hand-held calculators are not, however, connected to sensors from which they can obtain their own data.

Phalanx CIWS is a simple AI machine that, in full-auto mode, makes a decision based on its own data collection whether to engage an incoming target—to shoot or not shoot. In this sense, it acts as a human would when provided with the same data. When set in a manual mode, CIWS does indeed require a human to press the firing trigger based on the data the system’s sensors provide, as well as any additional information the human operator can acquire from other sources. The reason for placing it in a fully automatic (or autonomous) mode is that the human operator cannot keep up with the speed of the engagement, or there is no human operator present. The danger in placing CIWS in a full-auto mode is that it might engage undesired targets, perhaps friendly aircraft, that are detected by its radar sensors and fit the parameters for which it is programmed to attack—speed of approach, flight profile, and other characteristics.

The difference between CIWS as simple AI and systems that constitute “narrow AI” is that CIWS is not a learning system. It cannot expand its knowledge base as to what is a target and what is not, but rather must conform to a decision-making rule set that it cannot alter until reprogrammed by humans. Hence, if a friendly aircraft with the same flight profile as an incoming enemy antiship cruise missile approaches the defending ship, it will be engaged. The CIWS unit will not learn from its “error” to distinguish between antiship missiles and friendly aircraft.

Narrow AI is the developmental level of current AI systems. “Narrow” refers to the fact that the AI machine can learn and self-program, but only to perform a narrow or specialized range of activities. It is also called, though less often, “modular AI” or “weak AI.”^([29](#08_Introduction.xhtml#rfn_29)) Winning against chess or iGo masters would be considered a narrow range of activities. All current applications of AI that involve machine learning remain narrow AI. Several narrow applications can be combined in one AI machine but not yet in a single neural network.

General AI or general intelligence AI—also known as strong AI—characterizes systems that mimic human awareness and have the ability to make decisions concerning multiple tasks or concepts. Instead of limited to chess or iGo, the AI machine can make decisions in a multiplicity of domains—similar to human multitasking. However, doing so generally requires some degree of mobility for the system to position itself at the site where the decision needs to be made—hence the close association of general/strong AI and autonomy. This association evokes the image of the film villain “the Terminator,” an autonomous system that appears human-like in its decision-making and actions but is programmed to achieve one particular result at all costs.

Mercifully, the ability to create a Terminator remains far out of reach for two reasons: the current programming characteristics have not yet developed a system with deep enough layers to make decisions in multiple domains (which would require many millions of lines of code), and engineering capabilities cannot make a device that can mimic and control all the moves of the human body (some can be mimicked, but not all, because human movement is biochemically, not mechanically, controlled). Could a Terminator-like humanoid be constructed someday? Perhaps, but it would require significant advances in biochemistry and other fields besides AI.

Such advancements are funded in the civilian sector primarily if there is a profit to be made. Currently, there are not such incentives to create general AI while narrow AI functions adequately to perform commercialized tasks. Even such virtual personal assistants as Siri or Alexa, which can seem human-like because they have natural language processors (understanding and replying in spoken languages), constitute narrow AI. They can perform rapid fact searches on the Internet or turn electrical/electronic devices on and off, but they are still narrow AI with limits to their functions.

In the military sector, today’s AI-driven systems that possess autonomy are largely simple AI, only bordering on narrow AI. The third offset strategy or third revolution in military affairs that is discussed by national security professionals (particularly in [chapter 2](#10_Chapter02.xhtml)) is primarily focused on increasing the application of narrow AI in military operations, not striving for general AI. The third offset also acknowledges that the U.S. military needs to leverage commercial AI advances in order to develop military applications. Given the amount of resources required and the fact that profit drives development, military applications are highly dependent on ongoing commercial development of AI. The Chief of Naval Operations acknowledged this fact in the 2018 Navy future fleet development plan, *A Design for Maintaining Maritime Superiority, Version 2.0.*^([30](#08_Introduction.xhtml#rfn_30))

## **AI AND AUTONOMY**

Autonomous systems are *not* synonymous with AI. Autonomous systems—machines that can operate without physical human intervention—are relatively rare and, more importantly, are preprogrammed to perform tasks, not to make independent decisions. Autonomous vacuuming devices may reverse course when they bump into walls or furniture, but they do not actually recognize walls or furniture; they are simply programmed to reverse or change to another preprogrammed course on any impact (including with children, dogs, and cats). Without that feature, they are similar to mechanical battery-operated toys with wheels or tracks that can offset, which have existed for decades.

Simple AI—as it is defined—does exist in military systems and has existed for several decades. Our previous example of Phalanx CIWS is but one form. Another is the Mk 60 Captor mine, a Cold War–era naval moored mine. Moored on the seabed, Captor had sensors that could detect submarines and, without the need for human decision-making, launch a torpedo against the target. Using set parameters, Captor, like other bottom mines, could distinguish between targets and nontargets. The human decision-making involved was simply to determine where to place the mine. Thus, Phalanx and Captor are both examples of simple AI that are autonomous (within prescribed limits).

The difference between Captor and an improvised explosive device in Afghanistan or Iraq is that, unless electrically or remotely controlled via cell phone by an observer, the latter (a land mine) cannot distinguish between a U.S./allied convoy, a humanitarian nongovernmental organization vehicle, or a terrorist-filled “technical” (pickup truck). There is no autonomous programming involved.

The term autonomous is also associated with unmanned vehicles (UVs). However, most military UVs utilized thus far have *not* been autonomous. Rather, as with the feared Predator or Reaper unmanned aerial vehicles, they have been remotely controlled by military personnel (humans) with limited support from narrow AI-processed intelligence (and a lot of human-processed intelligence). It is not that unmanned vehicles cannot be designed to be primarily autonomous but rather that there is considerable reluctance to trust their decision-making in that mode.^([31](#08_Introduction.xhtml#rfn_31)) Additionally, successfully adding narrow AI is a difficult and expensive engineering process.

The relationship between autonomy and AI is again similar to a Venn diagram. Both overlap, but the degree of overlap will be determined by future advances in AI and whether the third offset strategy comes to fruition.

## **AI AND WARFIGHTING**

The third offset strategy will be discussed in detail in later chapters. In short, it is an attempt by the United States and her allies to harness commercial developments in AI (and other emerging technologies) so as to remain ahead of military peer competitors in an international system defined by great power competition. “Third” refers to the fact that the United States is perceived to have leaped ahead of past military competitors by developing nuclear weapons and then precision-guided weapons. As noted, increasing the use of AI (and autonomous systems) is one of the goals of the third offset.

Thus far, programs supporting the third offset have focused on narrow AI because, for both moral and practical reasons, U.S. defense decision-makers and the American public are uncomfortable with contemplating general/strong AI weapons systems. Autonomous narrow AI weapons systems also remain, as noted, controversial in nations in which public opinion controls government. This will also be examined in a later chapter. However, authoritarian governments may not be so reluctant. Russia, in particular, is assessed as having developed *and* deployed several completely autonomous armed land combat systems.^([32](#08_Introduction.xhtml#rfn_32)) China is reportedly overtaking the United States in commercial AI development, although the effects on its military programs remain largely unknown.^([33](#08_Introduction.xhtml#rfn_33))

Areas in which current commercial AI could be used for military functions include photoreconnaissance analysis (and other imaging) and speech translation. These tasks fit narrow AI because they constitute pattern recognition of big data sets. In an earlier article, one of our chapter authors advised that “the Navy should invest in \[AI\] capabilities for tasks with rules or patterns that are predictable and difficult to disrupt, and should avoid automating tasks with rules and patterns that change unpredictably.”^([34](#08_Introduction.xhtml#rfn_34)) Rules and patterns that are predictable are the elements that enable AI to beat chess and iGo masters. The rules of these games do not change in the middle of these matches, even if a tremendous number of patterns must be recalled.

Can AI be used in unpredictable situations of chaos on the battlefield or to partially dispel the fog of war? Many experts argue yes, although they also admit that there can be no such thing as “perfect AI” and that “useful AI generates *good enough* results *at least* a little faster, better, or cheaper than those produced by human intelligence.”^([35](#08_Introduction.xhtml#rfn_35)) Of course, if one is onboard a warship seconds away from the impact of an enemy’s antiship missile and is trusting an AI machine to provide for the last-minute defense, “perfect AI” would be the desire. This is one reason for exploration of the use of AI for human-machine teaming in warfighting, a point particularly emphasized in [chapter 2](#10_Chapter02.xhtml). Imperfect AI may assist human decision-making, while relying on “perfect” AI to make its own decisions remains unreliable.

Whether in the form of pattern recognition in intelligence, weapons control, or human-machine teaming, AI will be a part of future military operations—just as it is and will be in commercial businesses. Examining exactly how AI can be applied to naval warfighting—without hype or alarm—is the objective of this book.

## **TASKS OF THE AUTHORS**

Working within the confines of unclassified information, each of the chapter authors or co-authors is charged with examining the applications and implications of AI to a discrete warfighting mission or function or series of related functions. Although this tasking may naturally evoke programs, projects, or studies that the authors are involved with on a day-to-day basis, they were asked to focus their writing on mission or function, not program.

Each of the authors was chosen because he or she is actively involved in developing, assessing, or advising on the applications of AI to naval warfare. Several were senior officials or commanders responsible for the command and control of forward-deployed combat forces. We have deliberately paired commanders, scientists, engineers, and program managers with national security analysts in order to ensure that discrete assessments *also* have broad background information so that the material is approachable by a nonspecialist. That does not mean that technical detail is avoided altogether; rather, we have attempted to place technical detail in contexts of combat operations and overall defense planning.

The goal for each chapter is to answer the question, “How could AI be applied to, support, or affect (or how has it already affected) a particular area of focus”—such as intelligence, command and control, integrated fires, strategic planning, deterrence, force development, operational decision-making, or deception—in other words, how could it work? What would be the results? What would be the dangers? Implied are three subordinate questions. First, does the application of AI to the focus area provide us with a new capability, make existing capabilities process faster, or simply replace manpower or reduce costs? Second, what assumptions, costs, and risks are involved in applying AI to that particular mission, function, or area of focus? Third, are the costs and risks worth it, or are alternate methods just as effective in achieving desired results? Indeed, recent defense workshops have suggested that some inputs to decision-making in war are too complex—using current techniques—to be adequately coded, or simply do not fit a logical pattern that can be considered rational thought. These are also themes with which the chapter authors grapple in their individual assessments.

## **STRUCTURE OF THE BOOK**

Many edited volumes result in a disconnected sampling of subtopics related to the general theme but not to each other. We have attempted to apply more discipline to this work. This book is structured into three associated segments. Following the foreword and introduction, the first series of chapters focuses primarily on the desired objective of introducing AI into naval operations, from a very broad perspective to one increasingly more specific.

Readers should note, however, that some of the chapter authors disagree with other authors. Although such differences are identified within the chapters, the editors have—by design—made *no* effort to seek agreement between the authors. It is important for readers to be well aware of the varying perspectives and disputes concerning the applicability of AI if they are to come to their own conclusions on AI’s effects on naval and joint warfighting.

[Chapter 1](#09_Chapter01.xhtml) provides a theory and conceptual history of AI and machine learning, written from the perspective of computer scientists who support research toward the development of general or strong AI. The authors describe machine learning programs as a form of applied statistics made possible by advances in computing hardware—a necessary advance in the application of technology to correlating big data—but not in itself constituting artificial intelligence. They argue that many of the algorithms applied to the probabilities that form the results of machine learning programming were developed long before the search for AI began.

[Chapter 2](#10_Chapter02.xhtml) examines AI and related technologies as elements of the third offset strategy and in the context of developments by potential adversaries. The author was one of the foremost champions of the third offset approach and the potential for AI applications during his past service as deputy secretary of defense.

[Chapter 3](#11_Chapter03.xhtml) reflects on (although does not constitute) the current official view of the Department of the Navy (Navy and Marine Corps) concerning its commitment to develop, fund, and implement AI. It is written by two serving Department of the Navy officials with the understanding that it is their own personal assessment of the department’s efforts. Even if the official view changes in the future, many of its premises will remain a part of the public debate on providing for national security.

[Chapter 4](#12_Chapter04.xhtml) assesses the relationship between robotics, autonomous weapons systems, and AI. This is the relationship that confuses and creates great fear in the critics of military use of AI. The author has previously published his own work on military AI, particularly in land combat.

[Chapter 5](#13_Chapter05.xhtml) provides insights from surveying the current analyses of the AI programs of potential military opponents, notably the People’s Republic of China and Russia. Relying on the work of the top researchers of foreign military AI, this chapter identifies the differing approaches of the AI “great powers.”

[Chapter 6](#14_Chapter06.xhtml) identifies the requirements for AI if it is to facilitate practitioner innovation and adaptation in crises and combat. Often forgotten in discussions on AI is that its effective use in military operations will be determined *more* by the operators than by the programmers/coders.

[Chapter 7](#15_Chapter07.xhtml) discusses the opportunities of utilizing AI for supporting and increasing the speed of decision for mission command, defined as “the conduct of military operations through decentralized execution based upon missiontype orders.”^([36](#08_Introduction.xhtml#rfn_36))

The second section of the book examines the application of AI to specific naval warfighting functions or “warfare areas,” along with effects it might have on fleet structure and the education of personnel. Starting with an overview ([chapter 8](#16_Chapter08.xhtml)), these areas include intelligence, surveillance, and reconnaissance ([chapter 9](#17_Chapter09.xhtml)), communications ([chapter 10](#18_Chapter10.xhtml)), command and control ([chapter 11](#19_Chapter11.xhtml)), and integrated fires ([chapter 12](#20_Chapter12.xhtml)). [Chapter 13](#21_Chapter13.xhtml) examines both the impact and requirements of AI on future military and naval force structure, to include the personnel aspect.^([37](#08_Introduction.xhtml#rfn_37)) In doing so, the chapter touches on the issue of whether the services can recruit and retain servicemembers with high-value cyber and AI skills.^([38](#08_Introduction.xhtml#rfn_38)) [Chapter 14](#22_Chapter14.xhtml) takes a deeper dive into the role and requirements of AI in naval education, specifically the education of midshipmen at the U.S. Naval Academy. [Chapter 15](#23_Chapter15.xhtml) uses a case study of an attempt to develop a modest decision aid for operational commanders to examine both the opportunities and limits of AI in fulfilling the operational requirements.

The third and final section of the book examines the policy and strategy elements involved with naval application of AI and the effects on current and future national security.

[Chapter 16](#24_Chapter16.xhtml) discusses the use of AI in terms of the overall cybered conflict that is occurring even in our time of “peace” and the potential for deception to create AI vulnerabilities. [Chapter 17](#25_Chapter17.xhtml) examines the organizational and bureaucratic-political impediments to committing to AI, as well as the ethical concerns, particularly those involved with autonomous systems and human decision-making regarding the use of deadly force. Since ethical concerns over military applications of AI are also discussed throughout many of the other chapters, the book does not include an individual chapter solely on AI ethics. By design, this choice was intended to mainstream this critical issue—not isolate it.^([39](#08_Introduction.xhtml#rfn_39))

[Chapter 18](#26_Chapter18.xhtml) identifies the impact of AI on naval strategy and tactics now and in the future. [Chapter 19](#27_Chapter19.xhtml) provides a scientific perspective on the general future of AI. Finally, an epilogue and an afterword provide practitioners’ perspectives on what this general future may mean to the naval services and what research is needed to continue this discussion.

Thus, the book begins its voyage with definitions, origins, requirements, and objectives; then sails into specifics; examines storms, shoals, and strategic effects; and ultimately provides possibilities and options for the future. One might shorthand the three segments as the promises, the particulars, and the problems.

## **INDIVIDUAL EFFORTS, PROXIMATE OBJECTIVE, CONTINUING PROCESS**

This book is built primarily around collaboration between members of two U. S. naval organizations, the U.S. Naval War College (NWC) in Newport, RI, and the Naval Information Warfare Center Pacific (formerly the Space and Naval Warfare Systems Center Pacific), in San Diego, CA. The organizational affiliations of authors at NWC include the Institute for Future Warfare Studies and the Cyber and Innovation Policy Center, both part of the Strategic and Operational Research Department of the Center for Naval Warfare Studies, the research arm of NWC. Additionally, authors include individuals from the Chief of Naval Operations Assessments Division (OPNAV N81) and its campaign analysis branch, located at the Pentagon; the U.S. Naval Academy, Annapolis, MD; the Oceanit Company of Honolulu, HI; the Leidos Corporation, headquartered in Reston, VA; the Center for a New American Security (CNAS), Washington, DC; the Center for Strategic and Budgetary Assessments (CSBA), Washington, DC; and retired flag officers of the U.S. Navy and senior DoD officials.

However, no matter the affiliation, all the authors worked exclusively on their own account and from their own perspective. Although current U.S. government policies are discussed, this book is decidedly not an official publication of the U.S. government or of any of the affiliated departments, agencies, or organizations. As the standard disclaimer reads: The views expressed in these chapters are those of the authors and do not necessarily reflect the official policy or position of the Department of the Navy, Department of Defense, or the U.S. Government.

The proximate goal of this book is to promote an understanding of the assumptions, possibilities, issues, costs, risks, effects, impediments, alternatives, and requirements for the application of artificial intelligence and related sciences to the modern art of war and specifically to U.S. naval forces. Our view is that this is an understanding needed by all national security professionals, but also by the citizens of the United States, the nation that we serve, have served, and will continue to serve.

Through providing our analyses, we hope to contribute to what should be a continuing DoD and nationwide discussion of the applicability of AI to our future. From this view, this book is but a start to what should be an ongoing process of research, analysis, debate, agreement, and development. The only way to decide the future of artificial intelligence is through the application of human intelligence, and the only way to successfully leverage artificial intelligence for military applications is for the operational forces to clearly define the narrow AI tasks that are most important to support Sailors in the fleet and Marines in the fleet and field.^([40](#08_Introduction.xhtml#rfn_40))

### **NOTES**

# 1

Theory and Conceptual History of Artificial Intelligence

PATRICK K. SULLIVAN AND THE OCEANIT TEAM

**The fields of artificial intelligence (AI)** and machine learning (ML) have made significant strides in the past few decades; now they are ubiquitous in modern society. Although the terms are often conflated, AI is “experimental epistemology”—the science of creating a “thinking machine” by encoding in a computer program a theory of human knowledge.^([1](#09_Chapter01.xhtml#rfn1_1)) In contrast, ML is the application of trained statistical models to recognize correlations in big data to make predictions, classifications, and approximations for practical use. AI/ML systems can be found in applications ranging from mission-critical uses such as the control of weapons systems, manufacturing, and logistic systems, to whimsical uses such as Snapchat filters.^([2](#09_Chapter01.xhtml#rfn1_2)) Due to our tendency to bestow “intelligence” on any ML result, AI and ML are often conflated into a single category.^([3](#09_Chapter01.xhtml#rfn1_3)) However, these fields are different and in fact compete to answer a more fundamental question: “How can we make a computational system intelligent?”

Many ML practitioners have faith that intelligence can be achieved by “learning” (in actuality, mathematical curve-fitting) from data. From this perspective, the key to solving the problem is big data and better computation; if only we had infinite data and hyper-computation, we could train ML for infinite possibilities.^([4](#09_Chapter01.xhtml#rfn1_4)) However, others in the so-called good old-fashioned AI community contend that humans are equipped with “innate knowledge” for learning from small or sparse data and engaging in general problem solving so as to survive and thrive in zero-day (i.e., novel) situations, creating new explanations and understanding of the world.^([5](#09_Chapter01.xhtml#rfn1_5)) Therefore, no AI system will be genuinely intelligent unless it is preprogrammed with knowledge that would enable more human-style cognition.

In order to understand this divide, we must go way back to the beginning of the AI story. We need to appreciate and understand competing philosophies that frame the discussion today and that gave rise to the fields of AI and ML.^([6](#09_Chapter01.xhtml#rfn1_6)) While the philosophy is important, neither approach could be practically implemented without the theory and practice of computing, which was established in the twentieth century. Nevertheless, the philosophical differences dating back to antiquity illuminate the differences in the AI and ML fields.

## **THE PHILOSOPHY: EMPIRICISM VERSUS RATIONALISM**

Our story begins in classical Greece with Plato and his pupil Aristotle, who, respectively, founded the philosophies of *rationalism* and *empiricism* that are key to everything that follows. The difference between the two is captured visually in the Italian Renaissance artist Raphael’s famous fresco *The School of Athens*.^([7](#09_Chapter01.xhtml#rfn1_7)) Plato and Aristotle are centered; the former points upward to the abstract and the latter downward to the concrete in an allegory for the rationalism/empiricism distinction—a distinction that would come to define the difference between AI and ML.

The philosophy of empiricism dictates the dogma that all knowledge derives from experience. Empiricism is best summarized by the Peripatetic axiom first stated by Thomas Aquinas in the thirteenth century and further developed by seventeenth-century philosopher John Locke: *nihil est in intellectu, quod non prius fuerit in sensu* (“nothing is in the intellect which was not previously in the senses”).^([8](#09_Chapter01.xhtml#rfn1_8)) It asserts that knowledge is acquired gradually through the formation of associations of external stimuli, and so the structure of knowledge “\[consists\] of links connecting \[concepts formed from sensedata\] with various other related concepts, essentially giving a sense of where \[a\] concept is located in ‘conceptual space’ by saying what it most resembles” in form and/or matter and/or space and/or time.^([9](#09_Chapter01.xhtml#rfn1_9))

The philosophy of empiricism has evolved over time. In classical Aristotelianism and Enlightenment empiricism (circa seventeenth/eighteenth century), it was asserted that “the world is structured in a certain way and that the human mind is able to perceive this structure, ascending from particulars to species to genus to further generalization and thus attaining knowledge of universals from perception of particulars.… We must possess an innate capacity to attain developed states of knowledge, but these are,” in Aristotle’s words, “neither innate in a determinate form, nor developed from other states of knowledge, but from sense perception.”^([10](#09_Chapter01.xhtml#rfn1_10)) This thesis would appear many times over the course of history, including the dominant theories of B. F. Skinner’s twentieth-century behaviorist psychology and twenty-first-century ML.^([11](#09_Chapter01.xhtml#rfn1_11))

![Photo 1-1. The School of Athens. In the original fresco, Plato and Aristotle are robed in red and blue, respectively. Their philosophical differences underpin the differences today between artificial intelligence and machine learning. ¶ Located at Apostolic Palace, The Vatican. Photo by Patrick J. Bayens, used with permission](images/pg26_1.png)

**Photo 1-1**. The School of Athens. In the original fresco, Plato and Aristotle are robed in red and blue, respectively. Their philosophical differences underpin the differences today between artificial intelligence and machine learning. ¶ Located at Apostolic Palace, The Vatican. Photo by Patrick J. Bayens, used with permission

While the adherents of empiricism vary in their beliefs, the common core tenet is that knowledge comes from drawing linkages between experiences. Therefore, a computational system (for example, a person or artifact) with the ability to make these connections can gain knowledge by being provided with enough examples/experiences/data to make the necessary connections.

Unlike the empiricists, *rationalists* argue that knowledge has a component that is fundamentally innate. Theories of this innate component have changed over time. Plato proposed that we have an innate knowledge of “Forms” (mathematical objects, Goodness, Beauty, etc.). During the Enlightenment, René Descartes argued that knowledge of the self was innate, while G. W. Leibniz thought mathematical logic was. Today, Noam Chomsky has espoused a rationalist philosophy in which knowledge of language is genetically endowed.

While ideas of precisely what type of knowledge is innate will differ, the rationalist theory is that our experiences are determined, codified, and understood using these innate components—in modern terms, “the extraction from experience of symbolic representations, which are carried forward in time by a symbolic memory mechanism, until such time as they are needed in a behavior-determining computation.”^([12](#09_Chapter01.xhtml#rfn1_12)) The extraction of information from experience necessitates innate modules—computational machinery of information extraction, representation, manipulation—specific to the domain of information to be extracted. It logically follows that knowledge acquisition is possible if, and only if, the mind is genetically endowed with representations of possible messages communicable by the environment and *abductive* (not *inductive*) algorithms. In inductive reasoning, a specific observation leads to a general conclusion. In abductive reasoning, incomplete information leads to a prediction. (In deductive reasoning, a general rule leads to specific conclusions.)

Thus, rationalism “shifts the burden of explanation from the structure of the world to the structure of the mind.” In the words of seventeenth-century rationalist philosopher Ralph Cudworth, “What we can know is determined by ‘the modes of conception in the understanding’ …; what we do know, then, or what we come to believe, depends on the specific experiences that evoke in us some part of the cognitive system that is latent in the mind.” As Cudworth explains, “The mind has an ‘innate cognoscitive power’ that provides the principles and conceptions that constitute our knowledge, when provoked by sense to do so.”^([13](#09_Chapter01.xhtml#rfn1_13))

The key difference between rationalism and empiricism, and the cause of the divide, is whether knowledge has a substantial innate component. This debate would persist for centuries. Locke, the empiricist, would quote Aquinas, saying that “there is nothing in the intellect that was not first in the senses,” to which seventeenth-century German mathematician Gottfried Leibniz, a rationalist, would reply, decisively, “except the intellect itself.”

The conflict between rationalism and empiricism persists to this day. It would take another invention, artificial computers, to turn differences in philosophy into differences in methods.

## **THE MEDIUM OF AI: THE THEORY AND PRACTICE OF COMPUTING**

The most vehement of supporters of AI and ML agree on very few things. However, both groups rely on the same underlying theory of computation and the associated hardware. Indeed, only after the introduction of the theory and hardware needed for computation could either field really begin to make strides.

One of the first, and most critical, questions in computing is determining which problems a computer can solve and which it cannot. The eminent German mathematician David Hilbert posed a variant of this problem in 1928. His “decision problem” (*Entscheidungsproblem*) was to formulate a procedure (*Entscheidungsverfahren*) that in a finite number of steps would decide the validity of any given logical expression. More generally, from a logical formalism of finitely specifiable axioms and theories, such a procedure would decide—*compute*, hence *explain*—potentially infinite nonarbitrary sets of theorems and data in systems of the formal and natural sciences. Such a formalization would approach realization of “Leibniz’s dream.”^([14](#09_Chapter01.xhtml#rfn1_14)) Leibniz, one of the greatest mathematicians and philosophers in history, “dreamt of an encyclopedic compilation, of a universal artificial mathematical language in which each facet of knowledge could be expressed, of calculational rules which would reveal all the logical interrelationships among these propositions. Finally, he dreamed of machines capable of carrying out \[these\] calculations.”^([15](#09_Chapter01.xhtml#rfn1_15))

Centuries on from Leibniz, Hilbert challenged mathematicians to make the dream a reality: “Once \[this\] logical formalism is established one can expect that a systematic, so-to-say computational treatment of logical formulas is possible.”^([16](#09_Chapter01.xhtml#rfn1_16)) In short, all reasoning and knowledge could be automated, reduced to computation. It “only” remained to formalize the intuitive concept of *computability*. This was done in 1936 by Alan Turing, who is now, decades on from his death, finally and rightly being recognized as one of the greatest minds in history.

In 1936 Turing ended the Hilbertian program by proving that no general decision procedure exists. However, in its application to the decision problem, Turing’s mathematics formalized the intuitive concept of a computational machine. “What is a computation?” This elementary but profound question receives a profound but elementary and elegant answer in the form of a thesis—arguably a theorem conjectured and arguably proved by Turing—that a computation is a machine (now known as a universal Turing machine), essentially a computer program, which is an artifact of conscious and methodical—artificial—design. Turing’s theorem can be stated simply: To be computable is to be computable by a Turing machine.

A Turing machine is a mathematical object characterizing a class of numerical functions, the computable functions, to be formally identified with the informal concept of effectively calculable functions.

A Turing machine is a mathematical object (hence not subject to spatiotemporal constraints) represented functionally (i.e., only by analogy with a physical computer) as a system with three basic components: a finite program of rules, states (internal configurations), and discrete symbols; a bidirectional tape divided into cells to function for unbounded input/output and as an unbounded memory; and a read/write head that “moves” over the tape, decoding, encoding, and manipulating symbols on the tape. In a stepwise process analogous to proof construction, the machine generates outputs (analogous to theorems) given inputs (which, with initial conditions, form a set analogous to axioms) by returning (recursing) intermediate results (analogous to lines or lemmas) according to its programmed rules. With this elegantly elementary model of computation, the general concept of a formal system was established that could both generate and explain sets of theorems/data.

![Figure 1-1. The Turing Machine. A mathematical model of computation that defines an abstract machine that manipulates symbols on a strip of tape, following a table of rules.](images/pg29_1.png)

**Figure 1-1**. The Turing Machine. A mathematical model of computation that defines an abstract machine that manipulates symbols on a strip of tape, following a table of rules.

While a Turing machine is a mathematical abstraction of a computer, the von Neumann architecture—named after John von Neumann, a prodigious genius of mathematics, physics, and everything—would define the architecture of computer hardware that we are familiar with today. The report “First Draft of a Report on the EDVAC” (Electronic Discrete Variable Automatic Computer) in 1945 described the design for a digital electronic computer that stored computer programs in memory. While computers, difference engines, or other analytical machines had existed in some form or another for centuries, they were purpose-built machines, and changing the program a machine ran would often require physically changing the machine. The von Neumann architecture avoided this issue and paved the way for the more powerful machines that would enable AI, ML, and the storage and use of big data.

## **FROM PHILOSOPHY TO AI AND ML**

The combination of philosophy with the theory and mechanics of computation gave rise to the fields of AI and ML. Specifically, the empiricism of Aristotle gave rise to the field of ML while symbolic AI (and, later, anthronoetic AI, meaning AI that can explain the answers it gives) was born from the rationalism of Plato.

In 1950 Turing posed the profound philosophical question, “Can machines think?” and thereby inspired modern AI research—now known variously as symbolic AI or “good old-fashioned AI” (GOFAI)—whose genesis was a funding proposal in 1955 for a “Summer Research Project on Artificial Intelligence” (the first usage of the term “artificial intelligence”). The proposal stated, “The study is to proceed on the basis of the conjecture that every aspect of learning or any other feature of intelligence can in principle be so precisely described that a machine can be made to simulate it. An attempt will be made to find how to make machines use language, form abstractions and concepts, solve kinds of problems now reserved for humans, and improve themselves.”

This project blossomed into a research program pursued for about the next twenty years—an “AI spring” that seeded AI labs at MIT, Stanford, and beyond—with some notable advances (e.g., Allen Newell and Herbert A. Simon’s Logic Theorist and General Problem Solver programs, John McCarthy’s LISP programming language, Marvin Minsky and Seymour Papert’s proof of fundamental limits on “neural network” ML, Minsky’s theory of symbolic mental “frames,” Terry Winograd’s SHRDLU natural language understanding system, and others). A particularly important advance was Noam Chomsky’s formal theory of natural language—the flagship of the “cognitive revolution” of the 1950s, and the intellectual movement that would establish new disciplines of cognitive science, neuroscience, and linguistics. Chomsky overthrew the prevailing paradigm in cognitive science, behaviorism—which, ironically, has been resurrected (but uncorrected) in modern reinforcement learning ML.

Chomsky’s analysis of work applying behaviorist concepts to complex human and nonhuman animal behavior demonstrated that

the notion of reinforcement \[a key aspect of behaviorism; think Pavlov’s dog\] has totally lost whatever objective meaning it may ever have had. \[It\] has no clear content, functioning only as a cover term for any factor, detectable or not, related to acquisition or maintenance of … behavior.… Running through \[numerous\] examples, \[t\]he phrase “X is reinforced by Y (stimulus, state of affairs, event, etc.)” is being used as a cover term for “X wants Y,” “X likes Y,” “X wishes that Y were the case,” etc. Invoking the term *reinforcement* has no explanatory force, and any idea that this paraphrase introduces any new clarity or objectivity into the description of wishing, liking, etc., is a serious delusion. The only effect is to obscure the important differences among the notions being paraphrased. \[This\] is just a kind of play-acting at science.^([17](#09_Chapter01.xhtml#rfn1_17))

Chomsky’s mathematical theory and explanation of the computations the human mind must be running points to natural language as the greatest example of human creativity or, in fact the words of Enlightenment/Romantic philosopher Wilhelm von Humboldt, the “infinite use of fine means.” This is one of the reasons algorithms that can replicate natural language have been a fundamental effort in AI. The rationalist theory of the mind that Chomsky proffered created the intellectual ferment in which GOFAI evolved.

## **A THEORY OF THE MIND VERSUS EXPERT SYSTEMS**

We can understand now more explicitly how a theory of the mind is necessary if human-style AI is to be created. A computer program is a theory (written in a specific notation). Thus, an AI program is really a theory of the mind. So if you have the wrong theory of the mind (as, in our view, behavioristic ML does), you have the wrong program. The right theory, and hence the right program, should be based on the mathematical biolinguistics of Chomsky, the prime mover of the cognitive revolution (in fact, the “second cognitive revolution,” the first being the rationalism of the Enlightenment). Tragically, however, his profound insights were never effectively incorporated into AI for numerous reasons, the most determinative being the increasingly instrumentalist (i.e., engineering) philosophy of science in general. Researchers—and funders—became more interested in scientific theories for predictions and applications (e.g., the “shut up and calculate” dogma adopted by physicists, the “neural cartography” of imaging experiments in neuroscience, etc.) rather than explanations and understanding. Of course, that also (understandably) defines the attitude of the users and will undoubtedly define the ultimate perspective of the Department of Defense.

So while Chomsky’s theory continues to progress independently, the success of other GOFAI research programs was limited as the mission to create human-level/human-style AI crept into and stagnated in the design of expert systems. These systems, like the ML systems of today, are powerful but rigidly domain-specific programs with no pretense to the creativity and fluidity of general intelligence. In other words, without a theory of the mind, general or strong AI cannot be achieved, and we are left with the narrow AI of expert systems.

Through the search- and logic-based approaches typical of GOFAI, the standard architecture of an expert system comprises a knowledge base (KB), an engine for searching the KB, and a logical-inference engine. The KB is constructed by human programmers eliciting into explicit form the knowledge of a human expert in the domain in question (e.g., organic chemistry in the case of the DENDRAL system or medical diagnosis in the case of the MYCIN system).^([18](#09_Chapter01.xhtml#rfn1_18)) This knowledge is then encoded propositionally, typically in conditional “if-then” statements (as described in the introduction). The inference engine enables the system to “reason” deductively given propositions from the KB. In a simple example, the system computes a classic hypothetical syllogism, the conclusion “If x, then z” from the premises “If x, then y” and “If y, then z.” With some sophistication, the system could be programmed with decision trees/conditional branching to query the user for additional information to validate its deductions: “Is *x* true in this situation?” (e.g., “What is the molecular weight of H[2]O?” or “Does the patient have a fever?”); if the answer is affirmative, the system infers z.

Such a system can demonstrate some nontrivial capabilities if equipped with extensive knowledge and elaborate rules. For instance, the CYC expert system, started in 1984 as an attempt to duplicate human “common sense,” infers that “George is wet” (or “probably wet”) from the statement “George is finishing a marathon” by means of searching and reasoning over its KB of laboriously compiled commonsense knowledge. Such knowledge includes voluminous information, such as that running a marathon requires high levels of exertion, and that human beings sweat (or probably sweat) at high levels of exertion, and that when something sweats, it is wet. (CYC reasons essentially by inference.)

## **EXPERT SYSTEMS, CHESS, AND PUBLICITY IN THE 1990s**

The apotheosis of the expert system approach was Deep Blue, the IBM chess program that defeated the world champion Garry Kasparov in 1997. This event, trumpeted in the press as “the brain’s last stand,” brought an awareness of scientific advances in ML and narrow AI to the general public. Chess had been a holy grail of AI research since the 1950s, when Alan Turing himself enumerated it as one of a number of domains where we could test whether a machine could “think.” For him, a chess-playing program, based on an “introspective analysis” of his own thought processes when playing, could be one with the potential to transcend its specific expertise (capable of answering questions such as “tell\[ing\] one whether, in a given position, white has a forced mate in three”) to attain a general intelligence (capable of answering any “questions put to it, in such a way that it would not be possible to distinguish its answers from those of a human”).

Of course, as Turing observed, the program might outplay its programmer simply by dint of “the speed of the machine, which might make it feasible to carry the analysis … farther than a man could do in the same time.”^([19](#09_Chapter01.xhtml#rfn1_19)) In Turing’s view, however, such brute-force technique, so quantitatively and qualitatively different from human thinking, would be of no scientific interest. For Turing and GOFAI, “the attempt to make a thinking machine will help us greatly in finding out how we think ourselves.”

Deep Blue, alas, was not designed to emulate human-style thinking. It was an expert system running on superhuman hardware.

Deep Blue searched up to 30 billion positions per move, reaching depth 14 routinely. The key to its success seems to have been its ability to generate singular extensions beyond the depth limit for sufficiently interesting lines of forcing/forced moves. In some cases, the search reached a depth of 40 plies \[levels\]. The evaluation function had over 8000 features, many of them describing highly specific patterns of pieces. An “opening book” of about 4,000 positions was used, as well as a database of 700,000 grandmaster games from which consensus recommendations could be extracted. The system also used a large endgame database of solved positions containing all positions with five pieces and many with six pieces. This database had the effect of substantially extending the effective search depth.^([20](#09_Chapter01.xhtml#rfn1_20))

Contrast this with chess master Bobby Fischer’s style of play. As a thirteen-year-old, this paragon of human intelligence outwitted an adult chess master in the so-called game of the century, not by brute-force search, but with methods Turing used to characterize the many styles of human cognition: creative and linguistically mediated combinations of symbolically structured “gistifications” (i.e., abstract descriptions/explanations) of board positions. These representations are conjectures that can be subjected to criticism in a nonrandom “trial and elimination of error” process from which only the “fittest” conjecture (i.e., the best move) survives. This Darwinian epistemology is antithetical to unthinking brute force.

Despite the publicity and media hype of Deep Blue versus Kasparov, Noam Chomsky concluded correctly that “a computer beating a grandmaster at chess is as interesting as a bulldozer winning a weight-lifting competition.” Indeed, “\[t\]he huge improvement in computer chess” and other expert systems and ML programs “since Turing’s day owes much more to advances in hardware engineering than to advances in AI. Massive increases in CPU speed and memory have meant that successive generations of machines have been able to examine increasingly many possible moves. Turing’s expectation was that chess programming would contribute to the study of how human beings think. In fact, little or nothing about human thought processes appears to have been learned from the series of projects that culminated in \[and have followed\] Deep Blue.”^([21](#09_Chapter01.xhtml#rfn1_21))

Thus, the scope and limits of expert systems are all too obvious: the knowledge and rules in a human mind are significantly greater in sophistication and subtlety.

Who is taller, Prince William or his baby son Prince George? Can you make a salad out of a polyester shirt? If you stick a pin into a carrot, does it make a hole in the carrot or in the pin? These types of questions may seem silly, but many intelligent tasks, such as understanding texts, computer vision, planning, and scientific reasoning require the same kinds of real-world knowledge and reasoning abilities. For instance, if you see a six-foot-tall person holding a two-foot-tall person in his arms, and you are told they are father and son, you do not have to ask which is which. If you need to make a salad for dinner and are out of lettuce, you do not waste time considering improvising by taking a shirt out of the closet and cutting it up. If you read the text, “I stuck a pin in a carrot; when I pulled the pin out, it had a hole,” you need not consider the possibility “it” refers to the pin.… To achieve human-level performance in domains such as natural language processing, vision, and robotics, basic knowledge of the commonsense world—time, space, physical interactions, people, and so on—will be necessary. Although a few forms of commonsense reasoning, such as taxonomic reasoning and temporal reasoning are well understood, progress has been slow.^([22](#09_Chapter01.xhtml#rfn1_22))

The glacial pace of development has been referred to as an “AI winter” in which GOFAI seemed to have failed due to the inflexibility and unscalability of its knowledge bases. Symbolic AI ossified into expert systems that, like ML today, were powerful in specific domains, but, like ML, do not generalize to emulate the competence in language, explanatory and aesthetic creativity, causal modeling, commonsense reasoning, and analogy-making characteristic of human-level intelligence.

## **ALGORITHMS AND NEURAL NETWORKS**

For scientists committed to general AI, hope, like a cliché, springs eternal, as AI research did with the “advent” of connectionist artificial neural networks in the 1980s. These, with only trivial tweaks, are the algorithms—the so-called deep learning neural nets—fueling the AI spring (really an “ML spring,” because AI should be reserved for systems emulative of human-style intelligence) we are currently experiencing.^([23](#09_Chapter01.xhtml#rfn1_23)) These souped-up connectionist networks are effectively equivalent to standard statistical analysis. Deep learning curve-fits a function to big data, computing distribution functions from samples of properties. These systems are not models of general (human) intelligence. Nor are they accurate analogues of biological neural networks. Contrary to connectionist claims, the “neurons” and “synapses” in an artificial neural network are only a metaphor for the neurons and axons/synapses in a biological neural network. A biological neural network is so many orders of magnitude greater in quantity and quality than AI/ML as to defy any nontrivial comparison.

Deep learning (DL) AI/ML neural networks typically consist of a set of input units “representing” samples of pixels, words, etc.; multiple hidden layers (the greater the number of layers, the deeper the network) containing hidden units (those so-called nodes or neurons); and a set of interconnected output units/nodes.^([24](#09_Chapter01.xhtml#rfn1_24)) In a typical application, such a network is trained on big data sets of handwritten digits (input images) and labels (the outputs) that stipulate how those inputs are to be categorized (this image is a two, that image is a three, etc.). Over a potentially lengthy period of time, a back-propagation algorithm enables a gradient descent process to adjust the connections between units so that a given input tends to spit out the corresponding output.

This technique is admittedly powerful in solving closed-end classification problems, in which a wide range of potential signals must be mapped onto a limited number of categories, provided that there are sufficient (usually curated) data and the test set closely resembles the training set. Yet ultimately, the function of a neural network is simply to learn the relation—the mapping—between inputs and outputs.

Hence, we concur with Douglas Hofstadter that

an ambiguity \[an insidious ambiguity, we should say\] in the adjective “deep” is being exploited here. When one hears that Google bought a company called DeepMind whose products have “deep neural networks” enhanced by “deep learning,” one cannot help taking the word “deep” to mean “profound,” and thus “powerful,” “insightful,” “wise.” Yet, the meaning of “deep” in this context comes simply from the fact that these neural networks have *more layers* (12, say) than do older networks, which might have only two or three. But does that sort of depth imply that whatever such a network does must be *profound*? Hardly. This is verbal spinmeistery.^([25](#09_Chapter01.xhtml#rfn1_25))

## **EMPIRICISM + COMPUTING = ML**

Drawing from its roots in empiricist philosophy, the objective of most ML systems is to *learn* some way of ordering the data/examples/experiences provided to the system. In practice, one supplies the system with a general model and uses these data to determine the model parameters that apply to the current situation.

Since most ML algorithms are a form of applied statistics, the algorithms themselves often predate the existence of digital computers. For example, one of the most widely used data-fitting methods is the least squares method, which was proposed by Adrien-Marie Legendre in 1805 but is still used to this day. The most basic (and most common) unsupervised learning method, principal component analysis, can similarly trace its roots back to 1901. Other methods would be developed over time, often to correct a limitation observed in the previous generation of algorithms. For example, the term “classification and regression tree,” which is a generalized form of a decision tree, was first coined in 1984. However, these trees often had issues with overfitting data (i.e., modeling noise, not signal). To correct this issue, new algorithms that combined multiple decision trees were later developed, including the Random Forest algorithm in 1995 and gradient boosting trees in 1999. This pattern can be found frequently within the history of ML: first, a new type of algorithm is developed that solves a useful class of problems; second, as practitioners gain experience with the new approach, they identify its shortcomings, which yields a new set of algorithms designed to mitigate that limitation.

Ironically, probably the most famous technique at the current time, deep learning, has a history that traces back further than many of these simpler methods. Most of the theory and algorithms behind the deep neural networks of today can trace their roots to 1957. At that time, the perceptron, which is one of the simplest network structures, was invented. The algorithms used to train neural networks are similarly old, as the technique of (what would later be called) backpropagation was pioneered by the Finnish computer scientist Seppo Linnainmaa in the 1970s. Even the precursors to more sophisticated techniques, such as convolutional neural networks, trace their origins to the “neocognitrons” developed in the 1980s.

Due to hardware limitations of that era, the size of these early network structures was relatively small. However, improvements in computing power over time enabled ML researchers to ingest larger data (and even big data) and build more sophisticated models. This change, augmented by updated algorithms, has vastly increased the power of ML techniques and enabled them to meet or even exceed human-level performance in a variety of tasks. Ultimately, however, to say of these machines that they “learn” is a grievous misnomer.

## **ARTIFICIAL GENERAL INTELLIGENCE: COGNITIVE SCIENCE AND ANTHRONOETIC AI**

The combination of philosophy and computing has generated two different but useful classes of approaches. However, a limitation of the current set of approaches is that they are all problem-specific, and a truly intelligent system should not be restricted to just a single application. The dream of artificial general intelligence or strong AI, which is an artificial system with all the capabilities of a human, is an active research area pursued by both communities. This problem is more widely studied by symbolic AI researchers, and it is here they argue that empiricist approaches of ML begin to fail.

While the success of ML is undeniable, critics claim such systems will never be genuinely intelligent and should be contrasted with the strong AI (symbolic AI, good old-fashioned AI, general AI) that Turing envisioned but did not implement. To achieve strong AI requires a program designed to attain human-level competence with a human style typified by syntactic generativity, semantic fluidity, and the creation of causal models. This has not been pursued in ML research, which is primarily focused on improved task-specific performance, which is a form of weak (narrow) AI.

Strong AI—what we defined as anthronoetic (i.e., human-level/human-style) AI—conjectures explanations and subjects them to criticism (logical and experimental). These explanations derive not from statistics, but from the mathematical theory of structural causal models. The distinction is profoundly important. It entails the distinction between probability and degree of corroboration. This differs from the standard methodology in ML, which is to collect data and “induce” from them the most probable predictive model/theory, and we believe it is fundamentally flawed. ML is based on a continuous series of observations and trial and error until an acceptable approximate answer occurs. However, as the British philosopher of science Karl Popper explained: “Scientific theories were not the digest of observations, but inventions—conjectures boldly put forward for trial, to be eliminated if they clashed with observations; with observations which were rarely accidental but as a rule undertaken with the definite intention of testing a theory by obtaining, if possible, a decisive refutation.”^([26](#09_Chapter01.xhtml#rfn1_26)) In other words, “This was a theory of trial and error—of *conjectures and refutations*. … \[This theory\] made it possible to understand why our attempts to force interpretations upon the world were logically prior to the observation of similarities \[or dissimilarities\]” in data. In opposition to statistical-minded ML researchers, we concur with Popper: “Although we seek theories with a high degree of corroboration, *as scientists we do not seek highly probable theories but explanations; that is to say, powerful and highly improbable theories*.” This ought to be obvious. Popper continues, “The probability of a statement (or set of statements) is always the greater the less the statement says; it is inverse to the content or deductive power of the statement, and thus to its explanatory power. Accordingly every interesting and powerful statement must have a low probability; and *vice versa*!”^([27](#09_Chapter01.xhtml#rfn1_27))

ML aims for high probability of identification, but at the cost of limited explanation. Thus the approach of anthronoetic AI is not that assumed in ML—the (irrational and impossible) task of inferring a highly probable predictive theory/model from data to be verified by repeated observations. On the contrary, like the human mind genetically endowed with a universal grammar (the basis for general intelligence), an anthronoetic AI would be preprogrammed with a linguistic competence to generate conjectures that it can then criticize (possibly in collaboration with humans), subject to error correction, and test by observation—in the process transforming data into evidence corroborating or (preferably) falsifying the conjectured theory. As Karl Popper notes, “So long as a theory stands up to the severest tests we can design, it is accepted; if it does not, it is rejected. But it is never inferred, in any sense, from the empirical evidence\[…\]. *Only the falsity of a theory can be inferred from empirical evidence, and this inference is a purely deductive one*.”^([28](#09_Chapter01.xhtml#rfn1_28)) Why is this logic of critical rationalism (i.e., conjecturing/criticizing causal explanations) so unorthodox in modern “AI” (i.e., ML) research? It is because ML researchers have misunderstood the history of AI, particularly the Enlightenment renaissance of the Classical rationalism/empiricism debate and its resurgence in the modern strong AI (computationalist) versus weak AI (connectionist) debate.

## **FROM LEIBNIZ TO TURING AND BEYOND**

The mathematician and computer scientist Martin Davis describes the history of AI as “the road from Leibniz to Turing.” In this chapter, we have explained how that road can be mapped from Plato and Aristotle to the Enlightenment rationalists (including Leibniz) and empiricists to the Chomskyans and behaviorists of the twentieth century to asymbolic or anthronoetic AI and ML.

The goal of strong AI is to create an artificial system with the capabilities of a human. However, that raises the questions of whether machines can think and how one would know if they succeeded in constructing such a system. The issue is that a strong AI system is more than simply a mapping from inputs to outputs. Suppose we were somehow to enumerate explanations of, say, dark matter that would be acceptable outputs of the program. If the program did output one of those explanations, it would not prove the system was capable of novel thought. For none of those explanations would be new; we would already have created them ourselves in order to write the test. However, if it did not produce one of those explanations, we would doubt its capability. Rather than a test with “right” or “wrong” answers, Turing himself proposed a more subjective test. It was that (human) judges be unable to detect whether the program is human or not when interacting with it via some purely textual medium so that only its cognitive abilities would affect the outcome. However, that test, being purely behavioral, produces no evidence for how to satisfy the criterion. In any case, intelligence—human or AI—cannot possibly be defined purely behaviorally.

In contrast to any functionality that has ever been programmed, AI can be realized by neither a specification nor a test of the outputs. What is needed is nothing less than a revolutionary discovery in philosophy, a new epistemological theory that explains how brains create explanatory knowledge and hence defines, in principle (without ever running them as programs), which algorithms possess that functionality and which do not. Such a theory is beyond our present-day knowledge.

What we do know of epistemology implies that any approach not directed toward that philosophical discovery must be futile. What we know of epistemology is in the work of Karl Popper, which orthodox computational cognitive scientists and ML researchers do not understand (if they are aware of it all). For instance, it is still assumed in ML that knowledge consists of justified, true beliefs and that, therefore, an AI’s thinking must include some process whereby it justifies some of its theories as true (or probable), rejecting others as false (or improbable). But as philosophers/scientists/programmers, we need to know where the theories originate. The prevailing misconception is that by assuming that “the future will resemble the past,” it can “derive” theories from repeated experiences by the alleged process of “induction.” That is impossible. It is simply not true that knowledge emerges from extrapolating repeated observations. Nor is it true that “the future resembles the past” in any sense that one could determine in advance without already knowing the explanation. The future is actually unlike the past. Of course, given the explanation, significant “changes” in preceding patterns are understood as being caused by an invariant underlying pattern or law. But the explanation always comes first. Without that, any continuation of any sequence constitutes “the same thing happening again” under some explanation.

The conventional wisdom of ML adheres to the problem of induction, which asks, “How and why can induction nevertheless somehow be done, yielding justified true beliefs after all, notwithstanding its being impossible and invalid respectively?” This has the catastrophic effect of simultaneously framing AI as the “problem of induction” and defining thinking as a process of predicting that future patterns of sensory experience will be like past ones. That appears to be extrapolation—which computers already do all the time (once they are given a theory of what causes the data). In reality, only a micro-component of thinking is predictive, let alone prediction of our sensory experiences. We think about the world: not only the physical world, but worlds of abstractions such as right and wrong, beauty and ugliness, the infinite and the infinitesimal, causation, fiction, fears, and aspirations—and about thinking itself. Indeed, the truth is that knowledge consists of conjectured explanations—guesses about what really is out there in all those worlds (or really ought to be, or could be). Even in the sciences, these guesses have no foundations and require no justification. Why? Because real knowledge contains both truth and error. Thinking consists of criticizing and fixing partially true guesses rather than generating or extrapolating guesses made from partial data.

The barrier preventing us from achieving strong AI is due to a convergence of misconceptions. If one does not understand that the functionality of an (anthronoetic) AI is qualitatively different from any other program, one cannot work on AI. If one works toward programs whose “thinking” is constitutionally incapable of violating predetermined constraints, one is endeavoring to engineer away the sine qua non of intelligence: creative explanation.

Discovering the algorithm for creativity must ultimately not be all that difficult. This is so because, to reiterate, anthronoetic creativity is qualitatively different from anything in the known universe, and given that apes do not possess it and we do, the information for how to create it must be encoded in the relatively small number of differences between the DNA of humans and that of chimpanzees. However, it has yet to be discovered and, once it is, it will be the best idea ever.^([29](#09_Chapter01.xhtml#rfn1_29))

### **NOTES**

# 2

AI, Autonomy, and the Third Offset Strategy

**Fostering Military Innovation during a Period of Great Change**

ROBERT O. WORK

**The 2018 National Defense Strategy** calls on the Department of Defense (DoD) to pursue “urgent change at significant scale.”^([1](#10_Chapter02.xhtml#rfn2_1)) One reason for urgency was a growing sense that the United States was in danger of ceding militarytechnical superiority to resurgent or rising great powers. As the strategy put it: “We cannot expect success fighting tomorrow’s conflicts with yesterday’s weapons or equipment. To address the scope and pace of our competitors’ and adversaries’ ambitions and capabilities, we must invest in modernization of key capabilities through sustained, predictable budgets.”^([2](#10_Chapter02.xhtml#rfn2_2)) Among the key capabilities that the strategy highlighted were advanced autonomous weapons systems. Specifically, the strategy declared, “The Department will invest broadly in military application of autonomy, artificial intelligence, and machine learning … to gain competitive military advantages.”^([3](#10_Chapter02.xhtml#rfn2_3)) This passage was a direct echo of the department’s so-called third offset strategy (3OS). This chapter aims to explain the thinking behind the 3OS and its emphasis on autonomy and artificial intelligence.

## **THE DEFENSE INNOVATION INITIATIVE**

One cannot fully understand the third offset strategy without first talking about the defense innovation initiative (DII). After the Cold War ended, U.S. defense strategy focused on shaping the international environment in ways conducive to American national interests, preventing the spread of weapons of mass destruction, and deterring and responding to acts of violence and aggression by regional powers. After September 11, 2001, counterterrorism and stabilization of “ungoverned territories” were added to the list. Great power competition was thought to be a thing of the past.

By early 2014, however, China had begun to reclaim rocks and awash features in the South China Sea, and Russia illegally annexed Crimea and destabilized eastern Ukraine. These activities were typical of authoritarian great powers working to secure their “near abroads.” They provided stark evidence that great power competition was once again something the Department of Defense would have to consider and deal with. Moreover, a key aspect of this emerging competition would involve a struggle for military-technical superiority, something the joint force had enjoyed since the end of the Cold War.

In response, in November 2014 secretary of defense Chuck Hagel announced the DII, an explicit response to the return to great power competition and a renewed struggle for technological superiority.^([4](#10_Chapter02.xhtml#rfn2_4)) In its original form, the DII had seven explicit lines of effort (LOEs):

1.  *Develop strategies for a long-term strategic competition with great powers*. Secretary Hagel intended the DII to represent a clear break with post–Cold War defense strategies, replacing them with one focused on a long-term strategic competition with China and Russia. Although the department developed new competitive strategies for both countries in support of LOE 1, they came too late in the Barack Obama administration to make any mark. Accordingly, the 2018 National Defense Strategy is best thought of as the end result of this line of effort.

2.  *Develop new operational concepts and organizational constructs for military advantage*. LOE 2 called on the four services to explore, develop, and pursue new technologically enabled operational concepts consistent with potential military operations against near peers and the new organizational constructs they would inspire. The DII recognized operational concepts were a key driving force behind military innovation, as they often spur the development of new systems, doctrine, tactics, techniques, and procedures, and organizations. Multidomain operations, distributed maritime operations, and expeditionary advanced base operations are all new operational concepts that can trace their lineage to LOE 2. The department also initiated a Russia strategic initiative, based on the highly successful China strategic initiative established by Pacific Command.^([5](#10_Chapter02.xhtml#rfn2_5)) These initiatives gave commanders of both European and Pacific Commands a forum to discuss deterrence and warfighting strategies, new operational concepts, and desired new operational capabilities with senior departmental leaders, and to influence programmatic choices.

3.  *Develop a competitive strategy to preserve and widen technological superiority*. The joint force has consistently sought military-technological superiority since the end of World War II and enjoyed it outright since the end of the Cold War. By 2014, however, a review of Chinese and Russian technological advancements since 2000 suggested U.S. tech superiority in high-end conventional warfare was steadily eroding after more than a decade focused on counterterrorism operations and irregular warfare. LOE 3 sought to change the trend lines. Its key component would be a new long-range research and development planning program (LRRDPP), conducted by the assistant secretary of defense for research and engineering and patterned after a similarly named effort in the early 1970s.^([6](#10_Chapter02.xhtml#rfn2_6)) The earlier LRRDPP was initiated to contend with a contemporary Soviet challenge to U.S. conventional superiority in the European theater of operations.

4.  *Expand wargaming and experimentation*. The DII assumed that war-gaming and field experimentation, which had atrophied across the department since September 11, would be essential ways to illuminate both military-technical solutions to emerging operational challenges and the new operational concepts to address them.^([7](#10_Chapter02.xhtml#rfn2_7)) This LOE led to the establishment of the wargaming incentive fund, which augmented service resources to stimulate additional gaming initiatives, especially those focused on operational challenges posed by the two great powers.^([8](#10_Chapter02.xhtml#rfn2_8)) This fund was later expanded to include a warfighting incentive fund, designed to augment service resources for field experiments designed to test new operational concepts.^([9](#10_Chapter02.xhtml#rfn2_9)) The results of both efforts were maintained in a new wargame repository in the cost analysis and program evaluation directorate and briefed to senior departmental leaders during the annual program review.

5.  *Improve capability information management*. In a military-technical competition, emergent capabilities are sometimes revealed to competitors to strengthen deterrence. Other times, they are concealed from rivals in hopes of securing a warfighting advantage should deterrence fail. This LOE would make recommendations to departmental leadership to either reveal or conceal new capabilities as they were developed and fielded.

6.  *Improve DoD and intelligence community integration*. It became immediately apparent that the DII would fail unless there was close collaboration between the department and the intelligence community. This led to the formation of the advanced capabilities and deterrence panel (ACDP), chaired by the deputy secretary of defense, the vice chairman of the joint chiefs of staff, and the principal deputy to the director of national intelligence. The ACDP oversaw all DII LOEs and the development of new capabilities associated with them, assuring tight departmental coordination with the intelligence community.^([10](#10_Chapter02.xhtml#rfn2_10))

7.  *Expand the number of concerned stakeholders*. This line of effort focused on the public outreach to the White House, Congress, and defense industry to explain the DII and its aims.^([11](#10_Chapter02.xhtml#rfn2_11)) One key output of this LOE was the “overmatch brief,” prepared by the RAND Corporation in support of the Office of Net Assessment. This classified brief used large, easy-to-understand graphics to explain Chinese and Russian military advances and how they would challenge and stress the joint force should a serious military confrontation occur. The brief was presented to members of the National Security Council and members of the Senate and House Armed Services Committees.

## **THE THIRD OFFSET STRATEGY IN CONTEXT**

As an integral part of the DII, the third offset strategy emerged as part of line of effort 3. In other words, the term was originally meant as shorthand for a competitive strategy to achieve and maintain technological superiority. It was not associated with LOE 1. This was a source of continual confusion, as several commentators—then–secretary of defense James Mattis among them—rightfully pointed out the 3OS was not a fully formed national defense strategy.^([12](#10_Chapter02.xhtml#rfn2_12)) Moreover, in hindsight, the term also became shorthand for the entire DII. This was equally unfortunate, as the initiative was never intended to be solely about technology. Instead, as its name suggested, the DII sought to foster military innovation in a time of great geopolitical and technological change. With its call for “urgent change at significant scale” in strategic approaches, operational concepts, and technological solutions, the 2018 National Defense Strategy helped reduce the earlier confusion by encompassing virtually all of the DII LOEs into one overarching strategic document.

The term “third offset strategy” was a historical reference and nod to the two previous technological offset strategies pursued by the United States during the Cold War. In the 1950s, the United States confronted a clear-cut Warsaw Pact numerical superiority in conventional forces with a smaller Army armed with battlefield atomic weapons. After the Soviet Union achieved strategic parity with the United States in the 1970s, however, the threat of U. S. forces in Europe employing tactical nuclear weapons to stop a Warsaw Pact invasion was far less credible. Consequently, the United States sought to offset Warsaw Pact numerical superiority by developing a new generation of conventional guided munitions and submunitions and the operational battle networks that employed them. These powerful guided munitions battle networks could achieve the same battlefield effects as tactical nuclear weapons. They thus helped strengthen conventional deterrence and helped end the Cold War on terms favorable to the United States and its North Atlantic Treaty Organization allies.

Once the Soviet Union collapsed, and before Russia’s resurgence and the rise of China, the U.S. lead in guided munitions battle network warfare gave the joint force an overwhelming conventional advantage against regional powers, as was demonstrated in Operation Desert Storm of 1991.^([13](#10_Chapter02.xhtml#rfn2_13)) However, twenty-five years after Operation Desert Storm, both China and Russia were steadily shrinking the U.S. lead in guided munitions battle network warfare. Both wanted to “look, shoot, and kill deep” with the same effectiveness as the U.S. joint force. And they were developing their own theater-wide battle networks to do so. The Russians call their battle networks reconnaissance-strike complexes; the Chinese refer to them as operational systems.^([14](#10_Chapter02.xhtml#rfn2_14)) The joint force tends to refer to both by emphasizing what they are designed to do: contest U.S. military access to their respective theaters and deny the joint force operational freedom of action once there. Consistent with this aim, the joint force refers to both as anti-access/area denial networks.

Dr. Andrew Marshall, the late director of the Office of Net Assessment, would say the proliferation of guided munition battle networks had resulted in a “mature revolutionary regime,” in which all the major competitors enjoyed a measure of parity in “the existing means for conducting war.”^([15](#10_Chapter02.xhtml#rfn2_15)) Militarytechnical parity is not something the U.S. joint force has had to contend with for more than three decades, and its emergence comes with troubling consequences. Parity in second offset technologies works to undermine America’s ability to project power abroad—not a good thing for a global superpower used to projecting decisive military force into distant theaters around the globe.

This circumstance spurred the aforementioned defense innovation initiative. Once again, the DII never intended to seek a technological “silver bullet.” It instead sought to spur the development of new technologically enabled concepts of operations and organizational constructs that would afford the joint force an advantage in guided munitions battle network warfare.^([16](#10_Chapter02.xhtml#rfn2_16)) As part of the DII, the third offset strategy was designed to illuminate the technological advancements that might lead to these new operational concepts.

The strategy’s immediate objective was to “stop the bleeding” and arrest the erosion of U.S. military-technical advantage by spurring a sharp improvement in guided munitions battle network performance in the near to mid-term.^([17](#10_Chapter02.xhtml#rfn2_17)) If, by doing so, it triggered a broader military-technical revolution that afforded the joint force a measure of operational superiority for a longer period of time, so much the better.

## **IMPROVING BATTLE NETWORK PERFORMANCE**

Despite their different names, battle networks, reconnaissance-strike complexes, and operational systems all represent large systems-of-systems with a digital backbone and at least four common, interconnected grids:

•  a multi-phenomenology *sensor grid* that “looks deep” and continually surveils the battlespace in every operating domain—space, air, sea, undersea, ground, cyberspace, and the electromagnetic spectrum

•  a *command, control, communications, computers, and intelligence (C4I)grid* that works to make sense out of the mountain of data and information collected by the sensor grid; develop a multidomain common operating picture; develop commander’s intent and courses of action to achieve specific battlefield aims and effects; select among the courses of action and develop final battlefield plans; and promulgate commander’s intent and orders to the joint and allied forces that execute the plan(s)

•  an *effects grid* that applies the kinetic and nonkinetic effects ordered by the C4I grid

•  a *sustainment and regeneration grid* designed to sustain battle network operations in combat and regenerate combat losses or damage.

The Chinese add a fifth grid, the *information contestation grid*, consistent with their theory of victory in guided munitions battle network warfare: system destruction warfare. Their thinking is that the side that can best hobble, disable, or destroy the opposing operational system will gain an information and combat advantage that makes victory all but inevitable. Their information contestation grid employs all available counternetwork capabilities—such as counter-space, -cyber, –electronic warfare, -information, and -deception operations—to render opposing operational systems ineffective.

To achieve a sharp increase in overall battle network performance, the 3OS focused first on improving the operation of each grid in the joint battle network grid. The question became: what technological approach might best achieve this end?

A 2014 defense science board summer study and the aforementioned LRRDPP, conducted in late 2014 and early 2015, concluded that improved autonomous systems, platforms, and operations in all grids and across all operating domains promised a tipping point in battle network performance and warfighting effectiveness. If the department wanted to reach this tipping point, the most important technology it had to pursue and dominate was in the realm of artificial intelligence (AI), as rapid advances in AI would be the best way to pursue and exploit more advanced autonomous systems and operations. This fundamental premise became the basis for the third offset strategy.^([18](#10_Chapter02.xhtml#rfn2_18))

## **AI, AUTONOMY, AND THE THIRD OFFSET STRATEGY**

As the 3OS defined it, autonomy resulted from freedom to develop and select a course of action required to achieve a higher authority objective. This applied to both human operators and intelligent machine systems. Importantly, the delegation of authority to intelligent machine systems would be confined to *specific tasks* assigned by a human commander or operator—e.g., sort through hours of full motion video and highlight important findings to analysts, select and kill a specific tank operating as part of a group of tanks earmarked for attack, and so forth.

The 3OS posited the joint force might potentially extend its militarytechnical advantage in the near to mid-term by inserting a variety of human-supervised *narrow-task systems* with improved and expanded AI-enabled autonomous functionalities into each battle network grid. These narrow-task autonomous systems would restrict their courses of action and decisions to solve a particular problem or domain—meaning the system could be programmed or trained to operate within the bounds of a defined problem and knowledge base. In practice, narrow-task autonomous systems would “have a degree of self-government and self-directed behavior with \[a\] human’s proxy for decision.”^([19](#10_Chapter02.xhtml#rfn2_19))

These human-supervised narrow-task autonomous systems might manifest themselves through autonomy at rest—that is, virtually, in software, in things such as intelligence support, planning, expert advisory, and predictive maintenance systems. Because the 3OS assumed all these types of systems would be designed to help humans make better decisions, it described autonomy at rest in terms of human-machine collaboration.

Human-supervised narrow-task autonomous systems might also manifest themselves through autonomy in motion—reflected in the physical world in the form of robotics and autonomous unmanned vehicles, systems, and weapons. Since the 3OS conceived of these systems as working hand in hand with humans to solve complex battlefield problems, it referred to autonomy in motion in terms of human-machine combat teaming.

The terms *human*\-machine collaboration and *human*\-machine combat teaming were intentional. The 3OS always envisioned these narrow-task autonomous systems as improving human battlefield performance. That said, the strategy fully expected that in some cases they might also perform independent battlefield tasks—especially if the tasks were dull or particularly dangerous, or involved operations in contaminated environments. In these cases, the 3OS envisioned the expanded use of machine-machine combat teaming, often in the form of combat swarms.

The framers of the 3OS deliberately emphasized human-supervised narrow-task autonomous systems, as opposed to more independent general task autonomous systems capable of performing more complex missions. Such systems would require AI that more closely mimicked human intelligence and reasoning.^([20](#10_Chapter02.xhtml#rfn2_20)) Once given commander’s intent and a mission—e.g., secure a village, clear an area of hostile forces—more advanced general or mission task systems would have the freedom to create, select, and change their own goals without further human intervention. The consensus was that the advanced AI necessary to empower more independent general task systems, even if possible, would not appear for some time, perhaps decades. In contrast, human-supervised narrow-task autonomous systems were well within the realm of current technological capabilities, and their performance was rapidly improving.

More importantly, however, it was hard to imagine a U. S. commander or any commander trained in the Western democracies as assigning a machine a more general combat mission, since the commander—not the machine itself—would be held accountable for the machine’s action under humanitarian international law and DoD’s own law of war manual.^([21](#10_Chapter02.xhtml#rfn2_21)) What commander would risk being designated a war criminal based on decisions made independently by a machine? It was far easier to imagine a mission being accomplished by human operators with the help of narrow-task autonomous systems operating under their direction and supervision.

## **ALGORITHMIC WARFARE AND HUMAN-MACHINE COLLABORATIVE BATTLE NETWORKS**

Universal digitization and widespread insertion of autonomous systems at rest and in motion into battle network grids are expected to lead to new forms of human-machine collaboration and human-machine and machine-machine combat teaming. These, in turn, could lead to new operational concepts and organizational constructs. The framers of the 3OS expected their emergence would signal the development of a new type of “algorithmic warfare”—the next logical evolutionary step in battle network development. However, they also posited that the “evolutionary” emergence of algorithmic warfare might lead to “revolutionary” battlefield results if it allowed joint force guided munitions battle networks to operate at a higher operational tempo than any adversary network.

Higher operational tempo would come from the deliberate and widespread insertion of human-supervised narrow-task autonomous systems into all four grids of joint multidomain guided munitions battle networks.

For example, sensors that are equipped with field programmable gate arrays and are capable of onboard machine learning could discern objects on their own without having to download the raw data to a processing center. Analytical tools powered by machine learning could assist intelligence analysts to discover patterns in complex multidomain scenarios characterized by enormous amounts of heterogeneous data. Decision aid tools could help develop courses of action for a commander’s review and consideration. Autonomous cognitive cyber and electronic warfare tools could help win the battle for electromagnetic spectrum superiority. Network-enabled autonomous weapons could coordinate their attacks with other weapons or manned platforms or provide information on enemy defenses to trailing salvos, which could then modify their attack plans (i.e., course of action).

At some point, the 3OS proponents hypothesized that this aggressive pursuit of narrow-task AI-enabled autonomous systems in all battle network grids would lead to the emergence of a new type of human-machine collaborative battle network. These new networks would be the physical manifestation of algorithmic warfare, capable of

•  more rapid sense-making of high heterogeneity and volume of data

•  more rapid understanding of the operational environment

•  more rapid development of a common joint multidomain operational picture, shared more quickly throughout the force

•  more rapid development of relevant courses of action and plans

•  more rapid force-wide understanding and appreciation of commander’s intent

•  more rapid and relevant decisions, promulgated faster to manned, unmanned, and human-machine combat teams and combat organizations.

In addition to enabling a much higher and more sustained operational tempo, widespread autonomous systems and operations would likely allow the joint force to operate more effectively during periods of denied or intermittent communications and conduct operations requiring high degrees of complexity and coordinated action, especially during multidomain operations. They were also expected to reduce the number of blue-on-blue and blue-on-green engagements and reduce collateral damage to both noncombatants and civilian infrastructure.

Importantly, the framers of the 3OS did not expect the decisions made by narrow-task autonomous systems to always be perfect. Indeed, given the state of contemporary AI capabilities, it is understood that these systems would make mistakes in combat just as humans do. Indeed, the 3OS working definition for machine intelligence was “the programmed ability of a machine to make faster decisions as well as, or better than, humans.” As long as machines could make faster, more relevant decisions that were no worse than one might expect from decisions made by humans, improved operational tempo and combat performance exceeding that from legacy networks should result.

## **THE OFFSET AFTER NEXT: ROBOTIC WARFARE**

In essence, algorithmic warfare could “power up” legacy guided munitions battle networks—allowing them to achieve and sustain a higher operational tempo, operate effectively during periods of network and communications outages, preserve forces by substituting machines for humans for especially dangerous tasks, and reduce collateral damage. The 3OS concept posits that the first competitor who successfully demonstrates algorithmic warfare and operates its associated human-machine collaborative battle networks may gain a decisive edge in a major conventional military confrontation.

That said, because artificial intelligence was a dual-use commercial technology, it was well understood by 3OS innovators that all competitors could—and most likely would—pursue variations of algorithmic warfare and human-machine collaborative battle networks, especially if their expected benefits were further demonstrated in battle. The Chinese People’s Liberation Army, in particular, sees artificial intelligence as providing the means to potentially surpass the U. S. military in operational effectiveness.^([22](#10_Chapter02.xhtml#rfn2_22)) Therefore, even if the joint force was the “first mover” in algorithmic warfare, it might not enjoy the longer-lasting competitive advantages that came with the first and second offset strategies. Accordingly, the 3OS had a more dynamic temporal dimension than the earlier offset strategies, during which the department would always need to be thinking about, and actively pursuing, the “offset after next.”

Up until now, thinking about the offset after next has never amounted to much more than institutional brainstorming and assigning organizations specific time horizons to pursue new ways and means for competitive advantage. For example, the strategic capabilities office had (and still has) the responsibility for pursuing competitive advantage inside the first future years defense plan (FYDP). This generally came in the form of modifying existing systems for new missions, such as modifying the Navy’s SM-6 surface-to-air missile to perform antiship strikes. Meanwhile, the cost analysis and program evaluation directorate and rapid capability offices of the armed services concentrated on accelerating the fielding of new capabilities in the second and third FYDPs. Lastly, the Defense Advanced Research Projects Agency focused its attention on developing entirely new capabilities in the fourth FYDP and beyond.

By establishing responsibilities for constantly and deliberately thinking about maintaining an advantage in an intense temporal competition, the 3OS sought to help the joint force forge, maintain, and perhaps extend its militarytechnical superiority over time.

Without question, however, the primary emphasis of the 3OS was on jump-starting the department’s efforts in the near term by devoting more spending on research and development (R&D) of artificial intelligence and its associated technologies (particularly machine learning). Near-term efforts included testing, demonstration, and fielding of numerous human-supervised narrow-task systems and applications, such as Project Maven, a computer vision application that analyzes full motion video feeds.^([23](#10_Chapter02.xhtml#rfn2_23)) These efforts incorporate experimentation with more advanced autonomous systems, such as the Navy’s *Sea Hunter* unmanned surface vessel.^([24](#10_Chapter02.xhtml#rfn2_24)) They also encompass the development of new concepts of operations and organizational constructs that exploit and employ them. It was expected that a top-down departmental emphasis on algorithmic warfare combined with bottom-up service wargaming and experimentation would lead to innovation at scale throughout DoD.

The expectation was that algorithmic warfare and its associated human-machine collaborative battle networks would inevitably lead to increasingly greater reliance on unmanned systems over time, for three reasons. First, the joint force is steadily pricing itself out of a human-centric force. Personnel costs for the all-volunteer force consistently rise faster than the rate of inflation, making personnel costs the most expensive component of defense spending. The average cost for an active-duty servicemember is now well over $100,000, and it continues to grow year after year. Second, as all great power competitors achieve rough parity in guided munitions battle network warfare, the lethality of future conventional combat will be staggering. Third, improvements in artificial intelligence and autonomous control systems will make unmanned systems increasingly capable of taking on more complex (and dangerous) battlefield tasks. For all these reasons, the 3OS expected future combat operations would gradually rely far more heavily on human-machine and machinemachine combat teams.

At some undefined point, the steady increase in the ratio of human-machine and machine-machine systems and combat teams to manned systems and combat teams was likely to reach another tipping point and result in new forms of robotic warfare much different from “the existing means of war.” Indeed, the expectation was that robotic warfare would likely usher in a new military-technical revolution. If true, the United States must strive to be a “first mover” in this new military regime, and the 3OS—with its pursuit of algorithmic warfare and human-machine collaborative battle networks—is the first step in its direction.

## **THIRD OFFSET STRATEGY: QUO VADIS?**

National security commentators have asked, “What happened to the third offset strategy?” The answer: it is embedded in the 2018 National Defense Strategy, along with many of the other lines of effort of the Defense Innovation Initiative, announced in November 2014 by then–secretary of defense Chuck Hagel. The 3OS focus on great power competition, its intent to arrest the erosion of the joint force’s military-technical superiority, and the determination to pursue the potential revolutionary impact of artificial intelligence and the autonomous systems and operations it enables are *all* prominent parts of the 2018 National Defense Strategy.

Other commentators claim the third offset strategy was just another quest for a technological silver bullet. Yet the historical record is quite clear that the strategy was never focused on technology per se. Instead, it sought to create technologically enabled operational concepts and organizational constructs that would provide the joint force with a competitive military advantage against great power competitors who enjoyed rough parity in guided munitions battle network warfare. AI is simply the means to that end.

A more trenchant critique might be that the department may not have fully embraced the idea that a broad push toward AI-enabled autonomous systems and operations is the best way to pursue military-technology superiority over its great power competitors. Although DoD established a joint AI center, it has little authority to direct overall departmental AI efforts. Moreover, the amount of R&D funds devoted to the advancement of AI and AI-enabled applications is but a small percentage of the department’s overall R&D budget. Any objective review of the department’s R&D priorities would conclude that DoD views hypersonic weapons and hypersonic weapons defense as far more important to the future of the joint force than advanced autonomous systems.^([25](#10_Chapter02.xhtml#rfn2_25))

Even if the top-down push for autonomous systems envisioned in the 3OS has not materialized, there is still abundant evidence the military departments are pursuing autonomous programs and other 3OS priorities with more urgency. The U.S. Army’s program includes a robotic combat vehicle, an optionally manned infantry fighting vehicle, network-enabled glasses for infantrymen and combat vehicle crew members, artificial and virtual training aids, and a variety of other 3OS-compatible equipment. The U.S. Navy’s program includes unmanned underwater vehicles, unmanned surface vehicles, an unmanned aerial tanker for its carrier air wings, and a variety of network-enabled autonomous weapons. The Air Force is pursuing collaborative attack weapons, swarming technologies, trusted unmanned wingmen, and a family of unmanned aerial vehicles. The Marine Corps is depending on a variety of unmanned systems and autonomous weapons to make its expeditionary advanced base operations concept possible. Likewise, all of the services are aggressively exploring machine learning systems to help them do everything from predictive maintenance to sub hunting to training programs. The hoped-for bottom-up aspect of the 3OS appears to be doing just fine.

It is important to reemphasize, however, that AI is a dual-use technology readily available to all of the great powers, and both China and Russia are determined not to lag behind in the race to field AI-enabled combat applications (chapter 5 in this book summarizes some of the efforts of potential opponents). The 3OS approach to this competitive dynamic was to organize the department for a temporal competition in which the R&D program was continually looking for the “offset after next.” The 2018 National Defense Strategy refers to this as “delivering performance at the speed of relevance.”^([26](#10_Chapter02.xhtml#rfn2_26)) The winner of the race for advanced autonomous systems will be the one that can do just that—consistently better than its competitors.

Fight’s on!

### **NOTES**

# 3

The Department of the Navy’s Commitment to Big Data, AI, and Machine Learning

WILLIAM BRAY AND DALE L. MOORE

**The Department of the Navy’s (DoN’s)** strategic guidance and planned budget acknowledge the disruptive impact that big data, artificial intelligence (AI), and machine learning (ML) will have on warfighting. Properly applied, these emerging technologies will inform the entire life cycle of research, development, acquisition, operations, and sustainment to provide more affordable, ready, and cost-effective capabilities that help to outpace global threats.

Today, the DoN is focused on the research, development, and delivery of big data, AI, and machine learning solutions that can sustain competitive advantage. While these technologies represent significant opportunities for the DoN to leverage, they also raise important questions about the future of maritime conflict, the new capabilities that will be required to succeed, and how these enabling capabilities are to be developed, delivered, and supported at the scale and pace needed to ensure a dominant naval force.

The DoN operates in a global strategic environment that is volatile, uncertain, complex, and ambiguous and that, over time, will require ever-increasing levels of operational agility. Concurrently, advanced technologies are being developed, democratized, and deployed around the world at accelerating rates, driving the need for rapid technological adoption and innovation to sustain a competitive edge. As a result, the world is becoming far less predictable and more susceptible to unanticipated disruption and strategic surprise. Now and in the future, the DoN must remain forward deployed, distributed, and ready to respond to any potential contingency at a moment’s notice to protect our national security.

It is against this backdrop that the DoN provides its strategic response to this new reality as described in *A Design for Maintaining Maritime Superiority, Version 2.0* (referred to here as *Design 2.0*). This response includes the need to “adapt to this reality and respond with urgency,” to “focus Navy efforts for fielding AI/ML algorithms on areas that most enhance warfighting, training and corporate decisions,” and to pursue an end state where the Navy can “learn and adapt faster than our rivals.”^([1](#11_Chapter03.xhtml#rfn3_1))

To meet these challenges, data is recognized as the basis for formulating actionable knowledge that enables well-grounded decisions, plans, and strategies. The expanded use of digitization, sensing technologies, and communication networks in both the military and commercial markets is providing new insights and foresights. New technologies such as advanced sensors, algorithms, cloud and mobile computing, and platforms have significantly improved data collection, organization, storage, and analysis. *Design 2.0* prioritizes the need to “establish data-driven decisions as the foundation for achieving readiness in our warfighting enterprises.”

Today, organizations are struggling to keep pace with their competition as new technologies, platforms, and business models enter the markets. Data science and analytics are fundamentally changing how business is conducted as competitive advantage becomes increasingly difficult to maintain. Taking cues from the commercial marketplace, the military will increasingly need to rely on leveraging data from all sources, including a vast array of commercial and military sensors. These sensors offer the potential to provide real-time situational awareness and predictive capabilities to help implement a comprehensive operational architecture in support of distributed maritime operations.^([2](#11_Chapter03.xhtml#rfn3_2))

To take full advantage of the value that large data sets can provide, machine learning technologies are being developed and applied across a range of context-specific applications. These large data sets must be organized and structured so that learning algorithms can use the data to train deep neural networks. Neural networks are comprised of nodes distributed across a requisite number of levels for the intended application. When fully trained and properly weighted, these nodes provide the working memory used for inference to provide responses to specific queries. Inference algorithms interpret the data from the environment or query by relating salient features to those placed in the trained neural network’s working memory.

These capabilities can offer significant advantages over conventional preprogrammed or physics-based computer technologies as they can more accurately interpret complex and interdependent real-world phenomena. As a result, inference algorithms provide a level of context-specific artificial intelligence that can perform complex pattern recognition at machine speeds equaling, and ultimately surpassing, that of human cognition.^([3](#11_Chapter03.xhtml#rfn3_3)) Artificial intelligence is a disruptive technology that will transform society as a whole but, most importantly, will transform the nature of conflict by augmenting and enhancing human situational awareness and decision-making in support of increasingly complex, dynamic, and highly distributed maritime operations.

Considering the full range of emerging next-generation technologies, it is anticipated that the most significant and pervasive impact will be felt through the fielding of artificial intelligence capabilities, which are built on a foundation of data analytics and machine learning. Artificial intelligence will fundamentally disrupt the nature of warfighting and will require a major paradigm shift in how we think about the development, deployment, and support of enabling capabilities, as well as how we consider the operations, tactics, and pace of warfare. AI-enabled technologies will expand the fleet’s and fleet marine force’s field of view, the speed of sensemaking and meaning-making, and the range of possibilities for the most effective strategies and decisions that help shape, deter, and defeat aggression.

## **AI-ENABLED DECISION-MAKING**

As AI technologies continue to develop and mature as well as become more pervasive across a range of applications, an unprecedented level of system agility will be required. System and system-of-system-level agility is rapidly becoming a required capability as information technologies enable operations at “machine speed”—that is, near–real-time communication with computer-based sensing, sensemaking, meaning-making, adaptation, and decision-making. Operating at machine speed refers to processing rates beyond those of human cognition and is considered essential for highly complex and dynamic data analysis, interpretation, and reasoning. By employing AI-enabled technologies, warfighters will be better informed and able to make decisions at the speeds necessary to win the fight.

To expand on the application of AI-enabled decision-making, a useful reference is John Boyd’s work on complex adaptive systems and the OODA (observe, orient, decide, act) loop model. Boyd recognized, developed, and articulated a decision and planning paradigm based on complexity science that can be adopted for use to provide competitive advantage. These concepts can be further exploited through the application of big data, artificial intelligence, and machine learning. In his work, Boyd highlights the need to use a wide variety of conceptual lenses to understand context under complex circumstances, move faster than the adversary to gain advantage, and change the nature of the conflict and the environment at speeds necessary to disrupt an opponent’s plans and strategies.

Boyd’s decision-making OODA loop framework is shown in [figure 3-1](#11_Chapter03.xhtml#fig2). The OODA loop provides important opportunities for the application of big data, artificial intelligence, and machine learning. It is a continuous and ongoing feedback-loop process that includes observing the environment to gather and filter salient data, orienting oneself in the context of the environment to support decision-making processes that ultimately enable action. Using the OODA loop as a decision-making framework, the application of big data analytics, artificial intelligence, and machine learning can provide a wider and more timely contextual lens to observe the environment, assess and interpret more complex patterns and trends during orientation, and provide statistically based recommendations to support human-/machine-based decision-making or, as appropriate, to the application of autonomous decision-making. Once decisions are made, they can be acted upon and continuously monitored to provide feedback for adjustments as new information is gathered and assessed.^([4](#11_Chapter03.xhtml#rfn3_4))

In the future battlespace, data will become more widely available and able to be collected at extraordinary rates and scale, crossing operational domains and boundaries for a more holistic and strategic perspective. Data will become increasingly complex and dynamic, requiring real-time analytics and visualization to provide an easily interpretable representation of synthesized information at the man-machine interface. Ultimately, big data analytics, artificial intelligence, and machine learning will offer the potential to make sense of operational chaos and ambiguity at speeds that are relevant to the conflict, which can influence decision-making across all levels and domains of warfare.

## **GLOBAL AI COMPETITIVE ASSESSMENT**

The Boston area–based Future of Life Institute has identified twenty-six national AI strategies and six international strategies that either have been released or are in the process of being released.^([5](#11_Chapter03.xhtml#rfn3_5)) The impact and implications of these strategies will have a profound effect on our national security as both growing threats by adversaries and enabling opportunities to leverage with both partners and allies. The speed at which organizations can develop, deliver, and proliferate these new and enabling capabilities will fundamentally determine who ultimately leads and who follows.^([6](#11_Chapter03.xhtml#rfn3_6))

![Figure 3-1. John Boyd’s OODA Loop](images/pg67_1.png)

**Figure 3-1**. John Boyd’s OODA Loop

In 2016 the Defense Science Board’s summer study on autonomy provided a “wake-up call” assessment of the rapid emergence of autonomous capabilities, fueled largely by the evolution of artificial intelligence, and concluded that autonomy—fueled by advances in artificial intelligence—has attained a “tipping point” in value. Autonomous capabilities are increasingly ubiquitous and are readily available to allies and adversaries alike. The study therefore concluded that the Department of Defense (DoD) must take immediate action to accelerate its exploitation of autonomy while also preparing to counter autonomy employed by adversaries.^([7](#11_Chapter03.xhtml#rfn3_7))

This call to action came with a comprehensive set of recommendations focused on accelerating DoD’s adoption of autonomous capabilities, strengthening the operational pull for autonomy, and expanding the envelope of technologies available for use on DoD missions. To accelerate the adoption of autonomous capabilities, the Defense Science Board made a broad range of recommendations addressing engineering and acquisition challenges, issues related to building trust and ensuring integrity, cyber resilience, test and evaluation, and technology insertion with implications for doctrine and new concepts of operations.

In 2017 the Harvard Kennedy School Belfer Center for Science and International Affairs conducted a study entitled “Artificial Intelligence and National Security” for the U.S. Intelligence Advanced Research Projects Activity (IARPA) that highlights the fact that private sector funding for AI far exceeds that of the U.S. government and that there are significant implications for U.S. national security. The report states that “future progress in AI has the potential to be a transformative national security technology, on par with nuclear weapons, aircraft, computers, and biotech.”^([8](#11_Chapter03.xhtml#rfn3_8)) From a military perspective, AI will provide advancements in new capabilities but also could make those capabilities more easily available to a broader range of actors, potentially giving weak states and terrorists significantly greater capabilities in areas such as autonomous systems, activity monitoring, and cyber.^([9](#11_Chapter03.xhtml#rfn3_9))

On July 20, 2017, the Chinese government released its national AI strategy, “A Next Generation Artificial Intelligence Development Plan,” designed to give China the global lead in AI by 2030.^([10](#11_Chapter03.xhtml#rfn3_10)) This comprehensive national plan provides China’s detailed approach to develop a broad range of artificial intelligence capabilities for both economic and military purposes. China is focused on seizing the strategic opportunity of AI, to build a first-mover advantage, and to accelerate its innovation capabilities to become a global power in science and technology that pushes Beijing to the forefront of military capabilities and economic dominance. The plan establishes ambitious national state goals for 2020, 2025, and 2030 and includes the full spectrum of research and development for next-generation AI capabilities, with the infrastructure and expert talent to drive transformation at all levels.^([11](#11_Chapter03.xhtml#rfn3_11))

In response to these global developments, less than two months later, Vladimir Putin publicly announced Russia’s clear intent to pursue AI technologies, stating, “\[W\]hoever becomes the leader in this field will rule the world.”^([12](#11_Chapter03.xhtml#rfn3_12)) Since that time, the Russian ministry of defense, in coordination with the ministry of education and science of the Russian federation and the Russian academy of sciences, held a conference to access global AI developments and to develop plans to focus Russia’s investments and initiatives. As a result, ministry officials released a ten-point plan that leverages public-private partnerships and focuses key research and development activities. On January 15, 2019, Putin approved an instruction for the government of the Russian Federation and other interested organizations to develop and submit proposals for a national strategy for the development of artificial intelligence.^([13](#11_Chapter03.xhtml#rfn3_13))

In January 2019 this high-stakes global competition was well characterized by then–director of national intelligence, the Honorable Daniel R. Coats, when he testified that “the global race to develop artificial intelligence (AI)—systems that imitate aspects of human cognition—is likely to accelerate the development of highly capable, application-specific AI systems with national security implications.” He further explained that “AI-enhanced systems are likely to be trusted with increasing levels of autonomy and decision-making, presenting the world with a host of economic, military, ethical, and privacy challenges,” and that “interactions between multiple advanced AI systems could lead to unexpected outcomes that increase the risk of economic miscalculation or battlefield surprise.” This comes as the threats to U.S. national security continue to expand across multiple dimensions.^([14](#11_Chapter03.xhtml#rfn3_14))

Concurrently, in January 2019 the Congressional Research Service report “AI and National Security” identified AI as a rapidly growing field of technology that is capturing the attention of commercial investors, defense intellectuals, policymakers, and international competitors alike, as evidenced by a number of recent initiatives. The report notes that China is seeking to develop a core AI industry worth more than $21 billion by 2020 and will “firmly seize the strategic initiative” and reach “world leading levels” of AI investment by 2030. Their report notes that in 2016, U.S. technology companies invested an estimated $20 billion–$30 billion with expectations on the order of $126 billion by 2025, whereas DoD’s unclassified expenditures were expected in 2017 to be more than $800 million.^([15](#11_Chapter03.xhtml#rfn3_15))

The global AI race has broad and significant implications for economics, communications, security, health care, the environment, and overall research and development. In its “Technology Trends 2019 Report on AI,” the World Intellectual Property Organization assessed the magnitude and direction of this competition. “Since artificial intelligence emerged in the 1950s, innovators and researchers have filed applications for nearly 340,000 AI-related inventions and published more than 1.6 million scientific publications. Notably, AI-related patenting is growing rapidly: over half of the identified inventions have been published since 2013.”^([16](#11_Chapter03.xhtml#rfn3_16))

## **U.S. NATIONAL ARTIFICIAL INTELLIGENCE GUIDANCE, STRATEGIES, AND PLANS**

In anticipation of the significant implications that artificial intelligence would have on national security and economic competitiveness, the National Science and Technology Council (NSTC) published “The National Artificial Intelligence Research and Development Plan” in October 2016 to define a highlevel framework to help identify AI-related scientific and technological needs. This plan provided seven strategies to address investments in human-machine collaboration; ethical, legal, and societal implications; safety and security; public datasets; training and testing environments; standards and benchmarks; and the needs of the research and development workforce.^([17](#11_Chapter03.xhtml#rfn3_17))

Concurrently, the NSTC published a report entitled “Preparing for the Future of Artificial Intelligence” to foster interagency coordination, provide technical and policy advice, and monitor the development of artificial intelligence technologies across industry, the research community, and the federal government. In December 2016 the executive office of the president issued a report entitled “Artificial Intelligence, Automation, and the Economy” to further investigate the effects of AI-driven automation on the U.S. job market and economy, as well as provide recommended policy responses.^([18](#11_Chapter03.xhtml#rfn3_18))

The National Security Strategy (NSS) released in December 2017 mandated the lead in research, technology, invention, and innovation. It provides guidance to build on the ingenuity that has launched industries, created jobs, and improved the quality of life at home and abroad. The NSS stipulates that to maintain our competitive advantage, the United States must prioritize emerging technologies critical to economic growth and security, including data science, advanced computing technologies, and artificial intelligence. The NSS notes that the field of artificial intelligence in particular is progressing rapidly and that the risks to U. S. national security will grow as competitors integrate information from both personal and commercial sources with intelligence collection and data analytic capabilities based on AI and machine learning.^([19](#11_Chapter03.xhtml#rfn3_19))

Executive Order 13859, signed on February 11, 2019, established the “American Artificial Intelligence Initiative” to maintain U.S. leadership in artificial intelligence. This executive order was guided by five principles as related to artificial intelligence, including driving breakthrough innovation, developing appropriate technical standards and reducing barriers to safe testing and deployment, training current and future generations of workers, fostering public trust and confidence, and promoting an international environment that supports U.S. AI research and innovation.^([20](#11_Chapter03.xhtml#rfn3_20))

In June 2019 the NSTC released “The National Artificial Intelligence Research and Development Strategic Plan: 2019 Update,” which reaffirmed the importance of the 2016 plan and its eight strategies while adding a ninth strategy focused on increasing the importance of effective partnerships between the federal government and academia, industry, other nonfederal entities, and international allies to generate technological breakthroughs and rapidly transition those breakthroughs into capabilities.^([21](#11_Chapter03.xhtml#rfn3_21)) As a result of this guidance, the expectation has been set for the overall portfolio of artificial intelligence research and development investments and a coordinated approach to grow the economy, increase national security, and improve the quality of life.

## **DOD/DON ARTIFICIAL INTELLIGENCE STRATEGIES**

National Defense Strategy

The National Defense Strategy, released in January 2018, describes the security environment as being “affected by rapid technological advancements and the changing character of war.” The new technologies identified include advanced computing, big data analytics, artificial intelligence, autonomy, robotics, directed energy, hypersonics, and biotechnology. The strategy identified artificial intelligence as one of the key technologies that will “ensure \[the United States\] will be able to fight and win the wars of the future.” The U. S. military is already integrating AI systems into combat via a spearhead initiative called Project Maven, which uses AI algorithms to identify insurgent targets in Iraq and Syria.^([22](#11_Chapter03.xhtml#rfn3_22))

## DoD Artificial Intelligence Strategy

The DoD AI Strategy (2018) directs DoD to accelerate the adoption of AI for a strong, technologically advanced capability that “drives the urgency, scale and unity of effort needed to navigate this transformation” that is essential for protecting the security of our nation. The Joint AI Center, designated as the focal point for this strategy, was chartered to explore AI’s full potential, study its implications, and begin the process of learning to assess the impact on defense. In this context, “AI refers to the ability to perform tasks that normally require human intelligence—for example recognizing patterns, learning from experience, drawing conclusions, making predictions, or taking action—whether digitally or as the smart software behind autonomous physical systems.”^([23](#11_Chapter03.xhtml#rfn3_23)) The strategy provides a multipronged approach, including delivering AI-enabled capabilities to address key missions, scaling AI’s impact across DoD through a common foundation that enables decentralized development and experimentation, cultivating a leading AI workforce, engaging with commercial, academic, and international allies and partners, and leading in military ethics and AI safety.

## Chief of Naval Operations Design for Maritime Superiority

In December 2018 the Chief of Naval Operations released *A Design for Maintaining Maritime Superiority, Version 2.0*, which acknowledged the challenges to our competitive advantage, the nature and scope of twenty-first-century global maritime competition, and the accelerating advances in technology that are resulting in disruptive rates of change. To meet this challenge, the design calls for the Navy to become more agile, compete in ways that are sustainable, and be able to fight as part of a joint force that can control the high end of maritime conflict. This is to be accomplished through partnerships with industry, academia, and research institutions and specifically requires fasttrack initiatives to accelerate the application of AI/ML in support of distributed maritime operations.^([24](#11_Chapter03.xhtml#rfn3_24))

## **ARTIFICIAL INTELLIGENCE TECHNOLOGICAL LEADERSHIP**

Defense Advanced Research Projects Agency AI Technology Development

Beginning in the 1990s, the Defense Advanced Research Projects Agency (DARPA) engaged artificial intelligence and machine learning technologies to analyze patterns of data from large data sets, natural language processing, and technologies supporting self-driving cars and other applications. The challenges were the large amount of data required for the ability to adapt to new situations, as well as being able to explain the results. To address these issues, DARPA is pursuing a multiyear program of more than $2 billion called the “AI Next” campaign to enable AI to partner with humans to solve difficult problems.

DARPA’s broader AI investments are targeted at sustaining the U.S. competitive advantage. These investments are essential to taking AI to the next level for disruptive capabilities, including advancing contextual reasoning and collaboration capabilities, and focusing on a number of critical national security fronts, including electromagnetic and cyber applications. DARPA is also developing the next generation of algorithms and technologies focused on explainability—a key characteristic that, once the key technologies and methodologies are matured, will greatly expand the domains of AI application across a broad range of critical national security and military applications. As a complementary set of investments, DARPA is also executing its artificial intelligence exploration program to further accelerate AI research, development, and deployment for meaningful applications and practice.^([25](#11_Chapter03.xhtml#rfn3_25))

## IARPA AI Technologies

The Intelligence Advanced Research Projects Activity supports the Office of the Director of National Intelligence. IARPA focuses on high-risk, high-payoff research and technology programs in support of the intelligence community. IARPA funds a range of research and conducts public challenges to tap into and develop cutting-edge technology, including artificial intelligence and machine learning.

Recent ongoing research in AI/ML includes augmenting and developing human cognitive performance, detection and prediction of anomalous activities, geopolitical and event forecasting, audio and text extraction and translation, big data analytics and data fusion technologies, three-dimensional rendering from video streams and multispectral sensing, and improving security and spoof-proofing AI/ML systems. IARPA is working to accelerate AI/ML training and refinement as well as engaging in several efforts aimed at understanding the impact and implications of new technologies and their emergence across multiple disciplines.

AI/ML technologies are being applied to assist in sense-making of complex situations in order to identify patterns of behaviors and activities including behavioral, biological, construction, and item of interest movements. IARPA is also focusing on enhancing computational capabilities by reverse-engineering the brain and its unique ability for pattern recognition such that continuously streaming data in complex and uncertain environments can be adaptively processed to make sense and give meaning to events, activities, and movements.^([26](#11_Chapter03.xhtml#rfn3_26))

## Naval Research and Development Framework

In July 2017 the Office of Naval Research released “A Framework for Accelerating to the Navy and Marine Corps after Next” to ensure that U.S. Navy and Marine Corps maritime superiority is sustained through technological superiority.^([27](#11_Chapter03.xhtml#rfn3_27)) The framework acknowledges the emerging power of big data analytics, artificial intelligence, and machine learning and is focused on both basic and applied research in artificial intelligence, cognitive science, autonomy, and human-centered computing designed to address the application of artificial intelligence technology and techniques to critical Navy and national problems. The technical emphasis is on the linkage between research, theory, and application, and conducting demonstration projects that use the full spectrum of artificial intelligence techniques including adaptive, intelligent, interactive, and perceptual systems.

## **DEPARTMENT OF THE NAVY FINANCIAL COMMITMENTS TO ENABLING CAPABILITIES**

The Department of the Navy fiscal year (FY) 2020 budget submission of $205.6 billion is an overall increase of $9.5 billion (4.6 percent) from the FY19 enacted budget. The increased funding is intended to restore the DoN’s competitive advantage and will field a larger and more formidable force. The DoN FY20 budget targets the development of long-range hypersonic strike, unmanned aircraft and vessels, ship-based lasers, rapid prototyping, big data analytics, artificial intelligence, and cybersecurity, as well as command, control, communications, computers, and intelligence to address multiple dimensions of conflict.

The DoN is making large investments in unmanned systems to accelerate enabling technology maturation and help pave the way for more enabling capabilities, especially those offered via big data and analytics, artificial intelligence, and machine learning. These unmanned systems include unmanned surface vehicles/vessels (USVs), unmanned undersea vehicles (UUVs), unmanned aerial systems, and unmanned aerial vehicles. Developments include the acceleration of the USV portion of the future surface combatant strategy; UUVs; the MQ-25 Stingray; the MQ0-4C Triton to provide persistent maritime intelligence, surveillance, and reconnaissance; and the MQ-9 aircraft as a single-engine, turbo-prop that is remotely piloted and designed to operate over the horizon at medium to high altitude for long-endurance sorties.^([28](#11_Chapter03.xhtml#rfn3_28))

## **ACCELERATING SUPERIOR AI MARITIME CAPABILITIES**

Over the long term of DoN programs, the breadth and scope of AI/ML applications are difficult to predict. However, given the broad range of emergent applications and the accelerating rates of commercial and military development, the implications promise to be profound. As new architectures, methodologies, technologies, tools, and strategies are created for developing, deploying, and leveraging AI/ML, the emergence of new and destabilizing capabilities is inevitable. The synergy between advancing technologies such as cloud computing, globally ubiquitous Internet of Things sensing, 5G and eventually 6G wireless communications, generative and adversarial AI, and quantum machine learning will fundamentally change the boundaries and competitive nature of both the commercial and military domains.^([29](#11_Chapter03.xhtml#rfn3_29)) Today, we see the financial sector leveraging AI algorithms at machine speeds to gain an upper hand in trading vast sums of resources, where the difference between making gains or absorbing losses is determined by milliseconds. We see the commercial sectors moving aggressively toward autonomous systems to reduce costs and provide new capabilities that increase efficiency and improve effectiveness at scale. The pervasive application of AI/ML can be anticipated as the boundaries and limits of technologies are pushed to the next level and barriers to adoption are addressed.

We are seeing the development of intelligent capabilities that make sense of what otherwise would appear to humans as chaos, as deep and broad patterns in seemingly disparate and unrelated data are identified, explored, and exploited. As nearly everything in society is captured digitally, in either quantitative or qualitative form, the ability to analyze and predict behavior, identify new and emergent patterns, and make predictions will increasingly improve. As a result of mobile and cloud computing, a great many of these capabilities will be widely available and will usher in an era of transparency with both benefits and risks for society.

For the DoN, mastering the evolution, development, and adoption of AI/ML is imperative. AI/ML will have a dramatic impact across the entire life cycle, spanning from how research and development is conducted, to how systems and integrated capabilities are analyzed, tested, and evaluated, to how manufacturing and production is organized, distributed, and managed, to real-time supply chain management, to highly complex and synchronized fleet and fleet marine force operations that optimize the value of contributions from each asset in the system of systems, and to how forward-deployed and continental U. S. logistics and sustainment are orchestrated.

For the near term, AI/ML capabilities will be enabled by and deployed with robust man-machine interfaces that ensure human-controlled decision-making. Over time, as confidence grows and AI/ML algorithms become explainable and predictable, more autonomous operations will be possible.

AI/ML will eventually become ubiquitous across all domains of operations. Ultimately, as AI/ML capabilities mature and become increasingly capable and predictable, there will be little choice but to empower autonomous systems at the limits of moral, legal, and ethical constraints. Over time, maritime operations will be increasingly dependent on AI/ML capabilities and the vast stores of data that feed them. We are now entering the era of algorithmic warfare, where AI systems will vie directly with adversarial AI systems in a head-to-head competition for superiority. Complex multidomain operations with a multitude of unmanned systems will be highly coordinated and optimized at machine speeds. AI systems will continuously explore and virtually test new strategies and tactics in an attempt to outmaneuver adversary AI systems in real time in multidomain head-to-head conflict.

## **A COMMITMENT TO ARTIFICIAL INTELLIGENCE CAPABILITIES AT SPEED AND SCALE**

DoD and DoN clearly recognize the significant paradigm shifts that big data analytics, artificial intelligence, and machine learning provide to help meet our national security requirements and commitments to allies and partners. Today, we are only at the beginning of a large-scale transformation that will fundamentally alter the nature of warfighting in the future. In the short term, a key focus will be on harnessing the symbiosis at the man-machine interface and exploiting the synergy that is possible by leveraging the best attributes of both humans and machines. Under these conditions, the man will be in the loop as information is aggregated, synthesized, and presented for decision-making. In the medium term, systems will become less dependent on human engagement and interactions for AI-enabled autonomous capabilities for nonlethal and noncritical applications. As confidence, trust, and capabilities are demonstrated and proven competent and competitive for warfighting applications, autonomous capabilities will become increasingly empowered. In the longer term, as AI capabilities are better understood, more highly predictable, and capable, the levels of autonomy will increase commensurate with policies and appropriate rules of engagement. As global competitors exploit AI capabilities, it will become necessary to ensure that DoN capabilities remain superior in terms of speed and lethality while retaining the confidence in system and system-of-system levels of performance.

Fundamentally, these are the characteristics of complex adaptive and anticipatory systems that underlie much of John Boyd’s prescient work. The DoN must ensure that it sustains superior warfighting capabilities that can adeptly sense and respond to the dynamics of a rapidly changing and uncertain environment at scale, using diverse and complex networks that aggregate and synthesize data to provide insights and foresights at relevant speeds and operational acuity. It is in these critical warfighting applications where big data, artificial intelligence, and machine learning can provide a clear competitive advantage. This is especially true for the more complex and dynamic mission areas that require rapid OODA loop decision-making in the fog of war.

### **NOTES**

# 4

The Navy at a Crossroads

**The Uneven Adoption of Autonomous Systems in the Navy**

PAUL SCHARRE

**The U.S. Navy stands at a crossroads**. Naval warfare is changing, and the Navy can embrace artificial intelligence (AI), robotics, and autonomy, or risk falling behind competitors. The military robotics revolution is approaching its third decade, and the United States has largely squandered an early lead. In the mid-2000s, the U.S. Navy was a pioneer in uninhabited systems, breaking barrier after barrier with innovative experimental programs like the X-47B Unmanned Combat Air System Demonstrator (UCAS-D). The X-47 was the first uninhabited aircraft to autonomously land on an aircraft carrier and to demonstrate autonomous aerial refueling.^([1](#12_Chapter04.xhtml#rfn4_1)) The Navy’s UCAS-D promised to usher in a new era of autonomous uninhabited aircraft that could extend the carrier’s reach—and the Navy’s relevance—in high-threat environments. Yet that era has not materialized, not because it was not possible, but because the Navy did not seize the opportunities in front of it. To adapt to future challenges, the Navy will need to first overcome internal cultural obstacles to change.

## **AI AND AUTONOMOUS SYSTEMS: DEVELOPMENTAL RELATIONSHIP**

Riding the exponential curves of increasing data and computing power, machines are becoming increasingly intelligent and capable of autonomous operation. The military robotics revolution that began as a tactical benefit from using remotely controlled drones and ground robots has evolved into a global explosion of AI. Advances in machine learning are enabling AI systems that are capable of perception, pattern recognition, prediction, optimization, and other tasks in ways that vastly outstrip what was possible even five years ago.

Nations around the globe are moving to capitalize on the AI revolution, which will enable more autonomous robotic systems as well as intelligent machines used in a variety of other tasks. AI is a general-purpose enabling technology, much like electricity or computers, and has a wide variety of military uses. As discussed in the other chapters, AI for predictive maintenance could save costs and improve readiness. AI could reduce energy usage, optimize processes, improve logistics, and enable better data analysis and decision-making. AI will also enable more capable autonomous vehicles in support and combat functions. Competitor nations such as China are moving aggressively to adopt AI into their military, and the Navy will have to do the same to keep pace.^([2](#12_Chapter04.xhtml#rfn4_2)) However, the Navy’s experience with robotic systems over the past two decades points to some of the challenges ahead that the service will need to overcome to remain dominant in the future.

To complement the tailored discussions of the other chapters, this chapter will focus on the adoption of uninhabited systems in the recognition that such systems will be primary “users” of AI whose capabilities and usefulness will expand as AI advances. Some AI developers even insist that artificial intelligence will only reach its true promise through autonomy.^([3](#12_Chapter04.xhtml#rfn4_3))

## **UNEVENNESS IN ADOPTING AUTONOMY**

Adoption of robotics and autonomous systems has been uneven within the Navy, with a noted divergence between the submarine, surface warfare, and aviation communities. The submarine community has enthusiastically embraced uninhabited undersea vehicles (UUVs) for the better part of the past two decades, with the first “UUV Master Plan” published in 2000.^([4](#12_Chapter04.xhtml#rfn4_4)) (Subsequent plans eventually became classified.^([5](#12_Chapter04.xhtml#rfn4_5))) Even during budget restrictions, the Navy continued UUV development, building prototypes of increasing size over time, up to the new Orca extra-large UUVs in development. The Navy’s current plan includes $359 million in fiscal year 2020 for UUVs, with an intent to field 191 UUVs of various sizes between 2019 and 2024 (with the balance of quantities toward smaller UUVs). The submarine community has also been steadily innovating with new concepts for employing UUVs in a variety of missions, including mine clearing, reconnaissance, and other roles, and in 2017 the Navy stood up its first dedicated UUV unit, Unmanned Undersea Vehicle Squadron One.^([6](#12_Chapter04.xhtml#rfn4_6)) Fielding of uninhabited surface vessels (USVs) has moved slower, perhaps due to the more complex technical challenges in ensuring safe autonomous operation in congested maritime surface environments. The success of the Defense Advanced Research Projects Agency’s (DARPA’s) *Sea Hunter* robotic ship was a groundbreaking achievement in USV development, paving the way for future Navy USV investments.^([7](#12_Chapter04.xhtml#rfn4_7)) The 132-foot trimaran *Sea Hunter*, born of DARPA’s Anti-Submarine Warfare Continuous Trail Unmanned Vessel program, autonomously navigated from San Diego to Hawaii in early 2019, operating with no onboard crew except for brief boardings to check equipment.^([8](#12_Chapter04.xhtml#rfn4_8)) In its fiscal year 2020 budget request, the Navy made a major move to capitalize on USV technology, requesting $3.7 billion from 2020–24 to invest in medium USVs (MUSVs), on the scale of *Sea Hunter*, and development of new large USV (LUSV) prototypes.^([9](#12_Chapter04.xhtml#rfn4_9)) The Navy has said it intends to procure ten LUSV prototypes by 2024, envisioned as approximately two-thousand-ton ships two hundred to three hundred feet in length.

While both medium and large USVs would be modular with reconfigurable payloads, the smaller MUSVs would first take on intelligence, surveillance, and reconnaissance (ISR) and electronic warfare missions. The LUSVs, by contrast, would be armed with antiship and land attack missiles to augment the magazine capacity of existing surface combatants.^([10](#12_Chapter04.xhtml#rfn4_10)) The LUSVs may finally allow the Navy to affordably realize the vision of missile-packed “arsenal ships” and are a key component of achieving a 355-ship Navy with a high-low mix of traditional human-inhabited and uninhabited surface ships.^([11](#12_Chapter04.xhtml#rfn4_11)) Now that USV technology has matured to the point where autonomous ship navigation has been demonstrated, the Navy surface warfare community appears eager to embrace the full potential of this transformative capability.

Despite early technological achievements, the Navy aviation community has had a more mixed track record, with uninhabited aircraft operationalized for support functions such as ISR but not in settings where they might compete with traditional human-inhabited aircraft. The Navy has undertaken a major investment in high-altitude long-endurance uninhabited aircraft for ISR in the MQ-4C Triton (a maritime version of the RQ-4 Global Hawk), and will invest more than $17 billion over the lifetime of the program to purchase seventy aircraft.^([12](#12_Chapter04.xhtml#rfn4_12)) The Navy has already integrated Triton into operations, and in June 2019 one was shot down by an Iranian surface-to-air missile when flying over the Strait of Hormuz.^([13](#12_Chapter04.xhtml#rfn4_13)) The Navy’s integration of Triton into maritime surveillance in “manned-unmanned teaming” with the P-8 Poseidon stands in contrast to its walkback of once-ambitious plans for carrier-based uninhabited combat aircraft.^([14](#12_Chapter04.xhtml#rfn4_14))

In the late 2000s the Navy was making headway toward a bold robotic future. The 2006 Quadrennial Defense Review called for development of “an unmanned longer-range carrier-based aircraft capable of being air-refueled to provide greater standoff capability, to expand payload and launch options, and to increase naval reach and persistence.” To achieve this goal, the Navy Unmanned Combat Air System (N-UCAS) program aimed to build a stealthy long-range uninhabited combat aircraft that would allow the carrier air wing to project power into contested areas.^([15](#12_Chapter04.xhtml#rfn4_15)) An uninhabited penetrating surveillance and strike aircraft is not only value-added but is in fact essential for maintaining the carrier’s relevance in future high-threat environments.^([16](#12_Chapter04.xhtml#rfn4_16))

The Navy launched the UCAS-D program to mature the technology sufficiently so that Navy personnel would trust an uninhabited aircraft in a carrier environment, successfully conducting autonomous takeoff and landing on a carrier in 2013. Yet despite overcoming the main technological hurdles to carrier operations, the Navy slowly strangled the N-UCAS vision through a series of requirements reviews in 2011 and 2012, downscoping the original concept of a stealthy penetrating surveillance and strike aircraft to an ISR drone for permissive airspace.^([17](#12_Chapter04.xhtml#rfn4_17))

Eventually, the Navy’s plans for a future carrier-based uninhabited aircraft evolved into the MQ-25 Stingray, whose primary mission is refueling traditional human-inhabited aircraft with a secondary ISR mission. The Navy is aiming for an initial operational capability for the Stingray in 2024 and has said that any discussions about future carrier-based combat aircraft are on hold until the service has experience with the MQ-25 in carrier operations.^([18](#12_Chapter04.xhtml#rfn4_18)) Even if the Navy moves promptly in the late 2020s to restart plans for a stealthy combat drone to operate in contested areas, it will have lost two decades in self-imposed delays, setting back naval aviation a generation.

## **IMPEDIMENTS TO THE ADOPTION OF AUTONOMOUS PLATFORMS**

What accounts for the difference in the adoption of uninhabited and robotic vehicles among different elements of the Navy? The operational need for robotics and autonomous systems is compelling in all three maritime domains, where the Navy faces increased threats as adversary precision-strike systems hold Navy air, surface, and undersea assets at risk. In all domains, uninhabited vehicles will allow the Navy to operate with greater range and persistence, giving commanders greater situational awareness and allowing more rapid prosecution of fleeting targets. Yet while the submarine and surface community have capitalized on the opportunities presented by UUVs and USVs as the technology has matured, the Navy aviation community has moved in the opposite direction, actually adopting less ambitious goals over time.

The Navy’s current position that uninhabited combat aircraft should be put on hold until after it has experience with integrating the MQ-25 into carrier deck operations is actually a step backward from where the service was five years ago. The Navy had two prototype X-47 aircraft that were being used in carrier deck operations and could have been used to better understand how to integrate uninhabited aircraft into the carrier air wing. Instead, the Navy terminated the UCAS-D program, shelving the aircraft when they had thousands of available flying hours remaining.^([19](#12_Chapter04.xhtml#rfn4_19))

New programs can often compete for funding with existing priorities, but funding pressures alone do not adequately explain Navy aviation’s deliberate decision to scale back its carrier-based drone programs. Other Navy robotics programs, such as UUVs, USVs, or the MQ-4C Triton, also compete for funding against traditional human-inhabited vehicles. After all, the Navy could choose to spend less on UUVs, USVs, and MQ-4Cs and buy additional human-inhabited submarines, surface ships, or maritime patrol aircraft. In every instance, the Navy has invested in uninhabited vehicles because they are an affordable way to augment existing human-inhabited platforms. Robotic vehicles can have a number of advantages depending on their design, often operating with greater persistence, at longer range, or lower cost than human-inhabited vehicles. Robotic vehicles can also undertake more hazardous missions without risking human lives. Introducing robotic vehicles into a “manned-unmanned team” can greatly improve combat effectiveness across all military domains.

Stealthy aircraft are no different, and the Air Force has invested in stealthy ISR drones to augment its fleet. The same dynamics exist for carrier-based stealth combat aircraft, and in fact the operational need is even more compelling.

## **WASTING CARRIERS**

Aircraft carriers will be of ever-diminishing utility over time—a “wasting asset”—without a penetrating long-range stealthy drone that can persist at range to hunt mobile targets.^([20](#12_Chapter04.xhtml#rfn4_20)) Currently, programmed short-range human-inhabited F/A-18E/Fs and F-35Cs lack the necessary range, even with refueling, to project power into high-threat environments.^([21](#12_Chapter04.xhtml#rfn4_21))

Without a longer-range uninhabited aircraft, the carrier will be of little value in the early stages of a conflict against a high-end competitor such as China. China has systematically invested in long-range antiship ballistic missiles and aircraft-launched cruise missiles that will push U. S. carriers to operate from farther beyond the effective range of current carrier-based aircraft.^([22](#12_Chapter04.xhtml#rfn4_22)) Even in a zero-sum budget environment, it would be far more sensible for the Navy to cut one or more carriers to fund development of an uninhabited combat aircraft than continue building $13 billion carriers that will lack the necessary aircraft to adequately project power against sophisticated competitors. Yet there is one critical difference for carrier-based aircraft versus other robotic programs, which may explain why the Navy has not only passed up opportunities but also actively downgraded its plans to *less* capable aircraft.

Carrier deck space is limited, and so perhaps even more acutely than in other domains, there is a direct zero-sum tradeoff between traditional human-inhabited and uninhabited carrier-based aircraft. The Navy can add only a modest number of additional aircraft per air wing (roughly five to six airframes, depending on the aircraft’s “spot size”), beyond which adding more aircraft would necessitate removing some existing ones. This is not the case for land-based aircraft, undersea, or surface vessels, where space considerations are not as acute. While pilots would still command uninhabited carrier-based aircraft, they would do so remotely from stations onboard the carrier. Even if the resulting “manned-unmanned” team of aircraft made for a more effective carrier air wing, it would significantly change the way in which naval aviators conduct military operations. “Top Gun” would have been traded for a trailer. The cultural consequences of such a change cannot be easily dismissed and indeed can be seen in the Air Force, where drone pilots are treated as second-class pilots despite their much higher operational value over fighter pilots in the past two decades of war.^([23](#12_Chapter04.xhtml#rfn4_23))

## **CULTURAL RESISTANCE**

It is no surprise that naval aviators would resist a change that would so sharply cut at the core of their culture. History abounds with other examples.^([24](#12_Chapter04.xhtml#rfn4_24)) Major technological transitions that alter a service’s or branch’s core identity—from sail to steam, horse to tank, or the introduction of airplanes—have often been met with resistance. Some innovations don’t just change how servicemembers carry out their jobs, but strike at the very core of their identity: sailor, cavalryman, or pilot. The shift from standing on the decks of a ship to working in an engine room shoveling coal, or from riding a horse to sitting inside a tank’s cramped crew compartment, or from flying a fighter jet to sitting in a trailer—these are not merely changes in a job’s task but rather fundamental alterations to a job that is central to servicemembers’ identity. Indeed, what is striking is how often these identities remain even when the job fades from memory. Today’s “sailors” are engineers—they don’t climb the mast and work the rigging. Modern Army “cavalrymen” wear Stetsons and spurs, even though actual horses are several generations removed from the ranks of Army cavalry units.

Not surprisingly, there are other examples of this kind of cultural resistance to identity-relevant job displacement from robotic vehicles in the U.S. military. The Army medical community has stridently resisted using robotic vehicles to evacuate casualties, even if it would save lives.^([25](#12_Chapter04.xhtml#rfn4_25)) The Marine Corps, which lacks a dedicated combat medevac community like the Army, has said they would happily use robotic vehicles to evacuate their wounded if it would save lives. The Army and Marine Corps have access to the same technology and have the same operational need. The difference is that in the Army, there is a service community whose identity is tied up not only in accomplishing a mission—evacuating wounded soldiers—but also in conducting a mission in a very specific way, which is sending medical personnel into harm’s way to evacuate the wounded. Flying helicopters into firefights to evacuate wounded soldiers is not merely part of the job; it is the core of the identity and ethos of those in the Army medevac community. Using robots for casualty evacuation would change how they conduct their mission, threatening their identity, even if it improved mission effectiveness. The same is true for robotic aircraft. Even as they might improve a pilot’s ability to conduct the mission, allowing for greater range and persistence, they change how the pilot conducts the mission in a fundamental way. A drone pilot may be a pilot, but he or she is not the same kind of pilot as one who sits in an airplane and is not seen as deserving of the same status, at least in today’s U.S. military. This dynamic does not exist with UUVs and USVs, which augment but do not replace human-inhabited submarines and surface ships.

## **AI AND MILITARY REVOLUTIONS**

Those who resist such cultural changes rarely do so for transparently self-interested reasons; they are genuine in their attachment to the benefits of an older way of doing business. Psychological studies have shown that people are susceptible to cognitive biases that cause them to reject new information that threatens their identities.^([26](#12_Chapter04.xhtml#rfn4_26)) This is a major hurdle for capitalizing on the AI revolution. Robotics, autonomy, and artificial intelligence will be valuable in every aspect of military operations. Indeed, the benefits of uninhabited vehicles, which are numerous, only begin to scratch the surface of the benefits of more intelligent machines.

Over time, AI will become as widely used in military operations as computers or electricity. In some cases, AI and robotics will allow militaries to conduct the same tasks more effectively or efficiently. This is the case for airborne ISR today, where the principal advantage of drones is their longer endurance, allowing for more persistence over target areas. But the real transformative potential of AI, like any new technology, lies not in doing the same thing better but doing it differently. A longer spear had military advantages, but the shift to firearms was a revolution.

Military history is punctuated with these revolutions, as the introduction of new technologies enables new ways of warfighting that radically transform combat operations. In each instance, it is not merely the introduction of a new technology alone that generates a revolution in warfare, but rather the combination of technology with new doctrine, organization, and concepts for war-fighting.

To capitalize on these opportunities, therefore, adopting a new technology alone is not sufficient. If the new technology merely improves on existing ways of warfighting, such as using uninhabited aircraft to refuel human-inhabited fighters, then the advantages will be incremental. The addition of MQ-25 Stingray aircraft to the carrier air wing will improve the air wing’s effectiveness, modestly extending the operational range of existing F/A-18E/Fs and F-35Cs. These changes will be incremental and hardly sufficient to give the air wing the operational reach and persistence it needs to remain relevant against high-end competitors such as China.

Truly transformative warfighting advantages come from changing how militaries fight. When those changes disrupt military culture, however, the result can be resistance from elements of a service, including in ways that might undermine that service’s combat effectiveness. Throughout history, militaries that have failed to adapt to disruptive changes in war have paid a steep price, losing lives, battles, or even wars.

## **STAYING AHEAD OF THE AI REVOLUTION**

In his sweeping history of military revolutions, *War Made New*, Max Boot recounts the infamous defeat of the Spanish armada at the hands of the British navy in 1588. Ships of both fleets carried cannons, a relatively new addition to naval warfare, but the British had reoriented their ship design, organization, and tactics to maximize the use of cannons while the Spanish navy was still primarily focused on closing with and boarding enemy ships, fighting hand to hand. The British went a step beyond merely adding a new technology to their inventory—they used it to change how they fought, reorganizing their entire fleet around cannons. As a result, the British fleet outgunned the Spanish by a third, and in battle British gunners were more effective at employing their cannons. The result was a rout of the Spanish armada and the beginning of the end of the Spanish empire.^([27](#12_Chapter04.xhtml#rfn4_27))

War is the ultimate arbiter of combat effectiveness, and even if the United States does not seize hold of the potential of the AI revolution, other nations will. The underlying technology behind these trends is too diffuse, globalized, and commercialized to be restricted or controlled. More than ninety countries have aerial drones today, as do many nonstate groups, and robotic ground and maritime vehicles are proliferating as well. The Navy is wisely investing in counterdrone technology such as lasers and electronic warfare; it reportedly used jamming to down an Iranian drone in July 2019.^([28](#12_Chapter04.xhtml#rfn4_28))

To stay ahead in the AI revolution, the Navy will need to embrace the opportunities enabled by new technology, build prototypes, and experiment with new concepts for warfighting. The biggest benefits are precisely where technology enables dramatic changes in how militaries conduct operations. Being open to these opportunities requires a shift in cultural mindset about how military personnel self-identify, with a move away from task-specific identities toward ones that are more mission-focused. The job of a pilot should be to project power in the air domain, not to fly planes, just as the job of a sailor is crewing a ship, not working a sail.

We do not yet know, at the very beginning of the AI revolution, what the best way to harness AI technology for military advantage will be. Uncovering the best ways of using AI will require an iterative process of prototyping, experimentation, and wargaming. If it does this, the U. S. Navy could secure a future of sea power as dominant as its recent past. But first, the Navy must be open to change.

### **NOTES**

# 5

AI Programs of Potential Military Opponents

**Propositions and Recommendations**

SAM J. TANGREDI

Artificial intelligence is the future, not only for Russia, but for all humankind. It comes with colossal opportunities, but also threats that are difficult to predict. Whoever becomes the leader in this sphere will become the ruler of the world.

—Russian president Vladimir Putin, September 1, 2017^([1](#13_Chapter05.xhtml#rfn5_1))

Artificial intelligence technology can accurately perceive, forecast, \[and\] early warn \[of\] infrastructure and social security operation … it is indispensable for the effective maintenance of social stability.… \[Our goals are to\] Promote the formation of multi-element, multi-field, highly efficient AI integration of military and civilian pattern.… Promote AI technology in military-civilian two-way transformation. Strengthen a new generation of AI technology in command-and-decision, military deduction, defense equipment, strong support, and guide AI in the field of defense technology to civilian applications.

*—Notice of the* \[PRC\] *State Council Issuing the Next Generation of Artificial Intelligence Development Plan*, July 8, 2017^([2](#13_Chapter05.xhtml#rfn5_2))

**Whether expressed in** the inflated rhetoric of a Russian president perpetually defying the perceived perfidiousness of the West, or in the cautious but telling phrases of the State Council of the People’s Republic of China (PRC), it is obvious that the other “great powers” view the development of artificial intelligence as a race, and one from which competitive military applications will be harnessed.^([3](#13_Chapter05.xhtml#rfn5_3))

From the American perspective—and that of a number of her allies—this race is largely, though not exclusively, an aspect of military competition. After all, it is assumed on the commercial side that in a global market competition between technology companies, no matter their nationality, AI development will continue without the need for governmental interference and will eventually result in global benefits in which all nations share, albeit perhaps unevenly.

Meanwhile, on the military side, there is American and allied concern about the possibility of one or more potential opponents leaping ahead in the development of AI. The third offset strategy was conceived as a method of staying ahead of the military competition for new technologies, such as AI, but it was also motivated by the need for the United States to create a military advantage to replace the one it formerly held in the centerpiece of the second offset strategy—precision weapons. This objective is made clear in chapter 2; and, indeed, both Russia and China appear to have caught up with many U.S. military technologies that were cutting edge in the 1980s and 1990s.^([4](#13_Chapter05.xhtml#rfn5_4))

The history of military great power competition indicates that an AI competition—or arms race, if you will—is a natural development. However, an even greater concern than technology leapfrog may be that the military rivals of the United States, all authoritarian regimes of some stripe, may not be as committed to maintaining a “human-in-the-loop” approach to integrating AI into military affairs. This appears to be true in current Russian military AI developments.^([5](#13_Chapter05.xhtml#rfn5_5)) It stokes the fears of the eventual creation—as noted in the book’s introduction—of a “Terminator.”

## **PURPOSE AND PROPOSITIONS**

The purpose of this chapter is not to offer original research in Russian or Chinese language sources, but to provide original understandings through a survey of research already published in the West—what we think we know. Analyses (as opposed to opinions) on Russian and Chinese military applications of AI are not extensive, but their number is growing.^([6](#13_Chapter05.xhtml#rfn5_6)) In surveying this literature, I have concluded that the more prolific and reputable analysts include, for Russian programs, Sam Bendett, currently at the Center for Naval Analyses, and for Chinese programs, Elsa Kania, currently at Harvard and an adjunct fellow at the Center for a New American Security. I have utilized their work extensively in this chapter, though my findings, expressed in the form of propositions, may not accord with theirs. There is also an increasing number of other researchers examining Russian and Chinese sources, and, of course, many who write on military AI from a theoretical or North Atlantic Treaty Organization (NATO) member perspective. Interestingly, the most short and concise but eloquent statement on Russian and Chinese military AI is by a freelance writer based in Sarajevo, Adrian Pecotic.^([7](#13_Chapter05.xhtml#rfn5_7))

A quick note is in order about use of the term propositions instead of findings or conclusions. Although the propositions expressed in this chapter accord with the general consensus of the sources surveyed, it is difficult to achieve certainty on the operational decisions of closed or partly closed societies. To do so requires a level of intelligence-grade information not available to the open-source (unclassified material) analyst. Thus, rather than describe my assessments based on research literature and my own analyses as findings and/or conclusions—terms that imply a degree of certainty—they are expressed as propositions that I hope could be used to structure unclassified discussions on military AI *and* assist in the organization of further classified analysis.

All three of the major military powers, Russia, China, and the United States, recognize that big data, artificial intelligence (AI), and machine learning hold the prospect for application to military capabilities. Yet all three have a different approach to the development and, more importantly, the prioritized goals for the militarization of AI. The immediate objectives of all three differ as to government involvement in AI research, the risks they are willing to take in its development, the degree to which they will concede autonomy to AI systems, and the immediate applications that they seek. This is the first proposition—a near-consensus of the current research.

## **INCENTIVES FOR THE DEVELOPMENT OF MILITARY AI**

*Proposition 1*. Objectives for military AI development differ among the three military powers. Each has different incentives to adopt military AI.

## United States

In the Department of Defense (DoD), current efforts have focused on harnessing commercial AI to conduct repetitive analytical tasks, such as cataloging and matching images in near-real time from drone video footage—the function of the frequently mentioned Project Maven. Other applications are primarily tactical in nature; they are intended to supplement the access to information of the individual warfighter, as is discussed in other chapters. In any event, a primary debate in the United States and other democratic states that place a considerable value on human rights and avoidance of civilian casualties is whether human control can be retained over the autonomy of weapons systems that can utilize AI for making independent decisions. This is the man-in-the-loop debate.^([8](#13_Chapter05.xhtml#rfn5_8)) DoD officials have made multiple pledges to retain humans-in-the-loop in decisions involving the use of deadly force by autonomous or AI-driven systems.^([9](#13_Chapter05.xhtml#rfn5_9)) This is discussed in extensive detail in chapter 18. (Many U.S. autonomous military systems, such as maritime surveillance or naval mine-seeking systems, are not built with the capacity to use deadly force.) This ethical consideration tends to limit AI applications to augmenting human capabilities and decision-making, not superseding them—driving them toward the tactical level, as noted in chapter 17.

Thus, the primary U.S. objective is to achieve what is called human-machine teaming, largely on the tactical level but, in the plans of proponents, approaching the strategic. Based on the discussions in the other chapters of this book, the objective for military applications of AI in the United States can be captured as follows:

•  continue/promote military predominance/overmatch

•  enhance operational and tactical capabilities and global logistics

•  reduce manpower costs

•  spur military-commercial AI/promote research/tech economy

•  be transformational.

## People’s Republic of China

Under the control of the Chinese Communist Party (CCP), China can be considered a surveillance or counterintelligence state. That is, the primary mission of state security is to preserve control by the ruling party through ensuring a tight watch over the populace and preventing foreign influence from encouraging domestic support for a multiparty system. With approximately 170 million surveillance cameras operated by the state (roughly one per every ten persons), this security apparatus is formidable.^([10](#13_Chapter05.xhtml#rfn5_10)) One estimate predicts China will have 626 million state surveillance cameras by 2020.^([11](#13_Chapter05.xhtml#rfn5_11)) The actual number of cameras is inconsequential in comparison to the logic behind their installation and use and the potential they present for facial recognition and other AI applications. Naturally, tying together and increasing the speed of the surveillance of the system—the worst fear of civil libertarians in Western states—is an attractive prospect for the CCP. There are many indications that the priority use for AI in the PRC “civilian” sector is also the priority military application: ensuring top-down control of military decision-making.

From this perspective, the top priority for the CCP appears to be the ability to utilize AI to bypass the need for operational decision-making by the mid-level military ranks in order to ensure that the orders of the party’s central military committee and top military commanders are applied directly at the tactical levels, In other words, the party seeks to develop a machine-speed analysis and decision-making grid that can provide operational- and tactical-grade information and situational awareness so that the higher levels of command can issue tactical-level orders and transmit them nearly instantaneously. The AI would carry out the functions normally assigned to field grade and junior officers and senior enlisted personnel in a Western military organization. Facetiously, this could be called the “certain-men-in-the-loop” approach.

For the CCP, prioritizing military AI development for bypassing command levels is eminently logical. Having achieved political power from the barrel of guns, as Chairman Mao Zedong is often quoted, the party does not want anyone with alternate ideas in control of any of the guns. The need for psychological control by the CCP leadership is reflected in the ubiquity of the political officer/commissars, sometimes senior in rank to the field commanders they “support.”^([12](#13_Chapter05.xhtml#rfn5_12)) In addition, purges of the high-level military ranks are routine.

In this way, AI can ensure the “loyalty” of the military since there are few opportunities for the intervening levels to make a “disloyal” decision or direct actions not in tight concordance with the course senior leadership might prefer.

Additionally, such an AI-based intelligence, surveillance, and reconnaissance (ISR) and command and control system could solve a potential problem noted by many Western analysts of the PRC military—a lack of operational initiative within the middle ranks trained to function under a burdensome hierarchic system.^([13](#13_Chapter05.xhtml#rfn5_13))

As a caveat, one must admit that the above argument is a proposition rather than a firm conclusion. There is simply not enough evidence—at the unclassified level—to demonstrate that that such is the definite priority of People’s Liberation Army (PLA) development of the military application of AI. However, it is in accord with so-called civilian application of AI within the PRC. Since the PLA is also ultimately responsible for the domestic control over Chinese society (those were not police tanks in Tiananmen Square), it is again logical that civilian and military AI priorities are in accord. This is a clearly stated goal of the PRC State Council as quoted at the beginning of this chapter.

Other incentives that motivate the PLA’s application of AI are in accord with the CCP’s overall strategic objectives: to offset U.S. joint military advantages in the global commons and facilitate eventual PLA overseas power projection capabilities; to spur military-commercial development of AI and potentially increase the PRC’s share of global arms sales; and to gradually increase the credibility of their combat-capable global operations (in contrast to mere presence or humanitarian assistance.) The combined objectives for the PRC are captured as:

•  ensure top-down control over strategic, operational decision-making (can bypass middle level leadership)

•  ensure loyalty of military personnel

•  offset U.S. advantages in global commons, overseas power projection

•  spur military-commercial AI, weapons sales

•  gradually expand credible global operations.

## Russia

The Russian military has set about a course of modernization—particularly in strategic and tactical nuclear weapons (along with strategic conventional alternatives).^([14](#13_Chapter05.xhtml#rfn5_14)) However, it still remains a shadow of the relative global military power of the former Soviet Union. A primary drag on increasing overall military power has been the decline in the military-age population due to both the break-up of the Soviet Union and a declining birthrate.^([15](#13_Chapter05.xhtml#rfn5_15)) This reality can be interpolated from the [table 5-1](#13_Chapter05.xhtml#tb1) below.

As noted in the introduction and other chapters, Russian leaders appear willing to build autonomous weapons systems without requiring a human-in-the-loop of decision-making, particularly in ground combat, where manpower disparities can have critical effects.^([16](#13_Chapter05.xhtml#rfn5_16)) Autonomy holds the promise of negating these disparities by substituting “thinking” machines for humans, and, as in the third offset, AI is perceived as the enabler of autonomy (hence the Putin quote cited earlier). If Russia is determined—as it is—to develop and maintain a globally capable military (or at least capable of limited out-of-area deployments, such as to Syria), the requirement for this substitution is logically the primary incentive for the military adoption of AI as a feature of autonomy and its priority application. To continue the context of the Putin quote, the Associated Press reported that “in his speech on Friday, Putin predicted that future wars would be fought by countries using drones. ‘When one party’s drones are destroyed by drones of another, it will have no other choice but to surrender.’”^([17](#13_Chapter05.xhtml#rfn5_17)) That is certainly a strong endorsement of autonomous weapons.

**Table 5-1. Comparative Populations and AI Implications (2017)**

![](images/pg98_1.png)

That is not to say that the Russian leadership would forsake AI as a decision aid tool for humans, only that such would be a secondary priority. Similar to those of the PRC, other incentives include to offset U.S. joint military advantages in the global commons, facilitate Russian overseas power projection capabilities, spur military-commercial development of AI, and potentially increase Russia’s share of global arms sales. Additionally, Russia sees the deterrent (and compelling) effects of its nuclear arsenal as a primary element of its status as a global power. Therefore, it is logical that it would seek AI applications that could buttress its strategic capabilities—a possibility of great concern to the international arms control community.^([18](#13_Chapter05.xhtml#rfn5_18))

Incentivized objectives for Russian adoption of military AI can be summarized as:

•  to offset comparative disadvantage in military-age population (replace the need for people with autonomous systems)

•  to offset U.S. advantages in global commons, power projection, and her alliance network

•  to spur military-commercial AI and weapons sales

•  to enhance deterrence capabilities, both conventional and nuclear.

## **AUTHORITARIAN GOVERNMENTS AND ARTIFICIAL INTELLIGENCE**

*Proposition 2*. Objectives for AI development are as dependent on the nature of the government as they are on a specific military situation.

Although the above proposition may seem self-evident to many defense analysts, it still bears stating, since the modern academic field of international relations has traditionally sought “solutions” to the problem of war by analyzing the nature of the international system rather than the nature of domestic regimes. The international system or environment is characterized as one of *anarchy* (without central authority), which prompts nations to focus on the need for security and sovereignty, with a sense of suspicion at the potential power and actions of others.^([19](#13_Chapter05.xhtml#rfn5_19)) Arguably, this overall intellectual focus on the structure of the international system has blinded some scholars—whose work influences defense analysts—to the fact that some regimes are constrained in their actions in both their domestic and international activities, while others are not. To assume all national governments act in similar ways in the international system is to reduce their very nature to irrelevance—pleasing to a moral relativist perhaps, but completely illogical.

It also misses the unfortunate reality that the very features of artificial intelligence—particularly the ability to centralize and increase the speed and ubiquity of surveillance—facilitates the internal control of authoritarian states. This is a fact that, despite the peaceful and egalitarian visions of many AI scientists, is beyond dispute. For states that use their military to preserve domestic control over the populace, domestic and international activities are inevitably entwined, with the use of force in the international affairs often motivated by the need to retain domestic control.^([20](#13_Chapter05.xhtml#rfn5_20))

For example, even though the People’s Liberation Army appears to be “professionalizing” by stressing military skills as much as political and ideological reliability, it “still confronts unique circumstance\[s\] as a military”—as Elsa Kania describes it—“that is required to obey the commands of the Chinese Communist Party (CCP), since it is pledged to defend the Party, not the state.”^([21](#13_Chapter05.xhtml#rfn5_21)) Yet from a historical viewpoint, such is not a unique circumstance. One shudders at the thought of what a Nazi regime, the Soviet Union under the control of Stalin, or the Red Guard under Mao would have done if AI capabilities were within their grasp.

Granted, few today would equate Putin or Xi Jinping with Joseph Stalin or Adolf Hitler. Such an all-encompassing network of power appears beyond their individual span of control, forcing them to destroy their enemies by more subtle means—such as individual bioweapons attacks or spontaneous corruption investigations.^([22](#13_Chapter05.xhtml#rfn5_22)) However, the application of AI certainly appears to increase both the domestic powers of their states and their individual power in facilitating the intensity of surveillance and speed of decision-making. Given its advantage in facial recognition, AI does not seem likely to improve the lot of Uighurs in China or dissidents in Russia.^([23](#13_Chapter05.xhtml#rfn5_23))

It is natural for authoritarian powers to utilize the same measures in their international politics, although generally with a greater degree of caution lest their actions are too obvious. There is ample evidence that Chinese-owned Internet service providers surreptitiously route their global traffic through China, which facilitates collection and analysis, eventually with the use of AI to sort out items of interest.^([24](#13_Chapter05.xhtml#rfn5_24)) The international expansion of fifth-generation wireless networks by Huawei increases this capability, and again AI can facilitate this analysis.^([25](#13_Chapter05.xhtml#rfn5_25)) This is natural for a Leninist state.

The Russian government does not have the same degree of control over Russian society and nominally retains electoral governance. Power is concentrated in the presidency and with those who were referred to as oligarchs but are now the managers of the large state-owned commercial enterprises.^([26](#13_Chapter05.xhtml#rfn5_26)) However, the undisguised goal of rebuilding Russia as a great (including feared) global power is as advantageous for the state-run enterprises and former oligarchs as it is for Putin.

In contrast, the U.S. government—extolling the virtues of free enterprise—appears to muddle through such competitions based on the invisible hand of economic competition and the traditional inventiveness of unfettered scientists, engineers, and entrepreneurs. Under conditions of an equally distributed globalization in an international economy characterized by free trade, that might be a winning formula. However, the commitment of authoritarian and semi-authoritarian governments to free trade is always tenuous. This is a disadvantage to those who are truly committed to playing in accordance with free trade rules. Public recognition that “free trade” has had certain disadvantages for the domestic U.S. economy is cited as one of the factors propelling the election of Donald Trump. Thus far, the global flow of commercial AI development has not been generally perceived as disadvantageous to the United States. However, some argue that it is.

In any event, indicators and logic support the view that objectives for AI development are dependent on the contrasting natures of the three governments involved in the AI “race.” This is an area in which additional quantitative research is warranted.

## **COMMERCIAL DEVELOPMENT AND MILITARY AI**

*Proposition 3*. Each of the three AI military powers has a different level of control over commercial AI.

Development of AI applications is obviously research and development (R&D)–funding-intensive. Investors have to be willing to spend considerable capital to fund the highly educated, low-density/high-demand personnel necessary to conduct the R&D. In a free, capitalist economy—particularly one that has embraced a philosophy that commercial firms owe strict allegiance to increasing the wealth of their shareholders, not necessarily their work forces—there has to be a high potential for future profit.

If, as in the PRC, profit is inevitably controlled by the government, there is obviously greater governmental control over the direction of R&D than in a less controlled economy. Such control, through which the government can pick commercial “winners and losers,” is in effect a low-cost government subsidy for the winners. The PRC government does not need to spend money to “encourage” AI companies to direct their R&D efforts toward applications that have military as well as commercial potential.

In contrast, the U.S. government needs to spend financial resources in order to encourage commercial AI firms to research (and produce) potential military applications, either through research contracts, grants, or the potential of purchasing the resulting product.

The Russian government possesses some of the same tools of influence as the PRC, having recreated the dominance of state-owned enterprises in certain commercial sectors, such as in exploitation of natural resources. However, the influence of the commercial oligarchs and managers of state-owned enterprises over government decision-making is such that the government can “pick winners and losers” mostly indirectly. Thus, it has less control over the direction of AI R&D by Russian firms doing global business, requiring it to provide financial resources along with intimidation.

The importance of the degree of control over *commercial* AI relates to the previously identified fact that most AI R&D is funded by commercial firms, particularly in the United States. As former secretary of defense Ashton Carter remarked in addresses to Silicon Valley companies, although the DoD might have difficulty in translating commercial AI to military applications, it recognized that it was dependent on commercial investment in AI R&D.^([27](#13_Chapter05.xhtml#rfn5_27)) If, indeed, military AI is dependent on commercial R&D and remains so, directing commercial R&D toward military applications depends largely on government influence to encourage investment in an effort in which profits might be marginal. Obviously, there is a disparity in the amount of influence the government of the three major AI military powers can bring to bear.

In addition to levels of control, there are also differences in the total incentives for the three AI powers to promote commercial AI development overall, leading to a fourth proposition.

*Proposition 4*. Each of the three AI military powers has different incentives to promote commercial AI.

Along with different levels of control, each of the three AI powers has a somewhat differing incentive to promote commercial AI. These incentives are related to the nature of the government and are linked to the second proposition. All of the states are motivated by economic benefits, which require the generation of profits that the AI produces from a domestic and/or international market. However, prioritization of these incentives is different, with open economies mainly prioritizing profit and closed or semi-open economies giving their respective governments more options for choice.

## PRC

Based on the existing literature, the prioritized incentives for the CCP to support the development of commercial AI in the PRC are

•  ensuring CCP control over the population by means of ostensibly commercial AI developments such as speech and facial recognition and Internet preference monitoring

•  regulating a historically unregulated society through an Internet-based social credit system^([28](#13_Chapter05.xhtml#rfn5_28))

•  increasing global influence by participating in and/or dominating the global AI market

•  feeding commercial AI developments into the military-industrial complex

•  generating profits.

## Russia

Russian government prioritization for commercial AI support differs in that the function of generating profits is both an economic benefit and a means of retaining the support of oligarchs invested in software and computer businesses. A short priority listing is

•  assisting in control over social activities of the population, particularly the activities of dissidents and non-Russian minorities

•  generating profits to retain the political support of oligarchs and managers of state-controlled enterprises

•  feeding commercial AI developments into the military-industrial complex

•  general economic benefits

•  increasing global influence by participating in and/or dominating the global AI market.

## United States

The incentives for the U.S. government for supporting commercial AI development center on general economic benefits. However, there are other incentives, some of them paralleling those of the other two states. Based on my analysis, a prioritization would be

•  generating profits as a general economic benefit

•  promoting technology-related jobs in a post-manufacturing economy

•  promoting research and scientific advancement that could eventually feed into the military-industrial complex

•  increasing global influence by participating in and/or dominating the global AI market for some individual elected officials, generating campaign contributions from technology companies, investors, and Wall Street.

## **PRIORITIZING MILITARY APPLICATIONS AND COMPARATIVE ADVANTAGE**

*Proposition 5*. Each of the three AI military powers will prioritize different military AI applications.

The prioritizations of proposition 5 are the effective result of the previous propositions, reflecting the issues of political control over military decision-making and disparity in demographics, combined with the current strategic military postures of the three AI powers.

## PRC

Given the antiaccess posture of the PRC versus potential U.S. interference in the South China and other near seas, as well as plans for Taiwan, prioritization for eventual military applications can be summarized as the development of

•  machine-human teaming at the operational level

•  dual-use (military and civilian) ISR systems

•  battle management for area control

•  autonomous weapons (in multiple domains)

•  matching and neutralizing anything the United States is developing.^([29](#13_Chapter05.xhtml#rfn5_29))

## Russia

Russia’s prioritization reflects five strategic elements: an emphasis on nuclear weapons capabilities as the ultimate arbiter of military power, a shrinking population and loss of potential manpower, involvement in gray zone operations, an antiaccess posture against NATO/the United States (but with offensive operational aspects), and fewer financial resources available than the two other AI powers.

The Russian government’s prioritization can be summarized as

•  autonomous weapons, particularly both nuclear and conventional missile systems

•  autonomous land combat systems that can substitute for manpower

•  battle management for area control.^([30](#13_Chapter05.xhtml#rfn5_30))

## United States

A summary of U.S. DoD priorities can be developed from the many chapters of this book, with particular reference to chapters 2 and 3 to indicate recent and current priorities:

•  military ISR systems

•  human-machine teaming at the tactical level

•  autonomous systems under human oversight

•  (eventual) human-machine teaming on the operational level

•  logistics and design systems.

It is entirely possible that priorities of all three AI powers will shift depending on global politics and the speed at which particular AI applications are developed and perfected.

If one accepts the validity of the previous five propositions and performs a rough net assessment to outline the comparative advantages of the three AI powers in developing and fielding *military* AI applications, one detects a potential for an eventual leader in the AI “arms race.” This leads to the most controversial proposition, and one that is disturbing for U.S. strategists.

*Proposition 6*. In a globalized world, China is the eventual natural leader in developing commercial and military AI.

Having a population four times the size of the United States, with the size of internal market and intellectual capital that such implies, control over its economy and ability to pick commercial winners and losers, and unilateral ruthlessness in its internal politics and Leninist philosophy (CCP as the vanguard of development), the PRC would be the natural AI leader in a truly globalized world. The size of its internal market—once prosperity is more evenly distributed among Chinese consumers—would certainly drive continued commercial AI development, as well as continue to entice the involvement of Western tech companies thirsting for growth. Thus far, the realization that support for commercial AI development in China inevitably supports the repressive capabilities of the CCP seems to have dissuaded only a handful of Western corporations.^([31](#13_Chapter05.xhtml#rfn5_31))

Control over the economy allows the CCP to support AI development by shifting resources in ways that Western governments (and semi-authoritarian powers) cannot match. The seamlessness with which commercial and military AI development can be mutually supportive might have been rivaled by the United States in the 1960s or 1970s, when U.S. government investment in research and development was larger than that of commercial tech firms. This has not been the case since the 1980s, and even enticing commercial tech firms to work closely with the Pentagon faces the hurdles of funding and (purported) antiestablishment sentiment within the more vocal portion of the programmer/coder labor force. Russia may have greater power in forcing commercial-military AI cooperation, but despite significant software development firms, it is hard to compete against a population ten times larger than their own.

Many analysts maintain that both China and Russia have demonstrated the ability to catch up to the previous U. S. dominance in precision weapons. In fact, as chapter 2 and others note, this is the rationale for the search for a third offset. Yet the rapid diffusion of technology that has characterized the twenty-first century would suggest that any offset would remain fleeting. If one views globalization as a continuing trend, the constant deliberate, inadvertent, or illegal transfer of knowledge from “first movers” (in the case of AI, this is assumed to be the United States) to “close followers” seems inevitable.

Given the facts of demographics and economic growth—both prime elements of geopolitics—how can it be assumed that AI and autonomy can provide the United States with an offset that will allow for future military predominance? This is a question that, thus far, has rarely been asked and deserves considerable discussion, as do all the propositions.

**Table 5-2. The Six Propositions**

 
| 1\. Objectives for military AI development differ among the three military powers. Each has different incentives to adopt military AI. |
| --- |
| 2\. Objectives for AI development are as dependent on the nature of the government as they are on a specific military situation. |
| 3\. Each of the three AI military powers has a different level of control over commercial AI. |
| 4\. Each of the three AI military powers has different incentives to promote commercial AI. |
| 5\. Each of the three AI military powers will prioritize different military AI applications. |
| 6\. In a globalized world, China is the eventual natural leader in developing commercial and military AI. |

## **RECOMMENDED POLICY ACTIONS**

For the strategist, it is not enough to put forward propositions. They must be matched by recommended courses of action. Analysis motivates me to suggest five recommended actions that could enhance the development of U.S. military (and, potentially, commercial) AI development and mitigate the scale advantage provided by Chinese demographics.

First, and most obvious, is an (1) *increase in government funding for applied AI research expected to lead to military applications*. This is a recommendation made by most of the agencies and committees dealing with AI within DoD, and it does not require elaboration here.

What should be noted, however, is that all the identified previous offsets were the results of R&D funded by the federal government, not self-funded by commercial firms. There were no commercial markets for nuclear or precision-guided weapons and thus no prospect of development outside government funding. While AI does have commercial applications, the level of difficulty in converting commercial applications to military functions—particularly as identified in chapter 16 as well as others—may be quite high. The assumption that robust commercial AI development will inevitably translate into useful military applications is just that—an assumption that has not been adequately analyzed. National security requirements would appear better served by the opposite assumption that commercial R&D is inadequate and considerable government funding (an increase) is required to create an offset.

Given the differing levels of control and incentives for the development of both commercial and military AI, it behooves the United States to (2) *expand developmental collaboration in both categories with her allies, partner nations, and fellow democracies*. Commercial collaboration may be a natural prospect since U.S. companies involved in AI development seek and will continue to seek foreign subsidiaries and partners to enter and maintain market share in free economy nations. Although the U. S. government can give rhetorical support for such commercial collaboration, any major attempt at government involvement in this commercial process may be counterproductive. Commercial collaboration follows profit. However, efforts by the federal government to *dissuade* commercial collaboration—such as in the interest of retaining a marginal number of jobs—would likely have a restraining effect since they could include tax penalties or actions that reduce the profit incentive.

In contrast, U.S. government efforts to encourage *military* AI production would likely have a positive, supportive effect in the same way that other current cooperative multinational defense acquisition programs—such as that of the F-35—result in cost sharing and economies of scale, making acquisition more affordable for the parties involved. NATO provides the means for such cooperation between nations capable of both independently and cooperatively developing high-technology products, and it is very logical that collaboration within NATO could facilitate the development of military AI applications. Existing bilateral treaties with Australia, Japan, and South Korea could be used for similar effect.

Another mechanism for spurring military AI collaboration could be the Five Eyes intelligence sharing program (Australia, Canada, New Zealand, United Kingdom, and United States), since AI use in big data assessment has become a feature of intelligence analysis. They have been unconfirmed reports of the cooperative testing of AI algorithms within Five Eyes collaboration.^([32](#13_Chapter05.xhtml#rfn5_32))

Whichever mechanism is used, it would seem obvious that the United States should seek to collaborate on military AI development with at least its close allies, maintaining the same security controls that it does with other acquisition programs that rely on classified information. Such activity would seem the norm rather than an exception.

More controversial—and certainly requiring careful analysis—would be the possibility of U.S. collaboration with India, the world’s second most populous nation (1.34 billion) and a democracy that many see as a natural Asian rival to the PRC. India is also developing a high-tech sector within its economy, largely in cooperation (or as subsidiaries) of Western firms. If India develops an AI sub-sector to satisfy its own internal market, its gradually developing economy could make a commercial AI competitor and, in turn, a military AI developer.

Officials of all three of the AI powers describe the development of military AI as a strategic competition. As such, it is subject to the tactics that are a part of such competition: deception, espionage, and the development of countermeasures. As chapter sixteen notes, deception is a topic that has barely been discussed in the literature on AI. Deception is not just a battlefield technique. Like all software, deception can be surreptitiously built into the algorithms that control AI applications, particularly as DoD is dependent on commercial development by programmers or scientists who hold ulterior motives. There are great incentives for the competitors to attempt to manipulate potential opponents’ AI development.

Meanwhile, espionage remains a routine technique for the stealing of opponents’ technology, including AI systems. The PRC has been particularly adept at this, aided by the fact that the scientists involved in AI R&D have always viewed themselves as an open academic community dedicated to sharing knowledge, and thus have had little previous interest in security. This, however, is not necessarily true for R&D conducted within the Western tech companies, since intellectual property theft might give a competitor an advantage or at least an equal opportunity for market share, and thereby reducing company profits. As previously emphasized, commercial AI development is all about profits.

With this reality in mind, (3) *the U.S. DoD (and allied militaries) should ensure it adopts AI applications with the expectation that deception, hacking, and countermeasures are natural occurrences for which it must be prepared*. This goes beyond just security within DoD. Products adopted should be assumed to be suspect until proven trustworthy. Even then, assessments of tactical and operational countermeasures must be conducted. Is the AI application dependent on an electromagnetic spectrum that can be spoofed or jam? Would the failure of the AI system result in a catastrophic collapse in analysis, ISR, or operational decision-making? These are natural questions for strategists to ask and decision-makers to consider but, thus far, they have not been a feature of the dialog on AI.

Naturally enough, governments that control their societies have great advantage in security, intelligence, and counterintelligence. Open societies are at a disadvantage.

Given these possibilities, it is incumbent that (4) *the U.S. military (and allies) retain “legacy systems” that can perform functions that will be assigned to AI as back-ups or war reserves*. This argument goes beyond the application of AI, and needs to be repeated often, because the promise of new technology always includes claims for better, more efficient, and cheaper results than before. This promise becomes a siren song when proponents start arguing that previous systems should be discarded to save money to develop new systems or reduce maintenance costs. The very term “legacy system”—used repeatedly in defense literature—implies obsolescence and irrelevance. Yet in a war of attrition—which is what systemic-changing wars (the most dangerous security threat) inevitably become—nothing is obsolete once the inventory of high-technology weapons is expended.

Earlier discussion of Western firms supporting AI development within potential military opponents must be addressed. In particular, (5) *the U.S. government and allied governments must continually publicize the fact that Western AI companies who work with the PRC are inevitably contributing to the surveillance state*. This could be a first step in enacting regulations concerning the spread of commercial AI technology to authoritarian governments (which are the potential military opponents). The actual enactment of such regulations would, however, be extremely difficult. Wall Street and numerous high-tech companies would push back, since the PRC with its burgeoning population is seen as the ultimate future market for Western products. The thought remains that economic interdependence will inevitably loosen the control of authoritarian governments and, therefore, trade in technology with the PRC (or Russia) or creation of subsidiaries within the PRC (or Russia) should not be hindered. Unfortunately, there is no hard evidence to prove that sentiment. In the case of Nazi Germany, it seemed the result was the opposite.

To address that issue requires the United States and other democratic nations to retain the high moral ground concerning military applications of AI. To do this, (6) *the U.S. government should provide modest diplomatic support for an AI weapons arms control regime*. Thus far, the “ban killer robots” movement has conflated unsupervised AI with remotely controlled drones and other systems that retain “humans-in-the-loop”—which is a premise of U.S. military AI development. The U.S. government should encourage a restructuring of that dialog to focus on the potentially unsupervised AI weapons of potential opponents. That would be a worthy target of the arms control community.

Could AI arms control work; that is, could it create an effective, equitable, and verifiable regime that would control unsupervised, nobody-in-the-loop weapons? Probably not. However, it is worth the diplomatic effort to set the global dialog on future military AI to conform to the rule of law and individual human security. After all, Putin has already stated (undoubtedly cynically, given the Russian nuclear weapons programs) that “if we \[Russia\] become leaders in this area, we will share this know-how with entire world, the same way we share our nuclear technologies today.”^([33](#13_Chapter05.xhtml#rfn5_33)) The “Terminator” is indeed technologically out of reach, but it probably would be better if the competing nations agreed to forego it—however, with complete verifiability.

**Table 5-3. The Six Policy Recommendations**

 
| 1\. Increase government funding for applied AI research expected to lead to military applications. |
| --- |
| 2\. Expand developmental collaboration in both categories with allies, partner nations, and fellow democracies. |
| 3\. Ensure AI applications are adopted with the expectation that deception, hacking, and counter-measures are natural occurrences for which preparations must be made. |
| 4\. Retain legacy systems that can perform functions that will be assigned to AI as back-ups or war reserves. |
| 5\. Publicize the fact that Western AI companies who work with the People’s Republic of China are inevitably contributing to the surveillance state. |
| 6\. Provide modest diplomatic support for an effective, equitable, and verifiable AI weapons arms control regime. |

## **CONCLUSION**

All three of the AI powers—as I refer to them—see the military application of AI to be a strategic competition. However, this competition is not some sort of equal race. The motives that drive each of the competitors are different. The incentives for adopting military AI are not the same. The integration of commercial and military AI development is unequal.

Like all arms races in which the underlying technologies become diffuse, national wealth is a factor; as a historical Chinese Qin dynasty and imperial Japanese motto stated: “Rich nation, strong army.”^([34](#13_Chapter05.xhtml#rfn5_34)) However, if resources are comparable, authoritarian states have natural advantages in conducting arms races. For one thing, they can stifle domestic opposition to spending the resources. Employees of commercial companies who oppose the militarization of AI (witness Google) can be squashed. Authoritarians have the additional incentive in that developing military operational AI applications are likely to be useful for internal population control. George Orwell’s *1984* has long been a popular book, but *2049* would probably be a more accurate title.

As its population gets relatively wealthier and better educated, the PRC has a natural advantage in AI (and all tech) development because it possesses at least four times the human capital of its potential opponents. Some in the West are cheering for this because they perceive the opening of a huge market for high-tech products, additionally justified by the comforting thought that greater trade brings greater political convergence. Neither of these expectations has any science behind it, but self-justifying optimism can be seductive.

Nevertheless, neither the United States nor Russia should assume it can match AI development in China in the long term, let alone offset other military developments, without taking firm steps to develop a comprehensive strategy for the competition. The six recommendations in this chapter are intended to outline some of these steps.

AI may be, as the introduction and other chapters suggest, one of the most beneficial technological developments of the future. However, it can benefit authoritarian states at least as much (probably more) as democratic states in either maintaining or overturning the current world order.

### **NOTES**

# 6

Battlefield Innovation on Patrol

**Designing AI for the Warfighter**

NINA KOLLARS

**Duffer is on day ten of her assignment** to document the life patterns of the people in a remote village. To assist her and her team, Duffer has an Internet-enabled computer tablet. With a few clicks and some labeling, the tablet feeds data back to a data integration drive, where a newly designed learning algorithm is busy doing some sort of magic beyond Duffer’s paygrade.

To collect her data, Duffer’s team transits by vehicle past long rows of rice paddies and lotus plants to the village. Upon arrival, they dismount and spread out to explore the narrow footpaths and side streets, taking account of the daily life of each family. Duffer is in the middle of her morning walk. Upon arrival at the end of a newly explored footpath, she sees a person she doesn’t recognize—a young woman dressed like a city dweller rather than a local farmer. Duffer finds this odd and decides to approach her. Duffer instinctively prepares her tablet and body cam. *Okay, you big brain*, she thinks, *what’s going on here?*

Duffer knows that, as her observational data is automatically drawn into the system, it is integrated with all the other observational data from her five-person team. The database of life activity in the village has been growing. In addition, with it, the learning software has begun to generate a vignette of the village’s life patterns. From that life pattern, the AI software’s designers think that they can generate reports about stability patterns. Unfortunately, according to those reports, stability has been declining over the past few days, and no one knows why. The AI software has some guesses … but so does Duffer.

## **THE PROMISE OF THE AI FOR THE WARFIGHTER**

AI is not a condiment. You cannot just sprinkle it on top and make everything better. Most writing about these potential technological additions spends more time explaining the technology and not enough time examining the complex and often deeply tacit spaces we weave them into. This is not only irresponsible; it also leads to ridiculous overestimation of what and where things can be made more effective and lethal.

The purpose of this chapter is to tackle three tasks in analyzing the costs and benefits of intelligent automated systems for warfighting. First, in terms of scope, I attempt an opening salvo at examining the potential implications of artificial intelligence (AI) for the individual warfighters—the practitioners—in their operational roles. Second, I consider the ways those systems might enable or disable innovation on the battlefield—specifically experimentation and development of previously unconsidered solutions within the context of use. Finally, I attempt to complete those two tasks in as specific and simple language as possible.

Why does this matter? The reason to do these three tasks in this chapter—in the spirit of this entire volume—is to move beyond the hand-waving obscurities and overly hyped terms such as “artificial intelligence,” “deep neural networks,” or “machine learning” toward something concrete. In my own estimation, the language of future technology is too elevated and out of context to be meaningfully understood. And if we don’t understand it, there’s no way to implement it. We cannot possibly know what we mean by the “effects” of these new forms of pattern recognition and automation until we put them into a specific context and think through the second- and third-order effects. For the purposes of this chapter, then, I will eschew ambiguous terms whenever possible and try to get as close to meaningful as one can about “future warfighting.”

In thinking through exactly to which functions we intend to apply the new systems, it is not uncommon—for example—to hear innovation gurus suggest that we should implement “AI for logistics.” On its own, that could mean a myriad of things—perhaps supply chain automation, agile path selection for moving supplies over oceans versus land, and so forth. To examine the overall suggestion, I will confine the discussion to one potential function: tracking which assets are on domestic soil and where they are. One method to do that is to introduce pattern recognition software into whatever supply/asset tracking system is already in place, to enable planners to learn previously unconsidered pathways to buy, maintain, and push assets from one place to another.

Initially, that sounds like an excellent and relatively low-cost idea. However, let’s put this into specific context. To artificially “intelligentize” the task, one presupposes that the tracking system is constructed in such a way that software could be meaningfully “introduced.” In practice, it is likely that there is no single unified system on an existing computer system for logistics. Instead, it is likely to be a patchwork of semi-automated, outdated systems connected by actual physical mechanisms that involve real-world human labor (observing, reporting, hand counting, note-taking, data entry, and so forth). Furthermore, it is probable that there are underlying but long-forgotten political reasons why the system is constructed in piecemeal fashion, including all the messy social aspects of major militaries—think domestic pork-barrel politics, defense industrial base proprietary requirements, and interservice incompatibilities. Under such circumstances, the system will probably need a complete overhaul in order to implement AI. If that ever gets completed, the software will likely offer elegantly efficient but politically toxic solutions that are impossible to implement.

The takeaway from this example is that the introduction of any new software or automation technology into a complex system requires even more consideration of the context of human systems than of the new technology being introduced. Building solutions outside of the human social context is easy. Building them for the human context is the actual challenge in implementation. Therein lies the innovative paradox: the reaction of a social system into which technology is introduced has more of an effect in implementation than the machines or ideas themselves.

The user system examples discussed in Duffer’s scenario are illustrative and may not exist today, but they are the types of tactical AI capabilities defense planners appear to envision. They also relate to functions performed in Iraq and Afghanistan in tactical cultural factors intelligence analysis.

## **BATTLEFIELD INNOVATION RESEARCH AND LITERATURE**

Many of the analytical discussions on AI technologies have centered on the speed implications of automating decisions, the so-called human-in-the-loop, human-on-the-loop, human-out-of-the-loop debate.^([1](#14_Chapter06.xhtml#rfn6_1)) However, my own research indicates that user-oriented designs of smart systems are more important when it comes to future warfighting and innovation.^([2](#14_Chapter06.xhtml#rfn6_2)) The question of whether there is a human in the loop is less important than the imperative for creating systems for warfighters that enable experimentation and on-site problem solving. Fulfilling this imperative will prove more determinative than any drawn-out abstract discussion of speeding up in, on, or out of loops.

Innovation matters in warfighting. In the literature referred to as security studies, academics have built a long history of analysis concerning the capacity for militaries to change in ways that produce positive effects on effectiveness, efficiency, and victory. That literature traces back to a root discussion of what is referred to in modern terms as the revolution in military affairs (RMA).^([3](#14_Chapter06.xhtml#rfn6_3)) The term is an attempt to describe the processes through which militaries might gain an advantage over other (primarily great power) militaries—usually through the use of new concepts and technologies. The language of RMA has since been supplanted by the more business school–oriented lexicon of “innovation” from which stemmed an additional surge of research, not simply on overall improvement, but on game-changing capabilities that cause a fundamental reordering of military operations and strategy. This subset of the military change literature is generally framed by its use of “disruption” or “disruptive innovation.”^([4](#14_Chapter06.xhtml#rfn6_4))

Subsequently, an additional thread of research on tactical wartime solutions began to appear in the literature. The so-called bottom-up turn in military innovation research postulates that not all military technological and organizational change comes at the direction of elite (senior) decision-makers. Rather, solutions can and do come from warfighters on the front lines and other experienced practitioners who are not on the front lines of combat but are supporting operations.^([5](#14_Chapter06.xhtml#rfn6_5)) The insights of this literature form the core of this chapter’s questions but are further informed by one additional set of insights—that of user innovation theory as set forth by Eric von Hippel of the Massachusetts Institute of Technology’s Sloan School of Management. Von Hippel’s area of expertise is in the phenomenon of user-based problem solving. In standard models of the market, firms produce products for consumers, and since firms want to make a profit, they have some incentive to produce goods a consumer will purchase. However, often the producer has no real sense of who the consumer will be or which communities are underserved by the goods already on the market. User innovation theory argues that in the absence of effective solutions offered by the market, consumers will produce their own solutions and often form communities to share those solutions with others.^([6](#14_Chapter06.xhtml#rfn6_6)) This behavior closely mimics the efforts of warfighters throughout history, and as such, its mechanisms naturally align with the bottom-up innovation literature. These key insights are incorporated into Jon Lindsay’s work on FalconView and my own work on innovation in Vietnam.^([7](#14_Chapter06.xhtml#rfn6_7))

Despite the surge of research on innovation, the factors examined by political scientists generally rely upon studies of organizational decision-making or some notion of leadership expertise as playing a part in driving innovation. This is decidedly an overly narrow view of the interaction between machines and humans in the battlefield environment. Few, if any, works in the scholarship on military innovation emphasize the role of user interface or machine design as enabling battlefield innovation. I offer here the beginning pieces of a theory that might generate testable hypotheses in their relationship to battlefield innovation. As a starting exercise, I suggest three characteristics that might inhibit or enable user-driven change on the battlefield: the transparency/opacity of the decision, whether the machine suggests solutions or overrides the warfighter’s choices, and whether the machine extends or replaces entirely the role of the warfighter.

These characteristics are new to the social scientific research on military innovation but are commonplace in engineering design research. Specifically, those aspects of engineering design that take into account user/practitioner behaviors are key to thinking about the kinds of creative responses practitioners might have while interacting with new machines.^([8](#14_Chapter06.xhtml#rfn6_8)) The literature on human-machine interaction is split into two core literatures: the social construction of technology (SCOT), and the applied engineering work of research laboratories.

SCOT research is derived from the field of the study of science and technology. It examines how machines are implemented, given human social systems of interaction. Works of this nature tend to be highly qualitative and to rely on observations and process tracing to explain why and how machines are adopted and change over time.^([9](#14_Chapter06.xhtml#rfn6_9)) Also included in this research arm is the historical recovery of how science as a practice creates new disruptive technologies such as missile guidance systems,^([10](#14_Chapter06.xhtml#rfn6_10)) as well as the work of technologists who develop potential future human-machine theories given those existing patterns of behavior—for instance, the effects of introducing more robots into everyday life.^([11](#14_Chapter06.xhtml#rfn6_11)) The SCOT literature, it is important to note, is an interdisciplinary agenda with a broad methodological commitment to more closely examining the determinants of our mechanical future. Thus, it is not without its own established and critical theorists—among them Karl Marx himself.^([12](#14_Chapter06.xhtml#rfn6_12))

Engineering design, specifically those aspects that influence user behaviors, is an applied field that studies the effects of things such as ergonomics, user interface, and advanced haptic feedback as factors that affect the ways in which humans interact with their machines. The field takes into account an extremely broad range of factors from physical to cognitive constraints of the human capacity to adopt new machines.^([13](#14_Chapter06.xhtml#rfn6_13)) The limitation of this work for our purposes is that the engineering design literature tends to focus on either blanket acceptance of the machine or the conditions of rejection. In Jeff Dyck et al.’s work, for example, adjustments in how game players engaged the software through the screen are considered successful by their measurement in terms of “user satisfaction.”^([14](#14_Chapter06.xhtml#rfn6_14)) From the frame of entertainment, satisfaction is one thing. When it comes to war technologies, satisfaction is but one component that should also include outcomes and, in our case, whether new solutions are created in the process of use.

This chapter draws from both schools of thought to arrive at some sense of the innovative potential of pairing well-designed smart machines with war-fighters. Rather than adhere to a single field—one that examines the effects of humans on machine use or the effects of machines on human adoption—this chapter accepts the interaction between these fields and posits factors that are present in both literatures as potentially productive. In this way, the author’s approach most closely aligns with the more integrative perspective of theorist Langdon Winner, who neither succumbs to technological determinism nor declares an optimism about our future in relation to machines.^([15](#14_Chapter06.xhtml#rfn6_15))

## **AI AND BATTLEFIELD INNOVATION: ENABLING OR DISABLING BY DESIGN**

Despite our most highly advanced computers and analyses of how and when to conduct military operations, the fog and friction of the battlespace require adaptability—at least if a force is interested in victory. Since warfighting is a complex endeavor for which prediction is impossible, militaries must inculcate a capacity to adjust tactics, techniques, and procedures (TTPs) to the context of the battlespace at hand.^([16](#14_Chapter06.xhtml#rfn6_16)) Effective use of new technologies, even unmanned autonomous systems, must account for the uncertainty of warfighting and the unanticipated context of application at every level of war—the strategic, the operational, and the tactical. For AI to have an effect on warfighting, it must support “in stride” adaptation at the tactical/operational level as applied by practitioners as they apply the tip of the spear to the problems of combat.^([17](#14_Chapter06.xhtml#rfn6_17))

Regardless of whether a service invites its practitioners to adapt their kit or TTPs, the practitioners will inevitably do so.^([18](#14_Chapter06.xhtml#rfn6_18)) This means that battlefield innovation is potentially a double-edged sword. Ignore the creative capacities of the practitioner, and the technology risks suboptimal use or complete rejection; but create an open design that encourages practitioner adjustment, and the leadership risks the spontaneous creation of applications that contravene laws or commander’s intent or simply create confusion for other users.

How should we design these new capabilities with this behavior in mind? Whom should we enable to make technical adjustments on the battlefield, and in what way? I offer an opening salvo—undoubtedly incomplete—of considerations concerning the design of learning algorithms in the context of enabling or disabling battlefield innovation. Specifically, I offer four design questions as they pertain to the individual practitioner.

•  Will the technology’s decision points be made opaque or transparent?

•  Will the AI systems input to the field user be suggestive or overriding?

•  Will the AI system provide a new capability or simply make an existing process more efficient (or cheaper)?

•  Will the technology support, extend, or replace the warfighter’s function with something different?

The answers to these preliminary design questions will affect battlefield innovation by

•  directly editing decision-making chains by creating new instances of nondecision and hyper-decision

•  enabling or disabling creative inputs at the user level

•  shaping the audience and purposes of lessons learned—whom they are intended for and who has access to them.

In short, smart software and learning machines do not automatically make situationally adaptive battlefield innovation more or less likely. It will depend on the deliberate choices made in the actual design of the systems and the context of use. For the purposes of this exploration, I will return to my narrative vignette of Duffer, a single warfighter on a notional patrol conducting routine reconnaissance.

## **OPAQUE, TRANSPARENT, SUGGESTIVE, OR OVERRIDING? EDITING THE DECISION CHAIN**

One of the fundamental misconceptions of the current state of data integration/analysis is the belief that the need for time-consuming and complex human decisions at the scene of action will be eliminated. Thus, humans can act without having to ponder all the possible alternatives (and possibly missing a few). While this could certainly happen, it needn’t necessarily be the case (nor might we want it always to be the case). Again, this is a matter of design. Learning systems can be designed to reveal the patterns and correlations that are driving their recommendations or actions—in other words, to be either transparent or opaque.^([19](#14_Chapter06.xhtml#rfn6_19)) They can also be designed to invite user input or deny that input altogether—to be suggestive or overriding.

Transparent systems are designed to reveal how and why they have arrived at a path or course of action. Think of it like watching movies on Netflix or Amazon Prime. When you click into the app, it shows you titles you’ve never heard of before. Rather than leave you wondering why you’re viewing this (and perhaps to reduce the fear that someone else has hijacked your account), the system explains itself. The app reminds you why it is showing you these movies by displaying orientation messages such as “because you watched *X* and *Y*, you might like Z.” The system is attempting to explain the logic of its recommendation and how it came to decide.

Perhaps somewhat more insidious are semitransparent systems that work through nudges rather than sheer transparency. For systems trained on an individual’s preferences (for example, your personal Amazon page), the algorithm can attempt to influence the user’s purchases without their specific conscious efforts to shop (the mark of a consumption-based economy). In opaque systems, the learning software offers no justification for its actions or paths offered.

Moreover, as in the Netflix example, systems (regardless of transparency or opacity) can invite or deny choice to a user—they can be suggestive or fully overriding in their course of action. What does this look like? Consider modern navigation systems like Waze or Google Maps. At a pivot point in your journey, the app asks whether you’d like to choose an alternate route due to changed traffic conditions. The software has gathered its insights about weather, road conditions, and the state of traffic, and it updates its recommendation about the best path to the destination. Conversely, the app could simply update without asking, leaving the user in the dark about the reasons behind the updates to the pathway—this is more akin to when the airlines cancel your flight; they simply rebook you into another ticket and let you know once a seat is secured. You can dispute their choice, but you cannot peer into it. In this sense, learning software doesn’t necessarily (and pragmatically in most cases should not) eliminate decisions in a decision chain, but it can be designed to. That is a question of control.

## **RETURNING TO THE SCENARIO**

Duffer taps the body cam awake and begins recording her discussion with the young woman. Duffer knows the system has already captured the woman’s image and is pushing snippets of the conversation into a database for later analysis by—who even knows? Perhaps the big brain is checking for regional dialects, capturing names mentioned and cross-referencing them, assessing threats to personnel. Or maybe it’s just her boss making guesses about what it all means. Duffer shrugs; she pulls out a notepad and a pen to jot down her own thoughts separate from those of “Whiskers” (She’d named her AI tablet Whiskers.… Somehow that helped her like it more). She wants to be sure she records her own thoughts for the after-action report.

Duffer notes that she’s a little irritated that the tablet keeps sending a buzz alert to her ear. She’s trying to focus on speaking to the young woman who is noticeably nervous about being questioned. Duffer isn’t sure if it is her side-arm, the headgear she uses to communicate with Whiskers, or the fact that they’re out in the open and people might see the conversation. Duffer silences the buzz—it’s only a notation message, nothing immediate—and completes the conversation. Sometimes Duff is a little uncertain whether she understood the woman’s answers, but the active translation function in her earpiece is a nice double-check.

After a few minutes of conversation, she pulls up the tablet’s message. Facial recognition yielded no positive results on the scan, but the story checks out. There is an elderly couple in town who have a daughter who lives in the city up north. Recent captured discussions of the couple indicate that they’re excited she’s coming home for a few days from the big city. The young woman is reportedly four months pregnant, and everyone is planning a party.

Duffer smiles. This is a good sign. No matter the depth of data the AI has, that elderly couple’s instincts are strong. They would never allow their daughter to come back to the village if it was dangerous. Perhaps things are getting better. Still, the young woman seemed rail-thin and not exactly the picture of a healthy pregnancy—or perhaps no pregnancy at all. Is this a sad story, or a sign of a threat?

Duffer jots down these questions in her notebook and continues her route. Just then, the tablet offers a suggestion: “Duffer, based on your prior week’s excursions we suggest that there are four potential routes that have yet to be taken for data capture. Would you like to follow a new route?”

She mutters to herself, “Gosh, that is probably the right thing to do.” But Duffer is hungry for something other than her MREs. She knows there’s a local rice ball shop that makes her favorite seasoned fish and seaweed rice ball. They’ll be ready and fresh if she goes back to her usual route.

Duffer utters, somewhat guiltily, “No thanks, Whiskers; dismiss route. I’m taking the usual route past rice ball vendor.”

The tablet responds, “Duffer, there is an unexplored route that intersects with the rice ball shop, would you like that route?”

“Creepy little lunch spy!” Duffer scowls. She’s a little spooked that Whiskers wasn’t only watching the villagers. The AI also follows her and learns her preferences. Still, it is better than having no choices at all. Duffer is also frustrated with Whiskers. The relationship is usually a one-way interaction (like with any good cat). Whiskers suggests routes and queries her regarding information it wants, but at the end of the day, Duffer really doesn’t quite understand why Whiskers thinks instability is on the rise. Duffer agrees to the route and walks on, allowing Whiskers to coach her left and right turns, watching the footpaths all the while. If only Whiskers would answer her more analytical questions rather than just talking at her all the time.

## **IMPLICATIONS OF THE SCENARIO**

In Duffer’s path so far, there are competing (and perhaps contradictory) reasons to make a system opaque and overriding or transparent and suggestive. The choice of one or the other edits the decision chain. By making a learning system opaque and overriding when in the hands of the practitioner, the design takes the decisions previously made by the user and moves them into the system. Since the actions required of the warfighter have been adjusted, that system has control over picking a new path, which forces Duffer to consider other aspects of the environment around her in making an alternative decision that is “outside the system.” Duffer is forced to “override” the overriding system in order to initiate an alternative, perhaps losing much of the value of the system.

Conversely, making a system transparent and suggestive enhances and even introduces new decisions, giving the user more agency regarding the best course of action. This also means that more responsibility for the actions is pushed downward. Duffer may not want to search the new path because she wants a nice lunch. The tablet nudges again, and since Duffer is a responsible warfighter (and not all will be), she accepts the compromise. In this, she does not lose the value of the system even when (previously) considering an alternative.

Consider that the system’s automatic response was to conduct the translation as well as make body camera and audio recordings. These decisions are designed into the system without Duffer’s vote. Also of note is Duffer’s sense that her AI is spying on her and not simply recording data about the village. This affects how she feels about Whiskers. Too much direction and spying from Whiskers might result in Duffer “accidentally” dropping the tablet and conducting the patrols on her own. In this case, the balance of design nudges Duffer to a compromise in action.

So far in our narrative, Duffer has an inkling that Whiskers is wrong about the increasing instability in the village. Duffer, however, has no access to Whiskers’ correlations that lead the system to affirm that instability is increasing. She’s frustrated by this. The system has been great at helping her be more thorough in her job, but the system isn’t designed for Duffer to explore her own questions about what is making Whiskers nervous about village stability. If that correlation is available, it isn’t on her level. If it was, Duffer might be able to offer additional insights about how to determine whether those correlations are causal. Instead, she hopes that her journal notes will be of some value when she gets back to base. Recently she’s become convinced that whatever Whiskers appears to be learning might be somewhat off target. She’s asked her teammates to supplement Whiskers’ work by taking their own notes.

Whiskers’ design is partially transparent and partially opaque. Whiskers is a suggestive AI rather than an overriding one, but it definitely is designed to function as a collector of data regardless of Duffer’s willingness to participate.

## **SUPPORT, EXTEND, OR REPLACE WARFIGHTER FUNCTIONS?**

Design features aside, the kinds of battlefield innovations likely to emerge will also be affected by what the learning algorithm is intended to do for the practitioners, with the practitioners, or in addition to what the practitioners are doing in their occupational specialties. If the system is designed to offload from the user basic, repetitive tasks that the practitioners would have previously done (and are now being done by the system), the user now has more time and space to think more deeply in their role. In this case, the practitioners gain higher levels of mastery in their jobs as the automated system reduces well-established rote data and information tasks that previously burned up their time.

In such a case, warfighter innovations will be enabled from the warfighters themselves because of the offload, rather than innovations being created through the technology itself. Potential innovations will emerge not from machine-human interaction, but rather because of it. In contrast, if the learning algorithm is designed as an assistant to support the warfighter, the interaction between the learning system and the warfighter could produce new insights or ways of doing the task. (This would be, of course, contingent upon the prior design factors.)

Finally, it is least likely that battlefield innovation will occur if the smart learning system is designed to replace the practitioner entirely—to reduce the practitioner to a set of legs and fingers pushing buttons. In this case, the only innovation introduced is the replacement of the warfighter—which is not a battlefield innovation. The embodied context of learning through the conduct of the mission is covered over by the replacement of the human body by the system. However, this might be the appropriate outcome for certain kinds of high-stress environments where practitioners are under too much duress to engage in creative problem-solving. But it is not effective innovation in war (as opposed to before or after war).

More distressingly—in this author’s estimation—replacing the role of the practitioner for most occupational specialties with complete automation risks creates novel dependencies that not only limit the likelihood of battlefield innovation through or by the new technology, but also could create new systemic operational vulnerabilities, since the warfighter’s skills in conducting their role may atrophy in the course of replacement. The atrophy of basic warfighting skills due to automation is a fundamentally dangerous prospect. It reduces a force’s capacity to degrade gracefully as conflicts draw out and support conditions diminish. In this sense, any military that designs for a full AI-versus-AI conflict—let’s call it robot-on-robot war—is a foolish one. Warfighters can only train on so many skills. Maintenance of robots in a fully robotic force could arguably occupy an entire force’s time and money. While maintainers are a fully respected component of the support for combat, an army of maintainers is not a warfighting force.

## **BACK TO THE SCENARIO**

Duffer has completed her new route with few new insights. She’s grateful for the automated data collection of Whiskers, which allows her to ponder what she wants to do later in the day—maybe write a few letters to her family and get some time at the gym. She knows she needs to pay attention, but Whiskers seems to have most of that managed for her, and since Whiskers doesn’t really seem interested in Duffer’s thoughts, there’s no reason to explore the relationship any further with her AI buddy. Sometimes she wishes she could just put Whiskers on one of the local neighborhood dogs; it seems like all she is these days is a pair of legs and a human face to the villagers.

Duffer spies Corporal Swinton coming around the corner. Swinton’s machine buddy is an experimental one that is interactive. Swinton is constantly asking her buddy “Mr. Ed” research questions about terrain patterns, weather changes, demographic shifts, and the particular cultural norms in the village. Swinton says it’s because she suspects that there are serious problems with the farming crops this year, but that the villagers are too reserved to talk about food supply issues with the team. Whiskers isn’t designed to fetch and reformulate data the way Mr. Ed is. Duffer finds herself a little jealous of Swinton’s buddy. At least Swinton can explore her ideas with Mr. Ed.

“Any new ideas, Swinton? You and that brainiac machine keep nerding out on the rest of us.”

“Yeah, boss, Ed and I have a few ideas. I’ve been scanning my notes at the end of the day. Ed wants to know if he can have a look at yours too. In fact, I’ve been making Ed chase down potential explanations for the unrest here. So, if everyone else in the team doesn’t mind, we could have Ed scan their notes too. You know, just to see what patterns might be emerging.”

“Why doesn’t Whiskers do that for me?” Duffer notes that Swinton refers to Ed as “he.” Whiskers doesn’t really have a gender. This AI stuff is so weird.

“Sorry about that, Whiskers is an older model. Definitely more stable, Ed is wicked glitchy, and he needs more data than Whiskers, but Ed is designed to work with me, not around me, or instead of me. Don’t get too jealous, they’re both spies. Last week I got written up for trying to bypass Ed’s security settings so I could post something to my Instagram.”

“SWINTON! Knock it off!” Duffer was doubly pissed—first, because she had no idea about this breach in protocol, and she should have been notified. But second, because Swinton’s use of social media on the job was a serious security issue.

“I know, boss, but I wanted my network to identify a weird looking bug that I found in the rice paddy. Ed had some guesses, but I couldn’t get a clear picture. I wanted to tap into the hive mind of our community to see if anyone who has deployed here before had ever seen it.”

Duffer listened closely. Then she queried Swinton. “Hey, do you figure we could have Ed try to identify environmental changes that we are all capturing in our notes that maybe these systems just don’t see?”

“That’s the plan, boss.”

“Okay, but even more importantly, do you figure we could get Ed to start looking at any notes that the unit before us collected? Or, even more interesting, we could be sure to have everyone across all units in this region take notes on every patrol and let Ed try and get a bigger view—in a sense he’d be learning from us and our thoughts over time and across a broader area.”

“You mean he’d be creating our own private hive mind of recon teams? Boss, that’s super cool. I’ll get on it. And in the meantime, we need to get you an upgrade.”

## **CONCLUSION**

The narratives have attempted to highlight that at the applied level of context, the innovative capacity of smart machines will shift based on users, on the environment, and on the design of the system itself. Certainly, the limits of thinking about future technology dictate that the narrative has analytical limits. However, when buttressed with the insights of the literature on machine design, there are clearly better and worse potential pathways when it comes to battlefield innovation. As suggested in Mitchel Resnick et al.’s work on tools that enable creativity, creating systems with what they refer to as “low threshold, high ceilings, and wide walls”—designing tools that are approachable to novices but permit increasing levels of nuanced problem-solving—should be one of the key components when trying to initiate user problem-solving.^([20](#14_Chapter06.xhtml#rfn6_20)) As suggested above, single-sided opaque systems that are largely passive risk turning warfighters into mere legs and arms rather than on-site analytical thinkers, thereby stifling any potential new thinking with the new technology. To be fair, there are right and wrong times to invite creativity. Unlike in the business world, where the threat of deadly attack is unlikely, in military situations threat or risk to mission must be taken into account, not just the creative thinking processes. In our case, the entire “innovation” conversation between Duffer and Swinton happens out in the open, inviting serious risks to mission and force protection. To this point, the narrative could have easily and plausibly carried forward with an ambush on Duffer and Swinton by enemy forces as they direct their focus on screens and systems. This is truly something the reader should take seriously concerning the appropriate times to engage in creative problem-solving. If the scenario had another author, Swinton and Duffer could be dead.

Nevertheless, Swinton and Duffer dream up an alternate adaptive use for Mr. Ed, one that moves beyond its original intent. It is an innovation in Mr. Ed’s capabilities. Careful design and interactive components of smart systems can make this possible. The innovative solution that Duffer and Swinton come up with—tapping into the hive mind of machines and practitioners—accesses a particularly thick vein of new Internet-enabled horizontal knowledge management of how to most efficiently aggregate and transfer information.^([21](#14_Chapter06.xhtml#rfn6_21)) Interestingly, though, most of this literature does not recognize that the hive mind phenomenon is actually a recurring aspect of military innovation. Historically, it has been developed repeatedly, ad hoc, by practitioners in war. Whether during Vietnam in the form of potential new technologies to develop,^([22](#14_Chapter06.xhtml#rfn6_22)) in magazines created by World War II Eighth Army Air Forces fighter pilots over Germany,^([23](#14_Chapter06.xhtml#rfn6_23)) or in Iraq with the creation of tiger teams,^([24](#14_Chapter06.xhtml#rfn6_24)) practitioners tend to innovate by creating horizontal networks of data and experience—whether or not their leaders want them to. Leaders would do well to know history, prepare for these behaviors, and design these capabilities directly into their smart systems.

Finally, thinking not simply in terms of adoption but in the potential for resistance to the implementation of machines will affect the overall success of implementation. Designing for potential user resistance requires putting oneself in the situation of the practitioner and thinking through how and when the machine might make their mission more complex. Too much flexibility in the user machine interface, and the practitioner might focus too much on the machine and not enough on their environment; too much rigidity, and the likelihood of all-out rejection of the technology looms. Duffer and Swinton demonstrate some level of frustration with different designs. Duffer clearly wants more out of Whiskers than it can offer. Technological resistance at the cognitive/user design levels will ultimately affect adoption and, thereafter, innovation.^([25](#14_Chapter06.xhtml#rfn6_25))

Overall, this chapter has explored one tiny window of applied use of a smart system. The narrative functions purely as a way to help the reader understand that there are no sweeping generalizations at the practitioner level that can be made about the revolutionary or evolutionary promise of machines. It is the interaction between environment, machine, and humans that results in some kinds of battlefield innovation. The question for requirements writers and acquisitions processes to confront seriously is just how much interaction, transparency, replacement, or extension is appropriate for the future force. Only once we have arrived at those kinds of answers will we begin to realize the potential of smart machines and understand their effects on battlefield adaptability and innovation.

### **NOTES**

# 7

Mission Command and Speed of Decision

**What Big Data, Artificial Intelligence, and Machine Learning Should Do for the Navy**

ADM. SCOTT H. SWIFT, USN (RET.), AND ANTONIO P. SIORDIA

AI will not displace humans; it’s going to enhance us.

—Ray Kurzweil^([1](#15_Chapter07.xhtml#fn1))

**Before we can have a discussion** of how artificial intelligence (AI) could enhance command and control (C2), and the particular form of C2 that we refer to as *mission command*, it is important to understand the basic realities that cover all three (despite being used as a combined acronym, command and control are two different things).

Reflecting on Ray Kurzweil’s statement, the first reality is that the concept of pursuing process improvement tools for enhancing C2 is not new. Commanders, and those they command, have consistently sought more effective and efficient ways to execute the process of command and control of combat forces since time immemorial. This effort has largely been incremental in nature, spearheaded by particularly foresighted commanders facing acute operational challenges. To apply AI to this effort in the future is, in popular vernacular, a “no brainer.”

Unfortunately, the second reality as it applies to the incredibly complex leadership, management, budgetary, strategic planning, and political environment of modern naval operations is that our collective *institutional* interest in making *significant* enhancements to C2 as a process generally occurs when something goes wrong. Too often when command failures occur, initial efforts focus on the actions of those in command.

While important, we view these initial efforts as insufficient for characterizing the nature of any command and control failure or a critical review of the failed C2 process. When failure occurs, it is the elements within the process—such as the sometimes nebulous impact of the environment from weather, or an enemy that has not followed the expectations of intelligence, operators, and planners—that are not adequately reviewed. Consequently, human failures are addressed without a full understanding of the true nature of the contributing elements that led to the failure. In highly functional organizations, a holistic C2 systems review is (or should be) conducted and lessons learned gathered and applied. Ideally, but rarely, they are tested, critiqued, and incorporated into doctrine as well. The ramifications of applying the tools of artificial intelligence to a system with the potential for flaws need to be clearly understood, even *before* we attempt to apply AI. Command and control is not simply a collection of tech systems. Adding AI to a C2 process in which we have not incorporated the lessons learned through past human failures can simply ensure that failures ensue faster. It is the process of C2, not AI itself, that will always remain the critical element. That is the third reality.

## **HISTORICAL ATTRIBUTES OF EFFECTIVE C2**

Technophiles who predict great results from AI rarely express an appreciation for history, but AI cannot be applied effectively to C2 without examination of successful command and control in past battles. While earlier historical examples exist, Admiral Lord Nelson and his flag officers provide a good place to start a baseline understanding of C2.

There are a number of authoritative books on Admiral Nelson, his mentorship and leadership of his fleet, and his understanding of the differing nature of tactical and operational signals and how they can have positive and negative implications at both of those levels of war.^([2](#15_Chapter07.xhtml#fn2)) This potential for both positive and negative effects is especially true when up-echelon signals (from subordinate to superior command) are tactical in nature but are based on intelligence and knowledge that cannot be expressed in the signal and are thus unknown to the commander. Under these circumstances, a resulting disconnect between what is occurring and what is being ordered is often dismissively characterized in postbattle reviews as the result of the “fog of war.”^([3](#15_Chapter07.xhtml#fn3)) The disconnect is addressed “dismissively” in that the term is applied as validation that the fog of war cannot be managed and, as such, no further study and critique are required.

Yet habitually successful commanders anticipate the fog of war, recognizing that its inevitability in some form is a given. Its scope and scale not only *can* be managed, they *must* be managed. The question then arises as to how, when, and where it is appropriate for AI-based tools to help with this management. Scope and scale are managed through clear strategic guidance, establishing realistic operational objectives, and providing the necessary tactical latitude and broad guidance to subordinate commanders so that they, in turn, can leverage their tactical understanding of their environment and act accordingly with the tactical tools at their disposal. These are all qualities of human commanders, honed through mutual training and interaction, that do not seem to be captured in an algorithm, no matter how complex. If indeed AI can act as a decision aid, it must deal with the fog of war. Right now, ambiguity is not something AI can deal with without the acquisition of big data. AI also needs to complement the core attributes of successful warfighting—which are designed to deal with situations where there are no big data.

History indicates that core attributes to successful warfighting include

•  clear strategic guidance developed at the national level and communicated to operational commanders

•  operational commanders developing clear operational objective frameworks from this strategic guidance

•  through combined planning and delegated authority, the empowerment of subordinate commanders to execute the necessary tactical actions to achieve operational objectives in support of strategic guidance.

Both a top-down and a bottom-up flow of ideas, information, and knowledge must occur in the planning, execution, and assessment phases of war-fighting. Command and control is the mechanism through which these core attributes, this up-and-down information flow, are managed prior to and during battle. It must be anticipated that it will be impaired throughout by imperfect knowledge and operational resource shortfalls in supplies, equipment, people, training, and readiness, to name a few.

## **NELSON’S APPROACH TO C2**

Nelson’s approach to this dilemma included three warfighting principles that remain applicable today, especially to the subject of this book. He applied these elements in preparation for battle, recognizing the fog of war would make their application in battle difficult. The first two principles apply equally well to any era of warfare, but the third point stands to become truly transcendent when enabled by artificial intelligence. The first principle, to seek the knowledge, advice, and counsel of subordinate commanders, is self-explanatory. The second principle is to spend more time listening than talking, making sure feedback to subordinates is relevant to the strategic guidance given to you, to your derived operational objectives, and to the tactical realities they shared with you. Admiral Nelson’s feedback was as clear and unambiguous as possible while remaining broad and encompassing. He was an active listener, absorbing his subordinates’ tactical insights and providing in return clarity on his operational guidance with respect to what operational outcomes he sought in support of the strategic guidance that had been given him.

The third principle is, as battle approaches, to seek face-to-face exchanges with as many subordinate commanders as possible, collectively. This approach aims to avoid translation loss in exchanges between subordinate commanders misinterpreting what those present heard and what those absent were told. A key change in this last face-to-face exchange was that Nelson was doing the talking, soliciting questions and eliminating his subordinates’ uncertainty as to meaning to ensure his “commander’s intent” was as clearly understood as possible in both construct and context. This was critical to allow subordinate commanders the latitude to make tactical decisions that remained inherently supportive of Nelson’s operational objectives despite the ensuing fog of war. This discussion, the last face-to-face exchange between Nelson and his commanders, was focused on their jobs of determining the “what” and “how” of actions based on the tactical realities they faced at a moment of time in the battle without losing sight of his charter to achieve a positive operational outcome of strategic consequence at the end of the battle.

These elements are reflected in Nelson’s focus on expertise and precision with respect to the utilization of flag signaling. Their application was just as regimented and precisely executed during transit as during combat. The convenience they provided in voyage management acted as more practice to ensure that critical time during tactical execution of a battle was optimized by enhanced communications. Ultimately, this resulted in forces remaining aligned with Nelson’s commander’s intent throughout, regardless of whether the tactical fight unfolded within sight of the flagship or beyond its field of view. Further, he wanted to ensure his signals were additive, not distractive, to his tactical commanders and therefore not disruptive to their tactical actions in support of his operational objectives. Because of the fog created by cannon fire and the drifting nature of battle at sea, especially during the age of sail, battles tended to disperse over time. This required Nelson’s flag signals to be repeated with precision by each ship, ensuring the highest probability that his signals would reach the farthest engaged vessel from his flagship as originally signaled.

This is why the characterization of Nelson’s last signal to his fleet prior to the Battle of Trafalgar is so telling. While historians debate many elements of the battle, including how it was joined, there is common agreement that Nelson’s signal came about through a discussion with his commanders the morning of the battle, hours before it began. Despite this face-to-face meeting, Nelson wanted to send one last message to ensure there was clear understanding of his expectation of his commanders. His message was simply, “England expects that every man will do his duty”—an affirmation that his commander’s intent was aligned with the strategic expectations of the country they served.^([4](#15_Chapter07.xhtml#fn4)) Interestingly, the only other flag hoist from Nelson’s flagship that day was a “what,” not a “how,” message: “Engage the enemy more closely.” It flew until it was shot away.

More relevant to the subject of this chapter is the question of whether new AI-enabled tools will help lift the fog of war, helping engaged units stay aligned with commander’s intent, or whether they will act simply as signposts and tactical aids. We believe the answer is a combination of both, where AI cannot just be a blind decision-making toolset but also needs to be much more helpful than, for example, an aviation kneeboard decision aid.

## **TRUST IS CRITICAL TO C2**

The second example we share is from our own Navy history and involves Adm. Chester W. Nimitz, whose portrait hangs above the desk he used as U.S. Pacific Fleet commander. That portrait serves as a regular inspirational reminder of how Admiral Nimitz embodied the elements of command and control, mission command, and commander’s intent as critical elements of his command of the fleet.

Behind Nimitz in the picture is a high-frequency radio. Stories are told of how he would follow the progress of major battles as they unfolded by listening to the transmissions made on the command nets of those executing the battle plan of either Adm. William Halsey or Adm. Raymond Spruance—a plan on which he had previously been briefed and had approved. We have not been able to find any authoritative source to confirm that he ever made a transmission on that radio during a major battle. Based on his applied theory of command and control, we assume he did not.

Once operational planning had been completed and commander’s intent was clear, Nimitz’s work was done. There was no way to know if he was receiving all the relevant transmissions. Without having the full context of what was happening at all levels of the battle, tactical and operational—context that could only come from being there in both time and location—inputs from Nimitz would have been, at best, distractive. Commanders must always consider whether they have the necessary grasp of the context of the fight to provide meaningful guidance. Both Nelson and Nimitz understood this.

In an article written for U. S. Naval Institute *Proceedings*, we noted the following in reference to the same radio: “We often recall that Nimitz sent Rear Admirals Raymond Spruance and Frank Jack Fletcher into battle at Midway, charging them to take ‘calculated risk’ to gain advantage over the numerous imperial Japanese forces. What we often forget is that Nimitz listened to the fight unfold from his headquarters. At moments, it seemed to be going badly. Nonetheless, he never transmitted on that \[high-frequency\] radio to the engaged commanders—a level of trust and discipline to which every commander should aspire.”^([5](#15_Chapter07.xhtml#fn5))

The key word here is *trust*. In a YouTube video of Gen. Colin Powell, USA (Ret.), speaking at an undetermined time or venue, an individual who identifies herself as a White House fellow asks him, “How do you define the key characteristics of effective leadership that would allow you to be an advocate for good?” General Powell’s response is immediate and a single word—trust.^([6](#15_Chapter07.xhtml#fn6)) His response forms the core of how we need to think of the nexus of AI and C2. Our sense is that we need to think of it as a tool, just as Nelson’s flags and Nimitz’s high-frequency radio were tools. As tools, they represent the *science* of warfare—a critical element that commanders must master if they are going to be successful in warfare, but not *the* critical element.

Equally important to the science of warfare, but much more difficult to master, is the *art* of warfare: what to do in the fog of war, how to command decisively where knowledge is fleeting, confusion is pervasive, and communication opportunities are episodic at best. These are questions whose answers are formed from commander’s intuition. Warfighting intuition, informed by mission intent, is about as close to control as a commander can hope for at the operational level and above.

It follows, then, that *how* artificial intelligence can help people bridge the science and art of warfare is key to understanding how it will be incorporated into the fleet. To that end, enabling transparency in the development and deployment of AI is key. To trust computer-assisted decisions, people need to understand how an AI system arrives at its recommendations. This includes at least a tacit understanding of the following kind of questions: What data set(s) is incorporated? Is it biased in any way? How are tactical decisions balancing human and materiel losses?

Currently, deep learning and big data algorithms do poorly in explaining how they arrive at their conclusions. But researchers at IBM believe “we will get to a point, likely within the next five years, when an AI system can better explain why it’s telling you to do what it’s recommending,”^([7](#15_Chapter07.xhtml#fn7)) meaning that the trust in the tools themselves needs to start now. This should include having commanders jointly involved with the development of AI-based decision aids, ensuring integrated technical and tactical development.

## **TENETS OF C2: AT THE TACTICAL, OPERATIONAL, AND STRATEGIC LEVEL**

For the purposes of this book, the following points offer a limited view of a few tenets of C2 that are particularly relevant to this discussion, some of which have been addressed earlier. The first is an understanding of the difference between time and tempo in the context of fighting at the tactical, operational, and strategic levels. Another is data collection and data management.

Time as referred to here is in two contexts. One is a *point in time*. As risks and opportunities present themselves at any given point in time, do you have the ability to minimize the risks or seize the opportunities before that moment in time either, in the case of risk, culminates in failure or, in the case of opportunity, slips away? The other context is time as a *commodity*—something to own, control, and invest. Do I own time, or does it own me? Am I in control of time, or is it beyond my control? Do I have excess time to invest in resupply, repair, planning, training, and other activities?

Tempo of warfighting is the rate at which the fight is being executed. As with time as a commodity, there are many factors that influence it—enemy actions, of course, but also your logistics, weather, communications, fatigue, and knowledge of your own force actions as well as those of the enemy. As a rule, the tempo of the fight is higher the further down echelons one operates. That is not to say that up-echelon operation is not intense, but in combat, the tempo is much more manageable at the higher echelons. What is interesting, and leads into the next point, is that tempo is exacerbated by the excess of information at the tactical level, the challenge being how to process and make sense of it all. To deal with that challenge, tactical commanders are left with the option to act faster based on what they know. Juxtapose that with the operational level, where commanders are faced with a dearth of knowledge but are experienced in acting fast and do so even though they lack the firsthand knowledge the tactical commander has to make informed “fast” decisions.

This brings us to data collection and management, clear elements for applying big data. As noted, lower echelons’ data collection is less of a problem. You tend to fight based on what you sense as well as on what you see and hear. The result is a situation in which it is not only a challenge to manage the data you are receiving, but also a significant distraction if you are directed to do so. As you move up echelon, data collection becomes a challenge. Sensors are not attached to you organically. They are mechanical or electrical or chemical. They are susceptible to being so efficient that the sheer volume of data they provide can be overwhelming. Here, managing data is much more of a requirement to make sense of what to do operationally.

Likewise, because data is collected and conveyed by human design, it is relatively easy to be interdicted by man. This is recognized today by how often we talk about the challenge of operating in communications-denied environments as if this was something new. In many ways, the reality is we are in a “back to the future” scenario. We have lost our previous communications-denied edge due to having fought in a comms-enabled and -dependent C2 structure facilitated by operating in a pervasive comms- and network-enabled environment for at least the last twenty years.

In fact, most of our challenges with communications have been of our own making, having lost the ability to manage our own electronic spectrums. Not only have we lost the skillset to embrace silence on the net, we also have designed our C2 and weapons systems to be comms-enabled (not a bad thing), but in doing so too often we have made them comms-dependent (not a good thing). These dependencies and inherent vulnerabilities of tactical, operational, and strategic grids of control and information flow need to be clearly understood, in both our own systems, to be managed and defended, and those of the enemy, to be exploited and attacked.

The first question any commander should ask of a weapons system that is network-enabled should be, “What happens when the net goes down?” followed by “What are the critical nodes that I own? What are the critical nodes that I don’t own? What is the strategy to defend them? What is the impact on my ability to fight if they are denied to my forces?” We need to be careful that “comms-denied” does not become “weapons-denied.” We also need to take great care not to repeat our missteps with ubiquitous communications—that AI-enabled systems do not become AI-dependent systems, so that when the artificial intelligence is rendered unreliable by enemy action, system casualty, or conscious choice, the human operators can still right the ship.

## **MATURATION OF INTELLIGENCE: DATA TO INFORMATION TO KNOWLEDGE**

Intelligence is a team sport. There are many players on the team, and key ones are obviously intelligence experts but also operators. The latter are not obvious players. This is highlighted by such statements as “intelligence is a product,” as if it were a deliverable to be provided to operators. An example often used is the 9/11 attack on the United States being referred to as an intelligence failure. It was not. It was an operational failure. The intelligence was there but was treated as “black swan” information by the intelligence community because there was a sense it would not be considered credible by the operational community. This perception was correct, as the assessments of a potential 9/11-type attack were not considered credible by the operators that were briefed.^([8](#15_Chapter07.xhtml#fn8))

It would have been much more difficult to dismiss these assessments if intelligence and operational expertise habitually worked together as a team. From our experience after 9/11, the convention of working together as a team has not been sufficiently developed with the exception of the special operations forces (SOF) community. Here, not only do members work together as a team, they live together as well, developing a true team mentality built on mutual respect and trust. There is a clear understanding within the SOF community that both operations and intelligence experts must act inclusively if they are to act decisively. When they are not working as one, combined discussions on where they are aligned—but more importantly, where their perspectives are not aligned—cannot occur in a timely way, if at all. Where they do not agree is where both the risk of failure and the opportunities for success lie.

The maturation of intelligence (data to information, information to knowledge) is important for members of both the intelligence and operational communities to understand. Operators often voice frustration with the value they get from the intelligence products. What is troubling is when this frustration transitions into blaming either the intelligence or operational communities. The problem is not “them,” it is “us.” Where we are not working together in the process to produce intelligence, we are working against meaningful intelligence production. A flaw with the current process is that most of those tasked with actions and activities leveraging AI-enabled tools are almost exclusively from the intelligence community. Here we are missing the opportunity to begin to blend the intelligence and operator communities together by including operators early in this process.

The maturation of intelligence products occurs in stages. The first stage is the gathering of data. Early in their respective career paths, operators and intelligence community members start by gathering data and categorizing it through the thoughtful and informed application of metadata protocols. As experience is gained, these first-stage data gathering and classification practitioners eventually transition to information managers. Adept at building and managing databases, they leverage their expertise and skills to look for correlation within the databases to derive information in the context of what has happened, what is happening, and, if they’re really talented, why it might be happening.

Unfortunately, this is often where the cycle of intelligence maturation ends. To most operators, this information is critical to the mission sets they are tasked to execute. This makes sense, as most task-to-action occurs at the tactical level. Unfortunately, stopping the intelligence maturation process here does not serve us well at the operational or strategic level.

A large part of the issue is the reality that operators at the operational and strategic levels still think in terms of their experience at the tactical level. Too often they default to the role of crisis managers and ask the tactical of crisis operators: “What has happened? What are the current conditions? Who is involved?” This is a key reason it is so rare to find individually (and even more rarely, organizationally) talented knowledge developers.

There are few who are truly gifted knowledge developers at the operational and strategic levels. Words, definitions, and titles are important. Referring to them as directors of intelligence and information operations helps tie naming conventions and position descriptions with task terms. The task involves moving beyond providing the commanders and their staffs with information to providing them with knowledge of what is happening. This is the work of experienced intelligence and operations experts, experience developed through working closely together throughout their careers. The skills needed to develop such knowledge products move beyond the binary, science-based process of delivering information on what has happened, what is happening, and who is acting, to what is going to happen, who is going to take such action, how best to deter it, and, if deterrence fails, how best to defeat the action.

This is difficult work. It takes a deep understanding of the intelligence development process and how operators can best act to counter the risk. While data gathering and information management are largely science-based processes, knowledge development is an art. It is not a process of comparing ones and zeroes, black and white, yes and no, right and wrong. It is subjective—in the realm of probability, of experience-based deduction and subjective analysis. It is a hunch proven out by directing the commander at Midway to send a message saying he was running low on fresh water to confirm the next major objective of the Japanese Imperial Navy in the Pacific.^([9](#15_Chapter07.xhtml#fn9))

It is critical to stress this last point about the importance of the science and art, and the difference between the two, as we explore what we need to consider in applying artificial intelligence to command and control. As mentioned, the science of warfare is not about binary criteria. It is about getting the answers tactical operators require to develop plans for actions they need to take in a given moment in time. The art of warfare depends on the science of warfare, but more important than seeking answers, it is really about seeking the right questions by first correctly framing the problem.

Early in the planning and execution process, before sufficient knowledge has been developed to define a problem, operational and strategic commanders should be comfortable responding to questions from staffs and subordinate commanders about what to do with answers such as, “I don’t know.” “What do you think?” “Have we seen this before?” “What do we know?” “What don’t we know?” “How old is the information we have?” “What is its source?” “What is its half-life?” and most critical, “Are the assumptions we developed to fill planning information gaps born of knowledge and insight, or comfort and convenience?”

## **A WAY AHEAD**

It is simply too soon to draw conclusions on how best to apply AI to C2; we lack the depth of knowledge to do so yet. As we explore how to apply AI to C2, we should characterize that process as a learning one. We have a great deal of data and information, but not very much knowledge about how, or even what, to apply. That is the core value of this book.

The road to incorporating big data, artificial intelligence, and machine learning with the fleet should begin much as naval aviation did: with selected officers and civilian technologists carefully watching the new technology develop, and beginning its incorporation into limited roles as merited by engineering advances. These should be demonstrated regularly in fleet limited objective experiments, with the control being existing systems pairing off against AI-supported ones. Wargaming should take place at both the Naval War College and the Naval Postgraduate School, where complementary focuses on strategy and tactics can be juxtaposed with advanced technical rigor. Strike group work-ups should begin incorporating machine learning and big data–supported decision aids and tools as soon as practicable, starting with areas such as maintenance and logistics and growing into more tactically relevant ones, such as intelligence, over time.

Given the software-intensive nature of the kind of tools we are discussing here, it follows that they can readily be changed, adapted, and improved more easily than many traditional naval systems. As such, pairing skilled developers with operational forces, at least in peacetime (and especially in wartime), should be a core tenet of how these systems are developed. This means iterative development cycles, integrated technical and tactical development, early fleet/user buy-in and feedback, and the ability for operators to adapt the tools themselves based on what’s helpful and what isn’t. We must allow for rapid experimentation and be willing to accept risk in doing so.

We have set the stage for what needs to be a robust and ongoing discussion on the application of AI tools to command and control. We have done so hoping to ensure those discussions are thoughtful in the manner in which we explore how best to pursue exploring AI to C2 options, practices, and processes. We have tried to lay out the background context for the following key takeaways:

•  From the discussion on the importance and difficulty of fighting through the fog of war, and how a flawed failure review process can obscure critical learning points, we have to ask ourselves the question, “How well do we understand the problem we are trying to fix?” We should remind ourselves often in exploring the application of AI to C2 that before we can apply relevant and meaningful solutions, we need to make sure we fully understand what we are trying to fix.

•  AI should be applied to enhance and must not diminish Nelson’s principles: “Seek knowledge, advice and counsel of subordinates,” “Spend more time listening than talking,” and “Seek face-to-face exchanges.”

•  AI should enhance the precision and synchronization of signals in a modern context and must not diminish or exacerbate them.

•  AI should be considered a tool to use—a means to an end, not an end in and of itself.

•  AI should be applied to allow a commander to better own time as both a “point” and a “commodity.” It should do the same with respect to the tempo of the fight.

•  We should be informed by a discussion of the vulnerabilities a commander faces if comms-denied also becomes weapons-denied—that is, when high-technology weapons cannot use their full electromagnetic-enabled targeting capabilities in a contested electronic warfare domain. How do we ensure that AI as a C2 enabler does not become a commander’s disabler?

•  An immediate focus of AI should be in the area of maturation of intelligence. It has great potential to speed up the process of data management while at the same time increasing the precision of data characterization, expanding the scope and scale of data management, and allowing faster access to relevant data key to informing problem definition. Doing so will improve the veracity of the translation of data into information and, in doing so, will increase the rigor and validity of the predictive analysis, what will happen, and who will be responsible and why, that is key to the development of a commander’s knowledge on which to base intent and decisions.

•  AI should enhance a commander’s intuition. It must not replace it. It is critical to remember commander’s intuition is inherently subjective.

We must guard against making an assumption that AI is intuitive until clearly proven otherwise. We put at risk a commander’s ability to command and control forces by mistaking the ability of AI to speed up the application of algorithms for intuition. Making deductive assumptions based on repeated outcomes to divergent inputs remains a science-based capability/process. It does not represent the art of a commander’s intuition applied in the form of commander’s intent. AI, for now, needs to remain a tool to assist a commander’s decision-making process, not replace it. To this end, AI products and processes need to be contained within our current staff process, informing but not providing the options from which commanders decide which actions they take.

Here, with the application of AI to command and control, it is useful to remind ourselves that often, “slow is fast.” Our approach to the application of AI to command and control needs to be assertive, thoughtful, and measured, informed by modeling, experimentation, exercises, and wargaming, all tied together through robust critiques, analysis, and assessments. This requires time and thoughtful and patient study. The approach, therefore, can be thought of as assertive in the steady, measured active pursuit of thoughtful consideration of what are we trying to fix, progress measured with both predetermined and ad hoc performance metrics derived from modeling, experimentation, exercises, and wargaming, tied together through robust critiques and assessment.

Finally, AI has to enhance *trust*, the most critical element of any C2 system and process, and must not diminish it. Even if you create the finest AI-enabled decision tool, if its users do not trust it for any of a host of possible reasons, all you have done is muddied the decision-making process for our military forces and made a poor investment of both financial resources and intellectual capital.

### **NOTES**

# 8

Practical Applications of Naval AI

**An Overview of Artificial Intelligence in Naval Warfare**

CONNOR S. McLEMORE AND CHARLES R. CLARK

The wars of the future will not be fought on the battlefield or at sea. They will be fought in space, or possibly on top of a very tall mountain. In either case, most of the actual fighting will be done by small robots. And as you go forth today, remember always your duty is clear: to build and maintain those robots.

—*The Simpsons*^([1](#16_Chapter08.xhtml#rfn8_1))

**Naval artificial intelligence (AI)** applications will transform how sea services man, train, equip, and employ naval forces. While human cognition limits the maximum speed and complexity of some naval tasks, AI can now execute many of them, including combat tasks, without regard to human limits. AI can often perform those tasks faster, better, and cheaper than humans.

Contrary to the certainty of *The Simpsons*, it is unclear whether the preponderance of fighting in future wars will take place at sea, in space, or on the top of a very tall mountain; regardless, the fighting will involve AI. All naval personnel will interact with AI systems to some extent—some will have the duty to maintain them, while others will need to train them and be accountable for their actions.

When AI performs tasks, its actions and decisions may not be understandable to humans. However, slowing or simplifying AI so that it becomes understandable may also hamper its performance. Sailors fighting with slowed or simplified AI, which we henceforth refer to as “restrained AI,” could be put at a disadvantage, especially when facing opponents using unrestrained AI. For future multidomain naval combat, the belligerent best able to leverage unrestrained AI to quickly generate the appropriate military effects necessary to win—that is, the side best able to attack effectively first—will need to allow AI to take actions that are too fast for humans to follow in real time.^([2](#16_Chapter08.xhtml#rfn8_2))

AI applications themselves are not weapons. According to Michael Horowitz, AI is an enabling technology “that is more like electricity or the combustion engine than a weapon system.”^([3](#16_Chapter08.xhtml#rfn8_3)) AI already enables robotic ship, aircraft, and submarine prototypes to navigate without sailors; no substantial technical limitations are preventing those prototypes from also being enabled to kill autonomously without human oversight.^([4](#16_Chapter08.xhtml#rfn8_4)) However, significant technical hurdles remain before such systems can be trusted to always perform as desired. Therefore, imperfect AI remains a persistent danger to its users as well as its opponents.

Completely trustworthy autonomous combat systems do not exist and may not be achievable. At what point does the pursuit of “perfect AI” become the enemy of “good enough AI”? Automobile companies face a similar question in their pursuit of the first completely trustworthy, fully autonomous vehicle. As of 2019 problems with existing systems persisted, and incidents of drivers who crashed because they were not prepared to take control of their imperfect “autonomous” vehicles still occur.

While control by a moral agent is necessary for accountability in military combat systems, how humans will control imperfect, opaque automated systems acting at speeds faster than human comprehension allows is unclear. Such automation may make humans more robotic instead of making automation more human. In cases where humans are shown to make worse decisions than machines consistently, why are humans still allowed to make those decisions? In the future, decision-makers may be forced, or even eager, to cede important military decisions to unrestrained AI, including those potentially resulting in human casualties. Naval leadership should be concerned about these issues and thinking about the roles humans and machines will play in AI-enabled navies, including how to ensure AI will be used responsibly by all sides.

## **AUTOMATION, NOT THOUGHT**

The term “artificial intelligence” is misleading. The word “intelligence” in AI refers to the ability of algorithms to emulate human intelligence, not the ability of a machine to be intelligent. Arguably, the term AI describes a human emotional response to new automation and is not a description of how that automation works. The most impressive AI addressing the most difficult challenges cannot be easily categorized by algorithmic technique because it commonly involves combinations of techniques. What is and is not considered AI is always evolving and should be principally judged by whether a machine is doing something that, until recently, could only be done by human intelligence or couldn’t be done at all. Tasks first performed by machines long ago (e.g., automatic telephone switchboards) are *always* considered mere automation, while machines performing new magic tricks are both AI *and* automation. The automation called AI today—for example, autonomous vehicles, computer vision, natural language processing—will someday be considered unremarkable and will then no longer be thought of as AI.^([5](#16_Chapter08.xhtml#rfn8_5))

An example of this phenomenon occurred with IBM’s Deep Blue chess-playing computer system, which was the first automated computer system to defeat a human chess world champion under regular time controls. In 1997 Deep Blue defeated the chess master Garry Kasparov. There are several features of chess that make it “ideal” to address with AI: the state space, while large, is finite; the game has perfect information; the rules are stationary; and there is only one objective. At the time, IBM heavily publicized the feat to showcase its leadership in AI.^([6](#16_Chapter08.xhtml#rfn8_6)) However, if Deep Blue performed that same feat today, it would not be considered AI because machines capable of defeating chess masters—and masters of other complex games—are now common-place.^([7](#16_Chapter08.xhtml#rfn8_7))

To understand the naval applications of AI that will be most useful, the capabilities and limitations of AI need to be understood. Perhaps the principal limitation of AI is that *it cannot think*, although some AI gives the appearance of doing so. Humans learn to think over a lifetime by developing, updating, and making connections between diverse and flexible mental models, and humans generally know which models to employ for a given situation.

In contrast to human intelligence, all AI systems are “narrow” in that they are limited when conducting tasks beyond their designed purpose; for example, AI applications built to win at poker are not useful for driving a Tesla. AI is unable to put new experience, knowledge, and skills into context without human assistance.^([8](#16_Chapter08.xhtml#rfn8_8)) As noted in both the introduction and chapter 1, thinking AI, or artificial general intelligence, does not exist. Similar to the path from nuclear fission to cold fusion, the path from narrow AI to artificial general intelligence might be right around the corner or might not exist at all (we are not as sanguine about its eventual development as are the authors of chapter 1). Some think the nonexistence of thinking AI is not a limitation but rather a beneficial feature. Artificial general intelligence could be extraordinarily dangerous according to high-profile thought leaders such as Bill Gates, Stephen Hawking, and Elon Musk, and as depicted in a considerable share of sciencefiction canon such as *The Matrix, 2001: A Space Odyssey, Battlestar Galactica, Ex Machina, WarGames*, and, of course, *The Terminator*.^([9](#16_Chapter08.xhtml#rfn8_9))

AI doesn’t need to be able to think to be useful. Most military tasks only require AI to be trained and to learn, an activity at which AI already excels. As naval tasks become increasingly automated, AI will reset the playing field by turning above- and below-average–performing sailors into average performers by displacing or augmenting human strengths and weaknesses.^([10](#16_Chapter08.xhtml#rfn8_10)) For example, the mission of submarine hunting requires personnel with long attention spans. Sailors with short attention spans generally perform the mission poorly. Constant vigilance is necessary for hours at a time while listening to sonar or visually searching swaths of the ocean for periscopes. AI doesn’t suffer from a limited attention span and has proven particularly efficient at recognizing visual and audio patterns. Submarine hunters augmented with AI would neither benefit from long attention spans nor be disadvantaged by short ones.

One human attribute that AI will not soon displace is critical thinking. Sailors will have difficulty distinguishing themselves from other sailors as automation surpasses other human attributes; this is likely to result in a shift in organizational preference toward personnel with critical thinking skills in competitive organizations and accelerate lurking anti-intellectual tendencies in uncompetitive ones. Many tasks that do not require critical thinking will become AI-enabled, even complex tasks that used to require highly trained specialists—for example, unmanned U. S. Navy aircraft can now land on aircraft carriers.^([11](#16_Chapter08.xhtml#rfn8_11)) However, many rote tasks will still require some level of human involvement. Sailors in ratings that do not require critical thinking can anticipate multitasking in jobs they have not done before where machines tell them what to do and how to do it. For these reasons, navies should start to prioritize the identification and promotion of critical thinking over specialized, rote human skills—and should start to reorganize accordingly. U.S. Navy ratings that require high levels of critical thinking should remain relevant while those that do not can be displaced with automation.

Due to AI’s inability to think, it typically performs poorly when applied to tasks with changing rules but often excels at tasks with fixed rules. AI may not deal well with even small changes to rules and patterns. For example, Uber found that its self-driving cars that trained to drive on data collected in sunny weather could not operate in the rain.^([12](#16_Chapter08.xhtml#rfn8_12)) To address such issues, Uber adds data collected from tests and human drivers to their training sets to enable their cars to learn how to react to these previously unseen circumstances that are not directly relatable to their current “knowledge.”

AI’s lack of flexibility should be a principal concern to military decision-makers because, in many military situations, opponents have the motive and opportunity to disrupt rules and patterns. For this reason, military decision-makers should always think in terms of applying AI when rules and patterns are fixed or predictable and opponents cannot disrupt them. For example, military organizations can only control changes in their own operating patterns and disguise, not the unpredictable changes of their opponents. Therefore, developing reliable AI that can automatically characterize an opponent’s systems or actions directly based on rules and patterns is impossible. However, if friendly patterns are known and neutral patterns are expected to be predictable, AI could be used to automatically identify friendly and neutral forces and therefore could also be used to identify opponents by exception.

## **FOCUS ON DATA FIRST**

Automated pattern recognition is a rapidly expanding subset of AI. Machine learning and deep learning techniques allow predictions to be automated based on patterns in data, making computer vision and natural language processing possible. Pattern recognition algorithms are useful for rapidly conducting comprehensive pattern searches in large data sets and are principally judged by their predictive power, although other criteria, such as their speed and deployability (the capability to be rapidly implemented), may also be important.^([13](#16_Chapter08.xhtml#rfn8_13)) The complexity of the patterns composing fundamental naval tasks once had to be simple enough not to exceed human cognitive decoding ability. Automated pattern recognition fundamentally changes this dynamic in two ways: deciphering patterns no longer requires humans, and human cognition doesn’t limit human understanding of complex patterns.

Automated pattern recognition is dependent on reliable sources of “fuel” in the form of the right types of clean data, which have had inaccurate records restored or removed. Putting incorrect or dirty data in a pattern recognition algorithm becomes a lot like putting incorrect or dirty fuel in an aircraft—neither should then be relied upon to perform adequately. Therefore, any discussion about the potential implementation of any AI, and pattern recognition AI especially, should begin with a discussion of available data sources. Questions about data sources should include who owns the data, whether the data are the right types and quality, whether enough data exist, how expensive the data are, whether the data are clean or can be cleaned, where the databases are, and how the data sets will be accessed.^([14](#16_Chapter08.xhtml#rfn8_14)) If satisfactory answers to these questions do not exist, implementing an AI solution may not be worthwhile.

Senior naval leadership is recognizing the need for better access to clean data. Vice Chief of Naval Operations Adm. Bill Moran stated, “We need to move quickly to intentional, authoritative, high-quality data that is securely captured, stored, shared, and integrated across the Navy. We have to curate and rationalize the countless disparate databases and outdated technology which leaves us unable to ‘see’ and make use of basic information.”^([15](#16_Chapter08.xhtml#rfn8_15)) For navies to capture, store, share, and integrate clean data will require naval units to have reliable and secure access to databases and greater numbers of data-literate personnel. Improved database technology will take time and money. However, data curating can become a basic enlisted skill across most ratings now, and navies should start adjusting their training and education paths to support such efforts. With data collection, cleaning, and training preparation commonly taking the most time when deploying AI, data-literate personnel supported by sound and transparent data plans can save time and money.

Navies should focus on developing new business rules for future databases. First, they should stop storing data in systems requiring the use of proprietary software to access and should move data exclusively to open-standard, crossplatform compatible databases. Second, all of their data should be stored in a common schema with a built-in audit trail and provenance, to identify authoritative data straightforwardly. Third, data should be structured to capture interdependencies within and between data sets. Fourth, navies should always retain ownership of their data and any analysis generated from them.^([16](#16_Chapter08.xhtml#rfn8_16)) Those that do not do so will be at risk of data loss when switching vendors.

A serious limitation to employing AI in a naval context is the lack of “Internet-like” connected, open-standard, secure, long-range data communication paths at sea. If enough of the right clean AI fuel can be made available in accessible databases, a navy’s next steps are to identify the communications paths to access that fuel and design interfaces to quickly communicate AI-developed directions and recommendations to human and machine actors. Most U.S. Navy communications systems and data links are essentially distinct “walled gardens” where each has its own proprietary data formats and applications. They can’t talk directly to each other without human translators. Data are still mostly passed manually via unconnected, low-bandwidth means such as chat or voice.

The lack of a reliable Internet-like communications system at sea is likely to remain the single largest limitation to the rapid adoption of naval AI for the foreseeable future. However, if naval systems can be connected and open, nonproprietary protocols can be established, then AI can be used by navies to enable extremely low-bandwidth communications. AI-enabled sensor systems could refine terabytes of mostly useless naval data into kilobytes of valuable information. Those tiny bytes of information could then be transmitted efficiently through connected, low-bandwidth communications systems. For example, real-time streaming videos from sensor aircraft require high-bandwidth communications systems to transmit terabytes of data to intelligence cells for analysis—for example, according to *The Economist*, each operating Global Hawk drone now uses more than five hundred megabits per second of satellite bandwidth.^([17](#16_Chapter08.xhtml#rfn8_17)) AI software at the sensor could extract valuable information to be transmitted directly to interested parties via low-bandwidth means. Naval forces should abandon unconnected, proprietary communications systems and focus on acquiring connected, open protocol communications systems, even at the expense of bandwidth.

The Department of Defense (DoD) already uses its data to train AI to perform automated pattern recognition, and it is showing enormous military potential. Project Maven, the collaborative effort between Google and DoD discussed in previous chapters, developed automated pattern recognition algorithms to sort and categorize images in full-motion video at speeds that would be impossible for humans. Instead of it being necessary to send streaming video from distributed sensors to an intelligence cell for human analysis, Maven instantly parameterizes data in streaming video without any human involvement. However, Maven began generating controversy when it became apparent that nothing prevents Maven’s data from being directly fed to targeting systems. After four thousand Google employees signed a petition objecting to Maven, Google announced in 2018 that it would not renew the Maven contract.^([18](#16_Chapter08.xhtml#rfn8_18)) What is it about the idea of completely removing humans from military targeting cycles that has people worried?

## **BUILDING TRUST IN AI THROUGH ACCOUNTABILITY**

AI cannot be accountable for its actions when it faces moral decisions and, therefore, is not a moral agent. AI ethics can be programmed, but AI cannot sin, tell right from wrong, experience moral injury, or suffer.^([19](#16_Chapter08.xhtml#rfn8_19)) AI-enabled combat systems that can act far away from human oversight in location and time, and thus can operate outside of human control, could be controversial; such systems can shield humans from accountability when used irresponsibly.

Weapons systems acting outside of human control are not a new problem. Naval mines and landmines are similar to AI in that they can be designed to be untraceable. When mines are used irresponsibly, establishing accountability is often difficult. Those humans responsible for the landmines scattered throughout countries such as Cambodia, Angola, and Afghanistan will probably never be held to account for the suffering those weapons continue to cause, stoking public fear and outrage and calls for global bans.^([20](#16_Chapter08.xhtml#rfn8_20)) Military AI used irresponsibly should be expected to generate similar public backlash for comparable reasons.

A public backlash could lead to severe restrictions on the use of military AI. Navies should implement strong measures to ensure unambiguous human accountability over each of their automated systems through a person on/in the loop, particularly for any system that could involve human harm or infrastructure damage. Such measures are already in place for U.S. landmines. For example, landmines placed in clearly marked and tightly monitored minefields near the no-man’s-land of the thirty-eighth parallel between North and South Korea are unlikely to result in indiscriminate deaths. However, if those mines did kill the wrong people, the humans in charge of those minefields can be straightforwardly identified and held to account.

Another reason to put a person on/in the loop of an automated system is to improve AI system performance. However, simply designating a human to be on/in the loop will guarantee neither improved performance nor accountability. As AI continues to improve, humans in human-machine teams should focus on maintaining clear accountability for the use of AI, providing AI with operating boundaries, and being available for decisions involving critical thinking.

Putting a person on/in the loop the right way can improve an AI system’s impact and efficiency. Doing it the wrong way can negatively affect a system’s impact and make it less efficient. As previously discussed, humans and machines are good at different things. While control and accountability may need to come at the expense of speed and quality, having machines do things humans should be responsible for, and vice versa, can ruin otherwise well-designed AI systems. In general, humans are best at tasks requiring flexible thought, while machines are best at tasks that are predictable and repeatable and that involve structured complexity. Humans and machines working together are typically best for tasks requiring both.

The U.S. Navy has not traditionally put its people in positions of great responsibility without providing them opportunities to acquire the training and knowledge necessary to understand the systems for which they are responsible. Preparing Sailors to employ unrestrained AI-enabled systems should be handled no differently. Expecting an untrained Sailor placed on/in the loop of an automated combat system to be accountable for its actions would be illogical. Human accountability should be established over AI-enabled combat systems the same way it is for any complex and dangerous system: rigorous training resulting in expertise allowing for safe, responsible system operation coupled with policy delineating authority and accountability. Additionally, a transparent and thorough system will need to be in place for when things go wrong with military AI to find out where failures occurred, to implement corrective actions, and to hold the right people accountable to maintain the public trust.

A military example of poorly trained humans on the loop failing to stop complex, highly automated systems from mistakenly killing humans occurred in 2003 at the start of the Iraq war. The U.S. Army was operating its Patriot air defense batteries in automated mode, allowing missiles to fire without any human interaction. Two British flyers and one U.S. aviator were killed when inadequately trained and led U.S. Army personnel in two separate Patriot batteries allowed their systems to shoot down a Royal Air Force Tornado GR4 and a Navy F/A-18C Hornet within a week and a half, despite the fact that the Iraqi air force was not flying at the time.^([21](#16_Chapter08.xhtml#rfn8_21)) Additionally, the day after the first shootdown, a U.S. Air Force F-16 *Falcon* managed to avoid destruction only by disabling a Patriot’s radar with a missile after being targeted.^([22](#16_Chapter08.xhtml#rfn8_22)) After the second fratricide incident, leadership directed that Patriot batteries switch engagement modes to manual. The systems were still highly automated, but a human operator was required to give the order to fire before a missile could launch. After this change, fratricide incidents by Patriot batteries ceased.^([23](#16_Chapter08.xhtml#rfn8_23)) However, it is unclear if this policy change would have been possible had the Iraqi air force posed a greater threat.

## **REALITIES OF NAVAL APPLICATIONS OF AI**

Navies will gain many practical benefits by correctly implementing AI. However, additional concerns exist beyond the general capabilities and limitations of AI and the establishment of accountability in AI-enabled naval combat systems. These considerations include vulnerability to deception, knowing right from wrong, and the value of data as a function of uncertainty.

## Naval AI Remains Vulnerable to Deception

As discussed in more detail in chapter 12, variations that do not fit the patterns in the data used to train a pattern recognition AI can mislead that AI. For example, something as simple as a yellow sticky note placed on a stop sign may break up a sign’s pattern enough to fool a self-driving car’s AI into thinking there is no stop sign.^([24](#16_Chapter08.xhtml#rfn8_24)) Navies should start to formulate plans to change patterns unpredictably to deceive opposing AI. If an opponent is visually classifying ships using an AI-enabled sensor system, ships with distinctive structural alterations or unique paint jobs might be able to defeat such a system.

Another way to fool an opponent that is reliant on automated pattern recognition would be to train their pattern recognition systems incorrectly over time. If yellow sticky notes were placed on *all* stop signs while the AI applications are learning, and then they were *all* taken off at the same time, AI-enabled cars might be unable to recognize stop signs. This parallels the signal deception plans utilizing electronic wartime reserve modes attributed to the Soviet armed forces during the Cold War.^([25](#16_Chapter08.xhtml#rfn8_25)) Training an opponent’s pattern recognition AI by consistently conducting naval operations with similar formations, communications, and emissions might be possible. Changing those patterns would then hamper the ability of an opponent’s AI to use things learned previously. The key to this deception would be to provide a believable and continuous ruse. If a ruse is not believable, an AI system properly monitored by humans can be corrected or biased away from the ruse.

Just as the U.S. Navy will eventually have plans to deceive opposing AI, so will its opponents. As naval systems and processes integrate AI, this fact should remain at the forefront of the minds of both developers and customers. Decision-makers must know the potential vulnerabilities and imperfections of the AI-enabled systems they are acquiring. For example, the filters that sort spam out of inboxes of even the best commercial email systems are known to have false positives and false negatives. Safeguards must be put into place so as not to draw the wrong conclusions in wartime based on opponents’ peacetime operating patterns. These safeguards may be as simple as flagged reports for human analysis or as advanced as experimenting with a constructed enemy AI to train on simulated potential variances.

AI should never be considered a source of truth because all AI is imperfect, even when opponents are not attempting to deceive it. Military operators must have a strong understanding of the flaws of their AI for this reason. However, many AI-enabled systems are still useful despite their imperfections. Many of the techniques in AI rely on statistical processes and limited data sets and, as such, have underlying probabilities that they are correct. For example, an AI that can identify a ship in a satellite image as an opponent’s destroyer may be correct most of the time. However, a chance exists that the AI gets it wrong; pattern recognition algorithms are evaluating things they have never exactly seen before.

## Naval AI Does Not Know Right from Wrong

How long does a child take to understand right from wrong? Even after learning simple things (for example, that hitting another child is wrong), time and experience are needed to inculcate those lessons and interpolate or extrapolate them to new experiences. Unlike a child, narrow AI is not flexible enough to apply the lessons it learns to new experiences. However, programming AI with proactive rules can minimize the probability that it takes an action considered wrong within a designed operating context.

Even without knowing right from wrong, a comprehensively designed, well-trained, and exhaustively tested AI-enabled weapons system should be able to do some things reliably. The tested level of AI and the mission parameters certified as capable for AI systems should be the responsibility of expertly trained naval operators, not the vendors who build AI-enabled systems. Operators in positions of public trust should be responsible for properly scoping AI and informing safeguards to prevent unforeseen circumstances from resulting in AI taking undesirable actions. Navies will need to ensure they have expert operators trained in the fundamentals of AI to guarantee that the development and deployment of AI are thoughtful, well-scoped, flexible, and appropriate with regard to policy and expectations.

Untrained and untested AI-enabled systems put into scenarios will perform solely on the preset decisions of their designers and operators, with potentially catastrophic results. Adequately training AI-enabled systems’ operators well enough to know when their systems may be going into situations they have not trained on or been tested for will be essential. For example, a robotic surface vessel that is well trained to reliably transit in autonomous mode open ocean but not a narrow strait may put itself and other ships in extremis if sailed into such a strait.

Narrow AI will be left to take action based only on limited rule sets provided by its designers and trainers. Therefore, as navies investigate mishaps involving AI, regulations and the ideas of right and wrong they represent may be secondary to determining what went wrong. Questions to be answered in a mishap involving AI will be of this type: “Was the appropriate AI used?” “Was the AI employed correctly under appropriate circumstances?” and “Did the AI take unexpected actions under the circumstances?”

These questions are not intended to provide means to avoid accountability but instead will have to be taken into consideration to apply accountability at the right level and to the right entities. An operator might have chosen to employ an AI capability outside of the validated tactics, techniques, and procedures, or a commander used AI that was not appropriate due to misunderstanding, or a design flaw went undiscovered during testing. In any case, the factors that caused the mishap can be determined to establish appropriate human accountability to reinforce the trust of the public.

## The Value of Naval Data Is a Function of Uncertainty

More data are not always better; tiny amounts of the right types of data are often more valuable than vast quantities of the wrong types. When a lot of uncertainty surrounds a question, a little of the right data can clear it up, even when those data are difficult to acquire. Because naval decision-makers often deal with highly uncertain situations, they may need less data than they think. Some navies spend enormous effort in collecting terabytes of mostly worthless data—data that is collected because it is easy to measure and accumulate, not because it contains valuable information.

For some questions, large data sets may be useful if they are easy to acquire and maintain through efficient databases. For example, in naval aviation, the helicopter communities employ the Integrated Mechanical Diagnostics Health and Usage Management System.^([26](#16_Chapter08.xhtml#rfn8_26)) This system uses data pulled from accelerometers to measure different performance aspects of the aircraft and its internal systems. The system allows for analysis and potential part failure predictions. Systems such as these are prime candidates for getting unanticipated insights at low cost through the application of AI techniques.

For other questions, getting the right data cheaply and easily is not possible. For example, to get data on missile performance, large amounts of cheap data probably cannot substitute for small amounts of costly live-fire data. When data are expensive, a balance exists between uncertainties reduced by additional data versus the cost of the data. Particularly in the early stages of testing new complex systems, the cost for data and the level of uncertainty can be high. A handful of data from a few well-designed tests that substantially reduce the uncertainty surrounding a system’s performance could be far more valuable than terabytes of data that cannot.

Knowing if navies are collecting what they think they are, if it is what they need, and if other data need to be collected is difficult without robust and adequately supervised data collection systems in place. Without thoughtful consideration of the costs to acquire data relative to the value of the uncertainty to be dispelled, data may not be very useful. To properly implement AI solutions, navies will need accompanying data collection plans that include the resources to collect and evaluate additional data and to evolve as data requirements change.

## **NAVAL TASKS TO AUTOMATE NEXT**

Given the realities identified, the types of tasks the U.S. Navy should focus on utilizing AI for automating include planning and scheduling processes, detecting patterns of interest in images, sounds, and electronic signals, command and control (C2) decision processes at the tactical and operational levels, and autonomously operating platforms and weapons.

Many rote and repetitive planning and scheduling tasks in the U. S. Navy are still done manually and could be done by automation better and faster. Some examples of naval planning and scheduling tasks that would benefit from automation include flight, range, and training pipeline scheduling; predictive aircraft and ship maintenance; dynamic communications and electronic warfare; and passenger and cargo movement plans.^([27](#16_Chapter08.xhtml#rfn8_27))

Being able to better detect patterns of interest in images, sounds, and electronic signals could have great utility for the U.S. Navy. Tasks that could benefit include airborne early warning, combat identification, submarine hunting, electronic suppression, deception operations, collision avoidance, and battle damage assessments.

Delays in tactical- and operational-level C2 decision-making can cause missed opportunities for effective attack and defense of naval systems. C2 decision processes that could benefit from automation include real-time distributed shipboard weapon pairings to threats, strike weapon–target pairing, and coordinating swarming systems to identify moving contacts efficiently.

Developing autonomous ships, aircraft, and submarines will provide the U.S. Navy with extraordinary capabilities and engineering challenges. Robotic systems will be able to perform many combat tasks better than humans. However, governments may not respond to the loss of manned platforms in the same way they would autonomous ones. Militaries may be willing to shoot opponents’ robotic systems, even very expensive ones, far more readily than they would manned systems because human life is not at risk.^([28](#16_Chapter08.xhtml#rfn8_28)) Unmanned systems operated near threat envelopes should either be attritable (destroyable by the enemy without grave consequences) or effectively defended. Optionally manning nonattritable autonomous platforms may produce enough uncertainty regarding the presence of humans to politically deter adversaries and could be an effective method of defense. However, other defenses for nonattritable autonomous systems, e.g., stealth or the ability to semi-submerge, may be cost-prohibitive.

## **CONCLUSION**

The term AI describes a human emotional response to new automation and is not a description of how that automation works. While all AI is automation, not all automation is AI. AI cannot think, but it does not need to be able to think to be useful. Properly implemented unrestrained naval AI applications will enable increasingly faster C2, communications, and decision processes while disrupting and deceiving opponents’ processes.

However, navies will remain limited by several factors in their implementation efforts, including a lack of clean, reliable databases and connected, reliable, secure Internet-like communication paths at sea. Naval leadership should always keep in mind that AI is vulnerable to deception, does not know right from wrong, and may perform poorly when applied to tasks with changing or unpredictable underlying rules. If used irresponsibly, AI may result in a loss of public confidence, and a resultant backlash could lead to severe restrictions on military AI. Sailors will require substantial training to maintain control over imperfect, opaque, robotic systems acting at speeds faster than human comprehension allows. Navies should start to prepare to implement strong measures to ensure unambiguous *human* accountability over each of their automated systems. AI’s limitations will not be easy for navies to overcome. Success will require infrastructure investment, appropriate policy, and an understanding of AI’s strengths and weaknesses.

AI’s reliance on data will be a driving factor in implementation. Navies must develop processes to collect, store, and curate data sets that may be expensive or difficult to collect. Additionally, for systems deployed at sea, a reliable, connected, Internet-like communications system remains the greatest limitation to rapid naval AI adoption.

Despite AI’s limitations, it will deliver extraordinary advantages in naval combat. For example, unrestrained AI can quickly generate complex combinations of military effects faster than humans can follow and can allow navies to communicate effectively by substantially reducing bandwidth requirements at sea by extracting valuable information from large data sets directly on sensor platforms.

Trained sailors placed on/in the loop of automated combat systems can be accountable for AI’s actions, but they might not improve system performance. Decision-makers could be willing to cede some important military decisions to unrestrained AI, including those that could result in human harm. However, AI will not soon displace the need for critical thinking. By properly playing to the strengths and taking advantage of the weaknesses of both human and artificial intelligence, navies can begin to position themselves for the future of AI-enabled combat—whether at sea, in space, or on tall mountains.

### **NOTES**

# 9

How AI Is Shaping Navy Intelligence, Surveillance, and Reconnaissance

MARK OWEN, KATIE RAINEY, AND RACHEL VOLNER

The digital era has profoundly changed our operating environment. Bulk data combined with modern analytics make the modern world transparent.

—Sir Alex Younger, chief of the Secret Intelligence Service (MI6)^([1](#17_Chapter09.xhtml#rfn9_1))

**According to Carl von Clausewitz**, the *nature* of war is enduring, but the *character* of warfare is shaped by its environment and is therefore ever-changing.^([2](#17_Chapter09.xhtml#rfn9_2)) In recent years, two pivotal trends—the return of great power competition and the rapid pace of technology development—have significantly altered the strategic environment, and thus also the character of warfare. Notably, future warfare is expected to be conducted with both a speed and level of complexity that far outpace current military operations. The Navy’s intelligence, surveillance, and reconnaissance (ISR) enterprise is modernizing to meet this challenge, and artificial intelligence (AI) will be crucial in this transformation.

The speed of war is increasing in part due to the advent of information warfare. Its component capabilities—cyber operations, electronic warfare, and space capabilities—all operate at the speed of electrons. However, the pace of kinetic warfare is also increasing, as evidenced by the development of ever-faster precision guided munitions, hypersonic vehicles, and scramjet engines. In this environment, windows of opportunity will likely be narrow, and the Navy’s ISR enterprise will be required to support rapid decisions and decision analysis. This requirement outstrips an unaided human operator’s ability to observe, orient, decide, and act (OODA). However, AI promises the ability to rapidly fuse and process ISR data, allowing intelligence analysts to generate conclusions and work with their systems to recommend courses of actions (COAs) at the speed of relevance.

At the same time, the complexity of warfare is also increasing. In the words of then-chairman of the joint chiefs of staff Gen. Joseph Dunford, “\[There’s a\] high likelihood that any future conflict will be transregional, multi-domain, and multifunctional. And this is a marked shift, in my perspective, from conflicts in the past.”^([3](#17_Chapter09.xhtml#rfn9_3)) The naval enterprise is changing course to meet the challenges of this new era, most notably through the development of new naval operating concepts. The fleet design construct and its subordinate distributed maritime operations concept now represent the major new thrust in the Navy’s warfighting thought. This conceptual direction envisions a construct in which “fleet-centric fighting power, enabled by integration, distribution and maneuver, allows simultaneous employment of synchronized kinetic and non-kinetic mission execution across multiple domains.”^([4](#17_Chapter09.xhtml#rfn9_4)) This planned level of coordination relies on the ability to swiftly and seamlessly distribute target-quality data among platforms in an “any sensor, any shooter” construct. Human operators alone will be unable to meet this challenge; the required advances will only be possible by integrating AI into the ISR function.

The Navy’s ISR enterprise is transforming with a focus on the ability to rapidly process ISR data to derive meaningful intelligence; fuse, integrate, and distribute this processed data across multiple sources, domains, and regions; and generate recommended courses of action within military-relevant timeframes. However, the contrast between this vision and current operations is, unfortunately, stark. The Navy’s tasking, collection, processing, exploitation, and dissemination (TCPED) process is still largely manual. Additionally, big data has overwhelmed networks, databases, and analysts with volumes of data that were not previously achievable. As the *Economist* recently reported, “In 2011 alone, the most recent year for which there are data, America’s 11,000-or-so drones sent back over 327,000 hours (37 years) of footage.”^([5](#17_Chapter09.xhtml#rfn9_5)) Currently, only a small percentage of collected data can be manually evaluated for intelligence by analysts in the naval community. Fortunately, though, this big data challenge contains the seeds of its own solution in that big data serves as the “fuel” for AI.

## **OVERVIEW OF THE ISR FUNCTION AND THE TCPED PROCESS**

Before describing how AI can enhance the ISR function, it’s necessary to first discuss what the ISR function itself encompasses. In short, ISR is the process by which the military detects, identifies, tracks, targets, engages, and assesses adversary forces in a continuous, high-operational-tempo loop to ensure all threats are accounted and planned for before, during, and after conflict. ISR is the primary means by which naval personnel extract pertinent information necessary to meet the commander’s intelligence requirements.

Parsing it further, *intelligence* provides warfighters the means to determine an adversary’s intent. With this information, a warfighter can perform COAs to counter and remove possible threats to the ship or other unit. *Surveillance* is the process of observing an activity of interest and determining if there has been a significant change that would require action. An example of this might be the observation that all naval maintenance vessels are out of port, which provides the commander the information that ships are being repaired out at sea. Finally, *reconnaissance* is the means by which naval forces acquire hard and soft data. Hard data is sensor data, such as a radar signal received via electronic intelligence or an image taken from an electro-optical sensor. Soft data is textual data, such as a written report or a naval message communicating new priorities to the commander. By acquiring both hard and soft data via reconnaissance systems and processes, the commander can take appropriate action. For example, if the seas become heavy due to an oncoming typhoon, the ship can be vectored elsewhere and safely continue its mission at a later time. The ISR function operates using the TCPED process shown in [figure 9-1](#17_Chapter09.xhtml#fig3).

The TCPED process of ISR systems is a block chain of actions that are used together to produce data products and information for the warfighter. The *tasking* portion of the process assigns platforms, sensors, people, or other assets to prepare to gather information at a specified time. For example, an unmanned aerial vehicle could be tasked to hover over a location and dwell its video camera for twenty minutes on a selected location, and then move on to the next task in its queue. The *collection* portion of the process performs sensing by any modality that has been chosen during tasking. For example, a photograph could be taken, an infrared image could be produced, chemical sensing could be performed on air samples, or radio frequency information could be collected by an electronic surveillance measurement system, among many other modalities from seabed to space. The *processing* portion of the process performs signal processing, data fusion, or other analytics to generate an information product. This information product could be a detected signal in the radio frequency spectrum, an image of a location on the earth, a sound velocity profile from the sea, or digital radio frequency memory recordings. These generated products are then sent to the *exploitation* processing function. Exploitation can be thought of as deriving intelligence from the reconnaissance and surveillance functions that have collected and processed the data. Exploitation is thus an attempt to generate “actionable” knowledge from categorized information in the form of an intelligence “product.” Once intelligence products are available, they are distributed to warfighters through networks and satellite communication networks via the *dissemination* process. These could be labeled imagery or video, geolocated signals on the earth, or underwater signals classifying types of whales, among many other intelligence products warfighters require to perform their mission.

![Figure 9-1. The TCPED Process with AI Extension](images/pg170_1.png)

**Figure 9-1**. The TCPED Process with AI Extension

ISR is a complex big data process that includes sensors (both soft and hard), people, platforms, networks, and weapons, and that also integrates all domains (undersea, surface, air, space, and cyberspace). Each of these complex big data environments involves a large envelope of processes and computing power along with the high-level reasoning of the human mind to assess each piece of ISR information and to make an overall determination for a course of action to execute.

## **AI ADVANCES HOLDING PROMISE FOR THE ISR FUNCTION**

As we discussed earlier, the big data inherent to the ISR function is both a challenge and a potential solution. It is a challenge in that the sheer volume of big data is overwhelming Navy analysts’ ability to keep pace with it. However, this big data problem that has transpired over decades of advances in platforms, sensors, and computers has also provided an opportunity for the Navy to reexamine and reevaluate AI tools for the automation of manual analyses.

AI and machine learning techniques are providing new innovative solutions to big data problems that were not feasible decades ago due to computing and processing power availability and limitations. Advances have already been seen in industry, academia, and government sectors. Google has shown that the tagging and labeling of big data can provide a rich training and evaluation set of data for extremely large machine learning techniques such as convolutional neural networks.^([6](#17_Chapter09.xhtml#rfn9_6)) In its 2012 paper on big data, Google demonstrated that it was able to have a “blind box” use thousands upon thousands of templates to learn to identify with extremely high accuracy all cats in images on the Internet. The blind box term describes a device utilizing “unlabeled” images or information, evoking the simile of toy figure series (such as Harry Potter characters, Marvel superheroes, or Lego minifigures) in which the exact character in the box is unknown prior to purchase. It is a self-learning system that does not need data curation.

With this industry proof of concept on an extremely large big data set, the AI community received a new shot in the arm and was brought to the forefront for the third time in its short history as a possible solution for critical war-fighting requirements.

Progress since then has continued to encourage the AI community. According to Stanford University’s annual index of AI progress, by 2015 algorithms surpassed human performance in image classification in lab-based tests.^([7](#17_Chapter09.xhtml#rfn9_7)) Moreover, between 2015 and 2018, algorithms nearly doubled their performance in object segmentation, a tougher task that involves picking out multiple objects from single images.

Currently, industry, academia, and government researchers around the world are working on utilizing AI to solve problems that contain such large nonlinearities that it is difficult to mathematically model or derive each model without significantly or overly simplifying the mathematics due to linearization techniques of the true physical environment. Furthermore, researchers are applying AI (i.e., neural networks^([8](#17_Chapter09.xhtml#rfn9_8))) to large data sets that are not amenable to standard system identification techniques, such as auto-regressive moving-average techniques and other classes of linear cost minimization or maximization processes. Evolutionary computation and Kalman filter neural networks utilized as function approximators perform extremely well when data is conditioned and proper training is applied to the data to be modeled.^([9](#17_Chapter09.xhtml#rfn9_9))

It is this modeling of brain function that neural networks—as described in the previous chapters—strive to attain when they are used in system modeling and approximation of processes. [Figure 9-2](#17_Chapter09.xhtml#fig4) shows a neural network three-layer architecture designed to perform the sequence of steps in the TCPED process as it could be computed by an AI system. In other words, [figure 9-2](#17_Chapter09.xhtml#fig4) illustrates how an AI system would perform the functions sketched in [figure 9-1](#17_Chapter09.xhtml#fig3) (with the exception of dissemination). It models the process from sensor input to the discernment of differences in predicted courses of action (exploitation). Massively parallel processing engines are able to encode history and memory for recall of what functions or processes should be performed, given the current state of the world.

When used in its proper context, AI can perform at lightning speeds and achieve desired outcomes faster than the human warfighter. Control of platforms, sensors, systems, desired outcomes, communications, and many other facets of warfare can be manipulated to provide an overall outcome of war that is not currently possible without utilizing artificial intelligence. The naval research and development (R&D) enterprise is working toward utilizing AI to improve on its systems, including its ISR system-of-systems.

## **AI APPLIED TO THE ISR FUNCTION**

With the onslaught of sensors, including drones, in all domains, the amount of collected and processed data is daunting. Cloud computing and parallel processing by vertical and horizontal scaling help with data processing and classifying results into threat and nonthreat categories. However, there is an inherent need by the community to have the human brain applied to algorithms and processes, either heuristically or by mathematical bounds and constraints applied to the individual problem. This added human knowledge domain allows algorithms and analytics to determine threats or find solutions to optimization problems for path planning—for example, to achieve the best course and speed for a vessel over time on its mission.

![Figure 9-2. Three-Layer Neural Network Architecture](images/pg173_1.png)

**Figure 9-2**. Three-Layer Neural Network Architecture

As a typical naval mission is executed, it will involve the execution of numerous submissions to accomplish it, each of which adds layers of complexity. For example, a naval mission might involve sorties being flown, helicopter missions, Marines loading into a landing craft air cushion for deployment ashore, and many other submissions in either the planning stages or under execution. As each submission is executed, situational awareness (SA) becomes more difficult to determine; warfighters might struggle to know exactly what is going on in the world around them at the moment. How will we provide that overall real-time SA that is required to the commander? With so much information being provided by the current and future ISR systems, new capabilities and tools must be implemented to inform the commander of the overall SA and to provide real-time COAs to quickly allow the commander to take action and to continue performing at a high level, even in conflict.

AI is one of the tools in the technological toolbox that can enable the naval R&D establishment to develop capabilities to allow the commander a real-time SA continually, without interruption due to fatigue, human error, or loss of networks. AI as a tool has the ability to learn in a supervised or unsupervised manner to model a given environment and provide a function approximation between data inputs and outputs. This function approximation ability allows AI to perform parallel processing at an extremely high speed and level of accuracy following the modeling of the brain structure of humans. These AI human-modeled mathematical processes execute in parallel at very high speeds, mimicking the brain’s processes and allowing extremely fast reactions and decision-making by a computer. The computing process could quickly determine threat, COA, and future COAs for all entities (ships, aircraft, drones, and people), and do so in a fraction of the time that it would take a human to determine, evaluate, and decide on provided information from the ISR processes.

## **PROJECTED NEAR-TERM ADVANCES**

Assuming that AI advances continue along their current trajectory, in the near term the Navy could apply it to help process raw imagery data to identify objects of interest and also to analyze the vast amounts of collected and stored data at a processing speed faster than real time. For example, analysts searching for signs of piracy threats would no longer need to comb through vast amounts of the ocean’s surface, hoping to find a ship with characteristics matching those of a pirate vessel. Instead, they will be provided with only those areas of interest that include an object of importance that was detected, identified, and tracked by AI techniques.

Another example is having on-board processing on unmanned vehicles in any domain to reduce throughput requirements and hardware costs, along with the reduction in manpower to process and exploit the data. Having on-board processing with AI at the helm allows for orchestration of analytics to process and exploit critical data without the need for manual intervention. This processing capability would both dramatically speed up the TCPED cycle of the ISR process and reduce manpower and systems costs, as well as deter and, if deterrence fails, quickly mitigate threatening behavior.

## **PROJECTED MID-TERM ADVANCES**

Looking ahead to the mid-term, we project that AI will allow the Navy to exploit existing data sources that currently go unused (for example, satellite imagery that gets dropped). This could include historical information that would provide pattern-of-life information. Government, industry, and academia are all extremely good at building hardware to sense and detect phenomenologies such as radio frequency, infrared, sound, vibration, imagery, and many others. However, by developing hard sensors, the amount of big data that is collected and stored on some level is astronomical. It is not possible to have enough manpower to sift through all the data, let alone process and exploit it for a commander to make a critical decision under stress.

One way forward for the naval R&D establishment is to continue to adapt current and future systems to utilize artificial intelligence to make use of big data that is currently unexploitable due to people, processes, and policies. AI could enable pattern-of-life models that are not yet available due to current standard techniques, as described in the scenario in chapter 6. By allowing AI to view and process data in multiple variants instead of a set processing chain, AI will be able to determine pattern-of-life examples and find threats that we presently are not able to find. AI will also enable the processing of large amounts of big data that are stored in the hopes that someday it will be exploited. AI is going to provide the means for relentless processing of historic data to detect minor and major shifts in behavior and other change detection parameters to utilize against our adversaries.

## **PROJECTED LONG-TERM ADVANCES**

In the long term, we project that AI will provide significant new capabilities across the board. If it is tailored to analyze new data sources that are largely untapped today (such as synthetic aperture radar images, acoustic recordings, video recordings, and sonar and radar data), AI could provide the Navy with a valuable new capability of having real-time processed and exploited data that is disseminated to warfighters worldwide. Having multiple intelligence sources exploited and subsequently disseminated will enable analysts to quickly manipulate data into a context for solving their warfighting requirements.

Additionally, massive amounts of big data that are time-consuming to process will be exploited at lightning speed to provide the commander detections, events, and COAs that are not achievable at this time. Even longer term, AI could further add soft sensors such as financial, news, cyber activity, social media, and other information to the processing chain. By exploiting financial data and other soft sensors, AI will provide insight into adversarial ideology and inform us of their strengths, weaknesses, and potential vulnerabilities.

Another domain of ISR is the utilization of data fusion as a capability to fuse disparate soft and hard data sources with AI finding linkages between them that humans cannot.^([10](#17_Chapter09.xhtml#rfn9_10)) This will enable the future “any sensor, any shooter” concepts, integrating ISR data from various platforms across all of the services and coalition and allied partner nations as well. It will also allow for a swarm of ISR sensors, each having a different function, for distributed TCPED across the battlefield.

Building on this fusion capability, the AI systems could offer valuable predictions and assessments to enable analysts to select the best COA for moving forward while maintaining the real-time requirements of the TCPED processing chain. These automation and automated learning developments would allow analysts to focus on the abilities at which they excel: applying their knowledge and experience to ascribe context to the ISR data, to determine its significance and impact, as well as select the COAs that will enable the best effects during a conflict. In short, these mid- and long-term technological leaps would allow analysts to perform more complex and meaningful analyses.

One key factor to the success of this vision is the ability for AI to team effectively with analysts with a balance of information and decision superiority for the naval warfighter. The technology must be fully integrated into the TCPED cycle, and new processes must be built to accomplish this. Additionally, we must recognize that in tailoring AI to process novel data sources, the Navy will not exclusively be able to leverage commercial advances. While industry has made significant strides in imagery recognition, commercial use cases from acoustic, video, or other nonimaging sensors are more limited and less closely aligned with the challenges the naval enterprise needs to solve in the future. Therefore, the capability will likely have to be developed in-house at naval laboratories and at government expense. Despite this, we expect that the cost will be more than offset by the capability gains and manpower savings, and most importantly by the timeliness of winning the continuous high-operational-tempo cycle in an act of conflict.

## **ADAPTIVE CLOSED-LOOP CONTROL**

The near-, mid-, and long-term advances discussed above each serve to automate parts of the TCPED process or to expand it by adding new (currently untapped) sources of data. However, the creation of an adaptive closed-loop control (ACLC) processing environment would completely transform the TCPED process. The high-level TCPED process shown in [table 9-1](#17_Chapter09.xhtml#tb4) contains an explanation of current, mid-term, and long-term AI processes to be solved by the naval R&D establishment. The change we are trying to facilitate is a break from sole dependence on manual or semi-automated methods of TCPED and development of automated methods similar to our neural network model. [Table 9-1](#17_Chapter09.xhtml#tb4) summarizes the current situation as well as what we envision can be eventually achieved.

Each of the TCPED processes can be extremely time-consuming and involve multiple human decisions along the processing chain. By applying AI techniques through R&D efforts, we believe the naval R&D enterprise will be able to achieve in the future an ACLC processing environment that works across all operating domains and across every platform available, including, in the future, drone swarms.^([11](#17_Chapter09.xhtml#rfn9_11)) Intelligent control to provide real-time information is key to winning future conflicts, as the initial and most impactful points that will occur in future warfare will revolve around information.^([12](#17_Chapter09.xhtml#rfn9_12)) To the extent that the Navy can quickly implement ACLC systems-of-systems, it will be able to leverage a new form of AI warfare that enables such quick decision-making that the OODA loop model for staying ahead of the enemy will be achieved by incorporating AI into all of our systems-of-systems.

**Table 9-1. TCPED Process with AI Extension**

![](images/pg178_1.png)

The ACLC system shown in [figure 9-3](#17_Chapter09.xhtml#fig5) depicts several stages of processing within a systems-of-systems context. ACLC processing is the key to the future of ISR utilizing artificial intelligence. A few key items in the figure are:

•  Desired outcome: AI techniques will either determine on their own or receive commands from the warfighter to drive a system or systems-of-systems underutilization to a desired state

•  Correction of errors: AI’s goals will be to drive system errors toward zero, thus enabling the best estimates of target states and overall intelligence

•  Systems under control: AI will perform route planning in near realtime to adapt to wartime environments at speeds human warfighters are not able to execute

•  Sensors: AI’s sensor control will enable sensors to be controlled in near real-time. AI will take video, adapt sensor gain to pull out quiet radar, and collaborate across swarms of platforms and sensors to generate a unified intelligence product.^([13](#17_Chapter09.xhtml#rfn9_13))

![Figure 9-3. Adaptive Closed-Loop Control Processing](images/pg179_1.png)

**Figure 9-3**. Adaptive Closed-Loop Control Processing

By applying AI to the adaptive closed-loop control process, the warfighter will have a total warfare TCPED process from seabed to space that will dominate any future threat or adversary. This will not, as Clausewitz might note, change the nature of war, but the increased (machine) speed of the process might change its character as AI systems contest other methods (and potentially their AI systems). Yet war’s characteristic struggle between detection and deception will likely remain, something Clausewitz would recognize.

## **CHALLENGES AND COSTS IN APPLYING AI TO THE ISR FUNCTION**

Many of the recent high-profile academic and commercial advances in AI in the field of computer vision lend themselves naturally to ISR applications that rely on exploitation of imagery and similar data types. But the high accuracy rates reported on carefully curated benchmark data sets do not necessarily translate into the robustness required in an operational application. Careful implementation is required to ensure that learned image classifiers are robust to noise and other image transformations. “Adversarial” examples, where inputs can be constructed that will fool a classifier into giving a wrong answer, have made headlines.^([14](#17_Chapter09.xhtml#rfn9_14)) But more mundane are situations where a classifier may be wrong because the input was out of the training distribution or for other reasons that we are unable to understand.

Researchers are increasingly starting to study these behaviors and try to explain why they might happen, how they can be prevented, and how system performance can be validated. This type of research is crucial to enable systems to be properly tested and validated before being deployed in a safety-critical application.

Robustness issues also raise trust issues in ISR applications that may not be considered in commercial applications. Many potential ISR applications of AI are as analyst aids. An analyst may lose confidence in an algorithm when it gets wrong what the analyst perceives to be an easy example, and they may gain undue confidence when they see the algorithm work. This can lead to the analyst turning the system off altogether or putting too much faith in the outputs. Additional research is needed into defining performance bounds and otherwise describing the capabilities and limitations of machine learning algorithms.

### **NOTES**

# 10

Communicating at the Speed of War

**The Future of Naval Communications and the Rise of Artificial Intelligence**

ALBERT K. LEGASPI, JEFF MAH, AND STEPHANIE HSZIEH

**The U.S. Navy’s strategic document** titled *A Design for Maintaining Maritime Superiority, Version 2.0 (Design 2.0*) noted the Navy must be able to compete in multiple domains and across the competition-conflict spectrum. In short, the Navy needs to be agile. Agility—the ability to move quickly^([1](#18_Chapter10.xhtml#rfn10_1))—has been a key factor in naval operations since the early days of trimarans and sails. The Duke of Wellington noted: “All the business of war, and indeed all the business of life, is to endeavor to find out what you don’t know by what you do; that’s what I call guessing what’s on the other side of the hill.”^([2](#18_Chapter10.xhtml#rfn10_2))

Since the beginning of time, commanders have tried to guess “what’s on the other side of the hill” and as part of the effort have developed means of communication to build a common tactical picture of the battlespace. Much of the effort has been influenced by the state of communications technologies and the advancing arsenal of weapons and ships. In the developing national security environment, the current and future battlespace is complex and has expanded into the virtual world as well with the recognition of cyberspace as the warfighting fifth domain.

If the Navy of today and tomorrow is to understand what is beyond the horizon, it needs to be able to establish and maintain universal communications to perform its mission. The term “universal communications” is used to describe the communications coverage from seabed to space. The U.S. Navy’s deployed command, control, communications, computers, intelligence, surveillance, and reconnaissance (C4ISR) systems are engaged in supporting multiple missions dynamically, often making it difficult to provide optimum network and communications configurations to support the many demands for applications/services performance guarantees. Operating in various environments from seabed to space enables the collection of sensor data on environmental conditions that can be used to design systems to adapt optimally to support operations. The richness of data can be taken advantage of using artificial intelligence.

Communicating at sea with the aim of better understanding what is over that horizon, as well as coordinating operations, has been a major endeavor for navies for millennia. To gain a better picture of the situation, navies have led in integrating the latest information and communications technologies into their operations. These technologies have taken various forms since the dawn of warfare—from signal flags to the harnessing of radio waves to networking communications technologies together in the digital age.

## **AGILITY AND SEA CONTROL**

The maritime domain has been an important source of economic, social, and political power for most of human history; civilizations and modern-day nation-states have depended on it for valuable resources and as a means for transportation and communication.^([3](#18_Chapter10.xhtml#rfn10_3)) Today, the sea lanes that traverse the globe are vital conduits of many of the products, raw materials, and commerce that drive the world’s economy. With 90 percent of global trade conducted on the oceans, it is no wonder that the United Nations reported that global sea trade expanded by 4 percent in 2017, the fastest in five years—amounting to a total volume of 10.7 billion tons of goods shipped.^([4](#18_Chapter10.xhtml#rfn10_4)) In the United States alone in 2017, 90 percent of imports and exports were carried by ship, and maritime activity generated $4.6 trillion and supported roughly 23 million jobs.^([5](#18_Chapter10.xhtml#rfn10_5))

The importance of these sea lanes and of global seaborne trade has often turned the world’s oceans into contested regions in an era of great power competition where rising regional powers compete for maritime access to maintain their economic, political, and military strength. Of growing concern is the rise of China and Russia, two nations that have publicly stated their intent to act as counterweights to the perceived dominance of U. S. power on the international stage.^([6](#18_Chapter10.xhtml#rfn10_6)) The case of China is particularly worrisome, as its activities in the South China Sea and military modernization efforts are part and parcel of the development of sophisticated anti-access/area denial capabilities.

The U.S. Navy’s *Design 2.0* highlights the need to “expand the competitive space” to compete for sea control amid the rise of regional national powers intent on asserting their ability to control the sea lanes of communication in their respective spheres of influence. The U. S. Navy is gearing up for an environment of uncertainty and increasing competition from near powers with naval forces that equal our own. A key part of building the naval capabilities to succeed in this competitive space is agility—the ability of naval forces to operate in any given situation across the full spectrum of conflict. *Design 2.0* noted that “restoring agility means realizing that operating in the spectrum can be non-linear and simultaneous.”^([7](#18_Chapter10.xhtml#rfn10_7))

The evolving concept of distributed operations incorporates the concept of agility into how our future naval force will operate. Distributed operations, when fully developed, will “describe the fleet-centric warfighting capabilities necessary to gain and maintain sea-control through the employment of combat power that may be distributed over vast distances, multiple domains, and a wide array of platforms.”^([8](#18_Chapter10.xhtml#rfn10_8)) The associated concept of distributed lethality calls for networked, distributed surface action groups equipped with their own offensive and defensive capabilities.^([9](#18_Chapter10.xhtml#rfn10_9)) These groups would be able to operate independently, thus increasing the ability of naval forces to adapt to a rapidly changing battlespace. According to the U.S. Navy, “distributed lethality spreads the playing field for our surface forces at sea, provides a more complex targeting problem, and creates more favorable conditions to project power where required.”^([10](#18_Chapter10.xhtml#rfn10_10)) At the heart of a distributed approach to naval force employment is the communications network, the electronic glue that connects all naval platforms and systems deployed across the globe and operating in multiple domains.

## **COMMUNICATING AT THE SPEED OF WAR**

The term communications, as it relates to maritime affairs, has two meanings. The first refers to the means of movement of commercial goods and services along with military supplies and troops across the world’s sea lanes.^([11](#18_Chapter10.xhtml#rfn10_11)) The second meaning of communications at sea refers to what *Webster’s Dictionary* defines as “a process by which information is exchanged between individuals through a common system of symbols, signs, or behavior.”^([12](#18_Chapter10.xhtml#rfn10_12)) This meaning of communications is what this chapter will address—the continuing evolution of how maritime forces exchange information at sea.

The key part of our definition of communications is “information exchange”—the ability to exchange information between members of one nation’s naval force or across a maritime coalition.^([13](#18_Chapter10.xhtml#rfn10_13)) In the arena of naval warfare, communications is needed to maintain dominant battlespace awareness—to know where your enemies are and where your own forces are arrayed. From this knowledge comes the ability to plan to defeat the enemy. As Wayne P. Hughes and Robert P. Girrier note, “Modern naval battle will be fast, destructive, and decisive. More often than not the result will be decided before the first shot is fired,” as advancements in weapons technology (primarily missile technology) and scouting capabilities have increased the reach and lethality of many naval forces.^([14](#18_Chapter10.xhtml#rfn10_14)) For the U. S. Navy, the ability to operate in this complex and ambiguous battlespace is increasingly influenced by the need to harness the power of information to assess the situation and deliver the appropriate response.

The speed and lethality of the modern battlespace brought about the need for commanders to extend their range of situational awareness through the adoption of the technologies of the computer age. The age of missiles and longrange nuclear weapons refocused attention to improving the speed of weaponry and fires and scouting or sensing.^([15](#18_Chapter10.xhtml#rfn10_15)) The increased tempo of the battlespace that came with guided missiles and aircraft forced navies to rethink how to communicate and gather vital information to assess what was out there.^([16](#18_Chapter10.xhtml#rfn10_16)) In 2018 Adm. John Richardson, then Chief of Naval Operations, noted the importance of the ability of a networked fleet to shift through information faster than our adversaries:

A third dimension of naval power as we think about it is to take those platforms with their inherent capability which we can increase, and then network them together. So this third component is a networked fleet. So we have sort of a bigger fleet, a more capable fleet, and now a networked fleet. And there are plenty of examples in history where just the power of networking things together creatively, adaptively, brings actually more power to that force. So we can talk about some of those historical examples. But it makes intuitive sense, as well. It sort of checks with the chart that if you’re able to share data more across the force, you’re able to respond to that awareness with more agility, you can be a more powerful fleet.^([17](#18_Chapter10.xhtml#rfn10_17))

The U.S. Navy has a long history of networking and was the earliest adopter among the services. In the 1950s the U.S. Navy fleet exercises revealed that combat information centers (CICs) organized around manual and analog technology had trouble detecting “enemy” aircraft. The slow pace of detecting and cataloguing enemy and friendly aircraft and of communicating with airborne early warning aircraft quickly overwhelmed the CICs of the fleet. During one exercise in the 1950s conducted by Sixth Fleet, “\[t\]he load was so great and communications so slow that half of all bandits \[enemy aircraft\] closed seventeen nautical miles or more between being detected and having CAP \[Combat Air Patrols\] assigned. Delays in the arrival of CAP further reduced defense effectiveness, so that in the end, three-quarters of all raids arrived at the force completely unopposed by fighters.”^([18](#18_Chapter10.xhtml#rfn10_18))

Work began in the U.S. Navy and in other Western navies—particularly in the United Kingdom and Canada—on automating combat systems to improve fleet reaction times to jet age threats. An officer in the Royal Canadian Navy, Lieutenant James Belyea, proposed early on that digital computers could be the key to improving combat systems. Lieutenant Belyea and a Canadian engineer, Stanley F. Knights, proposed a digital link that would “connect the systems aboard ships operating together.”^([19](#18_Chapter10.xhtml#rfn10_19)) From this came the tactical data links and the digital command and control technology that emerged during the Vietnam War era.

The development of tactical data links allowed the almost instantaneous sharing of sensor data between ships and aircraft and provided commanders a common view of force sensors and the ability to rapidly coordinate operations. Tactical data links and computerization proved to be invaluable assets to the U.S. Navy during operations in the waters and airspace of North Vietnam. Naval tactical data systems along with ultra-high-frequency (UHF) radio systems made it possible for the U.S. Navy to network its ships and aircraft with each other and with the U. S. Air Force. This early “netting” of assets allowed the U.S. fleet to obtain an operational picture deep into North Vietnam to counter the North Vietnamese MiG threat.^([20](#18_Chapter10.xhtml#rfn10_20))

The development of the Advanced Research Projects Agency network and its growth in the 1970s began the information age, where quickly evolving computers were connected to grow the original Internet and expand it into the World Wide Web of today.^([21](#18_Chapter10.xhtml#rfn10_21)) While the Internet spurred an information and communications revolution in the private sector, another revolution—the revolution in military affairs (RMA)—entered the lexicon of U.S. military thinkers. RMA was first brought forth by the Soviets in the 1940s and argued that “the combination of nuclear weapons, jet aircraft, and missiles had drastically changed warfare … \[and\] computers \[which they called cybernetics\] would have a similar impact.”^([22](#18_Chapter10.xhtml#rfn10_22))

A primary concern in the United States was how to conduct force planning after the fall of the Soviet Union and the emerging era of smaller defense budgets. Military and civilian defense planners struggled to devise the proper force construct to manage the United States’ new position as the global leader yet work with fewer battalions and ships. For example, the U. S. Navy, at the height of the Cold War, had a fleet of more than 590 ships. When the Soviet Union collapsed and the Cold War ebbed, the U. S. Navy’s fleet shrunk dramatically to 392 in 1995 and to the current level of around 280 ships.^([23](#18_Chapter10.xhtml#rfn10_23)) It was in this environment of balancing the U.S. military’s increased engagement in operations other than war and decreasing force structure that military leaders and strategists examined the promise of information communications technologies and netting to do more with less.

The ideas professed by RMA thinkers to use information age technologies to revolutionize the way the United States wages war were documented officially in the 1997 *Quadrennial Defense Review* (QDR). The QDR was a congressionally mandated review of the U.S. military to provide the civilian leadership and the American public an assessment of the Department of Defense’s (DoD’s) strategies and priorities. The first QDR was published in 1997 and set the U.S. military on the course to transforming to achieve “information superiority.”

The ongoing transformation of our military capabilities—the so-called Revolution in Military Affairs (RMA)—centers on developing the improved information and command and control capabilities needed to significantly enhance joint operations. With the support of an advanced command, control, communications, computers, intelligence, surveillance, and reconnaissance (C4ISR) common backbone, the United States will be able to respond rapidly to any conflict; war-fighters will be able to dominate any situation; and day-to-day operations will be optimized with accurate, timely, and secure information. Just as much of the non-defense world has become increasingly interconnected through the growth of internetted communications, the Department of Defense is working to provide a complementary, secure, open C4ISR network architecture.^([24](#18_Chapter10.xhtml#rfn10_24))

The U.S. Navy was the first to take advantage of the emerging information communications technologies when it fielded the Copernicus information technology architecture. The four goals of the architecture were “to provide a common tactical picture to all members of a naval force; to comprehensively connect them in a web of instantaneous voice and data links; to compress the steps involved in moving information from sensors to shooters; and to conduct information operations that would degrade enemy warfighting capabilities.”^([25](#18_Chapter10.xhtml#rfn10_25))

The Copernicus architecture was the first effort to develop the network-centric warfare concept. Introduced to the defense community in 1998 by Vice Admiral Arthur Cebrowski and John Garstka, network-centric warfare was developed to take advantage of information and communications technologies and business processes that were changing how businesses operated.^([26](#18_Chapter10.xhtml#rfn10_26)) The authors pointed to several businesses like Walmart that had used information and communications technologies to keep detailed reports on the levels of inventory that were shared directly with vendors who could better determine what was needed at various Walmart stores.^([27](#18_Chapter10.xhtml#rfn10_27)) Cebrowski and Garstka argued in their U.S. Naval Institute *Proceedings* article that successful businesses employed “network-centric operational architectures that … provide the ability to generate and sustain very high levels of competitive space awareness, which is translated into competitive advantage.”^([28](#18_Chapter10.xhtml#rfn10_28))

While the term “network-centric warfare” has faded from use, the belief in the power of networked forces continues. The concept of the future Navy envisions a fleet netted “together in ways that are reliable and secure” to allow commanders to make decisions faster than the enemy.^([29](#18_Chapter10.xhtml#rfn10_29)) The netted Navy of today and tomorrow will need a reliable global communications network that can operate in an increasingly contested operational space with highly mobile and dispersed forces.

## **THE PROMISE OF ARTIFICIAL INTELLIGENCE**

In a lecture more than thirty years ago, Nobel Prize–winning economist Herbert Simon described artificial intelligence as “the study of computers doing intelligent things—that that would require intelligence of people.”^([30](#18_Chapter10.xhtml#rfn10_30)) Back then, in the late 1980s, the U. S. Navy was exploring the use and application of artificial intelligence. During his lecture, Simon speculated on the future of AI and the possibility of computers discovering new scientific laws given the ability of intelligent systems to analyze large amounts of empirical data. With that in mind, Simon further noted the following about the role of AI in augmenting and supporting the development of human understanding and performance: “In AI there are two complementary routes to enhancing human intelligence. One is to build intelligent machines that can augment it. The other is to improve our skills in using our own minds for learning, thinking, solving problems, and making decisions. The latter route, the enhancement of human performance, may in fact be the more important one.”^([31](#18_Chapter10.xhtml#rfn10_31))

Simon’s observations three decades ago summarize today’s many assessments of the burgeoning power of artificial intelligence to enhance human intelligence and performance. The DoD description of AI echoes a similar assessment of the importance of this technology in supporting military and department operations—that is, impacting the work of both the “tooth and the tail”: “the ability of machines to perform tasks that normally require human intelligence—for example, recognizing patterns, learning from experience, drawing conclusions, making predictions, or taking action—whether digitally or as the smart software behind autonomous physical systems.”^([32](#18_Chapter10.xhtml#rfn10_32))

The DoD approach to harnessing the power of AI is stated in the summary of its 2018 artificial intelligence strategy that listed four general areas where AI will support the department’s mission:

•  support and protect service personnel and civilians through “decision-making and operations to reduce risk to fielded forces and generate military advantage”

•  enhance the ability to predict and respond to threats in the physical and cyber world

•  optimize and streamline workflows by using AI to handle mundane and routine tasks while freeing up humans to work on more complex tasks

•  develop new capabilities, at a global level, to “pioneer AI approaches across the full scale of our global defense enterprise in a manner that is Joint and interoperable with interagency, allied, and coalition partners.”^([33](#18_Chapter10.xhtml#rfn10_33))

The U.S. Navy is also looking to artificial intelligence to enhance the ability of the fleet and individual warfighters to assess the battlespace and complete the observe, orient, decide, act (OODA) loop faster than our adversaries.^([34](#18_Chapter10.xhtml#rfn10_34)) Naval analyst Norman Friedman described the importance of the OODA loop to warfighting in the information age:

A reasonably persuasive theory of combat holds that the enemy’s will can be destroyed if he cannot move quickly enough to react to successive blows. In this “OODA loop” theory, combat is cyclical, consisting of observation, orientation, decision and action. If the cycle used by one combatant is significantly slower, the combatant loses the ability to understand what is happening to him; ultimately, he suffers what amounts to a nervous collapse. OODA loops success can be achieved by a combination of accelerating our own operations and slowing the enemy’s.^([35](#18_Chapter10.xhtml#rfn10_35))

Artificial intelligence is the hoped-for technology that the Navy and the other services are looking toward to rapidly build the picture of what is over the horizon and act faster than the adversary. The age of missiles and the coming era of hypersonic weapons have expanded the boundaries of the battlespace—the area of ocean and space that a battlegroup is able to observe with its organic and electronic sensors.^([36](#18_Chapter10.xhtml#rfn10_36)) A 1994 Naval Studies Board study of what was then the emerging naval communications network architecture noted that an effective battlespace is one where “a target is located and identified, weapons delivered, and assessment of damage obtained”; however, “\[w\]hen the battle space is dynamic, as with mobile forces or in crisis situations with little warning, there is a burden on communication to and from the on-scene forces.”^([37](#18_Chapter10.xhtml#rfn10_37)) Twenty-plus years later, there is a similar need for communications networks and systems that can support dynamic operations with an increasingly mobile and dispersed force, but now the technology is closer at hand with developments in software-centric systems and emerging technologies such as artificial intelligence and machine learning.

Reliable communications networks will be the backbone of any artificial intelligence ecosystem the U.S. Navy and other services will need to establish, because the lifeblood of AI is data. In discussions of the use of artificial intelligence in military operations, the focus tends to center around its application in intelligence, surveillance, and reconnaissance, logistics, information operations, command and control, autonomous systems, and lethal autonomous unmanned systems. These current and future applications of AI will require a robust communications network that can transmit, receive, and route large amounts of data from all domains—from seabed to space—and in any environmental condition a globally dispersed Navy may find itself.

A mobile ad hoc network (MANET), with the addition of AI, will support resilient communications consisting of mobile platforms in a dynamic connection environment. As reliance on networked systems for critical applications and services increases, there is a recognition that networks have a significant impact on all aspects of operations.^([38](#18_Chapter10.xhtml#rfn10_39)) Development of resilient networks will increase in importance: “A MANET is needed for self-forming, self-configuring, and self-healing operation where the media and communications channels undergo rapid changes (e.g., over free space optical, RF \[radio frequency\], and underwater acoustic links) and nodes freely enter and leave the network.”^([39](#18_Chapter10.xhtml#rfn10_39))

This complex system of multiple elements of various types and random connectivity presents challenges that AI can potentially address. Several challenges to be addressed include forecast of network environment, adapting to a constantly changing operating environment, and awareness of user service requirements and governance: “Artificial Intelligence (AI) techniques enable real-time, context-aware adaptivity that have the potential to meet the needs of networks in general, and MANETs in particular.” AI applied to MANETs will form the basis of a highly adaptive network that is much more effective under a wide range of operating environments.

An area where AI has the potential to support future naval operations is in the development of software-based cognitive communications systems. Software-defined radios have been around for a while and have made it possible for new and legacy radios to cover multiple communications frequencies—high, very high, and ultra-high—and operate on mobile ad hoc networks. Since AI is software-based, the next logical step has been the incorporation of AI code in these radios. Cognitive radios are the future offshoot of software-defined radios and can crunch through data to automate the monitoring of the frequency spectrum and the electromagnetic environment.^([40](#18_Chapter10.xhtml#rfn10_40))

The Defense Advanced Research Projects Agency’s (DARPA’s) adaptive radio frequency technology is developing the future generation of cognitive radios that “would be able to reconfigure themselves to operate in any frequency band with any modulation and for multiple access specifications under a range of environmental and operating conditions.”^([41](#18_Chapter10.xhtml#rfn10_41)) Another DARPA project incorporating AI/machine learning capabilities addresses another communications issue—wireless communications threats in the battlespace. The goal of the Behavioral Learning for Adaptive Electronic Warfare program is to develop machine learning algorithms that can detect and neutralize wireless communications threats in the field rather than the current method of assessing and developing countermeasures in laboratories.^([42](#18_Chapter10.xhtml#rfn10_42))

Within the Navy’s research and development laboratory community, research is under way on employing artificial intelligence/machine learning capabilities to optimize communications pathways to enable the fleet to operate in any part of the world and under any conditions.

## **UNIVERSAL COMMUNICATIONS**

The U. S. Navy needs to be able to establish and maintain universal communications in order to perform its mission. The term “universal communications” is used to describe the communications coverage from seabed to space. The ability to maintain basic communications is often a challenge, especially when operating in regions without a communications and networking infrastructure, such as the Arctic. Even operations in peacetime within the mid-latitude have always been a challenge due to limited bandwidth and instability of satellite communications and line-of-sight links. However, with those challenges in mind, the U. S. Navy must be able to support simultaneous missions that will require the fleet’s underlying networking/communications infrastructure as well as the required applications and services to adapt to the dynamic operational environment. Adapting these optimization changes to networks within one domain, such as at sea, will be a significant challenge due to the heterogeneity of the networks as well as the challenges imposed by the dynamic environmental and operational conditions.

Each platform has several classified enclaves, each consisting of legacy as well as Internet protocol–based networks. Hence, adapting changes for all domains—from seabed to space—may be considered impossible. With such complexity, one may consider embedding machine learning algorithms within strategic points of the network to enable training locally. These algorithms will learn from locally collected data and provide recommended changes to configuration in order to improve performance of traffic locally. The more challenging approach is to train, in a timely fashion and subject to limited bandwidth resources, all algorithms that are geographically spread in order to improve overall network performance. In this section, we will discuss these challenges associated with tactical networks and include some technologies that may help support a distributed machine learning architecture.

## Data

In a tactical wireless environment, the wide area network and mobile devices have the capability of generating huge amounts of data ranging from the application to physical layers.^([43](#18_Chapter10.xhtml#rfn10_43)) Complexity is added with changes in propagation properties, such as drops of packets due to fading as well as changes of nodes’ access points. Wide area and local area network routers and switches will have logs and tables that summarize routing and switching configurations while radios, modems, and controllers provide specific settings as well as some performance data. Network management systems monitor and adjust network devices defined by metrics for each network device. Network data can be collected at all seven layers of the open systems interconnection stack, resulting in volumes of unstructured and diverse data.

## Machine Learning Algorithms

Arthur L. Samuel was among the first to discuss machine learning based on work he did for IBM in 1959. He defined machine learning as a “field of study that gives computers the ability to learn without being explicitly programmed.” Hence, computers are trained and machine learning algorithms are adjusted using data captured through digital activity or by integrated sensors in order to improve prediction.

Several types of machine learning algorithms are available through the open market. Determining which type is desired depends on how these algorithms are classified by their learning methodologies, which in turn helps users determine a suitable algorithm based on the type of data collected. In addition to learning methodologies, another way to distinguish one algorithm type from another is by grouping them by their operational mechanics. There are several types of mechanics such as regression, decision tree, and clustering. Most of these algorithms require a subject matter expert working with data scientists to help set up the training data. For example, with supervised training, each data point collected is labeled prior to training. In scenarios with a large volume of heterogeneous data, this approach would certainly be unrealistic. Deep learning is a specialized class of algorithm that handles large amounts of unstructured data through a multilayer nonlinear processing approach.^([44](#18_Chapter10.xhtml#rfn10_44)) Neuro-networks are commonly used in deep learning where adjustable parameters (for example, weights and probabilities) in each layer are adjusted as input data pass through the network. Over time, the neuro-net’s output becomes more accurate. Several assessments have been done to demonstrate the ability of neuro-nets in handling big data.^([45](#18_Chapter10.xhtml#rfn10_45))

## Synchronization

In a tactical environment, deep learning algorithms will need to be trained and synchronized to ensure end-to-end traffic flow is coordinated appropriately. Unfortunately, synchronizing parameters between nodes may be complicated by the inherent delay due to propagation, loss of data because of channel fading, and limited and unstable availability of bandwidth. In addition, algorithms that are deployed may require frequent synchronization due to mobility, so care must be taken to ensure the implementation of the algorithms does not affect operational performance. There are a variety of distributed deep learning systems studies that show good performance in a mobile context.^([46](#18_Chapter10.xhtml#rfn10_46)) Each solution will need to be assessed by a combination of network engineers and machine learning experts.

## Computing and Architecture

In a distributed machine learning architecture, computing capability will be a main factor for all nodes of a wide area network. Mobile edge devices such as smart phones must have sufficient computing power and power resources. In addition, training synchronization among mobile and fixed platforms will require a computing architecture that reduces the necessity of sharing large amounts of data throughout the networked environment. In mobile wide area networks, especially in the U.S. Navy, bandwidth will be limited, and as a result, latency will affect the efficiency of training devices for distant platforms. Fortunately, these challenges are being addressed in architectures developed for fog computing. Fog computing places storage and computing with edge devices and enables connections with data centers to permit essential data transfer. Fog computing edge devices are equipped with power-efficient and parallel processing chips to handle the computing requirements required at the edge. The deployment of 5G technology will include graphics processing unit technologies that provide much more computation power through parallel computing.^([47](#18_Chapter10.xhtml#rfn10_47)) Google’s edge tensor processing unit was designed for edge computing by providing machine learning capability at the edge, which consumes less power than traditional units with the same number of processors.

## Security

A distributed machine learning architecture has several vulnerabilities at all layers ranging from the application to the wireless medium. Securing vulnerabilities of the network has always been a challenge as adversaries continue to pursue new attack methods. In addition to the security mechanisms for networks and communications devices, sensors and data collection nodes will also have to be secured to ensure authentic, validated, and verified training data are made available. Training data can be sabotaged, thereby impacting machine learning algorithms’ output performance. Data can be added or modified to training in order to compromise algorithms. Hence, poisoned algorithms become less accurate, enabling further infiltration by an adversary. For example, spam detection algorithms have been impacted by bad data, enabling unwanted traffic from entering the network.^([48](#18_Chapter10.xhtml#rfn10_48)) Imagery data have been modified to enable misidentification by classification algorithms. As with network security, a distributed machine learning architecture must also be hardened to prevent or reduce impact to algorithms.

The heterogeneity of today’s mobile tactical nodes—such as the number of network elements, diversity of applications, edge device types, interface characteristics, and mobile network configuration—will cause users to experience severe performance degradation. External environmental factors (for example, adversarial actions or propagation losses) may result in loss of access to network services and impact operations. Fortunately, selective application of machine learning algorithms can be employed to develop an agile, resilient, and effective system for information exchange. Distributed machine learning capability can certainly improve performance, especially for a large network consisting of multiple domains from seabed to space. We have covered some of the potential issues with distributed machine learning architecture with a high-level discussion of solutions—hardware or software—along with the need to secure the artificial neural net from compromise by crafted attacks applied to the AI.

## **CONCLUSION**

In late 2019 Adm. Michael Gilday became the thirty-second Chief of Naval Operations. During his confirmation hearings, Admiral Gilday noted:

\[The United States faces\] an urgent imperative to adapt to rapid technological advancements and avoid further erosion of our competitive military advantage. Algorithms and machine learning have become commodities, accessible to our adversaries and with the potential to accelerate the pace of military operations beyond what our systems were built to confront. We need to get faster—across the entire service—in order to inject uncertainty into our competitors’ decision cycle and become better at competing across the full spectrum of competition. The adaptability and agility of our people, both uniform and civilian, are key to responding to this central challenge.^([49](#18_Chapter10.xhtml#rfn10_49))

Naval communications systems and networks also need to be agile and fast in an environment where adversaries hold comparable AI and machine learning systems that could put them at the leading edge of the ever-important OODA loop. The nation and the U.S. Navy will need the talents of its industry and academic partners and its in-house government scientists and engineers to harness the potential of artificial intelligence to enable the fleet to operate in this emerging future battlespace.

### **NOTES**

# 11

How AI Is Shaping Navy Command and Control

DOUG LANGE AND JOSÉ CARREÑO

Ultimately, command and control is the commander’s contribution to winning the fight. One day, the U.S. military is going to encounter an enemy who is multi-dimensional, well-equipped, well trained, willing to fight, and intending to win. When that day comes, the commanders who are best trained to exert exacting control over their forces to relentlessly advance their plans will win the day—every time.

—Vice Adm. Robert F. Willard, U.S. Navy^([1](#19_Chapter11.xhtml#rfn11_1))

**From Trafalgar to Midway to Leyte Gulf**, effective command and control (C2) proved indispensable to the outcome of these historic naval engagements. As old as warfare itself, C2 ultimately constitutes a human endeavor, prone to the imperfections and vicissitudes endemic to mankind.^([2](#19_Chapter11.xhtml#rfn11_2)) The application of technology to support commanders—from flag signals in the age of sail to the modern-day combat information center—has improved commanders’ ability to observe the enemy, orient and communicate with their forces, and act upon their adversaries. The concomitant rise in the reach and accuracy of modern-day “batteries” in the form of over-the-horizon missiles traveling at supersonic speeds has reduced the time in which commanders can and should act to minutes or seconds.

Making decisions by leveraging the inordinate and increasingly overwhelming volume of data at the speed required to survive and prevail in highend warfare today presents a challenge of cognitive overload. Whereas Lord Horatio Nelson had hours before making contact with the French and Spanish fleets at Trafalgar, today’s naval leaders do not—and tomorrow’s leaders will not—have that luxury. They will be trying to make sense of the deluge of data and information from intelligence, surveillance, and reconnaissance sensors even as they attempt to communicate orders and decisions to subordinate units. Clearly, the challenge to command and control naval forces in modern times is to provide commanders with the ability to make better decisions, faster than their adversaries. Artificial intelligence (AI) offers the means to deal with the data deluge, mitigate cognitive overload, and provide commanders with decision aids that expedite their ability to develop, evaluate, and decide upon courses of action.

However, as countless observers and official defense and naval guidance documents have expressed, the United States finds itself competing in the domain of artificial intelligence. Notably, the *National Defense Strategy* prioritizes investments in new technologies such as artificial intelligence to “gain competitive advantage” and ensure “we will be able to fight and win the wars of the future.”^([3](#19_Chapter11.xhtml#rfn11_3)) Nations that prevail in this race will bestow their future naval commanders with the tools to make decisions better and faster than their adversaries. The *National Defense Strategy* does not mince words; the United States cannot take its position for granted. The outcome of this competition remains unknown, and “America’s military has no preordained right to victory on the battlefield.”^([4](#19_Chapter11.xhtml#rfn11_4))

Future Nelsons, Burkes, and Halseys will count on command and control empowered by the best artificial intelligence to prevail. Lest anyone doubt this as an exaggeration, former commander of the U.S. Pacific Fleet Adm. Scott Swift noted, “This is not science fiction. In the not-too-distant future we surely will shift from man-to-man direction to man-machine and machinemachine interfaces, and finally (although worrisome to many) to machineman arrangements.”^([5](#19_Chapter11.xhtml#rfn11_5)) Ceding ground in the application of AI to C2 will leave future Sailors and Marines at a distinct disadvantage.

## **COMMAND AND CONTROL DEFINED**

An abundance of research and work exists on the topic of C2—from historical studies to theoretical and conceptual models—offering a range of definitions.^([6](#19_Chapter11.xhtml#rfn11_6)) In general terms, it is about setting a goal, evaluating options to achieve it, directing actions to that end, and monitoring progress. The U. S. Department of Defense defines command and control as “the exercise of authority and direction by a commander over assigned and attached forces to accomplish the mission,” listing a dozen tasks that encompass the “C2 function.” The publication goes on to note an important difference between “command” and “control:” “Command includes both the authority and responsibility to use resources to accomplish assigned missions. Control is inherent in command. To control is to manage and direct forces and functions consistent with a commander’s command authority. Control provides the means for commanders to maintain freedom of action, delegate authority, direct operations from any location, and integrate and synchronize actions throughout the operational area (OA).”^([7](#19_Chapter11.xhtml#rfn11_7))

Notably, the Department of Defense highlights the unique nature of C2 in the maritime domain, one steeped in the “traditions and independent culture” of naval forces where subordinate commanders execute operations independently based on an understanding of “commander’s intent.”^([8](#19_Chapter11.xhtml#rfn11_8)) Decentralization thus characterizes joint maritime operations; subordinate leaders at every echelon must understand their commander’s intent and “exercise disciplined initiative and act aggressively and independently to accomplish the mission.”^([9](#19_Chapter11.xhtml#rfn11_9))

The fact that the Department of Defense also offers definitions of command and control for the land and air domains suggests that there is no single “one size fits all” approach to C2. This point cannot be overstated. Command and control approaches span the spectrum from highly centralized to highly decentralized models, and choosing the “correct” approach depends on a variety of factors.^([10](#19_Chapter11.xhtml#rfn11_10)) Long-time scholars of command and control David Alberts and Richard Hayes list among these factors:

•  warfighting environment—from static (trench warfare) to mobile (maneuver warfare)

•  continuity of communications across echelon

•  volume and quality of information moving across echelon and function

•  professional competence of the decision-makers (senior officers at all levels of command) and their forces

•  degree of creativity and initiative the decision-makers in the force, particularly the subordinate commanders, can be expected to exercise.^([11](#19_Chapter11.xhtml#rfn11_11))

By way of example, Alberts and Hayes posit that the Soviet Union adopted a highly centralized approach during World War II “because they lacked the communication systems needed for richer exchanges, because Stalin demanded the ability to make all important decisions, because they were resource constrained and felt they needed a central control that would optimize their allocations, and because their commanders and forces lacked the professional skills to exercise creativity.”^([12](#19_Chapter11.xhtml#rfn11_12))

In contrast, a decentralized “control free” C2 philosophy provides “virtual autonomy” to subordinate commanders who are entrusted by their superiors. General Douglas MacArthur, for example, reportedly “called in the commander of his theater Army Air Corps and told him to ‘keep the Japanese air forces out of my way.’ That was the only order issued and the subordinate was left free to decide how he would accomplish the mission.”^([13](#19_Chapter11.xhtml#rfn11_13))

Notably, the decentralized approach has “been relatively rare in history and very rare since the telegraph and wireless made it possible for senior commanders to stay in touch.”^([14](#19_Chapter11.xhtml#rfn11_14)) In his book *Command at Sea*, historian Michael Palmer underscored that since the age of sail, “the natural tendency of most commanders has been and always will be, to control, to centralize,” and this proclivity has only increased as the technology that allows “senior commanders to stay in touch” has proliferated.^([15](#19_Chapter11.xhtml#rfn11_15))

Any discussion of technological application to command and control, and no less the application of artificial intelligence, must bear in mind two key things. First, resist the temptation to view the latest technological advances as the panacea to the ills that afflict command and control.^([16](#19_Chapter11.xhtml#rfn11_16)) Second, bear in mind the centrality of the human element, for at the end of the day, “only humans command.”^([17](#19_Chapter11.xhtml#rfn11_17)) Given its human nature, the practice of command and control bears scientific, analytical, and artistic semblances.

## **THE ART OF COMMAND AND CONTROL**

In his article, “Rediscover the Art of Command and Control,” Vice Adm. Robert Willard posited that C2 should be understood as “operational arts and methods for effective control of forces” and not in terms of specific technologies.^([18](#19_Chapter11.xhtml#rfn11_18)) Command and control, he lamented, “is a lost operational art that has been swept into cyberspace by a whirlwind of technologies, made less significant by weak doctrine and misunderstood terms, and put off by future visions of every war fighter possessing relevant information.” He further warned that “the immense power of all these tools will go to waste until we master the whole of C2 and understand precisely where and when the tools play in the commander’s decisions and responsibility to control the fight.”^([19](#19_Chapter11.xhtml#rfn11_19))

Sixteen years later, Adm. Scott Swift echoed these sentiments, warning that “we must guard against the thirst for the latest high-tech weaponry and reliance on complex computer systems that operate them.” He went on to observe that “too much time, attention, and resources are being devoted to the science of warfare, rather than the art of it,” asserting that this constitutes a “grave mistake … because the most important skill a warfighter needs to master is the art of C2.”^([20](#19_Chapter11.xhtml#rfn11_20)) Thus, any discussion on the merits of artificial intelligence and the promise it holds for how the Navy conducts command and control should be understood as a supporting element, or what Admiral Swift coined as “science in the service of art.” This clearly articulated need by two senior naval officers and operators constitutes one that scientists and engineers should heed in order to deliver capability congruent with operational realities.

AI constitutes a pivotal element to the success of future commanders who are likely to face an accelerated pace of operations in potential conflicts against peer and near-peer adversaries. What Admiral Swift describes as “augmented” C2 encompasses the potential of AI to future commanders; the ability for them to rapidly assess, act, and react to complexity in tense, high-pressure, and stressful environments faster than any potential adversary.^([21](#19_Chapter11.xhtml#rfn11_21)) This is what some have termed as “getting inside the enemy’s OODA \[observe, orient, decide, and act\] loop” and is an important way to understand how artificial intelligence can—as Admiral Swift wrote—“serve to support, enhance, and facilitate more effective C2.”

## **APPLYING AI TO THE OD OF OODA**

As discussed in previous chapters, Col. John Boyd’s OODA loop offers a useful framework by which to evaluate the application of AI to C2. Colonel Boyd developed this framework to describe the success of U. S. fighter pilots over their adversaries in the skies over Korea. Simply, the pilot would observe (i.e., detect) the enemy MiG. He would then orient his aircraft toward an advantageous position, decide on a course of action, and then act on it.

In order to decide on an effective course of action, the pilot also must have enough knowledge of the enemy (and his/her doctrine) to be able to predict enemy reactions over the course of the engagement. It is likely that Boyd chose not to include a separate “predict” phase but rather to subsume it in the act phase because of the speed at which fighter engagements are conducted. The pilot acts instinctively based on knowledge of the enemy as well as the combat conditions. It is fair to ask if AI, operating at machine speed, could help in predicting enemy reactions.

With the idea that C2 lives primarily in the realm of “orient-decide,” it is possible to ground the capabilities that AI can provide to these aspects along with C2 tasks. This chapter will expand on the orient-decide zone by discussing orientation, rapid decision-making (which includes the particular concept of prediction), analysis and planning, and communicating decisions and continuous reassessment. The second and third elements will allow a discussion on the application of fast versus slow/deliberate approaches in decision-making, which can result in using different AI techniques, and will also delve into how problems might be decomposed to utilize both in the applications of the future.

## **HOW AI CAN AFFECT THE TASKS OF COMMAND AND CONTROL**

Planning cycles exist in part because of the need to bring a variety of information together, to analyze interactions among participants, and to ensure that the humans involved in the planning process understand the plan. It is often said that plans are useless, but that the process of planning is quite valuable. As artificial agents are incorporated into the planning process, the need for and value of cycles and various aspects of the process will change. In some cases, AI will be used to find information and present it to the human decision-makers, simply speeding up their effort and allowing for a faster cycle. In other cases, agents themselves will present portions of the plan to the team, meaning that humans were not part of some aspects of the process. In other cases, artificial agents will be tasked with monitoring and making decisions over particular aspects of the battle space. Our current planning cycles and their time periods will have little relevance here. Decision-making must become based on events, not cycles, and AI will both help and necessitate such a change.

## Orientation Tasks

As mentioned, one common model of decision-making is the OODA loop. Orientation sits at the fuzzy boundary between intelligence, surveillance, and reconnaissance (ISR) and C2. Orientation is the process of making sense of the information provided and updating one’s model of the world. This process occurs in both human and artificial agents. The use of classifiers in interpreting sensor data assists in this process. Classifiers indicate the presence of a pattern suggesting a particular hypothesis to be made—for instance, a particular type of ship was present in a particular area of the ocean at a particular time.

ISR systems can go further using techniques known as plan, activity, and intent recognition (PAIR). In the future, we will have PAIR capabilities that work on groups and swarms of units. Put together over an entire area of interest, ISR systems can provide the portion of the world view that a command needs to understand the activities of opposition and neutral elements.

Orientation around the disposition of friendly forces is critical as well. While much of the reporting and tracking of our own forces doesn’t fall into the AI category, there are aspects that will. First, PAIR will not only be used to interpret the actions of opposition and neutral units. Our own units are subject to conditions that mean that communications will not be continuous or of sufficient bandwidth for full information to always be available. Naval forces are subject to the environment as well as enemy efforts to prevent communications. Forces may also employ emission control strategies to mask their own movements and actions. For this reason, the same AI techniques used in PAIR for opponents is useful for predicting the activities of our own forces when isolated from communications with higher command, though we should also have doctrinal information and previous plans to help us improve our estimates of these activities.

Similarly, we wish to forecast our own force status based not only on where they are now, but also on what we expect them to do in the future. AI can allow us to predict equipment status based on recent operations and expected logistics. This is one of the capabilities that will be available to us the soonest. Using machine learning–derived models, equipment state can be predicted if we have sufficient instrumentation providing data about not only the current performance, but also other aspects that might be predictive of future equipment performance, such as vibrations, temperature, and time since last maintenance, among others.^([22](#19_Chapter11.xhtml#rfn11_22))

## Analysis and Planning

Deliberate planning has been studied as an AI field for decades. In AI, planning is essentially reduced to a search process. If one can define actions in terms of pre-conditions and post-conditions, then one simply has to find a sequence of actions that satisfies the goal given the current state. By assigning costs or rewards to each action, one can also evaluate sequences for their expected cost or reward and pick the optimal choice. Uncertainty and nondeterminism can be included by using what are known as partially observable hidden Markov models and other related variants.^([23](#19_Chapter11.xhtml#rfn11_23))

Markov decision process models can be learned by machines using a class of machine learning (ML) techniques known as reinforcement learning, and some of the most important research in decision-making AI is being done in this area. Learned strategies in games such as chess, *Go*, Atari-style games, and even real-time strategy games that mimic command and control (such as *StarCraft* II) are increasingly being solved using reinforcement learning alone or combined with search. Therefore, if one had a suitably robust simulation of naval warfare and nearly infinite training time available, one could solve naval warfare with these methods.

But we do not have these available. We have simulations, which are necessarily simplifications of the real world, and we have limited computer time for training. But we also have human intelligence to team up with artificial agents. Humans can help prune the search, constrain the problem, and provide guidance about where to search most effectively. A strike group commander’s staff could, notionally, derive great value through the rapid development of courses of action as AI digs deep into data, patterns, and past actions at speeds and with a precision that far outpace human analysts.

When it comes to analysis and planning, it appears that human-machine teams will provide the most effective means of solving these problems. Thus, planning processes that include humans will still be useful, and the humans must still gain situational awareness from the process if they are to be full members of the team and contribute as they must. So, while rapid decision-making might be done by either humans or AI, it is likely that deliberate planning will be done by human-machine teams on a spectrum that is based on importance and urgency rather than simply a binary solution. As time available decreases relative to available human attention, decisions will move more into the rapid decision-making model. As time is available, decision-making approaches that allow more features to be examined and greater situational awareness to be developed will be used. What we will not see are doctrinally defined planning cycles. As one observer proposes: “The Navy should invest in these capabilities for tasks with rules or patterns that are predictable and difficult to disrupt, and should avoid automating tasks with rules and patterns that change unpredictably. The service should focus on collecting data efficiently, finding effective communications pathways in the absence of reliable Internet access, especially at sea, and customizing already available algorithms for naval purposes.”^([24](#19_Chapter11.xhtml#rfn11_24)) As historical examples demonstrate, the introduction of new technology accelerates the tempo at which critical command and control decisions need to be made, making this challenge all the more critical to future commanders.

## Rapid Decision-making

One way to separate decision-making approaches is by speed. Daniel Kahneman’s “Systems One and Two” make a distinction between decisions made as an automatic rapid response to a stimulus or situation, and those made through controlled, effortful, and deliberate processes.^([25](#19_Chapter11.xhtml#rfn11_25)) In tactical situations, one can easily see the need for rapid decision-making. Inbound aircraft or missiles require immediate decisions. While situations farther away from the battle space could require immediate decisions, that will often be the sign of a lack of robustness in the planning, given the time and distance necessary for large group movements.

However, ideas of tactical, operational, and strategic levels of command make very little difference to us here. The key is we want to come to an immediate decision based on a pattern of information; whether using visual, electronic, acoustic, or digital cyber clues, or some combination of these, an immediate decision must be made from the updated world view following orientation. Long-term goals may only factor slightly into these decisions, perhaps favoring one choice over another, but only because of applying some immediate input. Deliberate planning solutions by humans or machines may take too long.

Here, models developed using machine learning are strong candidates. Robots can be trained to react to a set of stimuli (for example, data from sensors) to prevent collisions in unmanned automobiles, boats, or planes. Similarly, robots can navigate through buildings for which they have no map, having been trained to navigate through other buildings. No long-term optimized planning is taking place, but the robot understands how to move through a building while heading in a perceived general direction.

At play here is a tradeoff in learning and execution time. It might take months of processing time over a large quantity of data to develop the models but, once built, the reaction time using them can be quite fast. If we know simple heuristic rules, we can still operate faster, but if we are unable to program in enough detail and robustness, learned models, perhaps in conjunction with programmed models, can provide rich decision-making and will be of use to platforms as well as command staffs.

A robot represents a system-of-systems that progresses toward some goal. The various assets being commanded by any echelon also look like a system-of-systems progressing toward a goal. The difference is that the goals at higher levels become harder to quantify, and progress is more difficult to measure. A robot moving from one space to another in a building can measure its distance from its goal in meters. Its risks are collisions, loss of power, or getting stuck or lost. A strike group has more complex objectives and more varied risks. This is why deliberate planning will still be quite difficult. But immediate reactions relative to key objectives and risks look very similar to the robot navigation problem.

## Communicating Decisions and Continuous Reassessment

By eliminating fixed cycles, we enable decisions to be made in a distributed fashion based on events rather than habit. Perhaps initial plans will exist, but they rarely survive during execution. Decisions will be communicated as often as necessary and possible. A key feature of naval warfare that will not only continue but also intensify is the need to operate under intermittent communications. C2 systems featuring AI will be continuously monitoring operations and communications in order to predict when messages will be sent or received from each unit. Decisions will need to be made with communications opportunities in mind.

Plan monitoring will become an area in which AI provides significant help to the commander. Intelligent agents will monitor the progress of every aspect of every operation and continually assess the likelihood of success. Demonstrations have already been performed with plan monitor software that, in addition to being able to make predictions about the success of plans, could in some cases repair those plans and let the decision-makers know of the repairs that were made.

But as with planning, there are different levels of assessment and repair that can be performed. At the simplest level are individual or small aggregations of sensor readings that can indicate a problem and rapid rule-based or learned decisions to solve problems. These are related to the collision avoidance discussion earlier. Another example might be that a unit is behind schedule and a simple order to speed up will solve the problem. These solutions do not take into consideration the effects on other aspects of a plan. For instance, using the extra fuel to speed up might make the overall plan fail, whereas simply changing the constraints for a later execution and communicating that to all participants might be a more optimal strategy.

Utility calculations can be made on strategies that take a more centralized problem-solving approach across a range of features. This approach has been used in autonomic frameworks such as Carnegie Mellon University’s Rainbow and has been experimented with in domains ranging from computer network defense to the C2 of a team of autonomous vehicles.^([26](#19_Chapter11.xhtml#rfn11_26)) This approach makes assumptions about the value of strategies and does not take into account that these may be too simply modeled to be appropriate. Learned strategies and learned strategy selection offer solutions to the weaknesses of utility calculations, and planning approaches similar to those discussed above for more deliberate decision-making can provide more flexibility in responses to problems.

Whatever approach is used, a key to this capability will be the ability of the AI to explain itself. This gets to the issue of trust between the operators and the AI systems, particularly for human-machine teaming scenarios: “A strength of such a human-machine teaming approach is that humans can provide the AI its purpose, goals, and some context to focus the machine’s reasoning. However, for teaming to succeed, trust must prevail. One important concept for trust in automation is a reliable, known performance envelope. Users must understand the conditions for which their system has been designed and have sufficient feedback mechanisms to determine where the system is in the performance envelope and when it is about to violate it.”^([27](#19_Chapter11.xhtml#rfn11_27))

Tracking the provenance of decision-making will be critical in C2 systems. The fact that the resulting provenance graphs can be used to generate natural language explanations will ensure that human decision-makers know what the system is doing.

## Task Management

AI researchers have long imagined that computer-based assistants would help manage a decision-maker’s effort, much as human assistants have for centuries. The Defense Advanced Research Projects Agency (DARPA) Personalized Assistant that Learns (PAL) program initiated in 2003 was not the first such effort, but it was perhaps the first that resulted in a commercial spin-off headed in this direction.^([28](#19_Chapter11.xhtml#rfn11_28)) Siri is a widely known AI-based application that attempts to provide some assistance to users. Earlier work focused on either voice recognition or providing task-based interfaces to systems designed as standard menu-based systems. With PAL, the idea that an assistant would learn about the human decision-maker and about the tasks that needed to be executed became more important than the voice recognition or engineered task models. Work by the U.S. Navy since then has begun to explore that learning further.

Task management will become an important aspect of C2 capabilities that will not only utilize AI, but also allow AI tools to be brought into use. Current prototypes in the United States and elsewhere utilize designs that include a model of the human decision-maker’s preferences, abilities, and current attention. This allows the system to suggest when the human should take on a task or when the machine might be best able to provide assistance. Much like a smart cruise control, the system can be empowered to take on tasks automatically when there is not time for a human response. Psychologists warn against under-loading human efforts as much as overloading. People need to be involved in tasks in order to maintain situational awareness and make informed decisions efficiently and effectively. Task managers will enable commanders and their staff members to engage sufficiently to maintain awareness of the tactical situation while ensuring that tasks do not languish when human attention is not available.

One of the critical problems that must be solved for task managers is the discretization of the task space. When C2 is only performed using human intelligence, the tasks themselves can remain abstract and simply known to the humans. Doctrine defines some of the tasks of C2, but not to the level of detail required for automation. PAL demonstrated that not all tasks need to be predefined. Tasks can be learned by AI agents, and interactions between computers and humans regarding those tasks can be linked to speech-based and screen-based interfaces.

As tasks are defined or learned, a model must be maintained concerning their execution. One such model allows tasks to be decomposed into alternate methods and subtasks. As multiple methods can be used to complete a task, it is possible to have several methods—ones that rely solely on human intelligence, ones that rely solely on computer-based intelligence, and ones that use a mix of the two—as options that can be selected. So that humans are ultimately in control, a feature known as a working agreement is used to indicate to the task manager what authority and responsibility it is given regarding tasks. In this way, the models of human performance can be brought together with learned tasks in order to determine if a human or AI should perform a given task at a given time.

Intelligent task managers will be enhancing the performance of commanders and their staffs as the C2 environment continues to become more complicated and time critical. They will become an integral part of the capability to make decisions, communicate them, and monitor the progress of missions. Their incorporation of models of human performance and knowledge of task execution will allow a staff to essentially include an almost limitless number of artificial staff members, ensuring that the most complex operations are executed and monitored with an extreme attention to detail and that human decision-makers are kept aware and in ultimate control of the operation.

## **THE PATH AHEAD**

Even as the conversation about—and demand for—AI evolves and grows, the Navy and Marine Corps must define what they want artificial intelligence to do, and no less when it comes to command and control. The challenge and imperative for inserting AI into naval operational constructs are well understood. Naval wargames and simulators could start considering the impact and implications of AI on command and control constructs to start gleaning operational implications. This should be considered both for near-term and longterm AI technologies, the former to start developing the “muscle memory” as new technologies come into the fore, and the latter to investigate the art of the possible. Could, for example, a small AI-enabled force match or supersede the lethality of a larger adversary? Exploring the possibilities could yield results that inform future concepts of operations, as well as investment decisions in shipbuilding, training, education, and research and development.

The Navy’s *A Design for Maintaining Maritime Superiority, Version 2.0* advances the call by directing its four-star fleet commanders to “identify five priority warfighting problems for AI/ML \[machine learning\] to address.”^([29](#19_Chapter11.xhtml#rfn11_29)) AI technologies hold promise in providing the commanders the ability to make better and faster command and control decisions than their adversaries. But these efforts will not come to fruition on their own. Focused attention and direction that prioritize investments in operational challenges are needed to ensure the Navy outpaces potential adversaries. This will drive investments by industry, as well as inform the path for the Navy’s research and development and acquisition communities. As some observers have noted, “\[T\]echnical developments in AI probably represent less than half the battle in attempting to effectively integrate AI capabilities into militaries. The real challenge now, both in the United States and abroad, is going beyond the hype and getting the right people, organizations, processes, and safeguards in place.”^([30](#19_Chapter11.xhtml#rfn11_30))

Just as the development of steam and wireless technology in the nineteenth and twentieth centuries accelerated the timeline for decision-making, so too will artificial intelligence increase the tempo at which decisions will have to be made. Future commanders must command and control forces faster than their adversaries, at speeds that might well exceed the ability of humans to make decisions on their own. Human operators without AI—or with AI inferior to that of their adversaries—will find themselves at a severe disadvantage in future conflicts. Focused investments and actions today can assure that the U. S. Navy maintains its dominance across the global commons.

### **NOTES**

# 12

AI and Integrated Fires

MICHAEL O’GARA

Such is concentration reasonably understood—not huddled together like a drove of sheep, but distributed with a regard to a common purpose, and linked together by the effectual energy of a single will.

—Alfred Thayer Mahan^([1](#20_Chapter12.xhtml#fn1))

The merit of concentration, then, in this sense, is its power of permitting us to form our mass in time at one of the greatest number of different points where mass may be required.

—Julian S. Corbett^([2](#20_Chapter12.xhtml#fn2))

**Centuries of naval conflict** have challenged commanders, and strategists such as Alfred Thayer Mahan and Julian S. Corbett, to determine the proper balance between covering the vast approaches of the maritime domain and massing forces for decisive action. For centuries, commanders have recognized the ability to orchestrate coordinated effects on the battlefield as a key attribute of victorious forces. Victory in ancient battles often went to much smaller forces that could execute a synchronized employment of infantry, archers, and cavalry, as exemplified by Alexander the Great and Hannibal. In more recent history, commanders such as Napoleon Bonaparte and Robert E. Lee were able to distribute their forces and coordinate complex movements to keep opposing forces off balance until they could deliver a concentrated attack meant to cause the maximum physical and psychological damage.

While technological advances in weapons, sensors, and communications have increased a commander’s ability to coordinate forces and deliver effects over larger areas, their adoption has driven down force size while driving up unit cost. Effectively, this has made every naval platform a high-value unit and has done little to assist the commander in determining the optimal distribution and maneuver scheme for the force. In addition to having fewer physical entities, today’s commanders must consider operations in several more dimensions than their historical peers did; they must consider maneuver and effects in space, cyber, and across the electromagnetic spectrum as well as the more traditional dimensions of sea, air, and land. The increase in domains of operation, along with a multitude of rules for engagement, have complicated the already complex calculus of coordinating forces to produce integrated effects. The art of directing actions across all these arenas is still emerging in concepts such as integrated fires, distributed maritime operations, and multidomain battle. Fortunately, emerging technological advances in artificial intelligence (AI) may provide the means to manage this increasing complexity. In this chapter, we will explore the implications of AI in helping generate desired effects in support of these integrated fires concepts.

The advent of artificial intelligence and machine learning presents much-needed opportunities to aid maritime commanders in coordinating actions across this expanded battlespace. There are several areas for discussion, many of which have already been addressed in previous chapters in this book. In regard to integrated fires, the role of AI in helping locate, identify, assess, and share potential threats supports the commander’s decisions to maneuver and engage at the pace of battle. Integrated fires itself is focused on imposing effects upon the enemy. Before discussing the use of AI in coordinating the implementation of those effects, we should first highlight some of the decision space and execution processes for delivering maritime effects.

## **ASPECTS OF NAVAL WARFARE**

In very broad terms, naval warfare thought processes differ from those of land warfare. One difference is that naval commanders operate with basic components such as destroyers, submarines, and cruisers that are roughly equivalent to battalions. There are also an increasing number of company (unmanned systems) and a few brigade (aircraft carriers, amphibious assault ships) representative platforms in their order of battle. Unlike an actual company, battalion, or brigade, however, a naval platform’s combat power is usually not degraded slowly in battle. Due to the nature of ships and antiship weapons, naval platforms typically either remain undamaged, are damaged to the point of retiring from the battle, or are sunk. It is possible to have some platforms continue to engage while degraded, but the commander must generally consider their units will survive or be lost for further action through engagement. With this reality, naval engagements have centered on a first salvo objective embodied at least since the concept of “crossing the T,” in which warships maximize the number of guns they can bear by maneuvering their broadside against the enemy’s bow. That objective is pursued today through the fielding of extended range weapons, passive sensing systems, and technologies to thwart adversary detection efforts.

Modern navies attempt to neutralize first salvo lethality by fielding sophisticated defensive systems. As a result of this, commanders seek to employ diverse weapon types delivered by multiple platforms that are synchronized in time and space to overwhelm the adversary’s defenses and ensure the effectiveness of their salvo. In maneuvering their forces for such an attack, a commander must also anticipate that by delivering fires, there is an increased likelihood the firing units will be detected and subjected to counterstrikes by the enemy. Taken together, these factors may make the employment of AI in the maritime fight somewhat more effective than in ground warfare. The reason is that predicting a ship’s chance of survival against certain threats is a simpler calculus than it might be to forecast the combat power of an infantry unit engaged and undergoing attrition over the course of a battle. Additionally, the nature of maritime hit-and-hide tactics should generally lead to a series of smaller and more manageable optimization problems for AI to consider than in protracted ground engagements. This is not to say the maritime calculus is easy, but the application of AI looks to align somewhat more easily within these maritime considerations.

Another consideration unique to naval conflict is that once forces are beyond the littorals, the vast distances between maneuvering units and supply depots create a complex logistical problem. Units that are low on ammunition, fuel, or food must retire from battle far enough to reduce the risk of losing limited replenishment vessels. Ideally, this might take as little as several hours, but it could potentially take a unit out of action for several days. Therefore, decisions regarding the use of ammunition must consider the target priority, probability of success, magazine levels, fuel state, and availability of resupply assets relative to other potential firing units as well as the overall force readiness. These factors all weigh into the commander’s decision processes for delivering effects and could present somewhat more difficult problems for AI than in a ground campaign in which units may be able to resupply while engaged. Although much of this problem space can be addressed through deliberate planning by humans, there is still an opportunity to enhance a force’s efficiency and lethality by having AI support the processing of plans for maneuver, engagement, and resupply as the campaign progresses.

## **NAVAL FIRES PROCESSES**

There are multiple processes utilized by maritime commanders depending on the mission, force structure, and time horizon, but we will concentrate on two processes utilized at the fleet maritime operations center (MOC) that center on the integration of fires.^([3](#20_Chapter12.xhtml#fn3)) In very general terms, the MOC will utilize the joint targeting cycle for offensive effects and the composite warfare commander (CWC) process for defensive fires. The joint targeting cycle is a six-phase, iterative process that methodically analyzes, prioritizes, and assigns assets against targets to create effects that will contribute to the achievement of the commander’s objectives. It integrates and synchronizes fires into operations by utilizing available joint capabilities weighed against operational priorities to create specific lethal or nonlethal effects on targets.^([4](#20_Chapter12.xhtml#fn4)) This is a deliberate and somewhat lengthy process. However, the nature of and time frame associated with maritime targeting typically require more immediate responsiveness. In this case, the commander would utilize the dynamic targeting processes that are established within the joint targeting cycle. The dynamic targeting procedures, when used to prosecute maritime targets, are often referred to as find, fix, track, target, engage, and assess.^([5](#20_Chapter12.xhtml#fn5)) This process addresses targets of opportunity that meet the criteria to achieve objectives but were not located for action earlier in the current joint targeting cycle. Due to the need to engage targets rapidly, many elements of maritime strike packages must be prearranged to assure their availability. This is particularly true if joint or cyber effects are desired. [Figure 12-1](#20_Chapter12.xhtml#fig6) depicts the phases of the joint targeting cycle.

According to the *Joint Military Operations Reference Guide*,

The Navy’s CWC Concept shares similarities with the joint force command and control construct, albeit with a more tactical focus. Under the CWC architecture, the Officer in Tactical Command (OTC) delegates command authority in tactical warfare areas to subordinate commanders within his organization. Subordinate commanders then execute assigned tasks within those warfare areas with assigned assets based on the OTC’s guidance. The CWC concept is the Navy’s C2 construct for tactical execution. This construct, though designed for tactical level maritime operations, is not unlike the construct utilized by Joint Force Commanders (JFC), who employ decentralized execution and a form of command by negation in directing the operational execution of subordinate component commanders.^([6](#20_Chapter12.xhtml#fn6))

![Figure 12-1. The Joint Targeting Cycle. Joint Publication 3-09, IV4.](images/pg223_1.png)

**Figure 12-1**. The Joint Targeting Cycle. *Joint Publication 3-09, IV4*.

Therefore, within the CWC construct, assets are in place and effects are coordinated by or between subordinate commanders. This tends toward actions that are more defensive, as the rules of engagement for protection of the force are usually clearer, thus making it easier to delegate to a subordinate commander’s discretion.

## **POTENTIAL USE OF AI IN THE FIRES PROCESS**

Having identified some of the considerations and processes utilized by the maritime commander for the employment of integrated fires, we can explore how we might exploit the use of AI to deliver more capability. We will begin by exploring the phases of the joint targeting cycle depicted in [figure 12-1](#20_Chapter12.xhtml#fig6). The initial phase establishes the commander’s objectives, guidance, and intent. In doing so, the commander will articulate the desired effects, along with time constraints, collateral effects restrictions, and acceptable levels of risk to forces. AI can readily assist the commander in calculating the probabilities of various strike packages successfully affecting a target, whether for soft or hard kill purposes. AI can also potentially support a commander in estimating the second-and third-order effects of a particular target strike. For example, AI might present estimates of how much less likely a soft kill would be in leading to an escalation of hostilities than a hard kill of a particular target. We could utilize AI to access environmental data and the operational picture in real time to calculate and present a more reliable tactical situation (TACSIT) for friendly units to assist the commander in determining the risk of counterstrikes to blue firing platforms.

With advances in AI, the commander will have the ability to build models that act as filters on unit AIs to reflect the latest guidance, rules of engagement, and intent. AI could then help distribute the commander’s intent across dispersed forces and account for forces out of contact. This would be accomplished by training the AI and establishing models to align to the commander’s attitude, decision processes, and priorities. In this way, an independent unit would receive course of action recommendations based on algorithms tuned to the latest objectives and calculus of the commander. This supports and aligns subordinate commanders whose dispersed units might only have intermittent communications with the MOC. For example, such models could bias toward aggressive kinetic action if a unit is facing imminent attack (TACSIT 1) and hold offensive weapons release authority at the MOC for a unit that appears undetected (TACSIT 3). Even more subtly, AI could learn a commander’s tendencies through exercises or wargames and apply that knowledge to advise subordinate commanders when out of contact.

The second and third phases of the targeting cycle center on target development, prioritizing, and capabilities analysis. This is performed well by humans in more deliberate planning but has the potential to overwhelm a commander in dynamic targeting due to the time constraint. AI could prove extremely helpful in dynamic capabilities analysis because of the speed at which it could assess the many variables and present prospective courses of action. If architected correctly, the AI should be aware of exactly what assets are in communication, their current offensive capabilities, mission priorities, fuel state, and relative vulnerability to counterattack. Additionally, the AI should be aware of any preapproved cyber packages that are available across the joint players.

Accessing all this information, the AI could comprehensively support the commander’s decision and force assignment in phase four of the fires cycle. AI has the potential to rapidly analyze which combinations of fires are available, tied to the associated time and position requirements for coordinated launches, while also assessing impacts to ongoing missions, adherence to commander intent, likelihood of second- and third-order effects, vulnerability to counterattack, and probability of achieving the desired results for the commander. This information could be presented to the commander in courses of action with assigned levels of confidence and timelines for execution much more rapidly and thoroughly than is currently achieved by even the most proficient staff. Leveraging similar calculations, the AI could provide the commander with real-time alerts when units are unable to participate in combined effect packages due to ranges, lost communications, low magazines, or other restraints. This would greatly assist the commander in maintaining a mutual support posture throughout a mission while feeding plans to phase five, the mission execution, of the joint fires cycle.

The combat assessment phase of the joint fires cycle can be difficult in maritime engagements, particularly those executed at extended ranges or prosecuted using nonkinetic methods. More reliable information, such as provided by electro-optical sensors, might not be available near the target or might be unable to provide images helpful in determining soft kill effectiveness. AI could likely help in two ways. First, it could assist by helping direct assessment assets into position for the commander during strike planning. Second, AI could help in analyzing multiple sensor inputs to provide a battle damage assessment. More specifically, AI could help rapidly identify variations across acoustic, electromagnetic, cyber, and visual sensors in combination with pattern analysis of adversary communication and maneuver schemes to provide a probability of achieved effects for consideration on the need to reattack a target. Throughout this process, the AI could also begin to catalogue and learn the success of various effects and combinations of effects against specified target types for future consideration in integrated fires planning.

## **POTENTIAL USE OF AI AT ENGAGEMENT SPEEDS**

The use of AI discussed throughout the joint fires cycle above employs a human-in-the-loop approach, in which suggested actions are presented but a human decision-maker must initiate those actions. Within the CWC processes, there is need to consider the employment of human-on-the-loop approaches for certain activities. In a sense, this aligns well with the CWC concept that authorizes subordinate commanders to act while the senior commanders retain the authority to negate those actions at their discretion. Because CWC processes are aligned mostly for defense of force, they are naturally more reactive than deliberate in nature. Machines are well suited for reactive responses, and defensive warfighting systems have been deployed for decades that allow for automatic responses to defined parameters (such as discussed concerning close-in weapons systems in the book’s introduction).

As with the deliberate firing cycle, correctly designing systems for the use of AI can also provide improved capabilities for integrated defensive fires. Consider the speed at which an active missile seeker can shift frequencies, a cyber-intrusion can proliferate, or a hypersonic weapon can transit an engagement window. Opportunities to counter can simply be lost when dependent on the speed of human reasoning and interaction. The complexity increases tremendously when there are multiple units supporting each other and attacks are conducted across several domain areas. Defending against such an attack can require the supporting and supported roles between warfare commanders to shift rapidly and often in response to mission priorities. Managing those shifting priorities can reach a point of failure quickly when relying on human negotiation in the midst of dynamic multidomain threats. AI holds promise in handling resource priorities across domains more seamlessly while being capable of initiating responses based on more accurate and timely threat assessments.

Since hostile intent is more readily apparent from a defensive posture, commanders should have fewer inhibitions about allowing AI to initiate hard and soft kill engagements. It is possible that in such a posture, the most favorable, and perhaps only, engagement opportunities will unfold at machine speeds. Since commanders must take all available action in defense of their force, AI must have the ability to initiate defensive actions while being monitored, though not directed, by the commander.

## **AI AND COMMANDER’S INTUITION**

In addition to the more direct application of AI to the current processes discussed above, there may be opportunity to make beneficial use of AI in enhancing the commander’s intuition. Successful commanders have had an ability to sense their opponent’s next moves and rapidly recognize shifts in momentum. Malcolm Gladwell’s book *Blink* explains how this intuition occurs in the pattern recognition of unconscious thought processes.^([7](#20_Chapter12.xhtml#fn7)) Conscious human processing is accomplished on the order of tens of bits per second. The unconscious human processing described by Gladwell, on the other hand, can operate at greater than hundreds of gigabits per second. Researchers have conducted multiple experiments demonstrating the brain becomes aware of patterns and can start modifying behavior well before a person is able to articulate any recognition of a pattern. This delay between unconscious and conscious thought is the basis of an individual’s intuition.

Often, success in battle has gone to the commander who better trusts and can act upon their intuition. Machine learning is exceptionally good at pattern recognition and can aid commanders in more rapidly understanding and trusting, or dismissing, their intuitive sense of the battle. The recognition of patterns and ability to create information and recommendations from disparate data sets can provide the commander greater insights that will produce higher confidence in selected actions. In essence, AI may be able to provide the commander a more robust, trusted, and repeatable intuition.

Such an ability need not be confined to anticipating adversary action but could also be used to reinforce or reshape impressions a commander has about subordinates. Although somewhat more controversial, this presents the possibility to see through personal biases in assessing the best commanders, units, or staff for specific missions. AI could help a commander weigh the predicted performance of individuals and units in order to accomplish an assignment based on historical performance in exercises, wargames, or previous action. Imagine the possible historical use of such a tool by Adm. William Halsey in his decision to relieve Capt. Gilbert Hoover over the *Juneau* tragedy.^([8](#20_Chapter12.xhtml#fn8)) Perhaps the AI could have presented reasons to retain him based on *Helena’s* exceptional performance in two surface night actions under Hoover’s command.^([9](#20_Chapter12.xhtml#fn9)) It is hard to estimate how the experience of this commanding officer might have influenced future surface actions, but we do know Admiral Halsey came to regret the decision to remove his most successful cruiser captain. Perhaps AI could aid the commander in avoiding regrettable decisions by helping quantify where to assign subordinate warfare commander responsibilities or task element compositions for improved delivery of effects.

## **AI AND COMMANDER’S PERSONALITY**

A related application to consider is whether AI should be tailored to support an individual commander by knowing that commander’s tendencies and considering them in deriving courses of action. An initial use may have AI designed to alert the commander when repeating patterns that are comparatively predictable in order to avoid courses of action that could be more easily anticipated and countered by an adversary. AI applied to integration of fires in this manner could help randomize the disposition of assets, sequence of emissions, or resupply patterns to enable the sustained delivery of effects while minimizing risk to blue forces.

A more difficult step would be developing AI that would take into account the personality type of the commander to make recommendations calculated to provide balance to those personal traits. In doing so, we need to consider the desirability of achieving a standard result in wargaming from every commander, contrasted with the potential deviation of results due to variance between personality types. The risk here is that the same AI that might talk Admiral Halsey out of steaming Third Fleet through Typhoon Cobra might also convince him to scratch the Doolittle raid.^([10](#20_Chapter12.xhtml#fn10))

One possible compromise would be to assign a personal AI to every individual when he or she enters the service that travels and matures with him or her throughout their career. This personal AI could be designed to interact with platform AIs through a standard application programming interface while providing a consistent human-machine interface throughout an individual’s tours of duty. Such an arrangement could build experience, trust, and confidence in the human-machine team while permitting individual variance between commander preferences, approaches, and outcomes. By being aware of these differences, an AI could theoretically advise a commander on the best combination of staff personalities to plan a mission, compose a surface action group, or defend an approach lane. The informed placement of personnel could help to optimize the coordination of effects across a campaign.

## **ALLEVIATION OF DIRECT TASKING**

To assist with unconscious thought processes, it is possible to have AI shift some activity to the equivalent of those processes for the commander and the staff. As the commander consciously maneuvers forces, AI offers the potential to ensure automated platforms provide coverage and are fueled, armed, and maintained to support changing operational tempos. Ideally, this would be done similarly to how an unconscious response to danger might produce more adrenaline, increase heartrate, and enhance sight for a person. This could include the positioning of autonomous platforms and sensors in response to maneuvers based on the commander’s intent and assessed threat, running in background and only rising to the commander for conscious consideration when there are shortages or impacts to planned operations. These unconscious processes could also include alerts to changes in TACSIT with automated changes to weapons postures and material conditions based on established guidance. Although likely difficult to achieve, alleviating a maritime staff of direct involvement in these decisions would free up more time to focus on the execution of the campaign.

## **CHANGING THE ENGAGEMENT CALCULUS**

Another indirect impact possible through the fielding of AI in integrated fires is expanding our military options. As a Western democracy, the United States puts a high value on life, which can become a constraint against adversaries who are not as sensitive to casualties. The advent of autonomous systems provides commanders the possibility for actions that might otherwise be unavailable with human assets. The destruction of Torpedo Squadron 8 at Midway was the result of uncoordinated action; however, it pulled Japanese fighter cover to low altitude. This allowed the dive-bombing squadrons to attack unmolested and with decisive effect.^([11](#20_Chapter12.xhtml#fn11)) No commander then or today would likely direct the destruction of an entire squadron unless the threat of dire national consequences compelled it. Autonomous systems can provide the commander a more acceptable calculus for taking increased risk and, as a result, provide additional options for coordinated effects. Strike packages can be constructed so that the most likely risk of counterattack is to unmanned systems. Unmanned systems could potentially be expended to buy time for manned platforms to avoid attack or maneuver for the delivery of integrated strike packages. Essentially, they can change the calculus of every maritime unit being considered a high-value unit. Additionally, the targeting of unmanned systems may decrease the risk of escalation by an adversary. This would give AI more latitude in helping the commander determine the right target types to deliver fires upon as appropriate to the circumstances.

## **REVOLUTIONARY PROCEDURAL, ORGANIZATIONAL, AND CULTURAL IMPLICATIONS**

Thus far, we have identified opportunities to leverage AI for possible improvement in performance of current processes within the existing organizational structures. It is somewhat harder to envision the possible organizational and process structures that could emerge through the proliferation of AI. Consider how command and control evolved over the history of warfare. For many centuries, command was very dependent on the personality of the leader. Individual leaders handled all aspects of command from strategic down to tactical decisions, and their staffs were generally comprised of experienced element commanders who could provide advice across all aspects of warfare. As the size of armies, range of arms, and complexities of command grew, staffs became more specialized. The innovation of the Napoleonic structure allowed commanders to focus on priority issues while being able to call on staff members with specific knowledge in studied areas when needed. In a sense, the commander used the staff as human data storage and processing devices to bin knowledge in particular warfighting specialties for easier access and more thorough analysis. In this way, the Napoleonic organization helped level the field between leaders’ abilities by helping provide commanders expert versus generalized information when needed.

Since the application of AI has the capacity to store and rapidly access data, analyze patterns, detect anomalies, and understand relationships between differing domain priorities more thoroughly than human staff officers, there may be opportunity to organize staffs in nontraditional, non-Napoleonic schemes. Perhaps, with AI providing the expert analysis, commanders can reduce staffs and return to generalists who assist the commander in a more holistic management of forces. This potential movement toward a staff of generalists that could have delegated authority across multiple specialties might shift staff focus more toward monitoring execution than deriving information for the commander. The biggest impact of such a shift would likely be upon the CWC concept. Instead of shifting supported and supporting roles between specialized subcommanders in a complex integration of fires, commanders could conceivably assign their subordinate commanders sector or regional responsibilities to manage effects across all domains.

One could speculate that continued advances in AI could eliminate the current designation of personnel within certain domains. Potentially, an officer who is a generalist supported by AI could be assigned to submarines, surface ships, and aircraft (or artillery, infantry, or motor transport roles) alternatively throughout their career. Imagine the impact on the acquisition organization if resource officers represented all domain platforms. AI could even blur or eliminate the lines between officer and enlisted sourcing, with command potential being measured in wargame and simulation performance rather than educational background. The fielding of AI that could support such cultural changes is likely far off; however, the Navy should consider some detailed analysis of potential changes and synchronize organizational and process improvements with the acquisition of enabling technology.

## **CONSIDERATIONS IN REALITY**

Up to this point, we have considered several possible uses of AI in support of integrated fires concepts. Now we need to explore the likelihood or practicality of pursuing development of those applications. The current state of integrated fires in the fleet is improving. The brittle kill chains and stovepiped acquisition programs used for decades are increasingly being replaced with more agile and lethal capabilities. The Naval Integrated Fire Control (NIFC)—Counter Air effort really pioneered the drive to work across systems commands and programs of record in a system-of-systems approach to enable greater coordination and delivery of fires. The acquisition community has taken up this initiative in developing Naval Integrated Capability Concepts (NICC) to act as requirements documents across multiple programs based on mission capability needs. The development of the NIFC Increment III NICC looks to further build agile, resilient, and lethal capabilities across fleet platforms. Investment in these efforts along with improvements to user-centered designed interfaces will provide much greater capability to maritime commanders. AI can begin to be integrated within NIFC design plans, but there are several factors to consider.

As mentioned in previous chapters, the key to implementing successful use of AI is in meticulously collecting, conditioning, and curating data that is suitable for the application. Such effort generally comprises 80 percent of most AI project development resources across industry leaders.^([12](#20_Chapter12.xhtml#fn12)) This presents two main thrust areas for the Navy: to identify what data are needed and then to make that data accessible to the applications that need it. The difficulty of these tasks can perhaps be reinforced through two anecdotes. The first involves the Results Only Work Environment (ROWE) created by Best Buy employees Jody Thompson and Cali Ressler, which has been implemented by several organizations and dictates employees are only accountable for results with no monitoring of hours or work locations.

One of the greatest difficulties in implementation has consistently been managers’ inability to identify exactly what results they need from each employee.^([13](#20_Chapter12.xhtml#fn13)) The second is personal and centers on my own experiences when assigned as a liaison to the Ninth Marine Regiment in Okinawa. The regimental commander, then-colonel Anthony Zinni, gave the staff a motivational talk about his command philosophy. He related the story of a sergeant he knew departing a tour of duty in Vietnam and waiting in Okinawa several days for his flight stateside. One day the sergeant noticed there were several curly flypaper traps hanging in the mess tent. Bored, he decided to draw out a map of the tent depicting the location of each trap and indicating how many flies were attached. He did this for several days and would deposit his drawing in the inbox of the mess tent supervisor until his flight home. Sometime the following week, the supply officer entered the mess tent upset that he had not received his fly report in days. Despite its humorous beginnings, the fly report provided some measurable information and highlighted some elements of human nature.

Identifying which metrics are really needed can be difficult within the military, as it was for the ROWE managers. We tend to want more information because we never know when we might need it. This is particularly true if we are newer to an organization that has routinely reported certain information, as we assume there must be a purpose that we may not have perceived yet. Considering the variation in organization and commander personalities across the Navy, the task of identifying what is required information, information of limited use, and unnecessary information will be difficult. The difficulty is amplified for the Navy by the current employment of disparate data formats and the operational limitations of the disconnected, intermittent, limited bandwidth environment.

Considering the current issues with data handling, the applications of broader AI for integrated fires may not be possible in the near term. The Navy will need to consider investment in the rapid implementation of a data strategy prior to heavy investment in fielding AI applications. To do otherwise is to risk returning to stovepiped systems feeding boutique AI applications that do not collaborate and confuse the commander with differing recommendations. This is not to say the Navy should avoid investment in near-term applications of AI altogether. There are opportunities for AI to assist the fleet in conducting integrated fires within existing systems. Narrower AI applications can enhance current systems used by staff members to compile, analyze, and present options for the commander, but their implementation should be standardized and well planned in relation to a system-of-system evolution.

## **POSSIBLE LIMITS**

We have examined some robust uses of more general AI in gathering information across the complexity of the integrated fires battlespace, but we need to consider the likelihood of achieving those applications. It is postulated that the human mind can operate at one thousand petaFLOPs, or one billion billion calculations per second, while drawing only the energy equivalent of powering a dim lightbulb.^([14](#20_Chapter12.xhtml#fn14)) By comparison, the IBM Summit supercomputer can operate at about two hundred petaFLOPs and cost roughly $200 million to build, covers two full basketball courts in space, requires fifteen megawatts of energy to run, and needs a flow of four thousand gallons of water per minute for cooling.^([15](#20_Chapter12.xhtml#fn15)) That is enough energy to power seven thousand homes and provide water to four hundred of them during peak usage. Those requirements may be achievable onboard naval ships and fixed shore installations, but few other military platforms will be able to meet these demands.

There is also the possibility that certain human thought processes cannot be replicated at all, as noted elsewhere throughout this book. As Wolfgang Smith questioned in his book, *Physics and Vertical Causation*, “If we knew the morphology of a living organism perfectly at a given moment of time, could we then *in principle* calculate its behavior with perfect accuracy? Or taking ‘quantum effects’ into account: can the behavior of a living entity ‘violate the laws of physics’, be they classical or quantum-theoretic? What we are asking in effect is whether a living organism is actually *more* than a physical system.”^([16](#20_Chapter12.xhtml#fn16)) If what Dr. Smith speculates is true, then there might always be some component of human thought that cannot be replicated or predicted through calculation. However, we do not need to know the potential limits of AI to begin leveraging current improvements for naval integrated fires.

And then, there is always the potential for deception and the hostile penetration of AI systems, possibilities discussed in a later chapter.

## **MOVING AHEAD**

There are functions within integrated fires that humans can perform well, and there are functions that machines can perform well. The human warfighter, across all mission areas, has been saddled with the majority of the information fusion functions to orient properly for a decision. Automation, improved user interfaces, and AI can all be applied to alleviate the burden of recalling, assembling, and analyzing information for the human operator. This will free up the operator to perform the higher-level decision-making that is not supported by the current infrastructure or is beyond current AI performance and cost considerations. AI can also begin helping tackle those defensive integrated fires issues that require human-on-the-loop operations at machine speeds due to the broader general risk acceptance. Additionally, the use of AI in autonomous vehicles can provide a meaningful amplification in combat capability and fires options in the near term.

The use of general AI to manage the complexity of multidomain fires and perform as key staff and deputy level players is likely many years away. The progress of graphene circuit boards and quantum computing technologies may accelerate and heighten these abilities, but the key will remain in building the proper foundation of accessible data. With that foundation, it is not hard to imagine an AI assistant soon capable of advising, “You may fire when you are ready, Gridley,”^([17](#20_Chapter12.xhtml#fn17)) but there is likely a great deal more to prepare before we are likely to field an AI that will generate advice like, “Damn the torpedoes! Four bells. Captain Drayton, go ahead! Jouett, full speed!”^([18](#20_Chapter12.xhtml#fn18))

## **NOTES**

# 13

Artificial Intelligence and Future Force Design

HARRISON SCHRAMM AND BRYAN CLARK

**Most discussions of artificial intelligence (AI)** in military operations focus on how AI will be used to improve existing systems and operational concepts. This is a logical approach, because capital-intensive militaries are unlikely to rapidly replace their equipment and retrain their people to take advantage of a new technology. Such an approach, however, constrains the benefits that AI could convey and could prevent a military force from gaining a prolonged advantage. Instead, militaries should evolve their force design and decision-making processes to fully exploit the agility and complexity enabled by the most promising military application of AI, which is in command and control.

This chapter consists of two parts. The first focuses on a particular method of reorganizing operational forces so as to optimize the benefits of future AI developments. The second part consists of our observations and recommendations as to the process of integrating AI applications into the U.S. military.

## **THE DECISION REVOLUTION**

Military advantages against competent nation-state adversaries are fleeting at best. This is most recently illustrated by assertions from U.S. defense leaders that the American military is losing the superior position it accrued during the “unipolar moment” following the Cold War.^([1](#21_Chapter13.xhtml#rfn13_1)) To reverse this trend, the U. S. military has been pursuing new ways of operating that would provide it a prolonged advantage against great power adversaries China and Russia—the third offset strategy, as discussed in chapter 2. During the twentieth century, new technologies such as nuclear weapons or stealth catalyzed major operational changes and U. S. military advantages.^([2](#21_Chapter13.xhtml#rfn13_2)) AI could be a similarly disruptive technology during the twenty-first century. This chapter will describe how AI might be best applied to warfare, describe key actions needed to enable this approach, and highlight potential roadblocks to its implementation.

For purposes of our discussion, we define AI consistent with the rest of this book: as a combination of programming, algorithms, and data running on computer hardware that mimics the function of the human brain and is used for tasks that were previously the sole domain of humans. Therefore, the definition of AI is naturally fluid. As chapter 8 maintains, what we would have considered AI ten years ago is not what we consider AI today. For the types of AI we consider, a key attribute is that they are “self-programming”—the system evolves when exposed to new information. AI is differentiated from natural intelligence, a term that describes the processes that actual humans use when making decisions.^([3](#21_Chapter13.xhtml#rfn13_3))

AI may be the catalyst of a new revolution in military affairs (RMA), in which innovative approaches to warfighting are combined with emerging technologies to address urgent military challenges. In contrast to evolutionary military improvements, RMAs establish new ways of measuring military performance that change the character of warfare.^([4](#21_Chapter13.xhtml#rfn13_4)) The most recent such revolutions could be considered the advent of nuclear warfare at the end of World War II and the introduction of precision strike and stealth during the late Cold War. The U. S. military pursued these revolutions during the 1950s to offset the Warsaw Pact’s numerical advantages and later in the 1980s to overcome Soviet nuclear parity. In both cases, the combination of operational concepts and technologies enabled the U.S. military to sustain an advantage for a decade or longer before Soviet forces could catch up.

One of the most urgent emerging operational challenges facing the U.S. military today is the need to conduct faster and more effective decision-making than its adversaries. Although improved decision-making is important to exploit new capabilities such as swarming autonomous systems, cyber and electronic warfare, and hypersonic weapons, decision-making superiority could also provide a way to offset the localized numerical superiority the nation’s great power competitors can achieve.

Unlike the Warsaw Pact of the Cold War, China and Russia do not individually have larger militaries than the United States. They can, however, concentrate more forces in their region than the globally deployed U.S. military. And although they share the Soviet Union’s desire to revise some elements of the international order, Chinese and Russian military operations focus on gaining influence and territory on their countries’ peripheries, rather than winning an existential competition with the United States.^([5](#21_Chapter13.xhtml#rfn13_5)) As a result, rather than convincing the Soviet military it would suffer unsustainable attrition, today’s challenge for the U. S. Department of Defense (DoD) is convincing great power adversaries that they are unlikely to be successful in a local act of aggression. This will require the ability to create uncertainty for an aggressor regarding U.S. capabilities, posture, and intentions. If conflict does arise, as evidenced by Chinese and Russian gray-zone operations, success for the U.S. military will depend less on attrition of opposing forces than on denying the enemy a path to its objective within acceptable limits of time and reputational risk.^([6](#21_Chapter13.xhtml#rfn13_6))

Preventing an adversary from reaching its objective is a goal of maneuver warfare, which seeks to impose multiple insoluble dilemmas on an adversary through a combination of tempo, mobility, and distribution.^([7](#21_Chapter13.xhtml#rfn13_7)) Maneuver warfare is a longstanding warfighting concept, but the advent of AI and autonomous systems could introduce a dramatically improved version of this approach. AI-enabled decision support systems could develop potential courses of action (COAs) that create a complex picture for an adversary to assess, maneuver forces and employ fires to impose multiple dilemmas, and plan communication and logistics schemes to enable operations to proceed. Moreover, AI-enabled control systems could allow for greater adaptability and unpredictability by quickly developing and proposing COAs a human planning staff would not consider. We could characterize this application of AI to command and control (C2) as human command with machine control.

Research and wargaming of AI-enabled warfare suggest that force design and C2 processes are the main contributors to fully exploiting the potential of AI-enabled systems.^([8](#21_Chapter13.xhtml#rfn13_8)) The remainder of this chapter will describe how force design and C2 processes should change and ways those changes could be implemented in today’s U.S. military.

## **A NEW FORCE DESIGN FOR MOSAIC WARFARE**

Realizing the full benefits of AI-enabled machine control will require changes to force design. Although AI-enabled control systems could develop COAs using today’s multimission ships, troop formations, and aircraft, the value added by AI control systems would be modest. Today’s systems are simply too expensive and few in number to be used in the wide range of combinations that an AI-enabled control system could develop. Today’s multimission platforms and units also often have to perform multiple functions in a sensor-C2-effect chain and themselves need to be protected, which would constrain the variety of force packaging options available to the AI-enabled control system.

A more disaggregated and reconfigurable force structure would enable a wider variety of potential force presentations. An AI-enabled control system could exploit the composability of a disaggregated force to create greater adaptability for the U. S. military and impose more dilemmas and complexity on an adversary, thereby increasing the opponent’s uncertainty. Because of its use of disaggregated, recomposable forces, this operational concept has been titled “mosaic warfare” in research sponsored by the Defense Advanced Research Projects Agency.^([9](#21_Chapter13.xhtml#rfn13_9))

In a mosaic force, some multifunctional aircraft or ships would be replaced by unmanned vehicles or smaller manned platforms able to perform only one or two functions. Large troop formations would be broken down into platoons or squads with less functionality and sustainability but supported by unmanned systems for sensing, protection, communication, and logistics. For example, a section of three F-35A Lightning II strike fighters could be replaced by a single F-35A as a command node accompanied by four unmanned vehicles that can be a sensor, jammer, weapons platform, or refueling aircraft. Similarly, a surface action group of two destroyers and a frigate could be replaced by a frigate and three unmanned surface vessels carrying sensors or weapons.

The U.S. Navy is taking some initial steps toward these force design features with the development of unmanned refueling aircraft, unmanned surface vessels, and unmanned undersea vehicles.^([10](#21_Chapter13.xhtml#rfn13_10)) The U.S. Army and Marine Corps are fielding unmanned ground vehicles to carry cargo and act as remote sensors or communication relays and experimenting with smaller, more distributed ground units.^([11](#21_Chapter13.xhtml#rfn13_11)) Similarly, the U.S. Air Force is developing a “loyal wingman” aircraft that could operate under the command of a nearby pilot to conduct higher risk operations or provide additional sensor or weapon capacity.^([12](#21_Chapter13.xhtml#rfn13_12)) We argue that these efforts should be accelerated with large, multimission units being part of the trade-space used to pay for them.^([13](#21_Chapter13.xhtml#rfn13_13))

Autonomous systems will be an essential component of a force executing a concept such as mosaic warfare. Disaggregating the capabilities and functions of monolithic multimission platforms and troop formations into a larger number of less expensive units will depend on autonomous controls that reduce the number of operators required or enable the unit to be completely unmanned. Autonomous controls can be AI-enabled, but they do not need to be.

The most significant limiting factor in evolving the U.S. military’s force design is that law, regulations, and the practical requirements of manning, training, and equipping preclude DoD from starting with a blank slate to create a mosaic force. And while the technologies for more disaggregated, increasingly autonomous military platforms and systems already exist, the U.S. military will continue to need large, multifunctional platforms and troop formations for peacetime and deterrence operations requiring endurance and predictability. Moreover, the funding to develop and field mosaic forces will be constrained by the need to sustain traditional military units and cover increasing personnel and maintenance costs.

Implementing a mosaic force design can be done incrementally. In recent wargaming, we found that a 10 percent shift in DoD procurement funding toward more disaggregated capabilities was sufficient to enable complex operations by highly reconfigurable forces. For this modest shift in force design to yield the most benefit, DoD needs to co-develop C2 processes that can operate a more disaggregated force and to pursue a new innovation strategy that focuses less on gaps in the ability of today’s force to operate as desired and more on how the future force could perform better with new capabilities that may create novel ways of operating. These changes are discussed further below.

## **HUMAN COMMAND AND MACHINE CONTROL**

Disaggregation and distribution are already being applied in several emerging DoD operational concepts, such as distributed maritime operations and multidomain operations. Yet the impact of these concepts will be constrained by today’s human-centric C2 processes. A commander and a planning staff will likely be unable to exploit the ability of a highly disaggregated force to create complexity and uncertainty for an adversary because they will lack the time or modeling and simulation capability to consider and assess nontraditional force packages or novel tactics and operational approaches. By combining human command with AI-enabled machine control, however, a small number of personnel could manage a large, adaptable, and complex force in fully exploiting the potential of maneuver warfare.

There are several ways AI can support C2, but one straightforward method is to use an auction and bid process similar to ride-hailing applications such as Uber and Lyft.^([14](#21_Chapter13.xhtml#rfn13_14)) In this approach, the commander would publish or broadcast tasks to be done, including constraints, priorities, metrics, and objectives. The capabilities under the commander’s purview would bid on the tasks in whole or part based on their ability. A distributed AI-enabled control system would award winning bids to a force package that could execute the tasking and direct the relevant forces to initiate the operation. Under this mechanism, participating platforms would report their results when communications availability allows and could also report anomalous findings such as an expected enemy system being out of place. The commander can decide, or have predetermined, if he or she wants the AI-enabled control scheme to execute a new “play” in response to anomalous findings.

An important benefit of using machine control is that it enables C2 architectures to adapt to communications availability, rather than DoD having to invest in robust communications infrastructure to support a “one-size-fits-all” C2 hierarchy. Under the concept of mission command as discussed in chapter 7, if communications between higher commanders and subordinates are lost, subordinates are expected to take charge of their forces and use their own initiative to accomplish objectives in accordance with their higher commander’s intent. Yet the results of mission command may be dependent on the ability of a junior leader, who may not have a planning staff, to develop and execute operations. This becomes more problematic in a situation where speed and highly complex decision-making (and experience) are needed to ensure success. By combining human command and machine control, however, junior leaders can manage their forces with minimal support and effectively conduct maneuver warfare. Moreover, AI-enabled control systems would enable learning to be applied from previous operations, freeing junior commanders from some of the administrative burden in preparing for the next operation.

## **EMBRACING AI**

With difficulty, today’s DoD and government planning and decision processes might be able to implement AI-enabled C2 and new warfighting concepts centered on decision-making. However, to more quickly establish the conditions for a military revolution centered on decision superiority, DoD should reform how it develops new capabilities, recruits and trains personnel, and assesses and funds programs. All of these are elements of overall future force design. These changes will need to address a significant difference between the coming decision-centric RMA and the two most recent ones. Today, the civilian industrial base has parity with, and in some cases leads, government initiatives. The government will need to improve its ability to bring civilian expertise and technology into government programs.

Integrating AI into U.S. military C2 will be potentially its most challenging application. To work up to the required level of confidence and proficiency with AI-enabled systems, DoD should choose a subset of problems that have low operational risk but are amenable to AI because they involve subjects that are relatively well-bounded and have rich data sets that can be mined for insights. The following areas should be pursued as pilot projects for the military services to consider to gain knowledge, both institutionally and individually in AI:

•  Safety data. The services may use AI, machine learning, and advanced analytics to understand the implications and so-called weak signals in data currently collected for safety analysis. The services writ large have a robust data collection effort with years of history, particularly for aviation. There also appears to be a potential for AI-enabled analysis of surface ship operational practices and safety.^([15](#21_Chapter13.xhtml#rfn13_15))

•  Permanent change-of-station (PCS) moves. DoD currently spends billions of dollars a year on PCS moves that impact the lives and families of nearly every servicemember. An AI-enabled control system like that of today’s ride-sharing or food-delivery applications could improve the planning or conduct of moves, or machine learning could be employed to analyze previous or planned moves to identify efficiencies in transporting servicemembers’ household items. At face value, this does not seem to be a force design issue, but it has great impact on the recruiting and retention of personnel with high-tech skills. The notion of turning over routine tasks that impact servicemembers at home should be considered a litmus test on the maturity of AI; if you aren’t willing to trust AI with your pay or movers, perhaps it isn’t ready to be trusted with integrated air and missile defense.

Both of the aforementioned examples would take AI away from being a buzzword that is simultaneously all-powerful and terrifying and turn it into an actionable “thing” that the services can put to use. And that is its rightful place—as a tool for solving problems, not as an end unto itself.

## **SHIFTING FROM CAPABILITY REQUIREMENTS TO OPPORTUNITIES**

Current DoD program development efforts follow a gap-driven requirements process that is well suited for attrition warfare using highly engineered systems-of-systems (SoS). In a gap-driven requirements process, problems are identified based on the current or expected way of operating planned SoS against a projected adversary in a notional scenario. Gap-driven requirements reflect numerous assumptions and drive capability development toward a point solution. As a result, the requirements process could often demand a solution that will be obsolete when it arrives.

In contrast, a force operating under an AI-enabled control scheme will not have gaps, per se, because it will attempt to compose itself to conduct tasks in accordance with the commander’s direction. A lack of capability will tend to manifest itself as the force package completing tasks in ways the commander does not want, rather than the force package being unable to complete a task. The program development process in a decision-centric warfighting approach should therefore look for opportunities to improve the capability of likely force packages through useful emergent behavior, rather than simply filling gaps in current or planned SoS and tactics. By useful emergent behavior, we mean systems addressing threats or challenges autonomously or semi-autonomously in ways that were not part of the initial design of the force package.

Developing new capabilities that do not service identified gaps will require a new process for DoD research and development (R&D). One such approach is opportunity-based innovation. In this R&D process, the need for new capabilities and concepts would be introduced via open-ended requests for proposals, similar to a broad area announcement. However, rather than targeting an already-defined gap or program need as in today’s broad area announcement, future requests for proposals would be to support overarching missions or concepts.^([16](#21_Chapter13.xhtml#rfn13_16))

In this model, opportunities or ideas would continue to be proposed by innovators. However, instead of shepherding the development of specific opportunities into a demonstration or deliverable, program managers would focus on evaluating new opportunities through challenges that quickly discard unfruitful opportunities and retain those with promise. Before significant development work is started, the challenge process could determine through experimentation or simulation whether the new opportunity can create useful emergent capabilities in the force packages it is likely to be part of during operations. Overall, this approach would shift more of the expenses of technical development from before to after an opportunity is assessed as being useful. In today’s model, a capability is designed and developed to fill a gap, after which operators and testers assess whether it is useful.

An opportunity-based R&D approach could also improve DoD’s ability to compete with great power adversaries compared to traditional requirements-driven R&D. Great power adversaries study U.S. military capabilities and research priorities and have likely assessed the potential results. By not starting with current or planned SoS and tactics, opportunity-based innovation would naturally identify how new, potential disruptive technologies and revolutionary concepts could change the way U. S. forces operate. This may afford the U.S. military an advantage relative to other great powers by reducing their ability to predict future U.S. force development efforts.

Open standards, or infrastructures that all developers can contribute to, will be important to enabling opportunity-based innovation. Software development is a particularly relevant example because it is central to a growing number of military systems. Currently, DoD uses significant numbers of computing systems for which it does not own the source code or data rights. This is in sharp contrast to open-source computing architectures used in the commercial world, such as R and Python. To promote innovation and reduce the ability of vendors to lock themselves into a program through proprietary software, DoD has been adopting various forms of government-managed open standards and in some cases is using public open standards.

New ways to develop and pay for software would be enabled by open standards or the government buying data rights to source code for new military systems. Commercial software production is moving toward the developmental operations, or DevOps, model in which software is purchased as a service rather than a product. In the DevOps model, software is created by cross-disciplinary teams to support operator needs in consultation with engineers, who then test and use software and inform continuous improvement efforts by software developers. Using DevOps, AI algorithms and the models they produce would not be “completed,” per se, but instead would continuously improve.

Most importantly, opportunity-based innovation will depend on forward compatibility, which is the ability to integrate components that have not been designed or, in some cases, even conceived. The forward compatibility afforded by open standards and DevOps may be more expensive than current approaches to system development because they incorporate a capacity for future changes that is not used today. Forward compatibility is essentially an investment option on future operations and does not by itself pay any of today’s bills. In a time of competing priorities, this option may be incorrectly perceived as a luxury that can be sacrificed to pay for more military hardware.

## **CREATING BETTER AI USERS AND CONSUMERS**

DoD, as well as the rest of society, needs to make a choice with regard to implementing AI-enabled systems: Are we educating AI’s masters, or are we training its servants? It is ironic perhaps that the most important element of fielding and employing better thinking machines is to develop better thinking humans. Today, DoD is potentially conducting a dangerous experiment; it is encouraging and increasing investment in AI, while simultaneously reducing the number and quality of personnel with the skills and aptitude to fully understand AI at a sufficient level of detail to be able to diagnose and, if necessary, retrain algorithms in situ. The following chapter discusses education in AI at the U.S. Naval Academy, but we remain unconvinced that DoD overall is sufficiently committed to recruiting and training “coding-capable” forces.

It is possible that the ability to rapidly and effectively author and adapt code will become as critical a “warfighting skill” as the ability to fire a rifle or pilot an aircraft. In order to effectively build this force, the military services will need to find ways to compete for personnel with technical giants that dominate investment in software creation. The challenge of recruiting servicemembers with the potential for managing AI-enabled systems is exacerbated by the shrinking population of American high school and college students with the physical and psychological aptitude and background for military service.^([17](#21_Chapter13.xhtml#rfn13_17))

In addition to recruiting new personnel with the right skills, the U. S. military needs to find and incentivize junior leaders and give them the space to introduce better technical capabilities—including, but not limited to, AI. One prerequisite that can be done now is to try to loosen up, where practical, overly restrictive information technology policies. Most people working in DoD only have access to the Microsoft Office suite of applications. Microsoft has done an excellent job creating the analytic equivalent of a Swiss army knife—light, easy to use, lots of applications. Having said this, one would not want to build a house with a Leatherman tool, and the services would do well to allow forward-leaning technically inclined members to have access to open-source computing environments, such as R and Python. The speed of advance in these computing languages and libraries vastly outstrips anything that is within DoD’s current information technology framework. Gaining knowledge and experience in these systems in an everyday, noncombat situation is a prerequisite to success.

DoD should also begin putting AI-like programs into the hands of more servicemembers for them to use in the conduct of their daily jobs, such as in predictive logistics and maintenance, target recognition, training, and COA development. While this will not, as previously noted, appear at first directly impactful on warfighting effectiveness, it will serve a critical function as personnel will gain institutional knowledge of how AI-enabled systems work.

One feature of an AI-enabled RMA that is different from previous revolutions is that innovation will be driven as much from the force as it is from the research and acquisition communities. This is perhaps the most novel feature of an AI-enabled revolution; innovation across the force will come from the bottom up, as chapter 6 ably explains. In the coming AI revolution, with large technological solutions being pushed down from the senior ranks and innovation bubbling up from the junior ranks, the key element of the workforce will be field grade officers in the O-4/O-5 paygrades. The field grades who will be serving at the height of the AI revolution are the lieutenants and ensigns who are in service today.

## **HOW TO AVOID FAILING AT AI**

Although C2 appears to be the most promising application of AI for military operations, fully realizing its potential will likely take decades, and the path to its implementation is not completely clear. Many other applications of AI are also promising and might be useful stepping stones toward achieving human command with machine control.

When one is unsure of which direction to go, it is sometimes useful to identify the direction that you do not want to go and travel away from it. With that technique in mind, DoD should pursue the following approaches:

•  Do not ask for an AI-enabled solution without first deciding what decision it will influence and what the “left and right limits” of the decision will be. Engineers are generally interested in elegant solutions to problems. However, elegance is not necessarily the correct metric when applying AI because its value is in proposing solutions that address numerous objectives simultaneously. The resulting solution might not appear to be the simplest one, but it might be the best one depending on the metrics the AI-enabled system was asked to pursue. Because other problems might not require an AI-enabled approach, we should also consider other analytic techniques and methods to solve problems.^([18](#21_Chapter13.xhtml#rfn13_18))

•  Do not assume the machine will get it right the first time out of the box. There will be many failures on the way. It is expected that approximately 15 percent of AI projects are successful in the sense that they reach the objectives laid out in the initial project.^([19](#21_Chapter13.xhtml#rfn13_19)) Toward this goal, there needs to be a strong differentiation between technical risk and management risk. Management risk is the possibility that a project fails because of process problems such as cost overruns and schedule delays. Technical risk is indicative of projects that might not work because the science does not exist at the outset, and there is no guarantee that it will be discovered during the course of the effort. The types of efforts we are discussing in this book are cutting-edge and of high technical risk. Technical risk can be addressed through research and experiments of simulations challenging the utility and validity of a new opportunity. Managerial risk should be managed by first understanding the level of technical risk and then assessing the ability of the organization to deliver the intended results. If technical risk is not clearly separated from management risk, researchers could be discouraged from pursuing innovative AI research due to the inability to effectively manage management risk.

•  Do not assume that all tactical and operational problems can be solved with AI. They cannot be. Large data-centric web merchants such as Amazon are very good at drawing inferences on what people may be interested in purchasing on a given evening because they have a functionally infinite sample space of previous actions upon which to build the model. This is radically different from military problems where the amount of data on previous interactions is extremely small and the adversary might have tactics and systems that have not been observed previously. Making inference where there is little to no data is the domain of natural intelligence.

•  Do not partition the force into AI and non-AI, making servicemembers who develop and employ AI-enabled systems a separate category from those who are developing and operating non–AI-enabled systems. This would be analogous to making a distinction between pilots, who fly aircraft and manipulate levers and switches, with infantrymen, who are on the field firing weapons. This is a distinction without a difference; the “switches” the pilots manipulate are connected directly to the aircraft’s weapons systems and can produce the same effects as the infantryman’s.

## **CONCLUSION**

Harnessing the potential of AI in military operations will require more than simply trying to integrate AI into every military system. Coupled with evolutionary changes to force design, AI-enabled C2 could enable a new revolution in military affairs that would provide the first mover a significant and prolonged advantage. Realizing that advantage will require changes to how DoD develops military capabilities, recruits and trains its personnel, and sustains the force once it is fielded. Without these reforms, however, the U.S. military could find itself “offset” by its great power competitors.

### **NOTES**

# 14

Entry Pass to Future Warfare

**AI Education at the U.S. Naval Academy**

NATHANAEL CHAMBERS, FREDERICK L. CRABBE, AND GAVIN TAYLOR

**Early one morning in April**, a midshipman contacted her professor to inform him that her hallway-monitoring device was confiscated by the staff at Bancroft Hall, the sprawling dormitory that serves as the home of the brigade of midshipmen. The device was a small computer about the size of one’s hand with a golf ball–sized motion sensor. She had been working on this custom-built device with her computer science capstone team all year. They purchased the tiny computer (a Raspberry Pi) with their own money and placed the sensor in the hallway outside the barber shop in Bancroft, tucked under a chair out of the way, complete with a note about their capstone project. Above on the ceiling was a live webcam that Bancroft broadcasts to the brigade so midshipmen can see how long the wait is for a haircut, one of those routine necessities for midshipman life.

This particular capstone team was given permission to use the webcam feed, and they had programmed a neural network to visually count people in the video; in the event of poor lighting, the motion sensor would contribute more accurate statistics. The goal was to build an AI system that used these statistics to characterize the movement of the brigade population through the barber shop and predict the best times to visit. Unfortunately, the security staff, uncomfortable about the sensors often necessary for AI, had intervened. Unfamiliar devices with “open circuits” need to be vetted.

The Bancroft Hall staff personnel were just doing their jobs, and the midshipmen should have asked for more permission. However, what ensued from this confiscation illustrates the broader need for and challenge to AI education at the U.S. Naval Academy (USNA). Multiple officers and chief petty officers in Bancroft didn’t understand the project and were annoyed at the students; one of them threw the team out of his office when they arrived to get it back. It was eventually revealed that someone thought the device was dangerous (it was not), that one might get electrocuted (you cannot), and that they didn’t personally ask for his permission (this was true).^([1](#22_Chapter14.xhtml#rfn14_1)) What background do our future officers need to approach and understand technology like this? Sensors are a basic component of AI technology, yet this small sensor with an explanatory note caused a stir. While the Naval Academy is well known for its science, technology, engineering, and mathematics (STEM) prowess, AI itself is progressing fast enough that unfamiliarity with the techniques and technology might cause an unfortunate disconnect between an incredibly powerful technology and a distrustful community that must use it effectively.

What is the Naval Academy doing in terms of teaching artificial intelligence? What aspects of its STEM courses are relevant? What does the average midshipman learn regardless of their major choice? If midshipmen want to engage more deeply in AI, what curriculum and research opportunities are available to them? This chapter strives to answer these questions and include examples of how the academy is leading the charge for a deeper and broader AI education. In essence, it is a case study of one aspect of the Navy’s overall education and training efforts in AI. The chapter begins with a survey of core requirements and their relevance to AI, then discusses ways that different majors are introducing AI, with a special focus on the computer science department and its new AI and data science track.

## **CORE STEM REQUIREMENTS AT THE NAVAL ACADEMY**

All incoming students to the Naval Academy are required to take a set of core courses that include such topics as leadership, ethics, and navigation, several of which are unavailable at most liberal arts colleges.^([2](#22_Chapter14.xhtml#rfn14_2)) The largest set of courses in this core are what people usually refer to as STEM courses, and they are largely what makes the Naval Academy known for being a STEM-focused college. High school applicants often mention the STEM emphasis as an attractive quality. But what are these courses, and do they prepare midshipmen to engage with AI?

**Table 14-1. Course Requirements**

 
| Chemistry || Two semesters |
| --- | --- |
| Cyber Studies || Two semesters of computer security |
| Electrical Engineering || One semester of introductory electrical engineering |
| Systems Control || One course plus lab of weapons systems and control engineering |
| Mathematics || Three semesters of calculus plus one semester of further study specific to major |
| Physics || Two semesters |

## Physical Sciences

The core curriculum for each midshipman is quite broad. The physical sciences aspect that our future officers require is well covered by physics, chemistry, electrical engineering, and systems. While important to a naval education, these are not particularly relevant to AI; the core of AI is intelligence and software, even in domains such as robotics, which may be included in the above courses. Understanding software and where intelligent decision-making comes from in a computer does not flow easily from the education provided by this core.

## Electrical Engineering

Electrical engineering (EE) is often grouped with its sibling of computer engineering (CE), which in turn is connected to computer science (CS). These lie on a spectrum from electricity to computing chips to software: EE–CE–CS. This suggests that exposure to EE may be helpful in understanding the workings of a computer, but understanding software and AI as intelligent behavior is several steps of abstraction removed from understanding the flow of electrons. The reality is that most experts in artificial intelligence (including the authors of this chapter) know very little about EE.

## Math

Calculus makes up the bulk of the core curriculum. The calculus track provides a solid foundation for midshipmen to think mathematically, but most of the course topics are not directly relevant to AI. Two exceptions to this are derivatives and vector operations. Readers might recall from their own education that a derivative is how we measure the slope (rate of change) of a function. It turns out that this is fundamental to many machine learning (ML) applications, an automatic method to analyze changing environments. However, even derivatives don’t provide insight per se into the capabilities of AI algorithms. They are a prerequisite for students who will do a deep dive into AI, but knowing how to take a derivative doesn’t itself give the student insight into the capabilities of intelligent AI systems. Perhaps in contrast to derivatives, one of the more important topics to understanding AI is probability and discrete structures (sets, graphs, logic). However, despite four required courses in mathematics at the academy, most students do not encounter these topics. A few majors do substitute probability into the fourth course of this sequence, but these are in the minority and not part of the general midshipman education.

## Cyber Courses

Finally, we come to the cyber studies two-course sequence. A mystique has formed around the term “cyber” where people might think it covers anything related to technology and computers. In reality, there are two semesters of content, and they focus on specific topics about security of systems. Most important to any understanding of artificial intelligence, computer programming is mostly absent from its curriculum.^([3](#22_Chapter14.xhtml#rfn14_3)) The two courses introduce topics of policy, networks, authentication, basic hardware, signals, encryption, and the varied avenues from which people exploit these for attacks and defense. The material is multidisciplinary as well, devoting weeks to international relations and policy. There are case studies of breaches, security policy, and discussions of the motivation behind attacks. These are important subjects but are not directly relevant to AI and data science.

The two cyber courses are split between a more high-level application and lower-level electronic signals understanding, although overlap does exist. The first course spends more of its time on the web, networks, encryption, and attacks along those vectors. The second course is more engineering-focused with topics on electronic signals, data transmission, antenna theory, and frequency hopping. Successful students finish with a broad outlook of the cyber battlefield, what tools are available, what entities are acting, and where systems might be vulnerable. It’s important to note that these courses dip their toes into many diverse security topics. The Naval Academy is graduating midshipmen with a broad view of the many threats that abound around our computer systems; however, these threats are orthogonal to an understanding of AI.

## **A TASTE OF ARTIFICIAL INTELLIGENCE**

AI and data science require a different toolkit than what is currently covered in the STEM core. Even the two cyber courses are quite different than what is needed, and the understanding of what an AI system can (and, more importantly, cannot) do requires a different background. Looking at it all from a bird’s-eye view, while the core curriculum’s topics are not directly relevant to AI, they do provide the midshipmen with the tools that, in our estimation, a good education should always foster: critical thought, mathematical reasoning, and an introduction to general computer technology.

This leads us to what the USNA is doing for midshipmen who want to understand AI and take a deeper look into the material. What opportunities does a future AI warfighter have?

As the influence and importance of AI grow, the tools available to nonexperts become easier to use. We now see such AI tools springing up across the Naval Academy grounds, for example, with the use of machine learning to model the propagation of a laser beam in low altitude, or neural networks to find the ground state of multicomponent Bose-Einstein condensates.^([4](#22_Chapter14.xhtml#rfn14_4)) Most of these applications are giving students but a taste; they are being taught to use AI and ML as tools to solve engineering or scientific problems. These tools highlight the maturity of AI systems, but intelligent application of these tools sometimes requires a deeper understanding of the mechanisms underlying them. To address this, several departments have begun formal instruction in specific elements of AI and ML. They’ve also entered into collaborative engagements with the computer science department. As we’ll describe later, the deepest dive into AI mastery is primarily in the computer science department.

The two main departments with courses dipping into AI are the mathematics department and the weapons, robotics, and control engineering (WRCE) department.

## Mathematics

The mathematics department began offering two courses emphasizing the data science elements of machine learning in 2018. The first course, “Introduction to Data Science,” is targeted at mid-program undergraduates. It is based on the “Data 8” course developed at the University of California Berkeley and uses the free online textbook *Computational and Inferential Thinking: The* *Foundations of Data Science*.^([5](#22_Chapter14.xhtml#rfn14_5)) Since the course has no computational prerequisites and relies on a popular library in Python, it begins with a crash course in Python programming and the use of this library.^([6](#22_Chapter14.xhtml#rfn14_6)) The remainder of the course looks at building models and sampling data to learn and reinforce statistical concepts such as Bayes’ rule.^([7](#22_Chapter14.xhtml#rfn14_7)) A follow-on course is currently under design with a new textbook with more mathematical rigor.

The other new course is called “Machine Learning and Artificial Intelligence,” loosely based on a Coursera machine learning course.^([8](#22_Chapter14.xhtml#rfn14_8)) With programming done in MATLAB, the course covers regression, gradient descent, neural networks (NN), and kernel approaches, as well as ethical implications of machine learning.^([9](#22_Chapter14.xhtml#rfn14_9))

## Weapons, Robotics, and Control Engineering

The WRCE department currently offers “Deep Learning: The Truth Behind the Hype,” a one-credit course focusing on demystifying deep learning and explaining what factors have led to the explosion of interest in our current era. It traced the history of boom and bust cycles in AI, how the availability of vast data sets affects ML and NN, and recent directions in hardware development, such as graphics processing units (GPUs). The creators are working to develop the course into a three-credit version. Elsewhere in the department, ML can be seen as a tool for solving applications, such as the use of deep neural networks in the machine vision course.

Finally, several faculty members in WRCE have been collaborating with peers in computer science on two sponsored competitions that involved a combination of engineering and AI. The first, the Service Academy Swarm Challenge (SASC), was a Defense Advanced Research Projects Agency (DARPA)–sponsored project that pitted the Naval Academy, Air Force Academy, and West Point against each other in drone swarm aerial (simulated) combat in the spring of 2017. DARPA provided each academy with a mixed fleet of fixed-wing and multirotor platforms with the goal of developing innovative offensive and defensive tactics. The USNA team consisted of both faculty and students from WRCE and computer science. The CS students focused on developing and evaluating the AI behaviors for the tactics. Each tactic could be activated on any or all of the drones by ground control at any time. Navy won the competition.

Currently, the Office of Naval Research is running the Squad with Autonomous Teammates competition (SWAT-C) between Navy and Army. The purpose of the competition is to integrate autonomous systems into squad teams. As with SASC, this is a collaboration between WRCE and computer science, with the CS team developing the vision and tracking systems and the search algorithms, as well as the integration of the various AI components. The final competition for the current SWAT-C will be held in the spring of 2021.

## **A DEEPER DIVE INTO ARTIFICIAL INTELLIGENCE**

The deepest dive into AI material is offered by the computer science department. Due to recent innovations and new courses, we focus here on how this department is training future officers for an AI world. The department recently revamped its entire AI curriculum to address these new needs.

The goal is to produce students who can make effective use of AI tools and understand the underlying technology but also to create AI solutions to new problems—in other words, to develop officers who are able to design AI applications for specific operational tasks. This is done through four components, some compulsory and some optional, in addition to the core computer science curriculum. The first component is a new elective track in AI and data science, in which students can choose to focus their major electives on a sequence that leads to a deep understanding of AI. The second is the capstone program, in which teams of computer science majors must produce a large-scale project of their choice that demonstrates their capabilities at the end of their undergraduate education. Frequently, interested students make this project AI-centric. The third is a large number of summer internships, which give participating midshipmen opportunities to engage with practical problems requiring AI and data science. Finally, faculty who are experts in AI offer research experience to particularly capable and interested students. We will describe each of these in more detail to showcase what we believe is an effective strategy for teaching AI to the computationally minded while fully engaging students of all ability levels and interests.

## **A CORE CURRICULUM IN COMPUTER SCIENCE**

The required courses in the computer science major are intended to teach practical computational skills as well as the analytical skills required to develop and evaluate solutions to computational problems. These sets of skills are prerequisites for graduates to create and deploy AI solutions during their careers. We will start by describing a typical computer science major.

The computer science major consists of twelve required courses and three electives. It is not dissimilar from what one typically finds at any major university, but with the added benefit of allowing a deep focus on AI. The first year of the major usually involves four classes providing practical experience in increasingly complex programming projects in C++, C, Java, Python, and MIPS computer languages, and in a variety of programming paradigms. Students become accomplished at breaking down complex problems into simpler ones and at making the computer perform the computations they want. After this first year in the major, the student will then be able to focus on what the computer should be doing in order to be useful, not on how to make the computer do it.

The second and third years become a mix of courses that require students to either build a working computer system or expand their analytical and problem-solving abilities so they can develop solutions to difficult computing problems. These practical courses cover the workings of computer networks, the workings of compilers, the wide variety of features available in different programming languages, and the techniques used by an operating system to manage the workload of an entire computer.

The analytical courses develop a student’s ability to create solutions and analyze those solutions in a quantitative and well-structured way. They include a two-course sequence in producing and analyzing algorithms that perform tasks quickly and efficiently, examining different perspectives on computer behavior, and developing solutions of their own through these frameworks. This sequence is critical to their future understanding of the potential and, more importantly, the limits of AI algorithms.

Through exposure to these classes, students become adept at interacting with computers and writing programs that accomplish tasks without bugs, but also at solving problems and understanding the quality of their solutions. This combination of practical and logical ability grounds students for further study in AI.

## **DEEP AND THOROUGH AI EDUCATION: AN ELECTIVE TRACK**

The computer science major requires students to choose three electives to expand the skills learned in the core curriculum. As part of this, the department is offering a new “AI and data science” elective track to allow interested students to dedicate their efforts in depth to AI. To earn recognition for this concentration, students must take a foundational course on artificial intelligence, and then two from the choices of natural language processing, intelligent robotics, high-performance computing, or machine learning and data science. This track has received a lot of student interest, and we expect a great deal of participation.

At the core of this track is the AI course. By requiring all AI-interested students to take a common course as a foundation of knowledge, fundamental techniques do not have to be taught from scratch in the other courses. Brief details of each of these courses provide a sense of our goals for the track.

Artificial intelligence is the foundation course for the track, with a prerequisite that students have completed a course on data structures (usually meaning they have been in the major for three semesters). This course has run for several years but has been restructured to provide the foundational understanding required by the other courses. Topics are varied and include reasoning via graph search, game playing, reinforcement learning, Bayesian inference and Bayes nets, perceptrons, and natural language processing. Necessarily, many of these topics are mere introductions, but they provide an awareness of the field and techniques as a whole, as well as a reintroduction to mathematical concepts such as basic linear algebra and Bayesian probability, which are used heavily by other courses in the track.

Natural language processing is the study of how computers can understand and produce human languages (e.g., English, Chinese, etc.). Language is fundamental to what it means to be a human, and this course is an important piece of the AI puzzle on the path to human-level intelligence from our machines. It is a heavy machine learning course with algorithms that can learn from large amounts of text and that ease communication between human and machine. Some topics covered in the class include author identification, information retrieval from social media, email filtering, and sentiment analysis.

Intelligent robotics is a lab-based class in which students use AI techniques to extract intelligent decision-making and behavior from physical robots. The course builds from mechanical to abstract; it starts at kinematics, then moves to perception and sensing, including computer vision, then localization and mapping, then navigation, action selection, and finally learning. Throughout, students must demonstrate these behaviors by programming robots to accomplish tasks autonomously and intelligently.

High-performance computing teaches students how to use very fast parallel computers to accomplish a large amount of computation or process a large amount of data, a key and frequently overlooked component of training many modern AI systems. The course begins with an understanding of supercomputer architecture and then moves on to several common parallel programming paradigms, appropriate for different architectures. These include message passing interface, OpenMP, and CUDA.^([10](#22_Chapter14.xhtml#rfn14_10)) The goal is to prepare students to take the AI techniques they learn in other classes and scale them up to solve bigger, more computationally expensive problems. Course projects are conducted on the Naval Academy’s own Cray supercomputer.

Finally, the machine learning and data science course covers the science of understanding, and making predictions based on, large amounts of data. Topics include clustering, dimensionality reduction, recommendation systems, regression, and classification. The focus of the course is on understanding machine learning from a mathematical standpoint, focusing on concepts such as over-fitting or feature selection rather than on chasing the latest machine learning fads (of which there are many!). Again, projects are completed on the Naval Academy’s own high-performance computing systems, including the Cray supercomputer and GPU machines.

As a group, these courses provide a thorough curriculum to technically competent students, resulting in graduates who are capable of understanding, using, and creating AI for a variety of applications and contexts.

## **CREATIVE APPLICATION OF AI: CAPSTONE PROJECTS**

The U.S. Naval Academy requires that every graduate produce a capstone project of substantial size using knowledge from their major. In the computer science department, this takes the form of a year-long group project, chosen by the group itself and approved and advised by faculty members. In recent years, as the students have become more interested in AI, more have begun incorporating AI into their capstones. Our broader push is to encourage students who take the AI elective track to also propose an AI capstone. In fact, among the most recent graduating class, six of thirteen projects contained AI. Projects were extremely varied. They included:

•  a one-shot facial recognition system for automatic midshipman mustering

•  object and person recognition to characterize the ways a population used a space in order to detect anomalies

•  an Internet-of-Things device able to learn proper scenarios for detonating an explosive device

•  a system able to detect adversarial advertising campaigns, such as a foreign country’s attempts to influence elections on Facebook

•  a life-expectancy predictor given medical data and proposed treatments in cancer patients

•  an autonomous drone able to provide reconnaissance information for human ground forces.

These capstones directly tie AI capabilities to problems confronted by the Navy and Marine Corps, allowing students to use their education and skills in their future careers.

## **THE SUMMER OF AI: INTERNSHIPS AND RESEARCH**

The USNA computer science department is fortunate to have a large number of faculty whose research focus is on AI, encompassing areas including intelligent robotics, autonomous control, natural language processing, understanding of social networks, neural networks, and others. These faculty are leaders in their fields and participate in the most productive and prestigious communities of AI research. This allows excellent students to participate in this research, both during the school year and during their summers.

During the school year, a research course counts as a three-credit elective, although they are frequently taken in addition to a normal load of courses. Recently, four students were involved with three projects involving AI: “Algorithms for Improving Drone Swarm and Counter-Swarm Tactics,” “Automated Underwater Mine Recognition,” and “Detecting Obscured Phone Numbers with Neural Networks to Fight Sex Trafficking.” These courses frequently result in peer-reviewed publications.^([11](#22_Chapter14.xhtml#rfn14_11))

Midshipmen can also use a portion of their summer block to do research, both with faculty and with outside agencies. Many of these internships are supported by the Department of Defense High-Performance Computing Modernization Program.^([12](#22_Chapter14.xhtml#rfn14_12)) Recently, students spent time learning about applications of AI at the National Oceanic and Atmospheric Administration, the National Security Agency, and at Department of Defense High-Performance Computing Centers.

In all of these opportunities, the goal is to challenge the very best students who might not get the same attention in class as those who struggle. By doing so, we aim to give them the tools to fulfill their potential and impact the future of their own career and the Navy and Marine Corps.

## **MOVING FORWARD WITH AI EDUCATION AT THE NAVAL ACADEMY**

Prioritizing education is a challenging process at an institution such as the Naval Academy. There are many areas of education that are important to a midshipman’s development, but there is only limited class time. When we consider the growing importance of AI in society, additional education in this field must be weighed against the changing tides of other, still-crucial subjects already offered at USNA. While broad education of AI for all midshipmen may not be part of the core, the most important step to enabling AI education is to build a deep program in artificial intelligence so that those midshipmen who know they want to become experts have the opportunity to do so. It is with this goal in sight that the computer science department has created its elective track of five different AI classes. We now see a new generation of midshipmen enrolling, and we look forward to training future officers to be AI-savvy as they lead decision-making in the fleet.

### **NOTES**

# 15

Trying to Put Mahan in a Box

**Insights from Attempting to Develop a Decision Aid for the Operational Commander**

ADAM M. AYCOCK AND WILLIAM G. GLENNEY IV

**Current Department of Defense (DoD)** initiatives related to the application of artificial intelligence (AI) do not yet support the commander or staff whose domain is the operational level of war. The operational level of war is officially defined as “the level of warfare at which campaigns and major operations are planned, conducted, and sustained to achieve strategic objectives within theaters or other operational areas.”^([1](#23_Chapter15.xhtml#fn1)) For the U. S. Navy, the operational level of war is associated with the fleet commander.

At the same time, the complexity, span, and number of contested domains of the current and future battlefield are expanding. This creates a combat environment often exceeding the informational and cognitive capacity of war-fighters and units at the tactical level.^([2](#23_Chapter15.xhtml#fn2)) The natural response is to assume that this increasingly complex character of future conflict can be sorted out, analyzed, and resolved at the higher operational level.

However, a mere aggregation of tactical complexity does not add up to the comparable complexity occurring at the operational level of war—a complexity that itself is expanding. Thus far, DoD’s developmental focus has been on tactical decision aids similar to those described in the scenario in chapter 6. While the decision aids currently being developed may indeed prove beneficial to commanders and their staffs (since they too are being bombarded by tactical information), these decision aids only address tactical-level challenges. Current and planned decision aids fail to incorporate principles of war that need to be addressed on the operational and strategic levels.

In essence, current decision aids featuring AI, such as photo recognition, may help win a battle but will come up short in assisting the operational commander to win the campaign or the war. These aids have not yet penetrated the level of planning and decision-making defined by the classical authors whose works form our fundamental understanding of the nature, if not the character, of war and conflict. Metaphorically, no one has yet figured out how to put Alfred Thayer Mahan in a box.

## **EXAMINING THE PROBLEM**

Most of the current and planned AI decision aids are based on explicit applications of physics, mathematics, and statistics; even those using “natural language processing” are really just turning words, phrases, and sentences into numerical representations, and then solving complex math problems with a very fast computer.^([3](#23_Chapter15.xhtml#fn3)) In fact, many “AI applications” are best viewed as merely an automation of processes that take advantage of Moore’s Law.

The authors of this chapter have been unable to find any Department of the Navy (DoN) or DoD-sponsored AI project that attempts to address the operational and strategic challenges faced by the fleet or joint force commander. Yet we believe that it is on the operational and strategic levels that war-winning advantages of AI will emerge.

Recognizing this shortfall in AI initiatives, the U.S. Naval War College’s (NWC’s) Institute for Future Warfare Studies (IFWS) set out to explore, with several industry partners, the development of a small-scale, narrow AI domain for maritime operations at the operational level of war. This effort was not intended to fully develop a new Navy AI application, but was an experiment that would identify the requirements for operational-level AI. From a programmatic sense, the results of our experiment may seem underwhelming, but the interaction with the industry partners resulted in the overall insight that very few existing commercial AI applications—perhaps none—are particularly useful at the operational level. This contrasts greatly with the prevalent assumption among senior officials that advances in commercial AI will *necessarily* result in advances in military AI applications and that these applications will function at the operational and strategic levels.

This chapter provides a general description of the IFWS effort and the lessons learned leading to the overall insights and seeks to inform DoN and DoD thinking about applications for AI in war. We believe DoN and DoD thinking is overly influenced by untested assumptions about what commercial AI can produce.

## **THEMES FROM CURRENT COMMERCIAL AI SUCCESSES**

In October 2017 there was exciting news regarding the intersection of artificial intelligence, big data, and machine learning. *Nature* magazine reported that the DeepMind subsidiary of Google had produced a new version of AlphaGo called AlphaGo Zero.^([4](#23_Chapter15.xhtml#fn4)) While AlphaGo had learned the game of Go by analyzing games between human players, AlphaGo Zero taught itself Go based only on the rules of the game and playing many games against itself. AlphaGo took a reported several months and 30 million training games to beat the world’s best human Go player four games to one. In comparison, after three days and 4.9 million training games, AlphaGo Zero achieved similar success, winning almost 69 percent of its games while playing against the original AlphaGo algorithm.

Since then, there have been multiple announcements of AI successes in a variety of subject areas, such as financial markets, predictive maintenance, image processing, medicine, and self-driving cars. If one were to take the news at face value, one might conclude that AI will soon be capable of handling any and all tasks and solving even the most difficult and complex problems. Such news may sell software, but the reality as opposed to the promise is more complex than the complex problems themselves.^([5](#23_Chapter15.xhtml#fn5))

Correlating our experience in trying to put Mahan in a box with the applications, reports, successes, and claims of AI, we derived thirteen observations concerning the characteristics of the competitive endeavors in which AI programming is perceived to have had success beating the decision-making of humans. Such competitive activities are often viewed as intellectual proxies for the formulation of military strategies or decision-making in war. Yet whether it is chess, shogi, checkers, Go, poker, or any other competition, the AI successes all share the same factors but are not relevant to warfare. In the thirteen observations, we contrast the required characteristics for AI success in competitions with the reality of the situations faced by operational commanders. The factors are:

1.  The rules associated with the endeavor are well defined, clear, stable, unchanging over time, and known to all participants. None of these conditions characterize the operational level of war—or any other level.

2.  There is a massive amount of data (big data) available for the endeavor, and there is little or no uncertainty in validity or meaning of the data. The games can be run many times so that the AI system can gather additional data. The available data has been cleaned and is well structured. None of this is true concerning the fog of war, and the same battle cannot be fought repeatedly simply to gather additional data. Unlike actual armies and navies, there are no consequences for AI systems if they lose the initial rounds during their self-learning.^([6](#23_Chapter15.xhtml#fn6))

3.  There is a clear, reasonably well-defined context surrounding the endeavor, and there is little or no uncertainty in the environment within which the endeavor occurs. Likewise, all participants know all about this well-defined context. The only associated uncertainty is the question of what move or action an adversary will take. Nevertheless, even the range of moves is bounded by known rules. The context is so well defined that if the AI is placed into a less certain environment, such as making AlphaGo try to play poker, the AI will fail quickly and significantly. In contrast, military and naval units must be capable of fighting in different domains or “all domains,” each with different characteristics and “game rules,” simultaneously.^([7](#23_Chapter15.xhtml#fn7)) Decision-making on the operational level cannot be specialized for one domain alone.

4.  The data for and information about the endeavor and the environment are known to all participants. Obviously, a human playing a game against an AI system would certainly not be able to recall as much information as a system that can play 4.9 million training games. However, in theory at least, the human would have all of the “data” available to him or her, the data being all the possible moves. In an efficient military organization, both real-world and simulation-delivered training is intended to “teach” tactical combat units all the possible moves as bounded by their capabilities. Yet once the “game” rises to the operational or strategic level, the complexity is such that it is rare that all possible moves are fully known. Rarely is the environment fully known. Moreover, the opponent frequently attempts to ensure that the data is hidden or distorted.

5.  The endeavor allows near-boundless iterations, permitting participants to exhaustively explore the bounded environment. Again, AI competitions are most successful with clearly defined rules. Wars may have a peculiar nature or character with most rules nonexistent or ill-defined until the war is being fought. There are indeed a few “rules” defined by the international laws of war and through prudent nuclear deterrence. However, even these rules are often bent and occasionally disregarded by warfighters in the breach; but human decision-makers will likely be uncomfortable with allowing AI to determine when the “rules” should be violated or the extent to which a ruleless AI system will go to achieve victory. The role of the operational commander is to determine what should be done as well as what should not be done, and he or she does not have the luxury of boundless iterations to determine such.

One could also ask whether the ability for AI systems to generate boundless iterations under a hard and fast defined rule set does not simply result in the same general answer again and again, predetermined by the nature of the rule set itself. If programmed to determine the best plays in cricket, an AI system would not apply the tactics of baseball, although both sports are related. On the other hand, if not bounded by strict rules, would AI apply the tactics of martial arts? The point is that in a bounded system, strictly defined AI iterations would not necessarily provide operational staffs with greater options for action.

6.  There are many feedback loops within the endeavor, and the time scales of those feedback loops are comparable to the time scale of the endeavor. In other words, the feedback for one move is received before the decision is required for the next move. This tight coupling allows for more rapid training and faster evolution of AI systems. However, this differs from a military operation in which feedback (battle damage assessments or actions of the enemy) may not be received before a follow-on action is required. The famous OODA (observe, orient, decide, act) loop of John Boyd, discussed in the other chapters as applicable to the functioning of tactical AI, was originally inspired by aerial dogfights in which a combat pilot, if in position to observe, gains near-instantaneous feedback on his or her actions. Though the OODA model is certainly a valuable representation of human decision-making, rarely does the operational commander receive near-instantaneous feedback, even with the most powerful sensor suite. The operational commander might not receive feedback, and the effects of one move might not be recognized until several subsequent moves have been made. Furthermore, a competent enemy would be likely to attempt to mask or manipulate this feedback. Under such circumstances—and unlike AI in competitive games—it is difficult to “learn” from a first move in order to craft the second.

7.  In the competitive games (and other AI endeavors), there is clear and direct “cause and effect” relating an action to an outcome. If AI could be applied to problems at the operational level of war, a system of algorithms might be able to explore the range of possible causes and effects. However, this is much more difficult than in competitive games where cause and effect are obvious and the system does not have to spend considerable computing power to analyze possible causes and effects prior to analyzing all viable responses. If it cannot pinpoint a specific cause and effect, it is unlikely to be able to make a pinpoint recommendation for action. Rather, it would provide the operational commander with a range of possible moves, making the AI useful but not necessarily a tremendous leap over what is available today.

8.  Additionally, because of the nature of these endeavors, the level of action involved is limited. Unlike in military operations in which differing actions (with available responding options) are simultaneously occurring at the tactical, operational, and strategic levels, AI game systems necessarily deal exclusively on the tactical level. Even if one defines an overall game plan as occurring on a “strategic” level (which we do not), the adjustment of the plan occurs solely due to tactical results. In the case of the operational commander, higher-level authorities based on simultaneous actions on the strategic level might change the objectives. Perhaps allied forces operating independently have suffered a setback. Perhaps operations in a different theater require a draw from the resources under control of another operational commander. In short, in warfare, different “games,” each with different rule sets, are simultaneously being played on different levels.

In other words, the operational commander is faced with making broad decisions in an environment where tactical actions are occurring in multiple “games” (domains), each with different “rules.” For example, the tactics of submarine warfare differ greatly from the tactics of ground combat, but the results of both tactical events need to be compiled and coordinated at the operational level. Thus far, no AI system has demonstrated its ability to deal with such complexity. We do not say that it is impossible for an AI system based on hundreds of thousands of algorithms and millions of lines of code to approximate such an ability. However, we do maintain that developing such an AI system would likely require billions of dollars and tremendous labor. Commercial firms, having few customers for such systems, will not build them on speculation. Google’s DeepMind is a money loser that only exists because its parent company makes tremendous profits in other business sectors. Whether it is prudent for DoD to spend billions of dollars for such a decision aid is a debate beyond the scope of this chapter, but it must be acknowledged.

9.  The existence and presence of biased values in current AI competitions are known and accepted as part of the endeavor and environment. In contrast, can an operational commander be certain of the biases of the adversary’s commanders? Although difficult to do in an authoritarian country such as Russia, intelligence activities may uncover patterns of behavior or statements made by the individual adversary commanders that can be characterized as “counterintelligence.” AI methodology might be applied to analyze this information, blending the input from multiple sensors and sources. However, one has to consider the opponent’s AI systems will likely be designed to deceive by preventing the use of accurate data. This is a natural aspect of war occurring long before it was identified by Sun Tzu.

10.  The risk associated with AI games is known, small, and considered relatively inconsequential. This is obviously the most significant difference between war and AI applications to chess, Go, and other games. There are no casualties. Never is a participant executed for losing a game. AI is playing for low stakes. Can AI systems be used with any sense of trust when playing for high stakes? An interesting experiment would be to “destroy” an AI system every time it loses, thereby forcing it to relearn all the data that it had previously learned. Would it learn the same data? Would it be more or less effective if the AI system were to begin again with a clean slate following a loss?

11.  The definition of success in these endeavors is clear, agreed upon, and known by all the participants. In contrast, the definition of “victory” in modern war remains currently under debate.^([8](#23_Chapter15.xhtml#fn8))

12.  There are no competing objectives leading to a clear, small set of tradeoffs for optimization. In competitive games thus far featuring AI, there are no mission-manpower tradeoffs, such as tempo of operation versus casualties, with all the moral implications that they involve. In competitive games, levels of resources are generally fixed, avoiding the need to allocate varying availability of resources against a changing list of requirements.

13.  None of the AI algorithms appear to make strategic- or operational-level decisions in the games in which they have been tested thus far. Instead, they are only executing tactics, albeit at numbers and speeds that exceed human abilities. Humans make the decisions as to the context, the timing, and how to use the AI system. A human makes the strategic decision whether to play Go or poker; the AI merely executes the tactics for that decision.

In summary, successes to date for AI systems in competitive games have been enabled primarily by faster computer processing speed, better “math” computation for the data and information, or some combination of both. When the context surrounding the endeavor, the endeavor itself, or the environment within which the endeavor is conducted depart from any of the above thirteen factors, AI falters or fails. As discussed above, warfare is characterized by the antithesis of every one of these thirteen factors. In war, timely big data can be very hard to obtain and is often obfuscated by the adversary; the rules are not clear and are subject to change by all sides of the conflict; the uncertainty for all aspects is huge; feedback loops are few and slow; there is often an absence of clear, direct cause and effect with divergent behaviors frequently arising; there are many competing and irreconcilable objectives; the risk is significant; and the definition of success is cloudy at best.

There have been reports that AlphaGo has been trained to play other multiple games.^([9](#23_Chapter15.xhtml#fn9)) In actuality, this is little more than adding another software module providing the rule set defined in the new game to the existing learning software. Yet there is no evidence that AlphaGo can decide which game to play and do so before starting the play. It is likely that within a few moves, AlphaGo could determine which game is being played, but only after actually engaging in that game. The strategic-level decision—which game to play, along with the overall objective of winning—remains the purview of a human. Once that strategic decision has been made, the execution—the tactical play—can well be accomplished by AlphaGo.

Reports of AI successes in competitive games, such as Texas Hold ’Em poker, Atari’s *Montezuma’s Revenge*, and *StarCraft II*, have caused many (including defense resource decision-makers) to assume that AI can, with a reasonable amount of effort and resources, be used for well-defined technical challenges of the military or possibly for niche capabilities at the tactical level of war.^([10](#23_Chapter15.xhtml#fn10)) However, while these successes may well be conceptually useful for the Navy, there is no evidence that existing systems or any AI system in the immediate future will contribute to or produce a war-winning capability for the operational or strategic levels of war for the fleet commander or the geographic combatant commander. To put this conclusion in folksy language: AlphaGo ain’t warfare, and it ain’t strategy.

## **MAHAN-IN-A-BOX: INTRODUCTION**

Having described some of our findings from the general investigation, let us present the specifics of what we call “Mahan-in-a-Box” (MIAB). MIAB is an exploratory attempt to determine the possibility of crafting a small-scale prototype that would examine the application of narrow AI and natural language processing to the operational level of war.^([11](#23_Chapter15.xhtml#fn11)) Our vision was twofold, with the choice of final direction based on preliminary output. The first was to examine if AI could answer the types of questions that the Pacific Fleet commander would ask in preparing for war. The second was to examine the application of the entire body of work in the U.S. Naval War College library and archives to help improve the student education at NWC.

The logic of linking the two objectives is (presumably) that the knowledge taught at the Naval War College is ultimately designed to educate a future operational-level commander, and this knowledge would be useful in helping an operational-level commander formulate a method for examining an operational problem. In effect, MIAB is about exploring the extreme edges of unstructured data and questions with an absence of numerical data, high degrees of uncertainty, and a low number of data sets. That is the situation facing a commander at the operational level of war and, in theory, the war college student.

## **MAHAN-IN-A-BOX: THREE ONTOLOGIES**

Beginning with the end in mind, we designed a notional concept of Mahan-in-a-Box as a tool for the operational commander consisting of three AI domains ([figure 15-1](#23_Chapter15.xhtml#fig7)): Mahan-in-a-Box ontology (left side), Joint Military Operations ontology (lower right), and Mahan-in-a-Box historical data (upper right).

An ontology is a method (like taxonomy) of both linking and separating terms and bits of related information. This method has been referred to in previous chapters as “labeling.” In modern computer science, the ontology term has been adapted to refer to the association or distinction of programming symbols into categories.^([12](#23_Chapter15.xhtml#fn12)) For AI, “an ontology is a specification of the meanings of the symbols in an information system … a conceptualization … of what individuals and relationships are assumed to exist and what terminology is used for them … and gives some axioms that restrict the use of that vocabulary.”^([13](#23_Chapter15.xhtml#fn13))

An example of an ontology is the “mapping from a conceptualization to a symbol” by associating the terms “condos,” “flats,” and “apartment complex” with the symbol “ApartmentBuilding.” Such a symbol needs to be “usually written independently of a particular application and often involve a community to agree on the meaning.”^([14](#23_Chapter15.xhtml#fn14)) The example states:

An ontology of individuals that could appear on a map could specify that the symbol “ApartmentBuilding” will represent apartment buildings. The ontology will not *define* an apartment building, but it will describe it well enough so that others can understand the definition. We want other people, who may be inclined to use different symbols, to be able to use the ontology to find the appropriate symbol to use.… An ontology may give axioms to restrict the use of some symbol. For example, it may specify that apartment buildings are buildings, which are human-constructed artifacts. It may give some restriction on the size of buildings so that shoeboxes cannot be buildings or that cities cannot be buildings. It may state that a building cannot be at two geographically dispersed locations at the same time (so if you take off some part of the building and move it to a different location, it is no longer a single building). Because apartment buildings are buildings, these same restrictions also apply to apartment buildings.^([15](#23_Chapter15.xhtml#fn15))

![Figure 15-1. Mahan-in-a-Box Conceptualized at the Operational Level of War](images/pg275_1.png)

**Figure 15-1**. Mahan-in-a-Box Conceptualized at the Operational Level of War

All the terms are “mapped into” the symbol “ApartmentBuilding,” with condos, flats, and apartment complex becoming part of the ontology. The symbol “ApartmentBuilding” can be linked to a more inclusive ontology headed by “ResidentialBuilding.”

An AI system “creates knowledge,” which in our desired outcome provides recommendations to an operational commander or information to a war college student, if it is able to associate data separated into one (or more) ontology with another through the use of thousands of mathematical algorithms. Algorithms are simply mathematical procedures in which numbers are used to represent the symbols. As a theoretical and greatly simplified example: in a “simple” competitive game, an AI system must associate a move (from a “move ontology”) with an outcome (from an “outcome ontology”), in effect creating a new greater ontology. The advantage of AI over a human is that it can make these associations faster, handle a larger data set (big data), and sort through more possible outcomes than any human. In effect, this is what happens in Project Maven where the AI processes vast amounts of unmanned aerial vehicle video footage in search of potential targets.^([16](#23_Chapter15.xhtml#fn16))

One potential disadvantage in adopting any particular ontology must be acknowledged, however. Committing to a particular ontology inevitably limits the range of terms that an AI system can utilize in creating data associations. Given the nature of human thought, it is relatively easy for humans to shift between ontologies; it may never be as easy for AI systems.

In the MIAB project, we found that current AI technologies could conceivably support two of the three AI domains that we wanted to use: the Mahan-in-a-Box ontology and Joint Military Operations ontology. The Mahan-in-a-Box ontology is an attempt to associate “real time” input with an action identified in an operational campaign plan.^([17](#23_Chapter15.xhtml#fn17)) This is conceptually similar to the Project Maven approach in that an input would be identified as fitting the campaign planning scenario, alerting the operational commander that he or she needed to take action. At the same time, the Joint Military Operations ontology would consist of a body of knowledge that could be queried as to what action should be taken.^([18](#23_Chapter15.xhtml#fn18))

However, in our view, simply identifying a situation and retrieving an option for action does not constitute “intelligence” and does not provide an advantage over using existing (non-AI) databases. We also wanted to collect past wisdom from history as an input to the operational commander. The “artificial intelligence” would associate real-time data (correlated to aspects of a planning scenario) and options for action with the knowledge of results from similar situations in the past. The operational commander (or war college student) would have three tools: an alert that action needs to be taken, a group of the possible options for action, and the academic knowledge of past results from situations similar in concept albeit not in details—in other words, the wisdom of the past.

Imagine a wealth of knowledge for a future fleet commander gleaned from the problem-solving methodology of Fleet Adm. Chester Nimitz based on Nimitz’s own documented material.^([19](#23_Chapter15.xhtml#fn19)) A system that could be fed the characteristics of a current operational problem—for example, how best to position naval forces in a narrow strait—and apply the methodology and logic of Nimitz to this problem could be a valuable advisor to a modern-day naval command (and his/her staff) who has not previously faced such a problem. This knowledge of past methodologies is resident in the Mahan-in-a-Box historical data ontology (also incorporating the other data) shown in the top right section of [figure 15-1](#23_Chapter15.xhtml#fig7).

Unfortunately, our research found that the AI domain shown as Mahan-in-a-Box historical data is beyond the capabilities of current and planned AI technology. None of the commercial firms consulted for MIAB had a solution as to how an AI system could associate input from three distinctly different ontologies any more than AlphaGo could play three different games using the same rules to create a single outcome.

## **MAHAN-IN-A-BOX: PROBLEMS IN THE EXECUTION**

Current natural language processing methods involve various methods of assigning numerical values to word, phrase, and sentence entities and then using mathematical methods to process the entity values. This does not create “understanding” by the machine. For Mahan-in-a-Box historical data, “understanding” would be the ability to access large amounts of categorized data referred to as data lakes. The central problem in the execution is not just in creating the computational structure or writing algorithms. The problem is also that the big data we wanted to use is too complex for current or planned AI.

Gleaning wisdom from the memoranda of Admiral Nimitz or the prolific writings of Alfred Thayer Mahan is more difficult than counting the number of computer clicks that a potential Amazon customer makes when searching websites. It requires considerable resources to “clean up” and properly structure data before data can be exploited. But how does one “clean up” and categorize *The Influence of Sea Power Upon History* in such a way that it can be associated with the writings of the ancient Chinese strategist Sun Tzu? This would require, for example, data scientists to know the differences in meaning between what Mahan understood as “war” and what Sun Tzu understood as “war.” U. S. Naval War College professors debate this even today.

As previously noted concerning our second objective, a fundamental assumption of the MIAB project is that the Navy educates and produces operational level of war thinkers by their participation in the joint professional military education–approved core curriculum at NWC. Therefore, the inputs to the “human brain” are contents of the books and documents in the course syllabus, questions posed in the syllabus and their answers, speakers in the curriculum, examination questions and their answers, and discussions and debate in the seminars. If AI-based processes are to be useful at the operational level of war, then an AI domain “trained” with the same data should work. Graduates of NWC are certified operational level of war thinkers and doers. Therefore, we viewed the syllabus of the NWC core curriculum as the valid “data lake” with which to train the AI. Could AI pass the NWC examinations?

Given the arguably central role of Carl von Clausewitz, Sun Tzu, and Mahan in the “Strategy and War” part of the NWC curriculum, the seminal works of these three authors were chosen for the MIAB training data. This decision was also driven by limitations on time, funding, and the amount of “data” (that is, the volume of words from Clausewitz, Sun Tzu, and Mahan) that would be ingested.^([20](#23_Chapter15.xhtml#fn20)) The research team drew selected extracts from Clausewitz, Sun Tzu, and Mahan to establish a basic ontology, basic lexicon, and set of relationships that would be useful at the operational level of war. The team also examined the actual details of how computers process unstructured natural language data, machine learning, and classification, and initiated numerous discussions concerning feasibilities with commercial AI firms.

The team had extensive discussions with IBM Watson Services, Amazon Web Services, Forge. AI, and commercial firms attending the 2018 Georgia Tech AI Symposium and the Office of Naval Research’s Naval Research and Development Enterprise Applied Artificial Intelligence Summit in October 2018 to explore different AI approaches to the data processing in the MIAB prototype. All of these discussions were done separately and done on a nonattribution basis.^([21](#23_Chapter15.xhtml#fn21)) Of the major contributors, one eventually declined to continue because it could only develop algorithms for well-defined ontologies that already exist in the world of Internet marketing but not for the ill-defined world of Mahan. Another firm’s proposed solution was to “hard-wire” a set of specific relationships among data in a way that the system could not “teach” itself—ultimately not an AI product. We thus worked with two large established services in two parallel but separate tracks to learn the capabilities of their two systems and to gain insights into directions AI might take in the near future.

## **MAHAN-IN-A-BOX: FINDINGS**

The findings of the MIAB effort may seem very pedestrian to an AI scientist, but they say a great deal about the difficulty of applying AI to military and naval decision-making at the operational level of war. These are difficulties that nonexpert senior leaders must consider before they try to, as termed in chapter 6, “sprinkle” AI on top of an operational or strategic problem. Our findings:

•  Commercially available AI systems are not sufficient.

•  Better math (algorithms) will not solve the problem.

•  Faster processing will not solve the problem.

•  Natural language processing is not good at understanding broad concepts, cannot synthesize big ideas, and fails in the face of high levels of ambiguity or uncertainty.

•  Words, terminology, and definitions are critical.

•  Text requires significant human effort to be cleaned and prepared for ingestion, generally more effort than required to design the system or write the algorithms, yet usually glossed over.

•  Introductions, prefaces, and postscripts in documents introduce bias.

•  Interfacing effectively with AI is a new skill set. Knowing how to query AI is critical to the output.

•  Nobody else within DoD is trying to do this—“this” being trying to develop an AI decision-making tool at the operational level of war.

Current commercially available systems are not sufficient because the open market is not demanding the kind of AI capabilities needed for a fleet commander. Commercially available systems tend to be optimized for handling clean, well-crafted data or text and narrowly defined challenges and probably cannot be modified for the ill-defined tasks that characterize the operational level of war.

Better math and faster processing won’t solve the problem. Most recent AI improvements or gains are the direct result of one or both of these factors. Many AI challenges revolve around hard-core mathematics, such as vectors, tensors, and multivariable calculus. For those problems, there is typically lots of data, and in those cases where there is insufficient data, either more data can be obtained or the processing can be modified to account for the dearth of data. At the operational level of war, the preexisting data sets are sparse, if they even exist at all. The existing and anticipated mathematical tools simply cannot handle extremely ill-defined concepts for warfare.

In its current and future expected state, natural language processing is not good at understanding broad concepts and cannot synthesize big ideas. The same processing that analyzes text and discovers sentiment does not appear to be adaptable to broad concepts such as the principles of war. When Mahan-in-a-Box was queried, “What is war?” it was able to provide some applicable quotes from Clausewitz and Sun Tzu but couldn’t synthesize those quotes into a coherent answer. When queried, “What is *not* war?” Mahan-in-a-Box, as well as those people working on the project, was at a loss for words because the data lake did not contain a specific passage associated with the question.

Text requires significant human effort to be cleaned and prepared for ingestion. While having been used for many years and reasonably “processed” by human students, textbooks for “philosophers of war” Clausewitz, Sun Tzu, and Mahan required extensive manipulation and formatting in order to place them in a condition so that they could be uploaded into Mahan-in-a-Box and processed without being confused by page numbers, chapter titles, footnotes, and other material not relevant to the main ideas.

Introductions, prefaces, and postscripts, while useful to a human reader, introduce bias into the data set. When Clausewitz’s *On War* was ingested and processed, one of the overarching themes determined by the system was reported as “Clausewitz.” But we know that Clausewitz did not talk in the third person about himself. This is when we discovered that the front and back matter of a text could influence the math, causing a bias or creating a variable or entity that is of no value. Front and back matter may prove useful if ingested once the core ontology is created. However, this issue drives home the need to steward the data, the process, and the domain from cradle to grave with understanding and deliberation.

Words, terminology, and definitions are critical. At the heart of the challenge of thinking at the operational level of war is the ability to synthesize words and ideas across a number of documents. *On War* by Clausewitz, *The Art of War* by Sun Tzu, and *The Influence of Sea Power on History* (both volumes) by Mahan were written by at least three different authors (it is questionable if Sun Tzu wrote all of the text), at three different times of world history, in three different contexts, and based on three different experiences (data sets). Therefore, it should be no surprise that “war” in Clausewitz is not the same as “war” in Sun Tzu is not the same as “war” in Mahan. Furthermore, key terms used in one document are absent from another.

Interfacing effectively with AI is a new skill set. Knowing how to query AI is critical to the output. The manner in which a question is asked directly influences the natural language processing algorithm and affects the output. The ability to have a “conversation” with the AI is a requirement for achieving meaningful results for the user.

Nobody else within DoD is trying to do this!^([22](#23_Chapter15.xhtml#fn22)) Based on attendance at and participation in the Naval Research and Development Enterprise Applied Artificial Intelligence Summit, a similar workshop hosted by Georgia Tech Research Institute, discussions with the DoD Joint Artificial Intelligence Center, the staff of the Deputy Chief of Naval Operation for Information Warfare, Office of Naval Research, Defense Advanced Research Projects Agency (DARPA), faculty at the Naval Postgraduate School, and the North Atlantic Treaty Organization Supreme Allied Commander Atlantic Innovation Center, none within DoD are working on the potential application of AI to the operational and strategic levels of war. All current projects are focused on specific technical problems or narrow tactical-level problems. One industry subject matter expert stated the MIAB was working beyond the current edge of commercial AI technology. One former DARPA program manager told the MIAB team that he would not fund this project if it came to him because it was too hard and too undefined.

## **CONCLUSIONS AND RECOMMENDATIONS**

For now, there are no commercial AI applications or any DoD projects that appear useful as a decision-making aid at the operational level of war. None appears to be on a path that could lead to a useful aid. The use of AI in support of multiple tactical operations does *not* aggregate to effective use on the operational level.

There certainly appear to be potential tactical applications for AI. As noted in other chapters, AI has had reported success as an aid in intelligence analysis, such as photo recognition in Project Maven. However, our brief experience with ontological development and discussions with AI service providers indicate that no existing off-the-shelf solutions can augment human decision-making by fleet or joint force commanders, particularly in simultaneous all-domain warfare. Furthermore, without direct contracting by DoD, there does not seem to be commercial incentive to develop the applicable specialized AI algorithms.

That is not to say that operational-level AI decision-making tools *cannot* be developed. They might be achievable. However, all indications are that they would need very direct, long-term, and persistent efforts by DoD itself. As evidenced by the controversy within Google, this will not be as easy as many DoD leaders have been led to believe.

We recommend that the Navy and DoD begin now to develop AI that supports operational- and strategic-level decision-making. The Navy and DoD should not wait for commercial AI spin-offs to solve operational problems. Operational AI will be a military and naval construct, and it will not be developed except at great cost in human resources, time, and money. Unfortunately, we do not see any DoN or DoD operational-level AI programs of record emerging. An unexpected commercial technical breakthrough could always occur, but that is not something on which DoD should bet.

## **NOTES**

# 16

“Sea Hacking” Sun Tzu

**Deception in Global Al/Cybered Conflict and Navies**

CHRIS C. DEMCHAK AND SAM J. TANGREDI

**How do we program a computer** to distrust its own outputs and subroutines? How do we teach a machine to suspect the truthfulness of what it is being taught? How does an algorithmic process learn to sense when it is being fed by corrupted sensors? How does society keep its complex digital devices useful if they must be disconnected from the shoddy global cyberspace just to be secured from adversaries?

Currently, there are no answers to these questions. However, there is no disputing the inevitability of artificial intelligence (AI) spreading everywhere and into everything that networks have penetrated. It will inherit all of the vulnerabilities of the existing, shoddily constructed cyberspace substrate. It will be central to the twenty-first-century’s great power competition between the United States, with its consolidated democratic allies, and the much larger world of authoritarian regimes increasingly led by the People’s Republic of China (PRC)’s resources, economic statecraft, and ubiquitous presence.

At the moment—and as implied by chapter 5—China holds the edge in three of the “four horsemen of AI”: scale, strategic coherence, and fore-knowledge,^([1](#24_Chapter16.xhtml#fn1)) while the allied democracies only have the advantage in the speed of sharing knowledge for technology advance and adopting.^([2](#24_Chapter16.xhtml#fn2)) If this situation holds, China will be able to act with strategic coherence, using AI built on unprecedented stocks of foreknowledge acquired from a globally scaled plethora of information resources. It will be extraordinarily difficult for another nation to do anything at a national scale without a PRC actor having already received advanced information and, through AI, determined a response most likely to be favorable to PRC interests.

## **WHEN AI DECEIVES**

Chinese president Xi Jinping acknowledges the writings of the legendary strategist Sun Tzu as a key guide to Chinese behavior across the cybered conflict spectrum from peace to war. Hence, the benefits of the three AI horsemen will be put to particular use in deception as a (if not the primary) key multiplier in the global power competition. In contrast, consolidated democracies are unique in holding transparency as a key society value. As a cultural more, their warriors tend to disdain deception as dishonorable; their citizens prefer to trust others. As a whole, these democracies are therefore unusually vulnerable to deception campaigns—especially covert operations. The global cards are not stacked in the favor of the democracies.

In order to maximize the benefits of holding the edge in the remaining “horseman,” speed of adoption and related innovation, the United States and its democratic allies must overcome the additional challenge of learning how to recognize, defend against, and use deception in, through, and enabled by every AI application employed, while also moving rapidly and collectively to embrace the AI/cybered world. It will not be easy. As noted by a recently initiated Defense Advanced Research Projects Agency program called Guaranteeing AI Robustness against Deception, the vulnerabilities to abuse of machine learning as the underlying key process of AI are not themselves well known or studied.^([3](#24_Chapter16.xhtml#fn3)) To then add having to design the AI from the outset for deception—passively or actively and for defense or offense—places an extraordinary burden on the consolidated democracies in their great power competition.

Nonetheless, AI/cybered deception is a key competency that all warriors in democracies, whether in time of peace or war, need to master—particularly if the following four conditions apply. First, the system in question is losing in the relative scale of its global footprint economically and demographically when compared to hostile entities. Second, its defenders cannot determine well or match what its adversaries can acquire, coerce, or use in advanced knowledge against it. Third, the systems at risk and essential for defense are themselves unique and concentrated in the overall defenses, lacking substitutes. Fourth, the state must prevail or forestall losses as a long-term, whole-of-society existential requirement. Each of these is a killing asymmetry that has produced deception as a critical response throughout history. From irregulars in the American Revolution, to Napoleon’s navy, to Mao Zedong’s long march, to the Serbian use of armor opposing North Atlantic Treaty Organization forces in the 1990s, short- or long-term existential conflict with great scale asymmetries makes deception exceptionally necessary. The very large, competent, economically powerful states engage in deception to lower costs and achieve outcomes with less effort. The smaller defenders pursue it as a necessity.

The coming world is one in which the consolidated democracies will be a minority community of nations governed differently and holding dramatically different values from the much larger and more authoritarian rest of the world. Deception will be needed to level the playing field in defense, and AI will play a key role. Today’s Pollyanna-esque promotional hype needs to be ignored, and AI/cyber tools need to be rapidly but sensibly designed and employed with deception uppermost in all systemic planning.

The challenge for navies in this coming world is no less stark and demanding than for the societies they serve. The U.S. Navy has already publicly admitted its failures in securing its use of cyber so far, with one senior official saying the organization is “woefully behind” in cybersecurity.^([4](#24_Chapter16.xhtml#fn4)) The incoming AI systems will need to nest within the very cyber substrate currently viewed as insecure. To add to the challenge, the strong impetus to put AI in strategically critical processes and systems throughout the service will need to be matched by an equally compelling anticipation of, and reorganization for deception in, through, and enabled by, that technological advance.

This chapter first argues that deception is a necessary pillar of all future operations and must be included from the outset in all new AI/cybered applications as the nation and the Navy move quickly into the world of AI. Second, the U.S. Navy has to abandon its preferences for concentrated force structures and embrace deception as it modernizes with AI in order to survive as well as have a chance to prevail in the coming years. If it does not learn to effectively “sea-hack” the incoming deception campaigns, adversaries and their proxies will game the AI systems that the service thinks it can use to prevail. The cards are not in the Navy’s favor at present, irrespective of the hype.

## **DECEPTION, CYBER, AND AI**

AI will accelerate the global system-versus-system cybered conflict cycles already in full swing. Major adversaries already practice peacetime digital deception across a wide array of campaigns for economic, military, and political advantage. Deception in tools and opaqueness in attack origins are two of the five key offense advantages enabled by the shoddiness of the current cyberspace substrate (the others are scale, proximity, and precision).^([5](#24_Chapter16.xhtml#fn5)) The widespread implementation of AI will speed up, disperse more widely, and hone the accuracy of current cybered efforts in the promulgation of false information, the penetration of networks via social engineering (or fooling people into downloading malware), and the installation of backdoors in the supply chain for later use in encouraging false interpretations or obscuring origins of actions.

Deception is strongly dependent on the deceiver having access to and then manipulating inputs somewhere within the opponent’s decision-making cycle. As a general process, deception has two common modalities: to present a false story, and to draw those to be “phooled”^([6](#24_Chapter16.xhtml#fn6)) to see and accept the false story.^([7](#24_Chapter16.xhtml#fn7)) The first can be as simple as camouflage, and the second as ornate as changing the leaves, the animal tracks, and even the noises from a camouflaged forest area in order to attract attention without alerting to danger.

For example, in the Kosovo operations of the 1990s, the Serbians were said to have fooled overhead satellite imagery by constructing fake tanks and tents, forcing the allies to waste efforts bombing cardboard.^([8](#24_Chapter16.xhtml#fn8)) The allied forces did not have enough boots on the ground to check everywhere. In the languages of computer system deception, the allies did not have the right scale, modality, and dispersion of sensors. As a result, the allied systems processed—and acted upon—bad data to the benefit their adversaries.^([9](#24_Chapter16.xhtml#fn9))

Yet that is an example of only one data stream being corrupted—overhead imagery. Decision-making of the future will depend on feeding many streams of widely sourced data into a myriad of grouped statistical processes embedded in software that then presents operating pictures or options for decision-making—in other words, it will depend on AI. When deception can be applied to any organization’s AI/cybered decision-making inputs throughout society, the future will be extraordinarily challenging for those unable to respond defensively and in kind.

Research by Gavin Taylor, a U.S. Naval Academy professor of computer science and a co-author of chapter 14, identifies just such a deception called “data poisoning.” Taylor and his co-authors point to the fact that much of the training data used for commercial AI is harvested from the insecure, shoddy (as we call it) cyber Internet: “Deep neural networks require large datasets for training and hyper-parameter tuning. As a result, many practitioners turn to the web as a source for data, where one can automatically scrape large datasets with little human oversight.”^([10](#24_Chapter16.xhtml#fn10)) Their conclusion, an understatement from a strategy perspective, is that “unfortunately, recent results have demonstrated that these data acquisition processes can lead to security vulnerabilities.”

Data poisoning is possible by embedding perturbations within an image on the Internet or building a false frame around the image—perhaps visually undetectable—that becomes an accepted part of the training data set used for machine learning. In a nation with control over public images of its military system, such as the People’s Republic of China, it would be possible to provide false data within these images that could train AI systems not to recognize them or view them as nonthreatening.

Dealing with this future will be doubly difficult for Westernized political, military, and economic leaders. In most consolidated democratic states, because deception is certainly not seen as a virtue nor is it viewed as honorable,^([11](#24_Chapter16.xhtml#fn11)) the initial development of cyberspace among the information technology (IT) communities of these nations ignored the need for the security in programming. In the 1990s and 2000s, developers did not perceive as a serious threat the sort of criminality and deception that would later occur on the Internet. They saw no need for the extra effort to build in safeguards. Indeed, a major application that now uses AI—Facebook—was famously led by the chief executive officer’s mantra, “Information wants to be free.” Only now is the firm paying the costs of having been blatantly deceived by adversaries skilled at deception.^([12](#24_Chapter16.xhtml#fn12))

The hype around AI systems developed by such countries already has that flavor in which the efficiencies of the technology are paramount, and security is treated in promotional literature as a necessary but secondary—or even postproduction—issue. In an unfortunate replay of early cyberspace development, the rampant development of AI systems today is likely to produce systems highly vulnerable to strategic deception from the outset in their design and coding.^([13](#24_Chapter16.xhtml#fn13))

AI/cybered systems are digitized but not free from the biases of the societies around them or the communities that create them. Research is already showing that the selection of training data sources can produce biased results that reflect the blind spots of the society. Recent research showed that an advanced AI system learning on domestic U.S. news, magazines, and other data concluded that men are better than women at science, technology, engineering, and mathematics. The volume of material with this presumption massively outweighed the small amount of over a decade of scientific research showing no significant difference in math ability between boys and girls.^([14](#24_Chapter16.xhtml#fn14)) Furthermore, the programmers and computer scientists themselves, as well as users who point to the data to be collected, are affected by the surrounding strategic culture and therefore affect what the AI systems are taught. If the surrounding community does not look for or disdains deception as dishonorable, its AI-driven decisions could reflect a strategic culture that is in large part oblivious to the underlying vulnerabilities enhanced by the biases in the data on which its AI learns.

At all decision-making levels, knowing what is going wrong and being able to do something rapidly to avoid the worst consequences are two different but related large system challenges. With great complexity, neither knowing nor acting is easy, cheap, or necessarily quick enough. The larger the complex systems, the more likely are “normal accidents”—that is, accidents due largely to the relative decrease in either knowing or acting among humans at some or many points along the way. A normal accident of complex systems offers more opportunities for exploitation and enhancement of effect for adversaries seeking moments of distraction or disruption in order to slip into systems. Additionally, the expectation of normal accidents may mask outside interference. As another cybered cartoon states: “That was a cyber-attack? I thought it was a Windows update.”

In adversarial situations, when systems grow in complexity—that is, in numbers of nodes, differentiation of those nodes, and interdependence among them,^([15](#24_Chapter16.xhtml#fn15)) the chances of successful penetration increase and the adversaries will be able to hide themselves or their operations/tools from the purview of the operations of that complex system. If key nodes are deeply embedded (such as deep machine learning) with nontransparent forms of cyber connectivity, the job of knowing accurately what is happening is harder for the defenders of the system unless they have prepared sufficient sensors in the right locations and are able to acquire, assess, and act upon their data rapidly.

These sensors, however, will also be part of AI/cybered systems in order to respond quickly when triggered. Indeed, a multiplicity of sensors is a routine solution to possible multisource failures in large engineering systems, but cyber/AI-driven sensors also offer remote or embedded opportunities (from supply chains) to mislead defenders that rarely existed prior to this era. In short, adversaries seek to make sensors “blink” at just the right time for their campaign. If they have a hold in the supply or AI development chain, that certainly creates opportunity. Under these circumstances, how can AI be taught to learn when to distrust the sensors on which it is now learning?

Furthermore, AI systems that are expected to be deceived are more likely to be designed to reach across a large number of sensors drawing in data from multiple sources—possibly globally—in order to learn and then confirm. The problem then becomes how far back in time or how widely across data sources an adversary can prepare in order to consistently skew input data to the targeted AI. An adversary whose state champions have obtained critical positions in building, operating, maintaining, and updating the national telecommunications systems of a number of nations—as have Huawei and China Mobile, for example—would have better chances of a successful deception campaign that is strategically coherent and comprehensive in scale. Multiple sources may be corrupted nearly simultaneously and consistently over time to provide a false picture to a targeted set of defenders. As the corrupted picture gradually displaces the real, their own internal analysis is hampered in challenging what appears to have become the new normal. Hence, having presence globally with the ability to alter what data is collected particularly helps create the false knowing and benefits larger-scale attackers.

Deception cannot be detected or neutralized by diversity in data streams alone. If all the streams meet in a centralized large-scale AI system—standardized in design for efficiency or acquisition and reduced costs—as the sole decision-making aid in a critical operation, the chances of deception on top of the normal surprises of complexity increase as well. One might argue that a defense can be built by having some redundancies, such as multiple AI systems checking on each other’s calculations. However, if multiple AI systems are standardized in design for efficiency and reduced costs, it is more likely that they all could suffer from the same flaws and vulnerabilities and, ultimately, manipulation of biases or interpretation.^([16](#24_Chapter16.xhtml#fn16)) In short, diversity and multiplicity as fixes need nuanced implementations that anticipate the range of adversary advantages, such as a global technical basic network presence throughout other nations’ networks.

Every year since its advent, cyberspace has produced unpleasant surprises, and the future developments of AI are unlikely to be any smoother. For example, what was not grasped until recently is that potential threats begin long before use—at the sources of the technology from second- and third-party designers, software companies, and hardware manufacturers, as well as in the acquisition of systems through the hacking of computer-aided designs, routine theft of intellectual capital, and potential disruption of logistics and supply chains. Currently, advanced democracies are losing 1 to 2 percent of their annual gross domestic product to cyber insecurity.^([17](#24_Chapter16.xhtml#fn17)) The addition of AI without attention to the potential for large-scale, long-term, and crippling deception campaigns will majorly increase this loss. It is already not sustainable over decades.

Nonetheless, the gauntlet must be taken up. Artificial intelligence in the hands of adversaries makes deception a more central component of modern state-state conflict. As constructed today, cyberspace draws foreknowledge and resources closer in time, accentuates the loss of distance as a buffer, and increases the ease and speed of acquiring a higher volume of more precise data. As a subset of cyber, mature AI systems make analysis faster, foreknowledge more accurate, and actions more effective. However, as a subset of cyberspace, AI massively enhances the value of successful deception. If systems operating at the speed of AI systems can be fooled, misfed, redirected, or corrupted, adversaries or defenders gain invaluable benefits in an otherwise complex, fast-paced, and systemic struggle. Lack of national (strategic) or operational foreknowledge (either through normal accident, direct attack, or deception) could be crippling in the wars of the future—ones that will be digitized and laden with deception from multiple sectors as attackers and defenders each try to manipulate systems’ foreknowledge and abilities to act in their own favor.

Deception in this new world is more than surprise. John L. Casti, the developer of the “science of surprise,” notes that surprise is when our anticipations do not match the reality we face.^([18](#24_Chapter16.xhtml#fn18)) In his Western military classic, Carl von Clausewitz states, “Surprise lies at the foundation of all undertakings without exception, only in very different degrees according to the nature of the undertaking and other circumstances.”^([19](#24_Chapter16.xhtml#fn19)) The very complexity of a digitized world greatly rewards the state actors able to obscure their own operations, level and sources of resilience, and likely actions while still maximizing the timeliness and comprehensiveness of their own foreknowledge stocks and the amount, readiness, and appropriateness of their resources systemically. Rather than wait for the adversary to move into a position more favorable to oneself, one arranges for the adversary to believe that choice is good for them.

In any case, the major adversaries today already recognize this rising reality, and they are widely engaged in control of key information sources globally through their state champions and social engineering campaigns. As previously noted, Xi Jinping is very fond of Sun Tzu. In addition to his emphasis on deception, Sun Tzu is famous in large part for his similar observation about speed, concentration of forces, and prevailing without excessive losses. In particular, the Chinese leader’s fondness for Sun Tzu’s teaching centers on the requirement to “outwit, outsmart, and deceive opponents in order to turn weakness into strength and achieve the desired outcome without shedding blood and fighting.” Surprise may accompany the end of the deception campaign, but as Michael Howard observes, deception is “plant\[ing\] in the adversary’s mind an erroneous image … to affect the actions of the adversary” before they are surprised.

The United States and its allies need to move rapidly into a competitive, collective position in this emergent AI/cybered world. Mastering the emergent technologies will be at the heart of winning in any contest. Mastering AI/cybered deception, whether in defending or in offense, is doubly important when one represents a global minority of states, each individually weaker than the major adversaries. There is no choice but to learn how to defend and prosper in spite of this deception challenge—and it is likely to require considerable structural, technical, and narrative changes for success.

## **NAVIES, DECEPTION, AND RETHINKING STRUCTURES FOR AI/CYBERED CONFLICT**

While not viewed as heroic or noble in Western military contexts, deception is a meta-category of systemic conflict in the coming world. To respond accurately and quickly enough, the U. S. Navy and its allied services will have to formally recognize the coming reality of being a key defender for a minority community of democratic states forced to embrace deception as they move into the truly digitized world, including preparing for both surprise and false knowing in advance, during, or after the surprise. The service will have to adapt the lessons of past conflicts without assuming that it or its nation automatically has the scale, strategic coherence, or foreknowledge advantages enjoyed since 1945.

The U.S. military is a formidable and battle-experienced force. However, in the various conflicts that have occurred since 1991, the U. S. joint force has had the luxury of vast amounts of mostly accurate information, obtained by a wide array of sophisticated, technically cutting-edge sensors and processes by a variety of information systems. By and large, these networked systems have been resistant to extremes of deception, mostly because the United States and her allies have faced less technologically sophisticated opponents or small groups that—despite having some high-tech–capable individuals—did not have the scale to electronically attack core networks or the vast array of sensors and systems. Such will not be true if hostilities occur against technologically sophisticated and innovative authoritarian (“great”) powers. Such is not true today in the current system-versus-system struggle for the security of democratic cyberspace. Since the commercial development of cyberspace has sacrificed security for capability and profit, the flaws in the underlying substrate mean that even the tightest crypto-guarded application can be hacked if a wealthy government wants to expend the effort.

## Navies Have Always Employed Deception in Operations

Ironically, deception should be a natural topic for maritime discussions in any case, but even more so for defensive maritime forces in a deeply cybered, hostile, and post-Western world. In military operations historically, deception by means of camouflage, feints, decoys, false signals, electronic wartime reserve modes, and so forth has always been a feature of war, including naval warfare and modern cybered conflict.^([20](#24_Chapter16.xhtml#fn20)) Nonetheless, for modern Westernized ground forces, deception is eschewed in favor of sheer mass of lethal platforms and soldiers. For air forces, the mass is in the munitions dropped once the antiaircraft artillery defenses are neutralized. Armies work on outnumbering each other, while air forces focus on outpacing adversaries. These commanders engage in deception as a secondary operation as needed, especially if they are outgunned. For these large formations of land and air forces, deception is the exception or a useful accessory depending on force ratios, timing, and other factors. As a result, army and air force scholars and retired practitioners discuss deception readily, even if casually.

Oddly enough, Westernized navy scholars and retiree-authors do not extensively discuss deception,^([21](#24_Chapter16.xhtml#fn21)) even though the service has an arguably deeper relationship with it. Navies have used the stratagem writ large for centuries to expand the gap between an attacker’s foreknowledge and their ability to bring resources to bear to act successfully on that knowledge. From false flags of affiliation to alleged fishing trawlers suddenly becoming missile-armed military vessels or intelligence-gathering platforms, navies have overcome their own—or exploited others’—weaknesses in concentration of forces, numbers, and even weather by methods of obscuration and convincing, well-timed false impressions.

This use of deception is not by strategic preference, but by practical necessity. Naval forces are physically concentrated on ships, unable to spread out like armies or fly individually in all directions like air forces if they are surprised or suffering critical failures. The loss of a single platform in a navy costs the overall force proportionately much more than it does in an army or a reasonably sized air force. Throughout history, naval captains have directed their ships to lurk or loiter in order to catch the best winds, the best fog, the best tidal flow, or the unsuspecting adversaries in ports, down rivers, or on seas. Navies thus have developed unique talents that invisibly encourage the embedded application of deception, even if the concept is disdained among Westernized warrior classes.

A modern expeditionary (blue water) navy is more inherently self-sufficient than either of its ground- or air-based sister services in terms of its ability to use deception. Its forces can loiter deceptively, dispersed at great distance, and for considerable time. They routinely seek cover from the weather and also use the weather to hide from the planes and satellites of adversaries. At the tactical level, the employment of deception is even more obvious. In the age of fighting sail, it was acceptable to fly a false flag as a *ruse de guerre* prior to an engagement. Of course, prudent captains expected such and approached warily, searching for additional information. Arguably, then, renewing the older relationship to deception as an adaptive response of modern large-scale navies to the coming AI/cybered conflictual world should be less challenging than introducing equivalent changes in their fellow air and ground forces.

## Naval Culture Traditionally Accepts Independent Operations by Warship Captains

In a fully cybered, widely distributed, and AI-resilient maritime force, long loiter capacity is one key to prevailing in cybered conflict; the others include the ability to act independently and disconnected and yet complete operations furthering the overall strategic mission. For that, the main combatant in a navy—the ship’s captain—needs to have the confidence, training, and socialization necessary for informed, successful, independent decision-making. Only the navy has such a small number of critical combatants; neither soldiers nor pilots—the key combatant in their respective services—have the same authority, capabilities, and institutional history of decisions with strategic effects as do warship captains. This is one of the reasons the concept of mission command is a prominent feature of navies, as noted in chapter 7.

As the captain goes, so goes the ship and all its capabilities.^([22](#24_Chapter16.xhtml#fn22)) Traditionally, navies function by captains fooling each other while grappling with the demands of the otherwise neutral weather gods. Ingrained at a profound level among warships’ captains, then, was the acceptance of deception as a part of the routine defense or stratagem used for centuries, not an exceptional tactical or strategic option. The loss of the independence of the individual platform commander was coterminous with the rise of the huge, modern Westernized fleet in the U.S. Navy during and after World War II. Until then, even in the U.S. Navy, admirals sent orders to captains of ships as “suggestions,” and many captains chose to treat them that way.

World War II was a four-year lesson for the United States in more than operations research on strategic bombing targets and results; it also spurred enormous interest in and research on how to structure, analyze, manage, and control exceptionally large formations of military services.^([23](#24_Chapter16.xhtml#fn23)) During the Cold War, outlier or wayward behavior by commanders not acting as centrally expected became increasingly less acceptable for a host of management and analysis struggles to efficiently operate an organization of the size of the U. S. military. Plus, with such overwhelming military dominance, the U.S. strategy of attrition did not need the innovative or accidental discoveries that independent action often produces.

The U. S. Navy was not immune from the natural tendency of managers to seek greater control of uncertainty. Digital connections encourage the urge to micromanage, especially if the leaders involved are responsible for large, diverse, and dispersed forces whose traditional culture encouraged wayward, unexpected actions by warship captains. Like the other services, the modernized Navy developed over time the “no-fail” bureaucracy led by a Department of Defense averse to bad press.^([24](#24_Chapter16.xhtml#fn24)) Nonetheless, naval officers are still socialized on the independent, surprising, and often deceptive histories of Nelson, Halsey, and others.

Today, these officers admire those independent captains and prefer their culture while nonetheless complying with the strict confines of modern integrated naval operations. It is this dual culture among naval officers that offers the best chance of wider organizational adaptation to a new Navy organized for deception across all AI/cybered systems, and for the challenges of defending democracies as a minority community.

## Modern Navies Are Technical Services

Adapting to AI/cybered conflict with new structures and strategies including deception, decoupled long loiters, surprising actions, and keeping the larger forces of authoritarian states at bay will require deep familiarity with technology (as noted in chapter 13) along with presumption of independent decision-making by ship commanders. Modern navies, especially the U.S. Navy, encourage both, making them more initially capable of absorbing the new lessons of this kind of world. Under the right sets of circumstances, that combination of skill and worldview should also be amenable to experimentation and wider innovation across a multitude of organizational forms, behaviors, tools, techniques, and leadership styles. Some subset of officers will inevitably emerge who are skilled in the technologies, confident (and successful) as independent leaders, and capable of adapting both to the survival needs of the Navy and the nation as one of a small community of nations intending to survive as democracies. If their experimentation is organizationally encouraged and their lessons absorbed, they are more likely to provide the paths by which much deeper forms of systemic deception can be faced, defended against, used as appropriate and acceptable, and overcome in adversary campaigns without losing the essential democratic nature of the nation in the process.

## **DIFFERENT NARRATIVE AND STRUCTURE FOR FLEET FORCES: MORE SLY THAN SYNCHRONIZED**

Once maritime leaders embrace what they have always viewed as a regrettable necessity—deception—and the new global reality as a minority community, they will need to successfully adopt it on all levels into their narrative, structures, and strategic/operational planning, especially in AI implementations. Their collective defense will depend greatly on whether their maritime forces are able to escape the vulnerabilities of physical concentration of forces in ships and transform into resilient, dispersed, decomposable, effective employers of deception for survival and defense of national well-being.

The challenge is considerable for any military service, of course. Cybered conflict increasingly riven with AI systems, then, particularly challenges maritime commanders to acknowledge the role of deception as both a shield for and Achilles’ heel of their operations. While the concentration constraints have traditionally made deception essential, warrior cultures rarely idolize the liar, even if they achieve missions without engaging in battles. Had Nimitz hidden behind Guam and sunk the Japanese naval fleets at long range without ever having to take shots to his own fleet, military historians would have noted the success but moved on.^([25](#24_Chapter16.xhtml#fn25)) The World War II story is intrinsically one in which deception won the day, but the sacrifices of the ships, captains, and crews are what fill the history books. Hence, the move to designing and operating an entire force deceptively is a cognitive challenge of the digitized world that is arguably greater for maritime leaders than it is for ground or air leaders. The latter recognize the challenge because being constantly deceptive is something different. If they accept it, it will not be the continuation of a practice engaged in reluctantly in the past. All will have to deal with the deception potential of cyber/AI in their operations, but naval commanders will have to accept that this necessity is also the best way to fight.

AI/cybered conflict in the emerging world requires a different narrative and accompanying rationalizations for behaviors and choices. In AI/cybered systemic warfare, for example, dispersion and redundancy will be more important system resilience guidelines than physical concentration of forces or centralization of control. The current hyperbolic promotion of AI emphasizes centralized control of all data and analysis. Given the scattered and disparate nature of most networks in most large services, seeking that level of central visibility over what one has is hardly undesirable. It is, in short, both a necessary and an urgent need not only in order to implement current forms of AI but also simply to know what, how, where, and what adversary cyber campaigns may target before the target is had. However, crucial deeper levels of thinking about—and then acting on—this AI/cybered implementation are often pushed off or ignored entirely.

Mapping one’s own networks is urgent and using AI/cybered as the incentive and the goal is useful, but that is only second-order thinking. The Navy needs to engage in third-, fourth-, fifth-, and sixth-order thinking. It must be prepared for when naturally occurring complex system surprises cause errors to ripple throughout the centralized enterprise (third-order question). It must be prepared and organized to know and respond when adversaries have induced or enhanced these ripples (fourth order). The fifth-order challenge is to set up the systems to be able to determine if deception has played a role in the events and, further, to respond appropriately. Finally, the sixth-order challenge is to use the desire of adversaries to deceive from within our systems against the adversary in return. It is a level at which innovation, narrative, structures, systems architecture, and introspective design blend. This level of analysis begins with rethinking systemically the maritime strategy, stories, tools, and structures to embed deception, AI/cyber, and a changed global distribution of scale and power.

## Rethink AI/Cyber Sources and Assets Choices, Designs, and Operations

From the outset, the lessons of large-scale complex adaptive systems can be merged with those of deception in the design and deployment of AI/cyber systems. Especially relevant are the three basic empirically driven recommendations for every complex enterprise faced with possible multiple-source, urgent systemic surprises: (1) ensure a redundancy of knowledge sources at the point of surprise—not replication of the same kind of source; (2) ensure slack in time before surprise events or cascades can intrude or accelerate through systems; and (3) engage in constant forms of discovery and trial-and-error learning across the whole system.^([26](#24_Chapter16.xhtml#fn26)) The central challenge is how a modern navy does this in preparing for an AI-dependent, deception-prone, peace and wartime cybered conflict situation.

Deception needs to be embedded as a defense concern and offense consideration at all levels from tactical to strategic. At the tactical level, in principle, the greater the number of sensors, the harder it is to achieve deception using nondigital means. Obscurants can blind optical sensors, but they do not affect electronic warfare systems. Signals deception can be countered by optical detection.^([27](#24_Chapter16.xhtml#fn27)) However, even at the tactical level, no sensor arrays are to be routinely trusted, as that pattern of standardized behavior will in itself create the opportunity for adversary use of deception once discovered.

AI analysis based on sensor data is valuable for its speed, but AI internalized adjudication must make a correct judgment when its sensors provide conflicting information, and the process must vary defensively. The automated rules for sorting out what is deception and what is not will need to have variable validity testing using a variety of deception tests, lest the standardization or routinization of these tests again provide opportunities to fool the test mechanisms.^([28](#24_Chapter16.xhtml#fn28)) Even using a method of voting across suspected sensors and restricting trust to 60 percent unanimity means, for example, the adversaries need only create contrary data inputs 41 percent of the time to stall, stymie, or put decision-making at a disadvantage. Standardized systems, processes, and accompanying algorithmic assessments are a major challenge in defending against cyber/AI-advanced adversaries. If the deceptive adversary is successful, defenders will still be constantly scrambling to compensate for the shortcomings of the deceived AI/cybered systems installed to compensate for human inadequacies.

One solution that has been proposed is to restrict the use of AI itself to, perhaps, primarily military administrative functions, but not to rely on it for critical operations. But that does not avoid most of the deception challenges from supply chains and merely redirects adversaries to distorting operations up to the point of deployment. Adversaries are already there in cybered operations. Restricting AI to functions is no apparent help.

Furthermore, it is currently unclear if any commercial off-the-shelf (COTS) AI system can actually do what is required here.^([29](#24_Chapter16.xhtml#fn29)) This difficulty is why having in-house cyber/AI talent is critical for navies, not only to check the design of COTS, but to design the AI/cyber systems from the outset for the systemic needs of a new navy adapted to the coming world. Much is made of IT talent’s unwillingness to work for the government, but that is a failure of the narrative to mobilize these actors to stand up to the rise of authoritarianism in structures organized for the longer-term survival of the system under which they benefit. As long as they—and the professors who teach them—believe democracy as a whole can never be destroyed (especially not economically), democracies are not a global minority but dominant and desired by everybody, and that their effort is not essential for the defense of this system, then they will not design the IT systems essential to government and the private sector for whole-of-society defense and well-being.^([30](#24_Chapter16.xhtml#fn30))

Deception detection requires extensive knowledge and the tools to act accordingly, as well as the commensurate narrative rationalizing operations and, as discussed below, appropriate organizational design. For the coming world, the U.S. Navy and its allies need to transform into introspective forms of organization, designed for positive identification on all elements and actions, especially the supply and logistics chains.

This level of visibility is arguably only doable with sufficient AI/cybered tools to track the lifeblood of the organization. But it is not merely an option. Even for cyber security, an enterprise process of least privilege requires just such panoptic identification, and AI/cyber implementation deepens the need for a systemic architecture that makes roles and responsibilities clearly attached to this positive identification.

Rethinking the organization for the new reality means, at a minimum, having its systems constructed and sourced so that a basic cross-correlation of roles, responsibilities, authorizations, and identifications is achievable and understandable across multiple diverse nodes. If adversaries are thereby forced to corrupt multiple components in a consistent long-term or synchronized controlled fashion to assure achievement of the deception effects, then the “work factor” burden involved in their AI/cyber campaigns becomes enormous.^([31](#24_Chapter16.xhtml#fn31)) At the very least, the costs become enormous, and the volume of such attacks is likely to slow or even atrophy.

Moreover, this comprehensive identification needs a justifying narrative, and it is advanced if the talent is brought into daily contact with the knowledge available and needed for operations, including deception. The traditional separation of knowing and acting does not work well in the coming forms of conflict; having separated intelligence and networks operations, for example, is counterindicated for the speed and complexity of this new systemic conflict. Here, the U. S. Navy’s early N2/N6 (information dominance) innovation is helpful in demonstrating the need to bring the military’s IT and intelligence talent into the same unit for cross-pollination of narratives and skills.^([32](#24_Chapter16.xhtml#fn32)) In a similar vein, although it is insufficiently used in strategic communications, the combination of the National Security Agency and U.S. Cyber Command under one commander is a close equivalent; the combined operations—and tool design, development, and use—have a similar effect.

## Dispersed Operations versus Decoupled Operations

The U.S. Navy needs to rethink dispersed operations versus decoupled operations with different asset configurations. While the concerns for deception defense in AI/cyber systems argue for embedded panoptic identification, the organization as a whole is neither required nor encouraged to be or stay centralized in large nodes. Rather, resilient large-scale complex socio-technical-economic systems gracefully decouple down to minimally self-sustaining elements in relevant time, keep operating, and assure mission continuity at minimally acceptable levels for extended periods. In maritime settings, these systems are likely to be located on vessels that themselves can operate independently and then easily recouple (regroup) effectively, gracefully, and operationally smoothly, while still being hard for an opponent to geographically locate. Ideally, those AI systems under attack can be taught to degrade gracefully, recognizing and warning their users about the oncoming loss of functions and contributions. Recent analysis at the Naval Postgraduate School on the vulnerabilities of networks in peer (or near-peer) warfighting with a highly contested electromagnetic spectrum has led to the concept of “network optional warfare,” in which naval units have systems that remain at least partially effective even if disconnected (or disrupted) from the fleet information network.^([33](#24_Chapter16.xhtml#fn33))

Defending a minority of states in the coming world, U.S. and allied naval commanders will have to find ways to protect themselves and their capabilities in a deeply digitally deceptive and equally transparent world. Technological advances are unlikely to be adequate when complexity science and history suggest the very concentration of force capabilities on ships—and then on collocated fleets or task forces—can prove to be the singular major disability. Concentration of force is taught universally throughout military institutions across the Westernized democracies and, in the abstract, it is likely to always be desirable. However, in cybered conflict permeated by AI systems and the potential for adversaries to have massive amounts of foreknowledge and hence greater accuracy and speed in actions, concentration of forces can easily mean concentration of high-value targets in the digital battlespace. Deception and dispersion may be the most effective suppression and survival strategies, especially for the opponents with smaller-scale resources and presence.

This adaptive response is already an objective of the distributed maritime operations (DMO) concept. If AI is going to be widely adopted, however, it needs to be used in the creation of deception operations as an integral part of DMO. And these operations will then challenge preferred operational control structures. Current AI development promotions—especially for large organizations—often appear to ignore the lessons of cyber and deception and argue for a form of centralization to both maximize AI efficiencies and reduce costs. Arguably, successful cybered warfare is more similar to modern naval warfare than land warfare in that dispersion and redundancy seem generally more important principles than concentration of forces, especially for states that will be part of a minority community in the coming authoritarian globe. If AI centralizes systems and yet is vulnerable to deception, mistakes could result in cascading systems errors at digital speeds.

This concentration vulnerability has subtleties. For example, an AI-dependent navy—particularly one whose operational decision-making is concentrated in fleet maritime operations centers (MOCs)—would be “informationally concentrated,” even if the ships are physically dispersed.^([34](#24_Chapter16.xhtml#fn34)) Instead of the fleet being the enemy’s primary target, the MOC becomes the primary target. If it can be targeted nonkinetically by penetrating its AI system, the spirit of Sun Tzu would be propitiated.

The U.S. Navy has expended much time and resources in the creation of the fleet MOCs as the means of providing information and command and control of the fleet under the DMO concept. In essence, the fleet MOCs are intended to replace the command and control previously concentrated on aircraft carriers within carrier battle groups. Presumably, the battle group ships can then be dispersed, and the carrier hidden by electronic emissions control. The physical dispersion should also facilitate physical deception. If AI is adopted as a primary decision aid, under this disposition it would most likely be concentrated in the MOCs (as discussed in chapter 12). Is not the fleet therefore intellectually/informationally concentrated? Which is easier to deceive—the MOC, which has access to more national technical means information, or a battle group engaged in the actual combat? AI calculations are based on probabilities. Probabilities are that—in a contested electronic spectrum—the MOC would be easier to deceive.

The best of all possible solutions to the AI/cyber, deception, and maritime solutions outlined in this chapter is not yet known. But the balance of probabilities argues that a navy with a new narrative and structure directly embedding AI/cyber and deception in its thinking is likely to find solutions that are good enough.

This naval force is likely to be dispersed electronically and physically and able to use its AI configurations dynamically for the following three missions. First, its ships can operate independently for some time despite challenges from a trustless approach to its AI/cybered systems. Second, these forces competently use their AI assets to detect and neutralize penetrations and deceptions and to conceal routinely all related activities. Third, these mobile, and hard-to-find, globally deployed assets can also participate in continuously engaged AI campaigns meant to deceive back into adversaries’ AI/cyber systems. Ships as Janus-like double agents, defending an otherwise vulnerable minority of consolidated democratic communities, are likely to be critical surprise vectors, disturbing the larger, more numerous campaigns of key adversaries for some years to come. In short, the properly attuned maritime force is able to “sea-hack” the adversary, turning Sun Tzu and threats to the navy and the nation on their heads.

## **BRINGING DOUBT TO AI**

Returning to the initial questions asked by this chapter, are there any answers we can provide? Can AI be taught not to trust its own knowledge or judgment? The most current answer—reinforced by a reading of all the other chapters—is “no.” Except for the aspect of the spoofing of networked sensors and data poisoning on the Internet, the whole concept of deception seems antithetical to the scientific decision-making that led to the development of AI as a new method of rapidly compiling and analyzing data—a search for knowledge, as it were. In popular media, there have been many anecdotal, humorously written news articles on how particular AI image recognition systems have mistaken a squirrel for a sea lion or a crocodile crossing the road for a unicycle.^([35](#24_Chapter16.xhtml#fn35)) However, from the developers’ point of view, there seemed no purpose to create AI systems that would doubt themselves. Doubt was for humans, not machines.

If AI *can* be programmed to detect or learn to detect deception, it would seem easiest to do that at the tactical level, since that is where the relationship between AI decision-making and sensor data is the closest. Likewise, the closer the human operators are to the actual sensors and sensor data, the more likely they will detect the presence of deception, even when the AI system assisting them has not detected it. This form of tactical adaptation was illustrated by the scenario in chapter 6. In other words, humans at the tactical level would find it easier to override the AI that is being phooled.

We need to bring deception into military AI applications as a potential element of the information examination and processing cycle. Similarly, it could be an output to stratagems designed to phool the enemy. However, we also need to consider the fact of deception in our decisions to adopt AI to advise or make decisions, since it is uncertain how to induce doubt into machines. Perhaps we will not be able to, or—if we do—AI will give us only a marginal advantage (speed) over other forms of computation or human instinct and intuition. Many chapters have discussed the OODA loop, but they have not incorporated a cycle of “observe deception,” “orient correctly despite deception,” “decide what is true,” and “act only on accurate (not all) information.” It might be that humans can do this more quickly than narrow AI under the intelligence principle that “if there is doubt, there is no doubt.” Doubt needs to be a factor in the very decision to acquire and apply AI to complex decision-making.

### **NOTES**

# 17

Overcoming Impediments to AI for Unmanned Autonomy and Human Decision-Making

GEORGE GALDORISI

**If you have read the preceding chapters** and have not formed the opinion that big data, artificial intelligence (AI), and machine learning represent a revolution in military affairs, that our peer adversaries—and others—are determined to harness these technologies to ensure that their military forces can dominate ours, and that the United States has clearly articulated the intent to leverage these same technologies to provide our warfighters with an edge in combat, then this chapter is likely unnecessary.

On the other hand, if you believe that the U.S. military intends to move forward as rapidly as possible to harness big data, artificial intelligence, and machine learning to make the platforms, systems, sensors, and weapons it employs more effective and efficient, the natural reaction might be to assume that we will, to borrow a military term, “move out smartly” and do just that. As you have read previously, the highest levels of national and security leadership have directed that this happen and are funding a wide array of AI programs and projects.

Yet the way ahead is not without impediments. By way of analogy, in recent years we have seen large technology companies—represented most prominently by the so-called FAANG Five (Facebook, Apple, Amazon, Netflix, and Alphabet’s Google)—come under intense scrutiny for a number of reasons, but primarily for either purposefully or negligently losing control of their data or having AI do things detrimental to the interests of their customers. At the end of the day, however, even the most egregious data breeches by these corporations don’t cost people their lives.

This is not the case with military weapons systems that employ AI. The bar is much higher for the U.S. Department of Defense (DoD) in assuring the American public that—to borrow a phrase from the medical profession—AI-enabled military weapons systems will “first, do no harm.” And while policy documents have clearly articulated the requirement to have a human “in-the-loop” when lethal unmanned systems are employed, pieces of paper may not be enough to assuage the public’s concern, a concern built up over a half-century of a steady diet of media showing how “killer robots” can turn on their human masters. It is worth reviewing just how deeply these concerns are embedded in the American psyche to understand what DoD must do to mitigate these fears so that the U. S. military might reap the full advantages of AI.

## **DOD COMMITMENT TO BIG DATA, AI, AND MACHINE LEARNING**

As you have seen in the foregoing chapters, the potential of big data, artificial intelligence, and machine learning to transform warfare is virtually unlimited. As William Roper, former director of the DoD Strategic Capabilities Office, noted, “Weapons autonomy undergirded by AI is the biggest thing in military technology since nuclear weapons.”^([1](#25_Chapter17.xhtml#fn1)) More recently, author Chris Ford put it this way: “Autonomous weapons—those weapons that can select and engage targets without human intervention—herald perhaps the most fundamental change in warfare in generations.”^([2](#25_Chapter17.xhtml#fn2)) However, the U.S. military’s embrace of big data, artificial intelligence, and machine learning is not assured. While DoD policy directives are clear that a human must be “in the loop” (not just “on the loop”) when lethal unmanned systems (UxS) are employed, this may not be enough.^([3](#25_Chapter17.xhtml#fn3)) As many of the previous chapters have noted, the American public, fed a steady diet of books and movies about “bad” robots (e.g., *War of the Worlds, The Terminator*) and even about “good” robots gone rogue (e.g., *2001: A Space Odyssey, Ex Machina*), are fearful that the U.S. military might lose control of its armed unmanned systems.

These concerns have manifested themselves in many ways, most notably in Google discontinuing work on DoD’s Algorithmic Warfare Cross-Functional Team, otherwise known as Project Maven.^([4](#25_Chapter17.xhtml#fn4)) Beyond these headline-grabbing stories, a great deal of thoughtful work has been published regarding the efficacy of using unmanned systems, especially lethal ones, in warfare. Sadly, these books have not gripped the public’s attention to the extent that popular media have.

Unless or until the ethical concerns regarding the use of big data, artificial intelligence, and machine learning by the U.S. military—and *especially* in military unmanned systems—are addressed in a way that is compelling enough to help the American public accept the U.S. military’s use of these technologies, their enormous potential may never be realized, putting U.S. warfighters at an enormous disadvantage on the battlefield. And while big data, artificial intelligence, and machine learning will be used in a vast array of platforms, systems, sensors, and weapons *other* than unmanned systems, the public’s attention is—understandably—primarily focused on these platforms.^([5](#25_Chapter17.xhtml#fn5)) Therefore, the U.S. military’s focus must be on demonstrating that AI-enabled unmanned systems will “first, do no harm.” The reasons for this emphasis are compelling and will be explained below.

## **THE POTENTIAL DARK SIDE OF UNMANNED SYSTEMS AUTONOMY**

One of the most iconic films of the last century, Stanley Kubrick’s *2001: A Space Odyssey*, had as its central theme the issue of the autonomy of robots (the unmanned vehicles of the time). Few who saw the movie can forget the scene where the astronauts consider disconnecting the cognitive circuits of their computer, named HAL (for Heuristically programmed ALgorithmic computer), when it appears to be mistaken in reporting the presence of a fault in the spacecraft’s communications antenna. They attempt to conceal what they are saying but are unaware that HAL can read their lips. Faced with the prospect of disconnection, HAL decides to kill the astronauts in order to protect and continue its programmed directives.^([6](#25_Chapter17.xhtml#fn6))

While few today worry that a twenty-first-century HAL will turn on its masters, the issues involved with fielding increasingly autonomous unmanned systems are complex, challenging, and contentious. Kubrick’s 1968 movie was prescient. More than half a century later, while we accept advances in other aspects of unmanned systems improvements such as propulsion, payload, stealth, speed, endurance, and other attributes, we are still coming to grips with how much autonomy is enough and how much may be too much. This is arguably *the* most important issue we need to address with respect to military unmanned systems over the next decade. These ongoing debates have spawned a cottage industry of books that attempt to address in a thoughtful manner the complex issue of AI, autonomy, and unmanned systems, especially armed military unmanned systems.^([7](#25_Chapter17.xhtml#fn7))

Unmanned systems will become more autonomous in direct proportion to their ability to sense the environment and adapt to it. This capability enables unmanned systems to achieve enhanced speed in decision-making and allows friendly forces to act within an adversary’s OODA (observe, orient, decide, act) loop.^([8](#25_Chapter17.xhtml#fn8)) As the environment or mission changes, the ability to sense and adapt will allow unmanned systems to find the optimal solution for achieving their mission, without the need to rely on constant human operator oversight, input, and decision-making. But while we need unmanned systems to operate inside the enemy’s OODA loop, are we ready for them to operate without our decision-making—to operate inside *our* OODA loops?

An article in *The Economist* entitled “Morals and the Machine” addressed the issue of autonomy and humans-in-the-loop this way:

As they become smarter and more widespread, autonomous machines are bound to end up making life-or-death decisions in unpredictable situations, thus assuming—or at least appearing to assume—moral agency. Weapons systems currently have human operators “in-the-loop,” but as they grow more sophisticated, it will be possible to shift to “on the loop” operation, with machines carrying out orders autonomously.

As that happens, they will be presented with ethical dilemmas. Should a drone fire on a house where a target is known to be hiding, which may also be sheltering civilians? Should a driverless car swerve to avoid pedestrians if that means hitting other vehicles or endangering its occupants? Should a robot involved in disaster recovery tell people the truth about what is happening if that risks causing a panic?

Such questions have led to the emergence of the field of “machine ethics,” which aims to give machines the ability to make such choices appropriately—in other words—to tell right from wrong. More collaboration is required between engineers, ethicists, lawyers and policymakers, all of whom would draw up very different types of rules if they were left to their own devices.^([9](#25_Chapter17.xhtml#fn9))

In an op-ed in the *New York Times* entitled “Smart Drones,” Bill Keller put the issue of autonomy for unmanned systems in another way:

If you find the use of remotely piloted warrior drones troubling, imagine that the decision to kill a suspected enemy is not made by an operator in a distant control room, but by the machine itself. Imagine that an aerial robot studies the landscape below, recognizes hostile activity, calculates that there is minimal risk of collateral damage, and then, with no human in the loop, pulls the trigger.

Welcome to the future of warfare. While Americans are debating the president’s power to order assassination by drone, powerful momentum—scientific, military and commercial—is propelling us toward the day when we cede the same lethal authority to software.^([10](#25_Chapter17.xhtml#fn10))

More recently, while it may seem counterintuitive, concerns about autonomous machines and artificial intelligence are also coming from the very industry that is most prominent in developing these technological capabilities. An article in the *New York Times* entitled “Robot Overlords? Maybe Not” quoted Alex Garland, director of the movie *Ex Machina*, who talked about artificial intelligence and quoted several tech industry leaders: “The theoretical physicist Stephen Hawking told us that ‘the development of full artificial intelligence could spell the end of the human race.’ Elon Musk, the chief executive of Tesla, told us that A.I. was ‘potentially more dangerous than nukes.’ Steve Wozniak, a co-founder of Apple, told us that ‘computers are going to take over from humans’ and that ‘the future is scary and very bad for people’.”^([11](#25_Chapter17.xhtml#fn11))

DoD is addressing the issue of human control of unmanned systems as a first-order priority and has issued policy direction to ensure that humans *do* remain in the OODA loop. A directive by then–Deputy Secretary of Defense (and later Secretary of Defense) Ashton Carter issued the following guidance in 2012:

Human input and ongoing verification are required for autonomous and semi-autonomous weapons systems to help prevent unintended engagements. These systems shall be designed to allow commanders and operators to exercise appropriate levels of human judgment over the use of force. Humans who authorize the use of, or operate these systems, must do so with appropriate care and in accordance with the law of war, applicable treaties, weapon system safety rules and applicable rules of engagement. An autonomous system is defined as a weapon system that, once activated, can select and engage targets without further intervention by a human operator.^([12](#25_Chapter17.xhtml#fn12))

These are the kinds of directives and discussions that are—and should be—part of the dialogue between and among policymakers, military leaders, industry, academia, and the science and technology community as the design and operation of tomorrow’s autonomous systems are thoughtfully considered. As then–Deputy Secretary of Defense Robert Work noted during his remarks at the Center for a New American Security Defense Forum, “We believe, strongly, that humans should be the only ones to decide when to use lethal force. But when you’re under attack, especially at machine speeds, we want to have a machine that can protect us.”^([13](#25_Chapter17.xhtml#fn13))

It is one thing to issue policy statements, but quite another to actually *design* autonomous systems to carry out the desired plan. This is a critical point from a policy perspective, because although one can choose to abdicate various levels of decision-making to an autonomous machine, one cannot escape responsibility for the resulting actions.^([14](#25_Chapter17.xhtml#fn14)) In highly autonomous platforms, the system may become opaque to operators, and they frequently ask questions such as: What is it doing? Why is it doing that? What’s it going to do next?^([15](#25_Chapter17.xhtml#fn15)) It is difficult to see how an operator can fulfill his or her responsibility for the autonomous system’s actions if these questions are being asked.

## **UNDERSTANDING THE CHALLENGES OF EMPLOYING MILITARY UNMANNED SYSTEMS**

In an address at a military-industry conference, Peter Singer offered an analogy to help understand the issue of the military’s use of AI-enabled unmanned systems. He noted, “What is playing out in driverless cars is also playing out in military UxS. You will never be able to ‘engineer out’ all of the ethical dilemmas surrounding the use of military UxS.”^([16](#25_Chapter17.xhtml#fn16))

Those responsible for the concepts, research, development, building, fielding, and use of these systems might be well served to look into the commercial trade space, to the automobile industry, for best practices examples. It is here that we may well find the vital customer feedback that indicates what drivers *really* want. And while not a perfect one-to-one match, this analogy can suggest what kinds of unmanned systems supported by big data, artificial intelligence, and machine learning that industry should offer to the military.

Automobiles are being conceived, designed, built, and delivered supported by increasing degrees of big data, artificial intelligence, and machine learning. It is worth examining where these trend lines are going. Put a bit simplistically, automobiles can be broken down into three basic categories: a completely manual car—something your parents drove; a driverless car that takes you where you want to go via artificial intelligence;^([17](#25_Chapter17.xhtml#fn17)) and a car with augmented intelligence—all under the driver’s control.^([18](#25_Chapter17.xhtml#fn18))

The initial enthusiasm for driverless cars has given way to second thoughts regarding how much a driver might be willing to be taken completely out of the loop. One article in particular in the *New York Times*, “Whose Life Should Your Car Save?” captures the concerns many have about driverless cars and, by extension, about other fully autonomous systems:

We presented people with hypothetical situations that forced them to choose between “self-protective” autonomous cars that protected their passengers at all costs, and “utilitarian” autonomous cars that impartially minimized overall casualties, even if it meant harming their passengers. (Our vignettes featured stark, either-or choices between saving one group of people and killing another, but the same basic trade-offs hold in more realistic situations involving gradations of risk.)

A large majority of our respondents agreed that cars that impartially minimized overall casualties were more ethical, and were the type they would like to see on the road. But most people also indicated that they would refuse to purchase such a car, expressing a strong preference for buying the self-protective one. In other words, people refused to buy the car they found to be more ethical.^([19](#25_Chapter17.xhtml#fn19))

As the study referenced in this article—as well as an increasing number of analyses and reports—indicates, there is a growing consensus among consumers that drivers want to be “in-the-loop” and that they want semi-autonomous and not fully autonomous cars. That may change in the future, but perhaps not.^([20](#25_Chapter17.xhtml#fn20)) It is understandable that an American public that is conflicted about the future of its most basic means of transportation is equally perplexed—and therefore concerned—about the issue of AI-enabled military unmanned systems.

## **DESIGNING IN THE *RIGHT* DEGREE OF AUTONOMY IN UNMANNED SYSTEMS**

Most of us are familiar with the children’s fable *Goldilocks and the Three Bears*. As Goldilocks tastes three bowls of porridge, she finds one too hot, one too cold, and one just right. As DoD and the services look to achieve the optimal balance of autonomy and human interaction—to balance these two often-opposing forces and get them “just right”—designing this capability into tomorrow’s unmanned systems at the outset, rather than trying to bolt it on after the fact, may be the only sustainable road ahead. If we fail to do this, concerns that our armed unmanned systems will take on “HAL-like” powers and be beyond our control almost inevitably will derail the promise of these important warfighting partners.^([21](#25_Chapter17.xhtml#fn21))

Trying to determine what degree of autonomy is desired and how to achieve it is not a trivial undertaking and—as Albert Einstein famously noted—will require a new way of figuring out how to think about the problem. Importantly, most informed discussion begins with the premise that adversaries who intend to use unmanned systems against U. S. interests will not be inhibited by the kinds of legal, ethical, and moral strictures to which the United States adheres. Chapter 5 examines some of the incentives potential opponents may have in avoiding legal, ethical, or moral strictures. If potential opponents lack such restraints, would that provide them an advantage that would be fatal to our competitive efforts? That is unknown. Nevertheless, designing the right degree of autonomy into our unmanned systems is *the* central issue that will determine their success or failure.

The capabilities required to find this just-right balance of autonomy in military unmanned systems must leverage many technologies that are still emerging. The military knows what it *wants* to achieve but often not what technologies or even capabilities it *needs* in order to field UxS with the right balance of autonomy and human interaction. A key element of this quest is to worry less about what attributes—speed, service ceiling, endurance, and others—the machine itself possesses and instead focus on what is *inside* the machine. The Defense Science Board report, *The Role of Autonomy in DoD Systems*, put it this way: “Instead of viewing autonomy as an intrinsic property of unmanned systems in isolation, the design and operation of unmanned systems needs to be considered in terms of human-systems collaboration.… A key challenge for operators is maintaining the human-machine collaboration needed to execute their mission, which is frequently handicapped by poor design.… A key challenge facing unmanned systems developers is the move from a hardware-oriented, vehicle-centric development and acquisition process to one that emphasizes the primacy of software in creating autonomy.”^([22](#25_Chapter17.xhtml#fn22))

One need only attend an industry conference where unmanned systems are being displayed at multiple booths to understand that today the emphasis is almost completely on the machine itself. What is inside is typically not a primary consideration. But as the Defense Science Board notes, it is software that is the primary driver of capabilities. For example, the manned F-35 Lightning II has ten billion lines of computer code, and there is human supervision by the pilot. How many lines of code will need to be built into an unmanned system to get the balance of autonomy and human interaction just right?

Some of the controversy regarding military unmanned systems stems from a lack of precision in terminology. One way to help clarify this ambiguity is to ensure that when the word *autonomy* is used, it refers to the relationship between the person and the machine. Machines that perform a function for some period of time, then stop and wait for human input before continuing, are often referred to as semiautonomous or as having a human-in-the-loop. Machines that can perform a function entirely on their own but have a human in a monitoring role, with the ability to intervene if the machine fails or malfunctions, are often referred to as human-supervised autonomous or human-on-the-loop. Machines that can perform a function entirely on their own with humans unable to intervene are often referred to as fully autonomous or human-out-of-the-loop.^([23](#25_Chapter17.xhtml#fn23))

This suggests that we need to recalibrate some of the debate on autonomous weapons to more accurately distinguish between increased autonomy *in* weapons and *autonomous* weapons. In this sense, autonomy is not about the intelligence of the machine, but rather its relationship to a human controller.^([24](#25_Chapter17.xhtml#fn24)) For the relatively small numbers of unmanned systems that will engage an enemy with a weapon, this balance is crucial. Prior to firing a weapon, the unmanned platform needs to provide the operator—and there must be an operator in the loop—with a pros-and-cons decision matrix regarding what that firing decision might entail.

## **THE THIRD OFFSET STRATEGY AND MAN-MACHINE TEAMING**

We began this chapter with the thesis that unmanned systems that leverage big data, artificial intelligence, and machine learning have the potential to be critical partners to the joint warfighter. But this can only happen if the rapid—some would say galloping—technological advances in unmanned systems, big data, artificial intelligence, and machine learning take into account valid moral and ethical considerations regarding their use.^([25](#25_Chapter17.xhtml#fn25)) Perhaps most importantly, as senior U.S. officials have emphasized, from the DoD perspective, unmanned systems must *always* have the option for human control and verification, especially when it comes to the use of lethal force by AI-enabled unmanned systems. And as the Defense Science Board suggested, ultimately, it is human-machine collaboration that determines the utility of an unmanned system.

As presented (by a prominent champion) in chapter 2, DoD has embraced a third offset strategy to attempt to provide the United States with an asymmetric advantage over peer and other adversaries.^([26](#25_Chapter17.xhtml#fn26)) While there are many aspects to this strategy, one pillar deals with technology, and this pillar is critically dependent on big data, artificial intelligence, and machine learning to gain this advantage. As a subset of this technological focus, man-machine teaming is offered as a way to harness AI-enabled unmanned systems to gain a military advantage.^([27](#25_Chapter17.xhtml#fn27)) But what does man-machine teaming look like?

One way to address this is to consider one of the most recognized photographs from World War II (see photo 17-1). Taken by 1st Lt. John Moore of the U.S. Signal Corps, the photo depicts Gen. Dwight Eisenhower talking with men of the 101st Airborne Division on June 5, 1944, the day before the invasion of Normandy. Previously, Eisenhower had been briefed by Air Marshal Leigh-Mallory that the 101st was one of two units that would suffer 80 percent casualties during the invasion.

Those who study the impact of unmanned systems on military operations—especially those who are strong advocates of unmanned systems—can look at this photo and envision General Eisenhower speaking not with American airborne soldiers, but with robots that he will send into battle (see photo 17-2). Those who fear unmanned systems might picture the airborne soldiers as the photo depicts them, but instead of General Eisenhower, they would envision a robot commanding the soldiers—clearly an untenable situation (see photo 17-3). But those who thoughtfully consider the impact of AI-enabled unmanned systems on military operations would envision General Eisenhower addressing a team of American airborne soldiers standing with their robot partners (see photo 17-4). Clearly, more work needs to be done to fully address what manmachine teaming means to today’s military.^([28](#25_Chapter17.xhtml#fn28))

![Photo 17-1. Historical Pre-Invasion Speech](images/pg320_1.png)

**Photo 17-1**. Historical Pre-Invasion Speech

![Photo 17-2. Pre-Invasion Speech to AI Machine Troops](images/pg320_2.png)

**Photo 17-2**. Pre-Invasion Speech to AI Machine Troops

![Photo 17-3. Pre-Invasion AI Machine Speech to Human Troops](images/pg321_1.png)

**Photo 17-3**. Pre-Invasion AI Machine Speech to Human Troops

![Photo 17-4. Pre-Invasion Speech to Human-Machine Team](images/pg321_2.png)

**Photo 17-4**. Pre-Invasion Speech to Human-Machine Team

It is imperative that DoD clearly demonstrate that it will not lose control of killer robots and that AI-enabled unmanned systems make these platforms more precise and less likely to induce civilian casualties. If DoD fails to do this, then it is likely that more technology companies will be uncomfortable working for the department. That said, and the Project Maven drama notwithstanding, this is achievable. Here is how Microsoft president Brad Smith addressed his company’s position: “First, we believe in the strong defense of the United States, and we want the people who defend it to have access to the nation’s best technology, including from Microsoft. We are not going to withdraw from the future. In the most positive way possible, we are going to help shape it.”^([29](#25_Chapter17.xhtml#fn29))

Beyond clearing the way for the U.S. military to employ more-capable unmanned systems, this nuanced understanding is important for a more compelling reason: to open the way for big data, artificial intelligence, and machine learning to provide U.S. warfighters with the ability to make better decisions faster with fewer people and fewer mistakes. The executive branch and DoD must enhance the dialogue with the American public to help them understand how urgent it is to instantiate this enhanced decision-making capability.^([30](#25_Chapter17.xhtml#fn30))

## **ACCELERATING THE USE OF BIG DATA, AI, AND MACHINE LEARNING**

As anyone with a smart phone learns soon after turning the machine on, having access to sufficient data is rarely an issue. What is sometimes overwhelming is sorting through vast amounts of data and trying to tease out only what is essential at the moment. From a warfighting perspective, this means having systems that present a decision-maker with only that well-curated information that helps him or her make better decisions, often in the stress of combat.^([31](#25_Chapter17.xhtml#fn31))

The U.S. Navy—as well as other U.S. military services—has experienced a number of tragic incidents where decision-makers have made the wrong decision and have paid dearly in lives lost. From USS *Stark* taking two Iraq Exocet missiles in May 1987, to USS *Vincennes* shooting down Iran Air Flight 655 in July 1988, to two U.S. Air Force F-15 Strike Eagles shooting down two U.S. Army UH-60 Blackhawk helicopters over Iraq in April 1994, to USS *Greenville* surfacing under the Japanese fishing vessel *Ehime Maru* in February 2001, to others, bad decisions have caused needless deaths.

Indeed, while there were multiple reasons behind the Navy’s recent tragic accidents at sea, most notably the fatal collisions involving USS *Fitzgerald* and USS *John S. McCain*, it is clear that in every case, there was data available that—properly used—might have broken what safety experts call the “accident chain.”^([32](#25_Chapter17.xhtml#fn32)) What is striking in all these accidents across several decades is that in every case, tragedy ensued because the data wasn’t properly curated, analyzed, and displayed to the decision-maker in a timely enough fashion to make the right decision.

The Navy has been at the forefront of leveraging technology to help war-fighters make better decisions faster with fewer people and fewer mistakes in stressful situations. In the 1980s the Office of Naval Research initiated a program to study how warfighters could make better decisions in high-stress situations. The initiative, dubbed TADMUS (Tactical Decision Making Under Stress), used cognitive science to break new ground in understanding how decision-makers make decisions.^([33](#25_Chapter17.xhtml#fn33)) This led to several prototypes (Multi-Modal Watch Station, Knowledge Wall, and others) that were beta-tested and that achieved promising results in helping decision-makers achieve optimum decisions.^([34](#25_Chapter17.xhtml#fn34))

TADMUS—along with similar Navy programs—was good as far as it went. Now DoD and Department of the Navy need to take these efforts to a new level. It would appear that key leaders “get it.” The Honorable James Geurts, assistant secretary of the Navy for research, development, and acquisition, put it this way at a military-industry conference: “If a force can harness AI to allow decision-makers to make decisions faster than the adversary, it will win every time.”^([35](#25_Chapter17.xhtml#fn35))

Then–Chief of Naval Operations Adm. John Richardson gave this notion more specificity in an address at the Naval War College Current Strategy Forum.^([36](#25_Chapter17.xhtml#fn36)) He turned the clock back to the 1950s to Col. John Boyd, USAF, and his OODA loop. Admiral Richardson used the OODA loop as a way of discussing the kinds of new technologies the U.S. Navy is fielding.^([37](#25_Chapter17.xhtml#fn37)) He noted that the Navy has already invested heavily in the Observe and Act parts of Boyd’s taxonomy. He pointed out that until the advent of emerging technologies such as big data, artificial intelligence, and machine learning, “we couldn’t do much about the Orient and Decide aspects of the OODA loop, but that today we can.”^([38](#25_Chapter17.xhtml#fn38))

Indeed, in an address, Navy budget director Rear Adm. Dietrich Kuhlmann put the question of how the Navy can best use big data, artificial intelligence, and machine learning even more directly: “How do we leverage AI, not to produce autonomous platforms that kill people, but to give commanders the edge in combat?”^([39](#25_Chapter17.xhtml#fn39)) More recently, the U.S. Navy’s *A Design for Maintaining Maritime Superiority, Version 2.0* challenged commanders to accelerate the use of AI technologies to solve today’s challenges.^([40](#25_Chapter17.xhtml#fn40))

The essence of what the U.S. Navy—and by extension, the U.S. military—wants to do with big data, artificial intelligence, and machine learning is not to launch Terminator-like unmanned systems downrange against our adversaries with no human oversight, but to help operators make faster, better informed decisions.^([41](#25_Chapter17.xhtml#fn41)) This is what big data, artificial intelligence, and machine learning mean for the U.S. military. Now it is a first-order priority for America’s military to help the public understand that providing our warfighters with big data, artificial intelligence, and machine learning leads to better decisions and that this ultimately saves lives.

## **ANTICIPATING—AND CLEARING AWAY—IMPEDIMENTS**

This chapter has focused primarily on addressing the public’s concerns regarding employing military AI-enabled unmanned systems, especially those platforms carrying weapons. We also pointed out that employing big data, artificial intelligence, and machine learning to help commanders—as well as warfighters at every level—make decisions faster than the adversary has the potential to convey a war-winning advantage for U. S. forces.

That said, as the U.S. military moves forward to leverage big data, artificial intelligence, and machine learning, there are a number of issues that must be considered and addressed to ensure that these technologies reach their full potential.

## Education

As pointed out in chapter 14, the U. S. military must educate the current—and future—generation of officers and enlisted to understand these technologies and how they will ultimately impact virtually all weapons systems. In a constrained budget environment, it is unlikely that funding can be obtained for things that cannot be explained in layman’s terms. Senior military leaders will need to be able to convey the benefits of these technologies in a compelling way.

## Career Paths

Each of the services has developed a cadre of professionals with expertise in information, communications, cyber, and other things that are essentially invisible. For the U.S. Navy, these officers carry the Information Warfare designator. But as AI-enabled weapons systems permeate the U.S. military, it is unlikely that a separate designator is the answer to fully leveraging these systems. More work needs to be done to ensure that those who use these technologies develop their expertise in much the same way as they grow in their primary warfare designators.

## Procurement

For most military systems, those in uniform—as well as the public—can see and sometimes touch a piece of equipment. Army and Marine Corps tanks appear in military parades, Air Force aircraft perform at public airshows, and Navy ships participate in “Fleet Week” events nationwide. Furthermore, these visible platforms are built in key congressional districts (for example, Huntington Ingalls Shipbuilding in Virginia) and develop key advocacy. The technologies that support AI-enabled military systems don’t have this visibility—or advocacy.

## Acquisition

Closely related to the procurement issue is that of acquisition. The technologies needed for AI-enabled military systems are developing so rapidly that they may be obsolete if they are only procured via the traditional planning, programming, budgeting, and execution process. Other procurement authorities exist to help acquire these technologies more rapidly, but our experience suggests that these congressionally granted authorities are not yet used to their full extent and advantage.

## Stovepiping

Each U.S. military service understands that it needs big data, artificial intelligence, and machine learning, and funding is being applied at the service level. That said, it is unclear as to whether—and when—DoD will create an omnibus organization to coordinate these developments between and among the services in order to pool scarce resources and obtain more bang for the buck. The highly touted Joint Artificial Intelligence Center, the DoD Artificial Intelligence Center of Excellence, is a good start—but only a start.

## International Law

As addressed in earlier chapters, considerable momentum exists internationally to limit—or completely ban—the use of lethal unmanned systems. The U.S. military legal community has begun to address this issue in a thoughtful way, but more likely needs to be done, and U.S military lawyers must be proactive—rather than reactive—to help the international community understand that the United States has no intention of employing completely autonomous “killer drones.”

This is only a sampling of the issues that must be addressed in a thoughtful way to clear away the impediments to the U. S. military fully leveraging big data, artificial intelligence, and machine learning to give our warfighters an advantage in all phases of conflict.

Finally, as the U.S. military embraces these technologies and inserts them in their platforms, systems, sensors, and weapons, we must be mindful of the extent to which acceptance of “black boxes” has permeated our lives and has—perhaps—made us too accepting and trusting of the machine, often yielding authority to the device.

As the U.S. military fields AI-enabled unmanned systems, the human *must* be the dominant teammate. This isn’t to say that the unmanned system can’t do amazing things that are out of reach for a human. What it *does* mean is that the human operator must not be tempted to cede complete authority to the machine.

While this scenario might initially seem farfetched, concerns about this human-machine balance are already appearing in the informed literature. For example, two psychologists addressed the pernicious way that we allow technology to be too dominant in our daily lives: “To navigate by GPS is to ensure a series of meaningless pauses at the end of which you do precisely what you are told. There is something deeply dehumanizing about this. Indeed, in an important sense, this experience turns you into an automated device GPS can use to arrive at its destination.”^([42](#25_Chapter17.xhtml#fn42))

The U.S. military must fully leverage big data, artificial intelligence, and machine learning to prevail in future conflicts. Embracing these technologies does not mean blind acceptance, but rather developing a well-nuanced understanding of the balance between the human and the machine, with the human always in charge.

## **NOTES**

# 18

The Influence of Artificial Intelligence on Naval Strategy and Tactics

REAR ADM. NEVIN CARR, USN (RET.), AND SAM J. TANGREDI

From time to time the superstructure of tactics has to be altered or wholly torn down; but the old foundations of strategy so far remain, as though laid upon a rock.

—Alfred Thayer Mahan^([1](#26_Chapter18.xhtml#rfn18_1))

Artificial intelligence … I’m certainly questioning my original premise that the fundamental nature of war will not change. You’ve got to question that now. I just don’t have the answers yet.

—Secretary of Defense James Mattis^([2](#26_Chapter18.xhtml#rfn18_2))

**Capt. Alfred Thayer Mahan**, world-renowned strategist of seapower, never had to consider the impact of artificial intelligence (AI) on naval strategy or tactics. He did, however, witness periods of profound technological change. Warship propulsion transitioned from sail to a combination of sail and steam to exclusively steam. Fuel changed from coal to oil. Ship design transformed from iron-clad vessels with mixed gun batteries to the iron and steel all-big-gun dreadnought battleships. In America, John Holland eventually convinced the U.S. Navy to buy submarines, Herreshoff Manufacturing built the prototype destroyer, USS *Cushing*, and Simon Lake experimented with what today would be considered seabed warfare systems.

Although Mahan’s two most famous books focused on naval warfare in the age of sail, he was certainly aware of the changes in naval tactics resulting from the evolution of technology. After all, he trained as a midshipman in a three-masted, square-rigged frigate, commanded a single-screw, schooner-rigged steam sloop off the west coast of South America, and finally commanded the steam cruiser USS *Chicago*, one of the U.S. Navy’s most modern warships at the time. Long before he became president of the U. S. Naval War College and embarked on his writing of history, he served as head of the department of ordnance at the U.S. Naval Academy, teaching both theoretical and practical gunnery to midshipmen. In fact, the first lectures he prepared for the Naval War College were not on past history or grand strategy at all, but on steam battle fleet tactics and “comprehensive and systematic consideration of modern technical capabilities.”^([3](#26_Chapter18.xhtml#rfn18_3)) His assessment of the unchanging nature of national, naval, and military strategy, in comparison to the requirement for continual changes in tactics based on advances in technology, cannot be dismissed as merely the biased view of a history-centric strategic theorist.^([4](#26_Chapter18.xhtml#rfn18_4))

Through his long and very active combat career, Marine general and former secretary of defense James N. Mattis earned a reputation as an avid reader and thinker on strategy, tactics, and military history. His career spanned the period of digitization, including, as Bob Work calls it, the transition from the first to the second offset. Although skeptical by nature of what he perceived as trendy and redundant concepts—such as effects-based operations—he appeared committed as secretary of defense to developing the emerging technologies identified by the third offset strategy for military applications. Perceived as a combination of self-motivated scholar and successful warrior, he cannot be dismissed as a military technophile who ignored history, convinced that “everything is different now.”

How, then, can we reconcile Mahan’s and Mattis’ statements?

## **THE EFFECT ON TACTICS**

For some commentators, reconciling the two perspectives requires an esoteric debate on the differences between the “fundamental nature of war” and the “character of war.” Both terms come from the work of the great German philosopher of war, Carl von Clausewitz, a scholar and practitioner and author of the classic *On War*. This debate is particularly keen among defense intellectuals associated with the U.S. Marine Corps and U.S. Army (hence, the manner in which Secretary Mattis addresses the issue).^([5](#26_Chapter18.xhtml#rfn18_5)) Clausewitz himself was a bit vague as to the absolute differences; however, a simplistic explanation is that the nature of war addresses the motivation and purpose of war—the desire to bend an opponent to one’s will—versus the means of carrying out war, such as the composition and technology of the forces employed. From this perspective, the character of war has changed throughout history as military technology has advanced. One might assume, therefore, that military application of AI—particularly as it might be used to control unmanned autonomous systems—holds the potential to eventually change the character of war, in similar fashion to previous technologies. It is, as experienced by Mahan in his time, a profound technological change.

However, some proponents of military AI argue that adoption changes the nature of war as well.^([6](#26_Chapter18.xhtml#rfn18_6)) In this view, the inevitable shift to military decision-making, aided—or possibly controlled—by AI systems, will create a fundamental change in how humans relate to war (for better or worse). War has the potential to become less of a human endeavor in which passion rages and influences human decision-making, and more of a logical process in which technology fights technology and less human blood is shed, particularly if unmanned autonomous systems dominate the battlefield.^([7](#26_Chapter18.xhtml#rfn18_7)) One might, of course, argue that it holds the potential for more human bloodshed, perhaps in previously unexpected manners. (Since science fiction is currently popular among defense intellectuals as helping to ascertain the technology-driven future, one can point to a then-popular 1966 episode of the television show *Star Trek* to illustrate the latter argument.^([8](#26_Chapter18.xhtml#rfn18_8))) Without the hindsight of history, we have no certainty that AI-driven autonomous weapons will inspire the same aversion as nuclear weapons in creating a balance of terror that supports strategic deterrence, rather than being a purely technological leap such as the machine gun, which produced greater slaughter.

As naval strategists, respecting Clausewitz but revering Mahan, we prefer to side-step the entire debate and very simplistically associate the nature of war with strategy and the character of war with tactics. (We can already hear our land-centric counterparts screaming.) From our point of view, tactics will indeed inevitably change as more AI-driven autonomous systems are used at sea and on the battlefield. This has already been implied in chapters 2, 3, and 17. *Exactly how* they will change is unclear, since none of the competing powers have experience in the large-scale usage of autonomous weapons systems. Limited usage, we are used to—there were some unique applications of unmanned systems in World War II and ever since, albeit without the added impact of AI.

Yet from a naval perspective, we already have a historical example of how autonomous systems profoundly changed naval tactics: mine warfare. Once naval mines became practical, reliable weapons, no admiral could shout with impunity, “Damn the torpedoes \[mines\], full speed ahead.” Those who did, such as occurred with the Allied fleet during the World War I battles at Gallipoli, failed in their mission.^([9](#26_Chapter18.xhtml#rfn18_9)) Countermine warfare or mine countermeasures became a necessary requirement (often a precursor) for fleet operations, as will be the case in future naval warfare. Interestingly, modern mine countermeasure systems being used or under development today largely center on unmanned, often autonomous, systems, which is arguably a case of autonomy versus autonomy.

The *DoD Dictionary of Military and Assorted Terms* defines tactics as “the employment and ordered arrangement of forces in relation to each other.” Here is where speed of decision is a great need, which is why the most sophisticated Cold War–era naval weapons systems were built with autonomous modes. The potential for a saturation attack by cruise or ballistic missiles requires reaction times measured in seconds. The introduction to this book notes that such systems can be considered simple AI, with narrow AI understood as simple AI with learning capabilities. The transition from simple to narrow AI—as an aid to human decision-making and an autonomous control system when in extremis—would not seem difficult from a conceptual point of view.

Once deployed or fielded in numbers, AI-driven autonomous systems will logically have an effect on overall future tactics—although many of these systems will also be integrated into current tactics. For example, the unmanned prototype platform Sea Hunter has demonstrated the ability for autonomous surface ships to operate at long distance, and the Navy leadership has fully embraced the fact that unmanned platforms are essential in keeping up the strength of the overall fleet.^([10](#26_Chapter18.xhtml#rfn18_10)) It is a just matter of time before unmanned ships are armed with weapons similar to those on manned surface warships. There is a growing public discussion on whether autonomous vessels will perform as “arsenal” ships, a former Navy program objective. Whether these unmanned, partially manned, or optionally manned warships will operate independently, as part of a battle group, or slaved to individual manned warships will be a function of their designed capabilities. Without being great prognosticators, we can say that they likely will operate in all three fashions, as will AI-driven autonomous undersea and aviation systems.

One caution: contrary to some of the public hype, these tactical changes will be gradual. Legacy systems (a biased term if ever there was one), by which many mean manned systems, will not be made obsolete overnight, if ever. Those who think AI-driven systems “change everything” will be disappointed. They change *some* things, particularly operational tactics, as they become—through painstaking engineering, experimentation, and trial and error—reliable tools in the naval toolkit.

As per the Mahan quote, will current tactics be “torn down?” We think we can categorize those exact words as a rhetorical flourish. But if we interpret that quote as meaning tactics will change, our answer is yes; increasing autonomy enabled by AI will inescapably change them. Whether AI-driven autonomy will change the nature of war—meaning strategy—is a different question.

## **THE PROBLEMS OF STRATEGY**

In addressing the effects on strategy, two different questions emerge involving artificial intelligence. First, does the increasing use of autonomous systems, particularly those directed by AI, require the United States to adopt a new defense strategy because the nature of war has changed? Second, should AI be used as a decision-making aid—or even a fundamental means—for the creation and implementation of strategy?

The first is a relatively straightforward question—whether the integration of autonomy and AI into the military force structure (and in the force structure of potential opponents) changes the defense environment to the extent that the current (and past) strategy no longer fits.

The second question is not quite as straightforward because it bumps up against what actually constitutes the creation and implementation of strategy—rational (hopefully) human decision-making. This requires an examination of AI inclusion in two different aspects (or “problems,” as Clausewitz might term them) of strategy: strategy as a means of decision-making in a particular situation, or strategy as a planning process.^([11](#26_Chapter18.xhtml#rfn18_11)) In introducing AI as a tool for strategy-making, as well as its impact on tactics, it would appear the function of AI would differ in each new application.

For example, if one views strategy as the application of a preplanned policy to key decisions at critical moments (the particular situations), one might be tempted to utilize AI to make the actual decisions. After all, AI is driven by logic rather than emotion and can assess hundreds of thousands of options in seconds, whereas emotional humans might stumble through thinking of incomplete alternatives. Chess is often used as a metaphor for strategy, and it has already been demonstrated that AI can win at chess.^([12](#26_Chapter18.xhtml#rfn18_12)) If indeed, as other chapters suggest, the key advantage of AI is to increase the speed of decision-making, the fastest speed would be achieved without human interference. This can be done by an AI review of all possible moves and options conducted faster than any human team of analysts could accomplish. Former Chief of Naval Operations Adm. John Richardson frequently suggested that AI could be utilized to support *iterative* wargaming so as to generate a range of options for war planning and force design.

However, it is not a mere straw man to suggest that there are alluring dangers in reliance on AI, when combined with the application of a preplanned policy, to key decisions either over time or at critical moments. Rear Admiral J. C. Wylie defines strategy as the means to “power control”—in other words, decisions that can favorably control events.^([13](#26_Chapter18.xhtml#rfn18_13)) He views strategy as a direct result of matching means to ends or, as he describes it, “a purpose together with some measures for its accomplishments.”^([14](#26_Chapter18.xhtml#rfn18_14)) Admittedly, Wylie distinguishes between a linear sequential strategy and a cumulative strategy and suggests that a cumulative strategy provides “a useful hedge against a bold plan going wrong.”^([15](#26_Chapter18.xhtml#rfn18_15)) However, the idea that strategy can be boiled down into a comparison between ends (objective) and means (resources) could easily lure enthusiasts, budget cutters, or the incautious to consider AI as more efficient than humans in making the most efficient matches. Initial successes could result in an almost irresistible temptation to give AI increasing control over decision-making. In the fears of some AI critics, the ultimate result would be similar to the plot of the movie *WarGames*, in which preplanned actions controlled by an AI system cannot be shut down, overriding human control.

Proponents of the increasing use of AI would argue that the U.S. civilian and military leadership—led by public opinion—would *never* adopt such an integrated usage of AI in decision-making as to take humans out of the loop. Our opponents, however, might not possess the same self-restraint. As chapter 2 makes clear, current policy is to always keep humans in the loop when deadly force is being authorized. The vision is one of human-machine teaming, or “human-on-the-loop,” in which humans are *assisted* by the speed of data interpretation and information processing of AI. But there is always a bit of a slope. The question therefore becomes: at what level does this *assistance* end, leaving remaining decisions exclusively to humans? If AI is “better” at making maintenance decisions, programming decisions, logistics decisions, force generation decisions, and force disposition decisions, shouldn’t it be “better” at strategic decisions? The allure builds.

Returning to the illustrative use of science fiction, the great writer Arthur C. Clarke is well known as the author of *2001: A Space Odyssey*, whose subsequent movie version is often cited as a warning against strong/advanced AI. However, Clarke also wrote, back in 1951, a short story titled “Superiority” in which a more technologically advanced galactic alliance is defeated by another because it chose to discard old technology before fully testing operations with the new.^([16](#26_Chapter18.xhtml#rfn18_16)) The story could also be titled “Unintended Consequences,” since the logic of adopting, and thereby becoming increasingly dependent on, advanced (and continually advancing) technology to solve immediate problems becomes so compelling as to seem irrefutable. This may have eventually led Clarke to think about the problem of AI as seen in *2001*.

The other problem of relying on AI as a decision-making tool is well developed in chapter 16—the ever-present problem of deception. Deception and a continuing peacetime algorithm versus algorithm war will continually lurk in the background.

If one, however, views strategy *primarily* as an analytical process to generate objectives to pursue eventually—remaining divorced from actual decision-making, which itself is dependent on particular circumstances as much as the strategy itself—it seems more likely that AI assistance would be utilized in a more segregated fashion.

In its most bureaucratic form, strategy as process is illustrated by the public strategy-making conducted by the U.S. government. In the documentation of national security, first comes the White House–level *National Security Strategy* (NSS). Derived from that is the Defense Department–level *National Defense Strategy* (NDS), which in turn frames the Joint Staff–level *National Military Strategy* (NMS). At that point, strategy as process splits into two paths. The regional combatant commands develop their war or contingency plans inspired by the NMS, but more attuned to local circumstances (what is happening in the region) than process, and generally less resource-constrained in view than the NMS or NDS. At the same time, the individual services develop their respective strategies that attempt to tie the NSS, NDS, and NMS to the program development, training, and acquisition that defines their budget—which, hopefully, satisfy the requirements of the combatant commands. In the Navy’s case, this process is evidenced by the fact that the classified 2018 service strategy was initially titled “The Navy Response to the National Defense Strategy” (the NMS had not yet been developed).^([17](#26_Chapter18.xhtml#rfn18_17))

Strategy as process comes closer to Wylie’s concept of cumulative strategy than it does to linear sequential strategy because each of the plateaus in the process interjects a different perspective and a new set of interests, based on the organization and its strategy drafters. Although AI could be utilized to assist the drafters on each of the individual levels, it would be difficult—even with hundreds of millions of lines of code (any one of which could be wrong without proper oversight)—for AI to duplicate the cumulative results of the process. Let us, then, examine the applications and implications of AI to, and for, strategy in greater detail.

## **AI AS AN ELEMENT OF STRATEGIC DECISION-MAKING**

The separation of national security planning into three levels of activities—strategic, operational, and tactical—may be convenient in assigning responsibilities, but it results in an artificial separation that rarely occurs in modern decision-making. Based on its World War II experience, the U.S. Army long favored the three levels of planning, although it was not until the 1980s that the operational level became a commonplace term in defense literature. The logic of its use is that the strategic level belonged (especially in World War II) to the heads of government/commander in chief and the joint and combined military chiefs of service, the operational level to army or corps commanders, and the tactical level to division commanders and below. Previously, military operations were generally characterized as consisting of two levels: strategic and tactical. The U.S. Navy long resisted the switch to three levels but eventually yielded in deference to jointness.

In theory, the decision-making on each level is dependent on the decisions made at higher levels. This dependence could be duplicated by learning algorithms so that a decision from the uppermost level could be translated to a decision at the lowest tactical level, if enough data could be introduced into the AI system. For example, if the president were to decide that U.S. forces in theater needed to respond to an adversary’s chemical attack on civilians, AI that incorporated data from a common operational picture of U.S., opposed, and unengaged forces with knowledge of U.S. force capabilities, with conditions on the scene (via remote sensors), and through biometric pattern recognition, could presumably make tactical recommendations to individual pilots or on the squad level as to what to shoot (or not shoot).^([18](#26_Chapter18.xhtml#rfn18_18)) In accordance with the very fears of opponents of “killer robots,” the AI algorithms—theoretically—could be given the authority to give direct commands to autonomous systems.

As previously noted, to create such a reality would require the Department of Defense to overturn its own policy concerning retaining humans “in the loop” of any decision to apply violent force.^([19](#26_Chapter18.xhtml#rfn18_19)) Physically, it would require millions of lines of code and extensive machine learning. An error in sensor data could lead to a catastrophic recommendation and decision. However, in a world of ubiquitous cell phones and instantaneous audio and visual communications, twenty-four-hour news cycles, and pressure and desire to increase the speed of decision-making, it is conceivable that decision-makers would be tempted to rely on such an AI system—it would certainly cut out delays caused by otherwise necessary middle-level decisions. And, as proponents might argue, humans in the fog of war would likely make even more mistakes than AI. Proponents are also likely to point out that commercial businesses successfully rely on AI to augment their decision-making. However, these uses are concentrated in the areas of marketing and sales, not in life-threatening or corporate structure decisions.^([20](#26_Chapter18.xhtml#rfn18_20))

The overall point is that if strategy is viewed as synonymous with the decision-making process, the cascade of interrelated responsibilities *could* induce the application of a single AI system to the entire military action decision-making cycle. It would be a tremendously difficult engineering and data acquisition feat, but as a common expression goes: “If we can send men to the moon, we can \[insert aspiration here\].” Beyond a doubt, AI would have an influence on strategy under those circumstances.

## **AI AS AN ELEMENT IN THE CUMULATIVE STRATEGY PROCESS**

Aside from the bureaucratic process of developing documents such as the NDS, how does one separate strategy as process from strategy as decision-making? At first glance, it may seem that the separation is very narrow, since the common concept is that effective strategy *should* lead to decisions. However, as noted before, if strategy is viewed as a process that develops a path of activities that results in cumulative steps toward a policy goal, then it is much easier to divorce decision-making from strategy-building.

An example of such a divorce is President John F. Kennedy’s decision-making during the Cuban missile crisis of 1962.^([21](#26_Chapter18.xhtml#rfn18_21)) The U.S. grand strategy was containment of the Soviet Union, a strategy built on cumulative steps that involved military, diplomatic, economic, scientific, and informational aspects. The Soviet Union being allowed to maintain nuclear-armed ballistic missiles in Cuba would be perceived as a serious failure of that grand strategy. The United States had the tactical forces in place to remove the installed missiles and prevent further transshipment, and such action would be in the logic of the strategy.^([22](#26_Chapter18.xhtml#rfn18_22)) Yet President Kennedy chose to take a lesser action (quarantine) that arguably was a step outside of the logic of the strategy. This was done based on the fear of prompting a nuclear war—that is, a human emotion.^([23](#26_Chapter18.xhtml#rfn18_23)) It actually did nothing to force the removal of missiles already in place, although they ultimately were removed. One could also argue that a nuclear response by the Soviet Union to the forcible removal of the missiles would have been illogical since the Soviet homeland was not affected, and it would have more to lose than gain.^([24](#26_Chapter18.xhtml#rfn18_24)) The point, however, is that the decision itself stood outside of the strategy per se—the strategy could continue even though a (single) decision did not (at least initially) appear to contribute to its success.

Fast-forwarding the circumstances of the Cuban missile crisis to the era of AI participation in decision-making, one must ask if an AI system in a similar situation would be able to include a (human) emotional fear of nuclear escalation when the logic might appear to lead to the opposite conclusion. It might, however, be able to improve the human ability to consider a range of unthinkable strategic consequences in cold terms as quantifiable “pros and cons.” If AI were allowed to approach the problem from the “strategy as decision-making” point of view, the decision might not have “stood outside the strategy.” Thus, there appears to be cautionary value in applying AI to the process of strategy-building but not to the decision-making. We must also bear in mind that human accountability is an important element of every decision—especially those involving potential loss of life. While an argument can be made that human coders might bear responsibility for the actions of the machines they enable, the line of traceability becomes less distinct once machines are allowed to “learn” and evolve behaviors that may not have been intended. Perhaps in the twenty-first-century setting, this would constitute Wylie’s “useful hedge against a bold strategy gone wrong.”

How could AI be utilized effectively in strategy as process? An initial answer is that it could be used as an iterative analytical tool at each individual step of the strategy-building process. For example, at the service level it might be used to do cost comparisons for multiple weapons systems where a massive amount of data is required. Assessing changes in cost for an acquisition program due to parts substitution is a difficult process because of a wide variety of alternatives. If there is change in one part for the sake of economy, there may be a need to change multiple parts, which, in turn, generates many cost alternatives. To be able to explore all options, the program needs to run thousands of iterations. If the strategists as well as the acquisition personnel could have such calculations, service strategies could become the art of the possible, rather than aspirational declarations.

In the development of war plans, AI can be used as a tool for analyzing the pattern of results for wargames run thousands of times with changes in the input variables, as per Admiral Richardson’s view. These patterns may provide unanticipated clues to an opponent’s potential behavior. Use of AI-run and -analyzed wargames loses the educational and heuristic effects obtained from individual humans playing the games. However, they may prove a useful analytical tool—as long as the analysis can understand the logic applied and the manner in which the AI machine does its calculations. To do so would require explainable AI with supervised learning. “Supervised” does not necessarily mean that there is a human “on watch” over the system (it might), but rather that the system has been trained on verified data and can compare its outputs to similar outputs that are known to be correct. As the introduction notes, that costs more money.

It is important also to note that both examples utilize AI as a planning tool for discrete parts of the overall strategy-building or strategy-implementing process, not as a method of decision-making by the same algorithms through the total process. This approach would ensure that humans do indeed remain in the strategy loop. The drawback is that it reduces the speed at which a strategy can be built. Ultimately, however, the highest possible speed is not necessarily needed for a thoughtful process.

## **ASSESSMENT: IF AI FULLY DIRECTS A STRATEGIC COURSE OF ACTION**

For compleat strategists, it is not enough to simply identify problems; it is imperative to offer at least some partial assessments, even when information is incomplete.

In his book *Cyberspace in Peace and War*, Martin C. Libicki expresses his surprise and consternation over how decision-makers ignored the societal vulnerabilities inherent in connecting physical infrastructure to the Internet. At the beginning of the Internet era (c. 1991), Libicki explains: “Then as now, it was hard to conclude the cyberwar was going to trump every other form of warfare. I was confident that the threat from cyberspace could be contained, in part because I believed that people, aware of the threat, would not willy-nilly connect critical systems (such as those that supply electric power) to the Internet. In this, I was wrong.”^([25](#26_Chapter18.xhtml#rfn18_25))

Having examined the benefits, costs, and risks of relying on or allowing AI to direct the *complete* course of strategy for the nation in its global affairs or the *entirety* of a military campaign, we conclude that such would occur only if our decision-makers are “willy-nilly,” or—quite frankly—stupid.

There are just too many vulnerabilities in AI itself, and the loss of human control results in a situation in which logic can drive war to extremes beyond which humans would carry it. Most wars do not end based on a logical decision that one of the combatants makes concerning the probability of eventual defeat.^([26](#26_Chapter18.xhtml#rfn18_26)) Instead, the losing side gives in because its people and decision-makers are emotionally exhausted and no longer have the will to continue fighting. The losses in lives or treasure exceed (sometimes far exceed) any gain then possible. This decision is rarely made because of logic, but because of emotion. The people have a sense (or are thoroughly convinced) that they have already been defeated. This is one of a number of reasons that the United States appears to have failed to achieve its ultimate objectives in Iraq or Afghanistan: the opponents (or people involved) have never perceived themselves as being “defeated” despite suffering crushing losses in fighters, territory, or power. Could AI as a decision-making aid have helped us be successful in Afghanistan? As discussed in chapter 6, AI can provide tools in the tool kit on the tactical level. Even there, trust will always be questioned. Beyond the tactical level, however, it is hard to assert that AI could substantially adjust a strategic perspective based largely on hubris. At the end of the day, it’s all about what people think.

How, then, would a campaign conducted exclusively by AI conclude? No one—and we mean no one—has even begun to understand how to program an understanding of emotion into AI. And if AI cannot grasp human emotion, how does it decide when war ends? Some scientists argue that human emotion can be mimicked in AI and that the development of sentient AI “beings” is but a generation away. With experience in both strategy and the development of military technology, we say: no way—in multiple generations perhaps, or perhaps not.

## **ASSESSMENT: IF AI DIRECTS DISCRETE ELEMENTS IN A STRATEGIC PLANNING PROCESS**

However, AI *can* be very efficiently utilized as a decision-making aid that can categorize strategic options in a strategy-building process. This may be an obvious conclusion, but it is still worth the contrast of using AI to direct a course of action.

With regard to the many mathematical calculations required for the detailed campaign analysis that leads to force composition and strategy alternatives, an AI tool—like the current computational models under use—would prove useful. Yet the algorithms useful for quantitative evaluations are not necessarily useful for qualitative ones. For example, even if AI systems could be programmed to consider the history, culture, and religious beliefs that influence the strategy of a potential opponent, the programming costs would likely surpass those of the training of a human area specialist.

It is difficult to assign quantitative values to primarily qualitative assessments. AI, like all computer-based systems, requires large amounts of quantitative data to compare. Such data are available in particular elements or aspects of the strategic planning process, but the picture is far from complete. Quantifying qualitative assessments simply means the evaluation process is shifted from an area specialist or subject matter expert to a data scientist or programmer—or, somewhat better, a different subject matter expert who happened to be hired by the AI software developer. Yet in any event, it will be a *human* judgment on which the options are based, not on machine manipulation of “big data.”

Our assessment is that AI can provide substantial assistance in discrete elements of the strategic planning process but not in all elements. There is no simple series of algorithms that can manage the entire planning process, and the complexity involved would inevitably require qualitative human judgments. A specific algorithm cannot fit all, at least in the near term.

## **TRUST AND WHERE TO PLACE IT**

Several times, we have asked: whatever the manner of adoption, how can we trust the results? In short, we can’t. As noted in chapter 16, there are so many paths to error in the face of deception and normal accidents. But such is, and always has been, a characteristic of war. Expecting AI to change that is a teenager’s rant against an elder’s oppressive wisdom.

This points to the need for rigorous experimentation, testing, and evaluation practices along with comparisons to previous (non-AI) outcomes, with the continual recognition that a logical but incorrect answer is always possible. The mantra of operations analysis that “all models are wrong, but some are useful,” applies here. Trusting AI-generated answers to discrete elements of a decision-making or planning process appears much safer than trusting the “final answer” of a complex, interconnected process (even if it was cost-effective to create one). A practical problem in trying to adopt commercial AI applications to military processes is that many of the cutting-edge AI firms tend toward unsupervised learning of AI, which does not fit a rigorous evaluation process requiring transparency and traceability, as mentioned earlier. This is another reason our assessment recommends the use of AI to assist in evaluating discrete elements of strategy rather than determining a course of action.

On the tactical level, AI can help lift the fog of war as to the overall environmental factors. It can also increase the speed of reaction to an enemy’s action. We use simple AI already. Adding learning AI systems seems to be a natural evolution. Tactics inevitably will be adjusted to support this.

However, nothing can lift the fog of war as to the enemy’s intent at a specific moment of time. This may be a statement with which others will certainly disagree. Indeed, some of the research sponsored by the joint staff’s strategic multilayer assessment team suggests that AI can detect a great deal in an opponent’s decision. About that, we remain skeptical. In contrast, we believe that, as an important tool in a large kit, AI is suitable for reducing the fog but cannot effectively dispel it entirely, as much as proponents might wish. The issue of trust, combined with the prodigious complexity required to build truly predictive AI, is a tremendous, perhaps insurmountable, hurdle. There are also good reasons not to surmount it, although we cannot ignore the actions of adversaries who may not show the same restraint.

## **CONCLUSION**

Returning to the question of reconciling the two quotes at the beginning of the chapter—we do not see them as irreconcilable. Mahan is right: tactics will change as AI-driven autonomous systems become increasingly common. Tactics necessarily evolve as technology changes. However, strategy, which is more dependent on the assessments of the future security environment, human nature, and human reaction to technology than on technological development per se, evolves slowly. Even when rapid change occurs—such as when the (first) Cold War ended—we see previous concepts bounce back when great power competition returns.

Former Secretary Mattis posed the question about whether AI changes the nature of war. If one defines nature of war as representing strategy, our answer is “no,” or at least, “it shouldn’t.”

What, then, is the future of AI for the Navy and Marine Corps? We see its principal near-term impact as being on the tactical level; its use in autonomous systems such as Sea Hunter, the Orca extra-large unmanned undersea vehicle, and unmanned air combat vehicles will change how navies fight in a particular operational context.^([27](#26_Chapter18.xhtml#rfn18_27)) It will also be a useful planning tool for determining fleet composition. However, the influence of AI on strategy seems, at least in the foreseeable future, rather muted. AI will certainly help us determine how we fight, but not necessarily why we fight.

### **NOTES**

# 19

The Future of AI

PATRICK K. SULLIVAN AND THE OCEANIT TEAM

**Even when equipped with big data**, the current generation of artificial intelligence (AI) and machine learning (ML) systems are powerful but fragile. Once properly trained and vetted, AI/ML systems have demonstrated performance that meets or exceeds human capabilities in numerous tasks. As noted in previous chapters, the most widely known applications of AI/ML are high-profile incidents such as AlphaGo’s victory over Go world champion Lee Sedol—a “Sputnik moment” for AI/ML development in China. However, AI/ML have also proven their worth at more mundane tasks such as optimizing supply chains or industrial operations down to things as small as spam filtering or filling cells in an Excel spreadsheet in a “smart” fashion.

The most common types of AI systems today are those based on ML. As discussed in previous chapters, ML systems can perform many valuable tasks such as enabling vehicles to operate autonomously, identifying/classifying unknown objects based on sensor readings, and predicting the future state of complex systems. In the near future, AI/ML will still perform these roles, but will do so with increased capability and less “babysitting” than the current generation of approaches. In order to achieve this goal, researchers are enhancing the current set of AI/ML methods to compensate for some well-known limitations. The advantage of these near-term systems is that they can be used to help solve many of the problems currently outstanding in the Navy and Marine Corps. Examples include support for the missions of fleet sustainment, cybersecurity, and intelligence, surveillance, and reconnaissance (ISR). The longer-term future of AI and ML is a shift away from many disparate systems to a single AI system (or a smaller number of systems) with enhanced capabilities. The goal for some AI researchers is artificial general intelligence (AGI), which would be an AI system with human-level intelligence. (The “anthronoetic artificial intelligence” discussed in chapter 1 would be an AGI, but in addition to being human-level, its intelligence would be human-*style*, a critical factor.) Such a system could act as a virtual assistant and would be capable of performing many tasks simultaneously.

## **ROBUST MACHINE LEARNING AND ARTIFICIAL INTELLIGENCE**

The ML systems of the near-term future will bear a strong resemblance to the systems of today. Due to increases in the availability of data, computing power, and algorithms capable of leveraging both, these systems will certainly be able to make use of bigger data than is currently available today. While this enhanced access will boost performance, these near-future systems will also feature modified algorithms targeted toward addressing some of the limitations identified in the current generation of systems. These targets include:

•  the challenge of adapting AI systems to changing environments

•  learning models from data with less structure

•  identifying causal models that enable what-if questions to be asked

•  making AI systems understandable to human overseers

•  defending against adversarial attacks and deception.

In the remainder of this chapter, we will describe what the issues associated with each of these limitations are, why solving them is of interest to the Navy, and what steps are currently being taken to find solutions.

## **THE PROBLEM OF STATIC DATA**

Most present-day AI systems implicitly assume the environment they are operating in is *static*. The benefit of this assumption is that they can leverage data sets, no matter when or where they were collected, during the training process. Furthermore, many systems are trained once and then deployed, so the system lacks the capability to update itself. However, even for systems that can incorporate new data sets, this static assumption can ultimately degrade performance as the AI system “focuses” on correlations or patterns that are no longer relevant.

![Figure 19-1. Quantity versus Accuracy of Training Data. The retention of outdated data ultimately reduces performance.](images/pg353_1.png)

**Figure 19-1**. Quantity versus Accuracy of Training Data. The retention of outdated data ultimately reduces performance.

As a prototypical example of the *concept drift* that occurs in dynamic environments, [figure 19-1](#27_Chapter19.xhtml#fig11) shows a plot of the accuracy of a classifier trained on a hip replacement data set.^([1](#27_Chapter19.xhtml#rfn19_1)) In lieu of a single fixed data set, this classifier was trained incrementally on batches of fifty samples sequentially in time. Initially, the amount of data available limits the performance of the classifier, so increasing the number of samples from 50 to 150 boosts accuracy to nearly 90 percent. However, the relationship between the features and labels in these data change over time, but because the classifier is trained on *all previous data sets*, it is unable to compensate for this change. As a result, the accuracy of the classifier falls to just over 10 percent as the correlations/relations that were once important no longer perform well. In other words, the retention of outdated data ultimately reduces performance.

The issue of dynamic environments and concept drift is not limited to hip replacements or medical data; indeed, it is a ubiquitous phenomenon. A real-world example occurs in predictions of the on-time performance of airlines, which relates to the problem of applying AI to logistics. This task depends on other information not contained within the data set, such as the status of an individual airplane and changes in air-traffic control policies over time and due to events such as 9/11. Another example is in intrusion detection systems that distinguish intrusions or cyberattacks from “normal” connections by identifying the signatures that differentiate them. Intrusion detection systems must be able to adjust as new cyberattacks are created or existing attacks modified to avoid detection. Previous data is not sufficient.

The AI systems of the near future will be more robust and responsive to changing environments. In recent years, there has been a push to develop AI systems that operate on data streams rather than data sets. These algorithms enable a system to continually sample its environment and update its understanding of the world as time progresses. However, as illustrated in [figure 19-1](#27_Chapter19.xhtml#fig11), more data is not always better, and retaining out-of-date information can negatively impact performance. Researchers are developing AI/ML systems that are able to detect concept drift (slow changes in the environment) and concept shift (rapid changes in environment) and adapt to them either by forgetting irrelevant data, focusing on the most useful subset, or adapting the model to compensate for the change.^([2](#27_Chapter19.xhtml#rfn19_2))

In many commercial and defense applications, the operating environment is not static and will change due to factors outside of our control. Many AI/ML systems are trained and then deployed and must assume a static environment as a result. Streaming systems, which can continually update themselves, enable the system to respond to environmental changes but are often not agile enough to keep pace with this change. However, ongoing work in concept drift/shift adaption appears poised to enable AI/ML systems to more selectively use the data in such streams to keep pace with ever-changing environments.

## **LEARNING FROM LESS STRUCTURED DATA**

Once trained, the current generation of AI/ML systems can be powerful and quick. While the result and the algorithm used to obtain it might get the most publicity, the majority of the effort in constructing such a system is in gathering and cleaning the data required by the model. This process is laborious and time-consuming, as a human must examine the types of data available and determine how to “massage” the data so it can be used as an input to an AI/ML system. Chapter 15 discusses the difficulties of this effort.

This data cleansing process is needed because, despite their power, the current generation of AI/ML systems are only capable of ingesting data in a fixed format, and it is up to the user or designer to ensure any data are translated to that format. For example, state-of-the-art object recognition systems such as YOLO-net do not directly recognize image files like JPEG or PNG.^([3](#27_Chapter19.xhtml#rfn19_3)) Instead, the user must translate that image to a *tensor* (i.e., a cube of numbers) with the same statistics used for training. Inputs of the wrong shape, dimension, or normalization will cause the system to either crash or produce nonsensical outputs.

In addition to increasing the cost required to “stand up” an AI system, difficulties in determining the mapping from “raw” to “cleansed” data can prevent AI systems from being deployed simply due to a lack of data. This is particularly prevalent in applications where the primary data source is human-generated log files. They include both condition-based maintenance, where logs recorded by technicians are a valuable source of information, and ISR applications, where human-generated reports augment other forms of intelligence gathering. In principle, nothing prevents such data sources from being used; however, the complexity of ingesting them is a problem very difficult to solve in practice.

To overcome this limitation, the AI systems of the near future will increasingly incorporate natural language processing as a means of making use of text data. This is an extremely active research area, and state-of-the-art approaches such as Word2Vec address the problem of natural language processing by learning to associate words (and relationships between words) to the numerical vectors or tensors expected by deep neural networks and other ML approaches.^([4](#27_Chapter19.xhtml#rfn19_4)) These approaches often struggle to capture the larger context such as a sentence or document. For example, the word “bleed” means two very different things in the context of medicine (where it almost certainly refers to blood) and engine maintenance (where it refers to a gas system).

Researchers are currently trying to address these issues using approaches such as Doc2Vec (which is an extension of Word2Vec with a better grasp of the context of a word) or with new network structures able to ingest graphs and other more general types of input. Whether by modifying existing approaches or developing wholly new network structures, the short-term future of AI is to move away from the very mathematical but rigid structure of vectors/matrices/tensors to more flexible inputs such as natural language text.^([5](#27_Chapter19.xhtml#rfn19_5))

## **DECISION SUPPORT AND CAUSAL MODELING**

A common application of AI/ML systems is as a decision support tool—a system that will recommend to a human the best course of action to take in any situation. If successful, these systems will be particularly impactful in applications such as condition-based maintenance, where AI can determine when and where inspections should be performed to ISR systems and allow AI systems to direct resources to the subsystems most efficiently in gathering data. AI systems have also been proposed for applications such as target prioritization and threat assessment.

While these applications vary greatly, the common theme uniting them is a need for AI to fuse data from multiple sources and make decisions based on what it thinks will happen in the future. However, reasoning about the future state of a system can be a challenge for many current AI/ML systems. Most of the current generation of AI operates by ingesting a set of data and identifying patterns and/or relationships that exist between the variables. Due to the great computation power these systems possess, many state-of-the-art AI systems can find relations that would escape human observers. Yet that strength can also be a weakness. AI systems can find spurious correlations in the data that human observers would reject as being nonsensical. [Figure 19-2](#27_Chapter19.xhtml#fig8) shows an example of such a spurious correlation. Given this data, most AI decision support systems could conclude that the sale of domestic cars could be boosted by marrying more people in Wyoming.

Current AI systems identify associative models that can fall prey to spurious correlations in data. To overcome this limitation, researchers are developing AI systems that identify causal relations in the data. There are many approaches to causal modeling that vary based on the type of data supplied to the model and our current level of knowledge of the system of interest. A common thread between these methods is an underlying structure that defaults to previously known causal relationships that limit the structure of the model to causally plausible structures. The rigidity of these models also makes it difficult to optimize them for previously unencountered problems. Currently, much ongoing work is in the development of methods to identify useful causal models in an operationally feasible amount of time—in other words, models that can assess unexpected changes in data.

![Figure 19-2. Marriage Rate in Wyoming versus Car Sales. Many AI systems are fooled by spurious correlations in data. In this example, the marriage rate in Wyoming should be a good predictor of the number of domestic cars sold in the United States.](images/pg356_1.png)

**Figure 19-2**. Marriage Rate in Wyoming versus Car Sales. Many AI systems are fooled by spurious correlations in data. In this example, the marriage rate in Wyoming should be a good predictor of the number of domestic cars sold in the United States.

## **EXPLAINING AI CALCULATION PROCESSES**

While current AI systems have demonstrated superhuman performance in many different domains ranging from game-playing to designing supply chains, there have been challenges to their integration into human-based teams. These difficulties arise for many reasons, most prominent of which are the “black box” nature of many AI systems and the very structured format that AI systems require for data inputs. The former prevents humans from acting as true “overseers” of AI, as they are unable to understand why certain decisions are made. The latter restricts the types of human/machine interactions to a limited set of predetermined actions.

A dominant AI technique in recent years is the use of deep neural networks (also referred to as deep learning), which combine many relatively simple functions to represent complex relations. Deep neural networks have been used in numerous applications from cybersecurity to object detection and tracking to decision support systems. Yet one of the limitations of deep learning is the complexity of the models produced. Often, when an artificial neural network is used to fit a simple set of data to create a more easily mathematically analyzed curve, the equation required is far too long and complex for a human to understand or validate. As a result, the system remains a “black box” even though every individual weight in the network is known.

The inability of current generation AI systems to explain their actions acts as a barrier to entry in many mission-critical settings where human operators must learn to trust available AI systems. For example, current AI systems can prioritize certain targets or threats and even provide a measure of its confidence in their ordering. However, the decision to fire upon these targets falls to a human, who will likely be provided with what the AI thinks is important, but not why it thinks so. This problem is identified in chapters 6 and 12.

Currently, a tradeoff exists between methods that are easy for humans to understand but have had relatively limited performance and opaque systems that are difficult to understand but have had the highest level of performance. The more easily understandable systems utilize rule-based systems that describe decisions in terms of if-then rules (as described in the introduction). On the other hand, deep neural networks represent the difficult-to-understand AI techniques. Much near-term research in the scientific AI community and agencies such as the Defense Advanced Research Projects Agency focuses on designing new systems that avoid this tradeoff. Researchers are taking various routes to achieving this goal. They include both designing methods of extracting effective sets of rules from opaque methods such as deep neural networks, and taking approaches that enhance the power of rule-based or decision-tree–based systems. New approaches to AI might also avoid this tradeoff.

## **RESISTING ADVERSARIAL ATTACKS AND DECEPTION**

As AI and ML have become a critical part of many commercial and defense systems, adversarial approaches designed to defeat these systems have also been developed. The concept behind an adversarial attack is illustrated in [figure 19-3](#27_Chapter19.xhtml#fig9) for a two-dimensional classification problem.^([6](#27_Chapter19.xhtml#rfn19_6)) In this example, an ML system is trained to distinguish red points from blue points. To accomplish this, the AI/ML system learns a decision boundary, which is a curve that distinguishes the two classes. However, due to a finite amount of available data, there are inaccuracies in the AI/ML model causing data points to be misclassified. Adversarial attacks modify the features of a data point so it crosses a decision boundary and is therefore misclassified. As noted in chapter 16, defects in such a model can also be significantly enhanced by deception.

Many of the deep networks used for object recognition have proven to be susceptible to such attacks—for example, an adversarial attack on an image recognition system where a small amount of noise that is imperceptible to humans causes the classifier to misclassify a dog as an ostrich.^([7](#27_Chapter19.xhtml#rfn19_7)) Since many autonomous vehicles use vision systems for navigation or targeting, this class of attack could compromise either the safety or the efficacy of the vehicle. Indeed, researchers demonstrated that by carefully placing a few stickers on the road, they could cause the visual system of a Tesla Model S to navigate the car into the oncoming traffic lane.^([8](#27_Chapter19.xhtml#rfn19_8))

Adversarial attacks are a concern for more than just vision systems. Researchers have also used adversarial ML to modify malware in order to evade malware detection systems, which defeats any protection these systems may provide.^([9](#27_Chapter19.xhtml#rfn19_9))

To counteract this threat, researchers are developing new methods for training AI/ML systems. Approaches being considered include “front ends” capable of detecting when adversarial noise has been applied, modifications of the structure of existing networks to make attacks more expensive to design, and methods designed to make deep neural networks more “human-like” and therefore insensitive to many of the adversarial attacks on vision systems. Since the AI/ML systems of the future will be operating in a much more hostile environment, there will always be a race between designing networks that are more resistant and designing more effective attack strategies. While resilience is a “nice-to-have” feature in current AI/ML systems, it will be a crucial part of the systems of the future.

![Figure 19-3. Example of an Adversarial Attack in Two Dimensions](images/pg359_1.png)

**Figure 19-3**. Example of an Adversarial Attack in Two Dimensions

In the near future, AI/ML systems will look much like they do today since the bulk of research efforts are focused on addressing shortcomings that prevent current approaches from being more widely used. These current efforts are directed at a broad array of issues including pushing the limits of massively parallelizable algorithms intended to ingest petabytes of data and use petaflops of computing power to keep up with the increasing flow of data being made available. Simultaneously, researchers are also focusing on the problem of edge computing, which involves taking the current set of computationally intensive algorithms and “slimming them down” so they can be run on devices of small size and weight and low power. In essence, this would move computation from the cloud back to the user. Ultimately, the goal of these short-term efforts is to develop AI systems that are more robust and easier to work with.

## **THE FUNDAMENTAL PROBLEM OF MACHINE LEARNING**

The majority of ML systems today are based on a problematic *empiricist* theory of learning—experience (data) rewires the system (mind or machine) to implement a new lookup table. One problem with this form of learning is its nonproductivity; the system only recognizes variations on patterns from its training set. Empiricism as realized in deep learning neural nets is surely the most popular and successful ML technique, but its most basic functional weakness (nonproductivity) derives from its most basic mathematical weaknesses: the weight of a connection in a neural net is *unintelligible*, the function that maps from experiential data to the weight of connection is a many-to-one function, and for any one output value of the function state, there is an infinite number of combinations of input values that could have produced the state. For this reason, many ML systems are *unexplainable* black boxes.

In ML, big data are input and conclusions and recommendations are output, but the *process* whereby the former is used to derive the latter is completely opaque to the human analyst. To base a decision on such opacity is dangerously dubious. A (hypothetical) human-style AI would be transparent because it would be *constructive*. It would construct theories for which data are evidence. This differs from traditional ML techniques, which simply induce (or claim to induce) patterns and produce approximations of the unanalyzed data. Some ML systems have proved relatively successful in recognizing patterns in these data, but any such program is inherently and fatally limited by its architecture: the program cannot modify any of the components of the architecture, the program cannot modify itself, and the program cannot learn a function outside of its training space.

There is also a deeper problem with deep learning, expressed in press articles with such titles as “Is Artificial Intelligence Permanently Inscrutable?” and “Machine Learning Works Spectacularly Well, But Mathematicians Aren’t Quite Sure Why.” In a 2016 article in the journal *Nature*, Davide Castelvecchi explains,

Instead of storing what they have learned in a neat block of digital memory, \[neural nets\] diffuse the information in a way that is exceedingly difficult to decipher.… Just as in the brain, memory is encoded in the strength of multiple connections.… Where is the first digit of your phone number stored in your brain? Probably in a bunch of synapses, \[but\] there is no well-defined sequence of bits that encodes the number.… Even though we make these networks, we are no closer to understanding them than we are a human brain.^([10](#27_Chapter19.xhtml#rfn19_10))

Thus, for instance, we receive no explanations for why we frequently receive absurd recommendations from neural net–based recommender systems (e.g., “Based on your purchase of *The Brothers Karamazov*, you may enjoy *The Very Hungry Caterpillar*”).

In order for AI to be explainable, researchers must return to Alan Turing’s work, which maintains that any formalization of an effective calculation must be explicitly formulable (i.e., *generative*). Explicitness is required for ontological and epistemological completeness; if everything is given (by/in nature), everything is known (by the computer, natural or artificial), and nothing is undetermined or assumed, there should be no black boxes. Black box ML/AIs can generate absurd—even dangerously absurd—recommendations. An interesting corollary of explicitness is communicability and explainability; if the function is explicitly stated, this implies that it can be communicated.

## **THE GOAL OF ARTIFICIAL GENERAL INTELLIGENCE**

Progress in AI/ML is being made daily. In the near future, AI/ML systems will be easier to work with and more resilient to either changing environments or deliberate adversarial attacks. However, such systems are still considered weak AI systems (as termed in the introduction) because they are designed for, and only capable of solving, a particular problem. For example, an ML system designed to detect objects is not capable of then optimizing logistics or detecting spam.

Concentrating on weak AI is a very practical approach as it enables the AI and ML communities to produce useful results without having to design systems with all the complexity of the human mind. However, this is also limiting, since such systems need to be trained “from scratch” every time a new problem is encountered. This contrasts with humans who can draw upon their past experiences to adapt to new situations. In effect, the same “human system” can be used to solve many different problems, each of which benefits from this shared experience.

As a result, the ultimate goal of AI research, dismissed as quixotic by the majority in the ML community, is to produce systems with human-level intelligence, also referred to as artificial general intelligence, strong AI, or anthronoetic AI (as described in chapter 1). Once realized, such a system would be capable of solving any task that a human could, with the advantage of the more powerful computational hardware available to computers. Such a generalpurpose system could act as “virtual staff” or a virtual assistant in commercial and defense settings and provide advice or decision support information on a wide array of subjects (rather than—for example—having one system for threat assessment and another system for logistics). Due to the incredible benefits of realizing such a system, AGI is an area of active research effort, even though many AI researchers still believe this is a long-term task that will likely require two decades or more to achieve.

While the approaches of today, such as deep neural networks, may be the forebearers of such a strong AI system, many researchers believe that these approaches alone will not be sufficient to realize human-level intelligence/AGI. Indeed, a poll taken of AI researchers has placed a greater emphasis on biomimetic approaches that are either inspired by cognitive science, based upon cognitive architectures, or taken from computational neuroscience.^([11](#27_Chapter19.xhtml#rfn19_11)) Some researchers even believe that whole brain emulation will be required in order to achieve human-like performance. As a result, while AI/ML researchers can and will push the limits associated with big data and deep neural networks, the structure of AI systems in the long-term future may look very different from the structure of today’s systems. Yet ironically, they may actually look more like the systems of the past.

One aspect of human cognition that these frameworks seek to address is the ability to understand data in a hierarchical fashion. As previously stated, many ML systems are complex maps from input features to output predictions without many (understandable) intermediate structures. Many of the cognitive systems under development decompose inputs in a much more explicit way. This emphasis on the combination of symbols (primitives, parts, or other such terminology) harkens back to symbolic AI systems of the 1950s and, coupled with modern advances in computing technology, may provide an alternative path forward toward the goal of AGI.

## **ANTHRONOETIC ARTIFICIAL INTELLIGENCE**

Another related approach to cognitive-based AI is anthronoetic AI. Unlike neural networks, which are loosely inspired by the biological structure of the human brain, anthronoetic AI is inspired by the manner in which humans think and process information. One of the core axioms of this approach is that human cognition is based in language and any thought must be expressible in words. Due to that assumption, the core building blocks of anthronoetic AI are grammars—both the phrase structure grammars taught in school and the more abstract minimalist grammars of Noam Chomsky.

Grammars are most commonly associated with parsing sentences and understanding natural language. However, it is important to note that the mathematics behind linguistics and grammar are system-independent. [Figure 19-4](#27_Chapter19.xhtml#fig10) shows three different systems: language, mathematical expressions, and RNA molecules that can be represented using grammars.

While the language associated with each problem differs, anthronoetic AI systems could potentially apply a common set of techniques to many different fields simply by changing the language in which it is operating. Furthermore, if linguists such as Chomsky are correct, then there could exist a universal grammar that all humans innately possess that is independent of language, background, or even sensory input. An anthronoetic system equipped with such a grammar could in theory be applied to and solve any problem independently without modification. The conjecture that the human mind could, in principle, solve any solvable problem is controversial but logically sound.

![Figure 19-4. Three Different Types of Inputs: natural language, mathematical expressions, and RNA molecules. Although the applications may be very different, linguistic ideas apply equally well to all.](images/pg363_1.png)

**Figure 19-4**. Three Different Types of Inputs: natural language, mathematical expressions, and RNA molecules. Although the applications may be very different, linguistic ideas apply equally well to all.

An AI system capable of solving any solvable problem would revolutionize the world. As observed by the late Stephen Hawking (Cambridge physicist), Max Tegmark (MIT physicist), Stuart Russell (Berkeley computer scientist), and Frank Wilczek (MIT physicist, Nobel laureate): “\[AI\] research is now progressing rapidly.… The potential benefits are huge; everything that civilisation has to offer is a product of human intelligence; we cannot predict what we might achieve when this intelligence is magnified by the tools that AI may provide, but the eradication of war, disease, and poverty would be high on anyone’s list. Success in creating AI would be the biggest event in human history.”^([12](#27_Chapter19.xhtml#rfn19_12))

Indeed, the profundity of an anthronoetic AI cannot be exaggerated; such a system would by definition be effectively superhumanly intelligent given that its human-level/human-style intelligence would run on superhuman hardware.^([13](#27_Chapter19.xhtml#rfn19_13)) Moreover, as was understood at the dawn of AI research by the mathematician I. J. Good, such an intelligence has the potential for recursive self-improvement and thus could

far surpass all the intellectual activities of any man however clever, growing exponentially in a so-called intelligence explosion.… Since the design of machines is one of these intellectual activities, an ultraintelligent machine could design even better machines; there would then unquestionably be an “intelligence explosion,” and the intelligence of man would be left far behind.… Thus the first ultraintelligent machine is the *last* invention man need ever make, *provided that the machine is docile enough to tell us how to keep it under control*.^([14](#27_Chapter19.xhtml#rfn19_14))

## **ADDING CONTROL AND MORALITY TO AI**

Good’s statement paints the Janus face of artificial intelligence. In one direction is utopia, unbounded creativity, and problem-solving, “the eradication of war, disease, and poverty.” In the opposite is dystopia, the actualization of science fiction doomsday scenarios—and the descriptor “sci-fi” is anything but flippant; as Good counseled, “It is sometimes worthwhile to take science fiction seriously” for, as Hawking noted, “Today’s science fiction is often tomorrow’s science fact”:

In the near term, world militaries are considering autonomous-weapon systems that can choose and eliminate targets; the UN \[United Nations\] and Human Rights Watch have advocated a treaty banning such weapons. In the medium term … AI may transform our economy to bring both great wealth and great dislocation. Looking further ahead, there are no fundamental limits to what can be achieved.… An explosive transition is possible, although it might play out differently from in the movie\[s\]: machines with superhuman intelligence could repeatedly improve their design even further, triggering what Vernor Vinge called a “singularity.” … One can imagine such technology outsmarting financial markets, out-inventing human researchers, out-manipulating human leaders, and developing weapons we cannot even understand. Whereas the short-term impact of AI depends on who controls it, the long-term impact depends on whether it can be controlled at all. \[So, while\] it’s tempting to dismiss the notion of highly intelligent machines as mere science fiction … this would be a mistake, and potentially our worst mistake in history.^([15](#27_Chapter19.xhtml#rfn19_15))

Hence, it is imperative that we design AI with the capacity to be moral. We cannot design AI to be perfectly moral for more and less obvious reasons. More obviously, we humans have yet to discover the solutions to all the moral problems we have encountered and therefore could not possibly program an AI to be morally omniscient; indeed, the set of moral problems is unbounded (for each one solved, a new and more interesting one emerges), and therefore it would be impossible to preprogram an AI with complete moral knowledge.^([16](#27_Chapter19.xhtml#rfn19_16))

Less obviously, it follows from the latter statement that a perfectly moral mind could not be intelligent because epistemological infallibility—the incapacity to be wrong—is incompatible with intelligence. As discussed in chapter 1, the key to intelligence is creative conjecture interleaved with creative criticism (i.e., error correction). Criticism is crucial because, logically, no intelligence can predict the consequences of its creativity (for then the creative act would be unnecessary), and therefore it is always possible to be mistaken. As the great mathematician Kurt Gödel proved, there will always be truths yet to be proven.

Yet intelligence consists of the competence to detect, eliminate, correct, and learn from mistakes (its own and others). Thus, we can only program an AI with the capacity to make, criticize, and correct moral conjectures (moral statements, moral actions). This is exactly analogous to programming an AI with the capacity for language: given that complete knowledge of language is impossible because the set of all grammatical and meaningful expressions is unbounded, we can only program the system with a grammar to generate (conjecture) grammatical/meaningful expressions and recognize (criticize) ungrammatical/meaningless expressions.

There is much work to endow AI with moral grammar—a competence to distinguish moral and immoral statements/actions in analogous fashion to its competence to distinguish grammatical/meaningful and ungrammatical/meaningless expressions. The imperative for moral grammar is particularly acute for the military, given the inevitable development and adoption of lethal autonomous weapons systems. As Hawking et al. state, “The long-term impact depends on whether \[such AI\] can be controlled at all.”

## **IMPLICATIONS FOR THE UNITED STATES AND ITS MILITARY**

The nations of the world are racing to develop and deploy AI in all domains, most critically in the military. As we have discussed, the science of machine learning powering the new “AI spring” was developed decades ago. Now it is a race to engineer and deploy it. Here, data win because machine learning systems are essentially curve-fitting functions of their data. The problem is that other, more heavily managed societies have more engineers with more access to bigger and better data. So, as implied in chapter 5, this is a race the United States cannot win.

However, this is not to concede defeat in the race for AI, because there is a more important race to win, and it is one we can win because—as we have discussed in many of the chapters—contrary to machine learning assumptions, intelligence cannot be induced from data. What is critical is the intelligent use of data, big or small. Intelligence is the prerequisite. The intelligent use of data is based on the AI being preprogrammed with causal models in which data can be processed as evidence for or against a conjectured analysis of those data. This is analogous to how the human mind is genetically preprogrammed in order to make sense of a sparse-data or data-incomplete world. As pioneering computer scientist Judea Pearl has observed, “Many researchers in \[machine learning\] would like to skip the hard step of constructing or acquiring a causal model and rely solely on data for all cognitive tasks… But we ought to know how profoundly dumb data are about causes and effects.”^([17](#27_Chapter19.xhtml#rfn19_17))

Indeed, cause-effect relations—the most important for understanding the world—are not given in the data. Rather, they are conjectured by the mind, human or AI. So what the United States must do to win the AI race is to develop and deploy an anthronoetic AI organized with innate knowledge of causal models and operations to generate conjectures that then can be tested, criticized, corroborated, refuted, revised, and improved.

This is a mission that cannot be accomplished with more data and more engineers (to which some governments have access). It can only succeed if we invest in the creation of anthronoetic AI—artificial general intelligence.

The road to achieving AGI and developing a fully-fledged digital assistant remains a long one, and not all of the steps to achieving this goal are fully mapped out. Some researchers believe that large physics-based simulations of the human brain could achieve human-level intelligence. Others seek to achieve this goal by coupling existing statistical methods with ever-larger sources of data and computational power. A third camp uses algorithms inspired by cognitive science such as anthronoetic AI, which attempt to achieve high performance given relatively small amounts of data. While the *how* may be in flux, over a longer time horizon AI will evolve from a collection of independent programs, each specifically targeted to a single application, to a smaller number of more capable systems that can be tasked with solving multiple problems and multiple types of problems simultaneously. The ultimate goal is to reduce this to a single system that contains human-level intelligence merged with the computational power and memory of a computer.

## **AI AT WAR**

The implications of current and emerging AI developments will significantly impact a wide range of issues from the future of work to prosecuting warfare. We can group AI applications into three buckets:

1.  Human-assisted tools: This broad category is already transforming societies with both civilian and military applications, including logistics and supply optimization, communications and information management, law enforcement, cyber security, and threat risk mitigation. These applications are ubiquitous across civilian and military domains. The current AI arms race focuses on rapid and efficient implementation of deep-learning AI, “weak AI,” limited by access to massive data, computational power, and manpower. This epitomizes AI “table stakes” and will require significant sustained investment.

2.  General intelligence/general universal intelligence: This type of AI will create disruptive change because of its ability to operate in sparse data environments, with edge cases and ambiguity. Applications are both scary and profound, since these human-thinking machines will possess human-like intelligence, which can be used for immense good—or bad. Nevertheless, this inevitable evolution in AI will reduce most ML capabilities just shy of worthless.

3.  The future of warfighting: This will likely be the biggest change, significantly reducing the entire military enterprise workforce as well as changing military culture, which will evolve to accommodate tools and weapons that are yet to be invented. Nevertheless, just as bullets replaced spears and arrows, radios replaced messengers, and air/space machines replaced scouting, AI will transform solders of the future into humancyber machines with immense lethality, as well as increased responsibility, using technology in unimaginable ways.

## **CONCLUSION**

In this chapter, the future of AI and machine learning were discussed. The AI and ML systems of the present day have a handful of well-recognized limitations. These include difficulty coping with changing environments, the need for data to be rigidly structured, the inability to identify causal structures in data, difficulty in understanding and/or justifying their outputs, and vulnerability to adversarial attacks and deception.

While these limitations do not preclude the use of AI/ML systems, they have served as barriers to entry in many defense and commercial applications. For example, AI systems for ISR (as noted in chapter 9) must be capable of ingesting multiple types of data, potentially including relatively unstructured text data. AI systems that help determine maintenance decisions must be able to justify their actions so that human overseers can “sign off” on their work. AI used for cybersecurity must be able to compensate for the ever-changing threat environment in the cyber world and cannot remain static.

In the short-term future, AI/ML systems will still resemble the systems of today but will have compensated for these known limitations. However, they will still be specialized for a single application. The longer-term future of AI/ML is targeted toward AGI. Rather than developing multiple systems, the objective of AGI is to develop a single system with human-level intelligence that could be applied in many different settings.

The road to AGI will be long, and researchers are pursuing multiple approaches to get there. Many of these methods are traditional approaches that will leverage future increases in computational power and data availability. However, cognitively inspired methods such as anthronoetic AI offer an alternative set of approaches that have the potential to accelerate the rate of AGI development. AGI can seem too sci-fi to be serious, but we should abide by Turing’s admonishment: “For the individual scientist, \[AI research\] requires an imaginative forward glance at history which is difficult, exacting, and only partially achievable.… We must always exert the full strength of our imagination to examine where the full use of our new modalities may lead us.”

AGI—anthronoetic AI—will revolutionize “life, the universe, and everything,” including the military. However, it will not render military personnel—or any persons—redundant. As discussed in chapter 1, human-level/human-style intelligence is the upper bound of intelligence in this universe, and knowledge of any kind is always incomplete. It follows from these premises that any AI, however intelligent, will never be omniscient, and thus will always benefit from collaboration with us and our natural intelligence. If we succeed in creating an anthronoetic AI, it will be a human in all the intellectual and moral senses that count.

Since this human-level/human-style intelligence will run on superhuman hardware, intelligent problem-solving will be maximized. War is an outstanding but solvable problem. Ergo, the beginning of anthronoetic AI could be the end of war, and that surely is the ultimate objective of the U. S. military.

### **NOTES**

# **EPILOGUE**

GEORGE GALDORISI AND SAM J. TANGREDI

**As you have likely concluded** by reading this book’s nineteen chapters, artificial intelligence is a complex subject. Civilian and military uses of big data, artificial intelligence, and machine learning continue to evolve. Precisely how these technologies will impact our lives and influence how wars will be fought in the future is, to borrow a phrase from former secretary of defense Donald Rumsfeld, ultimately one of the great “known unknowns.”

The authors of this book’s chapters have substantial experience with big data, artificial intelligence, and machine learning and defense policy issues, and they have presented substantial information and original thoughts. We have not attempted to “modulate” what they have said for a reason: they all contribute to an informed dialogue on the subject, and we believe it is important for you to hear their unvarnished views.

Whenever one develops a high concept for a book, an important consideration is to define the book’s audience. In the case of this book, there were several natural constituencies we felt could benefit from reading this work.

The first, and most obvious, is those working with big data, artificial intelligence, and machine learning in the military context. This includes those with stewardship for the U.S. military’s strategy and doctrine, requirements officers in the Pentagon, acquisition officials in all the services, and especially the legions of scientists and engineers working in the military’s vast research and development enterprise, as well as their industry partners.

The second audience for the thoughts contained in this book includes all national security professionals, and in particular those in the field of educating the next generation of U. S. military leaders regarding just what big data, artificial intelligence, and machine learning mean in the military context and, importantly, what these technologies can do to provide our warfighters with an edge in combat. It is clear to us that U.S. military platforms, systems, sensors, and weapons will have some aspect of these technologies inserted into them. It is vital that we educate military leaders at all levels and provide a basic understanding of these technologies—both their capabilities and vulnerabilities. Knowing something about what the “black box” does (and cannot do) will ensure that our military uses these technologies in a thoughtful way.

But beyond these two readership groups, we intend this book to be one that helps an informed U. S. citizenry and anyone interested in the future of international security recognize the enormous impact big data, artificial intelligence, and machine learning will have on future military operations. As citizens and taxpayers, we all have “skin in this game” and must ensure that our elected representatives both challenge and support our senior military leaders regarding the who, what, where, why, when, and how of these technologies will be used in the military context. This is especially important when it comes to armed autonomous or semi-autonomous weapons.

There is always a tendency to embrace a promising technology as a “shiny new object” that will change the world, only to have it not reach the promise of its most zealous advocates. As anyone working in the field of artificial intelligence will hasten to tell you, there have been “AI winters” during which progress in these technologies has all but stopped. However, we believe firmly that big data, artificial intelligence, and machine learning are permanent technological developments and will profoundly influence military strategy, operations, and tactics in the near-term, mid-term, and distant future. They are not just buzzwords.

This book’s authors have addressed both the opportunities and challenges involved in inserting big data, artificial intelligence, and machine learning into military platforms, systems, sensors, and weapons. While effectual and seamless future development is not assured, we do believe that the desire to utilize AI in a thoughtful way is becoming a core belief of our senior military leaders. Here is some of what we have heard since our authors started work.

During his congressional testimony in July 2019, in response to the question, “What is the number one priority for DoD technology modernization?” defense secretary Mark Esper noted, “For me it’s artificial intelligence. I think artificial intelligence will likely change the character of warfare, and I believe whoever masters it first will dominate on the battlefield for many, many, many years. It’s a fundamental game changer. We have to get there first.”^([1](#28_Epilogue.xhtml#fn1))

In the naval context, our Department of the Navy officials appear to be on the right track. In a keynote address at the annual U.S. Naval Institute/AFCEA “West” Symposium, the assistant secretary of the Navy for research, development, and acquisition, the Honorable James Geurts, put the importance of these technologies this way: “If a force can harness AI to allow decision makers to make decisions faster than the adversary, it will win every time.”^([2](#28_Epilogue.xhtml#fn2))

Uniformed naval leaders appear to be leaning in as well. Speaking on technology priorities, Chief of Naval Operations Adm. Michael Gilday said, “On the top of my list I would put artificial intelligence.”^([3](#28_Epilogue.xhtml#fn3)) Speaking on the future of his service, commandant of the Marine Corps Gen. David Berger noted, “Our current resource request prioritizes our future naval force capabilities: not just conventional, but also next generation weapons like artificial intelligence, unmanned/man-machine learning and integration.”^([4](#28_Epilogue.xhtml#fn4))

One might take issue, as some of our authors do, with the rhetoric of AI changing the character of war, of being a “game changer.” However, one cannot take issue with the fact that current U.S. defense leaders have expressed a commitment to furthering the development of military applications of AI. Expressed too has been a commitment to ethical application.

Given the enormous number of stakeholders in the realm of military big data, artificial intelligence, and machine learning, it is often a challenge to understand where the responsibility lays for instantiating these technologies into U.S. military platforms, systems, sensors, and weapons. Today, the center of gravity for this effort is the newly formed Joint Artificial Intelligence Center (JAIC), which is currently the node for pulling together DoD efforts in this area. Here is how the JAIC defined its mission: “Like electricity or computers, modern AI offers a transformative portfolio of capabilities that will affect the full spectrum of DoD operations—from the back office to the front lines of the battlefield. The National Defense Strategy states that the United States will invest broadly in military application of autonomy, AI, and machine learning to gain competitive military advantages. Accelerated adoption of AI will help protect American servicemembers, safeguard our citizens, defend our allies, and improve the effectiveness, affordability, and speed of DoD operations.”

While the JAIC focuses on *all* aspects of how big data, artificial intelligence, and machine learning can deliver a warfighting edge, one sentence in the JAIC’s capstone publication captures what we believe these technologies can provide for our warfighters: “AI’s most valuable contributions will come from how we use it to make better and faster decisions. This includes gaining a deeper understanding of how to optimize human-machine teaming.”

From the time we delivered the manuscript for this book to the Naval Institute Press in late 2019 until the day you read this, AI has been evolving and changing. No book can possibly keep pace with all new technological developments. But what will always remain relevant are the basic issues revealed in the chapters: the challenges of scientific advances and engineering development, the painstaking work required to achieve innovation, the need for rigorous policy analysis, the friction of implementation within complex organizations, ethical concerns, and the ever-present dilemma of how to trust new technologies. As we suggested above, an informed citizenry is the most important aspect of ensuring that the U.S. military harnesses these technologies in a thoughtful way.

Finally, one important way for you—the reader—to give voice to your thoughts on this vital subject is to enter the defense dialog and share your ideas on the subject in the U.S. Naval Institute’s open forum publication, U.S. Naval Institute *Proceedings*. More on how to do this is on the USNI website at [https://www.usni.org/](https://www.usni.org/).

### **NOTES**

# **AFTERWORD**

ADM. MICHAEL S. ROGERS, USN (RET.)

**Big data, AI, and machine learning (ML)** are having, and will continue to have, profound implications for the world around us. They affect almost every aspect of the broader world in which we live, but—as addressed in this book—they particularly affect our profession as warriors in the service of our nation. This book has focused on the latter (from fires to command and control to command, control, communications, computers, intelligence, surveillance, and reconnaissance, to deterrence, and so on), but we, as citizens of this nation and the broader global community, forget the former at our peril.

There are many challenges to our ability to understand fully and implement these capabilities as warriors—not the least of which is separating fact from fiction (which is one of the primary benefits of this book). While there is great benefit to be gained, there are no perfect solutions. Nor are big data, AI, and machine learning capable of solving every challenge we face on their own. They have their vulnerabilities and limitations, and we must understand these to the same extent that we conceptualize how their benefits may be applied to achieving mission success. All the while, we need to consider and anticipate how others might use them to forestall our ability to achieve that mission success. This is not an insignificant realization; our challenge in applying AI is about much more than just gaining an attack advantage. We must be ready to respond to their use by opponents attempting to gain advantage for themselves while placing us at a corresponding disadvantage.

During my own thirty-seven-year journey in uniform, I was part of a Navy and a Department of Defense (DoD) that transitioned from a focus on largely organically generated data and information to one in which individuals, units, and formations were literally inundated with both internal data and information received from a much broader external set of actors and system capabilities. In the face of that massive new influx, we often failed to remember that the real value of data and information lies in the generation of knowledge and insight, not just the acquisition of more data. They are precursors to the higher level of understanding, which generates advantage for us on the battlefield, but they are means to an end and not the end itself. In the future, AI, ML, and big data are going to be the tools that make that higher level of understanding a tangible and valuable reality.

Initial efforts to meet the challenge of massive information and the need for speed in recognition of and action against modern threats were built around the development of rules-based and automated or autonomous systems such as AEGIS, SLQ-32, close-in weapons systems, and others. But how do we meet the challenges of a world in which many of the activities of interest or concern are neither rules-based nor readily discernable?

As a senior commander and leader in DoD, I continually asked myself about how I could focus on matters that generate the greatest value in executing our mission sets, and not be side-tracked or slowed by focusing on data and information that weren’t relevant to mission outcomes (or at least were not as important). In that respect, the true advantage of AI and ML and their ability to harness big data is in providing warriors with the insight and knowledge at speeds that can help focus on the critical. Through that process, we can learn to be adaptive and anticipatory and to do so against complex challenges that have little formal structure or rules and many variables, of which many are unknown or not understood.

As the commander of U. S. Cyber Command and the director of the National Security Agency in my final years of service, I focused much of my time—and that of the teams of which I was a part—in trying to crystalize our ideas on how to use these tools, while simultaneously trying to understand how our competitors and potential adversaries viewed these ideas and their strategies in attempting to harness their advantage.

I also spent a good deal of time focused on the human element in this process. What should the role of individuals be in the application of these capabilities? What are their implications for creating the warriors of the future? What are the human impediments to the generation and application of these capabilities within DoD? These are not easy questions to answer—particularly in a hierarchical or bureaucratic culture that is not inclined to rapidly embrace significant change. Contemplation led me to believe that, as noted in chapter 6, it is the human element, not the technology itself, that will be the most challenging aspect of developing and implementing AI and ML capabilities. We truly need to think beyond the technology and determine the role of humans in this world of AI and ML. What level of oversight or external involvement in these processes is appropriate, and under what conditions does that oversight/safety regime change or adapt?

AI and machine learning have advanced to the point where they can readily surpass humans in rules-based activity (such as games) because there are defined frameworks for these activities and AI can process more data more quickly than can humans. However, it is in the imperfect, non-rules–based challenge of the battlefield where AI and ML offer us the greatest hope for speed and advantage. The ultimate goal is to provide us with a greater range of options, not just within a great power competition framework (as important as that is), but across the full range of the DoD mission sets. Yet to do this will be exceedingly difficult, and there always will be limitations.

In all military operations, learning by trial and error (or learning while moving to contact) is a resource-intensive approach to mission accomplishment and a high-risk methodology in achieving mission success. AI and ML have the potential of allowing us to bypass or mitigate this human trial-and-error approach through the process of learning from their own trials and errors under simulated conditions. As previously discussed, the greatest value may be in helping human anticipation—the ability to use data and information to generate knowledge and insight of that which is unknown, previously unseen, or not rules-based in its approach. This anticipatory ability is not just for attack, but also to defend and counter.

Concerning cyber operations, our biggest challenge lies in differing mindsets between defensive and offensive actions. Most defensive strategies are based on a priori knowledge of activity; in other words, we optimize ourselves against that which is known or previously observed. However, on the offensive side, we need to be faster in generating previously unknown capabilities to both penetrate opposing systems and respond in real time to the defensive actions of the target. This divergence leads to more as-yet-unanswered questions. How do we generate weapons that can morph or adapt to what they encounter, and how do we create defensive methodologies and capabilities that can do the same? Can AI applications lead to systems that can “self-heal” and adapt on the fly? In this, encryption will also be both another massive opportunity and a threat.

My thanks to Sam Tangredi, George Galdorisi, and the many distinguished and insightful contributors to this book. Great journeys often begin with simple steps like committing insights and views to paper. We are all part of the voyage of trying to fully understand and, in turn, maximize the contribution of big data, AI, and machine learning to DoD’s accomplishment of its mission sets. The implications of failing in this effort are profound. We are in a race or competition to harness these capabilities against others who might do us harm—a race we dare not lose.

There are great opportunities in big data, AI, and machine learning, and I encourage us not to be fearful. Fortune favors the bold. Teams and individuals who can anticipate change and optimize themselves to apply new capabilities and embrace new methodologies, new structures, new processes, and new skill sets are the most likely to be so favored. It will take the insights of many individuals from a multitude of disciplines and perspectives if we are to truly understand and optimize these capabilities to generate effective outcomes. Thanks to all who contributed here, and BE BOLD!

# **SELECTED BIBLIOGRAPHY**

Adams, Karla, and William Booth. “Nerve Agent Poisoning: Theresa May Says Russian Intelligence Officers Carried Out Attack on Ex-Spy in Salisbury.” *Washington Post*, September 5, 2018. [https://www.washingtonpost.com/world/europe/britain-charges-two-russians-with-attempted-murder-of-ex-spy-with-nerve-agent/2018/09/05/db99c5c8-b0f7-11e8-a20b-5f4f84429666\_story.html?arc404=true](https://www.washingtonpost.com/world/europe/britain-charges-two-russians-with-attempted-murder-of-ex-spy-with-nerve-agent/2018/09/05/db99c5c8-b0f7-11e8-a20b-5f4f84429666_story.html?arc404=true).

Adhikari, Ani, and John DeNero. *Computational and Inferential Thinking: The Foundations of Data Science*. [www.data8.org/fa15/text/index.html](http://www.data8.org/fa15/text/index.html).

Adhikari, Gautam. “American Power: The End of the Unipolar Myth.” *New York Times*, September 27, 2004. [https://www.nytimes.com/2004/09/27/opinion/american-power-the-end-of-the-unipolar-myth.html](https://www.nytimes.com/2004/09/27/opinion/american-power-the-end-of-the-unipolar-myth.html).

Adkins, Roy. *Nelson’s Trafalgar: The Battle That Changed the World*. New York: Penguin, 2006.

Akerlof, George A., and Robert J. Shiller. *Phishing for Phools: The Economics of Manipulation and Deception*. Princeton, NJ: Princeton University Press, 2015.

Alberts, David S., and Richard E. Hayes. *Power to the Edge: Command and Control in the Information Age*. Washington, DC: Department of Defense Command and Control Research Program, 2005.

Allen, Gregory C. *Understanding China’s AI Strategy: Clues to Chinese Strategic Thinking on Artificial Intelligence and National Security*. Washington, DC: Center for a New American Security, February 2019. [https://s3.amazonaws.com/files.cnas.org/documents/CNAS-Understanding-Chinas-AI-Strategy-Gregory-C.-Allen-FINAL-2.15.19.pdf](https://s3.amazonaws.com/files.cnas.org/documents/CNAS-Understanding-Chinas-AI-Strategy-Gregory-C.-Allen-FINAL-2.15.19.pdf).

Allen, Gregory C., and Taniel Chan. *Artificial Intelligence and National Security*. Cambridge, MA: Harvard Kennedy School, July 2017. [https://www.belfercenter.org/sites/default/files/files/publication/AI%20NatSec%20-%20final.pdf](https://www.belfercenter.org/sites/default/files/files/publication/AI%20NatSec%20-%20final.pdf).

Allen, John, and Amir Husain. “AI Will Change the Balance of Power.” U.S. Naval Institute *Proceedings* 144, no. 3 (August 2018): 26–31. [https://www.usni.org/magazines/proceedings/2018-08/ai-will-change-balance-power](https://www.usni.org/magazines/proceedings/2018-08/ai-will-change-balance-power).

Allen, Kenneth, Brian Chao, and Ryan Kinsella. *China’s Military Political Commissar System in Comparative Perspective*. China Brief 13, no. 5 (March 4, 2013). [https://jamestown.org/program/chinas-military-political-commissar-system-in-comparative-perspective/](https://jamestown.org/program/chinas-military-political-commissar-system-in-comparative-perspective/).

Allison, Graham T. *Conceptual Models and the Cuban Missile Crisis: Rational Policy, Organization Process, and Bureaucratic Politics*, P-3919. Santa Monica, CA: RAND Corporation, 1968.

———. *Essence of Decision: Explaining the Cuban Missile Crisis*. Boston: Little, Brown, 1971.

Allport, Rowan. “Russian Conventional Weapons Are Deadlier Than Its Nukes.” *Foreign Policy*, January 17, 2019. [https://foreignpolicy.com/2019/01/17/russias-conventional-weapons-are-deadlier-than-its-nukes/](https://foreignpolicy.com/2019/01/17/russias-conventional-weapons-are-deadlier-than-its-nukes/).

Aquinas, Thomas. *Quaestiones disputatae de veritate*. [http://www.corpusthomisticum.org/qdv02.html](http://www.corpusthomisticum.org/qdv02.html).

Arkin, William. *Data and the Illusion of Perfect Warfare*. New York: Little, Brown and Company, 2015.

*Artificial Intelligence: Foundations of Computational Agents*, 2nd ed. Cambridge: Cambridge University Press, 2017.

“Artificial Intelligence Is Changing Every Aspect of War.” *The Economist*, September 7, 2019. [https://www.economist.com/science-and-technology/2019/09/07/artificial-intelligence-is-changing-every-aspect-of-war](https://www.economist.com/science-and-technology/2019/09/07/artificial-intelligence-is-changing-every-aspect-of-war).

Assistant Secretary of Defense (Research and Engineering). “Autonomy Community of Interest (COI) Test and Evaluation, Verification and Validation (TEVV) Working Group Technology Investment Strategy 2015–2018,” June 12, 2015. [https://defenseinnovationmarketplace.dtic.mil/wp-content/uploads/2018/02/OSD\_ATEVV\_STRAT\_DIST\_A\_SIGNED.pdf](https://defenseinnovationmarketplace.dtic.mil/wp-content/uploads/2018/02/OSD_ATEVV_STRAT_DIST_A_SIGNED.pdf).

Atherton, Kelsey. “Are Killer Robots the Future of War? Parsing the Facts on Autonomous Weapons.” *New York Times Magazine*, November 15, 2018. [https://www.nytimes.com/2018/11/15/magazine/autonomous-robots-weapons.html](https://www.nytimes.com/2018/11/15/magazine/autonomous-robots-weapons.html).

———. “Soul Search Engine.” *C4ISRNET*, July/August 2018, 12–14.

Awad, Mariette, and Rahul Khanna. *Efficient Learning Machines, Theories, Concept and Applications for Engineers and System Designers*. New York: Apress Media, 2015. [https://link.springer.com/content/pdf/bfm%3A978-1-4302-5990-9%2F1.pdf](https://link.springer.com/content/pdf/bfm%3A978-1-4302-5990-9%2F1.pdf).

Axe, David. “The Case of the Chinese Aircraft Carrier Spy.” *Daily Beast*, February 18, 2019. [https://www.thedailybeast.com/the-case-of-the-chinese-aircraft-carrier-spy](https://www.thedailybeast.com/the-case-of-the-chinese-aircraft-carrier-spy).

———. “That Time an Air Force F-16 and an Army Missile Battery Fought Each Other.” *War is Boring*, June 5, 2014. [https://medium.com/war-is-boring/that-time-an-air-force-f-16-and-an-army-missile-battery-fought-each-other-bb89d7d03b7d](https://medium.com/war-is-boring/that-time-an-air-force-f-16-and-an-army-missile-battery-fought-each-other-bb89d7d03b7d).

———. “This Video May Be the Future of Russia’s Army: Armed Ground Robots.” *National Interest*, March 18, 2019. [https://nationalinterest.org/blog/buzz/video-might-be-future-russias-army-armed-ground-robots-48022](https://nationalinterest.org/blog/buzz/video-might-be-future-russias-army-armed-ground-robots-48022).

Ayoub, Kareem, and Kenneth Payne. “Strategy in the Age of Artificial Intelligence.” *Journal of Strategic Studies* 39, no. 5–6 (2016): 793–819. [https://www.tandfonline.com/doi/full/10.1080/01402390.2015.1088838?src=recsys](https://www.tandfonline.com/doi/full/10.1080/01402390.2015.1088838?src=recsys).

Baker, Berenice. “Orca XLUUV: Boeing’s Whale of an Unmanned Sub.” *Naval Technology*, July 1, 2019. [https://www.naval-technology.com/features/boeing-orca-xluuv-unmanned-submarine/](https://www.naval-technology.com/features/boeing-orca-xluuv-unmanned-submarine/).

Bartlett, Matt. “The AI Arms Race in 2019.” *Towards Data Science*, January 28, 2019. [https://towardsdatascience.com/the-ai-arms-race-in-2019-fdca07a086a7](https://towardsdatascience.com/the-ai-arms-race-in-2019-fdca07a086a7).

Bendett, Samuel. “Autonomous Robotic System in the Russian Ground Forces.” *Mad Scientist Laboratory*, February 11, 2019. [https://madsciblog.tradoc.army.mil/120-autonomous-robotic-systems-in-the-russian-ground-forces/](https://madsciblog.tradoc.army.mil/120-autonomous-robotic-systems-in-the-russian-ground-forces/).

———. “Did Russia Just Concede a Need to Regulate Military AI?” *Defense One*, April 25, 2019. [https://www.defenseone.com/ideas/2019/04/russian-military-finally-calling-ethics-artificial-intelligence/156553/?oref=defenseone\_today\_nl](https://www.defenseone.com/ideas/2019/04/russian-military-finally-calling-ethics-artificial-intelligence/156553/?oref=defenseone_today_nl).

———. “Here’s How the Russian Military Is Organizing to Develop AI.” *Defense One*, July 20, 2018. [https://www.defenseone.com/ideas/2018/07/russian-militarys-ai-development-roadmap/149900/](https://www.defenseone.com/ideas/2018/07/russian-militarys-ai-development-roadmap/149900/).

———. “Russian Ground Battlefield Robots: A Candid Evaluation and Ways Forward.” *Real Clear Defense*, June 26, 2018. [https://www.realcleardefense.com/articles/2018/06/26/russian\_ground\_battlefield\_robots\_a\_candid\_evaluation\_113558.html](https://www.realcleardefense.com/articles/2018/06/26/russian_ground_battlefield_robots_a_candid_evaluation_113558.html).

———. “Putin Orders Up a National AI Strategy.” *Defense One*, January 31, 2019. [https://www.defenseone.com/technology/2019/01/putin-orders-national-ai-strategy/154555/?oref=d-river](https://www.defenseone.com/technology/2019/01/putin-orders-national-ai-strategy/154555/?oref=d-river).

Betz, Brandy. “AI Unit Owes Alphabet over 1B \[Pounds Sterling\].” *Seeking Alpha*, August 7, 2019. [https://seekingalpha.com/news/3488507-ai-unit-owes-alphabet-1b?dr=1#email\_link](https://seekingalpha.com/news/3488507-ai-unit-owes-alphabet-1b?dr=1#email_link).

Bevilacqua, Matt. “Uber Was Warned Before Self-Driving Car Crash that Killed Woman Walking Bicycle.” *Bicycling*, December 18, 2018. [https://www.bicycling.com/news/a25616551/uber-self-driving-car-crash-cyclist/](https://www.bicycling.com/news/a25616551/uber-self-driving-car-crash-cyclist/).

Beyene, Ayne, and Tewelle Welemariam. *Concept Drift in Surgery Prediction*. Master’s thesis, Blekinge Institute of Technology, Karlskrona, Sweden, September 2012. [https://www.diva-portal.org/smash/get/diva2:829599/FULLTEXT01.pdf](https://www.diva-portal.org/smash/get/diva2:829599/FULLTEXT01.pdf).

Bidwell, Christopher, and Bruce W. MacDonald. *Emerging Disruptive Technologies and Their Potential Threat to Strategic Stability and National Security*. Washington, DC: Federation of American Scientists, September 2018. [https://fas.org/wp-content/uploads/media/FAS-Emerging-Technologies-Report.pdf](https://fas.org/wp-content/uploads/media/FAS-Emerging-Technologies-Report.pdf).

Blank, Steve. “The National Defense Strategy: A Compelling Call for Defense Innovation.” *War on the Rocks*, February 12, 2018. [https://warontherocks.com/2018/02/national-defense-strategy-compelling-call-defense-innovation/](https://warontherocks.com/2018/02/national-defense-strategy-compelling-call-defense-innovation/).

Blasko, Dennis J. “PLA Weaknesses and Xi’s Concerns about PLA Capabilities.” Testimony before the U.S.-China Economic and Security Review Commission Panel on “Backlash from Abroad: The Limits of Beijing’s Power to Shape its External Environment,” February 7, 2019. [https://www.uscc.gov/sites/default/files/Blasko\_USCC%20Testimony\_FINAL.pdf](https://www.uscc.gov/sites/default/files/Blasko_USCC%20Testimony_FINAL.pdf).

Bonaccorso, Giuseppe. *Mastering Machine Learning Algorithms*. Birmingham, UK: Packt Publishing Ltd., 2018.

Boot, Max. *War Made New: Weapons, Warriors, and the Making of the Modern World*. New York: Gotham Books, 2006.

Booth, Ken. *Strategy and Ethnocentrism*. London: Croom, Helm, 1979.

Bosse’, E’loi, Jean Roy, and Steve Wark. *Concepts, Models, and Tools for Information Fusion*. Boston: ARTECH House, 2007.

Boyd, John. *Destruction and Creation*. Fort Leavenworth, KS: U.S. Army Command and General Staff College, 1976.

Brands, Hal. *Making the Unipolar Moment: U.S. Foreign Policy and the Rise of the Post–Cold War Order*. Ithaca, NY: Cornell University Press, 2016.

———. “Paradoxes of the Gray Zone.” Foreign Policy Research Institute, *E-Notes*, February 5, 2016. [http://www.fpri.org/article/2016/02/paradoxes-gray-zone/](http://www.fpri.org/article/2016/02/paradoxes-gray-zone/).

Bryant, William. “Cyberspace Resiliency: Springing Back with the Bamboo.” In Misty Blowers, ed., *Evolution of Cyber Technologies and Operations to 2035*. New York: Springer, 2015.

Buckner, Brandon. “The Case for Military Adoption of Artificial Intelligence.” Leidos, February 8, 2019. [https://www.leidos.com/insights/case-military-adoption-artificial-intelligence](https://www.leidos.com/insights/case-military-adoption-artificial-intelligence).

“Building Trust in AI.” [IBM.com](http://IBM.com). [https://www.ibm.com/watson/advantage-reports/future-of-artificial-intelligence/building-trust-in-ai.html](https://www.ibm.com/watson/advantage-reports/future-of-artificial-intelligence/building-trust-in-ai.html).

Burgess, Richard. “CNO: Precision Era Gives Way to Decision Era.” *Sea-power Magazine Online*, June 13, 2017. [http://seapowermagazine.org/stories/20170613-CNO.html](http://seapowermagazine.org/stories/20170613-CNO.html).

Burkov, Andriy. *The Hundred-Page Machine Learning Book*. Self-published, 2019.

Business Roundtable. *Growing Business Dependence on the Internet*. Washington, DC: Business Roundtable, 2007. [https://s3.amazonaws.com/brt.org/archive/200709\_Growing\_Business\_Dependence\_on\_the\_Internet.pdf](https://s3.amazonaws.com/brt.org/archive/200709_Growing_Business_Dependence_on_the_Internet.pdf).

Calfee, Sharif, and Harrison Schramm. “Better Data Can Improve Safety at Sea.” U.S. Naval Institute *Proceedings* 144, no. 7 (July 2018). [https://www.usni.org/magazines/proceedings/2018/july/better-data-can-improve-safety-sea](https://www.usni.org/magazines/proceedings/2018/july/better-data-can-improve-safety-sea).

Campaign to Stop Killer Robots. “A Growing Global Coalition: About Us.” [https://www.stopkillerrobots.org/about/#about](https://www.stopkillerrobots.org/about/#about).

Campbell, Thomas A. *Artificial Intelligence: An Overview of State Initiatives*. Evergreen, CO: FutureGrasp LLC, 2019.

Cannon-Bowers, Janis, and Eduardo Salas. *Making Decisions Under Stress*. Washington, DC: American Psychological Association, October 1998.

Cao, Longbing, and Philip Yu, eds. *Behavior Computing: Modeling, Analysis, Mining and Decision*. New York: Springer, 2012.

Carr, Nevin. “Balancing the Science Behind Warfighting.” U.S. Naval Institute *Proceedings* 137, no. 11 (November 2011): 52–57. [https://www.usni.org/magazines/proceedings/2011/november/balancing-science-behind-warfighting](https://www.usni.org/magazines/proceedings/2011/november/balancing-science-behind-warfighting).

“Carter: Human Input Required for Autonomous Weapon Systems.” *Inside the Pentagon*, November 29, 2012. [https://www.jstor.org/stable/insipent.28.48.02](https://www.jstor.org/stable/insipent.28.48.02).

Carter, Shan, et al. “Exploring Neural Networks with Activation Atlases.” *Distill*, March 8, 2019. [https://distill.pub/2019/activation-atlas/](https://distill.pub/2019/activation-atlas/).

Castelvecchi, Davide. “Can We Open the Black Box of AI?” *Nature*, October 5, 2016. [https://www.nature.com/news/can-we-open-the-black-box-of-ai-1.20731](https://www.nature.com/news/can-we-open-the-black-box-of-ai-1.20731).

Casti, John L. *Complexification: Explaining a Paradoxical World Through the Science of Surprise*. New York: HarperCollins, 1994.

Cebrowski, Arthur K., and John H. Garstka. “Network-Centric Warfare—Its Origin and Future.” U.S. Naval Institute *Proceedings* 124, no. 1 (January 1998): 28–35.

Chambers, Nathanael, et al. “Using Social Media Text to Detect Denial-of-Service Attacks: Applying Natural Language Processing to Network Security.” *Proceedings of the Conference on Empirical Methods in Natural Language Processing, 2018*. Association for Computational Linguistics, 2018.

Chen, Lingwei, Yanfang Ye, and Thirimachos Bourlai. “Adversarial Machine Learning in Malware Detection: Arms Race Between Evasion Attack and Defense.” 2017 European Intelligence and Security Informatics Conference. [https://ieeexplore.ieee.org/document/8240775](https://ieeexplore.ieee.org/document/8240775).

“China’s Competitive Strategy: An Interview with Bob Work, Conducted 10 October 2018.” *Strategic Studies Quarterly* 12, no. 1 (Spring 2019): 2–11. [https://www.airuniversity.af.edu/Portals/10/SSQ/documents/Volume-13\_Issue-1/Work.pdf](https://www.airuniversity.af.edu/Portals/10/SSQ/documents/Volume-13_Issue-1/Work.pdf).

Chivukula, A. S., and W. Liu. “Adversarial Deep Learning Models with Multiple Adversaries.” *IEEE Transactions on Knowledge and Data Engineering* 31, no. 6 (June 2019): 1066–79.

Chomsky, Noam. *Cartesian Linguistics*. New York: Harper and Row, 1966.

———. *Reflections on Language*. New York: Pantheon Books, 1975.

———. “Review of B. F. Skinner, *Verbal Behavior.” Language* 35, no. 1 (January–March 1959): 38–42.

Clark, Andy. “Natural-Born Cyborgs?” In *Cognitive Technology: Instruments of Mind*, proceedings of International Conference on Cognitive Technology, 2001. [https://link.springer.com/chapter/10.1007/3-540-44617-6\_2](https://link.springer.com/chapter/10.1007/3-540-44617-6_2).

Clark, Bryan, et al. *Regaining the High Ground at Sea: Transforming the U.S. Navy’s Carrier Air Wing for Great Power Competition*. Washington, DC: Center for Strategic and Budgetary Assessments, December 14, 2018. [https://csbaonline.org/research/publications/regaining-the-high-ground-at-sea-transforming-the-u.s.-navys-carrier-air-wi](https://csbaonline.org/research/publications/regaining-the-high-ground-at-sea-transforming-the-u.s.-navys-carrier-air-wi).

Clarke, Arthur C. “Superiority.” *Magazine of Fantasy and Science Fiction*, August 1951, 3–11. [https://www.baen.com/Chapters/1439133476/1439133476\_\_\_5.htm](https://www.baen.com/Chapters/1439133476/1439133476___5.htm).

Clausewitz, Carl von. *On War*. Ed. and trans. Michael Howard and Peter Paret. Princeton, NJ: Princeton University Press, 1984.

Cochran, James J., ed. *INFORMS Analytics Body of Knowledge*. Hoboken, NJ: John Wiley and Sons, 2019.

Coleman, Amber G. *A Predictive Analysis of the Department of Defense Distribution System Using Random Forests*. Master’s thesis, Naval Postgraduate School, June 2016. [https://calhoun.nps.edu/handle/10945/49436](https://calhoun.nps.edu/handle/10945/49436).

Comfort, Louise, Arjen Boin, and Chris Demchak, eds. *Designing Resilience: Preparing for Extreme Events*. Pittsburgh: University of Pittsburgh Press, 2010.

Copeland, B. Jack. *The Essential Turing*. Oxford: Oxford University Press, 2004.

Cordell, Carten. “DOD Awards Coveted JEDI Contract to Microsoft.” *Washington Business Journal*, October 27, 2019. [https://www.bizjournals.com/washington/news/2019/10/25/dod-awards-early-phase-of-10b-jedi-to-microsoft.html](https://www.bizjournals.com/washington/news/2019/10/25/dod-awards-early-phase-of-10b-jedi-to-microsoft.html).

Cordle, John. “Design Systems that Work for People.” U.S. Naval Institute *Proceedings* 144, no. 9 (September 2018): 18-23.

Corrigan, Jack. “Inside DARPA’s Ambitious ‘AI Next’ Program.” *Defense One*, March 10, 2019. [https://www.defenseone.com/technology/2019/03/inside-pentagons-big-plans-develop-trustworthy-artificial-intelligence/155427/?oref=d\_brief\_nl](https://www.defenseone.com/technology/2019/03/inside-pentagons-big-plans-develop-trustworthy-artificial-intelligence/155427/?oref=d_brief_nl).

———. “Lawmakers Propose $2.2B Over 5 Years to Advance AI.” *Nextgov*, May 22, 2019. [https://www.nextgov.com/emerging-tech/2019/05/lawmakers-propose-22-billion-advance-ai-over-next-five-years/157169/](https://www.nextgov.com/emerging-tech/2019/05/lawmakers-propose-22-billion-advance-ai-over-next-five-years/157169/).

———. “NIST Lays Out Roadmap for Developing Artificial Intelligence Standards.” *Nextgov*, August 13, 2019. [https://www.nextgov.com/emerging-tech/2019/08/nist-lays-out-roadmap-developing-artificial-intelligence-standards/159119/](https://www.nextgov.com/emerging-tech/2019/08/nist-lays-out-roadmap-developing-artificial-intelligence-standards/159119/).

———. “The Pentagon Wants AI to Take Over the Scientific Process.” *Defense One*, August 25, 2018. [https://www.defenseone.com/technology/2018/08/pentagon-wants-ai-take-over-scientific-process/150810/](https://www.defenseone.com/technology/2018/08/pentagon-wants-ai-take-over-scientific-process/150810/).

Creemers, Rogier, ed. “PRC Next Generation Artificial Intelligence Development Plan.” *China Copyright and Media*, July 20, 2017. [https://chinacopyrightandmedia.wordpress.com/2017/07/20/a-next-generation-artificial-intelligence-development-plan/](https://chinacopyrightandmedia.wordpress.com/2017/07/20/a-next-generation-artificial-intelligence-development-plan/).

Culora, Thomas J. “The Strategic Implications of Obscurants.” *Naval War College Review* 63 no. 3 (Fall 2010): 73–84. [https://digital-commons.usnwc.edu/nwc-review/vol63/iss3/6](https://digital-commons.usnwc.edu/nwc-review/vol63/iss3/6).

Darnell, Daniel J., and George J. Trautman III. “Shoulder to Shoulder: The Marine Corps and Air Force in Combat.” *Joint Force Quarterly* 52 (1st Quarter 2009): 125–28.

“Data, Data Everywhere.” *The Economist*, February 27, 2010. [https://www.economist.com/special-report/2010/02/27/data-data-everywhere](https://www.economist.com/special-report/2010/02/27/data-data-everywhere).

Davis, Ernest, and Gary Marcus. “Commonsense Reasoning and Common sense Knowledge in Artificial Intelligence.” *Communications of the ACM 58, no*. 9 (August 2015): 92–93. [https://doi.org/10.1145/2701413](https://doi.org/10.1145/2701413).

Davis, Martin. *The Universal Computer: The Road from Leibniz to Turing*. New York: A. K. Peters/CRC Press, 2011.

Davis, Zachary S. *Artificial Intelligence on the Battlefield: An Initial Survey of Potential Implications for Deterrence, Stability and Strategic Surprise*. Center for Global Security Research, Lawrence Livermore National Laboratory, March 2019.

“DeepMind’s Go Playing Software Can Now Beat You at Two More Games.” *New Scientist*, December 6, 2018. [https://www.newscientist.com/article/2187599-deepminds-go-playing-software-can-now-beat-you-at-two-more-games/](https://www.newscientist.com/article/2187599-deepminds-go-playing-software-can-now-beat-you-at-two-more-games/).

Defense Advanced Research Projects Agency. “ACTUV ‘Sea Hunter’ Prototype Transitions to Office of Naval Research for Further Development.” DARPA Web site, January 30, 2018. [https://www.darpa.mil/news-events/2018-01-30a](https://www.darpa.mil/news-events/2018-01-30a).

———. “AI Next Campaign.” DARPA Web site, no date. [https://www.darpa.mil/work-with-us/ai-next-campaign](https://www.darpa.mil/work-with-us/ai-next-campaign).

———. “DARPA Tiles Together a Vision of Mosaic Warfare.” DARPA Web site, no date. [https://www.darpa.mil/work-with-us/darpa-tiles-together-a-vision-of-mosiac-warfare](https://www.darpa.mil/work-with-us/darpa-tiles-together-a-vision-of-mosiac-warfare).

———. “Guaranteeing AI Robustness against Deception (GARD).” DARPA Web site, February 6, 2019. [https://www.darpa.mil/news-events/2019-02-06](https://www.darpa.mil/news-events/2019-02-06).

Defense Intelligence Agency. *Russia Military Power: Building a Military to Support Great Power Aspirations*. 2017. [https://www.dia.mil/Portals/27/Documents/News/Military%20Power%20Publications/Russia%20Military%20Power%20Report%202017.pdf?ver=2017-06-28-144235-937](https://www.dia.mil/Portals/27/Documents/News/Military%20Power%20Publications/Russia%20Military%20Power%20Report%202017.pdf?ver=2017-06-28-144235-937).

Defense Science Board. *Defense Science Board Summer Study on Autonomy*, June 9, 2016. [https://www.hsdl.org/?view&did=794641](https://www.hsdl.org/?view&did=794641).

———. *Task Force Report: The Role of Autonomy in DoD Systems*, July 2012. [http://sites.nationalacademies.org/cs/groups/pgasite/documents/webpage/pga\_082152.pdf](http://sites.nationalacademies.org/cs/groups/pgasite/documents/webpage/pga_082152.pdf)(slides), [https://fas.org/irp/agency/dod/dsb/autonomy.pdf](https://fas.org/irp/agency/dod/dsb/autonomy.pdf)(text).

“Defining Critical Thinking.” The Foundation for Critical Thinking. [https://www.criticalthinking.org/pages/defining-critical-thinking/766](https://www.criticalthinking.org/pages/defining-critical-thinking/766).

Demchak, Chris C. “China: Determined to Dominate Cyberspace and AI,” *Bulletin of the Atomic Scientists* 75, no. 3 (2019): 99–104. DOI:10.1080/00 963402.2019.1604857.

———. “Four Horsemen of AI Conflict: Scale, Speed, Foreknowledge, and Strategic Coherence.” In Nicholas D. Wright, ed., *AI, China, Russia, and the Global Order*. Maxwell Air Force Base, AL: Air University Press, 2019.

———. “Three Futures for a Post-Western Cybered World.” *Military Cyber Affairs* 3, no. 1 (Summer 2018): 115–31. [http://scholarcommons.usf.edu/mca/vol3/iss1/6](http://scholarcommons.usf.edu/mca/vol3/iss1/6).

Demchak, Chris C., and Yuval Shavitt. “China’s Maxim—Leave No Access Point Unexploited: The Hidden Story of China’s Telecom’s BGP Hijacking.” *Military Cyber Affairs* 3, no. 1 (Summer 2018). [https://scholarcommons.usf.edu/cgi/viewcontent.cgi?article=1050&context=mca](https://scholarcommons.usf.edu/cgi/viewcontent.cgi?article=1050&context=mca).

Department of the Navy. “Highlights of the Department of the Navy FY2020 Budget,” March 12, 2019. [https://www.secnav.navy.mil/fmc/fmb/Documents/20pres/Highlights\_book.pdf](https://www.secnav.navy.mil/fmc/fmb/Documents/20pres/Highlights_book.pdf).

Detar, Paul J. *Scheduling Marine Corps Entry-Level MOS Schools*. Master’s thesis, Naval Postgraduate School, September 2004. [https://calhoun.nps.edu/handle/10945/1444](https://calhoun.nps.edu/handle/10945/1444).

“Developing Inference Algorithms.” Edward Library. [http://edwardlib.org/api/inference-development](http://edwardlib.org/api/inference-development).

“Distributed Maritime Operations.” *USNI News*. [https://news.usni.org/tag/distributed-maritime-operations](https://news.usni.org/tag/distributed-maritime-operations).

Doctorow, Cory. “Saying Information Wants to Be Free Does More Harm than Good.” *The Guardian*, March 18, 2010. [https://www.theguardian.com/technology/2010/may/18/information-wants-to-be-free](https://www.theguardian.com/technology/2010/may/18/information-wants-to-be-free).

Dombrowski, Peter, and Eugene Gholz. “Identifying Disruptive Innovation: Innovation Theory and the Defense Industry.” *Innovations: Technology, Governance, Globalization* 4, no. 2 (Spring 2009): 101–17. [https://www.mitpressjournals.org/doi/abs/10.1162/itgg.2009.4.2.101](https://www.mitpressjournals.org/doi/abs/10.1162/itgg.2009.4.2.101).

Dreyfus, Hubert, and Sean Dorrance Kelly. *All Things Shining: Reading the Western Classics to Find Meaning in a Secular Age*. Tampa, FL: Free Press, 2011.

Dujmovic, Jurica. “Opinion: Drone Warship Sea Hunter of the U.S. Navy Is Powered by Artificial Intelligence.” *MarketWatch*, July 3, 2019. [https://www.marketwatch.com/story/drone-warship-sea-hunter-of-the-us-navy-is-powered-by-artificial-intelligence-2019-07-03](https://www.marketwatch.com/story/drone-warship-sea-hunter-of-the-us-navy-is-powered-by-artificial-intelligence-2019-07-03).

Dunford, Joseph, Jr. “Remarks and Q&A at the Center for Strategic and International Studies.” March 29, 2016. [https://www.jcs.mil/Media/Speeches/Article/707418/gen-dunfords-remarks-and-qa-at-the-center-for-strate](https://www.jcs.mil/Media/Speeches/Article/707418/gen-dunfords-remarks-and-qa-at-the-center-for-strate) gic-and-international-studi/.

Dyck, Jeff, et al. “Learning from Games: HCI Design Innovations in Entertainment Software.” *Proceedings of the 2003 Conference on Graphics Interface* 2003, 237–46.

Eady, Trent. “Tesla’s Advantage in Behavior Prediction for Autonomous Driving.” *Seeking Alpha*, August 11, 2019. [https://seekingalpha.com/article/4284671-teslas-advantage-in-behaviour-prediction-for-autonomous-driving](https://seekingalpha.com/article/4284671-teslas-advantage-in-behaviour-prediction-for-autonomous-driving).

Eckstein, Megan. “Sea Hunter Unmanned Ship Continues Autonomy Testing as NAVSEA Moves Forward with Draft RFP.” *USNI News*, April 29, 2019. [https://news.usni.org/2019/04/29/sea-hunter-unmanned-ship-continues-autonomy-testing-as-navsea-moves-forward-with-draft-rfp](https://news.usni.org/2019/04/29/sea-hunter-unmanned-ship-continues-autonomy-testing-as-navsea-moves-forward-with-draft-rfp).

Edmonds, Bill R. “After Moral Injury: Backing in a Side Door into Consciousness.” *War on the Rocks*, May 27, 2019. [https://warontherocks.com/2019/05/after-moral-injury-backing-through-a-side-door-into-consciousness/](https://warontherocks.com/2019/05/after-moral-injury-backing-through-a-side-door-into-consciousness/).

Elmer, Keegan. “Man Behind China’s New Aircraft Carrier Detained in Corruption Investigation.” *South China Morning Post*, June 17, 2018. [https://www.scmp.com/news/china/policies-politics/article/2151173/man-behind-chinas-new-aircraft-carrier-detained](https://www.scmp.com/news/china/policies-politics/article/2151173/man-behind-chinas-new-aircraft-carrier-detained).

Englehorn, Lyla. *CRUSER: Distributed Maritime Operations (DMO) Warfare Innovation Continuum (WIC) Workshop After Action Report*. Monterey, CA: Naval Postgraduate School, December 2017. [https://nps.edu/documents/105302057/109378023/SEP2017+WIC+Workshop+DMO+Final+Report/9c71305a-b467-4b70-9ac5-438fc6dd4a93](https://nps.edu/documents/105302057/109378023/SEP2017+WIC+Workshop+DMO+Final+Report/9c71305a-b467-4b70-9ac5-438fc6dd4a93).

Erickson, Jon. *Hacking: The Art of Exploitation*, 2nd ed. San Francisco: No Starch Press, 2008.

Euhus, Brandon T. “A Clausewitzian Response to ‘Hyperwarfare’.” *Parameters* 48, no. 3 (Autumn 2018): 65–76.

Everstine, Brian. “USAF to Give RPA Crews Prominent Awards.” *Air Force Magazine*, September 24, 2018. [http://www.airforcemag.com/Features/Pages/2018/September%202018/Prominent-Awards-Coming-Soon-for-RPA-Crews.aspx](http://www.airforcemag.com/Features/Pages/2018/September%202018/Prominent-Awards-Coming-Soon-for-RPA-Crews.aspx).

Executive Office of the President. Executive Order 13859, “Maintaining American Leadership in Artificial Intelligence,” February 11, 2019. [https://www.federalregister.gov/documents/2019/02/14/2019-02544/maintaining-american-leadership-in-artificial-intelligence](https://www.federalregister.gov/documents/2019/02/14/2019-02544/maintaining-american-leadership-in-artificial-intelligence).

Farragut, Loyall. *The Life of David Glasgow Farragut, First Admiral of the United States Navy: Embodying His Journal and Letters*. New York: D. Appleton and Company, 1879.

Farrell, Theo, Frans Osinga, and James A. Russell, eds. *Military Adaptation in Afghanistan*. Stanford, CA: Stanford University Press, 2013.

Federal Communications Commission. Technological Advisory Council, 5G IoT Working Group, *5G Edge Computing Whitepaper*. Washington, DC: Federal Communications Commission, 2018.

Fischbach, Steven J. *Linear Optimization of Frequency Spectrum Assignments Across Systems*. Master’s thesis, Naval Postgraduate School, March 2016. [https://calhoun.nps.edu/handle/10945/48520](https://calhoun.nps.edu/handle/10945/48520).

FitzGerald, Mary C. *Marshal Ogarkov on Modern War: 1977–1985*, revised ed. Alexandria, VA: Center for Naval Analyses, November 1986. [https://apps.dtic.mil/dtic/tr/fulltext/u2/a176138.pdf](https://apps.dtic.mil/dtic/tr/fulltext/u2/a176138.pdf).

FitzSimonds, James R., and Jan M. van Tol. “Revolutions in Military Affairs.” *Joint Force Quarterly*, Spring 1994. [https://apps.dtic.mil/dtic/tr/fulltext/u2/a360252.pdf](https://apps.dtic.mil/dtic/tr/fulltext/u2/a360252.pdf).

Fletcher, Barbara. “UUV Master Plan: A Vision for Navy UUV Development.” Space and Naval Warfare Systems Center D744, 2000. [https://apps.dtic.mil/dtic/tr/fulltext/u2/a397124.pdf](https://apps.dtic.mil/dtic/tr/fulltext/u2/a397124.pdf).

“Flight of the Drones: Why the Future of Air Power Belongs to Unmanned Systems.” *The Economist*, October 8, 2011. [https://www.economist.com/briefing/2011/10/08/flight-of-the-drones](https://www.economist.com/briefing/2011/10/08/flight-of-the-drones).

Fogel, D. B. *Evolutionary Computation: Toward a New Philosophy of Machine Intelligence*. Los Alamitos, CA: IEEE Press, 1995.

Foster, Kendrick. “The Modern Pen and the AI Sword.” *Harvard Political Review*, May 13, 2019. [https://harvardpolitics.com/united-states/pen-ai-sword/](https://harvardpolitics.com/united-states/pen-ai-sword/).

Frankish, Keith, and William M. Ramsey. *The Cambridge Handbook of Artificial Intelligence*. Cambridge: Cambridge University Press, 2014.

Freedburg, Sydney J. “How AI Could Change the Art of War.” *Breaking Defense*, April 25, 2019. [https://breakingdefense.com/2019/04/how-ai-could-change-the-art-of-war/](https://breakingdefense.com/2019/04/how-ai-could-change-the-art-of-war/).

———. “Hypersonics: Army Awards $699M to Build First Missiles for a Combat Unit.” *Breaking Defense*, August 30, 2019. [https://breakingdefense.com/2019/08/hypersonics-army-awards-699m-to-build-first-missiles-for-a-combat-unit/](https://breakingdefense.com/2019/08/hypersonics-army-awards-699m-to-build-first-missiles-for-a-combat-unit/).

———.“Joint Artificial Intelligence Center Created Under DoD CIO.” *Breaking Defense*, June 29, 2018. [https://breakingdefense.com/2018/06/joint-artificial-intelligence-center-created-under-dod-cio/](https://breakingdefense.com/2018/06/joint-artificial-intelligence-center-created-under-dod-cio/).

———. “Robot Wolfpacks: The Faster, Cheaper 355-Ship Fleet.” *Breaking Defense*, January 22, 2019. [https://breakingdefense.com/2019/01/robot-wolfpacks-the-faster-cheaper-355-ship-fleet/](https://breakingdefense.com/2019/01/robot-wolfpacks-the-faster-cheaper-355-ship-fleet/).

Freedberg, Sydney J., and Theresa Hitchens. “NDAA: HASC Doubles Joint AI Funding, Streamlines Software Buys.” *Breaking Defense*, June 11, 2019. [https://breakingdefense.com/2019/06/ndaa-hasc-doubles-joint-ai-funding-stream](https://breakingdefense.com/2019/06/ndaa-hasc-doubles-joint-ai-funding-stream) lines-software-buys/.

Freedman, Lawrence. *Strategy: A History*. Oxford: Oxford University Press, 2013.

Friedel, Frederic. “Kasparov on the Future of Artificial Intelligence.” *Chess News*, December 29, 2016. [https://en.chessbase.com/post/kasparov-on-the-future-of-artificial-intelligence](https://en.chessbase.com/post/kasparov-on-the-future-of-artificial-intelligence).

Friedman, B. A. *On Tactics: A Theory of Victory in Battle*. Annapolis, MD: Naval Institute Press, 2017.

Friedman, Norman. “Netting and Navies, Achieving a Balance.” In Andrew Forbes, ed., *Sea Power: Challenges Old and New*. Sydney: Halstead Press, 2007.

———. *Network-Centric Warfare*. Annapolis, MD: Naval Institute Press, 2009.

———. *Terrorism, Afghanistan, and America’s New Way of War*. Annapolis, MD: Naval Institute Press, 2003.

Friedman, Tom. “A. I. Still Needs H. I. (Human Intelligence).” *New York Times*, February 27, 2019. [https://www.nytimes.com/2019/02/26/opinion/artificial-intelligence.html](https://www.nytimes.com/2019/02/26/opinion/artificial-intelligence.html).

Friehe, Torben. “How Much Autonomy Is Too Much Autonomy for AI?” *TNW*, November 18, 2017. [https://thenextweb.com/contributors/2017/11/18/much-autonomy-much-ai/](https://thenextweb.com/contributors/2017/11/18/much-autonomy-much-ai/).

Fryer-Biggs, Zachary. “Coming Soon to a Battlefield: Robots That Can Kill,” *The Atlantic*, September 3, 2019. [https://www.theatlantic.com/technology/archive/2019/09/killer-robots-and-new-era-machine-driven-warfare/597130/](https://www.theatlantic.com/technology/archive/2019/09/killer-robots-and-new-era-machine-driven-warfare/597130/).

Future of Life Institute. “National and International AI Strategies.” [https://futureoflife.org/national-international-ai-strategies/](https://futureoflife.org/national-international-ai-strategies/).

Gains, Mosheh, Courtney Kube, and Adam Edelman. “U.S. Marines Jam an Iranian Drone in Gulf, Destroying It.” *NBC News*, July 19, 2019. [https://www.nbcnews.com/politics/national-security/trump-says-u-s-navy-ship-shot-down-iranian-drone-n1031451](https://www.nbcnews.com/politics/national-security/trump-says-u-s-navy-ship-shot-down-iranian-drone-n1031451).

Galdorisi, George. “Designing Autonomous Systems for Warfighters.” *Small Wars Journal*, August 2016. [https://smallwarsjournal.com/index.php/jrnl/art/designing-autonomous-systems-for-warfighters-keeping-humans-in-the-loop](https://smallwarsjournal.com/index.php/jrnl/art/designing-autonomous-systems-for-warfighters-keeping-humans-in-the-loop).

———. “The Navy Needs AI, It’s Just Not Certain Why.” U.S. Naval Institute *Proceedings* 145, no. 5 (May 2019): 28–32. [https://www.usni.org/magazines/proceedings/2019/may/navy-needs-ai-its-just-not-certain-why](https://www.usni.org/magazines/proceedings/2019/may/navy-needs-ai-its-just-not-certain-why).

———. “Producing Unmanned Systems Even Lawyers Can Love.” U.S. Naval Institute *Proceedings* 144, no. 6 (June 2018): 38–43.

Galdorisi, George, and Rachel Volner. “Keeping Humans in the Loop.” U.S. Naval Institute *Proceedings* 141, no. 2 (February 2015): 36–41. [https://www.usni.org/magazines/proceedings/2015/february/keeping-humans-loop](https://www.usni.org/magazines/proceedings/2015/february/keeping-humans-loop).

Gallistel, C. R., and A. P. King. *Memory and the Computational Brain: Why Cognitive Science Will Transform Neuroscience*. Oxford: Wiley-Blackwell, 2009.

Gama, João, et al. “A Survey on Concept Drift Adaptation.” *ACM Computing Surveys (CSUR*) 46, no. 4 (2014).

Garamone, Jim. “U. S. Military Must Develop All-Domain Defenses, Mattis, Dunford Say.” U.S. Department of Defense, April 13, 2018. [https://www.defense.gov/Newsroom/News/Article/Article/1493209/us-military-must-develop-all-domain-defenses-mattis-dunford-say/](https://www.defense.gov/Newsroom/News/Article/Article/1493209/us-military-must-develop-all-domain-defenses-mattis-dunford-say/).

Gelb, Arthur, ed. *Applied Optimal Estimation*. Boston: MIT Press, 1974.

Gertler, Jeremiah. *History of the Navy UCLASS Program Requirements: In Brief*. Washington, DC: Congressional Research Service, August 3, 2015. [https://fas.org/sgp/crs/weapons/R44131.pdf](https://fas.org/sgp/crs/weapons/R44131.pdf).

Giacomo, Carol. “Are You Ready for Weapons That Call Their Own Shots?” *New York Times*, July 5, 2019. [https://www.nytimes.com/2019/06/26/opinion/weapons-artificial-intelligence.html?searchResultPosition=1](https://www.nytimes.com/2019/06/26/opinion/weapons-artificial-intelligence.html?searchResultPosition=1).

Gibney, Elizabeth. “Self-Taught AI Is Best Yet at Strategy Game Go.” *Nature*, October 18, 2017. [https://www.nature.com/news/self-taught-ai-is-best-yet-at-strategy-game-go-1.22858](https://www.nature.com/news/self-taught-ai-is-best-yet-at-strategy-game-go-1.22858).

Gingrich, Dana. “Artificial Intelligence in Warfare.” *InterAgency Journal* 10, no. 3 (2019): 33–39. [http://thesimonscenter.org/wp-content/uploads/2019/08/IAJ-10-3-2019-pg33-39.pdf](http://thesimonscenter.org/wp-content/uploads/2019/08/IAJ-10-3-2019-pg33-39.pdf).

Gladwell, Malcolm. *Blink*. New York: Little, Brown and Company, 2005.

Glaser, April. “How Apple and Amazon Are Aiding Chinese Censors.” *Slate*, August 2, 2017. [https://slate.com/technology/2017/08/apple-and-amazon-are-helping-china-censor-the-internet.html](https://slate.com/technology/2017/08/apple-and-amazon-are-helping-china-censor-the-internet.html).

———. “Is a Tech Company Ever Neutral?” *Slate*, October 11, 2019. [https://slate.com/technology/2019/10/apple-chinese-government-microsoft-amazon-ice.html](https://slate.com/technology/2019/10/apple-chinese-government-microsoft-amazon-ice.html).

Good, I. J. “Speculations Concerning the First Ultraintelligent Machine.” In Franz L. Alt and Morris Rubinoff, eds. *Advances in Computers*, vol. 6. New York: Academic Press, 1965, 31–88. doi:10.1016/S0065-2458(08)60418-0.

Goodfellow, Ian J., Jonathon Shlens, and Christian Szegedy. “Explaining and Harnessing Adversarial Examples.” Cornell University Web archive, March 20, 2015. [https://arxiv.org/abs/1412.6572](https://arxiv.org/abs/1412.6572).

Gould, Joe. “How the Pentagon’s Fear of Risk Is Stifling Innovation.” *Defense News*, January 28, 2019. [https://www.defensenews.com/congress/2019/01/28/is-the-pentagons-fear-of-risk-stifling-innovation/](https://www.defensenews.com/congress/2019/01/28/is-the-pentagons-fear-of-risk-stifling-innovation/)

Governale, Carl. “Brain-Computer Interfaces Are Game-Changers.” U.S. Naval Institute *Proceedings* 143, no. 8 (August 2017): 64–69.

Goyal, Yash, et al. “Towards Transparent AI Systems: Interpreting Visual Question Answering Models.” Unpublished paper, Cornell University, September 9, 2016. arXiv:1608.08974v2 \[cs.CV\].

Grattan, Robert F. “Management Research During World War Two.” *Oxford Bibliographies*, January 28, 2013. [https://www.oxfordbibliographies.com/view/document/obo-9780199846740/obo-9780199846740-0021.xml](https://www.oxfordbibliographies.com/view/document/obo-9780199846740/obo-9780199846740-0021.xml).

Gray, Colin S. *Defining and Achieving Decisive Victory*. Carlisle, PA: U.S. Army War College Strategic Studies Institute, April 1, 2002. [https://ssi.armywarcollege.edu/pubs/display.cfm?pubID=272](https://ssi.armywarcollege.edu/pubs/display.cfm?pubID=272).;. *Nuclear Strategy and National Style*. Lanham, MD: Hamilton Books/ABT Press, 1986.

———. *Strategy for Chaos: Revolutions in Military Affairs and the Evidence of History*. London: Frank Cass, 2002.

Grissom, Adam. “The Future of Military Innovation Studies.” *Journal of Strategic Studies* 29, no. 5 (2006): 905–34. [https://doi.org/10.1080/01402390600901067](https://doi.org/10.1080/01402390600901067).

Gunzinger, Mark, et al. *An Air Force for an Era of Great Power Competition*. Washington, DC: Center for Strategic and Budgetary Assessments, 2019. [https://csbaonline.org/research/publications/an-air-force-for-an-era-of-great-power-competition](https://csbaonline.org/research/publications/an-air-force-for-an-era-of-great-power-competition).

Guszcza, James, and Nikhil Maddirala. “Minds and Machines: The Art of Forecasting in the Age of Artificial Intelligence.” *Deloitte Review*, no. 19 (2016). [https://www2.deloitte.com/us/en/insights/deloitte-review/issue-19/art-of-forecasting-human-in-the-loop-machine-learning.html](https://www2.deloitte.com/us/en/insights/deloitte-review/issue-19/art-of-forecasting-human-in-the-loop-machine-learning.html).

Hagel, Chuck. Remarks at Ronald Reagan Presidential Library, Simi Valley, CA, November 15, 2014. [https://dod.defense.gov/News/Speeches/Speech-View/Article/606635/](https://dod.defense.gov/News/Speeches/Speech-View/Article/606635/).

Haigh, Karen Zita. “AI Technologies for Tactical Edge Networks.” Paper presented at the ACM SIGMOBILE MobiHoc 2011, Paris, May 2011. [https://www.cs.cmu.edu/~khaigh/papers/Haigh-MobiHoc2011.pdf](https://www.cs.cmu.edu/~khaigh/papers/Haigh-MobiHoc2011.pdf).

Hammond, Grant T. *The Mind of War: John Boyd and American Security*. Washington, DC: Smithsonian Institution, 2001.

Hamner, Robert, and Gene L. Coon. “A Taste of Armageddon.” Adapted in short story form by James Blish in *Star Trek 2*. New York: Bantam Books, 1968: 13–25.

Hartman, Travis A. *Rapid Airlift Planning for Amphibious-Ready Groups*. Master’s thesis, Naval Postgraduate School, September 2015. [https://calhoun.nps.edu/handle/10945/47272](https://calhoun.nps.edu/handle/10945/47272).

Hasik, James. “Beyond the Third Offset: Matching Plans for Innovation to a Theory of Victory.” *Joint Force Quarterly* 91 (4th Quarter 2018): 14–21.

Hathaway, Melissa. *Cyber Readiness Index 1.0*. Great Falls, VA: Hathaway Global Strategies LLC, 2013.

Hawking, Stephen, et al. “Transcendence Looks at the Implications of Artificial Intelligence—But Are We Taking AI Seriously Enough?” *Independent*, May 1, 2014. [https://www.independent.co.uk/news/science/stephen-hawking-transcendence-looks-at-the-implications-of-artificial-intelligence-but-are-we-taking-9313474.html](https://www.independent.co.uk/news/science/stephen-hawking-transcendence-looks-at-the-implications-of-artificial-intelligence-but-are-we-taking-9313474.html).

Haykin, Simon O. *Neural Networks and Kalman Filtering*. Hoboken, NJ: Wiley and Sons, 2001.

Heath, Garrett. “Better Wargaming Is Helping the U.S. Military Navigate a Turbulent Era.” *Defense One*, August 19, 2018. [https://www.defenseone.com/ideas/2018/08/better-wargaming-helping-us-military-navigate-tur](https://www.defenseone.com/ideas/2018/08/better-wargaming-helping-us-military-navigate-tur) bulent-era/150653/.

Hecht-Nielsen, Robert. *Neurocomputing*. Englewood Cliffs, NJ: Prentice Hall, 1990.

Heller, Christian H. “Near Term Applications of Artificial Intelligence: Implementation Opportunities from Modern Business Practices.” *Naval War College Review* 72, no. 4 (Autumn 2019): 73–100. [https://digital-com](https://digital-com) [mons.usnwc.edu/nwc-review/vol72/iss4/7](http://mons.usnwc.edu/nwc-review/vol72/iss4/7).

Hendrix, Jerry. *Retreat from Range: The Rise and Fall of Carrier Aviation*. Washington, DC: Center for a New American Security, October 2015. [https://www.cnas.org/publications/reports/retreat-from-range-the-rise-and-fall-of-carrier-aviation](https://www.cnas.org/publications/reports/retreat-from-range-the-rise-and-fall-of-carrier-aviation).

Hersey, Frank. “China to Have 626 Surveillance Cameras within 3 Years.” Technode, November 22, 2017. [https://technode.com/2017/11/22/china-to-have-626-million-surveillance-cameras-within-3-years/](https://technode.com/2017/11/22/china-to-have-626-million-surveillance-cameras-within-3-years/).

Heuer, Richards J. *Psychology of Intelligence Analysis*. Washington, DC: Center for the Study of Intelligence, Central Intelligence Agency, 1999.

Hilbert, D., and W. Ackermann. *Grundzugen der Theoretischen Logik \[Principles of Theoretical Logic*\]. Berlin: Springer, 1928.

Hitchens, Theresa. “DARPA’s Mosaic Warfare—Multi Domain Ops, But Faster.” *Breaking Defense*, September 10, 2019. [https://breakingdefense.com/2019/09/darpas-mosaic-warfare-multi-domain-ops-but-faster/](https://breakingdefense.com/2019/09/darpas-mosaic-warfare-multi-domain-ops-but-faster/).

———. “‘GEOINT Singularity:’ There’ll Be Nowhere for DoD to Hide.” *Breaking Defense*, August 8, 2019. [https://breakingdefense.com/2019/08/geoint-singularity-therell-be-nowhere-for-dod-to-hide-exclusive/](https://breakingdefense.com/2019/08/geoint-singularity-therell-be-nowhere-for-dod-to-hide-exclusive/).

Hoadley, Daniel S., and Nathan J. Lucas. *Artificial Intelligence and National Security*, R45178. Washington, DC: Congressional Research Service, April 26, 2018, updated January 30, 2019. [https://www.hsdl.org/?view&did](https://www.hsdl.org/?view&did) =821457.

Hoc, Jean-Michel. “From Human-Machine Interaction to Human-Machine Cooperation.” *Ergonomics* 43, no. 7 (2000): 833–43.

Hoffman, F. G. “Will War’s Nature Change in the Seventh Military Revolution.” *Parameters* 47, no. 4 (Winter 2017/18): 19–31.

Hofstadter, Douglas, ed. *Fluid Concepts and Creative Analogies: Computer Models of the Fundamental Mechanisms of Thought*. New York: Basic Books, 1995.

———. *Godel, Escher, Bach: An Eternal Golden Braid*. New York: Basic Books, 1979.

———. “The Shallowness of Google Translate.” *The Atlantic*, January 30, 2018. [https://www.theatlantic.com/technology/archive/2018/01/the-shallowness-of-google-translate/551570/](https://www.theatlantic.com/technology/archive/2018/01/the-shallowness-of-google-translate/551570/).

Hordri, N. F., et al. “A Systematic Literature Review on Features of Deep Learning in Big Data Analytics.” *International Journal of Advances in Soft Computing and Applications* 9, no. 1 (March 2017): 32–49.

Hornfischer, James D. *Neptune’s Inferno: The U.S. Navy at Guadalcanal*. New York: Random House Publishing Group, 2011.

Horowitz, Michael C. “The Algorithms of August.” *Foreign Policy*, September 12, 2018. [https://foreignpolicy.com/2018/09/12/will-the-united-states-lose-the-artificial-intelligence-arms-race/](https://foreignpolicy.com/2018/09/12/will-the-united-states-lose-the-artificial-intelligence-arms-race/).

———. “Artificial Intelligence, International Competition and the Balance of Power.” *Texas National Security Review* 1, no. 3 (May 2018). [https://tnsr.org/2018/05/artificial-intelligence-international-competition-and-the-balance-of-power/](https://tnsr.org/2018/05/artificial-intelligence-international-competition-and-the-balance-of-power/).

Horowitz, Michael C., and Casey Mahoney. “Artificial Intelligence and the Military: Technology Is Only Half the Battle.” *War on the Rocks*, December 25, 2018. [https://warontherocks.com/2018/12/artificial-intelligence-and-the-military-technology-is-only-half-the-battle/](https://warontherocks.com/2018/12/artificial-intelligence-and-the-military-technology-is-only-half-the-battle/).

Hosanagar, Kartik, and Apoorv Saxena. “The First Wave of Corporate AI Is Doomed to Fail.” *Harvard Business Review*, April 18, 2017. [https://hbr.org/2017/04/the-first-wave-of-corporate-ai-is-doomed-to-fail](https://hbr.org/2017/04/the-first-wave-of-corporate-ai-is-doomed-to-fail).

Houser, Kristin. “DARPA Is Funding Research into AI that Can Explain What It’s Thinking.” *Futurism*, July 24, 2018. [https://futurism.com/the-byte/third-wave-ai-darpa](https://futurism.com/the-byte/third-wave-ai-darpa).

———. “It’s Really Easy for Hackers to Take Control of Robots.” *Futurism*, August 24, 2018. [https://futurism.com/the-byte/hacking-robots-easy](https://futurism.com/the-byte/hacking-robots-easy).

Hudson, Matthew. “The Pursuit of Creativity Can Make Algorithms Much Smarter.” *Wired*, November 18, 2019. [https://www.wired.com/story/the-pursuit-of-creativity-can-make-algorithms-much-smarter/](https://www.wired.com/story/the-pursuit-of-creativity-can-make-algorithms-much-smarter/).

Hughes, Wayne P., Jr. and Robert P. Girrier. *Fleet Tactics and Naval Operations*, 3rd ed. Annapolis, MD: Naval Institute Press, 2018.

Human Rights Watch. “Killer Robots.” [https://www.hrw.org/topic/armas/killer-robots#](https://www.hrw.org/topic/armas/killer-robots#).

Hurd, Graeme P. “Executive Summary: Understanding Russian Strategic Behavior, Russia Strategic Initiative Workshop 3.” George C. Marshall European Center for Security Studies, March 18–19, 2019. [https://www.marshallcenter.org/mcpublicweb/mcdocs/perspectives\_10\_-\_herd-\_rsi\_workshop\_3\_-\_mar\_2018.pdf](https://www.marshallcenter.org/mcpublicweb/mcdocs/perspectives_10_-_herd-_rsi_workshop_3_-_mar_2018.pdf).

“An Interactive Look at the U.S.-China Military Scorecard.” RAND Corporation. [https://www.rand.org/paf/projects/us-china-scorecard.html](https://www.rand.org/paf/projects/us-china-scorecard.html).

“An Interview with Robert O. Work.” *Joint Force Quarterly* 84 (1st Quarter 2017): 8–10.

Jackson, John, ed. *One Nation Under Drones*. Annapolis, MD: Naval Institute Press, 2018.

Jacobs, Roger S. *Optimization of Daily Flight Training Schedules*. Master’s thesis, Naval Postgraduate School, March 2014. [https://calhoun.nps.edu/handle/10945/41396](https://calhoun.nps.edu/handle/10945/41396).

Jeffrey, Cal. “Founder of Project Maven ‘Alarmed’ at Google’s Decision to Walk Away.” *Techspot*, June 26, 2018. [https://www.techspot.com/community/topics/founder-of-project-maven-alarmed-at-googles-decision-to-walk-away.247466/](https://www.techspot.com/community/topics/founder-of-project-maven-alarmed-at-googles-decision-to-walk-away.247466/).

Jennings, Gareth. “Air Force Unveils Loyal Wingman Concept.” *Jane’s Defence Weekly*, March 27, 2019. [https://www.janes.com/article/87512/usaf-reveals-skyborg-loyal-wingman-concept](https://www.janes.com/article/87512/usaf-reveals-skyborg-loyal-wingman-concept).

Jennings, Louis J., ed. *The Correspondence and Diaries of the Late Right Honourable John Wilson Croker, Secretary to the Admiralty from 1809 to 1830*. London: John Murray, 1885.

Johnson, Dave. *Russia Conventional Precision Strike Capabilities, Regional Crises, and Nuclear Thresholds*. Livermore Papers on Global Security No. 3. Lawrence Livermore National Laboratory Center for Global Security Research, February 2018. [https://cgsr.llnl.gov/content/assets/docs/Precision-Strike-Capabilities-report-v3-7.pdf](https://cgsr.llnl.gov/content/assets/docs/Precision-Strike-Capabilities-report-v3-7.pdf).

Joint Chiefs of Staff. *DoD Dictionary of Military and Associated Terms*. Washington, DC: Department of Defense, February 2019. [https://www.jcs.mil/Portals/36/Documents/Doctrine/pubs/dictionary.pdf](https://www.jcs.mil/Portals/36/Documents/Doctrine/pubs/dictionary.pdf).

———. Joint Publication 3-32, *Joint Maritime Operations*. Washington, DC: Department of Defense, June 8, 2018. [https://www.jcs.mil/Portals/36/Documents/Doctrine/pubs/jp3\_32.pdf?ver=2019-03-14-144800-240](https://www.jcs.mil/Portals/36/Documents/Doctrine/pubs/jp3_32.pdf?ver=2019-03-14-144800-240).

———. Joint Publication 3-0, *Joint Operations*. Washington, DC: Department of Defense, October 22, 2018. [https://www.jcs.mil/Portals/36/Documents/Doctrine/pubs/jp3\_0ch1.pdf?ver=2018-11-27-160457-910](https://www.jcs.mil/Portals/36/Documents/Doctrine/pubs/jp3_0ch1.pdf?ver=2018-11-27-160457-910).

———. Joint Publication 3-09, *Joint Fire Support*. Washington, DC: Department of Defense, 2019.

Kagan, Frederick W. “The U.S. Military’s Manpower Crisis.” *Foreign Affairs* 85, no. 4 (July–August 2006): 97–110.

Kahan, Dan M., et al. *Motivated Numeracy and Enlightened Self-Government*. Yale Law School, Public Law Working Paper No. 307, June 5, 2017. [https://papers.ssrn.com/sol3/papers.cfm?abstract\_id=2319992](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=2319992).

Kahneman, Daniel. *Thinking, Fast and Slow*. New York: Farrar, Straus and Giroux, 2011.

Kania, Elsa B. “The AI Titan’s Security Dilemmas.” *Governance in an Emerging World*, Hoover Institution, issue 218, October 29, 2018. [https://www.hoover.org/research/ai-titans](https://www.hoover.org/research/ai-titans).

———. *Battlefield Singularity: Artificial Intelligence, Military Revolution, and China’s Future Military Power*. Washington, DC: Center for a New American Security, November 2017. [https://s3.amazonaws.com/files.cnas.org/documents/Battlefield-Singularity-November-2017.pdf?mtime=20171129235805](https://s3.amazonaws.com/files.cnas.org/documents/Battlefield-Singularity-November-2017.pdf?mtime=20171129235805).

Karlik, Evan. “U. S.-China Tensions: Unmanned Military Craft Raise the Risk of War.” *The Maritime Executive*, August 12, 2019. [https://www.maritime-executive.com/editorials/us-china-tensions-unmanned-military-craft-raise-risk-of-war](https://www.maritime-executive.com/editorials/us-china-tensions-unmanned-military-craft-raise-risk-of-war).

Kessler, Aaron. “Riding Down the Highway, with Tesla’s Code at the Wheel.” *New York Times*, October 15, 2015. [https://www.nytimes.com/2015/10/16/automobiles/tesla-adds-high-speed-autonomous-driving-to-its-bag-of-tricks.html](https://www.nytimes.com/2015/10/16/automobiles/tesla-adds-high-speed-autonomous-driving-to-its-bag-of-tricks.html).

Kiddoo, Jean L., et al. “Operations Research Enables Auction to Repurpose Television Spectrum for Next-Generation Wireless Technologies.” *INFORMS Journal on Applied Analytics* 49, no. 1 (January/February 2019): 7–22. [https://doi.org/10.1287/inte.2018.0972](https://doi.org/10.1287/inte.2018.0972).

Kirby, Jen. “See Trump’s Statement on Syria Strike: ‘They Are Crimes of a Monster.’” *Vox*, April 13, 2018. [https://www.vox.com/2018/4/13/17236862/syria-strike-donald-trump-chemical-attack-statement](https://www.vox.com/2018/4/13/17236862/syria-strike-donald-trump-chemical-attack-statement).

Klare, Michael T. “AI Arms Race Gains Speed.” *Arms Control Today*, March 2019. [https://www.armscontrol.org/act/2019-03/news/ai-arms-race-gains-speed](https://www.armscontrol.org/act/2019-03/news/ai-arms-race-gains-speed).

Klein, Hans K., and Daniel Lee Kleinman. “The Social Construction of Technology: Structural Considerations.” *Science, Technology and Human Values* 27, no. 1 (2002): 28–52.

Knight, Will. “China May Overtake the U.S. with Best AI Research in Just Two Years.” *MIT Technology Review*, March 13, 2019. [https://www.technologyreview.com/s/613117/china-may-overtake-the-us-with-the-best-ai-research-in-just-two-years/](https://www.technologyreview.com/s/613117/china-may-overtake-the-us-with-the-best-ai-research-in-just-two-years/).

———. “The Dark Secret at the Heart of AI.” *MIT Technology Review* 120, no. 3 (May/June 2017): 54–61. [https://www.technologyreview.com/s/604087/the-dark-secret-at-the-heart-of-ai/](https://www.technologyreview.com/s/604087/the-dark-secret-at-the-heart-of-ai/).

Kollars, Nina. *By the Seat of Their Pants: Military Technological Adaptation in War*. PhD dissertation, Ohio State University, 2012. [http://rave.ohiolink.edu/etdc/view?acc\_num=osu1341314153](http://rave.ohiolink.edu/etdc/view?acc_num=osu1341314153).

———. “Military Innovation’s Dialectic: Gun Trucks and Rapid Acquisition.” *Security Studies* 23, no. 4 (2014): 787–813. [https://www.tandfonline.com/doi/full/10.1080/09636412.2014.965000](https://www.tandfonline.com/doi/full/10.1080/09636412.2014.965000).

———. “Organising Adaptation in War.” *Survival* 57, no. 6 (2015): 111–26. [https://doi.org/10.1080/00396338.2015.1116158](https://doi.org/10.1080/00396338.2015.1116158).

———. “War’s Horizon: Soldier-Led Adaptation in Iraq and Vietnam.” *Journal of Strategic Studies* 38, no. 4 (January 2015): 529–53. doi: 10.1080/01402390.2014.971947.

Kollars, Nina., Richard R. Muller, and Andrew Santora. “Learning to Fight and Fighting to Learn: Practitioners and the Role of Unit Publications in VIII Fighter Command 1943–1944.” *Journal of Strategic Studies* 39, no. 7 (2016): 1044–67.

Konaev, Margarita, and Samuel Bendett. “Russian AI-Enabled Combat: Coming to a City Near You?” *War on the Rocks*, July 31, 2019. [https://warontherocks.com/2019/07/russian-ai-enabled-combat-coming-to-a-city-near-you/](https://warontherocks.com/2019/07/russian-ai-enabled-combat-coming-to-a-city-near-you/).

Krauthammer, Charles. “Be Afraid.” *The Weekly Standard*, May 26, 1997. [https://www.weeklystandard.com/charles-krauthammer/be-afraid-9802](https://www.weeklystandard.com/charles-krauthammer/be-afraid-9802).

Kreisher, Otto. “Navy’s Triton UAV Passes Full-Motion Video To P-8 During Flight Test.” *USNI News*, June 23, 2016. [https://news.usni.org/2016/06/22/triton-uav-passes-full-motion-video-p-8-flight-test](https://news.usni.org/2016/06/22/triton-uav-passes-full-motion-video-p-8-flight-test).

Krepinevich, Andrew F. “Cavalry to Computer: The Pattern of Military Revolutions.” *National Interest* no. 37 (Fall 1994): 30–42.

———. “The Pentagon’s Wasting Assets.” *Foreign Affairs* 88, no. 4 (July/August 2009): 18–33. [https://www.foreignaffairs.com/articles/united-states/2009-07-01/pentagons-wasting-assets](https://www.foreignaffairs.com/articles/united-states/2009-07-01/pentagons-wasting-assets).

Krisher, Tom. “5 Reasons Self-Driving Cars May Be Many Years Away.” *Chicago Tribune*, April 23, 2019. [https://www.chicagotribune.com/business/ct-biz-tesla-self-driving-challenges-20190423-story.html](https://www.chicagotribune.com/business/ct-biz-tesla-self-driving-challenges-20190423-story.html).

Kuang, Cliff. “Can A. I. Be Taught to Explain Itself?” *New York Times*, November 21, 2017. [https://www.nytimes.com/2017/11/21/magazine/can-ai-be-taught-to-explain-itself.html](https://www.nytimes.com/2017/11/21/magazine/can-ai-be-taught-to-explain-itself.html).

Kumar, Shaily. “The Differences between Machine Learning and Predictive Analysis.” *D!gitalist Magazine*, March 15, 2018. [https://www.digitalistmag.com/digital-economy/2018/03/15/differences-between-machine-learning-predictive-analytics-05977121](https://www.digitalistmag.com/digital-economy/2018/03/15/differences-between-machine-learning-predictive-analytics-05977121).

Kunce, Lucas. “Dear Tech Workers, U.S. Service Members Need Your Help.” *New York Times*, August 29, 2019. [https://www.nytimes.com/2019/08/28/opinion/military-war-tech-us.html?searchResultPosition=1](https://www.nytimes.com/2019/08/28/opinion/military-war-tech-us.html?searchResultPosition=1).

La Porte, Todd R. *Organized Social Complexity: Challenge to Politics and Policy*. Princeton, NJ: Princeton University Press, 1975.

LaGrone, Sam. “NAVAIR: Aerial Refueling Will End X-47B Test Program, Salty Dogs Bound for Museums or Boneyard.” *USNI News*, April 14, 2015. [https://news.usni.org/2015/04/14/navair-aerial-refueling-will-end-x-47b-test-program-salty-dogs-bound-for-museums-or-boneyard](https://news.usni.org/2015/04/14/navair-aerial-refueling-will-end-x-47b-test-program-salty-dogs-bound-for-museums-or-boneyard).

———. “Navy Has No Plans to Develop Lethal Carrier UAV Before MQ-25 A Hits Flight Decks.” *USNI News*, May 22, 2019. [https://news.usni.org/2019/05/22/navy-has-no-plans-develop-lethal-carrier-uav-before-mq-25a-hits-flight-decks](https://news.usni.org/2019/05/22/navy-has-no-plans-develop-lethal-carrier-uav-before-mq-25a-hits-flight-decks).

Lambert, Andrew. *Nelson: Britannia’s God of War*. London: Faber and Faber, 2010.

Lanier, Jaron, and Glen Weyl. “AI Is an Ideology, Not a Technology.” *Wired*, March 15, 2020. [https://www.wired.com/story/opinion-ai-is-an-ideology-not-a-technology/](https://www.wired.com/story/opinion-ai-is-an-ideology-not-a-technology/).

Lapowsky, Issie. “How Russian Facebook Ads Divided and Targeted U.S. Voters Before the 2016 Election.” *Wired*, April 16, 2018. [https://www.wired.com/story/russian-facebook-ads-targeted-us-voters-before-2016-election/](https://www.wired.com/story/russian-facebook-ads-targeted-us-voters-before-2016-election/).

Latimer, Jon. *Deception in War*. London: Thistle Publishing, 2016.

Laumer, Sven, and Andreas Eckhardt. “Why Do People Reject Technologies: A Review of User Resistance Theories,” in Yogesh K. Dwivedi, Michael R. Wade, and Scott L. Schneberger, eds. *Information Systems Theory*, vol. 1. New York: Springer, 2012, 63–86.

Lawler, William, and Jonathan Will. “Moving Forward: Evolution of the Maritime Operations Center,” *CIMSEC*, October 19, 2016. [http://cimsec.org/moving-forward-evolution-maritime-operations-center/28849](http://cimsec.org/moving-forward-evolution-maritime-operations-center/28849).

Layton, Peter. *Algorithmic Warfare: Applying Artificial Intelligence to Warfighting*. Canberra: Air Power Development Center, Department of Defence, 2018. [http://airpower.airforce.gov.au/APDC/media/PDF-Files/Contemporary%20AirPower/AP33-Algorithmic-Warfare-Applying-Artificial-Intelligence-to-Warfighting.pdf](http://airpower.airforce.gov.au/APDC/media/PDF-Files/Contemporary%20AirPower/AP33-Algorithmic-Warfare-Applying-Artificial-Intelligence-to-Warfighting.pdf).

Le, Quoc V., et al. “Building High-Level Features Using Large Scale Unsuper-vised Learning.” *Proceedings of the 29th International Conference on Machine Learning*, 2012. [https://arxiv.org/pdf/1112.6209.pdf](https://arxiv.org/pdf/1112.6209.pdf).

Leimeister, Jan Marco, et al. “Leveraging Crowdsourcing: Activation-Supporting Components for IT-Based Ideas Competition.” *Journal of Management Information Systems* 26, no. 1 (Summer 2009): 197–224. [https://www.tandfonline.com/doi/abs/10.2753/MIS0742-1222260108](https://www.tandfonline.com/doi/abs/10.2753/MIS0742-1222260108).

Leone, Dario. “Blue-on-Blue! The Story of the U.S. Navy F/A-18 that Was Shot Down by a U.S. Army PAC-3 Patriot Missile Battery During OIF.” *The Aviation Geek Club*, March 8, 2018. [https://theaviationgeekclub.com/blue-blue-story-u-s-navy-f-18-shot-u-s-army-pac-3-patriot-missile-bat](https://theaviationgeekclub.com/blue-blue-story-u-s-navy-f-18-shot-u-s-army-pac-3-patriot-missile-bat) tery-oif/.

Lewis, Larry, and Diane Vavrichek. *Rethinking the Drone War*. Washington, DC: Center for Naval Analyses, 2016.

Libicki, Martin C. *Cyberspace in Peace and War*. Annapolis, MD: Naval Institute Press, 2016.

Licklider, J. C. R. “Man-Computer Symbiosis.” *IRE Transactions on Human Factors in Electronics*, vol. HFE-1 (March 1960): 4–11. [http://groups.csail.mit.edu/medg/people/psz/Licklider.html](http://groups.csail.mit.edu/medg/people/psz/Licklider.html).

Liedtka, David, and Luke McDowell. “Fully Heterogeneous Collective Regression.” 2018 IEEE 5th International Conference on Data Science and Advanced Analytics, 2018. [https://ieeexplore.ieee.org/document/8631408](https://ieeexplore.ieee.org/document/8631408).

Lindsay, Jon R. “‘War upon the Map’: User Innovation in American Military Software.” *Technology and Culture* 51, no. 3 (2010): 619–51.

Littell, Joe. “Don’t Believe Your Eyes (or Ears): The Weaponization of Artificial Intelligence, Machine Learning and Deepfakes.” *War on the Rocks*, October 7, 2019. [https://warontherocks.com/2019/10/dont-believe-your-eyes-or-ears-the-weaponization-of-artificial-intelligence-machine-learning-and-deepfakes/](https://warontherocks.com/2019/10/dont-believe-your-eyes-or-ears-the-weaponization-of-artificial-intelligence-machine-learning-and-deepfakes/).

Lobbia, R. N., S. C. Stubberud, and M. W. Owen. “Adaptive Extended Kalman Filter Using Artificial Neural Networks.” *The International Journal of Smart Engineering System Design* 1 (1998): 207–21.

Ma, Alexandra. “China Has Started Ranking Citizens with a Creepy ‘Social Credit’ System—Here’s What You Can Do Wrong, and the Embarrassing, Demeaning Ways They Can Punish You.” *Business Insider*, October 29, 2018. [https://www.businessinsider.com/china-social-credit-system-punishments-and-rewards-explained-2018-4](https://www.businessinsider.com/china-social-credit-system-punishments-and-rewards-explained-2018-4).

Macdonald, Julia, and Jacquelyn Schneider. “Battlefield Responses to New Technologies: Views from the Ground on Unmanned Aircraft.” *Security Studies* 28, no. 2 (June/July 2019). [https://doi.org/10.1080/09636412.2019.1551565](https://doi.org/10.1080/09636412.2019.1551565).

MacKenzie, Donald A. *Inventing Accuracy: A Historical Sociology of Nuclear Missile Guidance*. Cambridge, MA: MIT Press, 1993.

Magnuson, Stew. “DARPA Pushes ‘Mosaic Warfare’ Concept.” *National Defense*, December 16, 2018. [https://www.nationaldefensemagazine.org/articles/2018/11/16/darpa-pushes-mosaic-warfare-concept](https://www.nationaldefensemagazine.org/articles/2018/11/16/darpa-pushes-mosaic-warfare-concept).

Mahan, Alfred Thayer. *The Influence of Sea Power Upon History, 1660–1783*. London: Sampson, Low, Marston, Searle, and Rivington, 1890.

Mahoney, Matt. *The Cost of AI*. Draft unpublished paper, March 27, 2013. [http://mattmahoney.net/costofai.pdf](http://mattmahoney.net/costofai.pdf).

Mancillas, James. “Integrating Artificial Intelligence into Military Operations.” *Mad Scientist Laboratory*, December 16, 2019. [https://madsciblog.tradoc.army.mil/198-integrating-artificial-intelligence-into-military-operations/](https://madsciblog.tradoc.army.mil/198-integrating-artificial-intelligence-into-military-operations/).

Manoj P. D., Sai, et al. “Efficient Utilization of Adversarial Training toward Robust Machine Learners and its Analysis.” Paper presented at the 2018 IEEE/ACM International Conference on Computer-Aided Design, November 5–8, 2018.

Markoff, John. “Pentagon Turns to Silicon Valley for Edge in Artificial Intelligence.” *New York Times*, May 11, 2016. [https://www.nytimes.com/2016/05/12/technology/artificial-intelligence-as-the-pentagons-latest-weapon.html](https://www.nytimes.com/2016/05/12/technology/artificial-intelligence-as-the-pentagons-latest-weapon.html).

Martel, William C. *Victory in War: Foundations of Modern Military Policy*. Cambridge: Cambridge University Press, 2007.

Martin, Bradley, et al. *Advancing Autonomous Systems*, R2751. Santa Monica, CA: RAND Corporation, 2019. [https://www.rand.org/pubs/research\_reports/RR2751.html](https://www.rand.org/pubs/research_reports/RR2751.html).

Martinage, Robert. *Toward a New Offset Strategy: Exploiting U.S. Long-Term Advantages to Restore U.S. Global Power Projection Capability*. Washington, DC: Center for Strategic and Budgetary Assessments, 2014. [https://csbaonline.org/research/publications/toward-a-new-offset-strategy-exploiting-u-s-long-term-advantages-to-restore](https://csbaonline.org/research/publications/toward-a-new-offset-strategy-exploiting-u-s-long-term-advantages-to-restore).

Masakowski, Yvonne R., Jason S. Smythe, and Thomas E. Creely. “The Impact of Ambient Intelligence Technologies on Individuals, Society, and Warfare.” *Northern Plains Ethics Journal* 4, no. 1 (Fall 2016): 1–11. [http://northernplainsethicsjournal.com/wp-content/uploads/The-Impact-of-Ambient-Intelligence-Technologies-on-Individuals.pdf](http://northernplainsethicsjournal.com/wp-content/uploads/The-Impact-of-Ambient-Intelligence-Technologies-on-Individuals.pdf).

McCaney, Kevin. “How a Trojan Can Turn AI into a Manchurian Candidate.” *Government CIO Media and Research*, December 31, 2018. [https://www.governmentciomedia.com/how-trojan-can-turn-ai-manchurian-candidate](https://www.governmentciomedia.com/how-trojan-can-turn-ai-manchurian-candidate).

McLemore, Connor S., and Charles Clark. “The Devil You Know: Trust in Military Applications of Artificial Intelligence.” *War on the Rocks*, September 23, 2019. [https://warontherocks.com/2019/09/the-devil-you-know-trust-in-military-applications-of-artificial-intelligence/](https://warontherocks.com/2019/09/the-devil-you-know-trust-in-military-applications-of-artificial-intelligence/).

McLemore, Connor S., and Hans Lauzen. “The Dawn of Artificial Intelligence in Naval Warfare.” *War on the Rocks*, June 12, 2018. [https://waronthe](https://waronthe) [rocks.com/2018/06/the-dawn-of-artificial-intelligence-in-naval-warfare/](http://rocks.com/2018/06/the-dawn-of-artificial-intelligence-in-naval-warfare/).

McMillan, Robert. “AI Has Arrived, and That Really Worries the World’s Brightest Minds.” *Wired*, January 16, 2015. [https://www.wired.com/2015/01/ai-arrived-really-worries-worlds-brightest-minds/](https://www.wired.com/2015/01/ai-arrived-really-worries-worlds-brightest-minds/).

Mehta, Aaron. “AI Makes Mattis Question ‘Fundamental’ Belief About War.” *Defense News*, February 17, 2018. [https://www.c4isrnet.com/intel-geoint/2018/02/17/ai-makes-mattis-question-fundamental-beliefs-about-war/](https://www.c4isrnet.com/intel-geoint/2018/02/17/ai-makes-mattis-question-fundamental-beliefs-about-war/).

Metz, Cade. “Mark Zuckerberg, Elon Musk, and the Feud Over Killer Robots.” *New York Times*, June 9, 2018. [https://www.nytimes.com/2018/06/09/technology/elon-musk-mark-zuckerberg-artificial-intelligence.html](https://www.nytimes.com/2018/06/09/technology/elon-musk-mark-zuckerberg-artificial-intelligence.html).

———. “We Teach A. I. Systems Everything, Including Our Biases.” *New York Times*, November 11, 2019. [https://www.nytimes.com/2019/11/11/technology/artificial-intelligence-bias.html](https://www.nytimes.com/2019/11/11/technology/artificial-intelligence-bias.html).

Mewett, Christopher. “Understanding War’s Enduring Nature Alongside Its Changing Character.” *War on the Rocks*, January 21, 2014. [https://waron](https://waron) [therocks.com/2014/01/understanding-wars-enduring-nature-alongside-its-changing-character/](http://therocks.com/2014/01/understanding-wars-enduring-nature-alongside-its-changing-character/).

Michta, Andrew A. “Time to Push Back Against the Revisionists.” *American Interest*, December 13, 2018. [https://www.the-american-interest.com/2018/12/13/time-to-push-back-against-the-revisionists/](https://www.the-american-interest.com/2018/12/13/time-to-push-back-against-the-revisionists/).

“Microsoft’s President on Silicon Valley in the Cross Hairs.” *New York Times*, September 19, 2019. [https://www.nytimes.com/2019/09/18/business/dealbook/microsoft-president-brad-smith-interview.html?searchResultPosition=1](https://www.nytimes.com/2019/09/18/business/dealbook/microsoft-president-brad-smith-interview.html?searchResultPosition=1).

Milburn, Richard M. “Reclaiming Clausewitz’s Theory of Victory.” *Parameters* 48, no. 3 (Autumn 2018): 55–63.

Miller, John H., and Scott E. Page. *Complex Adaptive Systems*. Princeton, NJ: Princeton University Press, 2007.

Miller, Susan. “DARPA Outlines Adversarial AI Defense.” GCN, January 25, 2019. [https://gcn.com/articles/2019/01/25/darpa-adversarial-ai-defense.aspx](https://gcn.com/articles/2019/01/25/darpa-adversarial-ai-defense.aspx).

Mitchell, Anna, and Larry Diamond. “China’s Surveillance State Should Scare Everyone.” *The Atlantic*, February 2, 2018. [https://www.theatlantic.com/international/archive/2018/02/china-surveillance/552203/](https://www.theatlantic.com/international/archive/2018/02/china-surveillance/552203/).

Mohammadi, M., et al. “Deep Learning for IoT Big Data and Streaming Analytics: A Survey.” *IEEE Communications Surveys and Tutorials* 20, no. 4 (2018): 2923–60. [https://arxiv.org/abs/1712.04301v2](https://arxiv.org/abs/1712.04301v2).

Moran, Bill. “It’s Time to Make Data Strategic for Our Navy.” *Defense One*, April 2, 2019. [https://www.defenseone.com/ideas/2019/04/its-time-make-data-strategic-our-navy/156020/](https://www.defenseone.com/ideas/2019/04/its-time-make-data-strategic-our-navy/156020/).

Mortland, J. E., M. Cutler, and E. K. Kaprelian. *U.S. Army Land Warfare Laboratory*, vol. 1, *Project Report, Appendix A, Documentation*. Columbus, OH: Tactical Warfare Simulation and Technology Information Analysis Center, June 1974. [https://apps.dtic.mil/dtic/tr/fulltext/u2/a002572.pdf](https://apps.dtic.mil/dtic/tr/fulltext/u2/a002572.pdf).

Mozur, Paul. “One Month, 500,000 Face Scans: How China Is Using A. I. to Target.” *New York Times*, April 14, 2019. [https://www.nytimes.com/2019/04/14/technology/china-surveillance-artificial-intelligence-racial-profiling.html](https://www.nytimes.com/2019/04/14/technology/china-surveillance-artificial-intelligence-racial-profiling.html).

Müller, Vincent C., and Nick Bostrom. “Future Progress in Artificial Intelligence: A Poll Among Experts.” *AI Matters* 1, no.1 (2014): 9–11. doi: 10.1145/2639475.2639478.

Muslimi, Mehran. “‘Five Eyes’ Tests AI in Battlefield Scenario.” *Medium*, October 18, 2018. [https://medium.com/predict/five-eyes-tests-ai-in-battlefield-scenario-52ba2016c45c](https://medium.com/predict/five-eyes-tests-ai-in-battlefield-scenario-52ba2016c45c).

Myers, Meghann. “Top Recruiter: Just 136,000 out of 33 Million Young Americans Would Join the Army.” *Army Times*, October 12, 2017. [https://www.armytimes.com/news/your-army/2017/10/12/top-recruiter-just-136000-out-of-33-million-young-americans-would-join-the-army/](https://www.armytimes.com/news/your-army/2017/10/12/top-recruiter-just-136000-out-of-33-million-young-americans-would-join-the-army/).

National Research Council. *Artificial Intelligence: Current Status and Future Potential*. Washington, DC: National Academies Press, 1985. [https://doi.org/10.17226/18501](https://doi.org/10.17226/18501).

———. *Naval Communications Architecture*. Washington, DC: National Academies Press, 1994. [https://doi.org/10.1s7226/18600](https://doi.org/10.1s7226/18600).

National Science and Technology Council, Committee on Technology. *Preparing for the Future of Artificial Intelligence*, October 2016. [https://obamawhitehouse.archives.gov/sites/default/files/whitehouse\_files/microsites/ostp/NSTC/preparing\_for\_the\_future\_of\_ai.pdf](https://obamawhitehouse.archives.gov/sites/default/files/whitehouse_files/microsites/ostp/NSTC/preparing_for_the_future_of_ai.pdf).

National Science and Technology Council, Networking and Information Technology Research and Development Subcommittee. *The National Artificial Intelligence Research and Development Strategic Plan*, October 2016. [https://www.nitrd.gov/pubs/national\_ai\_rd\_strategic\_plan.pdf](https://www.nitrd.gov/pubs/national_ai_rd_strategic_plan.pdf).

National Science and Technology Council, Select Committee on Artificial Intelligence. *The National Artificial Intelligence Research and Development Strategic Plan: 2019 Update*. [https://www.nitrd.gov/pubs/National-AI-RD-Strategy-2019.pdf](https://www.nitrd.gov/pubs/National-AI-RD-Strategy-2019.pdf).

National Security Commission on Artificial Intelligence. *Interim Report*, November 2019. [https://www.epic.org/foia/epic-v-ai-commission/AI-Commission-Interim-Report-Nov-2019.pdf](https://www.epic.org/foia/epic-v-ai-commission/AI-Commission-Interim-Report-Nov-2019.pdf).

Naval War College. *Joint Military Operations Reference Guide*. Monterey, CA: Department of the Navy, 2011.

Needleman, Sarah E., and Katherine Bindley. “Google Puts Curbs on Political Debate by Employees.” *The Wall Street Journal*, August 23, 2019. [https://www.wsj.com/articles/google-puts-curbs-on-political-debate-by-employees-11566576970](https://www.wsj.com/articles/google-puts-curbs-on-political-debate-by-employees-11566576970).

Newman, Lily Hay. “The Drone Iran Shot Down Was a $220M Surveillance Monster.” *Wired*, June 20, 2019. [https://www.wired.com/story/iran-global-hawk-drone-surveillance/](https://www.wired.com/story/iran-global-hawk-drone-surveillance/).

Northrup Grumman. “MQ-4C Triton: Vigilance for a Changing World.” [https://www.northropgrumman.com/MediaResources/MediaKits/Avalon/Documents/Triton\_Brochure.pdf](https://www.northropgrumman.com/MediaResources/MediaKits/Avalon/Documents/Triton_Brochure.pdf).

———. “X-47B UCAS Makes Aviation History … Again! Successfully Completes First Ever Autonomous Aerial Refueling Demonstration.” [https://www.northropgrumman.com/Capabilities/X47BUCAS/Pages/default.aspx](https://www.northropgrumman.com/Capabilities/X47BUCAS/Pages/default.aspx).

O’Donoghue, Brendan. “The Manned-Unmanned Team Is the Future.” U.S. Naval Institute *Proceedings* 144, no. 6 (June 2018): 68–69.

Office of the Director of National Intelligence. “The AIM Initiative: A Strategy for Augmenting Intelligence Using Machines.” Web post, January 16, 2019. [https://www.dni.gov/index.php/newsroom/reports-publications/item/1940-the-aim-initiative-a-strategy-for-augmenting-intelli](https://www.dni.gov/index.php/newsroom/reports-publications/item/1940-the-aim-initiative-a-strategy-for-augmenting-intelli) gence-using-machines.

Office of the Director of National Intelligence, Global Intelligence Council. *Global Trends: Paradox of Progress*, January 31, 2017. [https://www.dni.gov/index.php/global-trends-home](https://www.dni.gov/index.php/global-trends-home).

Office of the Director of National Intelligence, Intelligence Advanced Research Projects Agency. “Research Programs.” Web post, no date. [https://www.iarpa.gov/index.php/research-programs](https://www.iarpa.gov/index.php/research-programs).

Office of Naval Research. *Naval Research and Development: A Framework for Accelerating to the Navy & Marine Corps After Next*, 2017. [https://www.onr.navy.mil/en/our-research/naval-research-framework](https://www.onr.navy.mil/en/our-research/naval-research-framework).

O’Rourke, Ronald. *Navy Large Surface and Undersea Unmanned Vehicles: Background and Issues for Congress*, R45757. Washington, DC: Congressional Research Service, updated September 18, 2019. [https://fas.org/sgp/crs/weapons/R45757.pdf](https://fas.org/sgp/crs/weapons/R45757.pdf).

Osborn, Kris. “Navy Fast-Tracks New Large ‘Strike Warfare’ Attack Surface Drones.” *Defense Maven*, June 27, 2019. [https://defensemaven.io/warriormaven/sea/navy-fast-tracks-new-large-strike-warfare-attack-surface-drones-vM](https://defensemaven.io/warriormaven/sea/navy-fast-tracks-new-large-strike-warfare-attack-surface-drones-vM) BZm-l51UaikVu8kF8t6Q

———.“New Navy Ocean Attack Plan—Combined Air, Surface, and Undersea Drones.” *Defense Maven*, June 5, 2019. [https://defensemaven.io/warriormaven/sea/new-navy-ocean-attack-plan-combined-air-surface-undersea-drones-6pcbbomEnkGCZ-lTsnoyaA/](https://defensemaven.io/warriormaven/sea/new-navy-ocean-attack-plan-combined-air-surface-undersea-drones-6pcbbomEnkGCZ-lTsnoyaA/).

Osinga, Frans P. B. *Science, Strategy, and War*. New York: Routledge, 2006.

Ozen, Bulend. “Towards Post-Strategy? The Hard Intervention of Artificial Intelligence on Military Thought.” *Small Wars Journal*, December 28, 2018. [https://smallwarsjournal.com/jrnl/art/towards-post-strategy-hard-intervention-artificial-intelligence-military-thought](https://smallwarsjournal.com/jrnl/art/towards-post-strategy-hard-intervention-artificial-intelligence-military-thought).

Palmer, Michael. *Command at Sea*. Cambridge, MA: Harvard University Press, 2007.

Papernot, Nicolas, and Ian Goodfellow. “Breaking Things Is Easy.” *clever hans-blog*, December 16, 2016. [http://www.cleverhans.io/security/privacy/ml/2016/12/16/breaking-things-is-easy.html](http://www.cleverhans.io/security/privacy/ml/2016/12/16/breaking-things-is-easy.html).

Parker, Emily. “Silicon Valley Cannot Destroy Democracy Without Our Help.” *New York Times*, November 3, 2017. [https://www.nytimes.com/2017/11/02/opinion/silicon-valley-democracy-russia.html](https://www.nytimes.com/2017/11/02/opinion/silicon-valley-democracy-russia.html).

Payne, Kenneth. “Artificial Intelligence: A Revolution in Strategic Affairs?” *Survival* 60, no. 5 (2018): 7–32. [https://www.tandfonline.com/doi/full/10.1080/00396338.2018.1518374](https://www.tandfonline.com/doi/full/10.1080/00396338.2018.1518374).

Pearl, Judea, and Dana Mackenzie. *The Book of Why: The New Science of Cause and Effect*. New York: Basic Books, 2018.

Pecotic, Adrian. “Whoever Predicts the Future Will Win the AI Arms Race.” *Foreign Policy*, March 5, 2019. [https://foreignpolicy.com/2019/03/05/whoever-predicts-the-future-correctly-will-win-the-ai-arms-race-russia-china-united-states-artificial-intelligence-defense/](https://foreignpolicy.com/2019/03/05/whoever-predicts-the-future-correctly-will-win-the-ai-arms-race-russia-china-united-states-artificial-intelligence-defense/).

Pellerin, Cheryl. “Project Maven to Deploy Computer Algorithms to War Zone by Year’s End.” DoD News/Defense Media Activity, July 21, 2017. [https://dod.defense.gov/News/Article/Article/1254719/project-maven-to-deploy-computer-algorithms-to-war-zone-by-years-end/](https://dod.defense.gov/News/Article/Article/1254719/project-maven-to-deploy-computer-algorithms-to-war-zone-by-years-end/).

———. “Work: Wargaming Critical in Dynamic Security Environment.” Department of Defense News, December 11, 2015. [https://dod.defense.gov/News/Article/Article/633892/work-wargaming-critical-in-dynamic-security-environment/](https://dod.defense.gov/News/Article/Article/633892/work-wargaming-critical-in-dynamic-security-environment/).

People’s Republic of China. “Notice of the State Council Issuing the Next Generation of Artificial Intelligence Development Plan, State Council Document \[2017\] No. 35,” trans. by the Foundation for Law and International Affairs. [https://flia.org/wp-content/uploads/2017/07/A-New-Generation-of-Artificial-Intelligence-Development-Plan-1.pdf](https://flia.org/wp-content/uploads/2017/07/A-New-Generation-of-Artificial-Intelligence-Development-Plan-1.pdf).

———, State Council Information Office. *China’s National Defense in the New Era*. July 2019. [http://www.xinhuanet.com/english/2019-07/24/c\_138253389.htm](http://www.xinhuanet.com/english/2019-07/24/c_138253389.htm).

Phillips, Eve M. *If It Works, It’s Not AI: A Commercial Look at Artificial Intelligence Startups*. Thesis, Massachusetts Institute of Technology, May 7, 1999. [https://dspace.mit.edu/bitstream/handle/1721.1/80558/43557450-MIT.pdf?sequence=2](https://dspace.mit.edu/bitstream/handle/1721.1/80558/43557450-MIT.pdf?sequence=2).

Pigeau, Ross, and Carol McCann. “Re-conceptualizing Command and Control.” *Canadian Military Journal* (Spring 2002). [http://cradpdf.drdc-rddc.gc.ca/PDFS/unc17/p519041.pdf](http://cradpdf.drdc-rddc.gc.ca/PDFS/unc17/p519041.pdf).

Piller, Charles. “Vaunted Patriot Missile Has a ‘Friendly Fire’ Failing.” *Los Angeles Times*, April 21, 2003. [https://www.latimes.com/archives/la-xpm-2003-apr-21-war-patriot21-story.html](https://www.latimes.com/archives/la-xpm-2003-apr-21-war-patriot21-story.html).

Pinch, Trevor J., and Wiebe E. Bijker. “The Social Construction of Facts and Artefacts: Or How the Sociology of Science and the Sociology of Technology Might Benefit Each Other.” *Social Studies of Science* 14, no. 3 (1984):399–441.

Pomerleau, Mark. “DoD Plans to Invest $600M in Unmanned Underwater Vehicles.” *Defense Systems*, February 2, 2016. [https://defensesystems.com/articles/2016/02/04/dod-navy-uuv-investments.aspx](https://defensesystems.com/articles/2016/02/04/dod-navy-uuv-investments.aspx).

———. “The Navy’s Plan to Stop Being ‘Woefully Behind’ in Cyber.” *The Fifth Domain*, October 24, 2019. [https://www.fifthdomain.com/dod/navy/2019/10/24/the-navys-plan-to-stop-being-woefully-behind-in-cyber/](https://www.fifthdomain.com/dod/navy/2019/10/24/the-navys-plan-to-stop-being-woefully-behind-in-cyber/).

Popper, Karl R. *Conjectures and Refutations: The Growth of Scientific Knowledge*. New York: Harper and Row, 1963.

Posner, Gerald. *Why America Slept: The Failure to Prevent 9/11*. New York: Random House, 2003.

Potter, E. B. *Bull Halsey*. Annapolis, MD: Naval Institute Press, 1985.

———. *Sea Power: A Naval History*, 2nd ed. Annapolis, MD: United States Naval Institute, 1981.

Powell, Colin L. “The Essence of Leadership.” YouTube, February 10, 2011. [https://www.youtube.com/watch?v=ocSw1m30UBI](https://www.youtube.com/watch?v=ocSw1m30UBI).

Preece, Jenny, et al. *Human-Computer Interaction*. Boston: Addison-Wesley Longman, 1994.

Pressman, Aaron. “‘A. I., Captain’: The Robotic Navy Ship of the Future.” *Fortune*, May 22, 2019. [https://fortune.com/longform/leidos-sea-hunter-ai-navy-ship/](https://fortune.com/longform/leidos-sea-hunter-ai-navy-ship/).

Price Waterhouse Cooper. “Global State of Information Security Survey 2015.” In *Annual State of Information Security Survey*, 2014, [https://www.pwc.com/gx/en/consulting-services/information-security-survey/assets/the-global-state-of-information-security-survey-2015.pdf](https://www.pwc.com/gx/en/consulting-services/information-security-survey/assets/the-global-state-of-information-security-survey-2015.pdf).

“Probabilistic Graphical Models 2: Inference.” Coursera, Stanford University. [https://www.coursera.org/lecture/probabilistic-graphical-models-2-inference/inference-summary-4ntRs](https://www.coursera.org/lecture/probabilistic-graphical-models-2-inference/inference-summary-4ntRs).

Ram, Aliya. “Europe’s AI Start-Ups Often Do Not Use AI, Study Finds.” *Financial Times*, March 4, 2019. [https://www.ft.com/content/21b19010-3e9f-11e9-b896-fe36ec32aece](https://www.ft.com/content/21b19010-3e9f-11e9-b896-fe36ec32aece).

Rawlinson, Kevin. “Microsoft’s Bill Gates Insists AI Is a Threat.” *BBC News*, January 29, 2015. [https://www.bbc.com/news/31047780](https://www.bbc.com/news/31047780).

Recorded Future. “White Paper: The Security Intelligence Graph,” 2019. [https://go.recordedfuture.com/security-intelligence-graph](https://go.recordedfuture.com/security-intelligence-graph).

Resnick, Mitchel, et al. “Design Principles for Tools to Support Creative Thinking.” *Carnegie Mellon Research Showcase @ CMU*, October 30, 2005. [http://www.iimagineservicedesign.com/wp-content/uploads/2015/08/Design-Principles-for-Tools-to-Support-Creative-Thinking.pdf](http://www.iimagineservicedesign.com/wp-content/uploads/2015/08/Design-Principles-for-Tools-to-Support-Creative-Thinking.pdf).

Ressler, Cali, and Jody Thompson. *Why Work Sucks and How to Fix It*. New York: Penguin Books Ltd., 2008.

Richardson, John M. *A Design for Maintaining Maritime Superiority, Version 2.0*, December 2018. [https://www.navy.mil/navydata/people/cno/Richardson/Resource/Design\_2.0.pdf](https://www.navy.mil/navydata/people/cno/Richardson/Resource/Design_2.0.pdf).

———. *The Future Navy*. May 17, 2017. [https://www.navy.mil/navydata/people/cno/Richardson/Resource/TheFutureNavy.pdf](https://www.navy.mil/navydata/people/cno/Richardson/Resource/TheFutureNavy.pdf)

———. “Navy Nation Needs.” Speech given at the Heritage Foundation, February 1, 2018. [https://www.navy.mil/navydata/people/cno/Richardson/Speech/180201\_CNORichardson\_Heritage\_Speech.pdf](https://www.navy.mil/navydata/people/cno/Richardson/Speech/180201_CNORichardson_Heritage_Speech.pdf).

Robitzski, Dan. “Advanced Artificial Intelligence Could Run the World Better Than Humans Ever Could.” *Futurism*, August 29, 2018. [https://futurism.com/advanced-artificial-intelligence-better-humans/](https://futurism.com/advanced-artificial-intelligence-better-humans/).

———. “Five Experts Share What Scares Them the Most About AI.” *Futurism*, September 5, 2018. [https://futurism.com/artificial-intelligence-experts-fear](https://futurism.com/artificial-intelligence-experts-fear).

———. “New AI Generates Horrifyingly Plausible Fake News.” *Futurism*, May 30, 2019. [https://futurism.com/ai-generates-fake-news](https://futurism.com/ai-generates-fake-news).

———. “Should Evil AI Research Be Published? Five Experts Weigh In.” *Futurism*, August 27, 2018. [https://futurism.com/should-evil-ai-research-be-published-five-experts-weigh-in](https://futurism.com/should-evil-ai-research-be-published-five-experts-weigh-in).

———. “When Will We Have Artificial Intelligence as Smart as a Human? Here’s What Experts Think.” *Futurism*, September 24, 2018. [https://futurism.com/human-level-artificial-intelligence-agi/](https://futurism.com/human-level-artificial-intelligence-agi/).

Roblin, Sebastien. “The U.S. Navy Has Orca Robot Submarines on the Way that Could Transform Naval Warfare.” *The National Interest*, October 20, 2019. [https://nationalinterest.org/blog/buzz/us-navy-has-orca-robot-sub](https://nationalinterest.org/blog/buzz/us-navy-has-orca-robot-sub) marines-way-could-transform-naval-warfare-89721.

Roff, Heather M., and David Danks. “‘Trust but Verify’: The Difficulty of Trusting Autonomous Weapons Systems.” *Journal of Military Ethics* 17, no. 1 (2018): 2–20.

Rondeau, Tom. “Adaptive RF Technology (ART).” Defense Advanced Research Projects Agency Web post. [https://www.darpa.mil/program/adaptive-rf-technologies](https://www.darpa.mil/program/adaptive-rf-technologies).

Rosenberg, Matt. “Population Decline in Russia: Russia’s Population Set to Decline from 143 Million Today to 111 Million in 2050.” *ThoughtCo*, September 2, 2019. [https://www.thoughtco.com/population-decline-in-russia-1435266](https://www.thoughtco.com/population-decline-in-russia-1435266).

Rothstein, Hy, and Barton Whaley, eds. *The Art and Science of Military Deception*. Boston: ARTECH House, 2013.

Rouhani, B. D., et al. “Assured Deep Learning: Practical Defense Against Adversarial Attacks.” Paper presented at the 2018 IEEE/ACM International Conference on Computer-Aided Design, November 5–8, 2018.

Rowden, Thomas, Peter Gumataotao, and Peter Fanta. “Distributed Lethality.” *U.S. Naval Institute Proceedings* 141, no. 1 (January 2015): 18–23.

Ruiz, Armand. “The 80/20 Data Science Dilemma.” *InfoWorld*, September 26, 2017. [https://www.infoworld.com/article/3228245/the-80-20-data-science-dilemma.html](https://www.infoworld.com/article/3228245/the-80-20-data-science-dilemma.html).

Russell, James. *Innovation, Transformation, and War: Counterinsurgency Operations in Anbar and Ninewa Provinces, Iraq, 2005–2007*. Stanford, CA: Stanford University Press, 2010.

Russell, Stuart J., and Peter Norvig. *Artificial Intelligence: A Modern Approach*, 2nd ed. Upper Saddle River, NJ: Prentice-Hall, 2003.

Ryan, Emma. “Law Firm Without Lawyers Opens Doors.” *Lawyers Weekly*, November 15, 2017. [https://www.lawyersweekly.com.au/sme-law/22256-law-firm-without-lawyers-opens-its-doors](https://www.lawyersweekly.com.au/sme-law/22256-law-firm-without-lawyers-opens-its-doors).

Samuels, Joel. “What Is an Oligarch?” *Defense One*, November 16, 2019. [https://www.defenseone.com/ideas/2019/11/what-oligarch/161353/?oref=d-river](https://www.defenseone.com/ideas/2019/11/what-oligarch/161353/?oref=d-river).

Samuels, Richard J. “*Rich Nation, Strong Army”: National Security and the Technological Transformation of Japan*. Ithaca, NY: Cornell University Press, 1994.

Sayler, Kelley. *Red Alert: The Growing Threat to U.S. Aircraft Carriers*. Washington, DC: Center for a New American Security, February 2016. [https://www.cnas.org/publications/reports/red-alert-the-growing-threat-to-u-s-aircraft-carriers](https://www.cnas.org/publications/reports/red-alert-the-growing-threat-to-u-s-aircraft-carriers).

Scharre, Paul. *Army of None: Autonomous Weapons and the Future of War*. New York: W. W. Norton, 2018.

———. “Centaur Warfighting: The False Choice of Humans vs. Automation.” *Temple International and Comparative Law Journal* 30, no. 1 (Spring 2016): 151-65. [https://sites.temple.edu/ticlj/files/2017/02/30.1.Scharre-TICLJ.pdf](https://sites.temple.edu/ticlj/files/2017/02/30.1.Scharre-TICLJ.pdf).

———. “How to Lose the Robotics Revolution.” *War on the Rocks*, June 29, 2014. [https://warontherocks.com/2014/07/how-to-lose-the-robotics-revolution/](https://warontherocks.com/2014/07/how-to-lose-the-robotics-revolution/).

———. “Left Behind: Why It’s Time to Draft Robots for CASEVAC.” *War on the Rocks*, August 12, 2014. [https://warontherocks.com/2014/08/left-behind-why-its-time-to-draft-robots-for-casevac/](https://warontherocks.com/2014/08/left-behind-why-its-time-to-draft-robots-for-casevac/).

———. “A Million Mistakes a Second.” *Foreign Policy*, September 12, 2018. [https://foreignpolicy.com/2018/09/12/a-million-mistakes-a-second-future-of-war/](https://foreignpolicy.com/2018/09/12/a-million-mistakes-a-second-future-of-war/).

Schneider, Jacquelyn. “Blue Hair in the Gray Zone.” *War on the Rocks*, January 10, 2018. [https://warontherocks.com/2018/01/blue-hair-gray-zone/](https://warontherocks.com/2018/01/blue-hair-gray-zone/).

Schneider, Tim, and Naomi Rea. “Has Artificial Intelligence Given Us the Next Great Art Movement? Experts Say Slow Down, the ‘Field Is in its Infancy’.” *ArtNet News*, September 15, 2018. [https://news.artnet.com/art-world/ai-art-comes-to-market-is-it-worth-the-hype-1352011](https://news.artnet.com/art-world/ai-art-comes-to-market-is-it-worth-the-hype-1352011).

“Sea Hunter Reaches New Autonomy Milestone.” *Naval News*, February 4, 2019. [https://www.navalnews.com/naval-news/2019/02/sea-hunter-usv-reaches-new-autonomy-milestone/](https://www.navalnews.com/naval-news/2019/02/sea-hunter-usv-reaches-new-autonomy-milestone/).

“Sea Hunter Reaches New Milestone for Autonomy.” Leidos Web site, January 31, 2019. [https://www.leidos.com/insights/sea-hunter-reaches-new-milestone-autonomy](https://www.leidos.com/insights/sea-hunter-reaches-new-milestone-autonomy).

Seck, Hope Hodge. “The Navy Is Getting a Pinpoint Landing System for F-35s on All Its Aircraft Carriers.” *Business Insider*, June 24, 2019. [https://www.businessinsider.com/navy-getting-jpals-pinpoint-landing-system-f35s-on-carriers-amphibs-2019-6](https://www.businessinsider.com/navy-getting-jpals-pinpoint-landing-system-f35s-on-carriers-amphibs-2019-6).

Shankland, Stephen. “IBM’s World-Class Summit Supercomputer Gooses Speed with AI Abilities.” *CNET News*, June 8, 2018. [https://www.cnet.com/news/ibms-world-class-summit-supercomputer-gooses-speed-with-ai-abilities/](https://www.cnet.com/news/ibms-world-class-summit-supercomputer-gooses-speed-with-ai-abilities/).

Shariff, Azim, Iyad Rahwan, and Jean-Francois Bonnefon. “Whose Life Should Your Car Save?” *New York Times*, November 6, 2016. [https://www.nytimes.com/2016/11/06/opinion/sunday/whose-life-should-your-car-save.html](https://www.nytimes.com/2016/11/06/opinion/sunday/whose-life-should-your-car-save.html).

Sharkey, Noel. “Killer Robots from Russia Without Love.” *Forbes*, November 28, 2018. [https://www.forbes.com/sites/noelsharkey/2018/11/28/killer-robots-from-russia-without-love/#3640d4dbcf01](https://www.forbes.com/sites/noelsharkey/2018/11/28/killer-robots-from-russia-without-love/#3640d4dbcf01).

Shneiderman, Ben. “Creativity Support Tools: Accelerating Discovery and Innovation.” *Communications of the ACM* 50, no. 12 (2007): 20–32.

Shoham, Yoav, et al. *The AI Index 2018 Annual Report*. AI Index Steering Committee, Human-Centered AI Initiative, Stanford University, December 2018. [http://cdn.aiindex.org/2018/AI%20Index%202018%20Annual%20Report.pdf](http://cdn.aiindex.org/2018/AI%20Index%202018%20Annual%20Report.pdf).

Shou, Darren. “The Next Big Privacy Hurdle? Teaching AI to Forget.” *Wired*, June 12, 2018. [https://www.wired.com/story/the-next-big-privacy-hurdle-teaching-ai-to-forget/](https://www.wired.com/story/the-next-big-privacy-hurdle-teaching-ai-to-forget/).

Siegelmann, Hava. “Guaranteeing AI Robustness against Deception (GARD).” DARPA Power Point brief, February 6, 2019. [https://www.darpa.mil/attachments/GARD\_ProposersDay.pdf](https://www.darpa.mil/attachments/GARD_ProposersDay.pdf).

Simon, Matt. “Facebook Knows More About You Than the CIA.” *Wired*, July 24, 2018. [https://www.wired.com/story/facebook-knows-more-about-you-than-cia](https://www.wired.com/story/facebook-knows-more-about-you-than-cia).

Singer, Peter. “In the Loop? Armed Robots and the Future of War.” Brookings Institution, January 28, 2019. [http://www.brookings.edu/research/articles/2009/01/28-robots-singer](http://www.brookings.edu/research/articles/2009/01/28-robots-singer).

———. *Wired for War: The Robotics Revolution and Conflict in the 21st Century*. New York: Penguin Press, 2009.

Skymind Inc. “Artificial Intelligence (AI) vs. Machine Learning vs. Deep Learning.” A. I. Wiki. [https://skymind.ai/wiki/ai-vs-machine-learning-vs-deep-learning](https://skymind.ai/wiki/ai-vs-machine-learning-vs-deep-learning).

———. “A Beginner’s Guide to Automated Machine Learning & AI.” A. I. Wiki. [https://skymind.ai/wiki/automl-automated-machine-learning-ai](https://skymind.ai/wiki/automl-automated-machine-learning-ai).

———. “A Beginner’s Guide to Neural Networks and Deep Learning.” A. I. Wiki. [https://skymind.ai/wiki/neural-network](https://skymind.ai/wiki/neural-network).

Slye, Robert J. *Optimizing Training Event Schedules at Naval Air Station Fallon*. Master’s thesis, Naval Postgraduate School, March 2018. [https://calhoun.nps.edu/handle/10945/58370](https://calhoun.nps.edu/handle/10945/58370).

Smith, Craig S. “Dealing with Biases in Artificial Intelligence.” *New York Times*, November 19, 2019. [https://www.nytimes.com/2019/11/19/technology/artificial-intelligence-bias.html](https://www.nytimes.com/2019/11/19/technology/artificial-intelligence-bias.html).

Smith, Wolfgang. *Physics and Vertical Causation*. Brooklyn, NY: Angelico Press, 2019.

Smith-Spark, Laura, and Milena Veselinovic. “Russians Charged Over UK Novichok Nerve Agent Attack.” *CNN*, September 5, 2018. [https://www.cnn.com/2018/09/05/uk/uk-russians-novichok-intl/index.html](https://www.cnn.com/2018/09/05/uk/uk-russians-novichok-intl/index.html).

Solomon, Jonathan F. “Maritime Deception and Concealment: Concepts for Defeating Wide-Area Oceanic Surveillance-Reconnaissance-Strike Networks.” *Naval War College Review* 66 no. 4 (Autumn 2013): 87–120. [https://digital-commons.usnwc.edu/nwc-review/vol66/iss4/7](https://digital-commons.usnwc.edu/nwc-review/vol66/iss4/7).

Spillner, Brent. “Bedrock Principles for Artificial Intelligence.” U.S. Naval Institute *Proceedings* 145, no. 7 (July 2019): 76–78.

Staughton, John. “The Human Brain vs. Supercomputers … Which One Wins?” *Science ABC*, 2015. [https://www.scienceabc.com/humans/the-human-brain-vs-supercomputers-which-one-wins.html](https://www.scienceabc.com/humans/the-human-brain-vs-supercomputers-which-one-wins.html).

Steele, Jeanette. “Joint Artificial Intelligence Director Tells Naval War College Audience to ‘Dive In’ on AI.” *U.S. Navy News Service*, December 13, 2019. [https://www.navy.mil/submit/display.asp?story\_id=111692](https://www.navy.mil/submit/display.asp?story_id=111692).

Stewart, Phil. “U.S. Drone Shot Down by Iranian Missile in International Airspace: U.S. Source.” *Reuters*, June 20, 2019. [https://www.reuters.com/article/us-mideast-iran-usa-shootdown/u-s-drone-shot-down-by-iranian-missile-in-international-airspace-u-s-source-idUSKCN1TL0IR](https://www.reuters.com/article/us-mideast-iran-usa-shootdown/u-s-drone-shot-down-by-iranian-missile-in-international-airspace-u-s-source-idUSKCN1TL0IR).

Strawser, Bradley, and Jeff McMahan. *Killing by Remote Control: The Ethics of an Unmanned Military*. Oxford: Oxford University Press, 2013.

Stubberud, Allen R., and H. Wabgaonkar. “Approximation and Estimation Techniques for Neural Networks.” *Proceedings of the 28th Conference on Decision and Control*, December 1990, Honolulu, 2736–40.

Sugden, John. *Nelson: A Dream of Glory*. New York: Holt and Co., 2004.

Sullivan, Patrick. *Strategic Robot Power: Artificial Intelligence and National Security*. Carlisle, PA: U.S. Army War College, January 4, 2017. [https://publications.armywarcollege.edu/pubs/3497.pdf](https://publications.armywarcollege.edu/pubs/3497.pdf).

Sumida, Jon Tetsuro. *Inventing Grand Strategy and Teaching Command*. Washington, DC: Woodrow Wilson Center/Johns Hopkins University Press, 1997.

Summe, Jack N. “Navy’s New Strategy and Organization for Information Dominance.” *CHIPS: The Department of the Navy’s Informational Technology Magazine* (January–March 2010). [https://www.doncio.navy.mil/CHIPS/ArticleDetails.aspx?ID=2557](https://www.doncio.navy.mil/CHIPS/ArticleDetails.aspx?ID=2557).

Surdu, John R., and Kevin Kittka. “Deep Green: Commander’s Tool for COA’s Concept,” 2008. [http://www.bucksurdu.com/Professional/Documents/11260-CCCT-08-DeepGreen.pdf](http://www.bucksurdu.com/Professional/Documents/11260-CCCT-08-DeepGreen.pdf).

Swift, Scott. “A Fleet Must Be Able to Fight.” U. S. Naval Institute *Proceedings* 144, no. 5 (May 2018): 38–43.

———. “Master the Art of Command and Control,” U.S. Naval Institute *Proceedings* 144, no. 2 (February 2018): 28–33.

Symonds, Craig. *The Battle of Midway*. New York: Oxford University Press, 2011.

Szegedy, Christian, et al. “Intriguing Properties of Neural Networks.” *Cornell University [arXiv.org](http://arXiv.org) IV*, December 21, 2013. [https://arxiv.org/pdf/1312.6199.pdf](https://arxiv.org/pdf/1312.6199.pdf).

Taber, Rob. “Character vs. Nature of Warfare: What We Can Learn (Again) from Clausewitz.” *Mad Scientist Laboratory*, August 27, 2018. [https://madsciblog.tradoc.army.mil/79-character-vs-nature-of-warfare-what-we-can-learn-again-from-clausewitz/](https://madsciblog.tradoc.army.mil/79-character-vs-nature-of-warfare-what-we-can-learn-again-from-clausewitz/).

Tangredi, Sam J. *Anti-Access Warfare: Countering A2/AD Strategies*. Annapolis, MD: Naval Institute Press, 2013.

———. “Running Silent and Algorithmic: The U. S. Navy Strategic Vision in 2019.” *Naval War College Review* 72, no. 2 (Spring 2019): 129–65. [https://digital-commons.usnwc.edu/nwc-review/vol72/iss2/20/](https://digital-commons.usnwc.edu/nwc-review/vol72/iss2/20/).

Tarraf, Danielle, et al. *The Department of Defense Posture for Artificial Intelligence: Assessment and Recommendations*, RAND Report 4229. Santa Monica, CA: RAND Corporation, 2019. [https://www.rand.org/content/dam/rand/pubs/research\_reports/RR4200/RR4229/RAND\_RR4229.pdf](https://www.rand.org/content/dam/rand/pubs/research_reports/RR4200/RR4229/RAND_RR4229.pdf).

Taylor, Chloe. “A Record Number of Robots Were Put to Work Across North America in 2018, Report Says.” *CNBC*, February 28, 2019. [https://www.cnbc.com/2019/02/28/record-number-of-robots-were-put-to-work-in-north-america-in-2018.html](https://www.cnbc.com/2019/02/28/record-number-of-robots-were-put-to-work-in-north-america-in-2018.html).

Taylor, Gavin, et al. “Training Neural Nets without Gradients: A Scalable ADMM Approach.” *Proceedings of the International Conference on Machine Learning*, 2016. [https://arxiv.org/pdf/1605.02026v1.pdf](https://arxiv.org/pdf/1605.02026v1.pdf).

Technology for Global Security. *AI and the Military: Forever Altering Strategic Stability*. February 13, 2019. [https://medium.com/@Tech4GS/ai-and-the-military-forever-altering-strategic-stability-7471363bf9de](https://medium.com/@Tech4GS/ai-and-the-military-forever-altering-strategic-stability-7471363bf9de).

Tencent Keen Security Lab, “Experimental Security Research of Tesla Autopilot.” March 28, 2019. [https://keenlab.tencent.com/en/whitepapers/Experimental\_Security\_Research\_of\_Tesla\_Autopilot.pdf.Video](https://keenlab.tencent.com/en/whitepapers/Experimental_Security_Research_of_Tesla_Autopilot.pdf.Video) version [https://www.youtube.com/watch?v=6QSsKy0I9LE](https://www.youtube.com/watch?v=6QSsKy0I9LE).

Thompson, Loren. *Networking the Navy: A Model for Modern Warfare*. Arlington, VA: Lexington Institute, 2003.

Till, Geoffrey. *Seapower: A Guide for the Twenty-First Century*, 3rd ed. New York: Routledge, 2013.

Tingle, Anthony. “The Human-Machine Team Failed Vincennes.” U.S. Naval Institute *Proceedings* 144, no. 7 (July 2018): 38–41.

Trent, Stoney, and Scott Lathrop. “A Primer on Artificial Intelligence for Military Leaders.” *Small Wars Journal*, August 22, 2018. [https://smallwarsjournal.com/jrnl/art/primer-artificial-intelligence-military-leaders](https://smallwarsjournal.com/jrnl/art/primer-artificial-intelligence-military-leaders).

Trevithick, Joseph. “Navy’s Sea Hunter Drone Ship Has Sailed Autonomously to Hawaii and Back Amid Talk of New Roles.” *The Drive*, February 4, 2019. [https://www.thedrive.com/the-war-zone/26319/usns-sea-hunter-drone-ship-has-sailed-autonomously-to-hawaii-and-back-amid-talk-ofnew-roles](https://www.thedrive.com/the-war-zone/26319/usns-sea-hunter-drone-ship-has-sailed-autonomously-to-hawaii-and-back-amid-talk-ofnew-roles).

———. “The U.S. Navy Has Created Its First Ever Underwater Drone Squadron.” *The Drive*, September 28, 2017. [https://www.thedrive.com/the-war-zone/14733/the-us-navy-has-created-its-first-ever-underwater-drone-squadron](https://www.thedrive.com/the-war-zone/14733/the-us-navy-has-created-its-first-ever-underwater-drone-squadron).

Tucker, Patrick. “European Countries to Test AI Border Guards.” *Defense One*, November 1, 2018. [https://www.defenseone.com/technology/2018/11/european-countries-test-ai-border-guards/152511/](https://www.defenseone.com/technology/2018/11/european-countries-test-ai-border-guards/152511/).

———. “House Appropriators Take Aim at Some of the Pentagon’s Most Ambitious Tech Ideas.” *Defense One*, May 21, 2019. [https://www.defenseone.com/technology/2019/05/house-appropriators-take-aim-some-pentagons-most-ambitious-tech-ideas/157170/](https://www.defenseone.com/technology/2019/05/house-appropriators-take-aim-some-pentagons-most-ambitious-tech-ideas/157170/).

———. “The Newest AI-Enabled Weapon: ‘Deep-Faking’ Photos of the Earth.” *Defense One*, March 31, 2019. [https://www.defenseone.com/technology/2019/03/next-phase-ai-deep-faking-whole-world-and-china-ahead/155944/](https://www.defenseone.com/technology/2019/03/next-phase-ai-deep-faking-whole-world-and-china-ahead/155944/).

———. “Pentagon Seeks a List of Ethical Principles for Using AI in War.” *Defense One*, January 4, 2019. [https://www.defenseone.com/technology/2019/01/pentagon-seeks-list-ethical-principles-using-ai-war/153940/](https://www.defenseone.com/technology/2019/01/pentagon-seeks-list-ethical-principles-using-ai-war/153940/).

———. “The U. S. Army Wants to Reinvent Tank Warfare with AI.” *Defense One*, October 18, 2019. [https://www.defenseone.com/technology/2019/10/us-army-wants-reinvent-tank-warfare-ai/160720/?oref=defense\_one\_breaking\_nl](https://www.defenseone.com/technology/2019/10/us-army-wants-reinvent-tank-warfare-ai/160720/?oref=defense_one_breaking_nl).

Tully, Anthony, and Jonathan Parshall. *Shattered Sword: The Untold Story of the Battle of Midway*. Dulles, VA : Potomac Books, 2005.

Turner, Julian. “Sea Hunter: Inside the U.S. Navy’s Autonomous Submarine Tracking Vessel.” *Naval Technology*, May 3, 2018. [https://www.naval-technology.com/features/sea-hunter-inside-us-navys-autonomous-submarine-tracking-vessel/](https://www.naval-technology.com/features/sea-hunter-inside-us-navys-autonomous-submarine-tracking-vessel/).

United Nations Conference on Trade and Development, *Review of Maritime Transport 2018*. New York: United Nations, 2018. [https://unctad.org/en/pages/PublicationWebflyer.aspx?publicationid=2245](https://unctad.org/en/pages/PublicationWebflyer.aspx?publicationid=2245).

U.S. Army. *U.S. Army Robotic and Autonomous Systems*. Ft. Eustis, VA: U.S. Army Training and Doctrine Command, 2019. [https://www.tradoc.army.mil/Portals/14/Documents/RAS\_Strategy.pdf](https://www.tradoc.army.mil/Portals/14/Documents/RAS_Strategy.pdf).

———, Futures and Concepts Center, Future Warfare Division. *Future Study Plan 2019 Operationalizing Artificial Intelligence for Multi-Domain Operations*. August 27, 2019.

U.S. Coast Guard. *Maritime Commerce Strategic Outlook*. Washington, DC: U.S. Coast Guard, 2018. [https://media.defense.gov/2018/Oct/05/2002049100/-1/-1/1/USCG%20MARITIME%20COMMERCE%20STRATEGIC%20OUTLOOK-RELEASABLE.PDF](https://media.defense.gov/2018/Oct/05/2002049100/-1/-1/1/USCG%20MARITIME%20COMMERCE%20STRATEGIC%20OUTLOOK-RELEASABLE.PDF).

U.S. Congress, Select Committee on Intelligence. Annual Threat Assessment—Opening Statement by The Honorable Dan Coats, Director of National Intelligence. 116th Cong., 1st sess., January 29, 2019. [https://www.dni.gov/index.php/newsroom/congressional-testimonies/item/1949-dni-coats-opening-statement-on-the-2019-worldwide-threat-assessment-of-the-us-intelligence-community](https://www.dni.gov/index.php/newsroom/congressional-testimonies/item/1949-dni-coats-opening-statement-on-the-2019-worldwide-threat-assessment-of-the-us-intelligence-community).

U.S. Congress, Senate Armed Services Committee. Advance Policy Questions for VADM Michael M. Gilday, USN, Nominee for Appointment to be Chief of Naval Operations Duties and Responsibilities. 116th Cong., 1st sess., July 31, 2019 [https://www.armed-services.senate.gov/imo/media/doc/Gilday\_APQs\_07-31-19.pdf](https://www.armed-services.senate.gov/imo/media/doc/Gilday_APQs_07-31-19.pdf).

U. S. Department of Defense. *Annual Report to Congress: Military and Security Developments Involving the People’s Republic of China 2019*. [https://media.defense.gov/2019/May/02/2002127082/-1/-1/1/2019\_CHINA\_MILITARY\_POWER\_REPORT.pdf](https://media.defense.gov/2019/May/02/2002127082/-1/-1/1/2019_CHINA_MILITARY_POWER_REPORT.pdf).

———. *Comprehensive Selected Acquisition Reports for the Annual 2018 Reporting Requirement as Updated by the President’s Fiscal Year 2020 Budget*, March 11, 2019. [https://media.defense.gov/2019/Aug/01/2002165676/-1/-1/1/DEPARTMENT-OF-DEFENSE-SELECTED-ACQUISITION-REPORTS-(SARS)-DECEMBER-2018.PDF](https://media.defense.gov/2019/Aug/01/2002165676/-1/-1/1/DEPARTMENT-OF-DEFENSE-SELECTED-ACQUISITION-REPORTS-\(SARS\)-DECEMBER-2018.PDF).

———. Directive 3000.09, “Autonomy in Weapon Systems,” November 21, 2012, updated May 8, 2017. [https://www.esd.whs.mil/Portals/54/Documents/DD/issuances/dodd/300009p.pdf](https://www.esd.whs.mil/Portals/54/Documents/DD/issuances/dodd/300009p.pdf).

———. *Quadrennial Defense Review Report*, February 6, 2006. [https://archive.defense.gov/pubs/pdfs/QDR20060203.pdf](https://archive.defense.gov/pubs/pdfs/QDR20060203.pdf).

———. *Report of the Quadrennial Defense Review 1997*. Washington, DC:Department of Defense, 1997. [http://www.dod.gov/pubs/qdr/sec7.html](http://www.dod.gov/pubs/qdr/sec7.html).

———. *Selected Acquisition Report (SAR): MQ-4C Triton Unmanned Aircraft System (as of FY2019 President’s Budget*), December 2017. [https://www.esd.whs.mil/Portals/54/Documents/FOID/Reading%20Room/Selected\_Acquisition\_Reports/18-F-1016\_DOC\_68\_Navy\_MQ-4C\_Triton\_SAR\_Dec\_2017.pdf](https://www.esd.whs.mil/Portals/54/Documents/FOID/Reading%20Room/Selected_Acquisition_Reports/18-F-1016_DOC_68_Navy_MQ-4C_Triton_SAR_Dec_2017.pdf).

——. *Summary of the Department of Defense Artificial Intelligence Strategy: Harnessing AI to Advance Our Security and Prosperity*. [https://media.defense.gov/2019/Feb/12/2002088963/-1/-1/1/SUMMARY-OF-DOD-AI-STRATEGY.PDF](https://media.defense.gov/2019/Feb/12/2002088963/-1/-1/1/SUMMARY-OF-DOD-AI-STRATEGY.PDF).

———. “Warfighting Lab Incentive Fund, Project Proposal Solicitation.” *Defense Innovation Marketplace*. [https://defenseinnovationmarketplace.dtic.mil/business-opportunities/warfighting-lab-incentive-fund/](https://defenseinnovationmarketplace.dtic.mil/business-opportunities/warfighting-lab-incentive-fund/).

U.S. Department of Defense, Joint Chiefs of Staff (J39). *AI, China, Russia, and the Global Order: Technological, Political, Global, and Creative Perspectives*, ed. by Nicholas D. Wright. Washington, DC: Department of Defense, December 2018. [https://nsiteam.com/social/wp-content/uploads/2018/12/AI-China-Russia-Global-WP\_FINAL.pdf](https://nsiteam.com/social/wp-content/uploads/2018/12/AI-China-Russia-Global-WP_FINAL.pdf).

U.S. Department of Defense, Office of General Counsel. *Department of Defense Law of War Manual*, June 2015. [https://dod.defense.gov/Portals/1/Documents/law\_war\_manual15.pdf](https://dod.defense.gov/Portals/1/Documents/law_war_manual15.pdf).

U.S. Marine Corps. Fleet Marine Force Manual 1, *Warfighting*. Washington, DC: HQMC, 1989, revised 1997. [https://www.marines.mil/Portals/1/Publications/MCDP%201%20Warfighting.pdf](https://www.marines.mil/Portals/1/Publications/MCDP%201%20Warfighting.pdf).

U.S. Navy. *Surface Force Strategy: Return to Sea Control*, 2017. [https://www.public.navy.mil/surfor/Documents/Surface\_Forces\_Strategy.pdf](https://www.public.navy.mil/surfor/Documents/Surface_Forces_Strategy.pdf).

U.S. Navy, Submarine Force Pacific Command. Web site for Unmanned Under sea Vehicles Squadron One (UUVRON-1). [https://www.csp.navy.mil/csds5/Detachments/Detachment-Unmanned-Undersea-Vehicles/](https://www.csp.navy.mil/csds5/Detachments/Detachment-Unmanned-Undersea-Vehicles/).

U.S. Secretary of Defense. Memorandum, “Subject: The Defense Innovation Initiative.” November 15, 2014. [https://archive.defense.gov/pubs/OSD013411-14.pdf](https://archive.defense.gov/pubs/OSD013411-14.pdf).

———. Memorandum, “Subject: Long Range Research and Development Plan (LRRDP) Direction and Tasking.” October 29, 2014. [https://defenseinnovationmarketplace.dtic.mil/wp-content/uploads/2018/02/LRRDP\_DirectionandTaskingMemoClean.pdf](https://defenseinnovationmarketplace.dtic.mil/wp-content/uploads/2018/02/LRRDP_DirectionandTaskingMemoClean.pdf).

———. *Summary of the 2018 National Defense Strategy of the United States of America*, 2018. [https://dod.defense.gov/Portals/1/Documents/pubs/2018-National-Defense-Strategy-Summary.pdf](https://dod.defense.gov/Portals/1/Documents/pubs/2018-National-Defense-Strategy-Summary.pdf).

“Using the Force.” *The Economist*, July 18, 2019. [https://www.economist.com/briefing/2019/07/18/attacking-satellites-is-increasingly-attractive-and-dangerous](https://www.economist.com/briefing/2019/07/18/attacking-satellites-is-increasingly-attractive-and-dangerous).

Vandiver, John. “Promotion Rates Improving for Air Force Drone Pilots, GAO Says.” *Stars and Stripes*, February 8, 2019. [https://www.stripes.com/news/promotion-rates-improving-for-air-force-drone-pilots-gao-says-1.567839](https://www.stripes.com/news/promotion-rates-improving-for-air-force-drone-pilots-gao-says-1.567839).

Vincent, Brandi. “How the CIA Is Working to Ethically Deploy Artificial Intelligence.” *NextGov*, May 31, 2019. [https://www.nextgov.com/emerging-tech/2019/05/how-cia-working-ethically-deploy-artificial-intelli](https://www.nextgov.com/emerging-tech/2019/05/how-cia-working-ethically-deploy-artificial-intelli) gence/157395/.

Vincent, James. “Putin Says the Nation that Leads in AI ‘Will Be the Ruler of the World’.” *The Verge*, September 4, 2017. [https://www.theverge.com/2017/9/4/16251226/russia-ai-putin-rule-the-world](https://www.theverge.com/2017/9/4/16251226/russia-ai-putin-rule-the-world).

Vogel, Steven. “Marx and Alienation from Nature.” *Social Theory and Practice* 14, no. 3 (1988): 367–87. [http://www.jstor.org/stable/23557052](http://www.jstor.org/stable/23557052).

von Hippel, Eric. “Democratizing Innovation: The Evolving Phenomenon of User Innovation.” *Journal für Betriebswirtschaft* 55, no. 1 (2005): 63–78.

Wakabayashi, Daisuke, and Scott Shane. “Google Will Not Renew Pentagon Contract That Upset Employees.” *New York Times*, June 1, 2018. [https://www.nytimes.com/2018/06/01/technology/google-pentagon-project-maven.html](https://www.nytimes.com/2018/06/01/technology/google-pentagon-project-maven.html).

Walan, Alexander M. G. “Anti-Submarine Warfare (ASW) Continuous Trail Unmanned Vessel (ACTUV).” DARPA Web site. [https://www.darpa.mil/program/anti-submarine-warfare-continuous-trail-unmanned-vessel](https://www.darpa.mil/program/anti-submarine-warfare-continuous-trail-unmanned-vessel).

Waldrop, M. Mitchell. *Complexity: The Emerging Science at the Edge of Order and Chaos*. New York: Simon and Schuster, 1992.

Walters, Greg. “Artificial Intelligence Is Poised to Revolutionize Warfare.” *Seeker*, September 6, 2017. [https://www.seeker.com/tech/artificial-intelligence/artificial-intelligence-is-poised-to-revolutionize-warfare](https://www.seeker.com/tech/artificial-intelligence/artificial-intelligence-is-poised-to-revolutionize-warfare).

Waltz, Kenneth N. *Theory of International Politics*. Reading, MA: Addison-Wesley, 1979.

Wang, James. “How Much Intelligence Does IBM Watson Have?” *Ark Invest*, July 12, 2017. [https://ark-invest.com/research/ibm-watson](https://ark-invest.com/research/ibm-watson).

Warner, Oliver. *Command at Sea: Great Fighting Admirals from Hawke to Nimitz*. New York: St. Martin’s Press, 1976.

Watts, Barry D. *The Maturing Revolution in Military Affairs*. Washington, DC: Center for Strategic and Budgetary Assessments, 2011. [https://csbaonline.org/uploads/documents/2011.06.02-Maturing-Revolution-In-Military-Affairs1.pdf](https://csbaonline.org/uploads/documents/2011.06.02-Maturing-Revolution-In-Military-Affairs1.pdf).

Webb, Amy. “China Is Leading in Artificial Intelligence—and American Businesses Should Take Note.” *Inc*., September 2018. [https://www.inc.com/magazine/201809/amy-webb/china-artificial-intelligence.html](https://www.inc.com/magazine/201809/amy-webb/china-artificial-intelligence.html).

Weisgerber, Marcus. “The Pentagon’s New Algorithmic Warfare Cells Gets Its First Mission: Hunt ISIS.” *Defense One*, May 14, 2017. [https://www.defenseone.com/technology/2017/05/pentagons-new-algorithmic-war](https://www.defenseone.com/technology/2017/05/pentagons-new-algorithmic-war) fare-cell-gets-its-first-mission-hunt-isis/137833/.

Werner, Ben. “Navy Awards Boeing $43 Million to Build Four Orca XLUUVs.” *USNI News*, February 13, 2019. [https://news.usni.org/2019/02/13/41119](https://news.usni.org/2019/02/13/41119).

———. “Pentagon Falling Behind in Using Artificial Intelligence on the Battlefield.” *USNI News*, October 22, 2019. [https://news.usni.org/2019/10/22/pentagon-falling-behind-in-using-artificial-intelligence-on-the-battlefield](https://news.usni.org/2019/10/22/pentagon-falling-behind-in-using-artificial-intelligence-on-the-battlefield).

Whaley, Barton. *Stratagem: Deception and Surprise in War*. Norwood, MA: ARTECH House, 2007.

White, D., and Donald Sofge, eds. *Handbook of Intelligent Control Neural, Fuzzy, and Adaptive Approaches*. New York: Van Nostrand Reinhold, 1992.

The White House. *National Security Strategy of the United States of America*. December 2017. [https://www.whitehouse.gov/wp-content/uploads/2017/12/NSS-Final-12-18-2017-0905.pdf](https://www.whitehouse.gov/wp-content/uploads/2017/12/NSS-Final-12-18-2017-0905.pdf).

“‘Whoever Leads in AI Will Rule the World’: Putin to Russian Children on Knowledge Day.” *RT*, September 1, 2017. [https://www.rt.com/news/401731-ai-rule-world-putin/](https://www.rt.com/news/401731-ai-rule-world-putin/).

Wilamowski, B. M., et al. “Big Data and Deep Learning.” Paper presented at the 2016 IEEE 20th Jubilee International Conference on Intelligent Engineering Systems, June 30–July 2, 2016.

Wiley, Richard G. *ELINT: The Interception and Analysis of Radar Signals*. Boston: ARTECH House, 2006.

Willard, Lee, and Greg Klesch. *Using Integrated Mechanical Diagnostics Health and Usage Management System (IMD-HUMS) Data to Predict UH-60L Electrical Generator Condition*. Master’s thesis, Naval Postgraduate School, March 2006. [https://apps.dtic.mil/dtic/tr/fulltext/u2/a445430.pdf](https://apps.dtic.mil/dtic/tr/fulltext/u2/a445430.pdf).

Willard, Robert. “Rediscover the Art of Command and Control.” U. S. Naval Institute *Proceedings* 128, no. 10 (October 2002): 52–54.

Wilson, Mark. “The World’s Most-Advanced AI Can’t Tell What’s in These Photos. Can You?” *Fast Company*, July 22, 2019. [www.fastcompany.com/90379047/the-worlds-most-advanced-ai-cant-tell-whats-in-these-photos-can-you](http://www.fastcompany.com/90379047/the-worlds-most-advanced-ai-cant-tell-whats-in-these-photos-can-you).

Winner, Langdon. *Autonomous Technology: Technics-out-of-Control as a Theme in Political Thought*. Cambridge, MA: MIT Press, 1978.

*WIPO Technology Trends 2019: Artificial Intelligence*. World Intellectual Property Organization, 2019. [https://www.wipo.int/edocs/pubdocs/en/wipo\_pub\_1055.pdf](https://www.wipo.int/edocs/pubdocs/en/wipo_pub_1055.pdf).

Wong, Leah, et. al. “Command World.” Proceedings of the 2006 Command and Control Research and Technology Symposium. [http://dodccrp.org/events/2006\_CCRTS/html/papers/142.pdf](http://dodccrp.org/events/2006_CCRTS/html/papers/142.pdf).

Woolf, Amy F. *Russia’s Nuclear Weapons: Doctrine, Forces, and Modernization*, R45861. Washington, DC: Congressional Research Service, August 5, 2019. [https://fas.org/sgp/crs/nuke/R45861.pdf](https://fas.org/sgp/crs/nuke/R45861.pdf).

Work, Robert O. Memorandum, “Establishment of an Algorithmic Warfare Cross-Functional Team (Project Maven),” April 26, 2017.

Work, Robert O., and Greg Grant. *Beating the Americans at their Own Game: An Offset Strategy with Chinese Characteristics*. Washington, DC: Center for a New American Security, June 6, 2019. [https://www.cnas.org/publications/reports/beating-the-americans-at-their-own-game](https://www.cnas.org/publications/reports/beating-the-americans-at-their-own-game).

Wyatt, Todd, and Donald Brutzman. “Network Optional Warfare.” *NPS Wiki*, May 3, 2018. [https://wiki.nps.edu/display/NOW/Network+Optional+Warfare](https://wiki.nps.edu/display/NOW/Network+Optional+Warfare).

Wylie, J. C. *Military Strategy: A General Theory of Power Control*. New Brunswick, NJ: Rutgers University Press, 1967.

Wyne, Ali. “Can America Remain Number One?” *National Interest*, February 18, 2019. [https://nationalinterest.org/feature/can-america-remain-number-one-44627?page=0%2C2](https://nationalinterest.org/feature/can-america-remain-number-one-44627?page=0%2C2).

Younger, Sir Alex. “Fourth Generation Espionage—Fusing Traditional Skills with Innovation.” Remarks at St. Andrews University, December 3, 2018. [https://www.sis.gov.uk/media/1186/st-andrews-university-speech-dec-2018.docx](https://www.sis.gov.uk/media/1186/st-andrews-university-speech-dec-2018.docx).

Yu, Eileen. “Huawei Unleashes AI Chip, Touting More Compute Power Than Competitors.” *ZDNet*, August 23, 2019. [https://www.zdnet.com/article/huawei-unleashes-ai-chip-touting-more-compute-power-than-competitors/](https://www.zdnet.com/article/huawei-unleashes-ai-chip-touting-more-compute-power-than-competitors/).

Zhen, Liu. “China Takes Step Towards Precision Warheads for Unstoppable Nuclear Weapon, State Media Says.” *South China Morning Post*, September 29, 2018. [https://www.scmp.com/news/china/military/article/2166298/china-takes-step-towards-precision-warheads-unstoppable-nuclear](https://www.scmp.com/news/china/military/article/2166298/china-takes-step-towards-precision-warheads-unstoppable-nuclear).

Zhou, Jianlong, et al. “Transparent Machine Learning—Revealing Internal States of Machine Learning.” *Proceedings of IUI2013 Workshop on Interactive Machine Learning*. [https://csjzhou.github.io/homepage/papers/iui2013\_transparent\_ml\_camera.pdf](https://csjzhou.github.io/homepage/papers/iui2013_transparent_ml_camera.pdf).

Zhu, Chen, et al. “Transferable Clean-Label Poisoning Attacks on Deep Neural Nets.” *Proceedings of the 36th International Conference on Machine Learning*, 2019. [https://www.usna.edu/Users/cs/taylor/pubs/icml19.pdf](https://www.usna.edu/Users/cs/taylor/pubs/icml19.pdf).

# **ABOUT THE CONTRIBUTORS**

## Editors

**George Galdorisi** is the Director of Strategic Assessments and Technical Futures at the Naval Information Warfare Center Pacific, where much of his work is focused on the operational uses of big data, artificial intelligence, and machine learning. Prior to joining the center, he completed a thirty-year career as a naval aviator, culminating in fourteen years of consecutive service as executive officer, commanding officer, commodore, and chief of staff. His last operational assignment spanned five years as chief of staff for Cruiser-Destroyer Group Three embarked in USS *Carl Vinson* and USS *Abraham Lincoln*. During this assignment, he also led the U.S. delegation for military-to-military talks with the People’s Liberation Army Navy. He has written a number of novels and nonfiction works, as well as articles in professional journals, including the U.S. Naval Institute *Proceedings* prize-winning article, “The Navy Needs AI: It’s Just Not Certain Why.” Other than writing, he enjoys connecting with readers via his website: [www.georgegaldorisi.com](http://www.georgegaldorisi.com).

**Sam J. Tangredi** is the Leidos Chair of Future Warfare Studies, director of the Institute for Future Warfare Studies, and professor of national, naval, and maritime strategy at the U.S. Naval War College. A U.S. Naval Academy and Naval Postgraduate School graduate, he earned a PhD in international relations from the University of Southern California. He served a thirty-year naval career as a surface warfare officer culminating as commanding officer of USS *Harpers Ferry* (LSD 49). Ashore, he served as a strategic planner and leader of strategic planning teams as head, Strategy and Concepts Branch (N513) of the Chief of Naval Operations staff and director of Strategic Planning and Business Development of the Navy International Programs Office. He also served as speechwriter and special assistant to the Secretary of the Navy, defense resources manager on the Joint Staff, and U.S. Defense Attaché to the Hellenic Republic of Greece. He has published 5 books and more than 150 articles and has earned 14 professional literature awards, including the U.S. Naval Institute’s Arleigh Burke Prize and the U.S. Navy League’s Alfred Thayer Mahan Award. He can be contacted via his website: [www.samjtangredi.com](http://www.samjtangredi.com).

## Contributors

**Capt. Adam M. Aycock, USN** (**Ret**.), was most recently a researcher in the Institute for Future Warfare Studies in the Center for Naval Warfare Studies of the U.S. Naval War College. Among other subjects, he studied the autonomy and safeguards necessary for the control of future unmanned systems. A career surface warfare officer, he held four commands at sea: as rotational commanding officer of USS *Gladiator* (MCM 11) and USS *Sentry* (MCM 3), USS *Mahan* (DDG 72), Afloat Training Group, Mayport, Florida, and USS *Shiloh* (CG 67). He served ashore in the Bureau of Personnel and on the Joint Staff as the maritime operational threat response expert in the Anti-Terrorism/Homeland Defense Division. Captain Aycock is a U. S. Naval Academy graduate and earned a master’s in military studies from the U.S. Marine Corps Command and Staff College.

**William Bray** serves as the Deputy Assistant Secretary of the Navy for Research, Development, Test, and Evaluation (DASN \[RDT&E\]) under the Assistant Secretary of the Navy for Research, Development, and Acquisition. He is responsible for executive oversight of all matters related to RDT&E budget activities, science and engineering, advanced research and development, prototyping and experimentation, and test and evaluation. As DASN (RDT&E), he is also responsible for oversight and stewardship of the Department of the Navy research and development establishment, including naval laboratories, warfare centers, and systems centers. Mr. Bray previously served as the executive director, Program Executive Office for Integrated Warfare Systems (PEO IWS); director of integrated nuclear weapons safety and security (SP30) in the Navy Strategic Systems Programs Office; and director, Integrated Combat Systems for PEO IWS, where he was the major program manager for surface Navy combat systems. He started his civil service career at the Naval Surface Warfare Center, Corona Division, California. Mr. Bray earned a bachelor of science in engineering from Pennsylvania State University and a master of science in systems management from the University of Southern California. He has been awarded the Department of the Navy’s Superior Civilian Service Award.

**Rear Adm. Nevin Carr, USN** (**Ret**.), is currently vice president and U.S. Navy strategic account executive for the global science and technology company Leidos. He is also a director of the Association for Unmanned Vehicle Systems International. Prior to joining Leidos, he was a Senior Advisor with McKinsey and Co., and a Distinguished Visiting Scholar at Stanford University. Rear Admiral Carr retired from the U.S. Navy following a thirty-four-year career, which included command of USS *Arleigh Burke* (DDG 51) and USS *Cape St. George* (CG 71). His shore duty assignments focused on ship combat systems and sea-based ballistic missile defense. On the Chief of Naval Operations staff, he served as deputy director of surface warfare for combat systems. Appointed Deputy Assistant Secretary of the Navy for International Programs, Rear Admiral Carr built international partnerships through training, cooperative development, and foreign military sales. His capstone assignment was as chief of naval research, where he led four thousand talented scientists and engineers executing the Navy’s $2 billion science and technology effort. He worked closely with industry, academia, and international partners to develop such emerging technologies as directed energy, autonomous systems, electromagnetic spectrum dominance, and the electromagnetic rail gun. He earned a bachelor’s degree in naval architecture from the U.S. Naval Academy and a master’s degree in operations research from the Naval Postgraduate School.

**José Carreño** is a senior analyst and the head of the Strategy and Decision Support Branch at Naval Information Warfare Center (NIWC) Pacific. His career in government service began under the auspices of the Office of Naval Research’s internship program, where he was assigned to NIWC Pacific. Following completion of his graduate degree, he joined NIWC Pacific as an operations research analyst. He was subsequently selected to lead the Strategy and Decision Support Branch, responsible for the development, management, and execution of the NIWC strategy, as well as all associated research and analysis. He also serves as the associate technical project officer for Chile, responsible for the information exchange agreement on command, control, communications, and computers between the U. S. and Chilean navies. Mr. Carreño completed his undergraduate studies at the University of California, Berkeley, and holds a master’s degree in Pacific international affairs from the University of California, San Diego, and a master’s in systems analysis from the Naval Postgraduate School.

**Dr. Nathanael Chambers** is an associate professor in the computer science department at the U.S. Naval Academy (USNA). He is also the co-director of the USNA Center for High Performance Computing. His research centers on natural language processing, applying machine learning to extract information from written text. The goal of his efforts is to enable deeper artificial intelligence reasoning by interpreting the information conveyed through human languages through unsupervised learning. Additionally, he investigates new methods for information extraction to better understand large amounts of text, and models time—when events start, how long they last, and the order in which they occur. During his nine years at USNA, he has published research papers with more than a dozen midshipmen co-authors. He also received the Class of 1951 Civilian Faculty Excellence in Research Award in 2020. He is a graduate of the University of Rochester and earned a PhD in computer science from Stanford University in 2011. He joined the faculty at USNA shortly after completion of his studies.

**Bryan Clark** is a senior fellow and director of the Center for Defense Concepts and Technology at Hudson Institute. His areas of research include naval operations, electronic warfare, autonomous systems, military competitions, and wargaming. From 2013 to 2019, he was a senior fellow at the Center for Strategic and Budgetary Assessments (CSBA), where he led studies for the Department of Defense Office of Net Assessment, Office of the Secretary of Defense, and Defense Advanced Research Products Agency on new technologies and the future of warfare. Prior to joining CSBA in 2013, he served as special assistant to the Chief of Naval Operations and director of his Commander’s Action Group, where he led development of Navy strategy and implemented new initiatives in electromagnetic spectrum operations, undersea warfare, expeditionary operations, and personnel and readiness management. Additionally, he served in the Navy headquarters staff from 2004 to 2011, leading studies in the Assessment Division and participating in the 2006 and 2010 Quadrennial Defense Reviews. Prior to retiring from the Navy in 2008, Mr. Clark was an enlisted and officer submariner, serving in afloat and ashore submarine operational and training assignments including tours as chief engineer and operations officer at the Navy’s nuclear power training unit.

**Lt. Cdr. Charles R. Clark, USN**, is an SH-60B/R naval aviator and qualified operations analyst and currently serves in the Office of the Chief of Naval Operations Assessment Division (OPNAV N81), where he conducts analysis of future fleet requirements. Lieutenant Commander Clark completed numerous operational deployments during seventeen years of service. His assignments included Helicopter Anti-Submarine Squadron Light 51 (HSL-51), USS *Boxer* (LHD 4), Helicopter Maritime Strike Squadron 49 (HSM-49), and Naval Forces, U.S. Central Command in Bahrain. During those assignments, he participated in operations throughout the Western Pacific, Arabian Sea, and Eastern Pacific. On shore duty, he served as an MH-60R flight instructor with Helicopter Maritime Strike Squadron 41 (HSM-41). He is a graduate of the U.S. Naval Academy with a bachelor of science in computer science, and he earned a master’s degree in operations research and a certificate in scientific computation from the Naval Postgraduate School, where he was awarded the Chief of Naval Operations Award for Excellence in Operations Research. He also holds an executive master of business administration degree.

**Dr. Frederick L. Crabbe** is a professor in the computer science department at the U. S. Naval Academy, where he teaches in the area of intelligent robotics. In his nineteen-year career at the academy, his research has focused on the intersection between artificial intelligence and robotic or similar agents. In particular, he has examined social learning between agents, either through observation, collaboration, or various forms of explicit teaching. Professor Crabbe earned a bachelor of arts in computer science modified with philosophy from Dartmouth College in 1992, including an exchange with the University of Edinburgh, and a PhD in computer science from the University of California, Los Angeles, in 2000. His defense research interests include developing autonomous agents that support infantry squads, and the application of artificial intelligence techniques to the development of better tactics in aerial drone swarms.

**Dr. Chris C. Demchak** is the Rear Admiral Grace M. Hopper Chair of Cyber Security and Senior Cyber Scholar of the Cyber and Innovation Policy Institute in the Center for Naval Warfare Studies at the U.S. Naval War College. She was previously co-founder and director of the Center for Cyber Conflict Studies. With engineering, economics, comparative complex organization theory, and political science degrees from Princeton University and the University of California, Berkeley, she served as an intelligence officer in the U.S. Army and taught at West Point and the University of Arizona. She also studied LISP programming, used as the original computer program for artificial intelligence research. Dr. Demchak is the developer of such concepts as cybered conflict (as opposed to cyber conflict), a “Cyber Westphalia” of competitive socio-technical-economic systems, and a Cyber Operational Resilience Alliance. In addition to many published articles, her books include *Military Organizations, Complex Machines* (1991), *Designing Resilience* (coeditor, 2010), and *Wars of Disruption and Resilience* (2011). She is a past chair of the international security section of the American Political Science Association. Her current projects include “Cyber Westphalia: Redrawing International Economics, Conflict, and Global Structures,” and “Cyber Command: Understanding Varying Models as National Cyber Defense Experiments.”

**Professor William G. Glenney IV** is a research professor in the Institute for Future Warfare Studies (IFWS) of the U. S. Naval War College and was its founding director. His research efforts include identifying future warfare trends and defining roles and missions for future naval forces. He also manages international cooperation with partner institutions for IFWS. For eighteen years, he was the deputy director of the Chief of Naval Operations strategic studies group, guiding the group in the study of strategy and in the development of innovative naval warfare concepts addressing high-level wicked challenges with no apparent solutions. An honors graduate in mechanical engineering from the U. S. Naval Academy, Professor Glenney served for ten years on active duty in the nuclear propulsion program and submarine force, followed by twenty years in the Naval Reserve, retiring as captain after four tours as commanding officer. Prior to joining the strategic studies group, he worked at Sonalysts, a high-technology firm working principally on submarine real-world operations and intelligence matters.

**Dr. Stephanie Hszieh** is a senior strategy analyst at the U. S. Navy Naval Information Warfare Center (NIWC) Pacific in San Diego. As an analyst, Dr. Hszieh informs and supports NIWC Pacific’s efforts in strategic planning and survey management. She also manages NIWC Pacific’s strategic management process and advises senior leaders on the implementation of the center’s strategy. She has authored numerous publications on networking the global maritime partnership. She also co-authored *Networking the Global Maritime Partnership*, published by the Sea Power Centre of the Royal Australian Navy. She holds a PhD in political science from the University of Southern California.

**Dr. Nina Kollars** is associate professor in the Cyber and Innovation Policy Institute at the U.S. Naval War College. Her research investigates the security implications of the intersection of emerging technology, humans, and organizations, with emphasis on the role of practitioners in driving innovation. Her early work traced the innovative tinkering of U.S. soldiers during war and the U.S. Army’s capacity to harness that creativity. Her current work takes the same “bottom-up” analytical approach to cyber security. Dr. Kollars has studied and worked with the “white hat” computer hacking community for the past several years and is preparing a book manuscript revealing the national security contributions of white hat hackers to the United States. Prior to her PhD studies, Kollars was a researcher at diverse institutions including the DuBois Institute at Harvard University, the Federal Research Division of the Library of Congress, and the World Bank. She has lectured to national leaders and scholars on innovative cyber security and innovation, including at the Sloan School of Business at the Massachusetts Institute of Technology, the National Security Council, and the Army Capabilities and Integration Center. She holds a master’s degree from George Washington University and a PhD in political science from The Ohio State University.

**Dr. Albert K. Legaspi** is senior engineer for tactical and enterprise networks at the Naval Information Warfare Center, Pacific; serves as the science, technology, and engineering expert for Navy networks; and chairs the coalition network for secure information sharing. Previously, he served as the competency lead for network centric engineering and integration. He led engineering efforts in system-of-system modeling and simulation, for the joint information environment, for shipboard antenna design and analyses, and for global positioning systems. The former head of the network division, he continues to serve as the Navy’s technical area expert in networking. For the deputy chief of naval operations for information warfare (OPNAV N6), Dr. Legaspi served as the head of the Network Centric Warfare Analysis Branch, as deputy director of the Navy Modeling and Simulation Office, and as the Navy’s representative to the Joint Chief of Staff’s Network Warfare Simulation program. He earned double bachelor’s degrees in mathematics and system engineering from the University of California, Los Angeles, and earned his master’s and PhD in electrical engineering from the University of California, San Diego. He has been awarded the Department of the Navy Meritorious Civilian Service Award.

**Dr. Doug Lange** is the distinguished scientist for machine learning (ML) and artificial intelligence (AI) at the Naval Information Warfare Center, Pacific. He began working on the development of command and control systems in 1983 after getting a bachelor of science degree in computer science and mathematics from the University of California, Davis. Subsequently, he earned a master’s degree and PhD from the Naval Postgraduate School. Dr. Lange has served on the staff of the Commander Seventh Fleet as a command, control, communications, and intelligence advisor and has led the engineering efforts of ashore and afloat systems. Participating in the Defense Advanced Research Projects Agency Personalized Assistant that Learns program, Dr. Lange began to bring ML into the AI research occurring at the center and has worked through several projects to grow the center’s efforts to bring ML and AI into naval command, control, communications, computers, intelligence, surveillance, and reconnaissance systems.

**Jeffrey Mah** has served for more than thirty-three years as an engineer at the Naval Information Warfare Center Pacific. During his career, he has developed solutions and led teams addressing complex communications programs ranging from naval operational networks to classified National Geospatial-Intelligence Agency external communications requirements. He has been a critical participant in the center’s systems development and support, which includes basic research, prototype development, systems engineering, and integration to life cycle support of fielded communications systems. His work has included partnering with industry, academia, and other government and nongovernmental entities. He is a graduate of the University of California, San Diego.

**Lt. Cdr. Connor S. McLemore, USN**, is an E-2C Hawkeye naval flight officer and qualified operations analyst and currently serves in the Office of the Chief of Naval Operations Assessment Division (OPNAV N81), where he conducts analysis of future fleet requirements. He completed numerous operational deployments during nineteen years of service in the U.S. Navy. With the “Sun Kings” of Carrier Command and Control Squadron 116 (VAW-116), he deployed to the Persian Gulf and Gulf of Oman in support of Operations Southern Watch, Iraqi Freedom, and Enduring Freedom. He is a graduate of the U.S. Naval Academy and the U.S. Navy Fighter Weapons School (Top-gun), and he earned master’s degrees from the Naval War College and the Naval Postgraduate School, where his thesis was awarded the Military Operations Research Society’s Stephen A. Tisdale Graduate Research Award. In 2014 he returned to the Naval Postgraduate School as military assistant professor and the operations research program officer. During his tenure, he taught graduate-level programming courses and published two papers in highly ranked international scientific journals. He is co-author of the article “The Dawn of Artificial Intelligence in Naval Warfare” published on the public policy website *War on the Rocks*.

**Dr. Dale L. Moore** is Director, Strategy and Innovation, Office of the Deputy Assistant Secretary of the Navy for Research, Development, Test and Evaluation. He also serves as the lead for the Department of the Navy Thirty-Year Research and Development Plan. Dr. Moore has more than thirty-seven years of experience across a wide range of technical, management, and leadership activities supporting the U.S. Navy, the Department of Defense, and many affiliated community and academic institutions. Previously, he served as director, Strategic Initiative Coordination and Execution for the Naval Air Systems Command; as the assistant to the commander for strategic operations, Naval Air Warfare Center Aircraft Division; and as the chief systems engineer for the Navy’s Unmanned Combat Air System. Dr. Moore holds a doctorate from George Washington University in human and organizational learning, leadership and change, a master’s degree with distinction in product development from the Naval Postgraduate School, and a bachelor’s degree in mechanical engineering. He has twice received the Department of the Navy Meritorious Civilian Service Award, is a member of the Department of Defense acquisition program management community, and is level III–certified in acquisition program management and systems engineering.

**Michael O’Gara** is a recognized expert in tactical data links and became the Naval Information Warfare Command’s enterprise technical warrant holder for integrated fires. As such, he served as Naval Information Warfare Center Pacific lead for advancing integrated fires between all naval research and development centers, earning a reputation for successful collaboration across the Navy and Defense technical communities. Currently, Mr. O’Gara is detailed to the Pentagon to serve as the technical advisor to the Chief of Naval Operations (OPNAV) Digital Warfare Office where he focuses on the employment of AI by the Navy. He continues to champion cross-warfare center development of a persistent, distributed live, virtual, and constructive environment for test and experimentation. A native of San Diego, California, he graduated from the U.S. Naval Academy in 1984 and chose a career as a surface warfare officer. During his active-duty career, he made eight deployments to the Western Pacific, Indian Ocean, and Arabian Gulf, across seven sea tours that began on USS *Long Beach* (CGN 9) and ended on USS *John C. Stennis* (CVN 74). He has earned two graduate degrees from National University and an engineering certificate in model-based systems engineering from the Massachusetts Institute of Technology.

**Mark Owen** is the senior scientific technical manager for intelligence, surveillance, and reconnaissance at the Naval Information Warfare Center Pacific and the center’s first multi-intelligence and correlation technology lead. His group conducts research, development, and system fielding of advanced multi-intelligence fusion technologies in support of Department of the Navy/Department of Defense requirements and national intelligence community initiatives. This includes naval capabilities in distributed intelligence, surveillance, and reconnaissance data analytics and predictive intelligence. Previously he was the U.S. Navy lead of the five-nation Technical Cooperation Program, C3I Group, Technical Panel on Information Fusion, and has twenty-eight years of experience in the research and development of signal processing and data fusion technologies. He is the author or co-author of thirty papers on the subjects of data fusion, neural network tracking, multi-hypothesis tracking, and neural network control, and he provided significant contributions to the book *Concepts, Models and Tools for Information Fusion*. He received the Dr. Delores M. Etter Top Scientists and Engineers of the Year Award for exceptional scientific and engineering achievement and the SSC Pacific Galileo Award for excellence in S&T for automated radar modeling and characterization. Mr. Owen earned a bachelor’s and master’s degree in electrical engineering from California State University, Long Beach.

**Dr. Katie Rainey** is a scientist at the Naval Information Warfare Center Pacific, where she conducts research into the robustness of machine learning algorithms for Navy applications. Her recent focus includes algorithm development for analyzing imagery from multiple sources and sensors, particularly under ocean environmental conditions. She is also the general chair and co-founder of the workshop on naval applications of machine learning, the premier technical forum for machine learning research in the defense community, and is active in building the community of AI researchers among defense laboratories. Dr. Rainey, a San Diego native, studied math as an undergraduate at the University of California (UC), Berkeley, and as a graduate student at UC Irvine, and received her PhD in mathematics at UC Irvine in 2010.

**Adm. Michael S. Rogers, USN** (**Ret**.), is currently supporting multiple companies in the private sector as board member, senior advisor or venture partner. He is also an adjunct professor at Northwestern University Kellogg School of Management and speaks globally on issues of cyber security, technology, geopolitics and leadership. A naval cryptology officer, his last active-duty assignment was as the commander of United States Cyber Command (USCYBERCOM) and the National Security Agency, responsible for U.S. electronic and cyber intelligence and defense. He was the first of the then-new information warfare community officers to be promoted to the rank of admiral. During his tour, he helped elevate USCYBERCOM into a unified combatant command. Previously he had been commander, U.S. Tenth Fleet and Fleet Cyber Command. During his career, he also served as the head of intelligence for U. S. Pacific Command and the Joint Staff. He is a graduate of Auburn University, a distinguished graduate of the National War College and a graduate of highest distinction from the Naval War College. He is also an MIT Seminar XXI Fellow and a Harvard Senior Executive in National Security alumnus..

**Paul Scharre** is a senior fellow and director of the technology and national security program at the Center for a New American Security. He is the author of *Army of None: Autonomous Weapons and the Future of War*, which won the 2019 Colby Award and was named as one of Bill Gates’ top five books of 2018. From 2008 to 2013 Mr. Scharre worked in the Office of the Secretary of Defense (OSD) where he played a leading role in establishing policies on unmanned and autonomous systems and emerging weapons technologies. He led the Department of Defense working group that drafted Directive 3000.09, establishing the department’s policies on autonomy in weapon systems. He was appointed Special Assistant to the Under Secretary of Defense for Policy. Prior to joining OSD, Mr. Scharre served as a special operations reconnaissance team leader in the U.S. Army’s 3rd Ranger Battalion and completed multiple tours to Iraq and Afghanistan. Mr. Scharre has published numerous articles, testified before the House and Senate Armed Services Committees, and has presented at the United Nations. He holds a master of arts in political economy and public policy and a bachelor of science in physics, cum laude, both from Washington University in St. Louis.

**Harrison Schramm** is a senior fellow at the Center for Strategic and Budgetary Assessments, where he most recently led their study on “COVID-19: Analysis and Policy Implications.” He has contributed to studies on artificial intelligence, maritime logistics, and future naval forces. During his U.S. Navy career, he served as helicopter pilot, military assistant professor of operations research at the Naval Postgraduate School, and operations research analyst at the Pentagon. In addition to military awards including the Meritorious Service Medal and Air Medal, he was recognized by the Naval Helicopter Association as a member of the Aircrew of the Year. A leader in the operations research community, he is a past vice president of the Military Operations Research Society and has received numerous professional awards, including the Clayton Thomas award for distinguished service to the profession of operations research. His published work has appeared in *INTERFACES*, the *Journal of Applied Meteorology and Climatology, SIGNIFICANCE*, the *Journal of Mathematical Biosciences*, U.S. Naval Institute *Proceedings, OR/MS Today*, and *Military Operations Research*.

**Antonio P. Siordia** is a senior program manager with the intelligence, surveillance, and reconnaissance department at the Naval Information Warfare Center Pacific, where he leads several efforts within the autonomous systems division. Prior to this, he completed a detail assignment as a program manager at the Office of the Secretary of Defense Strategic Capabilities Office. Previous assignments include the Office of Naval Research science advisor to the commander, U.S. Seventh Fleet, embarked on USS *Blue Ridge*, and director’s fellow to the Chief of Naval Operations strategic studies group in Newport, RI. He holds graduate degrees from the University of California, San Diego, and the Naval Postgraduate School.

**Adm. James G. Stavridis, USN** (**Ret**.), is an operating executive advising the Carlyle Group’s executive team and investment professionals on geopolitical and national security issues. Previously, he served as dean of the Fletcher School of Law and Diplomacy at Tufts University. Admiral Stavridis was the first naval officer to serve as Supreme Allied Commander, North Atlantic Treaty Organization (NATO) and commander, U.S. European Command, leading the NATO alliance in global operations from 2009 to 2013. He also served as commander of U.S. Southern Command, with responsibility for military operations in Latin America from 2006 to 2009. In his thirty-five-year naval career, he commanded a destroyer, destroyer squadron, and carrier strike group—all serving in combat. He is a distinguished graduate of the U.S. Naval Academy and earned a master of arts in law and diplomacy and PhD in international relations from the Fletcher School. A prolific author on global security issues, Admiral Stavridis has published nine books and regularly writes for the *New York Times, Washington Post, Atlantic, Time, Naval War College Review*, and U.S. Naval Institute *Proceedings*. He is also chief international security analyst for NBC News.

**Dr. Patrick K. Sullivan** founded Oceanit Laboratories in 1985 as a self-funded research and development technology incubator that today employs more than 200 scientists, engineers, and professionals, providing innovative solutions in the fields of aerospace, engineering, information technology, and life sciences. Oceanit has created cutting-edge innovations in bio-photonics, neurotoxin detection, optics, missile defense technology, space debris management, children’s health, and environmental applications that are the subject of numerous reports and patents. Dr. Sullivan has extensive experience on boards and commissions, serving or having served on the national Ocean Research Advisory Panel (appointed by the Secretary of the Navy), Parker Ranch, High Technology Development Corporation, Rehabilitation Hospital of the Pacific, Nanopoint, and Hoana Medical. He has developed nationally focused research programs, including the National Defense Center of Excellence for Research in Ocean Sciences and the National Electric Vehicle Demonstration program, both collaborations with the Defense Advanced Research Projects Agency. He is the author of *Intellectual Anarchy: The Art of Disruptive Innovation*. He also serves as the honorary consul of Indonesia. Dr. Sullivan received his bachelor of science in engineering from the University of Colorado, Boulder, and his PhD in engineering from the University of Hawaii.

**Adm. Scott H. Swift, USN** (**Ret**.), is founder of The Swift Group LLC, former Massachusetts Institute of Technology Center for International Studies Robert E. Wilhelm Fellow, MIT Research Affiliate, Senior Fellow at the Center for Naval Analysis, Adjunct Professor at the Naval War College and board member of the U.S. Naval Institute. Former commander of the U.S. Pacific Fleet, Admiral Swift served for more than forty years as a naval aviator. His operational assignments include Attack Squadron 94 (VA-94); Attack Squadron 97 (VA-97); Carrier Air Wing 11 staff; commander, Strike Fighter Attack Squadron 97 (VFA-97); commander, Carrier Air Wing 14; deputy commander, Naval Forces, U.S. Central Command in Bahrain; commander, Carrier Strike Group (CSG) 9; and commander, U.S. 7th Fleet, Yokosuka, Japan. During those assignments, he participated in combat in Operations Praying Mantis, Southern Watch, Enduring Freedom, and Iraqi Freedom. His shore tour assignments include commander of Strike Fighter Weapons School, Pacific; F/A-18 requirements officer, Navy Staff (OPNAV); commander, Strike Fighter Attack Squadron 122 (VFA-122); staff of the Under Secretary of Defense for Acquisition, Technology and Logistics; director of operations, U. S. Pacific Command; and director, OPNAV. He is a graduate of San Diego State University and earned a master’s degree from the U. S. Naval War College.

**Dr. Gavin Taylor** is associate professor of computer science at the U. S. Naval Academy. He is an award-winning teacher and an active researcher in many areas of machine learning, including reinforcement learning, data poisoning, and the optimization of neural networks. His most recent writings have been on adversarial attacks against AI systems. He also co-directs the academy’s Center for High Performance Computing. His bachelor’s degree is in mathematics from Davidson College, and his master’s degree and PhD in computer science are from Duke University. He joined the USNA faculty immediately after completion of his studies. A recent online student review stated, “This guy could teach a rock how to program.”

**Rachel Volner** is a senior strategy analyst at the Naval Information Warfare Center Pacific, the Navy’s center of excellence for the development of command, control, communications, computers, intelligence, surveillance, and reconnaissance, cyber, and space-based capabilities, where her current focus is on strategic and technical forecasting. Prior to that, she earned a master’s degree in international affairs from the University of California, San Diego, with a regional emphasis on China and a concentration in public policy. In addition to strategic and technical forecasting, she concentrates her analysis on the security and economic developments in the Indo-Pacific region.

**The Honorable Robert O. Work** is currently Distinguished Senior Fellow for Defense and National Security at the Center for a New American Security (CNAS) and vice-chair of the Congressionally-mandated National Security Commission on Artificial Intelligence. Secretary Work previously served as the deputy secretary of defense, responsible for overseeing the day-to-day business of the Pentagon and developing the department’s $600 billion defense program. He is credited for his work on the third offset strategy, which aimed to restore U.S. conventional overmatch over potential adversaries. Prior to serving as deputy secretary, Secretary Work spent one year as chief executive officer of CNAS after serving as Undersecretary of the Navy from 2009 to 2013. Following a twenty-seven-year active-duty career in the U.S. Marine Corps, retiring as colonel, he was a senior fellow and vice president for strategic studies at the Center for Strategic and Budgetary Assessments. He was also an adjunct professor at George Washington University. Secretary Work received a bachelor of science from the University of Illinois at Champaign-Urbana, a master of science in systems management from the University of Southern California, a master of science in systems technology (space systems operations) from the Naval Postgraduate School, and a master in international public policy from the Johns Hopkins School of Advanced International Studies.

# **INDEX**

The index that appeared in the print version of this title was intentionally removed from the eBook. Please use the search function on your eReading device to search for terms of interest. For your reference, the terms that appear in the print index are listed below.

5G technology

101st Airborne Division

*2001: A Space Odyssey*

adaptive closed-loop control (ACLC); diagram

Advanced Capabilities and Deterrence Panel (ACDP)

adversarial attack; diagram

Afghanistan

AI Next

AI revolution, *See also* cognitive revolution

AI winter

aircraft carriers

Alberts, David

algorithm; and adversarial AI; as applied statistics; and autonomy; back-propagation; commercial; as commodity; in communications networks; confidence in; cooperative testing of; for creativity; and DARPA; and deception; emulating human intelligence; enabling battlefield innovation; and human performance; inference algorithms; for intuition; in machine learning; in Naval Academy education; at operational level of war; in pattern recognition; poor in explaining self; and security; in synchronization, *See also* algorithmic warfare; pattern recognition

algorithmic warfare

AlphaGo, *See also* iGo

American Artificial Intelligence Initiative

amphibious assault ships

analog systems

anthronoetic AI

anti-access/area denial

applied engineering, literature on

Aquinas, Thomas

Aristotle

Australia

autonomy; dangers and ethics of; human interaction; and potential opponents of U.S.; and strategy; and Third Offset; true promise of AI; unevenness in adopting, *See also* robotic warfare; robot/robotics

battle network; grid

Behavioral Learning for Adaptive Electronic Warfare, *See also* electronic warfare

Belyea, Lt. James, RCN

Bendett, Samuel

Berger, Gen. David, USMC

Berkeley, University of California

big data; AI, relationship to; and Five Eyes; and ISR; and learning curve function; and OODA loop; overwhelming networks validity of, *See also* data

biolinguistics, *See also* Chomsky, Noam

black box

Boot, Max

Bose-Einstein condensate

Boyd, Col. John, USAF, *See also* OODA (observe-orient-decide-act) loop

budget, Defense; Navy; R&D, *See also* future years defense plan (FYDP)

Burke, Adm. Arleigh, USN

C4ISR. *See* command, control, communications, computers, intelligence, surveillance, and reconnaissance (C4ISR); intelligence, surveillance, and reconnaissance (ISR)

Cambridge, University

camera, surveillance

Canada

Captor, Mk 60 mine, *See also* mine warfare

career paths

Carnegie Mellon University

Carter, Ashton, secretary of defense

Castelvecchi, Davide

Casti, John

Cebrowski, Arthur

Center for a New American Security (CNAS)

Center for Naval Analyses

Center for Strategic and Budgetary Assessments (CSBA)

chess

*Chicago*

China, Peoples Republic of (PRC); AI policies of, *See also* Chinese Communist Party (CCP); People’s Liberation Army (PLA); People’s Liberation Army Navy (PLAN)

China Mobile

Chinese Communist Party (CCP), *See also* China, People’s Republic of (PRC); People’s Liberation Army (PLA); People’s Liberation Army Navy (PLAN)

Chomsky, Noam

Clarke, Arthur C.

classification and regression tree

Clausewitz, Carl von

closed-end classification

Close-In Weapons System (CIWS)

coalition

Coats, Daniel R., director of national intelligence

cognitive revolution

cognitive science

Cold War; introduction of stealth; signals deception plan

combat air patrol (CAP)

combat information center (CIC)

combat medevac

command and control (C2), *See also* mission command

command, control, communications, computers, intelligence, surveillance, and reconnaissance (C4ISR), *See also* intelligence, surveillance, and reconnaissance (ISR)

commercial AI; accelerated development; collaboration with military; deception of; incentives of opponents; level of government control; limits to application for military operations; military leveraging; PRC domination over; U.S. incentive

commercial-of-the-shelf (COTS)

composite warfare commander (CWC)

concept drift

Congress, U.S.

Congressional Research Service

constructive AI

Copernicus architecture

Corbett, Sir Julian S.

courses of action (COA)

Crimea

crossing the T

cruise control

Cuban missile crisis

Cudworth, Ralph

culture; military; strategic

*Cushing*

cyberattacks, *See also* cybersecurity; deception

cybersecurity, data; access to clean data; affecting strategy; analytics; capture/collection; causal model; command and control; curve fitting; deception of; in fires process; hierarchy of; and IARPA; labeled; limits; operational insufficiency; partial; relationship to AI; from sensor grid; spurious correlations; uncertainty; unstructured text, *See also* big data; data exhaust; data science; data scientists; data-driven decisions; pattern recognition

data exhaust

data science

data scientists

data-driven decisions

Davis, Martin

deception; AI vulnerability to; expectation of

Deep Blue

deep learning/deep neural networks

DeepMind, *See also* Google

Defense Advanced Research Project Agency (DARPA)

defense innovation initiative (DII)

Defense Science Board

*Department of Defense AI Strategy 2018*

Department of Defense HighPerformance Computing Modernization Program

*Design for Maintaining Maritime Superiority, A*

development operations (DevOps)

distributed maritime operations (DMO)

Doc2Vec

doctrine

domain; maritime

Doolittle raid

doubt

drones, *See also* unmanned systems

Dyck, Jeff

*Economist, The*

*Ehime Maru* (Japanese fishing vessel)

Einstein, Albert

Eisenhower, Gen. Dwight D., USA

electromagnetic spectrum/environment, *See also* electronic warfare

Electronic Discrete Variable Automatic Computer (EDVAC)

electronic warfare

effects grid

empiricism

epistemology

Esper, Michael, secretary of defense

ethics

European Union

*Ex Machina*

expeditionary advanced base operations (EABO)

experimentation

F-35 Lightning II

F/A-18 Hornet

FAANG five (Facebook, Apple, Amazon, Netflix, Google)

Facebook

failures

FalconView

*Financial Times*

Fischer, Bobby

*Fitzgerald*

Five Eyes

Fletcher, Adm. Frank Jack, USN

fog computing

fog of war

Ford, Chris

frequency spectrum, *See also* electromagnetic spectrum/environment

future years defense plan (FYDP)

Garland, Alex

general AI, *See also* strong AI

Geurts, James

Gilday, Adm. Michael, USN

Girrier, Rear Adm. Robert P., USN

Gladwell, Malcolm

Good, I. J.

good old-fashioned AI (GOFAI)

Google

Google Maps

GPS (global positioning system)

gradient descent process

great power competition, *See also* China, Peoples Republic of (PRC); Russia

*Greenville*

grids (C4I, sensor, effects, etc.)

Guam

Hagel, Charles (Chuck), secretary of defense

Halsey, Adm. William, USN

Harvard Kennedy School Belfer Center for Science and International Affairs

Hawking, Stephen

Hayes, Richard

helicopters

Hilbert, David

Hipple, Eric Von

Hofstadter, Douglas

Hoover, Capt. Gilbert, USN

Horowitz, Michael

hostile intent

*Houston*

Howard, Michael

Huawei

Hughes, Capt. Wayne, USN

Human Rights Watch

human-machine collaboration/teaming; photo

human/man-in-the-loop, on-the-loop; authoritarian governments; DoD pledge

Humboldt, Wilhelm von

Huntington Ingalls Shipbuilding

hyper-decision

hypersonic weapons

IBM

iGo

imitative learning

imperfect AI

India

induction

information contestation grid

innovation; battlefield; theory; war-fighter, *See also* defense innovation initiative (DII)

Institute for Future Warfare Studies

integrated fires

Integrated Mechanical Diagnostics Health and Usage Management System

intelligence, surveillance, and reconnaissance (ISR), *See also* command, control, communications, computers, intelligence, surveillance, and reconnaissance (C4ISR)

Intelligence Advanced Research Projects Activity (IARPA)

interdisciplinary agenda

international law

internet

internet of things

Iran

Iraq

Japan; Imperial

*John S. McCain*

Joint Artificial Intelligence Center (JAIC)

Joint Force Commanders (JFC)

*Joint Military Operations Reference Guide*

joint targeting cycle; diagram

*Juneau*

Kahneman, Daniel

Kalman filters

Kania, Elsa

Kasparov, Gary

Keller, Bill

Kennedy, John F., president

killer robots

Knights, Stanley F.

knowledge base (KB)

Kosovo

Kuhlmann, Rear Adm. Dietrich, USN

Kurzweil, Ray

landmines

lasers

law of war

Legendre, Adrien-Marie

Leibniz, Gottfried W.

Leigh-Mallory, Air Marshal, RAF

levels of war, *See also* operational level of war; tactics

Libicki, Martin

Lindsay, John

line-of-sight links

Linnainmaa, Seepo

LISP programming language

Locke, John

logistics

long-range research and development program plan (LRRDPP)

MacArthur, Gen. Douglas, USA

machine learning (ML), 2425; adversarial attacks; algorithms; as applied statistics; deception; defined education; and empiricism; fundamental problem; for ISR; goals; military applications; Navy’s commitment to; for planning; security; violent force

Mahan, Capt. Alfred T., USN

maritime operations center (MOC)

Marshall, Andrew

Marx, Karl

MATLAB (computer program)

Mattis, Gen. James, USMC, secretary of defense

McCarthy, John

Meyer, Rear Adm. Wayne, USN

Microsoft

Midway, Battle of

mine warfare, *See also* Captor, Mk 60 mine

Minsky, Marvin

mission command; defined

MIT (Massachusetts University of Technology)

ML spring

Moore, 1st Lt. John, USA

mobile ad hoc network (MANET)

moral agent, *See also* ethics

Moran, Adm. William, USN

Mosaic warfare

MQ-4C Triton

MQ-25 Stingray

multidomain operations

Napoleonic organization

narrow AI, *See also* weak AI

narrow task autonomous systems

*National Artificial Intelligence Research and Development Strategic Plan*

*National Defense Strategy* (NDS)

*National Military Strategy* (NMS)

National Oceanic and Atmospheric Agency (NOAA)

National Science and Technology Council (NSTC)

National Security Agency

*National Security Strategy* (NSS)

natural language processing

Naval Integrated Capabilities Concept

Naval Integrated Fire Control (NIFC)-Counter Air

Naval Postgraduate School

Naval War College, U.S.

Navy Information Warfare Center Pacific

Nelson, Vice Adm. Lord, RN

Netflix

network management, *See also* neural networks

Neumann, John von

neural networks; biological

*New York Times*

New Zealand

Newell, Alan

Nimitz, Adm. Chester, USN

normal accidents

Normandy invasion, *See also* 101st Airborne Division

North Atlantic Treaty Organization (NATO)

North Atlantic Treaty Organization Supreme Allied Command Atlantic Innovation Center

North Vietnam, *See also* Vietnam War

nuclear weapons

Obama, Barack, president

object recognition

Office of Naval Research

Office of Net Assessment

Officer in Tactical Command (OTC)

ontology

OODA (observe-orient-decide-act) loop; diagram, *See also* Boyd, Col. John, USAF

opaque design

open standards

Operation Desert Storm

operational level of war; definition

Orca large unmanned undersea vehicle

Orwell, George

Palmer, Michael

Papert, Seymour

Patriot missile system

pattern recognition: of adversarial communications; and data; deception; in DoD strategies; dominant characteristic of AI in human intuition; induction; in logistics; at machine speed; as narrow AI; on patrol; pattern-of-life analysis; predictability; in scenarios; static data; at tactical level

Pearl, Judea

People’s Liberation Army (PLA), *See also* China, People’s Republic of (PRC); Chinese Communist Party (CCP); People’s Liberation Army Navy (PLAN)

People’s Liberation Army Navy (PLAN), *See also* China, People’s Republic of (PRC); Chinese Communist Party (CCP); People’s Liberation Army (PLA)

permanent change-of-station (PCS) moves

personalized assistant that learns (PAL)

piracy

plan, activity, and intent recognition (PAIR)

Plato

Popper, Karl

Powell, Gen. Colin, USA

power control

practitioners

problem of induction

*Proceedings*, U.S. Naval Institute

procurement

Project Maven, *See also* pattern recognition

Putin, Vladimir

Python (computer program)

Quadrennial Defense Review (QDR)

R (computer program)

RAND Corporation

rationalism

reconnaissance, *See also* intelligence, surveillance, and reconnaissance (ISR)

reconnaissance-strike complex

Resnick, Mitchel

results only work environment (ROWE)

revolution in military affairs (RMA)/military-technical revolution

Richardson, Adm. John, USN

risk

robotic warfare

robot/robotics; and autonomy; courses in; decision-making goals; limited in function, *See also* killer robots; robotic warfare

Roper, William

Royal Air Force (UK)

RQ-4 Global Hawk

Rumsfeld, Donald, secretary of defense

Russia

Russell, Stuart

safety data

Samuel, Arthur L.

satellites

*Sea Hunter* unmanned surface vessel

sensor grid

service academy swarm challenge (SASC)

SHRDLU natural language understanding system

Silicon Valley

Simon, Herbert

simple AI

Singer, Peter

Smith, Brad

Smith, Wolfgang

social construction of technology (SCOT)

soft kill

South China Sea

South Korea

Soviet Union, *See also* North Atlantic Treaty Organization (NATO); Warsaw Pact

Spanish armada

special operations forces (SOF)

Spruance, Adm. Raymond

squad with autonomous teammates competition (SWAT-C)

Standard Missile-6 (SM-6) surface-to-air missile

Stanford University

*Star Trek*

*Stark*

static data

Strait of Hormuz

strategic capabilities office (SCO)

strategy process

strong AI

supervised learning

symbolic AI

synchronization

system of systems (SoS)

tactical decision making under stress (TADMUS)

tactical situation (TACSIT)

tactics; definition

tactics, techniques, and procedures (TTPs)

task managers

tasking, collection, processing, exploitation, and dissemination (TCPED); diagram

Tegmark, Max

*Terminator*

Third Fleet, U.S.

third offset strategy (3OS)

Torpedo Squadron

Trafalgar, Battle of, *See also* Nelson, Vice Adm. Lord, RN

transparency

Trump, Donald, president

trust in AI; autonomy; by commanders; by operators; public; trustless approach

Turing, Alan

Typhoon Cobra

Tzu, Sun

Ukraine

unipolar moment

United Kingdom

United Nations

unmanned surface vessel (USV)

unmanned systems

Unmanned Undersea Vehicle Squadron One

unmanned/uninhabited undersea vehicle (UUV)

unsupervised learning

U.S. Air Force (USAF)

U.S. Army (USA)

U.S. Army Air Corps/Force

U.S. Cyber Command

U.S. Marine Corps (USMC)

U.S. Pacific Command China strategic initiatives

user satisfaction

UUV Master Plan

Vietnam War

*Vincennes*

Vinge, Vernor

wargame

*WarGames* (movie)

Warsaw Pact, *See also* North Atlantic Treaty Organization (NATO)

Waze

weak AI, *See also* narrow AI

Wilczek, Frank

Willard, Vice Adm. Robert F., USN

Winner, Langdon

Winograd, Terry

Word2Vee

World Intellectual Property Organization

World War II

Wozniak, Steve

Wylie, Rear Adm. J. C., USN

X-Unmanned Combat Air System Demonstrator (UCAS-D)

Xi Jinping

YOLO-net

Younger, Sir Alex

Zinni, Gen. Anthony, USMC

**The Naval Institute Press** is the book-publishing arm of the U.S. Naval Institute, a private, nonprofit, membership society for sea service professionals and others who share an interest in naval and maritime affairs. Established in 1873 at the U.S. Naval Academy in Annapolis, Maryland, where its offices remain today, the Naval Institute has members worldwide.

Members of the Naval Institute support the education programs of the society and receive the influential monthly magazine *Proceedings* or the colorful bimonthly magazine *Naval History* and discounts on fine nautical prints and on ship and aircraft photos. They also have access to the transcripts of the Institute’s Oral History Program and get discounted admission to any of the Institute-sponsored seminars offered around the country.

The Naval Institute’s book-publishing program, begun in 1898 with basic guides to naval practices, has broadened its scope to include books of more general interest. Now the Naval Institute Press publishes about seventy titles each year, ranging from how-to books on boating and navigation to battle histories, biographies, ship and aircraft guides, and novels. Institute members receive significant discounts on the Press’s more than eight hundred books in print.

Full-time students are eligible for special half-price membership rates. Life memberships are also available.

For a free catalog describing Naval Institute Press books currently available, and for further information about joining the U.S. Naval Institute, please write to:

Member Services

**U.S. NAVAL INSTITUTE**

291 Wood Road

Annapolis, MD 21402-5034

Telephone: (800) 233-8764

Fax: (410) 571-1703

Web address: [www.usni.org](http://www.usni.org)