
## artificial intelligence meets human intelligence

## THE DEEP LEARNING REVOLUTION

TERRENCE J. SEJNOWSKI

## The Deep Learning Revolution

Terrence J. Sejnowski

The MIT Press
Cambridge, Massachusetts
London, England

© 2018 Massachusetts Institute of Technology

All rights reserved. No part of this book may be reproduced in any form by any electronic or mechanical means (including photocopying, recording, or information storage and retrieval) without permission in writing from the publisher.

This book was set in ITC Stone Sans Std and ITC Stone Serif Std by Toppan Best-set Premedia Limited. Printed and bound in the United States of America.

## Library of Congress Cataloging-in-Publication Data

Names: Sejnowski, Terrence J. (Terrence Joseph), author. Title: The deep learning revolution / Terrence J. Sejnowski. Description: Cambridge, MA : The MIT Press, 2018. | Includes bibliographical references and index. Identifiers: LCCN 2017044863 | ISBN 9780262038034 (hardcover : alk. paper) Subjects: LCSH: Machine learning. | Big data. | Artificial intelligence--Social aspects. Classification: LCC Q325.5 .S45 2018 | DDC 006.3/1--dc23 LC record available at https://lccn.loc.gov/2017044863

10 9 8 7 6 5 4 3 2 1

For Bo and Sol, Theresa, and Joseph

In memory of Solomon Golomb

## Contents

- Preface ix
- Part I: Intelligence Reimagined 1
- 1 The Rise of Machine Learning 3
- 2 The Rebirth of Artificial Intelligence 27
- 3 The Dawn of Neural Networks 37
- 4 Brain-style Computing 49
- 5 Insights from the Visual System 63
- Part II: Many Ways to Learn 79
- 6 The Cocktail Party Problem 81
- 7 The Hopfield Net and Boltzmann Machine 91
- 8 Backpropagating Errors 109
- 9 Convolutional Learning 127
- 10 Reward Learning 143
- 11 Neural Information Processing Systems 161
- Part III: Technological and Scientific Impact 169
- 12 The Future of Machine Learning 171
- 13 The Age of Algorithms 195
- 14 Hello, Mr. Chips 205
- 15 Inside Information 219
- 16 Consciousness 233
- 17 Nature Is Cleverer Than We Are 245
- 18 Deep Intelligence 261
- Acknowledgments 269
- Recommended Reading 275
- Glossary 281
- Notes 285
- Index 321

## Preface

If you use voice recognition on an Android phone or Google Translate on the Internet, you have communicated with neural networks trained by deep learning. In the last few years, deep learning has generated enough profit for Google to cover the costs of all its futuristic projects at Google X, including self-driving cars, Google Glass, and Google Brain. Google was one of the first Internet companies to embrace deep learning; in 2013, it hired Geoffrey Hinton, the father of deep learning, and other companies are racing to catch up.

The recent progress in artificial intelligence (AI) was made by reverse engineering brains. Learning algorithms for layered neural network models are inspired by the way that neurons communicate with one another and are modified by experience. Inside the network, the complexity of the world is transformed into a kaleidoscope of internal patterns of activity that are the ingredients of intelligence. The network models that I worked on in the 1980s were tiny compared with today's models, which now have millions of artificial neurons and which are dozens of layers deep. What made it possible for deep learning to make big breakthroughs on some of the most difficult problems in artificial intelligence was persistence, big data, and a lot more computer power.

We're not good at imagining the impact of a new technology on the future. Who could have predicted in 1990, when the Internet went commercial, what impact it would have on the music business? On the taxi business? On political campaigns? On almost all aspects of our daily lives? There was a similar failure to imagine how computers would change our lives. Thomas J. Watson, the president of IBM, is widely quoted as saying in 1943: “I think there is a world market for maybe five computers.” What's hard to imagine are the uses to which a new invention will be put, and inventors are no better than anyone else at predicting what those uses will be. There is a lot of room between the utopian and doomsday scenarios that are being predicted for deep learning and AI, but even the most imaginative science fiction writers are unlikely to guess what their ultimate impact will be.

The first draft of *The Deep Learning Revolution* was written in a few focused weeks after hiking in the Pacific Northwest and meditating on the remarkable recent shift in the world of artificial intelligence, which had its origin many decades earlier. It is a story about a small group of researchers challenging an AI establishment that was much better funded and at the time the “only game in town.” They vastly underestimated the difficulty of the problems and relied on intuitions about intelligence that proved to be misleading.

Life on earth is filled with many mysteries, but perhaps the most challenging of these is the nature of intelligence. Nature abounds with intelligence in many forms, from humble bacterial to complex human intelligence, each adapted to its niche in nature. Artificial intelligence will also come in many forms that will take their particular places on this spectrum. As machine intelligence based on deep neural networks matures, it could provide a new conceptual framework for biological intelligence.

*The Deep Learning Revolution* is a guide to the past, present, and future of deep learning. Not meant to be a comprehensive history of the field, it is rather a personal view of key conceptual advances and the community of researchers who made them. Human memory is fallible and shifts with every retelling of a story, a process called “reconsolidation.” The stories in this book stretch over forty years, and even though some are as vivid to me as if they occurred yesterday, I am well aware that the details have been edited by my memory’s retellings over time.

Part I provides the motivation for deep learning and the background needed to understand its origins; part II explains learning algorithms in several different types of neural network architectures; and part III explores the impact that deep learning is having on our lives and what impact it may have in years to come. But, as the New York Yankees’ philosopher Yogi Berra once said: “It’s tough to make predictions, especially about the future.” Text boxes in eight of the chapters to follow provide technical background to the story; timelines at the beginning of the three parts keep track of events that bear on that story and extend over sixty years.

## Part I: Intelligence Reimagined

### Timeline

- **1956—The Dartmouth Artificial Intelligence Summer Research Project** gave birth to the field of AI and motivated a generation of scientists to explore the potential for information technology to match the capabilities of humans.
- **1962—Frank Rosenblatt** published *Principles of Neurodynamics: Perceptrons and the Theory of Brain Mechanisms*, which introduced a learning algorithm for neural network models with a single layer of variable weights—the precursor of today’s learning algorithms for deep neural network models.
- **1962—David Hubel and Torsten Wiesel** published “Receptive Fields, Binocular Interaction and Functional Architecture in the Cat’s Visual Cortex,” which reported for the first time the response properties of single neurons recorded with a microelectrode. Deep learning networks have an architecture similar to the hierarchy of areas in the visual cortex.
- **1969—Marvin Minsky and Seymour Papert** published *Perceptrons*, which pointed out the computational limitations of a single artificial neuron and marked the beginning of a neural network winter.
- **1979—Geoffrey Hinton and James Anderson** organized the Parallel Models of Associative Memory workshop in La Jolla, California, which brought together a new generation of neural network pioneers and led to publication of Hinton and Anderson’s collected volume by the same title in 1981.
- **1987—The First Neural Information Processing Systems (NIPS) Conference and Workshop** was held at the Denver Tech Center, bringing together researchers from many fields.
