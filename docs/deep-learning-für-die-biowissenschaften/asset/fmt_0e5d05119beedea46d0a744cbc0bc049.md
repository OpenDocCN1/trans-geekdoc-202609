
# Rechnerische Vorhersagen sind schwierig

Rechnerische Vorhersagen sind schwierig, da die Proteinbindung viele sehr spezifische Wechselwirkungen beinhaltet. Eine winzige Veränderung der Positionen einiger weniger Atome kann darüber bestimmen, ob ein Molekül an ein Protein bindet oder nicht. Darüber hinaus sind viele Proteine flexibel und bewegen sich ständig. Ein Protein ist möglicherweise in der Lage, ein Molekül zu binden, wenn es sich in bestimmten Konformationen befindet, aber nicht, wenn es sich in anderen befindet. Die Bindung wiederum kann zu weiteren Änderungen der Konformation eines Proteins, und damit seiner Funktion, führen.

Im restlichen Kapitel werden wir die Herausforderung, die Proteinbindung zu verstehen, als motivierendes Rechenbeispiel verwenden. Wir werden uns eingehend mit aktuellen Deep-Learning- und Machine-Learning-Ansätzen befassen, um Vorhersagen zum Bindungsverhalten zu treffen.

## Biophysikalische Eigenschaften

Wie bereits im vorhergehenden Kapitel besprochen, besteht einer der ausschlaggebenden Schritte bei der Anwendung von Machine Learning in einer neuen Domäne darin, herauszufinden, wie Trainingsdaten in ein für Lernalgorithmen geeignetes Format umgewandelt (oder zusammengefasst) werden können. Wir haben mehrere Methoden zur Charakterisierung einzelner kleiner Moleküle vorgestellt. Könnten wir diese Techniken für den Einsatz in biophysikalischen Systemen vielleicht anpassen?

Leider ist das Verhalten biophysikalischer Systeme durch ihre 3-D-Struktur stark eingeschränkt, sodass die 2-D-Methoden aus den vorherigen Kapiteln wichtige Informationen übersehen. Aus diesem Grund werden wir in diesem Kapitel einige neue Featurization-Methoden abhandeln. Die erste Methode, die *Grid Featurization*, durchsucht eine 3-D-Struktur nach kritischen physikalischen Wechselwirkungen, wie Wasserstoff- und Salzbrücken (dazu später mehr), von denen bekannt ist, dass sie eine wichtige Rolle bei der Bestimmung der Proteinstruktur spielen. Der Vorteil dieser Technik ist, dass wir auf eine Fülle bekannter Fakten über die Physik der Proteine zurückgreifen können. Die Schwäche liegt natürlich darin, dass wir an die uns bekannte Physik gebunden sind. Dadurch sinkt die Wahrscheinlichkeit, dass unsere Algorithmen in der Lage sind, neue Physik zu entdecken.

Die alternative Featurization-Methode ist die *Atomic Featurization*, die einfach eine verarbeitete Darstellung der 3-D-Positionen und -Identitäten aller Atome im System liefert. Dies erhöht erheblich die Herausforderung für den Lernalgorithmus, da er lernen muss, kritische physikalische Wechselwirkungen zu identifizieren, aber es ermöglicht auch, dass Lernalgorithmen neue Muster interessanten Verhaltens erkennen.

### PDB-Dateien und ihre Fallstricke

Proteinstrukturen werden oft in PDB-Dateien gespeichert. Das sind einfache Textdateien, die Beschreibungen der Atome in der Struktur und ihre Positionen im Koordinatenraum relativ zueinander beinhalten. Featurization-Algorithmen basieren in der Regel auf Bibliotheken, die PDB-Dateien einlesen und in In-Memory-Datenstrukturen speichern. So weit, so gut, nicht wahr?

Leider sind PDB-Dateien oft fehlerhaft. Der Grund findet sich in der zugrunde liegenden Physik. Häufig hat ein Experiment nicht die nötige Auflösung, um einen Teil der Proteinstruktur vollständig zu bestimmen. Solche Regionen sind in der PDB-Datei nicht spezifiziert, sodass häufig viele Atome oder sogar ganze Teilstrukturen des Proteins in der Kernstruktur fehlen.

Bibliotheken wie `DeepChem` versuchen oftmals, das »Richtige« zu tun und diese fehlenden Regionen rechnerisch aufzufüllen. Es ist wichtig, anzumerken, dass diese Bereinigung ungenau ist und es immer noch keinen völlig zufriedenstellenden Ersatz für einen Experten gibt, der sich die Proteinstruktur anschaut (in einem geeigneten Betrachtungsprogramm) und auf Probleme hinweist. Es bleibt zu hoffen, dass sich die Software zur Behandlung dieser Fehler in den nächsten Jahren verbessert und die Notwendigkeit für fachkundige Beratung abnimmt.

