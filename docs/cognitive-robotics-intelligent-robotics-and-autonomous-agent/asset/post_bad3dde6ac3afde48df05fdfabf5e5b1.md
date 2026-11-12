
## COGNITIVE ROBOTICS

EDITED BY
ANGELO CANGELOSI
AND
MINORU ASADA

![](img/3dbcfad67b8516752e436bc9e574de5a_0_0.png)

## Cognitive Robotics

### Intelligent Robotics and Autonomous Agents

Edited by Ronald C. Arkin

A complete list of the books in the Intelligent Robotics and Autonomous Agents series appears at the back of this book.

## Cognitive Robotics

Edited by Angelo Cangelosi and Minoru Asada

The MIT Press
Cambridge, Massachusetts
London, England

© 2022 Angelo Cangelosi and Minoru Asada

This work is subject to a Creative Commons CC-BY-ND-NC license.

Subject to such license, all rights are reserved.

![](img/3dbcfad67b8516752e436bc9e574de5a_5_0.png)

The MIT Press would like to thank the anonymous peer reviewers who provided comments on drafts of this book. The generous work of academic experts is essential for establishing the authority and quality of our publications. We acknowledge with gratitude the contributions of these otherwise uncredited readers.

This book was set in Times New Roman by Westchester Publishing Services.

## Library of Congress Cataloging-in-Publication Data

Names: Cangelosi, Angelo, 1967– editor. | Asada, Minoru, editor.
Title: Cognitive robotics / edited by Angelo Cangelosi and Minoru Asada.
Other titles: Cognitive robotics (M.I.T. Press)
Description: Cambridge, Massachusetts : The MIT Press, [2022] | Series: Intelligent robotics and autonomous agents series | Includes bibliographical references and index.
Identifiers: LCCN 2021031320 | ISBN 9780262046831 (hardcover)
Subjects: LCSH: Autonomous robots.
Classification: LCC TJ211.35 .C628 2022 | DDC 629.8/92—dc23
LC record available at https://lccn.loc.gov/2021031320

To Stella and Virginia (AC)

To the memory of my beloved son Ryu, and to Jin and Yuko (MA)

## Contents

- Preface ... ix
- Acknowledgments ... xi

## I DEFINITION AND APPROACHES

- 1 **What Is Cognitive Robotics?** ... 3
  Angelo Cangelosi and Minoru Asada

- 2 **Neurorobotics: Neuroscience and Robots** ... 19
  Tiffany J. Hwu and Jeffrey L. Krichmar

- 3 **Developmental Robotics** ... 41
  Minoru Asada and Angelo Cangelosi

- 4 **Evolutionary Robotics** ... 59
  Stefano Nolfi

- 5 **Swarm Robotics** ... 77
  Mary Katherine Heinrich, Mostafa Wahby, Marco Dorigo,
  and Heiko Hamann

- 6 **Soft Robotics: A Developmental Approach** ... 99
  Luca Scimeca and Fumiya Iida

## II METHODS AND CONCEPTS

- 7 **Robot Platforms and Simulators** ... 123
  Diego Ferigo, Alberto Parmiggiani, Elena Rampone, Vadim Tikhanoff,
  Silvio Traversaro, Daniele Pucci, and Lorenzo Natale

- 8 **Biomimetic Skin** ... 145
  Markellos Ntagios, Oliver Oziko, and Ravinder Dahiya

- 9 **Machine Learning for Cognitive Robotics** ... 165
  Tetsuya Ogata, Kuniyuki Takahashi, Tatsuro Yamada, Shingo Murata,
  and Kazuma Sasaki

- 10 Cognitive Architectures
  David Vernon
  191

- 11 Embodiment in Cognitive Science and Robotics
  Tom Ziemke
  213

- 12 Ethics of Robotics
  Vincent C. Müller
  231

## III BEHAVIORAL AND COGNITIVE CAPABILITIES

- 13 Intrinsic Motivations for Open-Ended Learning
  Gianluca Baldassarre
  251

- 14 Principles of Cognitive Vision
  Yiannis Aloimonos and Giulio Sandini
  271

