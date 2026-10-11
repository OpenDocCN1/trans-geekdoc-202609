
# Deep Learning in der Medizin

## Code-Beispiel: U-Net für Bildsegmentierung

```python
learning_rate = dc.models.tensorgraph.optimizers.ExponentialDecay(0.01, 0.9, 250)

model = dc.models.TensorGraph(learning_rate=learning_rate,
                              model_dir='segmentation')

features = layers.Feature(shape=(None, 520, 696, 1)) / 255.0
labels = layers.Label(shape=(None, 520, 696, 1)) / 255.0

# Dreimal herunterrechnen (Downsampling)
conv1 = layers.Conv2D(16, kernel_size=5, stride=2, in_layers=features)
conv2 = layers.Conv2D(32, kernel_size=5, stride=2, in_layers=conv1)
conv3 = layers.Conv2D(64, kernel_size=5, stride=2, in_layers=conv2)

# 1x1-Konvolution (Bottleneck)
conv4 = layers.Conv2D(64, kernel_size=1, stride=1, in_layers=conv3)

# Dreimal hochrechnen (Upsampling mit Skip Connections)
concat1 = layers.Concat(in_layers=[conv3, conv4], axis=3)
deconv1 = layers.Conv2DTranspose(32, kernel_size=5, stride=2, in_layers=concat1)

concat2 = layers.Concat(in_layers=[conv2, deconv1], axis=3)
deconv2 = layers.Conv2DTranspose(16, kernel_size=5, stride=2, in_layers=concat2)

concat3 = layers.Concat(in_layers=[conv1, deconv2], axis=3)
deconv3 = layers.Conv2DTranspose(1, kernel_size=5, stride=2, in_layers=concat3)

# Berechnen der Ausgabe
concat4 = layers.Concat(in_layers=[features, deconv3], axis=3)
logits = layers.Conv2D(1, kernel_size=5, stride=1, activation_fn=None,
                       in_layers=concat4)
output = layers.Sigmoid(logits)

model.add_output(output)

loss = layers.ReduceSum(layers.SigmoidCrossEntropy(in_layers=(labels, logits)))
model.set_loss(loss)
```

