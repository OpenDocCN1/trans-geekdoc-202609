
## Wo liegen die Unterschiede dieser Architekturen?

Bisher scheinen die meisten von ihnen eine ähnliche Vorhersagekraft zu haben. Wir verwenden `Grid Featurization`, weil es eine optimierte Implementierung in `DeepChem` gibt, aber andere Modelle können diese Anforderungen ebenfalls erfüllen. Zukünftige Versionen von `DeepChem` werden für diesen Zweck vermutlich zusätzliche Architekturen enthalten.

Für den `Random Forest` erhalten wir einen Score von `0.979` auf den Trainingsdaten, der Score für die Testdaten liegt jedoch bei nur `0.133`. Die Trainingsdaten werden hervorragend reproduziert, die Testdaten jedoch nur sehr schlecht vorhergesagt. Offensichtlich haben wir es mit starkem `Overfitting` zu tun.

Im Vergleich dazu liefert das neuronale Netz einen Score von `0.990` auf den Trainingsdaten und `0.359` auf den Testdaten. Für den Trainingsdatensatz ist der Wert somit etwas besser und für den Testdatensatz deutlich besser. Es liegt nach wie vor `Overfitting` vor, jedoch in geringerem Maß, und die Fähigkeit des Modells, neue Daten vorherzusagen, ist viel höher.