- 15 Cognitive Robot Navigation
  Jiru Wang, Jianxin Peng, Rui Yan, and Huajin Tang
  295

- 16 Cognitive Robot Manipulation
  Yiming Jiang and Chenguang Yang
  315

- 17 Cognitive Control for Decision and Human-Robot Collaboration
  Erwin Jose Lopez Pulgarin, Ute Leonards, and Guido Herrmann
  337

- 18 Social Cognition
  Yukie Nagai
  361

- 19 Human-Robot Interaction
  Tony Belpaeme
  379

- 20 Language and Communication
  Angelo Cangelosi and Tetsuya Ogata
  395

- 21 Knowledge Representation and Reasoning
  Michael Beetz
  413

- 22 Abstract Concepts
  Alessandro Di Nuovo
  433

- 23 Robots and Machine Consciousness
  Antonio Chella
  453

- Contributors
  475

- Index
  477

## Preface

> Truth is verified only by creation or invention.
> —Gianbattista Vico

Artificial intelligence (AI), machine learning, and robotics have become household terms following recent significant advances in AI for various applications in health care, in banking, and on the web and in the testing of robots in nuclear-decommissioning sites, as social companions for children and older people, and, very recently, as potential technologies to manage infection risks in the COVID-19 era. Notwithstanding this significant progress and momentum and the overpromising, in some cases, of what robots endowed with AI algorithms can actually do, the challenge of building machines with humanlike behavioral, cognitive, and social capabilities is a daring enterprise.

What cognitive robotics offers is a novel and insightful way to address the bold challenges of building AI-powered intelligent robots by taking inspiration from the way natural cognitive systems (i.e., humans, animals, biological systems) develop intelligence by exploiting the full power of the interactions between their bodies and their brains, the physical and social environments in which they live, and their phylogenetic, developmental, and learning dynamics. This is consistent with Vico’s philosophical approach that “truth is verified only by creation or invention.” That is, by creating or inventing something new, such as designing a computational cognitive architecture to control a cognitive agent, or developing a machine-learning model of intrinsic motivation and consciousness capabilities in robots, or running experiments to test a robot’s capabilities to sense, plan, and act in the world, we can verify the validity of a scientific theory, hypothesis, or model.

The term and field of cognitive robotics have their origins in the 1990s, and it is somewhat surprising that over the last thirty years of research in this field, no comprehensive publications has covered the breadth and depth of cognitively inspired intelligent robotic systems. This is exactly the aim of this book: to provide the first comprehensive, state-of-the-art coverage of cognitive robotics research and of its definition, approaches, methods, and applications. We will set the scene in part I (“Definition and Approaches”) by providing a systematic definition of the term cognitive robotics and an overview of its historical developments. This part will also include a detailed discussion of the five main, seminal approaches to cognitive robotics: developmental, neuro-, evolutionary, swarm, and soft robotics. Part II (“Methods and Concepts”) further expands the primary methodologies and concepts employed in this field. These range from the analysis of the most commonly used cognitive robotics platforms and robot simulators to the case of biomimetic skin as an example of a hardware-based approach to cognitive robots. Two further methodological chapters examine the use of machine-learning methods and of cognitive architectures. Additionally, we look at theoretical considerations in cognitive robots, such as embodiment and the ethical implications of robotics and AI. The final part, III (“Behavioral and Cognitive Capabilities”), comprises a set of chapters covering the broad spectrum of robotics models, experiments, and applications with regard to various behavioral and cognitive capabilities. This ranges from intrinsic motivation and perception to social cognition and language and up to robot consciousness issues. Each of these chapters will also explicitly discuss the psychology and neuroscience findings and principles that have inspired the cognitive robots’ models and experiments.

The target readership of this volume includes master’s and PhD students who want to learn about the concepts and methods in the field as well as researchers interested in specific cognitive robotics models and experiments. The book is written for an interdisciplinary audience, balancing technical details and examples for the computational reader as well as theoretical issues and high-level descriptions of robot experiments for the empirical sciences reader.

We hope the reader will enjoy learning about the beneficial connection between psychology and neuroscience findings on cognitive development and learning in humans and animals and the design of intelligent robots.

Angelo Cangelosi and Minoru Asada
