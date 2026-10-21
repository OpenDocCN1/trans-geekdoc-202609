
## Excel

### TIPP Arbeiten mit der Auswahlliste

Bei Listen, in denen sich Eintragungen wiederholen, können Sie mit einem kleinen Trick die Schreibarbeit abkürzen. Klicken Sie in die nächste freie Zelle unterhalb Ihrer Liste und dort auf die rechte Maustaste. Im jetzt eingeblendeten Kontextmenü wählen Sie den Befehl „Auswahlliste“. Alle bereits vorgenommenen Eintragungen werden angezeigt und können durch einen Mausklick auf den entsprechenden Eintrag komfortabel übernommen werden.

![](img/5f36a0372e5f0f300d0bad16e6a18053_97_0.png)

7 In das Feld „Datenbankfeld“ geben Sie die Koordinate der Überschrift „GEHALT“, zum Beispiel „C1“, ein. Das Feld „Suchkriterien“ erwartet die Eingabe der Koordinaten zur Auswahl, in unserem Beispiel also den Bereich, in dem Sie „ABT“ und „EK“ geschrieben haben. Ein Klick auf die Schaltfläche „Ende“ berechnet die Summe der Gehälter für die Abteilung Einkauf.

8 Wenn Sie den Abteilungsnamen im Kriterienbereich ändern, wird die neue Summe der Gehälter sofort ausgerechnet und dargestellt.

9 Die Datenbankfunktionen arbeiten alle nach dem gleichen Schema: Als erstes muss der

Datenbereich der auszuwertenden Liste eingegeben werden, dann die Überschrift der auszuwertenden Spalte und zum Schluss das Suchkriterium. Es gibt insgesamt zwölf Datenbankfunktionen in Excel, von der Berechnung der Anzahl bis zur Varianzberechnung. Peter Schnoor/jh

![](img/5f36a0372e5f0f300d0bad16e6a18053_97_1.png)

## Mit Hilfe des Solvers zum Ziel gelangen

Lösen Sie Ihre komplexen Rechenprobleme mit Hilfe der Solverfunktion in Excel. Bei der „Zielwertsuche“ wird ein einzelner Wert so lange verändert, bis er das gewünschte Ergebnis liefert. Wenn das angestrebte Ergebnis aber von mehreren Werten abhängt, so kann es mit Hilfe der „Solverfunktion“ sehr einfach herausgefunden werden.

Der Optimalwert einer Berechnung mit dem „Solver“ wird durch folgende Elemente bestimmt: die „Zielzelle, die „veränderbaren Zellen“ und die „Nebenbedingungen“. Am Beispiel der Zielwertsuche können Sie auch die „Solverfunktionen“ ausprobieren.

1 Klicken Sie auf den Menübefehl „Extras“. Im folgenden Untermenü wählen Sie den Befehl „Solver“ aus. Das Dialogfenster „Solver-Parameter“ öffnet sich.

2 In das Eingabefeld „Zielzelle“ im Dialogfeld geben Sie den Wert „$B$4“ ein. In der Zeile „Zielwert“ aktivieren Sie die Option „Wert“ und in das Feld „Wert“ tippen Sie anschließend eine „0“ ein.

3 Im Bereich der „veränderbaren Zellen“ klicken Sie auf die Schaltfläche „Schätzen“. Excel erkennt aufgrund der vorgegebenen Zielzelle automatisch den Bereich „$B$1:$B$3“.

4 Im Bereich der „Nebenbedingungen“ klicken Sie auf die Schaltfläche „Hinzufügen“. Das Dialogfenster „Nebenbedingungen hinzufügen“ wird eingeblendet.

5 Die Einnahmen sollten 5000 DM nicht unterschreiten, klicken Sie deswegen auf die Zelle B1, wählen Sie anschließend mit Hilfe des Auswahlpfeils die Bedingung „>=“ und geben Sie dann in das Feld „Nebenbedingung“ den Wert „5000“ ein.

Ein Klick auf die Schaltfläche „Hinzufügen“ fügt die Bedingung hinzu, und Sie können die nächste Bedingung festlegen.

