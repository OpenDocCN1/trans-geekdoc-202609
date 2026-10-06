
# Vector Optimization

Johannes Jahn

# Order Analysis, Deep Learning, and Connections to Optimization

Springer

# Vector Optimization

Series Editor

Johannes Jahn, Department of Mathematics, University of Erlangen-Nuremberg, Erlangen, Germany

The series in Vector Optimization contains publications in various fields of optimization with vector-valued objective functions, such as multiobjective optimization, multi criteria decision making, set optimization, vector-valued game theory and border areas to financial mathematics, biosystems, semidefinite programming and stochastic multiobjective control theory. Studies of continuous, discrete, combinatorial and stochastic multiobjective objective models in interesting fields of operations research are also included. The series covers mathematical theory, methods and applications in economics and engineering. These publications being written in English are primarily monographs and multiple author works containing current advances in these fields.

Johannes Jahn

# Order Analysis, Deep Learning, and Connections to Optimization

![](img/e4a2e491dbba0d9f71abf293f149cd5b_3_0.png)

Johannes Jahn
Department of Mathematics
Friedrich-Alexander-University
Erlangen-Nürnberg (FAU)
Erlangen, Germany

ISSN 1867-8971 ISSN 1867-898X (electronic)
Vector Optimization
ISBN 978-3-031-67421-1 ISBN 978-3-031-67422-8 (eBook)
https://doi.org/10.1007/978-3-031-67422-8

© The Editor(s) (if applicable) and The Author(s), under exclusive license to Springer Nature Switzerland AG 2024

This work is subject to copyright. All rights are solely and exclusively licensed by the Publisher, whether the whole or part of the material is concerned, specifically the rights of translation, reprint, printing, reuse of illustrations, recitation, broadcasting, reproduction on microfilms or in any other physical way, and transmission or information storage known and retrieval, electronic adaptation, computer software, or by similar dissimilar methodology now or hereafter.

The use of general descriptive names, registered names, trademarks, service marks, etc. in this publication does not imply, in the absence of a specific statement, such names are exempt from the relevant protective laws and regulations and therefore free for general use.

The publisher, the authors and the editors are safe to assume that the advice and information in this book are believed to be true and accurate at the date of publication. Neither the publisher nor the authors or the editors give any warranty expressed or implied, with respect to the material contained herein or for any errors or omissions that may have occurred. The publisher remains neutral with regard to jurisdictional claims in published maps and institutional affiliations.

This Springer imprint is published by the registered company Springer Nature Switzerland AG
The registered company address is: Gewerbestrasse 11, 6330 Cham, Switzerland

If disposing of this product, please recycle the paper.

To Claudia and Martin

# Preface

This book provides an introduction to the two important areas of order analysis and deep learning from a mathematical perspective. The focus is on the connection to optimization, which forms a bracket as a key technology driver. Specifically, this means that applications of order analysis in optimization is a central point and that optimization is an essential tool in deep learning.

# Order Analysis

Algebraic order theory and analysis are important fields in mathematics with only a few overlaps. If the order theory fulfils an appropriate condition, then order analysis is a suitable tool for the treatment of order theory problems with methods of analysis. Order analysis summarizes methods of analysis that can be used to address problems in order theory. The term order analysis is used in this sense for the first time. However, in the context of mathematical modelling it used earlier. And in engineering, order analysis means the analysis of vibration signals and noise from rotating machinery. In the field of unsupervised deep metric learning, Kan, Cen, Li, Mladenovic, and He [82] used relative orders to decide which images belong to a certain class or not; this so-called relative order analysis is then combined with performance optimization of metric learning.

The main approach in order analysis is the fact that an inequality in order theory often be replaced by an inequality in R, making functional analysis the appropriate tool for studying problems in order theory. This book introduces order analysis and describes important applications in optimization. These applications include nonlinear optimization as well as vector and set optimization with fixed and variable order structures. Problems of so-called conditional optimization can be treated. In these optimization-related applications, order analysis can also be applied to problems in economy and finance.

The connection between order theory and analysis is given by a certain functional representing a negative convex cone in a real space as a sublevel set of this functional with respect to the level 0. Since a negative convex cone equals the set of all negative elements (including zero) of a real line space with respect to a preorder., the set of all negative elements equals this sublet. These representing functionals include Bishop-Phelfs functionals [18] and scalarizing functionals, like the signed distance functional introduced by Hiriart-Utty [61, 62] and the Gerstwitz scalarizing function by Tammer [43]. And certain penalty functionals are also covered by this theory, which is achieved by a unified approach.

In general, functionals representing a convex cone in one linear space are not unique, and so one can right to choose a suitable functional with properties that are useful for the theory. Thus, one is not restricted to a fixed type of such a function. This is an advantage for general order analysis.

The focus of the second part of this book is on the fundamentals of order analysis. The reader is assumed to have a basic grasp of functional analysis. The necessary basics are summarized in Part I. The theory outlined in the second part of this book can be applied to various applications in economics, finance, and optimization. We restrict ourselves to applications in optimization where real-, vector-, and set-valued objective methods are considered. These problems arise in nonlinear optimization, vector optimization, and set optimization.

# Deep Learning

Deep learning is the topic of the third part of this book. The basics of deep learning, as feedforward neural networks, supervised learning, and various forms of gradient methods, are presented in Chap.6. The focus is not on the basics that are essential in the context of optimization. Gradient methods, which are an important class of methods in numerical optimization, are discussed in more detail. Among the gradient methods, one with a new step size rule is introduced, the so-called-Newton type gradient descent method.

The central point of Chap. 7 is the extension of neural networks to those with set-valued inputs. Due to set-valued inputs, optimal weights and biases are obtained which are also valid for changed data if the changes are within the range of the considered sets. This leads to more robust estimators that are insensitive to certain data changes. This can also serve to improve defense against adversarial attacks. For this reason, set-valued inputs are of particular importance, and this issue is highly topical.

Sets given as closed intervals are particularly special case of set-valued inputs. Since the input data can vary very within closed intervals, we get simple formulas. Nevertheless, this comes at a high price because the corresponding optimization problem is constrained.

# Organization of This Book

The book is divided into three parts. Preliminaries are summarized in Part I. Order analysis is the subject of the second part. Representing functionals are studied in Chap. 2. Topics are definition, basic properties, sublinearity, directional derivative, subdifferential, zeros, extension to variable order structures, and separation results. The last three chapters of Part II are devoted to applications in nonlinear optimization and vector and set optimization with fixed and variable order structure.
