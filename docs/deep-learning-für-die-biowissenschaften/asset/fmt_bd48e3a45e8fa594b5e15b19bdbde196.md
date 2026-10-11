
Glücklicherweise gibt es eine einfache Lösung: Die Gewichtsmatrix des Datensatzes lässt sich anpassen, um dies zu kompensieren. `BalancingTransformer` passt die Gewichte einzelner Datenpunkte so an, dass das jeder Klasse zugewiesene Gesamtgewicht gleich ist. Somit hat die Fehlerfunktion keine systematische Vorliebe für eine Klasse. Der Fehler kann nur gesenkt werden, indem das Modell lernt, richtig zwischen den Klassen zu unterscheiden.

Jetzt, da wir die Tox21-Datensätze untersucht haben, können wir ergründen, wie wir Modelle auf diesen Datensätzen trainieren können. DeepChem hat ein Untermodul namens `dc.models`, das eine Vielzahl unterschiedlicher Modelle speziell für die Biowissenschaften enthält. Diese unterschiedlichen Modelle erben alle von der Elternklasse `dc.models.Model`, die eine allgemeine API bereitstellt, die den in Python üblichen Konventionen folgt. Wenn Sie bereits andere Machine-Learning-Bibliotheken in Python benutzt haben, werden Sie feststellen, dass Ihnen viele der `dc.models.Model`-Methoden vertraut sind.

In diesem Kapitel werden wir uns mit dem Aufbau dieser Modelle nicht wirklich im Detail befassen. Stattdessen geben wir ein Beispiel dafür, wie ein grundlegendes DeepChem-Modell instanziiert wird, `dc.models.MultitaskClassifier`. Dieses Modell erzeugt ein vollständig verbundenes Netz (ein MLP), das Eingabeeigenschaften mehreren Vorhersagen zuordnet. Das ist nützlich für *Multitasking*, bei dem es mehrere Labels pro Datenpunkt gibt. Es eignet sich gut für unseren Tox21-Datensatz, da wir insgesamt zwölf unterschiedliche Assays haben, die wir zeitgleich vorhersagen wollen. So erzeugen wir einen `MultitaskClassifier` in DeepChem:

```
model = dc.models.MultitaskClassifier(n_tasks=12,
    n_features=1024,
    layer_sizes=[1000])
```

Gehen wir nun kurz auf die verschiedenen Optionen ein, die es hier gibt. `n_tasks` ist die Anzahl der Aufgaben, und `n_features` ist die Anzahl der Eingabemerkmale jedes Datenpunkts. Wie wir bereits gesehen haben, hat der Tox21-Datensatz zwölf Aufgaben und 1.024 Merkmale für jeden Datenpunkt. Bei `layer_sizes` handelt es sich um eine Liste, die die Anzahl der vollständig verbundenen verborgenen Ebenen im Netz festlegt sowie deren jeweilige Breite. In diesem Fall definieren wir eine verborgene Ebene mit 1.000 Neuronen.

Wie können wir unser Modell auf den Tox21-Datensätzen trainieren, da wir es nun erstellt haben? Jedes `Model`-Objekt hat die Methode `fit()`, die das Modell an die in einem `Dataset`-Objekt enthaltenen Daten anpasst. Um `MultitaskClassifier` aufzurufen, reicht folgender Befehl:

```
model.fit(train_dataset, nb_epoch=10)
```

Wir haben dem Aufruf `nb_epoch=10` hinzugefügt. Dadurch wird das Gradientenverfahren in zehn Epochen während des Trainings durchgeführt. Eine *Epoche* entspricht einem vollständigen Durchlauf aller Elemente eines Datensatzes. Um ein Modell zu trainieren, werden die Trainingsdaten in Batches aufgeteilt, und für jedes Batch wird ein Schritt des Gradientenverfahrens durchgeführt. Im Idealfall erhalten Sie ein gut optimiertes Modell, bevor Ihnen die Daten ausgehen. In Wirklichkeit sind meistens nicht genügend Daten vorhanden, sodass Ihnen die Daten ausgehen, bevor das Modell optimiert ist. Daher müssen Daten wiederverwendet werden und zusätzliche Durchläufe durch den Datensatz erfolgen. Auf diese Weise kann ein Modell mit geringeren Datenmengen trainiert werden, aber je mehr Epochen verwendet werden, desto wahrscheinlicher erhält man ein überangepasstes Modell.

Als Nächstes bewerten wir die Leistung des trainierten Modells. Um zu bewerten, wie gut ein Modell funktioniert, muss eine Maßzahl gewählt werden. Die Deep-Chem-Klasse `dc.metrics.Metric` bietet eine allgemeine Möglichkeit, Maßzahlen für Modelle anzugeben. Für Tox21 ist der ROC AUC Score eine sinnvolle Metrik. Beachten Sie jedoch folgende Feinheit: Es gibt mehrere Tox21-Aufgaben. Für welche berechnen wir ROC AUC? Eine gute Vorgehensweise wäre, den mittleren ROC AUC Score über alle Aufgaben zu berechnen:

