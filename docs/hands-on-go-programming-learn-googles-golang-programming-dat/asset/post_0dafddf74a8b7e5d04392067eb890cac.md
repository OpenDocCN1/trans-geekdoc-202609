
## Hands-on Go Programming

Learn Google’s Golang Programming, Data Structures, Error Handling and Concurrency

SACHCHIDANAND SINGH  
PRITHVIPAL SINGH

![](img/e1030b71ae44b81457dd2ae7b5008eac_0_0.png)

![](img/e1030b71ae44b81457dd2ae7b5008eac_0_1.png)

## Hands-on Go Programming

*Learn Google’s Golang Programming,*  
*Data Structures, Error Handling and*  
*Concurrency*

Sachchidanand Singh

Prithvipal Singh

![](img/e1030b71ae44b81457dd2ae7b5008eac_1_0.png)

FIRST EDITION 2021

Copyright © BPB Publications, India

ISBN: 978-93-89898-19-4

All Rights Reserved. No part of this publication may be reproduced, distributed or transmitted in any form or by any means or stored in a database or retrieval system, without the prior written permission of the publisher with the exception to the program listings which may be entered, stored and executed in a computer system, but they can not be reproduced by the means of publication, photocopy, recording, or by any electronic and mechanical means.

## Limits of Liability and Disclaimer of Warranty

The information contained in this book is true and correct to the best of author’s and publisher’s knowledge. The author has made every effort to ensure the accuracy of these publications, but publisher cannot be held responsible for any loss or damage arising from any information in this book.

All trademarks referred to in the book are acknowledged as properties of their respective owners but BPB Publications cannot guarantee the accuracy of this information.

## Distributors

### BPB Publications

20, Ansari Road, Darya Ganj  
New Delhi-110002  
Ph: 23254990/23254991

### Micro Media

Shop No. 5, Mahendra Chambers,  
150 DN Rd. Next to Capital Cinema,  
V.T. (C.S.T.) Station, MUMBAI-400 001  
Ph: 22078296/22078297

### Deccan Agencies

4-3-329, Bank Street,  
Hyderabad-500195  
Ph: 24756967/24756400

### BPB Book Centre

376 Old Lajpat Rai Market,  
Delhi-110006  
Ph: 23861747

![](img/e1030b71ae44b81457dd2ae7b5008eac_4_0.png)

Published by Manish Jain for BPB Publications, 20 Ansari Road, Darya Ganj, New Delhi-110002 and Printed by him at Repro India Ltd, Mumbai

www.bpbonline.com

## Dedicated to

My Parents, Wife Nirmala  
&  
Loving Daughter Anvi and Son Vansh

— Sachchidanand Singh

My Parents, Wife Rajani  
&  
Loving son Parthiv

— Prithvipal Singh

## About the Authors

**Mr. Sachchidanand Singh** is working as Advanced Analytics, BI and Data Science SME at IBM India Software Labs (ISL), Pune. He is M.Tech from the Birla Institute of Technology and Science (BITS), Pilani. He has authored more than a dozen technical research papers in IEEE, international computer journals, and national/international conferences.

He holds several patents in Artificial Intelligence, Machine Learning, Cloud and Cognitive domain. He has rich experience in architecture design and solution implementation with technologies like Advanced Analytics and Business Intelligence (BI). He is an IEEE reviewer, Technical Program Committee (TPC) member of various national/international conferences, and a review board member of the American Journal of Computer Science and Information Engineering, USA.

**Mr. Prithvipal Singh** has been working in the IT industry for nearly a decade. He has vast experience working in Java, Golang, Spring, Node.js, and Python. He has expertise in microservice architecture and the cloud domain. He has an MCA from Savitribai Phule Pune University.

## About the Reviewer

