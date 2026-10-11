
# Die PDBBind-Fallstudie

## Der PDBBind-Datensatz

## Merkmale entwickeln im PDBBind-Datensatz

## Fazit

# 6 Deep Learning in der Genomik

## DNA, RNA und Proteine

## Und nun zur Wirklichkeit

## Transkriptionsfaktor-Bindung

### Ein Konvolutionsmodell für die TF-Bindung

## Zugänglichkeit von Chromatin

## RNA-Interferenz

## Fazit

# 7 Machine Learning in der Mikroskopie

## Eine kurze Einführung in die Mikroskopie

### Zeitgemäße Lichtmikroskopie

## Die Beugungsgrenze

### Elektronen- und Rasterkraftmikroskopie

### Superauflösende Mikroskopie

### Deep Learning und die Beugungsgrenze?

## Vorbereiten biologischer Proben für die Mikroskopie

### Einfärben der Proben

### Fixierung der Probe

### Schneiden der Probe

### Fluoreszenzmikroskopie

### Artefakte der Probenvorbereitung

## Deep-Learning-Anwendungen

### Die Zellzählung

### Zellsegmentierung

### Rechnergestützte Assays

## Fazit

# 8 Deep Learning in der Medizin

## Computerunterstützte Diagnostik

### Probabilistische Diagnosen mit Bayes’schen Netzen

## Die elektronische Gesundheitsakte

### Worin liegen die Gefahren großer EHR-Datenbanken?

## Deep Radiology

### Röntgenaufnahmen und CT-Scans

### Histologie

### MRT-Scans

## Lernmodelle als Therapeutika

### Diabetische Retinopathie

## Fazit

### Ethische Überlegungen

### Arbeitsplatzverluste

### Zusammenfassung

# 9 Generative Modelle

## Variational Autoencoder

## Generative Adversarial Networks

## Anwendungen generativer Modelle in den Biowissenschaften

### Entwicklung neuer Ideen für die Kernstrukturen

### Proteindesign

### Ein Tool für wissenschaftliche Entdeckungen

### Die Zukunft generativer Modellierung

## Mit generativen Modellen arbeiten

### Analysieren der Ausgabe des generativen Modells

## Fazit

# 10 Interpretieren von Deep-Learning-Modellen

## Vorhersagen erklären

## Eingaben optimieren

## Unsicherheit vorhersagen

## Interpretierbarkeit, Erklärbarkeit und reale Konsequenzen

## Fazit

# 11 Beispiel eines virtuellen Screening-Workflows

## Vorbereiten des Datensatzes

## Trainieren eines Vorhersagemodells

## Vorbereiten eines Datensatzes für die Vorhersage

## Ein Vorhersagemodell anwenden

## Fazit

# 12 Chancen und Perspektiven

## Medizinische Diagnosen

## Personalisierte Medizin

## Arzneimittelentwicklung

## Biologische Forschung

## Fazit

# Index

# Vorwort

In den vergangenen Jahren sind die Biowissenschaften und Data Science zusammengewachsen. Fortschritte in der Robotik und der Automatisierungstechnik haben es Chemikern und Biologen ermöglicht, riesige Datenmengen zu erzeugen. Heutzutage können Wissenschaftler innerhalb eines Tages mehr Daten erzeugen als ihre Vorgänger vor 20 Jahren während ihrer gesamten Laufbahn. Die Fähigkeit, Daten schnell zu generieren, hat auch zu einer Reihe neuer wissenschaftlicher Herausforderungen geführt. Die Zeit ist vorbei, in der Daten verarbeitet werden, indem sie in eine Tabelle geladen und einige Graphen erstellt werden. Um wissenschaftliche Erkenntnisse aus diesen Daten gewinnen zu können, müssen wir heute in der Lage sein, verborgene Zusammenhänge zu identifizieren und zu extrahieren.

Eine Methode, die sich in den letzten Jahren als wirksames Instrument zur Identifizierung von Mustern und Beziehungen in Daten herauskristallisiert hat, ist *Deep Learning*. Dabei handelt es sich um Algorithmen, die die Ansätze zur Lösung von Problemen bei Bildanalyse, Sprachübersetzung und Spracherkennung revolutioniert haben. Deep-Learning-Algorithmen zeichnen sich durch die Identifizierung und Nutzung von Mustern in großen Datenmengen aus. Deswegen findet Deep Learning breite Anwendung in allen Bereichen der Biowissenschaften. Dieses Buch vermittelt einen Überblick darüber, wie Deep Learning in einer Vielzahl von Bereichen eingesetzt wird, darunter Genetik, Arzneimittelforschung und ärztlicher Diagnose. Viele der vorgestellten Beispiele werden von Programmcode begleitet, der eine praktische Einführung in die Methoden bietet und Ihnen einen Ausgangspunkt für eigene Erkundungen gibt.

## Die in diesem Buch verwendeten Konventionen

In diesem Buch werden die folgenden typografischen Konventionen verwendet:

*`Kursiv`*

Kennzeichnet neue Begriffe, URLs, E-Mail-Adressen, Dateinamen und Dateierweiterungen.

`Feste Zeichenbreite`

Kennzeichnet Programmlistings sowie Programmelemente in Absätzen, wie etwa Variablen- oder Funktionsnamen, Datenbanken, Datentypen, Umgebungsvariablen, Anweisungen und Schlüsselwörter.

**`Feste Zeichenbreite fett`**

Zeigt Befehle oder anderen Text an, der vom Benutzer wortwörtlich eingegeben werden soll.

*`Feste Zeichenbreite kursiv`*

Kennzeichnet Text, der durch Werte ersetzt werden soll, die der Benutzer vorgibt oder die sich aus dem Kontext ergeben.

| ![image](Images/cat.jpg) || Dieses Symbol kennzeichnet einen Tipp oder Vorschlag. |
| --- | --- |
| ![image](Images/crow.jpg) || Dieses Symbol zeigt eine allgemeine Bemerkung. |
| ![image](Images/insert.jpg) || Dieses Element symbolisiert einen Warnhinweis. |

## Verwendung von Codebeispielen
