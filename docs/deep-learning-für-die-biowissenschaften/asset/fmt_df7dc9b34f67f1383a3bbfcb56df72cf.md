
Das ist der Kern jedes Regularisierungsverfahrens: den Trainingsprozess so zu beeinflussen, dass bestimmte Modelltypen anderen vorgezogen werden. Sie legen fest, welche Eigenschaften ein »gutes« Modell haben soll und wie es sich von einem overfitteten unterscheidet, und dann teilen Sie dem Trainingsalgorithmus mit, die Modelle mit diesen Eigenschaften zu bevorzugen. Natürlich sind diese Annahmen oftmals eher implizit als explizit. Es mag nicht offensichtlich sein, welche Annahmen bei der Auswahl eines bestimmten Regularisierungsverfahrens gemacht werden. Aber sie sind immer da.

Eine der einfachsten Regularisierungstechniken ist, das Modell kürzer trainieren zu lassen. Zu Beginn des Trainings neigt es dazu, grobe Eigenschaften der Trainingsdaten aufzunehmen, die vermutlich auf die wahren Daten zutreffen. Je länger das Training läuft, desto wahrscheinlicher beginnt es damit, feinere Details der einzelnen Datenpunkte der Trainingsdaten aufzugreifen. Indem die Anzahl der Trainingsschritte beschränkt wird, hat es weniger Gelegenheit zu overfitten. Anders ausgedrückt, man geht davon aus, dass sich »gute« Parameterwerte nicht zu stark von den Werten unterscheiden, mit denen man das Training beginnt.

Eine andere Methode besteht in der Begrenzung der Parameteranzahl im Modell. Zum Beispiel könnte man der Fehlerfunktion folgenden Ausdruck hinzufügen: `|θ|²`, wobei `θ` ein Vektor ist, der alle Modellparameter enthält. Somit nehmen wir an, dass »gute« Parameterwerte nicht größer als nötig sein sollten. Das trägt der Tatsache Rechnung, dass beim Overfitting oftmals (jedoch nicht immer) einige Parameter sehr groß werden.

Ein sehr beliebtes Regularisierungsverfahren ist das *Drop-out*. Für jede verborgene Ebene im Modell wird zufällig eine Gruppe von Elementen im Ausgabevektor `h[i]` ausgewählt und auf 0 gesetzt. Bei jedem Schritt des Gradientenverfahrens wird eine andere zufällige Elementengruppe ausgewählt. Das könnte so aussehen, als würde es das Modell zerstören: Wie kann es funktionieren, wenn interne Berechnungen nach dem Zufallsprinzip auf 0 gesetzt werden? Die zugrunde liegende mathematische Theorie, weshalb Drop-out funktioniert, ist etwas kompliziert. Grob gesagt: Wird Drop-out verwendet, gehen wir davon aus, dass keine der einzelnen Berechnungen im Modell zu wichtig sein sollte. Es sollte möglich sein, einzelne Berechnungen nach dem Zufallsprinzip zu entfernen, ohne dass das restliche Modell davon beeinflusst wird. Dadurch wird es gezwungen, überflüssige, stark verteilte Datendarstellungen zu lernen, die Overfitting unwahrscheinlich machen. Wenn Sie unsicher sind, welche der Regularisierungstechniken Sie benutzen sollten, ist Drop-out eine gute erste Wahl.

## Hyperparameteroptimierung

Inzwischen haben Sie vermutlich festgestellt, dass viele Entscheidungen zu treffen sind, sogar bei einem scheinbar allgemeinen Modell mit einem »allgemeinen« Lernalgorithmus. Beispiele hierfür sind:

*   Die Anzahl der Ebenen im Modell.
*   Die Breite jeder Ebene.
*   Die Anzahl der durchzuführenden Trainingsschritte.
*   Die im Training zu verwendende Lernrate.
*   Der Anteil an Elementen, die bei Verwendung von Drop-out auf 0 gesetzt werden.

Diese Optionen werden *Hyperparameter* genannt. Ein Hyperparameter ist ein Parameter des Modells oder des Trainingsalgorithmus, der im Voraus festgelegt werden muss, statt vom Trainingsalgorithmus gelernt zu werden. Wie nun sollen sie gewählt werden – und ist nicht Sinn und Zweck des Machine Learning, Einstellungen automatisch, basierend auf den Daten, auszuwählen?