**Dolly Talreja** is currently working as the technical lead and core member of a team developing 5G Core network (Golang Linux) and is an integral part of Altran Technologies. In her capacity, she is the owner of the nodes UDM and AUSF and is involved in completing SDLC. She is also an expert in analyzing network traces. She is part of a team that is at the forefront of innovation to address the entire breadth of the clients’ opportunities in the evolving world of cloud and digital platforms. She is an alumna of NIT Warangal, with more than 6 years of experience in the industry. She was the Lead Engineer at HP and played a key role in the development of LEDM. She is the owner of the Scan to Feature of HP. She was also part of the Samsung R&D Institute of India as the Senior Software Engineer and was part of a team developing SMB 3.0 protocol for Samsung’s MPF. She also has to her credit a published paper in IEEE on decentralized peer-to-peer networks.

## Acknowledgements

At this moment of my substantial enhancement, before we get into the thick of the things, we would like to add a few heartfelt words for the people who gave their unending support with their unfailing humour and warm wishes. First and foremost, praises and thanks to the God, the Almighty, for his showers of blessings throughout in completing this book successfully.

We want to acknowledge our colleagues who provided us with the impetus to write a more suitable text. We are thankful to the management, seniors and colleagues for constantly keeping on pushing us to move higher and higher. Besides them, we thank all our friends, well-wishers, respondents, and academicians who helped us throughout our journey from the inception to the completion.

## Preface

Golang is regarded as a swift and flawless programming language having loads of useful features like efficient built-in concurrency, garbage collector with automatic garbage detection and cleaning, dynamic growable call stack of goroutines, extremely fast compiler and cross platform versatility, etc. A lot of cloud, networking, and DevOps softwares are written in Golang like Docker, Kubernetes, Terraform, etcd, and Istio. The Go developers community is one of the most active open source communities on GitHub.

This book focuses on learning Golang, starting from the basic concepts to interfaces, pointers, concurrency, etc. We have explained each concept in detail using programming examples. We start with the basics and get into more complex stuff with each chapter. Each chapter has exercises which will help you in understanding the concepts clearly.

Over the 12 chapters in this book, you will learn the following:

### Chapter 1: Introduction

This chapter covers the basic concepts of data types, constants, variables, operators, reassignment, and redeclaration. You will learn how to use them in the Go programming language.

### Chapter 2: Functions

This chapter will cover the function declaration, parameters, multiple returns, variadic function, and defer statement. It will also cover the concept of call by value and how to pass the address of the variable as a value.

### Chapter 3: Control flows

The objective of this chapter is to introduce the concepts of control flows and loops to the readers and show how to use them.

### Chapter 4: Arrays

The objective of this chapter is to introduce the concept of arrays to the readers. It will also show how to declare and initialize arrays, and pass arrays to function.

### Chapter 5: Slices

The objective of this chapter is to introduce the concept of slices to the readers and tell them how to declare slices, the various ways of creating slices, modifying and comparing slices, about multi-dimensional slices, sorting slices, and iterate over slices.

### Chapter 6: Maps

This chapter explains the basic concept of map and how to use it in the Go programming language. It covers how to declare and initialize a map, iterate over a map, how to perform retrieve, update, and delete over the map, and how to check if a key exists in a map, etc.

### Chapter 7: Structs

This chapter explains the basic concept of struct and how to use it in the Go programming language. It covers how to declare and initialize struct type, access fields of structs, pointer to structs, exported and unexported structs, and struct fields.

### Chapter 8: Methods

This chapter covers the concept of methods in the Go programming language. You will learn how to declare a method, how to call a method, the syntax of different types of methods, and the method resolution process.

### Chapter 9: Interfaces

This chapter will cover the concept of interface in Golang. You will learn what the interface in Golang is, how Golang interfaces are different from other languages, how to declare an interface, and how implicit implementation happens in Golang and what are its benefits. We will create the interface without methods and see its benefits with built-in functions. We will see the impact of value receiver and pointer receiver while implementing the interface and creating polymorphic objects.
