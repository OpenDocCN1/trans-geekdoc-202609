
![](img/f0f0f5d89818fdddf117bbe758ac8143_0_0.png)

Second Edition

## Generative Deep Learning

Teaching Machines to Paint, Write, Compose, and Play

![](img/f0f0f5d89818fdddf117bbe758ac8143_0_1.png)

David Foster

Foreword by Karl Friston

## Generative Deep Learning

Generative AI is the hottest topic in tech. This practical book teaches machine learning engineers and data scientists how to use TensorFlow and Keras to create impressive generative deep learning models from scratch, including variational autoencoders (VAEs), generative adversarial networks (GANs), Transformers, normalizing flows, energy-based models, and denoising diffusion models.

The book starts with the basics of deep learning and progresses to cutting-edge architectures. Through tips and tricks, you'll understand how to make your models learn more efficiently and become more creative.

- Discover how VAEs can change facial expressions in photos
- Train GANs to generate images based on your own dataset
- Build diffusion models to produce new varieties of flowers
- Train your own GPT for text generation
- Learn how large language models like ChatGPT are trained
- Explore state-of-the-art architectures such as StyleGAN2 and ViT-VQGAN
- Compose polyphonic music using Transformers and MuseGAN
- Understand how generative world models can solve reinforcement learning tasks
- Dive into multimodal models such as DALL·E 2, Imagen, and Stable Diffusion

This book also explores the future of generative AI and how individuals and companies can proactively begin to leverage this remarkable new technology to create competitive advantage.

> "Generative Deep Learning is an accessible introduction to the deep learning toolkit for generative modeling. If you are a creative practitioner who loves to tinker with code and want to apply deep learning to your work, then this is the book for you."

–David Ha
Head of Strategy, Stability AI

> "An excellent book that dives right into all of the major techniques behind state-of-the-art generative deep learning. An exciting exploration of one of the most fascinating domains in AI!"

—François Chollet
Creator of Keras

David Foster is the cofounder of Applied Data Science Partners.

## Praise for *Generative Deep Learning*

> *Generative Deep Learning* is an accessible introduction to the deep learning toolkit for generative modeling. If you are a creative practitioner who loves to tinker with code and want to apply deep learning to your work, then this is the book for you.

—David Ha, Head of Strategy, Stability AI

> An excellent book that dives right into all of the major techniques behind state-of-the-art generative deep learning. You'll find intuitive explanations and clever analogies—backed by didactic, highly readable code examples. An exciting exploration of one of the most fascinating domains in AI!

—François Chollet, Creator of Keras

> David Foster's explanations of complex concepts are clear and concise, enriched with intuitive visuals, code examples, and exercises.
An excellent resource for students and practitioners!

—Suzana Ilić, Principal Program Manager Responsible AI, Microsoft Azure OpenAI

> Generative AI is the next revolutionary step in AI technology that will have a massive impact on the world. This book provides a great introduction to this field and its incredible potential and potential risks.

—Connor Leahy, CEO at Conjecture and Cofounder of EleutherAI

> Predicting the world means understanding the world—in all modalities. In that sense, generative AI is solving the very core of intelligence.

—Jonas Andrulis, Founder & CEO Aleph Alpha

Generative AI is reshaping countless industries and powering a new generation of creative tools. This book is the perfect way to get going with generative modeling and start building with this revolutionary technology yourself.  
—Ed Newton-Rex, VP Audio at Stability AI and composer

David taught me everything I know about machine learning and has a knack for explaining the underlying concepts. Generative Deep Learning is my go-to resource for generative AI and lives on a shelf next to my work desk amongst my small collection of favorite technical books.  
—Zack Thoutt, CPO at AutoSalesVelocity

Generative AI is likely to have a profound impact on society. This book gives an introduction to the field that is accessible without skipping on technical detail.  
—Raza Habib, Cofounder of Humanloop

When people ask me how to get started with generative AI, I always recommend David's book. The second edition is awesome because it covers the strongest models, such as diffusion models and Transformers. Definitely a must-have for anyone interested in computational creativity!  
—Dr. Tristan Behrens, AI Expert and AI Music Artist in Residence at KI Salon Heilbronn

Dense in tech knowledge, this is my number one go-to literature when I have ideas around generative AI. It should be on every data scientist's bookshelf.  
—Martin Musiol, Founder of generativeAI.net

The book covers the full taxonomy of generative models in excellent detail. One of the best things I found about the book is that it covers the important theory behind the models as well as solidifying the reader's understanding with practical examples. I must point out that the chapter on GANs is one of the best explanations I have read and provides intuitive means to fine-tune your models. The book covers a wide range of generative AI modalities including text, image, and music.  
A great resource for anyone getting started with GenAI.  
—Aishwarya Srinivasan, Data Scientist, Google Cloud

## **Generative Deep Learning**

by David Foster

Copyright © 2023 Applied Data Science Partners Ltd. All rights reserved.

Printed in the United States of America.

Published by O'Reilly Media, Inc., 1005 Gravenstein Highway North, Sebastopol, CA 95472.

O'Reilly books may be purchased for educational, business, or sales promotional use. Online editions are also available for most titles ([http://oreilly.com](http://oreilly.com)). For more information, contact our corporate/institutional sales department: 800-998-9938 or [corporate@oreilly.com](mailto:corporate@oreilly.com).

- Acquisitions Editor: Nicole Buttersfield
- Development Editor: Michele Cronin
- Production Editor: Christopher Faucher
- Copyeditor: Charles Roumeliotis
- Proofreader: Rachel Head

- Indexer: Judith McConvile
- Interior Designer: David Futato
- Cover Designer: Karen Montgomery
- Illustrator: Kate Dullea

- July 2019: First Edition
- May 2023: Second Edition

## **Revision History for the Second Edition**

2023-04-28: First Release

See [http://oreilly.com/catalog/errata.csp?isbn=9781098134181](http://oreilly.com/catalog/errata.csp?isbn=9781098134181) for release details.

The O'Reilly logo is a registered trademark of O'Reilly Media, Inc. *Generative Deep Learning*, the cover image, and related trade dress are trademarks of O'Reilly Media, Inc.

> The views expressed in this work are those of the author and do not represent the publisher's views. While the publisher and the author have used good faith efforts to ensure that the information and instructions contained in this work are accurate, the publisher and the author disclaim all responsibility for errors or omissions, including without limitation responsibility for damages resulting from the use of or reliance on this work. Use of the information and instructions contained in this work is at your own risk. If any code samples or other technology this work contains or describes is subject to open source licenses or the intellectual property rights of others, it is your responsibility to ensure that your use thereof complies with such licenses and/or rights.

*For Alina, the loveliest noise vector of them all.*

## Table of Contents

Foreword..... xv
Preface..... xvii

## Part I. Introduction to Generative Deep Learning

1. Generative Modeling..... 3
   What Is Generative Modeling?.... 4
   Generative Versus Discriminative Modeling..... 5
   The Rise of Generative Modeling..... 6
   Generative Modeling and AI..... 8
   Our First Generative Model..... 9
   Hello World!..... 9
   The Generative Modeling Framework..... 10
   Representation Learning..... 12
   Core Probability Theory..... 15
   Generative Model Taxonomy..... 18
   The Generative Deep Learning Codebase..... 20
   Cloning the Repository..... 20
   Using Docker..... 21
   Running on a GPU..... 21
   Summary..... 21

2. Deep Learning..... 23
   Data for Deep Learning..... 24
   Deep Neural Networks..... 25