6 Die Ausgaben werden mindestens die Hälfte der Einnahmen in Anspruch nehmen. Deshalb lautet die Eingabe für die Zelle „B2“: „>=$B$1/2“. Ein Klick auf die Schaltfläche „Hinzufügen“ fügt auch diese Bedingung in die Tabelle ein.

7 Die Belastung wird keinesfalls geringer als 2000 DM werden. Also lautet die letzte Bedingung: „$B$3>=2000“. Ein Klick auf die Schaltfläche „OK“ fügt die letzte Bedingung hinzu und schließt das Dialogfenster „Nebenbedingungen hinzufügen“.

8 Mit einem Klick auf die Schaltfläche „Lösen“ erscheint die Nachricht, dass der Solver unter Einhaltung der Nebenbedingungen eine Lösung gefunden hat. Ein Klick auf die Schaltfläche „OK“ übernimmt die Werte, ein Klick auf die Schaltfläche „Abbrechen“ stellt die Anfangswerte wieder her.

![](img/5f36a0372e5f0f300d0bad16e6a18053_97_2.png)

### TIPP Möglichkeiten zum Löschen

Excel bietet zum Löschen von Daten mehrere Optionen an, die nicht immer klar verständlich sind. Um zum Beispiel bestimmte Zelleninhalte zu löschen, markieren Sie die zu löschenden Zellen. Öffnen Sie anschließend das Menü „Bearbeiten“ und im Untermenü ziehen Sie den Cursor auf den Eintrag „Löschen“. Folgende Optionen stehen Ihnen dann zum Löschen zur Verfügung: „Alles“: Löscht alles, was in dieser Zelle vorhanden ist (Inhalt, Formatierungen und Kommentare). „Format“: Entfernt ausschließlich alle Formatierungen, die Inhalte und Kommentare bleiben erhalten. „Inhalte“: Löscht die Daten aus der Zelle, alle Formatierungen und Kommentare bleiben bestehen. „Kommentare“: Vorhandene Kommentare werden entfernt, Inhalte und Formatierungen der markierten Zellen bleiben erhalten.

## Unterschiedliche Szenarien durchrechnen

Mit Hilfe von unterschiedlichen Szenarien können Sie Excel künftige Entwicklungen durchrechnen lassen. Dabei ersetzen Sie innerhalb einer Tabelle eine Reihe von Werten durch andere Werte. Dadurch können Sie die unterschiedlichen Resultate miteinander vergleichen und beurteilen. Die unterschiedlichen Szenarien werden in der aktuellen Tabelle gespeichert. Das Beispiel einer Buchungsliste mit optimistischer und pessimistischer Zukunftsbeurteilung macht die Möglichkeiten des „Szenario-Managers“ deutlich.

1 Legen Sie eine Excel-Tabelle mit folgendem Inhalt an:

| Kategorie | Preis | Posten | Umsatz |
|---|---|---|---|
| Einfach | 99,00 DM | 199 | 19.701,00 DM |
| Mittel | 157,00 DM | 159 | 24.963,00 DM |
| Hoch | 219,00 DM | 19 | 4.161,00 DM |
| Exklusiv | 399,00 DM | 11 | 4.389,00 DM |

2 Die Umsätze berechnen Sie mit der Multiplikationsformel „=B2*C2“ und kopieren diese Formel für alle mit Kategorien belegten Zeilen. Die Summe der Umsätze berechnen Sie mit der Summenfunktion „=Summe(D2:D5)“. Speichern Sie anschließend die Arbeitsmappe.

3 Markieren Sie die gesamte Tabelle. Den Szenario-Manager aktivieren Sie, indem Sie auf den Menübefehl „Extras“ klicken und im Untermenü die Option „Szenario-Manager“ wählen. Das Dialogfenster „Szenario-Manager“ öffnet sich.

![](img/5f36a0372e5f0f300d0bad16e6a18053_98_0.png)

4 Klicken Sie im „Szenario-Manager“ auf die Schaltfläche „Hinzufügen“. Das Dialogfenster „Szenario hinzufügen“ wird eingeblendet.

