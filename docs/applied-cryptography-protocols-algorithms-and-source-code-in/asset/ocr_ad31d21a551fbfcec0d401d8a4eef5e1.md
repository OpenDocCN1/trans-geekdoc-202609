# 3.4 Formal Analysis

67

+   [3] Attack logic formulas to the statements: assertions about the state of the system after each statement.

+   [4] Apply the logical postulates to the assertions and assumptions to discover the beliefs held by the parties in the protocol.

The authors of BAN logic view the idealized protocols as clearer and more complete specifications than traditional descriptions found in the literature... [283,284]. Others are not so impressed and criticize this step because it may not accurately reflect the real protocol [161,1612]. Further debate is in [221,1557]. Others try to show that BAN logic can deduce characteristics about protocols that are obviously false [111]—[285,1509] for a rebuttal—and that BAN logic only deals with trust and not security [1509]. More debate is in [1488,706,1002].

Despite these criticisms, BAN logic has been a success. It has flaws in several protocols, including Nehadam-Schroeder and an early draft of CCIT X.500 protocol [303]. It has uncovered redundancies in many protocols, including Yamaha, Nehadam-Schroeder, and Kerberos. Many published papers use BAN logic to make claims about their protocol's security [40,1162,73].

Other systems have been published, some designed as extensions to BAN logic [645,586,1556,828] and others use BAN to correct perceived weaknesses [1488,1002]. The most successful of these is GNY [645]; although it has some shortcomings [40]. Probabilistic beliefs are added to BAN logic, with mixed success, comings [292,474]. Other formal logics are added [156,798,288], [1514] attempts to combine the features of several logics. [124,1511] present logics where beliefs can change over time.

The fourth approach to the analysis of cryptographic protocols models the protocol as an algebraic system, expresses the state of the participants' knowledge about the protocol, and analyzes the attainability of certain states. This approach has not received much attention as formal logic, but it is changing. It was first used by Michael Merritt [1076], who showed that an algebraic model can be used to analyze cryptographic protocols. Other approaches are in [473,1508,1531,1532,1510,162].

The Navy Research Laboratory (NRL) Protocol Analyzer is probably the most successful application of these techniques [1512,823,1046,1513]; it has been used to discover both new and known facts in a variety of protocols [1044,1045,1047]. The Protocol Analyzer defines the following:

+   Accept (Bob, Alice, N). Bob accepts the message from Alice during Bob's local N.

+   Learn (Eve, M). Eve learns M.

+   Send (Alice, Bob, Q, M). Alice sends M to Bob in response to query, Q.

+   Request (Bob, Alice, Q, N). Bob sends Q to Alice during Bob's local round N.