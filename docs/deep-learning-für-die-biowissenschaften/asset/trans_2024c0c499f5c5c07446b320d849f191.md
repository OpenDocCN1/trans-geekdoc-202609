
Ergänzendes Material (z. B. Codebeispiele, Übungen usw.) steht unter `https://github.com/deepchem/DeepLearningLifeSciences` zum Download bereit.

Dieses Buch ist dazu gedacht, Ihnen bei Ihren Aufgaben zu helfen. Grundsätzlich dürfen Sie die mit diesem Buch bereitgestellten Codebeispiele in Ihren Programmen und der dazugehörigen Dokumentation nutzen. Sie müssen uns dazu nicht um Erlaubnis fragen, es sei denn, Sie reproduzieren einen beträchtlichen Teil des Codes. Schreiben Sie beispielsweise ein Programm, das mehrere Codeabschnitte aus diesem Buch enthält, benötigen Sie keine Erlaubnis. Verkaufen oder verteilen Sie dagegen eine CD-ROM mit Beispielen aus Büchern von O’Reilly, benötigen Sie eine Erlaubnis. Eine Frage mit einem Zitat aus diesem Buch unter Angabe eines Codebeispiels zu beantworten, benötigt keine Erlaubnis. Wollen Sie dagegen einen wesentlichen Anteil der Codebeispiele aus diesem Buch in Ihr eigenes Buch integrieren, brauchen Sie eine Erlaubnis.

Wir freuen uns über Quellenangaben, verlangen diese aber nicht. Eine Quellenangabe enthält üblicherweise Titel, Autor, Verlag und ISBN. Zum Beispiel: »Deep Learning in den Biowissenschaften von Bharath Ramsundar, Peter Eastman, Patrick Walters und Vijay Pande (O’Reilly). Copyright 2019 Bharath Ramsundar, Peter Eastman, Patrick Walters und Vijay Pande, ISBN 978-3-96009-130-1.«

Wenn Sie glauben, dass Ihre Nutzung von Codebeispielen über das gewöhnliche Maß hinausgeht oder außerhalb der oben vorgestellten Nutzungsbedingungen liegt, kontaktieren Sie uns bitte unter `kommentar@oreilly.de`.

## Danksagung

Wir möchten uns bei Nicole Tache, unserer Lektorin bei O’Reilly, bedanken. Weiterhin danken wir den Tech- und Beta-Reviewern für ihre wertvollen Beiträge zum Buch. Darüber hinaus möchten wir Karl Leswing und Zhenqin (Michael) Wu für ihre Beiträge zum Programmcode und Johnny Israeli für die wertvollen Ratschläge zum Kapitel über Genomik danken.

Bharath möchte sich bei seiner Familie für ihre Unterstützung und Ermutigung während der vielen langen Wochenenden und Abende bei der Arbeit an diesem Buch bedanken.

Peter dankt seiner Frau für ihre unermüdliche Unterstützung und bedankt sich bei den vielen Kollegen, von denen er so viel über Machine Learning gelernt hat.

Pat bedankt sich bei seiner Frau Andrea und seinen Töchtern Alee und Maddy für ihre Liebe und Unterstützung. Auch möchte er ehemaligen und aktuellen Kollegen bei Vertex Pharmaceuticals und Relay Therapeutics danken, von denen er so viel gelernt hat.

Abschließend möchten wir uns bei der Open-Source-Community von DeepChem für die Ermutigung und Unterstützung während des gesamten Projekts bedanken.

# KAPITEL 1

# Warum Biowissenschaften?

Einsatzgebiete für all diejenigen mit technischem Verständnis und Leidenschaft für Daten gibt es viele, aber nur wenige Gebiete haben eine so grundlegende Auswirkung wie die biomedizinische Forschung. Der Beginn der modernen Medizin hat die Natur der menschlichen Existenz grundlegend verändert. In den letzten 20 Jahren wurden wir Zeuge, wie Innovationen das Leben unzähliger Menschen verändert haben. Bei ihrem ersten Auftreten im Jahr 1981 war HIV/Aids eine zumeist tödliche Krankheit. Die kontinuierliche Weiterentwicklung antiretroviraler Therapien hat die Lebenserwartung betroffener Patienten erheblich verlängert. Andere Krankheiten, wie zum Beispiel Hepatitis C, die vor einem Jahrzehnt noch als nicht behandelbar galt, können nun geheilt werden. Fortschritte in der Genetik ermöglichen die Identifikation und, hoffentlich bald, die Behandlung einer Vielzahl von Erkrankungen. Dank innovativer Diagnostik und Instrumentierung können Mediziner Krankheiten im menschlichen Körper spezifisch identifizieren und gezielt behandeln. Viele dieser Durchbrüche haben von rechnergestützten Methoden profitiert und werden durch diese weiter vorangetrieben.

