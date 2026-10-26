|  |  |
|---|---|
| CAUSE-EFFECT | *those cancers were caused by radiation exposures* |
| INSTRUMENT-AGENCY | *phone operator* |
| PRODUCT-PRODUCER | *a factory manufactures suits* |
| CONTENT-CONTAINER | *a bottle of honey was weighed* |
| ENTITY-ORIGIN | *letters from foreign countries* |
| ENTITY-DESTINATION | *the boy went to bed* |
| COMPONENT-WHOLE | *my apartment has a large kitchen* |
| MEMBER-COLLECTION | *there are many trees in the forest* |
| COMMUNICATION-TOPIC | *the lecture was about semantics* |

Table 17.1: Relations and example sentences from the SemEval-2010 dataset (Hendrickx et al., 2009)

(17.7) The cup contained tea from dried ginseng.

This sentence describes a relation of type ENTITY-ORIGIN between tea and ginseng. Nominal relation extraction is closely related to semantic role labeling (chapter 13). The main difference is that relation extraction is restricted to a relatively small number of relation types; for example, Table 17.1 shows the ten relation types from SemEval-2010.

# 17.2.1 Pattern-based relation extraction

Early work on relation extraction focused on hand-crafted patterns (Hearst, 1992). For example, the appositive Starbuck, a native of Nantucket signals the relation ENTITY-ORIGIN between Starbuck and Nantucket. This pattern can be written as,

PERSON , a native of LOCATION ⇒ ENTITY-ORIGIN(PERSON, LOCATION). [17.10]

This pattern will be “triggered” whenever the literal string , a native of occurs between an entity of type PERSON and an entity of type LOCATION. Such patterns can be generalized beyond literal matches using techniques such as lemmatization, which would enable the words (buy, buys, buying) to trigger the same patterns (see § 4.3.1). A more aggressive strategy would be to group all words in a WordNet synset (§ 4.2), so that, e.g., buy and purchase trigger the same patterns.

Relation extraction patterns can be implemented in finite-state automata (§ 9.1). If the named entity recognizer is also a finite-state machine, then the systems can be combined by finite-state transduction (Hobbs et al., 1997). This makes it possible to propagate uncertainty through the finite-state cascade, and disambiguate from higher-level context. For example, suppose the entity recognizer cannot decide whether Starbuck refers to either a PERSON or a LOCATION; in the composed transducer, the relation extractor would be free to select the PERSON annotation when it appears in the context of an appropriate pattern.