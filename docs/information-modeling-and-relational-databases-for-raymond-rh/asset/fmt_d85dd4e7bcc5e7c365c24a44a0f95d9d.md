
# Relating Processes to Data

We have seen how a data model may be specified at the conceptual level (e.g., with an ORM schema) and the logical level (e.g., with a relational schema). The overall information systems life cycle includes other tasks, as discussed in [Chapter 2](#Ch002_27-57_B9780443237904000128.xhtml). [Chapter 15](#Ch015_773-830_B9780443237904000190.xhtml) discussed how to specify business processes using UML and business process model and notation (BPMN). This section provides a brief overview of other design tasks such as relating processes to data, organizing large models, and specifying the user interface.

Suppose we need to design an information system for an automated teller machine (ATM) to be operated by a credit union. As part of the requirements analysis phase, we determine that four main functions of the system are to enable clients to make deposits, withdrawals, and transfers (e.g., from a savings account to a checking account) as well as obtain printouts of account balances. In UML, each of these functions may be treated as a use case and included in a use case diagram to provide an overview of the processes supported by the system. We might then flesh out these functions in a set of activity diagrams in UML or workflow diagrams in BPMN.

Suppose that when a client inserts a credit card into the ATM, the system checks whether the card is one of its own and, if so, accesses the client’s identifier (client number) from the card. The same account could be used by many clients (e.g., a joint account for husband and wife), and each client has a distinct client number. In this way, the system can track which client actually makes any given transaction.

Suppose in diagramming the `ValidateClient` and `GetBalance` processes, we see that the combined process of validating a client and printing a requested balance involves two input data flows (`clientNr`, `accountType`) from the Client and one output data flow (`balance`) to the client. If we consider the credit union’s account database system to be separate from the ATM, it may be thought of as another actor that actually provides the balance details in response to a request (e.g., an SQL query) sent from the ATM.

In such higher-level views, little or no detail is provided on the structure of the data store or on how the process manages to find the relevant data. Because such details are so far undefined, process diagrams often fail to provide an adequate basis for modeling the data perspective. Despite such informality, they can be of use in clarifying the UoD and for identifying functions to be included in the application’s screen menus. Indeed, ordinary cartoons with intuitive icons can be quite useful for communication between modeler and domain expert in the early stages of requirements analysis.

In principle, a process model could be successively refined to elementary transactions that expose the underlying fact types. However, this approach is simply too time consuming for data intensive systems and is often unstable because business processes tend to change far more rapidly than the underlying data. To expedite the data modeling process, we should seed it with data use cases and apply a modeling procedure such as the ORM conceptual schema design procedure (CSDP). If examples already exist, use these. If not, sit down with the domain expert and generate them. These could be in the form of tables, forms, graphs, or whatever. By now, you should have the verbalization skills to do CSDP step 1 properly on any of these varieties, and because clients find it easier to work at the instance level, this is the safest way to go. Moreover, by doing this you’ve already started prototyping external screens and reports the clients want.

Process models should be formally connected to the data models. This is best done after the conceptual and logical data models are determined. Although skilled modelers can refine process models into data models, this approach tends to be error-prone. For example, suppose we bypass conceptual data modeling, instead refining the process models mentioned earlier for validating clients and getting balances into the following table scheme and SQL procedure. Here, “&1” and “&2” are input parameters or placeholders. When the procedure is executed, actual values are input to these parameters.

```
D1: Account ( clientNr, accountType, balance )
P1: select balance from Account where clientNr = &1 and accountType = &2
```

Can you spot a potential problem with this design? It’s easiest to see the problem if you do a conceptual schema for D1. This is depicted in [Fig. 18.13](#Ch018_935-1005_B9780443237904000104.xhtml#f0070). Each account has one or more users and has exactly one account type (e.g., L = loans, C = checking, S1 = main savings, S2 = other savings). That’s fine. The problem lies in the identification scheme for Account. Although the combination of `clientNr` and `accountType` does identify an account in this domain, this should not be used for preferred reference because (`clientNr`, `accountType`) pairs do not relate to accounts in a 1:1 fashion.

![Fig. 18.13 The preferred reference scheme for accounts is unsafe.](images/B9780443237904000104/f18-13-9780443237904.jpg)

[Fig. 18.13](#Ch018_935-1005_B9780443237904000104.xhtml#B-f0070) The preferred reference scheme for accounts is unsafe.

For example, suppose your spouse’s `clientNr` is 1001, yours is 1002, and you share a main savings account (type = “S1”). This joint account may be referenced by (1001, “S1”) and by (1002, “S1”). This will not do for preferred reference. For instance, the `Account` table used for D1 will accept the population {(1001, “S1”, 9000), (1002, “S1”, 0)}. But this means that the same account has two different balances, which is nonsense. The obvious solution is to introduce another preferred identifier (e.g., `accountNr`), as shown in [Fig. 18.14](#Ch018_935-1005_B9780443237904000104.xhtml#f0075). This figure also includes the new relational schema (D1′) and the new procedure for computing the balance (P1′).

![Fig. 18.14 The preferred reference scheme for accounts is now safe.](images/B9780443237904000104/f18-14-9780443237904.jpg)

[Fig. 18.14](#Ch018_935-1005_B9780443237904000104.xhtml#B-f0075) The preferred reference scheme for accounts is now safe.

This example is simplified (e.g., Exercise 6.4 discussed how balances might be derived from account transactions) but it does illustrate how conceptual modeling facilitates a correct data design, and that a detailed process specification is of little use unless the data structure on which the process operates is defined accurately.

In practice, the use of `accountNr` for preferred reference should be obvious by inspecting other data examples associated with this use case or a related one for the accounting system (e.g., a balance statement). As discussed in [Section 5.3](#Ch005_159-209_B9780443237904000098.xhtml#s0025), a reference scheme within a given context might not be suitable for the global application. Bear this in mind when discussing data use cases with domain experts.

Although a rigorous process model is best built on top of a data model, an overview of the processes can be useful as a precursor to data modeling, especially if the application is large or only vaguely understood. It is often helpful to get a clear picture of the functions of the application first.

Starting with the overall objectives, the main functions and processes of the application may be specified systematically using a variety of diagrams. This kind of analysis helps us divide the domain into coherent modules of manageable size and facilitates the task of specifying information examples where none exist. At this point, CSDP step 1 may be applied to each module.