Dieser Aufbau ist etwas komplexer als der für das Zählen von Zellen, aber wir verwenden dieselbe Grundstruktur aus gestapelten Konvolutionsschichten, um unser gewünschtes Modell zu erhalten. Auch hier nutzen wir ein vortrainiertes Modell, um den Aufbau zu testen. Anweisungen zum Herunterladen des vortrainierten Modells finden sich im Code-Repository des Buchs (*https://github.com/deepchem/DeepLearningLifeSciences*). Sobald Sie die vortrainierten Gewichte übertragen haben, können Sie die Gewichte laden:

```python
model.restore()
```

Mithilfe dieses Modells erstellen wir einige Masken. Mit `model.predict_on_batch()` können wir die Maske für ein Eingabebatch vorhersagen. Die Genauigkeit unserer Vorhersagen überprüfen wir, indem wir unsere Masken mit den Masken des Ground-Truth-Datensatzes vergleichen und den Anteil der Überlappung prüfen:

```python
scores = []

for x, y, w, id in test_dataset.itersamples():
    y_pred = model.predict_on_batch([x]).squeeze()
    scores.append(np.mean((y > 0) == (y_pred > 0.5)))

print(np.mean(scores))
```

Der ausgegebene Wert sollte ungefähr `0.9899` betragen. Das bedeutet, dass fast 99 % der Pixel korrekt vorhergesagt werden! Es ist ein ordentliches Ergebnis, aber bedenken Sie, dass es sich hierbei um ein sehr einfaches Beispiel handelt. Ein Bildverarbeitungsalgorithmus mit einem Grenzwert für die Bildhelligkeit würde wahrscheinlich genauso gut funktionieren. Die hier vorgestellten Schritte sollten sich jedoch auch auf komplexere Bilddatensätze übertragen lassen.

Nachdem wir uns mit dem vortrainierten Modell befasst haben, wollen wir ein U-Net 50 Epochen lang trainieren:

```python
model.fit(train_dataset, nb_epoch=50, checkpoint_interval=100)
```

Dieses Training ist rechenintensiv und wird auf einer guten GPU einige Stunden laufen. Eventuell ist es nicht möglich, dieses Modell auf einem CPU-System zu trainieren. Sobald das Training abgeschlossen ist, werten Sie die Ergebnisse selbstständig aus. Erreichen Sie die Genauigkeit des vortrainierten Modells?

## Rechnergestützte Assays

Das Zählen und Segmentieren von Zellen ist eine relativ unkomplizierte visuelle Aufgabe. Daher ist es wenig verwunderlich, dass Machine-Learning-Modelle gute Leistungen bei diesen Aufgaben erbringen. Man mag sich nun fragen, ob das alles ist, was Machine Learning kann.

Zum Glück lautet die Antwort: Nein! Machine-Learning-Modelle können subtile Signale im Datensatz erfassen. Eine Studie hat beispielsweise gezeigt, dass Deep-Learning-Modelle die Ergebnisse fluoreszierender Labels anhand des Quellbilds vorhersagen können.[^3] Wie wir in „Vorbereiten biologischer Proben für die Mikroskopie“ auf Seite 112 gesehen haben, kann die Fluoreszenzfärbung sehr aufwendig sein. Es ist erstaunlich, dass Deep Learning in der Lage sein könnte, einige der erforderlichen Vorbereitungsarbeiten zu übernehmen.

Auch wenn das ein aufregendes Ergebnis ist, stehen wir doch noch am Anfang. Es ist weiterhin viel Arbeit notwendig, um diese Methoden zu „stabilisieren“, damit sie eine breitere Anwendung finden können.

## Fazit

In diesem Kapitel haben wir die Grundlagen der Mikroskopie und einige grundlegende Machine-Learning-Ansätze für Mikroskopiesysteme vorgestellt. Wir haben eine umfassende Einführung in einige grundlegende Fragen der modernen Mikroskopie gegeben (insbesondere in Bezug auf biologische Probleme) und erörtert, in welchen Bereichen Deep Learning bereits zum Einsatz kommt und wo zukünftige Einsatzgebiete liegen könnten.

Des Weiteren haben wir einen ausführlichen Überblick über einige physikalische und biologische Aspekte der Mikroskopie gegeben und versucht, zu vermitteln, warum dieses Wissen auch für Entwickler nützlich sein kann, die in erster Linie an der Erstellung effektiver Pipelines für die Handhabung von Mikroskopaufnahmen und -modellen interessiert sind. Die Kenntnis physikalischer Regeln, wie der Beugungsgrenze, ermöglicht es, zu verstehen, warum unterschiedliche Mikroskopietechniken verwendet werden und wie Deep Learning hierfür in der Zukunft bedeutend sein kann. Kenntnisse zu biologischen Probenvorbereitungstechniken helfen, die Arten von Metadaten und Annotationen zu verstehen, die für die Entwicklung eines Mikroskopiesystems wichtig sind.

Obwohl wir uns über die möglichen Anwendungen von Deep-Learning-Methoden in der Mikroskopie freuen, ist es uns wichtig, zu betonen, dass diese Methoden nicht ohne Vorbehalte sind. Zum einen haben mehrere neuere Studien die Empfindlichkeit visueller Konvolutionsmodelle hervorgehoben.[^4] Einfache Artefakte können solche Modelle ins Stolpern bringen und erhebliche Probleme verursachen. Ist beispielsweise das Bild eines Stoppschilds verwackelt, könnte es von einem Modell als grüne Ampel klassifiziert werden. Für ein selbstfahrendes Auto wäre das katastrophal!

Es lohnt sich also, zu fragen, welche Schwierigkeiten bei der Deep-Mikroskopie bestehen. Ist es möglich, dass Deep-Mikroskopie-Modelle einfach aus gespeicherten früheren Datenpunkten aufgefüllt werden? Auch wenn dies nicht die ganze Erklärung für ihre Leistung ist, ist es wahrscheinlich, dass zumindest ein Teil der Leistungsfähigkeit dieser Modelle aus einem solchen Rückfluss gespeicherter Daten stammt. Dies könnte in falschen Korrelationen resultieren. Daher ist es bei der wissenschaftlichen Analyse mikroskopischer Datensätze wichtig, zu hinterfragen, ob Ergebnisse auf Artefakte im Modell oder auf tatsächliche biologische Phänomene zurückzuführen sind. In den folgenden Kapiteln werden wir einige Tools vorstellen, mit denen Sie Modelle kritisch untersuchen können, um festzustellen, was Ihr Modell tatsächlich gelernt hat.

Im nächsten Kapitel betrachten wir die Anwendung von Deep Learning in der Medizin. Wir werden viele der in diesem Kapitel behandelten Themen für das visuelle Deep Learning wiederverwenden.

# KAPITEL 8

## Deep Learning in der Medizin

Wie wir im letzten Kapitel gesehen haben, ist die Fähigkeit, aussagekräftige Informationen aus visuellen Datensätzen zu extrahieren, nützlich für die Analyse von Mikroskopieaufnahmen. Die Verarbeitung visueller Daten ist auch für medizinische Anwendungen wertvoll. Heutzutage müssen Ärzte in der Lage sein, medizinische Scans kritisch zu analysieren. Deep Learning könnte diese Analysen einfacher und schneller (aber eventuell schwieriger zu deuten) machen.

[^3]: Fußnotenverweis 3
[^4]: Fußnotenverweis 4