Tippen Sie in das Feld „Szenarioname“ den Begriff „Optimist“ ein. Das Feld „Veränderbare Zellen“ belegen Sie mit dem Bereich der Buchungsangaben „C2:C5“. Klicken Sie anschließend auf die Schaltfläche „OK“. Das Dialogfenster „Szenariowerte“ wird eingeblendet.

5 Setzen Sie die optimistischen Schätzungen für jede Zelle ein. Ein Klick auf die Schaltfläche „OK“ führt Sie in das Dialogfenster „Szenario-Manager“ zurück. Sie können an dieser Stelle gleich ein weiteres Szenario einrichten, indem Sie auf die Schaltfläche „Hinzufügen“ klicken. Vergeben Sie jetzt den Namen „Pessimist“ und klicken auf die Schaltfläche „OK“.

6 In das jetzt eingeblendete Dialogfenster „Szenariowerte“ tippen Sie Ihre pessimistischen Schätzungen für jeden Buchungswert ein. Ein Klick auf die Schaltfläche „OK“ führt Sie wieder in den „Szenario-Manager“ zurück.

7 Markieren Sie eine der Szenarien und klicken Sie dann auf die Schaltfläche „Anzeigen“. Excel zeigt das jeweils aktivierte Szenarioergebnis in der Tabelle an. Ein Klick auf die Schaltfläche „Bericht“ erstellt einen aussagekräftigen Bericht über Ihre Szenarien, so dass Sie in Ruhe die Ausgangswerte mit den Schätzwerten und den daraus resultierenden Ergebnissen vergleichen können.

![](img/5f36a0372e5f0f300d0bad16e6a18053_98_1.png)

## Der Trick mit der Landkarte

Die Landkarten-Funktion von Excel bietet Ihnen die Möglichkeit, Daten geografisch zu veranschaulichen. Dabei ist es wichtig, dass Sie zuerst die Tabelle mit den Daten anlegen und dann die Landkarte. Weiterhin ist es bedeutend zu wissen, dass Sie als Kartenmerkmale nur Regionen, Länder oder Kontinente bestimmen können. Großstädte werden von der Excel-Landkartenfunktion nicht erkannt.

| Land | Mitglieder |
|---|---|
| Schleswig-Holstein | 2000 |
| Hamburg | 1200 |
| Berlin | 900 |
| Bremen | 81 |
| Bayern | 2200 |

1 Geben Sie in Excel eine Tabelle mit folgenden Werten ein:

2 Markieren Sie die Tabelle und klicken Sie auf das Symbol der Landkarte. Die Mausanzeige verwandelt sich in ein Kreuz. Ziehen Sie dieses Kreuz bei gedrückter linker Maustaste über den

### TIPP Mappen automatisch öffnen

Standardmäßig wird Excel mit einer leeren Arbeitsmappe geöffnet. Wenn Sie wollen, dass Excel automatisch mit einer oder mehreren Arbeitsmappen startet, so müssen Sie diese in einem speziellen Ordner ablegen. Dieser Ordner wird bei der Programminstallation automatisch angelegt und besitzt die Bezeichnung „XLSSTART“. Der Ordner wird auch als „Startordner“ bezeichnet und bei der Standardinstallation von Office in dem Pfad „Programme/Microsoft Office/Office/“ gelegt. Alle Arbeitsmappen, die Sie in diesem Ordner speichern, stehen Ihnen beim Start von Excel automatisch zur Verfügung. Um die aktuelle Arbeitsmappe in dem Startordner zu speichern, wählen Sie den Menübefehl „Datei“ und im Untermenü den Befehl „Speichern unter“. Im jetzt eingeblendeten Dialogfenster „Speichern unter“ wählen Sie den Startordner „XLSSTART“ aus und speichern Ihre Arbeitsmappe dort. Wenn Ihre in diesem Ordner hinterlegten Arbeitsmappen nicht mehr automatisch geöffnet werden sollen, so verschieben Sie diese in Ihren Standardordner, zum Beispiel „Eigene Dateien“ zurück.

![](img/5f36a0372e5f0f300d0bad16e6a18053_98_2.png)

![](img/5f36a0372e5f0f300d0bad16e6a18053_98_3.png)
