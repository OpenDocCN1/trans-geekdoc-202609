![](bbox=[0.04, 0.09, 0.3, 0.17])

# TIPP Diagramme aktualisieren

Excel aktualisiert das dazugehörige Diagramm automatisch, wenn Sie einen Datenwert verändern. Doch diese Eigenschaft funktioniert auch in die andere Richtung. Dazu markieren Sie in dem gewünschten Diagramm beispielsweise ein Element eines Balkendiagramms.

Ziehen Sie nun mit der Maus am Rand des Balkens die Säule in die gewünschte Höhe. Je nach Veränderung passt sich der Zahlenwert in der Tabelle ebenfalls an. Allerdings bedarf es bei diesem Vorgehen etwas Fingerspitzengefühl, um einen bestimmten Wert zu erreichen.

![](bbox=[0.04, 0.51, 0.28, 0.62])

# TIPP Datenreihe hinzufügen

Excel bietet die einfache Möglichkeit, ein Diagramm mit wenigen Handgriffen um eine Datenreihe zu ergänzen. Sie müssen also nicht immer ein komplettes neues Diagramm erstellen.

Markieren Sie dazu die neue Datenreihe mit der Maus, und bewegen Sie den Mauszeiger auf die Markierungsumrandung. Halten Sie die linke Maustaste gedrückt, und ziehen Sie die Reihe einfach in das bestehende Diagramm. Nach dem Loslassen der Taste fügt Excel die neuen Daten in die Darstellung ein, und alles erscheint im gleichen Layout.

# Nummerierung abhängig vom Inhalt

Sie möchten in einer Spalte eine automatische Nummerierung ausführen – abhängig davon, ob in der Zelle neben der Spalte ein Eintrag vorhanden ist. Hierzu existieren zwei Möglichkeiten.

+   1. In der ersten Variante orientieren Sie sich an der Zellennummerierung von Excel, also mit dem Wert 1 in der ersten Zelle A1 beginnend. Dabei wird überprüft, ob sich ein Wert in der Spalte B befindet.

+   2. Tragen Sie in der Zelle A1 folgende Formel ein:
+   =WENN(NICHT(ISTLEER(B1));ZEILE();)
+   Anschließend kopieren Sie die Formel in die darunter liegenden Zellen.

![](bbox=[0.65, 0.14, 0.95, 0.22])

+   3. Soll hingegen in einer beliebigen Zelle der Spalte A die Nummerierung mit der Zellennummer starten, beispielsweise in der Zelle A12 der Wert 12 stehen, fügen Sie folgende Formel ein:
+   =WENN(NICHT(ISTLEER(B12));ZEILE(A12);)

+   4. Auch hier kopieren Sie anschließend die Formel nach unten.

# Symbolleisten wiederherstellen

Beim Aufspielen einer neuen (aktuellen) Excel-Version auf den Rechner, gehen definierte Symbolleisten im ersten Schritt verloren, denn sie werden nicht standardmäßig übernommen.

Doch mit einigen Handgriffen richten Sie Ihre Symbolleisten wieder so ein, wie Sie es wünschen.

+   1. Wie vor jeder Änderung einer Software fertigen Sie im ersten Schritt eine Sicherung der aktuellen Konfiguration der Symbolleisten an. Denn der Import lässt sich nicht mehr rückgängig machen.

+   2. Beenden Sie dazu Excel, und starten Sie den Windows Explorer. Suchen Sie im Hauptverzeichnis von Windows (\Windows) und im Unterverzeichnis (\Windows\Anwendungsdaten\Microsoft\Excel) nach Dateien mit der Endung xlb. Hier legt Excel die individuellen Konfigurationen der Symbolleisten ab.

+   3. Arbeiten Sie mit Excel innerhalb eines Netzwerkes, finden Sie eine xlb-Datei mit Ihrem Namen und einer nachgestellten 8 (Beispiel: Mustermann8.xlb). Arbeiten Sie auf einem einzelnen Gerät, halten Sie Ausschau nach der Datei Excel.xlb. Dabei steht die 8 für Excel 97, bei Excel 95 suchen Sie nach einer 5. Die neue Version Excel 2000 verzichtet auf eine Zahl.

+   4. Erstellen Sie eine Sicherungskopie der Datei, indem Sie diese unter einem anderen Namen, zum Beispiel Sicher.xlb, ablegen.

+   5. Starten Sie Excel, und laden Sie über den Menüpunkt Datei und Öffnen die ältere xlb-Datei. Noch ändert sich nichts an Ihrer Symbolleiste. Rufen Sie jedoch den Menüpunkt Symbolleisten unter Ansicht auf, zeigt Excel wieder die alten Symbole an. Beachten Sie, dass die importierten Symbole nun ein fester Bestandteil von Excel sind.

# Werte farbig hervorheben

Sie können in Excel Zahlen, abhängig von ihrem Wert, problemlos farbig darstellen.

+   1. Geben Sie die gewünschten Zahlen in ein Excel-Sheet ein. Dabei ist die Anordnung belanglos. Markieren Sie die Werte.

+   2. Gehen Sie per Maus zu den Menüpunkten Format und Zellen. Im Register Zahlen wählen Sie die Kategorie Benutzerdefiniert. In das Eingabefeld geben Sie folgende Parameter ein: [Blau]< =10]#.##0;[Rot]<15]#.##0;[Grün]#.##0
+   
+   Bestätigen Sie die Eingabe. Zahlen bis zum Wert 10 werden nun in Rot, von 11 bis 14 in Blau und ab 15 in Grün dargestellt. Allerdings können Sie nicht mehr als drei Farbzuweisungen vornehmen, da sonst Excel Ihre Eingabe ignoriert.