```
metric = dc.metrics.Metric(dc.metrics.roc_auc_score, np.mean)
```

Da wir `np.mean` angegeben haben, wird der Mittelwert der ROC AUC Scores über alle Aufgaben ausgegeben. DeepChem-Modelle unterstützen die Bewertungsfunktion `model.evaluate()`, die die Leistung des Modells für einen bestimmten Datensatz und eine gegebene Maßzahl auswertet.

### ROC AUC

Wir wollen Moleküle als toxisch oder nicht toxisch einstufen, das Modell gibt jedoch stetige Zahlen aus, keine diskreten Vorhersagen. In der Praxis wird ein Schwellenwert gewählt und vorhergesagt, dass ein Molekül toxisch ist, wenn der Ausgabewert den Schwellenwert überschreitet. Ein niedriger Grenzwert führt zu vielen Falsch Positiven (ein nicht toxisches Molekül wird als toxisch eingestuft). Ein hoher Grenzwert erzeugt weniger Falsch Positive, aber mehr Falsch Negative (ein toxisches Molekül wird fälschlicherweise als nicht toxisch eingestuft).

Die *Receiver Operating Characteristic*-(ROC-)Kurve bietet eine bequeme Möglichkeit, diesen Kompromiss zu visualisieren. Man testet viele verschiedene Grenzwerte und zeichnet dann eine Kurve der Sensitivität gegen die Falsch-Positiv-Rate bei jeder Änderung des Schwellenwerts. Ein Beispiel finden Sie in [Abbildung 3-1](#Chapter03_9783960103516.xhtml#abb3-1).

Der ROC AUC ist die Gesamtfläche unter der ROC-Kurve. Die *Fläche unter der Kurve* (auch AUC) gibt einen Hinweis auf die Fähigkeit des Modells, verschiedene Klassen zu unterscheiden. Sollte es einen Grenzwert geben, bei dem jeder Datenpunkt richtig eingeordnet wird, beträgt der ROC-AUC-Wert 1. Gibt das Modell hingegen völlig zufällige Werte aus, die sich nicht auf die wahren Klassen beziehen, beträgt der ROC-AUC-Wert 0.5. Dadurch kann anhand des ROC AUC die Leistung des Klassifikators beurteilt werden. Es handelt sich zwar nur um eine Heuristik, aber eine beliebte.

```
train_scores = model.evaluate(train_dataset, [metric], transformers)
test_scores = model.evaluate(test_dataset, [metric], transformers)
```

Schauen wir uns nun die berechneten Werte an!

```
In : print(train_scores)
Out: {'mean-roc_auc_score': 0.9659541853946179}

In : print(test_scores)
Out: {'mean-roc_auc_score': 0.7915464001982299}
```

Wie Sie sehen, ist der ROC-AUC-Wert basierend auf den Trainingsdaten mit 0.96 viel höher als der auf den Testdaten mit 0.79. Somit wurde das Modell überangepasst. Der auf den Testdaten basierende Wert ist derjenige, der uns tatsächlich interessiert. Diese Zahlen sind nicht die bestmöglichen für diesen Datensatz – zum Zeitpunkt des Schreibens liegt der aktuellste ROC-AUC-Wert für den Tox21-Datensatz bei etwas unter 0.9 – für ein sofort gebrauchsfertiges System sind sie jedoch nicht schlecht. Die vollständige ROC-Kurve für eine der zwölf Aufgaben stellt [Abbildung 3-1](#Chapter03_9783960103516.xhtml#abb3-1) dar.

![image](Images/p34-1.png)

*Abbildung 3-1: Die ROC-Kurve für eine der zwölf Aufgaben. Die gepunktete Diagonale zeigt, wie die Kurve für ein völlig zufällig geschätztes Modell aussehen würde. Die tatsächliche Kurve liegt deutlich über der Diagonalen, somit schneiden wir viel besser ab als eine zufällige Schätzung.*

## Fallstudie: Trainieren eines MNIST-Modells

Im vorangegangenen Abschnitt haben wir die Grundlagen zum Trainieren eines Machine-Learning-Modells mit DeepChem vorgestellt, wir haben jedoch die vorgefertigte Modellklasse `dc.models.MultitaskClassifier` verwendet. Manchmal möchte man eine neue Modellarchitektur erschaffen, anstatt eine vorgefertigte zu nutzen. In diesem Abschnitt stellen wir vor, wie ein Convolutional Neural Network auf dem MNIST-Datensatz trainiert wird. Anstatt ein vorgefertigtes Modell wie im vorhergehenden Abschnitt einzusetzen, werden wir dieses Mal die komplette Deep-Learning-Architektur selbst festlegen. Hierfür stellen wir die Klasse `dc.models.TensorGraph` vor, die ein Framework zum Erstellen tiefer Architekturen in DeepChem bereitstellt.
