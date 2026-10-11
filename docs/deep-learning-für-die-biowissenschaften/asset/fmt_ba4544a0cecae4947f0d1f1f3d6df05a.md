
Bei der Entwicklung neuer Machine-Learning-Methoden kann MoleculeNet als Sammlung von Richtwerten zum Testen dieser Methoden verwendet werden. Unter *[http://moleculenet.ai](http://moleculenet.ai)* können Sie einsehen, wie gut verschiedene Standardmodelle für die einzelnen Datensätze funktionieren, und vergleichen, wie gut Ihr eigenes Modell im Vergleich zu etablierten Methoden abschneidet.

#### SMARTS-Strings

In vielen häufig verwendeten Anwendungen, wie etwa der Textverarbeitung, wollen wir nach einem bestimmten String suchen. In der Cheminformatik begegnen wir ähnlichen Situationen, in denen wir bestimmen wollen, ob Atome eines Moleküls einem bestimmten Muster entsprechen. Hierfür gibt es eine Reihe von Anwendungsfällen:

*   Durchsuchen einer Moleküldatenbank, um Moleküle zu identifizieren, die eine bestimmte Substruktur enthalten.
*   Ausrichten mehrerer Moleküle auf einer gemeinsamen Substruktur zur Verbesserung der Visualisierung.
*   Hervorheben einer Substruktur in einem Plot.
*   Beschränkung einer Substruktur während einer Berechnung.

SMARTS ist eine Erweiterung von SMILES, die wir bereits vorgestellt haben und die zur Erstellung von Abfragen verwendet wird. Man kann sich SMARTS-Muster ähnlich wie reguläre Ausdrücke in der Textsuche vorstellen. Bei der Suche in einem Dateisystem kann beispielsweise `foo*.bar` angegeben werden, das `foo.bar`, `foo3.bar` und `foolish.bar` finden würde. Ein SMILES-String darf ebenfalls als SMARTS-String verwendet werden. Der SMILES-String `CCC` ist auch ein gültiger SMARTS-String und findet Sequenzen von drei benachbarten aliphatischen Kohlenstoffatomen. Das folgende Codebeispiel zeigt, wie wir Moleküle aus SMILES-Strings definieren, diese Moleküle anzeigen und die Atome hervorheben können, die zu einem SMARTS-Muster passen.

Zuerst importieren wir die benötigten Bibliotheken und erstellen eine Liste von Molekülen basierend auf einer Liste von SMILES-Strings. Das Ergebnis ist in [Abbildung 4-11](#Chapter04_9783960103516.xhtml#abb4-11) zu sehen:

```
from rdkit import Chem
from rdkit.Chem.Draw import MolsToGridImage

smiles_list = ["CCCCC","CCOCC","CCNCC","CCSCC"]
mol_list = [Chem.MolFromSmiles(x) for x in smiles_list]
```

![image](Images/p57-1.png)

*Abbildung 4-11: Chemische Strukturen aus SMILES*.

Jetzt können wir sehen, welche SMILES-Strings zum SMARTS-Muster `CCC` passen (siehe [Abbildung 4-12](#Chapter04_9783960103516.xhtml#abb4-12)):

```
query = Chem.MolFromSmarts("CCC")
match_list = [mol.GetSubstructMatch(query) for mol in mol_list]
MolsToGridImage(mols=mol_list, molsPerRow=4, highlightAtomLists=match_list)
```

![image](Images/p57-2.png)

*Abbildung 4-12: Moleküle, die zum SMARTS-Ausdruck "CCC" passen*.

In dieser Abbildung sind einige Dinge zu beachten. Zunächst einmal entspricht der SMARTS-Ausdruck nur der ersten Struktur. Keine der anderen Strukturen enthält drei benachbarte Kohlenstoffatome. Beachten Sie auch, dass es mehrere Möglichkeiten gibt, wie das SMARTS-Muster mit dem ersten Molekül in dieser Abbildung übereinstimmen könnte – es könnte drei benachbarten Kohlenstoffatomen entsprechen, indem am ersten, zweiten oder dritten Kohlenstoffatom begonnen wird. RDKit enthält zusätzliche Funktionen, die alle möglichen SMARTS-Übereinstimmungen anzeigen, aber diese werden wir jetzt nicht vorstellen.

Zusätzliche Platzhalterzeichen können eingesetzt werden, um bestimmte Atomgruppen abzugleichen. Wie bei Text kann das Sternchen (`*`) verwendet werden, um jedes Atom zu finden. Das SMARTS-Muster `C*C` findet einen aliphatischen Kohlenstoff, der an ein Atom gebunden ist, das an einen weiteren aliphatischen Kohlenstoff bindet (siehe [Abbildung 4-13](#Chapter04_9783960103516.xhtml#abb4-13)):

```
query = Chem.MolFromSmarts("C*C")
match_list = [mol.GetSubstructMatch(query) for mol in mol_list]
MolsToGridImage(mols=mol_list, molsPerRow=4, highlightAtomLists=match_list)
```

![image](Images/p58-1.png)

*Abbildung 4-13: Moleküle, die dem SMARTS-Ausdruck "C*C" entsprechen*.

Die SMARTS-Syntax kann erweitert werden, um nur bestimmte Atomgruppen zuzulassen. Zum Beispiel findet der String `C[C,O,N]C` Kohlenstoff, der an Kohlenstoff, Sauerstoff oder Stickstoff gebunden ist, der an einen weiteren Kohlenstoff bindet (siehe [Abbildung 4-14](#Chapter04_9783960103516.xhtml#abb4-14)):

```
query = Chem.MolFromSmarts("C[C,N,O]C")
match_list = [mol.GetSubstructMatch(query) for mol in mol_list]
MolsToGridImage(mols=mol_list, molsPerRow=4, highlightAtomLists=match_list)
```

![image](Images/p58-2.png)

*Abbildung 4-14: Moleküle, die dem SMARTS-Ausdruck "C[C,N,O]C" entsprechen*.

SMARTS bietet noch viel mehr, als in dieser kurzen Einführung beschrieben wird. Interessierte Leser werden gebeten, das »Daylight Theory Manual« zu lesen, um einen tieferen Einblick in SMILES und SMARTS zu erhalten.^([1](#Footnote_9783960103516.xhtml#ch4fn1)) Wie wir in [Kapitel 11](#Chapter11_9783960103516.xhtml#ch11) sehen werden, kann SMARTS verwendet werden, um komplexe Abfragen zu erstellen, mit denen Moleküle identifiziert werden können, die in Assays problematisch sein könnten.

### Fazit

In diesem Kapitel haben Sie die Grundlagen des molekularen Machine Learning erlernt. Nach einem kurzen Überblick über die Grundlagen der Chemie haben wir untersucht, wie Moleküle traditionell für Computersysteme dargestellt wurden. Des Weiteren haben Sie Graph Convolutions kennengelernt, die einen neueren Ansatz zur Modellierung von Molekülen im Deep Learning darstellen. Anschließend haben wir ein vollständiges Beispiel für die Verwendung des Machine Learning mit Molekülen zur Vorhersage einer wichtigen physikalischen Eigenschaft gesehen. Diese Methoden dienen als Grundlagen, auf denen spätere Kapitel aufbauen werden.

## KAPITEL 5

## Biophysikalisches Machine Learning

In diesem Kapitel werden wir untersuchen, wie uns Deep Learning dabei behilflich sein kann, biophysikalische Systeme zu verstehen. Besonders gründlich werden wir uns der Frage widmen, wie vorhergesagt werden kann, wie kleine, arzneimittelähnliche Moleküle an gewünschte Proteine im menschlichen Körper binden.

Diese Frage ist in der Wirkstoffforschung von wesentlichem Interesse. Die gezielte Regulierung eines einzelnen Proteins kann oftmals einen signifikanten therapeutischen Effekt haben. Zum Beispiel liegt einer der Gründe für die Wirksamkeit von Imatinib, einem bahnbrechenden Krebsmedikament, in seiner engen Bindung an BCR-ABL. Es kann schwierig sein, ein genauso wirkungsvolles einzelnes Zielprotein für andere Krankheiten zu finden, da im menschlichen Körper so viele Mechanismen zusammenwirken.

| ![image](Images/insert.jpg) | | **Medikamente zielen nicht nur auf ein Protein ab** Wie bereits angesprochen, kann es sehr nützlich sein, das Problem der Entwicklung eines Arzneimittels für eine Krankheit auf das Problem der Entwicklung eines Arzneimittels zu reduzieren, das eng mit einem bestimmten Protein interagiert. Es ist jedoch äußerst wichtig, zu begreifen, dass in der Realität jedes Medikament mit vielen verschiedenen Teilsystemen im Körper interagiert. Die Wissenschaft derart vielfältiger Wechselwirkungen wird allgemein als Polypharmakologie bezeichnet. |
| --- | --- | --- |
| | | Derzeit sind Berechnungsmethoden für den Umgang mit Polypharmakologie noch zu wenig entwickelt, sodass der Goldstandard für die Prüfung auf polypharmakologische Wirkungen die Experimente an Tieren und Menschen bleiben. Durch Weiterentwicklung rechnergestützter Verfahren kann sich dieser Zustand in den nächsten Jahren jedoch ändern. |
