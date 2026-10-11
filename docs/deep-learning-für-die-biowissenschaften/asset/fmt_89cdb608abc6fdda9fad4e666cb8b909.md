
prev = layers.Conv1D(filters=10, kernel_size=10,
activation=tf.nn.relu, padding='same',
in_layers=prev)

prev = layers.Dropout(dropout_prob=0.3, in_layers=prev)

output = layers.Dense(out_channels=1, activation_fn=tf.sigmoid,
in_layers=layers.Flatten(prev))

model.add_output(output)

loss = layers.ReduceMean(layers.L2Loss(in_layers=[labels, output]))

model.set_loss(loss)

Mit nur wenigen Unterschieden ähnelt dieses Modell dem, das wir für die TF-Bindung verwendet haben. Da mit kürzeren Sequenzen gearbeitet und mit weniger Daten trainiert wird, wurde die Größe des Modells reduziert. Es gibt nur zwei Konvolutionsschichten und zehn Filter pro Ebene anstatt 15. Außerdem werden keine Gewichte benötigt, da jede Probe bei der Optimierung gleich viel beitragen soll.

Wir verwenden auch eine andere Fehlerfunktion. Bei dem Modell für die TF-Bindung handelte es sich um ein Klassifizierungsmodell. Jedes Label hatte den Wert 0 oder 1, und wir versuchten, vorherzusagen, welcher dieser beiden Werte es war. Hier handelt es sich jedoch um ein Regressionsmodell. Die Labels sind fortlaufende Zahlen, und das Modell versucht, sich diesen so weit wie möglich zu nähern. Aus diesem Grund verwenden wir die Distanz `L2` als Fehlerfunktion, die versucht, die mittlere quadratische Differenz zwischen den tatsächlichen und den vorhergesagten Labels zu minimieren.

Hier der Code zum Trainieren des Modells:

```
train = dc.data.DiskDataset('train_siRNA')
valid = dc.data.DiskDataset('valid_siRNA')
metric = dc.metrics.Metric(dc.metrics.pearsonr, mode='regression')
for i in range(20):
    model.fit(train, nb_epoch=10)
    print(model.evaluate(train, [metric]))
    print(model.evaluate(valid, [metric]))
```

Bei der TF-Bindung haben wir ROC AUC zur Bewertung unseres Modells verwendet, die misst, wie genau das Modell die Daten in zwei Klassen aufteilen kann. Dies ist für ein Klassifizierungsmodell angemessen, für ein Regressionsmodell jedoch nicht sinnvoll. Daher nutzen wir den Pearson-Korrelationskoeffizienten. Hierbei handelt es sich um eine Zahl zwischen –1 und 1, wobei 0 bedeutet, dass das Modell überhaupt keine Information liefert, und 1, dass das Modell die experimentellen Daten perfekt reproduziert.