Das bringt uns zum Thema *Hyperparameteroptimierung*. Die einfachste Art der Anwendung ist es, einfach viele verschiedene Werte für jeden Hyperparameter auszuprobieren und zu schauen, was am besten funktioniert. Das wird sehr aufwendig, wenn viele Werte für viele Hyperparameter ausprobiert werden sollen. Deshalb gibt es ausgeklügeltere Ansätze, jedoch mit der gleichen Grundidee: Teste verschiedene Kombinationen, um zu sehen, was am besten funktioniert.

Aber woher wissen wir, was am besten funktioniert? Die einfachste Antwort wäre, festzustellen, was den niedrigsten Wert der Fehlerfunktion (oder ein anderes Maß für die Genauigkeit) in den Trainingsdaten verursacht. Beachten Sie jedoch, dass uns das nicht wirklich interessiert. Wir wollen den Fehler in den Testdaten minimieren, nicht den Trainingsdaten. Das ist vor allem für Hyperparameter wichtig, die die Regularisierung betreffen, wie zum Beispiel die Drop-out-Rate. Ein geringer Fehler im Trainingsdatensatz kann bedeuten, dass das Modell overfittet und für die spezifischen Details der Trainingsdaten optimiert ist. Stattdessen wollen wir viele Hyperparameterwerte testen und dann diejenigen anwenden, die den Fehler in den Testdaten minimieren.

Aber das dürfen wir nicht tun! Bedenken Sie: Die Testdaten dürfen in keiner Weise verwendet werden, während das Modell entworfen oder trainiert wird. Deren Aufgabe ist es, Ihnen zu sagen, wie gut das Modell mit neuen Daten arbeiten kann, die es nie zuvor gesehen hat. Nur weil bestimmte Hyperparameter auf einem Testdatensatz am besten arbeiten, kann nicht garantiert werden, dass diese Werte immer am besten funktionieren werden. Wir dürfen nicht zulassen, dass die Testdaten das Modell beeinflussen, sonst ist es kein unvoreingenommener Testdatensatz mehr.

Die Lösung besteht darin, noch einen weiteren Datensatz zu erstellen, den *Validierungsdatensatz*. Dieser darf nicht mit dem Trainings- oder Testdatensatz überlappen. Der vollständige Ablauf sieht nun wie folgt aus:

1.  Für jede Kombination von Hyperparameterwerten wird das Modell auf den Trainingsdaten trainiert, und im Anschluss wird der Fehler anhand der Validierungsdaten berechnet.
2.  Diejenige Hyperparameterkombination, die den geringsten Fehler im Validierungsdatensatz erzeugt, wird als finales Modell akzeptiert.
3.  Das finale Modell wird anhand der Testdaten ausgewertet, um ein unabhängiges Maß dafür zu bekommen, wie gut es funktioniert.

## Weitere Arten von Modellen

Noch eine weitere Entscheidung bleibt zu treffen, und die ist ein großes Thema für sich: Welches Modell soll verwendet werden? Weiter oben in diesem Kapitel wurden mehrlagige Perzeptronen vorgestellt. Ihr Vorteil ist es, eine allgemeine Klasse von Modellen zu sein, die auf viele verschiedene Fragestellungen angewendet werden können. Leider haben sie auch schwerwiegende Nachteile. Sie benötigen eine immense Anzahl an Parametern, die sie anfällig für Overfitting macht. Es ist schwierig, sie zu trainieren, wenn sie mehr als eine oder zwei verborgene Ebenen haben. In vielen Fällen erhält man ein besseres Ergebnis, wenn man ein weniger allgemeines Modell verwendet, das die spezifischen Merkmale der Fragestellung nutzt.

Ein Großteil des Inhalts dieses Buchs befasst sich mit bestimmten Modellarten, die besonders in den Biowissenschaften nützlich sind. Mit denen befassen wir uns in späteren Kapiteln. In dieser Einführung sollten wir jedoch noch zwei sehr wichtige Klassen von Modellen vorstellen, die in vielen verschiedenen Bereichen sehr verbreitet sind. Hierbei handelt es sich um Convolutional Neural Networks und Recurrent Neural Networks.

### Convolutional Neural Networks

*Convolutional Neural Networks* (abgekürzt CNNs) waren mit die ersten Modellklassen, die im Deep Learning weit verbreitet waren. Sie wurden für den Einsatz in der Bildverarbeitung und im Bildverstehen entwickelt. Sie sind nach wie vor eine ausgezeichnete Wahl für viele Fragestellungen, bei denen fortlaufende Daten in einem rechteckigen Raster abgetastet werden: Audiosignale (1-D), Bilder (2-D), volumetrische MRT-Daten (3-D) usw.
