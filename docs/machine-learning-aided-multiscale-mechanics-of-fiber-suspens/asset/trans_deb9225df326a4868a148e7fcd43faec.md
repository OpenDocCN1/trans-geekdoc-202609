
Karlsruher Institut für Technologie

Schriftenreihe
Kontinuumsmechanik im Maschinenbau

## 28

## Benedikt Sterr

## Machine learning aided multiscale mechanics of fiber suspensions

Benedikt Sterr

## Machine learning aided multiscale mechanics of fiber suspensions

## Schriftenreihe

## Kontinuumsmechanik im Maschinenbau

## Band 28

Karlsruher Institut für Technologie (KIT)
Institut für Technische Mechanik
Bereich Kontinuumsmechanik

Hrsg. Prof. Dr.-Ing. habil. Thomas Böhlke

Eine Übersicht aller bisher in dieser Schriftenreihe erschienenen Bände finden Sie am Ende des Buchs.

## Machine learning aided multiscale mechanics of fiber suspensions

by
Benedikt Sterr

![](img/283dee3537da34c9897f9777475c5d3d_4_0.png)

Karlsruher Institut für Technologie
Institut für Technische Mechanik
Bereich Kontinuumsmechanik

## Machine learning aided multiscale mechanics of fiber suspensions

Zur Erlangung des akademischen Grades eines Doktor der Ingenieurwissenschaften von der KIT-Fakultät für Maschinenbau des Karlsruher Instituts für Technologie (KIT) genehmigte Dissertation

von Benedikt Sterr, M.Sc.

Tag der mündlichen Prüfung: 22. November 2024
Hauptreferent: Prof. Dr.-Ing. Thomas Böhlke
Korreferent: Prof. Dr. rer. nat. Matti Schneider
Korreferent: Prof. Dr. Andrew N. Hrymak

## Impressum

![](img/283dee3537da34c9897f9777475c5d3d_5_0.png)

Karlsruher Institut für Technologie (KIT)
KIT Scientific Publishing
Straße am Forum 2
D-76131 Karlsruhe

KIT Scientific Publishing is a registered trademark
of Karlsruhe Institute of Technology.
Reprint using the book pdf is not allowed.

www.bibliothek.kit.edu/ksp.php | E-Mail: info@ksp.kit.edu | Shop: www.ksp.kit.edu

![](img/283dee3537da34c9897f9777475c5d3d_5_1.png)

This document – excluding parts marked otherwise, the cover, pictures and graphs –
is licensed under a Creative Commons Attribution-Share Alike 4.0 International License
(CC BY-SA 4.0): https://creativecommons.org/licenses/by-sa/4.0/legalcode.en

![](img/283dee3537da34c9897f9777475c5d3d_5_2.png)

The cover page is licensed under a Creative Commons
Attribution-No Derivatives 4.0 International License (CC BY-ND 4.0):
https://creativecommons.org/licenses/by-nd/4.0/legalcode.en

Print on Demand 2025 – Gedruckt auf FSC-zertifiziertem Papier

ISSN 2192-693X
ISBN 978-3-7315-1421-3
DOI 10.5445/KSP/1000179536

## Publications and citation

This publication based thesis contains contents from the following publications, which are available under the CC BY 4.0 license¹:

- Sterr, B. and Wicht, D. and Hrymak, A. and Schneider, M. and Böhlke, T., 2023.
- Homogenizing the viscosity of shear-thinning fiber suspensions with an FFT-based computational method.
- Journal of Non-Newtonian Fluid Mechanics 321, 105101
- https://doi.org/10.1016/j.jnnfm.2023.105101
- Sterr, B. and Hrymak, A. and Schneider, M. and Böhlke, T., 2024.
- Machine learning assisted discovery of effective viscous material laws for shear-thinning fiber suspensions.
- Computational Mechanics
- https://doi.org/10.1007/s00466-024-02490-4
- Sterr, B. and Gajek, S. and Hrymak, A. and Schneider, M. and Böhlke, T., 2024.
- Deep material networks for fiber suspensions with infinite material contrast.
- arXiv:2406.11662
- https://doi.org/10.48550/arXiv.2406.11662
- Accepted in International Journal for Numerical Methods in Engineering in February 2025

Whenever content from these publications is used, this is indicated by a footnote in the corresponding chapter or section heading. To specify the manner in which the publication content is utilized, we define and use the clause *based on* as follows.

¹ https://creativecommons.org/licenses/by/4.0/

- Chapters or sections *based on* one or multiple publications include, but are not restricted to, selected content from the referenced publications. The sections from which the publication content was taken are given in the footnotes.
- Notation, spelling, and citation style of the publication content were homogenized throughout the thesis, and references to other chapters in this thesis were introduced.
- Repeating content was omitted and replaced with references to other sections of this thesis where appropriate.
- The numbering of equations, figures, and tables was adapted.

