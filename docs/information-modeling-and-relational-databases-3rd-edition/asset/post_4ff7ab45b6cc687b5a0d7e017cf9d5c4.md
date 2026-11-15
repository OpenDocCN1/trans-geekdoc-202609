
This page intentionally left blank

## Information Levels and Frameworks

## Chapter Outline

- 2.1 Four Information Levels
- 2.2 The Conceptual Level
- 2.3 Database Design Example
- 2.4 Development Frameworks
- 2.5 Summary

### 2.1 Four Information Levels

Some advanced information systems are described as “intelligent”. What intelligence is and whether machines will ever be as intelligent as humans are debatable questions. In the *Turing test* of intelligence, based on a revision of a test proposed by Alan Turing in 1950, an opaque screen is placed between a typical human (see A in Fig. 2.1) and the object being tested for intelligence. The human can communicate with the object by means of a computer (with a keyboard for input and a screen for output) in natural language about any desired topic.

If the human can’t tell from the object’s responses whether it is an intelligent human or a machine, perhaps the object should be classified as intelligent. Two key conditions in the test are that natural language is used and that there are no restrictions on the discussion topics. Once we restrict the language and the discussion topic, there are many examples of a computer performing at the level of a human expert (e.g., chess, diagnosis of blood diseases, mineral exploration). Such systems are called “expert systems” because they perform as well as a human expert in a specific domain. Expert systems have passed “restricted Turing tests” specific to given universes of discourse (UoD).

Recent advances in artificial intelligence (AI) systems enabled some systems to pass the unrestricted Turing test. Google’s LaMDA AI chatbot passed the test in 2022. Later, OpenAI’s ChatGPT also passed the test, and its March 2023 version based on GPT-4 can take images as well as text as input (see https://en.wikipedia.org/wiki/GPT-4). Microsoft’s Bing chat allows both text and voice input.

a Turing’s original test was based on the Imitation Game, requiring only that a computer be at least as good as a man in formulating responses intended to convey the idea that the man was actually a woman. For further discussion, see http://en.wikipedia.org/wiki/Turing_test.

![](img/1344db3eba3d550e6edb009556fcd95c_52_0.png)

A fifth-generation information system (5GIS) is like a “user-definable” expert system in that it allows the user to enter a description of the universe of discourse and then conduct a conversation about this, all in natural language. Just how well the system handles its end of the conversation depends on how powerful its user interface, database management, and inference capabilities are.

Although desirable, it is not necessary that a 5GIS always be able to operate at an expert level when we communicate with it. It must, however, allow us to communicate with it in a natural way. Natural languages such as English and Japanese are complex and subtle. It will be many years before an information system will be able to converse freely in unrestricted natural language. We should be content in the meantime if the system supports dialog in a formalized subset of natural language. There may be many “formal, natural languages”, one for English, one for Japanese, and so on. A 5GIS should be able to respond in the same language used by the human. For example, suppose we posed the query:

What is the age of Selena?

and we received the reply

sanjusai.

This would not help unless we knew that the reply is Japanese for “30 years old”. Even if we can translate Japanese to English, we might still misinterpret the reply because instead of assigning people an age of zero years when born, the Japanese assign an age of 1 year. So, an age of 30 years in the Japanese system corresponds to an age of 29 years in the Western system. In addition to the requirement for a *common language*, effective communication between two people requires that each assigns the *same meaning* to the words being used. To achieve this, they should (a) share the same context or UoD and (b) speak in sentences that are unambiguous with respect to this UoD.

With our example, the confusion over whether Selena’s age is 29 or 30 years results from different age conventions, one Western and one Japanese. Natural speech abounds with examples that can be disambiguated only by context. Consider “Pluto is owned by Mickey”. This is true for the world of Walt Disney’s cartoon characters. But suppose someone unfamiliar with Mickey Mouse and his dog Pluto interpreted this within an astronomical context, taking “Pluto” to refer to the minor planet Pluto—a drastic communication failure! It is essential to have a clear way of describing the UoD to the information system.

An information system may be viewed from *four levels*: *conceptual, logical, physical*, and *external*. The conceptual level is the most fundamental, portraying the business domain naturally in human concepts. At this level, the blueprint of the UoD is called the **conceptual schema**. This describes the structure or grammar of the business domain (e.g., what types of objects populate it, what roles these objects play, and what constraints apply).

While the conceptual schema indicates the structure of the UoD, the **conceptual database** at any given time indicates the *content* or instances populating a specific *state* of the UoD. Because information adds meaning to the data, the term “information base” is more appropriate (van Griethuysen, 1982). However, we’ll use the briefer, more popular term “database”. Conceptually, the database is a set of sentences expressing propositions taken to be true of the UoD. Because sentences may be added or deleted, the database may undergo transitions from one state to another.

However, at any particular time, the sentences populating the database must individually and collectively conform to the domain-specific grammar or design plan that is the conceptual schema. To summarize:

The conceptual schema specifies the structure for all permitted states and transitions of the conceptual database.

To enforce this law, we now introduce a third system component: the **conceptual information processor** (CIP). This supervises updates to the database by the user and answers user queries. Fig. 2.2 shows the basic conceptual architecture of an information system. This diagram assumes that the conceptual schema is already stored in the system. For each application area, a different conceptual schema is entered.

Although the diagram might suggest that the user is interacting directly with the CIP, the user’s interaction with the system is external rather than conceptual. The conceptual schema is not concerned with user interfaces or the physical details of how the database

![](img/1344db3eba3d550e6edb009556fcd95c_53_0.png)

can be efficiently maintained. These concerns are catered for by including external and internal components within the overall architecture.

When interpreted by people, the conceptual schema and database both provide knowledge about the UoD. The combination of conceptual schema and (conceptual) database is called a conceptual model of the UoD. The model or knowledge base is a formal description of the UoD, and the CIP controls the flow of information between the model and humans. Some authors use the term “model” in the more restricted sense of “schema”. This book uses the term “model” to include both the schema and a set of facts that populates the schema.

Recall that the domain expert is a person or group of people collectively familiar with the business domain. The modeler or conceptual designer is a person or team that specifies the conceptual schema by formalizing the domain expert’s knowledge. An end user makes use of the implemented system. For a small system, the domain expert, modeler, and user might be the same person. A large system might have several partial domain experts, a team of analysts and designers, and thousands of end users.

The modeler inputs the conceptual schema to the system and has read/write access to it. Typically, most users have read-only capability for the schema, but read/write access to the database. Different interfaces may be created for different users so that some users have access to only part of the model. Thus, different users may access different subschemas of the global conceptual schema. This situation is summarized in Fig. 2.3. Some users may have read-only access to the database.

An external schema specifies the UoD design and operations accessible to a particular user or group of users. Here we specify what kind of facts may be read, added, or deleted, and how they are displayed. For security reasons, different user groups are often allocated different access rights (e.g., to ensure that sensitive information is not made public). For user convenience, views may be constructed to hide information irrelevant to a user group, or to collect and display information more efficiently. Different interfaces may be designed to cater to users with different expertise levels even when accessing the same underlying information.

Conceptual schemas are designed for clear communication, especially between modelers and domain experts. While they give a clear picture of the UoD, they are usually

![](img/1344db3eba3d550e6edb009556fcd95c_54_0.png)

FIG. 2.3 Access to the model.