Den Korrelationskoeffizienten zu kennen, ist ein wichtiger erster Schritt, um unser erstelltes Modell zu verstehen. Es ist jedoch immer hilfreich, direkt zu visualisieren, wie unsere Vorhersagen mit tatsächlichen experimentellen Daten korrelieren. [Abbildung 5-12](#Chapter05_9783960103516.xhtml#abb5-12) zeigt die tatsächlichen im Vergleich zu den vorhergesagten Labels für jedes Modell auf den Testdaten. Wir sehen auf den ersten Blick, dass die Vorhersagen des neuronalen Netzes viel stärker mit den wahren Daten korrelieren als die des `Random Forest`.

![image](Images/p81-1.png)

*Abbildung 5-12: Wahre gegen vorhergesagte Labels beim Ausführen auf den Testdaten.*

### Fazit

In diesem Kapitel haben Sie gelernt, wie Sie `Deep Learning` auf biophysikalische Systeme anwenden können, insbesondere auf das Problem der Vorhersage der Bindungsaffinität von Protein-Ligand-Systemen. Vielleicht sind Sie neugierig zu erfahren, wie allgemein die Fähigkeiten sind, die Sie gelernt haben. Könnten die gleichen Modelle und Techniken angewendet werden, um andere biophysikalische Datensätze zu verstehen? Hierzu geben wir eine kurze Übersicht.

Protein-Protein- und Protein-DNA-Systeme folgen auf hohem Niveau der gleichen grundlegenden Physik wie Protein-Ligand-Systeme. Die gleichen Wasserstoffbrücken, Ionenbrücken usw. spielen eine entscheidende Rolle. Könnten wir solche Systeme mit dem Code aus diesem Kapitel analysieren? Die Antwort fällt etwas kompliziert aus. Viele der physikalischen Wechselwirkungen, die Protein-Ligand-Wechselwirkungen antreiben, werden durch geladene Dynamik vorangetrieben. Andererseits wird die Protein-Protein-Dynamik möglicherweise eher durch hydrophobe Interaktionen bestimmt. Wir gehen nicht näher auf die Bedeutung dieser Wechselwirkungen ein, aber qualitativ haben sie in gewissem Maße einen anderen Charakter als Protein-Ligand-Wechselwirkungen. Das könnte bedeuten, dass der `RdkitGridFeaturizer` nicht in der Lage wäre, diese Interaktionen zufriedenstellend zu charakterisieren. Andererseits ist es möglich, dass die atomaren `CNNs` diese Systeme besser handhaben können, da viel weniger über die Physik der Interaktionen in diesen Modellen fest codiert ist.

Davon abgesehen, bleibt das erhebliche Problem der Skalierung. Die atomaren `CNNs` brauchen lange zum Trainieren und erfordern viel Speicherplatz. Die Skalierung dieser Modelle für größere Protein-Protein-Systeme würde zusätzliche technische Arbeiten erfordern. Das Entwicklerteam von `DeepChem` arbeitet intensiv an diesen und anderen Herausforderungen. Es kann jedoch noch dauern, bis die Bemühungen Früchte tragen werden.

Antikörper–Antigen-Wechselwirkungen sind eine weitere Form wichtiger biophysikalischer Wechselwirkungen. Antikörper sind Y-förmige Proteine (siehe [Abbildung 5-13](#Chapter05_9783960103516.xhtml#abb5-13)) mit einer variablen »Antigen-Bindungsstelle«, die zur Bindung von Antigenen verwendet wird. Antigene sind hier Moleküle, die mit einem bestimmten Pathogen assoziiert sind. In Kultur gezüchtete Zellen können zur Bildung von Antikörpern genutzt werden, die auf bestimmte Antigene abzielen. Sind alle Zellen einer Kultur Klone einer bestimmten Zelle, sind die erzeugten Antikörper identisch. Solche »monoklonalen Antikörper« haben in jüngster Zeit eine breite therapeutische Anwendung gefunden.

![image](Images/p83-1.png)

*Abbildung 5-13: Diagramm der Antikörper-Antigen-Wechselwirkung. (Quelle, Wikimedia ([https://en.wikipedia.org/wiki/Antibody#/media/File:Antibody.svg](https://en.wikipedia.org/wiki/Antibody#/media/File:Antibody.svg)))*

Das Design von Antikörpern war bisher in erster Linie eine experimentelle Wissenschaft. Ein Teil davon ist auf die Herausforderungen zurückzuführen, die mit dem Gewinnen einer 3-D-Antikörperstruktur verbunden sind. Die Modellierung der komplexen Antigen-Antikörper-Bindungsstelle hat sich ebenfalls als Herausforderung erwiesen. Einige der Methoden, die wir in diesem Kapitel abgehandelt haben, werden in den nächsten Jahren möglicherweise bei der Antikörper-Antigen-Bindungsmodellierung von Nutzen sein.

Des Weiteren haben wir auf die Bedeutung der Dynamik für das Verständnis der Proteinphysik hingewiesen. Könnten wir `Deep Learning` nicht direkt auf Proteinsimulationen durchführen, um zu verstehen, welche Liganden an das Protein binden könnten? Grundsätzlich ja, jedoch bleiben gewaltige Herausforderungen. Einige Unternehmen arbeiten aktiv an dieser Herausforderung, gute Open-Source-Tools sind jedoch noch nicht verfügbar.

In [Kapitel 11](#Chapter11_9783960103516.xhtml#ch11) werden wir auf einige der biophysikalischen Methoden zurückkommen und zeigen, wie diese Modelle für die Wirkstoffforschung sehr nützlich sein können.

# KAPITEL 6

# Deep Learning in der Genomik

Das Herzstück jedes lebenden Organismus ist sein Genom: die DNA-Moleküle, die alle Anleitungen enthalten, um die Einzelteile des Organismus herzustellen. Wenn eine Zelle einem Computer entspricht, dann ist ihre Genomsequenz die auszuführende Software. Und wenn DNA als Software angesehen werden kann, als Information, die von einem Computer verarbeitet werden soll, kann dann diese Information nicht von Computern analysiert werden, sodass wir verstehen, wie sie funktioniert?

Selbstverständlich ist die DNA nicht nur ein abstraktes Speichermedium. Es ist ein Molekül, das sich kompliziert verhält. Es interagiert mit Tausenden anderer Moleküle, die alle wichtige Rollen bei der Verwaltung, dem Kopieren, dem Steuern und der Ausführung der in der DNA enthaltenen Anweisungen spielen. Das Genom ist eine riesige, komplexe Maschinerie, die aus Tausenden von Teilen besteht. Nach wie vor fehlt uns das Wissen über die Funktionsweise der meisten dieser Teile, ganz zu schweigen davon, wie sie als großes Ganzes zusammenkommen.

Dies bringt uns zu den beiden Bereichen *Genetik* und *Genomik*. Die Genetik behandelt die DNA als abstrakte Information. Sie betrachtet die Vererbungsmuster oder sucht nach Korrelationen zwischen Populationen, um die Zusammenhänge zwischen DNA-Sequenzen und physischen Merkmalen aufzudecken. Die Genomik andererseits sieht das Genom als Maschine. Sie versucht, die Einzelteile dieser Maschine und ihre Zusammenarbeit zu verstehen. Die beiden Ansätze ergänzen sich, und `Deep Learning` stellt für beide ein leistungsfähiges Instrument dar.

### DNA, RNA und Proteine

Selbst wenn Sie kein Biologe sind, haben Sie sich wahrscheinlich zu irgendeinem Zeitpunkt mit den Grundlagen der Funktionsweise von Genomen beschäftigt. Zunächst werfen wir einen Blick auf die vereinfachte Darstellung der Genomik, wie sie auch in Einführungskursen gelehrt wird. Anschließend werden wir einige der Unterschiede zeigen, die unterstreichen, dass die Realität deutlich komplizierter ist.
