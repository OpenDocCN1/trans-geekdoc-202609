
Die Moleküle, die den Alltag ausmachen, bestehen aus Atomen, oftmals sehr vielen davon. Diese Atome sind durch chemische Bindungen miteinander verbunden. Diese Bindungen »kleben« Atome regelrecht durch ihre gemeinsamen Elektronen zusammen. Es gibt viele verschiedene Arten molekularer Bindungen, einschließlich kovalenter Bindungen, und verschiedene Arten nicht kovalenter Bindungen.

### Kovalente Bindungen

Bei kovalenten Bindungen werden Elektronen zwischen zwei Atomen geteilt, sodass die gleichen Elektronen Zeit um beide Atome verbringen (siehe [Abbildung 4-3](#Chapter04_9783960103516.xhtml#abb4-3)). Grundsätzlich sind kovalente Bindungen die stärksten chemischen Bindungen. Sie entstehen und zerbrechen bei chemischen Reaktionen. Kovalente Bindungen sind in der Regel sehr stabil: Sobald sie sich gebildet haben, braucht es sehr viel Energie, um sie wieder zu lösen, sodass die Atome sehr lange gebunden bleiben können. Aus diesem Grund verhalten sich Moleküle wie individuelle Objekte anstatt wie lose Ansammlungen nicht verwandter Atome. Tatsächlich werden Moleküle durch kovalente Bindungen definiert: Ein Molekül ist eine Ansammlung von Atomen, die durch kovalente Bindungen verbunden sind.

![image](Images/p47-1.png)

*Abbildung 4-3: Links: zwei Atomkerne, jeder umgeben von einer Elektronenwolke. Rechts: Nähern die Atome sich an, verbringen die Elektronen mehr Zeit im Raum zwischen den Kernen. Dies zieht die Kerne zusammen und bildet eine kovalente Bindung zwischen den Atomen.*

### Nicht kovalente Bindungen

Bei nicht kovalenten Bindungen teilen sich Atome Elektronen nicht direkt, aber sie bilden schwache elektromagnetische Wechselwirkungen. Da sie nicht so stark sind wie kovalente Bindungen, sind sie kurzlebiger, zerfallen laufend und bilden sich neu. Nicht kovalente Bindungen »definieren« Moleküle nicht auf die gleiche Weise wie kovalente Bindungen, aber sie haben eine große Auswirkung auf die Formen, die Moleküle annehmen können, und die Art, wie sich verschiedene Moleküle miteinander verbinden.

»Nicht kovalente Bindungen« ist ein Oberbegriff, der verschiedene Arten von Interaktionen abdeckt. Beispiele nicht kovalenter Bindungen sind Wasserstoffbrücken (siehe [Abbildung 4-4](#Chapter04_9783960103516.xhtml#abb4-4)), Ionenbrücken, π-π-Wechselwirkungen usw. Die hier genannten Wechselwirkungen spielen häufig eine entscheidende Rolle bei der Arzneimittelentwicklung, da die meisten Wirkstoffe durch nicht kovalente Wechselwirkungen mit biologischen Molekülen im menschlichen Körper interagieren.

![image](Images/p47-2.png)

*Abbildung 4-4: Wassermoleküle bilden starke Wasserstoffbrücken zwischen Wasserstoff und Sauerstoff an benachbarten Molekülen aus. Ein solides Netzwerk von Wasserstoffbrücken trägt zum Teil zur Stärke des Wassers als Lösungsmittel bei. (Quelle: Wikimedia, [https://commons.wikimedia.org/wiki/File:SimpleBayesNet.svg](https://commons.wikimedia.org/wiki/File:SimpleBayesNet.svg))*

Wir kommen an anderen Stellen des Buchs wieder auf diese Bindungsarten zurück. In diesem Kapitel werden wir uns hauptsächlich mit kovalenten Bindungen befassen. Nicht kovalente Wechselwirkungen werden deutlich wichtiger, wenn wir damit beginnen, uns mit biophysikalischen Deep-Learning-Modellen auseinanderzusetzen.

### Molekülgraphen

Ein *Graph* ist eine mathematische Datenstruktur, die aus *Knoten* besteht, die durch *Kanten* (siehe [Abbildung 4-5](#Chapter04_9783960103516.xhtml#abb4-5)) verbunden werden. Graphen sind äußerst nützliche Abstraktionen in der Informatik. Tatsächlich gibt es einen ganzen Zweig der Mathematik, der als Graphentheorie bezeichnet wird und sich zum Ziel gesetzt hat, die Eigenschaften von Graphen zu verstehen sowie Wege zu finden, diese zu manipulieren und zu analysieren. Graphen werden für die Beschreibung von allem genutzt, von den Rechnern, aus denen ein Netzwerk besteht, über Pixel, die sich zu einem Bild zusammensetzen, bis hin zu Schauspielern, die in Filmen mit Kevin Bacon mitgewirkt haben.

![image](Images/p48-1.png)

*Abbildung 4-5: Beispiel eines mathematischen Graphen mit sechs Knoten, der durch Kanten verbunden wird. (Quelle: Wikimedia, [https://commons.wikimedia.org/wiki/File:6n-graf.svg](https://commons.wikimedia.org/wiki/File:6n-graf.svg))*

Wichtig ist, dass Moleküle auch als Graphen betrachtet werden können (siehe [Abbildung 4-6](#Chapter04_9783960103516.xhtml#abb4-6)). In dieser Beschreibung stellen die Knoten Atome im Graphen dar, während die Kanten die chemischen Bindungen abbilden. Jedes Molekül kann in einen entsprechenden Molekülgraphen umgewandelt werden.

![image](Images/p48-2.png)

*Abbildung 4-6: Ein Beispiel für die Umwandlung eines Benzolmoleküls in einen Molekülgraphen. Beachten Sie, dass Atome in Knoten und chemische Bindungen in Kanten umgewandelt werden.*

Im restlichen Kapitel werden wir wiederholt Moleküle in Graphen umwandeln, um sie zu analysieren und Vorhersagen zu treffen.

### Molekulare Konformationen

Ein Molekülgraph beschreibt die in einem Molekül enthaltenen Atome und deren Bindungen untereinander. Aber es gibt noch eine weitere Sache, die wir wissen müssen: die räumliche Anordnung der Atome, die als *Konformation* des Moleküls bezeichnet wird.

Atome, Bindungen und Konformationen stehen in Beziehung zueinander. Sind zwei Atome kovalent gebunden, kann dies den Abstand zwischen ihnen festlegen und mögliche Konformationen stark einschränken. Die Winkel, die durch drei oder vier gebundene Atome gebildet werden, sind ebenfalls oft beschränkt. Manchmal gibt es ganze Atomcluster, die völlig starr sind und sich alle als eine Einheit bewegen. Andere Molekülteile wiederum sind flexibel und ermöglichen den Atomen, sich relativ zueinander zu bewegen. Zum Beispiel erlauben viele (aber nicht alle) kovalente Bindungen den Atomgruppen, die sie verbinden, sich frei um die Achse der Bindung zu drehen. Dadurch kann das Molekül viele verschiedene Konformationen annehmen.

[Abbildung 4-7](#Chapter04_9783960103516.xhtml#abb4-7) zeigt ein sehr beliebtes Molekül: Saccharose, auch als Haushaltszucker bekannt. Es wird sowohl als chemische 2-D-Struktur als auch als 3-D-Konformation dargestellt. Saccharose besteht aus zwei miteinander verbundenen Ringen. Jeder Ring ist ziemlich starr, sodass sich seine Form im Laufe der Zeit kaum ändert. Aber das Bindeglied, das sie verbindet, ist deutlich flexibler, sodass sich die Ringe relativ zueinander bewegen können.

![image](Images/p49-1.png)

*Abbildung 4-7: Saccharose, dargestellt als 3-D-Konformation und chemische 2-D-Struktur. Bilder aus Wikimedia ([https://commons.wikimedia.org/wiki/File:Sucrose-3D-balls.png](https://commons.wikimedia.org/wiki/File:Sucrose-3D-balls.png)) und Wikipedia ([https://en.wikipedia.org/wiki/File:Saccharose2.svg](https://en.wikipedia.org/wiki/File:Saccharose2.svg)).*

Je größer die Moleküle werden, desto mehr mögliche Konformationen können sie annehmen. Große Makromoleküle wie Proteine (siehe [Abbildung 4-8](#Chapter04_9783960103516.xhtml#abb4-8)) benötigen zur Untersuchung möglicher Konformationen derzeit sehr kostspielige Simulationen.

![image](Images/p50-1.png)

*Abbildung 4-8: Eine in 3-D gerenderte Konformation von Bacteriorhodopsin (zur Erfassung von Lichtenergie). Proteinkonformationen sind besonders komplex und enthalten mehrere geometrische 3-D-Motive. Sie erinnern daran, dass Moleküle zusätzlich zu ihren chemischen Formeln auch eine Geometrie aufweisen. (Quelle: Wikimedia, [https://upload.wikimedia.org/wikipedia/commons/thumb/d/dd/1M0K.png/480px-1M0K.png](https://upload.wikimedia.org/wikipedia/commons/thumb/d/dd/1M0K.png/480px-1M0K.png))*

### Chiralität von Molekülen

Einige Moleküle (darunter viele Medikamente) liegen in zwei Formen vor, die sich spiegeln. Das wird *Chiralität* genannt. Wie in [Abbildung 4-9](#Chapter04_9783960103516.xhtml#abb4-9) dargestellt, hat ein chirales Molekül beides, eine »rechtshändige« Form (auch bekannt als »R«-Form) und eine »linkshändige« Form (auch bekannt als »S«-Form).
