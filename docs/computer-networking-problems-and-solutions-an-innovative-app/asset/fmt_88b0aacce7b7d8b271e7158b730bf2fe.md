
**Ethan Banks,** CCIE No. 20655, Routing & Switching, has been in IT since 1995, working early in his career as a systems engineer for Novell, Windows, and Linux environments. He later became an Internet services engineer working with DNS, SMTP, HTTP, and related applications at a regional ISP. He predominantly has been a network engineer and architect for enterprises in verticals including higher education, state government, consulting, finance, and technology. He has held titles such as senior network engineer, network operations manager, technical services manager, network architecture manager, and senior network architect.

In 2010, Ethan co-founded Packet Pushers Interactive, a media company whose premier product is a weekly podcast listened to by more than 10,000 network engineers all over the world.

Ethan is a writer whose content can be found in *Network World, Network Computing, InformationWeek, Modern Infrastructure*, and *TechTarget*, among other outlets. Ethan also maintains his own blog where he writes about technology at `ethancbanks.com`. Ethan has written and/or edited whitepapers for SolarWinds, Nuage Networks, CloudGenix, and NetBrain Technologies. He is currently the Future of Networking co-chair for Interop.

Ethan holds a Bachelor of Science degree in Computer Science & Business Administration from Pensacola Christian College in Pensacola, Florida where he graduated Summa Cum Laude in 1993. In the past, Ethan was certified as a Certified Netware Engineer, Microsoft Certified Systems Engineer, Cisco Certified Network Professional, Certified Ethical Hacker, and Cisco Certified Security Professional, among other titles.

## Introduction

There are many ways to approach teaching (or understanding) the fundamentals of computer network operation. For instance, one rather traditional way is to begin by examining the operation of a control plane in total, from building neighbor adjacencies to carrying information to building routes. Another common method is to start with a model, such as the Open Systems Interconnect (OSI) model, and describe the operation of the protocols from within the model. These methods have obviously been useful in teaching engineers and engineering students about how computer networks work, as they have been used to teach thousands, perhaps hundreds of thousands, of network engineers over the last 30 years.

But—in the view of the authors writing here—they have not been as effective as they could be. There are still many engineers who do not understand the basics of how a computer network actually works, in spite of many hours spent in labs, reading technical material, and even configuring and deploying network equipment. There is still a large gap in the fundamental mental skills of a large number of network engineers and engineering students that needs to be filled.

This book aims to fill that gap—not only for existing engineers, but also for all students who are trying to learn how computer networks work, even if network engineering is not their ultimate career goal. If you are a computer science student, a network engineer with 20 years of experience, someone just trying to learn network engineering, or even a business manager in charge of “the network,” this book has something to offer you.

### How This Book Is Organized

This book was born of more than 50 years of combined experience in the field of network engineering, split between two authors who have, over those years, taken in everything from forwarding devices to control planes to storage to compute. The authors (and reviewers!) have spent thousands of hours teaching the many different crafts involved in network engineering in formal and informal training, across a wide range of formats and venues. The organization of this book is the result of numerous hours spent considering how best to approach the many aspects of computer network technologies. What works and (more importantly) what does not work were considered in detail, until a plan finally emerged that the authors believe will be helpful to the largest possible set of people in and around the computer networking field.

The organization of this book begins with a seed laid out in the Internet Engineering Task Force (IETF) Request for Comments (RFC) 1925, *The Twelve Networking Truths*. Rule 11 states:

Every old idea will be proposed again with a different name and a different presentation, regardless of whether it works.

While this is clearly humorous, humor would not be funny without at least a grain of truth. In the case of rule 11, there is more than a grain of truth: buried in rule 11, there is an entire way of looking at technology, and the pace of technological change, that can revolutionize the way engineers learn technology. If it is true that every idea will be proposed again, then it is also true that every idea has been proposed before. If it were possible to learn the basic concepts behind an idea the first time it is proposed, it should be possible to understand every new proposal grounded in the same ideas in the future.

This observation—the grounding ideas behind the technologies that make computer networks work do not really change—is what drives the teaching method used in this book. Instead of focusing on models or protocols, this book follows a distinct pattern.

The thesis of this book is, then: To truly understand computer networks, you need to ask and answer three questions: What is the problem? What are the possible solutions? What do these solutions look like when they are implemented?

#### What Is the Problem?

This book is divided into three major parts covering data transport, the control plane, and specific design (or rather technology) situations. Within each of these parts, there are sets of chapters that begin by asking a basic question: what is the problem? Describing the problem set in a meaningful way will often involve a good bit more theory work, so these chapters may not, at first, seem to be very practical.

These chapters, however, are extremely practical; without a solid understanding of the problem, it is almost impossible to really understand any proposed or implemented solution in the correct context. Understanding the fundamental problems allows you to do two things:

• Relate problems you are facing right now, problems that might appear to be new, or unique, to a common body of problems solved in network engineering in the past.
• See and understand the component problems within a larger system clearly, and hence have a solid chance at applying a full range of solutions to each problem in a way that builds a complete and coherent system.

Asking this question is, in reality, the most important step you can take in truly understanding the technologies used to solve network engineering problems.

#### What Is the Solution?

Once the problem is laid bare, this book will then consider a range of possible solutions. The set of solutions will not (necessarily) be restricted to the most common solutions, or to implemented solutions. Rather, the solutions chosen for inclusion will (hopefully) provide you with a good overview of the types of solutions available. Again, this part will tend to be theoretical, specifically in describing point solutions designed to solve point problems. Again, the appearance of impracticality will be wrong—each solution is a “tool” you can add to the set of mental tools you can use to solve a wide array of problems. Combining problems and solutions in this way thus builds a solid set of mental skills useful for engineers of any type.

#### How Has This Been Implemented?