Das Ergebnis sehen Sie in [Abbildung 6-4](#Chapter06_9783960103516.xhtml#abb6-4). Der Wert für die Validierungsdaten erreicht nach 50 Epochen den Höchstwert von 0.65. Der Wert für die Trainingsdaten steigt weiter an. Da der Wert für die Validierungsdaten jedoch nicht weiter verbessert wird, handelt es sich um Overfitting. Aufgrund der Einfachheit des Modells und der begrenzten Menge an Trainingsdaten ist ein Korrelationskoeffizient von 0.65 ziemlich gut. Komplexere Modelle, die auf größeren Datensätzen trainiert wurden, schneiden zwar etwas besser ab, jedoch ist dies bereits eine respektable Leistung.

![image](Images/p99-1.png)

*Abbildung 6-4: Die Entwicklung des Pearson-Korrelationskoeffizienten während des Trainings für die Trainingsdaten (gestrichelte Linie) und die Validierungsdaten (durchgehende Linie).*

### Fazit

Ein Genom ist eine enorm komplizierte Maschine, bei der eine Vielzahl von Teilen zusammenarbeitet, um die Herstellung von Proteinen und anderen Molekülen zu steuern und auszuführen. Deep Learning ist ein mächtiges Werkzeug, um es zu untersuchen. Neuronale Netze können subtile Muster in genomischen Daten erkennen, Einblicke in die Funktionsweise des Genoms gewähren und Vorhersagen darüber treffen.

Mehr noch als die meisten anderen Bereiche der Biowissenschaften liefert die Genomik riesige Mengen experimenteller Daten. Beispielsweise enthält eine einzelne menschliche Genomsequenz mehr als sechs Milliarden Basen. Herkömmliche statistische Methoden tun sich schwer damit, das in all diesen Daten verborgene Signal zu finden. Oftmals erfordern sie vereinfachende Annahmen, die die Komplexität der Genomregulation nicht widerspiegeln. Deep Learning ist hervorragend dazu geeignet, diese Daten zu verarbeiten und unser Verständnis der wesentlichen Aufgaben lebender Zellen zu verbessern.

## KAPITEL 7

## Machine Learning in der Mikroskopie

In diesem Kapitel stellen wir Deep-Learning-Techniken für die Mikroskopie vor. In solchen Anwendungen wird versucht, die biologische Struktur eines mikroskopischen Bilds zu verstehen. Beispielsweise wollen wir einen bestimmten Zelltyp in einem vorliegenden Bild zählen oder bestimmte Organellen identifizieren. Die Mikroskopie ist eines der grundlegendsten Instrumente der Biowissenschaften, und die Fortschritte in der Mikroskopie haben die Humanwissenschaften bedeutend vorangetrieben. Imstande zu sein, biologische Objekte wie Zellen visuell zu untersuchen, schafft ein intuitives Verständnis der zugrunde liegenden Mechanismen des Lebens. Eine lebendige Visualisierung von Zellkernen und Zytoskeletten (wie in [Abbildung 7-1](#Chapter07_9783960103516.xhtml#abb7-1)) erzeugt ein viel tieferes Verständnis als eine trockene Erörterung in einem Lehrbuch.

![image](Images/p101-1.png)

*Abbildung 7-1: Menschliche SK8/18-2-Zellen. Diese Zellen werden eingefärbt, um ihre Kerne und Zytoskelette hervorzuheben, und unter Verwendung von Fluoreszensmikroskopie abgebildet. (Quelle: Wikimedia, [https://commons.wikimedia.org/wiki/File:SK8-18-2_human_derived_cells,_fluorescence_microscopy_(29942101073).jpg](https://commons.wikimedia.org/wiki/File:SK8-18-2_human_derived_cells,_fluorescence_microscopy_(29942101073).jpg))*

Es bleibt die Frage, was Deep Learning in der Mikroskopie bewegen kann. Bis vor Kurzem konnten Mikroskopbilder nur analysiert werden, indem Menschen (häufig Doktoranden oder wissenschaftliche Mitarbeiter) diese Bilder manuell auf nützliche Muster untersuchten. Neuerdings haben Instrumente, wie CellProfiler ([https://cellprofiler.org/](https://cellprofiler.org/)), es Biologen ermöglicht, automatisch Pipelines für den Umgang mit Bilddaten aufzubauen.

### Automatisierte Hochdurchsatz-Mikroskopbildanalyse

Fortschritte in der Automatisierung innerhalb der letzten Jahrzehnte ermöglichten die Durchführung automatisierter Hochdurchsatz-Mikroskopie auf einigen Systemen. Diese Systeme verwenden eine Kombination aus einfacher Robotik (für die automatisierte Handhabung der Proben) und Bildverarbeitungsalgorithmen, um Bilder automatisch zu verarbeiten. Die Bildverarbeitungsanwendungen können beispielsweise Vordergrund und Hintergrund von Zellen trennen und einfache Zellenzahlen ermitteln sowie andere grundlegende Messungen durchführen. Darüber hinaus helfen Instrumente wie CellProfiler Biologen ohne Programmiererfahrung, neue automatisierte Pipelines für den Umgang mit zellulären Daten zu erstellen.

Automatisierte Mikroskopiesysteme wurden jedoch von jeher mit einer Reihe von Einschränkungen konfrontiert. Zum einen konnten komplexe visuelle Aufgaben nicht von vorhandenen Bilderkennungs-Pipelines ausgeführt werden. Des Weiteren erfordert die ordnungsgemäße Vorbereitung der Proben für die Analyse vom Wissenschaftler, der das Experiment durchführt, ein erhebliches Maß an Erfahrung. Aus den genannten Gründen verblieb die automatisierte Mikroskopie eine Nischenmethode, obwohl sie anspruchsvolle neue Experimente ermöglicht.

Für die Erweiterung der Möglichkeiten von Instrumenten wie CellProfiler ist Deep Learning daher vielversprechend. Wenn Deep-Learning-Methoden komplexere Analysen durchführen können, könnte die automatisierte Mikroskopie ein wesentlich effektiveres Werkzeug sein. Deshalb besteht ein großes Forschungsinteresse an der Deep-Mikroskopie, wie wir im weiteren Verlauf dieses Kapitels sehen werden.