Additionally, the captions of figures and tables taken from the above publications are furnished with the clause *adapted from*. The formatting of figures and tables *adapted from* publications may have been changed and homogenized. The respective reference publication and the respective figure or table number are provided in the captions.

Another published article, which was *not* used in this thesis, is listed here according to the doctoral regulations for Mechanical Engineering (2017) §12 (1):

- Sterr, B. and Mahravan, E. and Kim, D., 2021.
- Uncertainty quantification of heat transfer in a microchannel heat sink with random surface roughness.
- *International Journal of Heat and Mass Transfer* 174, 121307.
- https://doi.org/10.1016/j.ijheatmasstransfer.2021.121307

## Zusammenfassung

In Formungsprozessen von faserverstärkten Kunststoffbauteilen beeinflusst die Fasersuspensionsviskosität verschiedene Prozessparameter und physikalische Felder, die sich wiederum auf die Eigenschaften des fertigen Bauteils auswirken. Beispielsweise beeinflusst die Fasersuspensionsviskosität die Schneckendrehzahl beim Spritzgießen, die Presskraft beim Formpressen und allgemein das Strömungsfeld. Deshalb ist ein genaues Verständnis der Fasersuspensionsviskosität von entscheidender Bedeutung für die Modellierung von Fertigungsprozessen und die Vorhersagegenauigkeit von digitalen Prozessketten. Allerdings ist die experimentelle und analytische Untersuchung der Fasersuspensionsviskosität mit erheblichen Schwierigkeiten verbunden. Insbesondere ist es während rheologischer Experimente eine Herausforderung, einen bestimmten Orientierungszustand der Fasern zu gewährleisten. Außerdem erschweren die stark nichtlinearen Eigenschaften von Polymerschmelzen und die komplexe Geometrie der Suspensionsmikrostruktur analytische Bemühungen.

In dieser Arbeit werden rechnergestützte Homogenisierungsansätze mit maschinellem Lernen kombiniert, um das anisotrope, viskose Verhalten von Fasersuspensionen zu untersuchen und zu modellieren. Genauer gesagt werden Fast-Fourier-Transformation (FFT) basierte Methoden verwendet, um die effektive Spannungsantwort von Fasersuspensionen für ein bestimmtes Strömungsszenario zu berechnen. Anschließend wird maschinelles Lernen genutzt, um rechnerisch effiziente Ersatzmodelle für das Effektivverhalten der Suspensionen zu entwickeln. Aufgrund der industriellen Relevanz von faserverstärkten Polyamid 6 (PA6) Materialsystemen, sind die Untersuchungen in dieser Arbeit auf Fasersuspensionen mit scherverdünnendem PA6 Matrixmaterial fokussiert.

Eine bestehende FFT-basierte Methode für Suspensionen mit Newtonschen Lösungsmitteln wird auf Suspensionen mit nicht-Newtonschen Lösungsmitteln erweitert. Insbesondere wird die Legendre-Fenchel-Transformation genutzt, um eine duale Formulierung des zugehörigen Variationsproblems zu erhalten, das effizient mit FFTs und einem Newton-CG-Ansatz gelöst wird.

Die FFT-basierte Methode wird mit überwachtem, maschinellem Lernen kombiniert, um Modelle für das Effektivverhalten von Fasersuspensionen mit einem scherverdünnenden PA6 Matrixmaterial zu entwickeln. Dazu wird das anisotrope Scherverdünnungsverhalten von Fasersuspensionen für 109 verschiedene Faserorientierungszustände untersucht. Basierend auf den Ergebnissen der Untersuchungen werden vier Modellkandidaten für die effektive Viskosität formuliert und die Modellparameter mit überwachtem, maschinellem Lernen identifiziert.

Darüber hinaus wird eine neuartige Deep Material Network (DMN)-Architektur für die Behandlung von Fasersuspensionen mit unendlichem Materialkontrast vorgeschlagen. Insbesondere werden zweiphasige, geschichtete Emulsionen als DMN-Bausteine verwendet und deren geschlossene Homogenisierungsfunktionen hergeleitet. Um unendlichem Materialkontrast zu behandeln, werden zweiphasige, geschichtete Emulsionen auf spezielle Art und Weise wiederholt geschichtet. Unter Verwendung der abgeleiteten geschichteten Materialien wird das direct DMN Framework auf die Flexible DMN (FDMN) Architektur erweitert. Anschließend werden FDMNs zur Vorhersage des effektiven viskosen Verhaltens von Fasersuspensionen mit einem scherverdünnendem PA6 Matrixmaterial verwendet.