## Warum Deep Learning?

Algorithmen für Machine Learning sind inzwischen ein wichtiger Bestandteil des Alltags, vom Onlineshopping bis Social Media. Informatiker entwickeln Algorithmen, die es digitalen Assistenten wie Amazon Echo oder Google Home ermöglichen, Sprache zu verstehen. Fortschritte im Machine Learning haben die Übersetzung von Webseiten im laufenden Betrieb ermöglicht. Des Weiteren hat Machine Learning viele Bereiche der Physik und Biowissenschaften beeinflusst. Algorithmen werden auf alles angewandt, von der Entdeckung neuer Galaxien aus Teleskopaufnahmen bis zur Klassifizierung subatomarer Wechselwirkungen am Large Hadron Collider.

Eine der Triebfedern dieser technologischen Fortschritte war die Entwicklung einer Klasse von Methoden des Machine Learning, die als Deep Neural Networks bekannt sind. Während die technologischen Voraussetzungen für künstliche neuronale Netze in den 1950er-Jahren entwickelt und in den 1980er-Jahren verfeinert wurden, entfaltete sich deren volles Potenzial erst in den letzten zehn Jahren mit der Weiterentwicklung der Computerhardware. Im nächsten Kapitel werden wir eine umfassendere Übersicht über Deep Neural Networks geben, es ist jedoch wichtig, die aus der Anwendung von Deep Learning entstandenen Fortschritte zu würdigen:

*   Viele der Entwicklungen bei der Spracherkennung, die in Mobiltelefonen, Computern, Fernsehern und anderen mit dem Internet verbundenen Geräten allgegenwärtig sind, wurden durch Deep Learning vorangetrieben.
*   Die Bilderkennung ist eine Schlüsselkomponente für selbstfahrende Autos, die Internetsuche und andere Anwendungen. Viele der Deep-Learning-Entwicklungen, die Anwendungen für Privatkunden vorangetrieben haben, werden jetzt in der biomedizinischen Forschung eingesetzt, zum Beispiel um Tumorzellen verschiedenen Typen zuzuordnen.
*   Empfehlungssysteme sind zu einer Schlüsselkomponente des Onlineerlebnisses geworden. Unternehmen wie Amazon wenden Deep Learning an, um ihre Kunden, die ein bestimmtes Produkt gekauft haben, dazu zu bewegen, zusätzliche Einkäufe zu tätigen. Netflix geht ähnlich vor, um Filme vorzuschlagen, die ein Nutzer möglicherweise ebenfalls sehen möchte. Viele der Ideen, die hinter diesen Empfehlungssystemen stehen, werden verwendet, um neue Moleküle zu identifizieren, die als Ausgangspunkte für neue Wirkstoffentdeckungen dienen könnten.
*   Übersetzungen waren einst die Domäne sehr komplexer statistischer Computerprogramme. In den letzten Jahren hat Deep Learning die Systeme, die jahrelang manuell kuratiert wurden, übertroffen. Viele der gleichen Ideen werden nun genutzt, um Konzepte aus der wissenschaftlichen Literatur zu extrahieren und Wissenschaftler auf Publikationen aufmerksam zu machen, die sie möglicherweise übersehen hätten.

Die hier genannten sind nur einige der Innovationen, die durch die Anwendung von Deep-Learning-Methoden entstanden sind. Es ist eine interessante Zeit, in der sich allgemein verfügbare wissenschaftliche Daten und Methoden zu deren Verarbeitung annähern. Diejenigen, die in der Lage sind, Daten mit neuen Methoden zu kombinieren, um aus Mustern in diesen Daten zu lernen, können wichtige wissenschaftliche Fortschritte erzielen.

## In den modernen Biowissenschaften geht es um Daten

Wie bereits erwähnt, hat sich die grundlegende Art der Biowissenschaften verändert. Die Verfügbarkeit von Robotik sowie miniaturisierte Experimente haben zu einem drastischen Anstieg der experimentellen Daten, die erstellt werden können, geführt. In den 1980er-Jahren führte ein Biologe ein einzelnes Experiment durch, das nur ein einzelnes Ergebnis lieferte. Dieses konnte dann meist manuell unter Zuhilfenahme eines Taschenrechners verarbeitet werden. Spulen wir zur heutigen Biologie vor, dann verfügen wir über Instrumente, die in ein oder zwei Tagen Millionen experimenteller Datenpunkte erzeugen können. Die Gensequenzierung beispielsweise, in der riesige Datensätze entstehen, ist kostengünstig und routinemäßig geworden.
