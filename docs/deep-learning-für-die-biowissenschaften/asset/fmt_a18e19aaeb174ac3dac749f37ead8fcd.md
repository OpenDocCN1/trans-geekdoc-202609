
# Deep Learning für die Biowissenschaften

*Einsatz von Deep Learning in Genomik, Biophysik, Mikroskopie und medizinischer Analyse*

**Bharath Ramsundar, Peter Eastman, Patrick Walters, Vijay Pande**

**Deutsche Übersetzung von Helena Schock**

## Inhalt

- [Vorwort](#Vorwort_9783960103516.xhtml#vor)
- [1 Warum Biowissenschaften?](#Chapter01_9783960103516.xhtml#ch1)
  - [Warum Deep Learning?](#Chapter01_9783960103516.xhtml#lev1)
  - [In den modernen Biowissenschaften geht es um Daten](#Chapter01_9783960103516.xhtml#lev2)
  - [Was werden Sie lernen?](#Chapter01_9783960103516.xhtml#lev3)
- [2 Einführung in Deep Learning](#Chapter02_9783960103516.xhtml#ch2)
  - [Lineare Modelle](#Chapter02_9783960103516.xhtml#lev4)
  - [Mehrlagige Perzeptronen](#Chapter02_9783960103516.xhtml#lev5)
  - [Trainieren der Modelle](#Chapter02_9783960103516.xhtml#lev6)
  - [Validierung](#Chapter02_9783960103516.xhtml#lev7)
  - [Regularisierung](#Chapter02_9783960103516.xhtml#lev8)
  - [Hyperparameteroptimierung](#Chapter02_9783960103516.xhtml#lev9)
  - [Weitere Arten von Modellen](#Chapter02_9783960103516.xhtml#lev10)
  - [Convolutional Neural Networks](#Chapter02_9783960103516.xhtml#sec1)
  - [Recurrent Neural Networks](#Chapter02_9783960103516.xhtml#sec2)
  - [Weiterführende Literatur](#Chapter02_9783960103516.xhtml#lev11)
- [3 Machine Learning mit DeepChem](#Chapter03_9783960103516.xhtml#ch3)
  - [DeepChem-Datensätze](#Chapter03_9783960103516.xhtml#lev12)
  - [Trainieren eines Modells zur Vorhersage der Toxizität von Molekülen](#Chapter03_9783960103516.xhtml#lev13)
  - [Fallstudie: Trainieren eines MNIST-Modells](#Chapter03_9783960103516.xhtml#lev14)
    - [Der MNIST-Datensatz](#Chapter03_9783960103516.xhtml#sec3)
    - [Eine Konvolutionsarchitektur für MNIST](#Chapter03_9783960103516.xhtml#sec4)
  - [Fazit](#Chapter03_9783960103516.xhtml#lev15)
- [4 Machine Learning mit Molekülen](#Chapter04_9783960103516.xhtml#ch4)
  - [Was ist ein Molekül?](#Chapter04_9783960103516.xhtml#lev16)
  - [Was sind molekulare Bindungen?](#Chapter04_9783960103516.xhtml#sec5)
  - [Molekülgraphen](#Chapter04_9783960103516.xhtml#sec6)
  - [Molekulare Konformationen](#Chapter04_9783960103516.xhtml#sec7)
  - [Chiralität von Molekülen](#Chapter04_9783960103516.xhtml#sec8)
  - [Featurization eines Moleküls](#Chapter04_9783960103516.xhtml#lev17)
  - [SMILES-Strings und RDKit](#Chapter04_9783960103516.xhtml#sec9)
  - [Konnektivitäts-Fingerprints](#Chapter04_9783960103516.xhtml#sec10)
  - [Molekulare Deskriptoren](#Chapter04_9783960103516.xhtml#sec11)
  - [Graph Convolutions](#Chapter04_9783960103516.xhtml#lev18)
  - [Trainieren eines Modells zur Vorhersage der Löslichkeit](#Chapter04_9783960103516.xhtml#lev19)
  - [MoleculeNet](#Chapter04_9783960103516.xhtml#lev20)
  - [SMARTS-Strings](#Chapter04_9783960103516.xhtml#sec12)
  - [Fazit](#Chapter04_9783960103516.xhtml#lev21)
- [5 Biophysikalisches Machine Learning](#Chapter05_9783960103516.xhtml#ch5)
  - [Proteinstrukturen](#Chapter05_9783960103516.xhtml#lev22)
  - [Proteinsequenzen](#Chapter05_9783960103516.xhtml#sec13)
  - [Eine kurze Einführung in die Proteinbindung](#Chapter05_9783960103516.xhtml#sec14)
  - [Biophysikalische Eigenschaften](#Chapter05_9783960103516.xhtml#lev23)
  - [Grid Featurization](#Chapter05_9783960103516.xhtml#sec15)
  - [Atomare Featurization](#Chapter05_9783960103516.xhtml#sec16)
- [6 Deep Learning für Genomik](#Chapter06_9783960103516.xhtml#ch6)
  - [Genomische Daten](#Chapter06_9783960103516.xhtml#lev24)
  - [DNA-Sequenzierung](#Chapter06_9783960103516.xhtml#sec17)
  - [Variantenaufruf](#Chapter06_9783960103516.xhtml#sec18)
  - [Deep Learning für Genomik](#Chapter06_9783960103516.xhtml#lev25)
  - [Fazit](#Chapter06_9783960103516.xhtml#lev26)
- [7 Deep Learning für Mikroskopie](#Chapter07_9783960103516.xhtml#ch7)
  - [Mikroskopische Bildgebung](#Chapter07_9783960103516.xhtml#lev27)
  - [Bildsegmentierung](#Chapter07_9783960103516.xhtml#sec19)
  - [Zellklassifizierung](#Chapter07_9783960103516.xhtml#sec20)
  - [Fazit](#Chapter07_9783960103516.xhtml#lev28)
- [8 Medizinische Analyse mit Deep Learning](#Chapter08_9783960103516.xhtml#ch8)
  - [Klinische Daten](#Chapter08_9783960103516.xhtml#lev29)
  - [Elektronische Patientenakten](#Chapter08_9783960103516.xhtml#sec21)
  - [Medizinische Bildgebung](#Chapter08_9783960103516.xhtml#sec22)
  - [Fazit](#Chapter08_9783960103516.xhtml#lev30)
- [9 Generative Modelle für Biowissenschaften](#Chapter09_9783960103516.xhtml#ch9)
  - [Variational Autoencoder](#Chapter09_9783960103516.xhtml#lev31)
  - [Generative Adversarial Networks](#Chapter09_9783960103516.xhtml#lev32)
  - [Molekülgenerierung](#Chapter09_9783960103516.xhtml#lev33)
  - [Analysieren der Ausgabe des generativen Modells](#Chapter09_9783960103516.xhtml#sec43)
  - [Fazit](#Chapter09_9783960103516.xhtml#lev48)
- [10 Interpretieren von Deep-Learning-Modellen](#Chapter10_9783960103516.xhtml#ch10)
  - [Vorhersagen erklären](#Chapter10_9783960103516.xhtml#lev49)
  - [Eingaben optimieren](#Chapter10_9783960103516.xhtml#lev50)
  - [Unsicherheit vorhersagen](#Chapter10_9783960103516.xhtml#lev51)
  - [Interpretierbarkeit, Erklärbarkeit und reale Konsequenzen](#Chapter10_9783960103516.xhtml#lev52)
  - [Fazit](#Chapter10_9783960103516.xhtml#lev53)
- [11 Beispiel eines virtuellen Screening-Workflows](#Chapter11_9783960103516.xhtml#ch11)
  - [Vorbereiten des Datensatzes](#Chapter11_9783960103516.xhtml#lev54)
  - [Trainieren eines Vorhersagemodells](#Chapter11_9783960103516.xhtml#lev55)
  - [Vorbereiten eines Datensatzes für die Vorhersage](#Chapter11_9783960103516.xhtml#lev56)
  - [Ein Vorhersagemodell anwenden](#Chapter11_9783960103516.xhtml#lev57)
  - [Fazit](#Chapter11_9783960103516.xhtml#lev58)
- [12 Chancen und Perspektiven](#Chapter12_9783960103516.xhtml#ch12)
  - [Medizinische Diagnosen](#Chapter12_9783960103516.xhtml#lev59)
  - [Personalisierte Medizin](#Chapter12_9783960103516.xhtml#lev60)
  - [Arzneimittelentwicklung](#Chapter12_9783960103516.xhtml#lev61)
  - [Biologische Forschung](#Chapter12_9783960103516.xhtml#lev62)
  - [Fazit](#Chapter12_9783960103516.xhtml#lev63)
- [Fußnoten](#Footnote_9783960103516.xhtml)
- [Index](#Index_9783960103516.xhtml#ind)
- [Über die Autoren](#Author_9783960103516.xhtml)
- [Kolophon](#Kolophon_9783960103516.xhtml)

Zu diesem Buch – sowie zu vielen weiteren O’Reilly-Büchern – können Sie auch das entsprechende E-Book im PDF-Format herunterladen. Werden Sie dazu einfach Mitglied bei oreilly.plus^+: [www.oreilly.plus](http://www.oreilly.plus)

---

Bharath Ramsundar, Peter Eastman, Patrick Walters, Vijay Pande

Lektorat: Alexandra Follenius

Übersetzung: Helena Schock

Korrektorat: Sibylle Feldmann, [www.richtiger-text.de](http://www.richtiger-text.de)

Satz: III-satz, [www.drei-satz.de](http://www.drei-satz.de)

Herstellung: Stefanie Weidner

Umschlaggestaltung: Karen Montgomery, Michael Oréal, [www.oreal.de](http://www.oreal.de)

Bibliografische Information Der Deutschen Nationalbibliothek

Die Deutsche Nationalbibliothek verzeichnet diese Publikation in der Deutschen Nationalbibliografie; detaillierte bibliografische Daten sind im Internet über [http://dnb.d-nb.de](http://dnb.d-nb.de) abrufbar.

ISBN:

Print 978-3-96009-130-1

PDF 978-3-96010-353-0

ePub 978-3-96010-351-6

mobi 978-3-96010-352-3

1. Auflage

Translation Copyright für die deutschsprachige Ausgabe © 2020 dpunkt.verlag GmbH

Wieblinger Weg 17

69123 Heidelberg

Authorized German translation of the English edition of *Deep Learning for the Life Sciences*, ISBN 9781492039839 © 2019 Bharath Ramsundar, Peter Eastman, Patrick Walters, and Vijay Pande. This translation is published and sold by permission of O’Reilly Media, Inc., which owns or controls all rights to publish and sell the same.

Dieses Buch erscheint in Kooperation mit O’Reilly Media, Inc. unter dem Imprint »O’REILLY«. O’REILLY ist ein Markenzeichen und eine eingetragene Marke von O’Reilly Media, Inc. und wird mit Einwilligung des Eigentümers verwendet.

*Hinweis:*

Dieses Buch wurde auf PEFC-zertifiziertem Papier aus nachhaltiger Waldwirtschaft gedruckt. Der Umwelt zuliebe verzichten wir zusätzlich auf die Einschweißfolie.

*Schreiben Sie uns:*

Falls Sie Anregungen, Wünsche und Kommentare haben, lassen Sie es uns wissen: [kommentar@oreilly.de](mailto:kommentar@oreilly.de).

Die vorliegende Publikation ist urheberrechtlich geschützt. Alle Rechte vorbehalten. Die Verwendung der Texte und Abbildungen, auch auszugsweise, ist ohne die schriftliche Zustimmung des Verlags urheberrechtswidrig und daher strafbar. Dies gilt insbesondere für die Vervielfältigung, Übersetzung oder die Verwendung in elektronischen Systemen.

Es wird darauf hingewiesen, dass die im Buch verwendeten Soft- und Hardware-Bezeichnungen sowie Markennamen und Produktbezeichnungen der jeweiligen Firmen im Allgemeinen warenzeichen-, marken- oder patentrechtlichem Schutz unterliegen.

Alle Angaben und Programme in diesem Buch wurden mit größter Sorgfalt kontrolliert. Weder Autor noch Verlag noch Übersetzer können jedoch für Schäden haftbar gemacht werden, die in Zusammenhang mit der Verwendung dieses Buches stehen.

5 4 3 2 1 0