## Grid Featurization

Wandeln wir biophysikalische Strukturen in Vektoren um, können wir mithilfe von Machine-Learning-Algorithmen Vorhersagen über sie treffen. Es liegt auf der Hand, dass es nützlich wäre, einen Algorithmus für die Verarbeitung von Protein-Ligand-Systemen zu haben. Einen solchen Algorithmus zu entwickeln, ist jedoch komplex. Idealerweise würde eine Featurization-Methode über umfangreiches Wissen der Chemie solcher Systeme verfügen, sodass sie nützliche Eigenschaften herausfiltern könnte.

Bei diesen Merkmalen könnte es sich unter anderem um die Anzahl nicht kovalenter Bindungen zwischen dem Protein und dem Liganden, wie Wasserstoffbrücken oder andere Wechselwirkungen, handeln. (Die meisten Protein-Ligand-Systeme haben keine kovalenten Bindungen zwischen Protein und Ligand.)

Glücklicherweise stellt `DeepChem` einen solchen Featurizer zur Verfügung. Der `RdkitGridFeaturizer` fasst eine Reihe wichtiger chemischer Informationen in einem kurzen Vektor zur Verwendung in Lernalgorithmen zusammen. Auch wenn es nicht notwendig ist, die zugrunde liegende Wissenschaft im Detail zu verstehen, um den Featurizer nutzen zu können, ist es dennoch hilfreich, Grundkenntnisse in der zugrunde liegenden Physik zu haben. Daher werden wir uns zunächst mit der Biophysik makromolekularer Komplexe befassen, bevor wir uns der Beschreibung der Berechnungen des Grid-Featurizers widmen.

Beim Lesen dieses Abschnitts kann es hilfreich sein, auf die im letzten Kapitel besprochenen Grundlagen chemischer Wechselwirkungen zurückzugreifen. Begriffe wie kovalente und nicht kovalente Bindungen werden häufiger genannt.

Der Grid-Featurizer sucht nach diesen chemischen Wechselwirkungen innerhalb einer gegebenen Struktur und erstellt einen Merkmalsvektor, der die Anzahl dieser Wechselwirkungen enthält. Im weiteren Verlauf dieses Kapitels werden wir genauer darauf eingehen, wie dieser Prozess algorithmisch aussieht.

### Wasserstoffbrücken

Ist ein Wasserstoffatom kovalent an ein elektronegativeres Atom wie Sauerstoff oder Stickstoff gebunden, verbringen die gemeinsamen Elektronen die meiste Zeit in der Nähe des elektronegativeren Atoms. Dadurch verbleibt der Wasserstoff mit einer positiven Nettoladung. Kommt nun der positiv geladene Wasserstoff in die Nähe eines negativ geladenen Atoms, ziehen sie sich gegenseitig an. Hierbei spricht man von einer Wasserstoffbrücke (siehe [Abbildung 5-6](#Chapter05_9783960103516.xhtml#abb5-6)).

![image](Images/p70-1.png)

*Abbildung 5-6: Ein gerendertes Beispiel einer Wasserstoffbrücke. Ein Überschuss an negativer Ladung des Sauerstoffs interagiert mit einem Übermaß an positiver Ladung des Wasserstoffs, wodurch eine Bindungswechselwirkung entsteht. (Quelle: Wikimedia, [https://commons.wikimedia.org/wiki/File:Hydrogen-bonding-in-water-2D.png](https://commons.wikimedia.org/wiki/File:Hydrogen-bonding-in-water-2D.png))*

Aufgrund der geringen Größe von Wasserstoffatomen können sie anderen Atomen sehr nahekommen, was zu einer starken elektrostatischen Anziehung führt. Dies macht Wasserstoffbrücken zu einer der stärksten nicht kovalenten Wechselwirkungen. Sie sind eine wichtige Form der Interaktion, die oft molekulare Systeme stabilisiert. Zum Beispiel sind die einzigartigen Eigenschaften von Wasser zum Großteil auf das Netz aus Wasserstoffbrücken zurückzuführen, die sich zwischen den Wassermolekülen bilden.

Der `RdkitGridFeaturizer` versucht, die in einer Struktur vorliegenden Wasserstoffbrücken zu zählen, indem es nach Paaren von Protein-Ligand-Atomen des richtigen Typs sucht, die entsprechend nahe beieinanderliegen. Dies erfordert eine Abstandsbegrenzung, die etwas willkürlich ist. Tatsächlich gibt es keine scharfe Trennung zwischen gebundenen und nicht gebundenen Atomen. Das kann zu einigen falsch identifizierten Wechselwirkungen führen, aber empirisch funktioniert ein einfacher Grenzwert recht gut.

### Salzbrücken
